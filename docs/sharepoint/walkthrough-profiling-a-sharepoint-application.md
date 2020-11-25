---
title: 'Exemplarische Vorgehensweise: Profilerstellung für eine SharePoint-Anwendung | Microsoft-Dokumentation'
description: Verwenden Sie in dieser exemplarischen Vorgehensweise die Profil Erstellungs Tools in Visual Studio, um die Leistung einer SharePoint-Anwendung zu optimieren.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 66e19f7744a56d147fb0760c6f20254ea4308603
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970107"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Exemplarische Vorgehensweise: Profilerstellung einer SharePoint-Anwendung
  In dieser exemplarischen Vorgehensweise wird die Verwendung von Profilerstellungstools in Visual Studio gezeigt, um die Leistung einer SharePoint-Anwendung zu optimieren. Bei der Beispielanwendung handelt es sich um einen SharePoint-Funktionsereignisempfänger, der eine Leerlaufschleife enthält, welche die Leistung des Funktionsereignisempfängers reduziert. Mit dem Visual Studio-Profiler können Sie den teuersten (langsamsten) Teil des Projekts suchen und eliminieren, auch bekannt als Langsamster *Pfad*.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- [Fügen Sie eine Funktion und einen Funktions Ereignis Empfänger hinzu](#add-a-feature-and-feature-event-receiver).

- [Konfigurieren und Bereitstellen der SharePoint-Anwendung](#configure-and-deploy-the-sharepoint-application).

- [Führen Sie die SharePoint-Anwendung](#run-the-sharepoint-application)aus.

- [Anzeigen und Interpretieren der Profil Ergebnisse](#view-and-interpret-the-profile-results).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von Microsoft Windows und SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>Erstellen eines SharePoint-Projekts
 Erstellen Sie zunächst eine SharePoint-Projekt.

### <a name="to-create-a-sharepoint-project"></a>So erstellen Sie ein SharePoint-Projekt

1. Wählen Sie in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus, um das Dialogfeld **Neues Projekt** anzuzeigen.

2. Erweitern Sie den **SharePoint** -Knoten entweder unter **Visual c#** oder **Visual Basic**, und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie im Bereich Vorlagen die **SharePoint 2010-Projekt** Vorlage aus.

4. Geben Sie im Feld **Name den Namen** **profiletest** ein, und klicken Sie dann auf die Schaltfläche **OK** .

    Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

5. Geben Sie auf der Seite **Standort und Sicherheitsebene für Debugging angeben** die URL für die SharePoint-Serversite ein, auf der Sie die Website Definition debuggen möchten, oder verwenden Sie den Standard Speicherort (http://<em>Systemname</em>/).

6. Wählen Sie im Abschnitt **Was ist die Vertrauens Ebene für diese SharePoint-Lösung?** das Optionsfeld **als Farm Lösung** bereitstellen aus.

    Zurzeit können Sie Farmlösungsprofile erstellen. Weitere Informationen zu Sandkasten Lösungen im Vergleich zu Farm Lösungen finden Sie unter [Überlegungen zu Sandkasten](../sharepoint/sandboxed-solution-considerations.md)Lösungen.

7. Klicken Sie auf die Schaltfläche **Fertig stellen**. Das Projekt wird in **Projektmappen-Explorer** angezeigt.

## <a name="add-a-feature-and-feature-event-receiver"></a>Hinzufügen eines Features und Funktions Ereignis Empfängers
 Fügen Sie dem Projekt als Nächstes eine Funktion zusammen mit dem Ereignisempfänger für die Funktion hinzu. Dieser Ereignisempfänger enthält den Code, für den das Profil erstellt wird.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>So fügen Sie ein Feature und den Funktionsereignisempfänger hinzu

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Knoten **Features** , wählen Sie **Feature hinzufügen** aus, und belassen Sie den Namen im Standardwert **Feature1**.

2. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für **Feature1**, und wählen Sie dann **Ereignis Empfänger hinzufügen** aus.

     Dadurch wird dem Feature eine Codedatei mit verschiedenen auskommentierten Ereignishandlern hinzugefügt, und die Datei wird für die Bearbeitung geöffnet.

3. Fügen Sie in der Ereignisempfängerklasse die folgenden Variablendeklarationen hinzu.

    ```vb
    ' SharePoint site/subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site/subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

4. Ersetzen Sie die `FeatureActivated`-Prozedur durch den folgenden Code.

    ```vb
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add a new announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    ' Waste some time.
                    TimeCounter()
                    ' Update the list.
                    listItem.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try
    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add a new announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +
    DateTime.Now.ToString();
                    // Waste some time.
                    TimeCounter();
                    // Update the list.
                    listItem.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

5. Fügen Sie das folgende Verfahren unterhalb der `FeatureActivated` Prozedur hinzu.

    ```vb

    Public Sub TimeCounter()
        Dim result As Integer
        For i As Integer = 0 To 99999
            For j As Integer = 0 To 9999
                result = i * j
            Next j
        Next i
    End Sub
    ```

    ```csharp
    public void TimeCounter()
    {
        for (int i = 0; i < 100000; i++)
        {
            for (int j = 0; j < 10000; j++)
            {
                int result = i * j;
            }
        }
    }
    ```

6. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das Projekt (**profiletest**), und wählen Sie dann **Eigenschaften** aus.

7. Wählen Sie im Dialogfeld **Eigenschaften** die Registerkarte **SharePoint** aus.

8. Wählen Sie in der Liste **aktive Bereitstellungs Konfiguration** die Option **keine Aktivierung** aus.

     Durch die Auswahl dieser Bereitstellungskonfiguration können Sie später die Funktion in SharePoint manuell aktivieren.

9. Speichern Sie das Projekt.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Konfigurieren und Bereitstellen der SharePoint-Anwendung
 Da das SharePoint-Projekt nun bereit ist, können Sie es konfigurieren und für den SharePoint-Server bereitstellen.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>So konfigurieren und stellen Sie die SharePoint-Anwendung bereit

1. Wählen Sie im Menü **Analyse** die Option **Leistungs-Assistenten starten** aus.

2. Belassen Sie auf der Seite 1 des **Leistungs-Assistenten** die Profil Erstellungs Methode als **CPU-Sampling** , und klicken Sie auf die Schaltfläche **weiter** .

     Die anderen Profilerstellungsmethoden können in komplexeren Profilerstellungssituationen verwendet werden. Weitere Informationen finden Sie unter [Grundlagen zu Profilerstellungsmethoden](../profiling/understanding-performance-collection-methods.md).

3. Belassen Sie auf der Seite 2 des **Leistungs-Assistenten** das Profil Ziel als **profiletest** , und klicken Sie auf die Schaltfläche **weiter** .

     Wenn eine Projektmappe über mehrere Projekte verfügt, werden sie in dieser Liste angezeigt.

4. Deaktivieren Sie auf der Seite 3 des **Leistungs-Assistenten** das Kontrollkästchen Profilerstellung für **ebeneninteraktion aktivieren** , und wählen Sie dann die Schaltfläche **weiter** aus.

     Das Feature Profilerstellung für Ebeneninteraktion (Tier Interaction Profiling, TIP) ist für das Messen der Leistung von Anwendungen, die Datenbanken abfragen, sowie für das Anzeigen der Anzahl der Häufigkeit, wie oft eine Webseite angefordert wird, hilfreich. Da diese Daten für dieses Beispiel nicht erforderlich sind, aktivieren wir dieses Feature nicht.

5. Lassen Sie auf der Seite 4 des **Leistungs-Assistenten** das Kontrollkästchen **Profilerstellung nach Abschluss des Assistenten starten** aktiviert, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

     Der Assistent aktiviert die Anwendungsprofil Erstellung auf dem Server, zeigt das **Leistungs-Explorer** Fenster an und erstellt dann die SharePoint-Anwendung, stellt Sie bereit und führt Sie aus.

## <a name="run-the-sharepoint-application"></a>Ausführen der SharePoint-Anwendung
 Aktivieren Sie das Feature in SharePoint, wodurch die Auslösung des `FeatureActivation`-Ereigniscodes ausgelöst wird.

### <a name="to-run-the-sharepoint-application"></a>So führen Sie die SharePoint-Anwendung aus

1. Öffnen Sie in SharePoint das Menü **Website Aktionen** , und wählen Sie dann **Website Einstellungen** aus.

2. Wählen Sie in der Liste **Website Aktionen** den Link **Website Features verwalten** aus.

3. Wählen Sie in der Liste **Features** neben **profiletest Feature1** die Schaltfläche **aktivieren** aus.

     Aufgrund der in der `FeatureActivated`-Funktion aufgerufenen Leerlaufschleife tritt eine Pause auf, wenn Sie dies vornehmen.

4. Wählen Sie in der **Schnellstart** Leiste **Listen** aus, und wählen Sie dann in der Liste **Listen** die Option **Ankündigungen** aus.

     Beachten Sie, dass der Liste eine neue Ankündigung hinzugefügt wurde, aus der hervorgeht, dass die Funktion aktiviert wurde.

5. Schließen Sie die SharePoint-Website.

     Nachdem Sie SharePoint geschlossen haben, erstellt und zeigt der Profiler einen Beispiel Profil Erstellungs Bericht an und speichert ihn als VSP-Datei im Ordner des **profilletest** -Projekts.

## <a name="view-and-interpret-the-profile-results"></a>Anzeigen und Interpretieren der Profil Ergebnisse
 Zeigen Sie nun nach der Ausführung und Profilerstellung der SharePoint-Anwendung die Testergebnisse an.

### <a name="to-view-and-interpret-the-profile-results"></a>Anzeigen und Interpretieren der Profil Ergebnisse

1. Beachten Sie, dass im Abschnitt **Funktionen mit den meisten einzelnen Aufgaben** des Beispiel Profil Erstellungs Berichts angezeigt wird, dass sich in der Nähe des oberen Rands der `TimeCounter` Liste befindet.

     Diese Position deutet darauf hin, dass es sich bei `TimeCounter` um eine der Funktionen mit der höchsten Anzahl an Beispielen gehandelt hat. Hierbei handelt es sich also um einen der größten Leistungsengpässe in der Anwendung. Diese Situation ist nicht überraschend, da dies für Demonstrationszwecke extra so entworfen wurde.

2. Wählen Sie im Abschnitt **Funktionen mit den meisten einzelnen** Aufgaben den `ProcessRequest` Link aus, um die Kostenverteilung für die `ProcessRequest` Funktion anzuzeigen.

     Beachten Sie im Abschnitt **aufgerufene Funktionen** für `ProcessRequest` , dass die Funktion **featureactiviated** als die teuersten aufgerufene Funktion aufgeführt ist.

3. Wählen Sie im Abschnitt **aufgerufene Funktionen** die Schaltfläche **featureaktiviert** aus.

     Im Abschnitt **aufgerufene Funktionen** für **featureaktivierte** `TimeCounter` wird die Funktion als die teuersten aufgerufene Funktion aufgelistet. Im Bereich **Funktions Code Ansicht** ist der hervorgehobene Code ( `TimeCounter` ) der Hotspot und gibt an, wo die Korrektur erforderlich ist.

4. Schließen Sie den Beispiel-Profilerstellungsbericht.

     Um den Bericht zu einem beliebigen Zeitpunkt erneut anzuzeigen, öffnen Sie die VSP-Datei im **Leistungs-Explorer** Fenster.

## <a name="fix-the-code-and-reprofile-the-application"></a>Korrigieren des Codes und erneyprofilieren der Anwendung
 Beheben Sie nun nach Ermittlung der fehlerhaften Funktion in der SharePoint-Anwendung das Problem.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>So beheben Sie den Code und nehmen eine erneute Profilerstellung der Anwendung vor

1. Kommentieren Sie im Funktionsereignisempfänger-Code den `TimeCounter`-Methodenaufruf in `FeatureActivated` aus, um zu verhindern, dass er aufgerufen wird.

2. Speichern Sie das Projekt.

3. Öffnen Sie in **Leistungs-Explorer** den Ordner Ziele, und wählen Sie dann den Knoten **profiletest** aus.

4. Wählen Sie auf der **Leistungs-Explorer** Symbolleiste auf der Registerkarte **Aktionen** die Schaltfläche **Profilerstellung starten** aus.

     Wenn Sie die Profil Erstellungs Eigenschaften vor der Neuerstellung der Anwendung ändern möchten, wählen Sie stattdessen die Schaltfläche **Leistungs-Assistenten starten** aus.

5. Befolgen Sie die Anweisungen im Abschnitt **Ausführen des SharePoint-Anwendungs** Abschnitts, zuvor in diesem Thema.

     Die Funktion sollte nun weitaus schneller aktiviert werden, da der Aufruf der Leerlaufschleife beseitigt wurde. Im Beispiel-Profilerstellungsbericht wird dies berücksichtigt.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Leistungs Sitzungen](../profiling/performance-session-overview.md)
- [Einführung in die Leistungsprofil Erstellung](../profiling/beginners-guide-to-performance-profiling.md)
- [Aufspüren von Anwendungsengpässen mit Visual Studio Profiler](/archive/msdn-magazine/2008/march/find-application-bottlenecks-with-visual-studio-profiler)