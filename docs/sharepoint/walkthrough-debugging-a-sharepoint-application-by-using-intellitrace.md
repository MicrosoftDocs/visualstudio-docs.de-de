---
title: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace
description: Verwenden Sie IntelliTrace, um SharePoint-Anwendungen einfacher zu Debuggen und zu beheben. Erstellen und Hinzufügen von Code zu einem Funktions Empfänger Testen Sie das Projekt. Sammeln von IntelliTrace-Daten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c7ab11dbe213208a2e8f5e39c3af2d20b79f5cb
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598483"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Exemplarische Vorgehensweise: Debuggen einer SharePoint-Anwendung mithilfe von IntelliTrace

Mit IntelliTrace können Sie SharePoint-Lösungen einfacher debuggen. Herkömmliche Debugger erstellen lediglich eine aktuelle Momentaufnahme der Lösung. Sie können mithilfe von IntelliTrace jedoch in der Lösung aufgetretene Ereignisse sowie den Kontext, in dem sie aufgetreten sind, überprüfen und zum Code navigieren.

 In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie ein SharePoint 2010-oder SharePoint 2013-Projekt in Visual Studio debuggen können, indem Sie Microsoft Monitoring Agent zum Erfassen von IntelliTrace-Daten aus Um diese Daten zu analysieren, müssen Sie Visual Studio Enterprise verwenden. Dieses Projekt integriert einen Funktionsempfänger, der bei aktivierter Funktion der Liste „Aufgaben“ eine Aufgabe und der Liste „Ankündigungen“ eine Ankündigung hinzufügt. Wenn die Funktion deaktiviert wird, wird die Aufgabe als abgeschlossen gekennzeichnet, und der Liste "Ankündigungen" wird eine zweite Ankündigung hinzugefügt. Die Prozedur enthält jedoch einen logischen Fehler, der verhindert, dass das Projekt ordnungsgemäß ausgeführt wird. Mit IntelliTrace können Sie den Fehler suchen und korrigieren.

 **Gilt für:** Die Informationen in diesem Thema gelten für SharePoint 2010-und SharePoint 2013-Lösungen, die in Visual Studio erstellt wurden.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- [Erstellen eines Funktions Empfängers](#create-a-feature-receiver)

- [Dem Funktionsempfänger Code hinzufügen](#add-code-to-the-feature-receiver)

- [Testen des Projekts](#test-the-project)

- [Sammeln Sie IntelliTrace-Daten mithilfe von Microsoft Monitoring Agent.](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Die SharePoint-Lösung debuggen und korrigieren](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von Windows und SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Erstellen eines Funktions Empfängers

Erstellen Sie zunächst ein leeres SharePoint-Projekt mit einem Funktionsempfänger.

1. Erstellen Sie ein SharePoint 2010-oder SharePoint 2013-Projektmappenprojekt, und nennen Sie es **intellitracetest**.

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt, in dem Sie sowohl die SharePoint-Website für das Projekt als auch die Vertrauens Ebene der Projekt Mappe angeben können.

2. Wählen Sie das Optionsfeld **als Farm Lösung** bereitstellen aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

     IntelliTrace kann nur für Farmlösungen verwendet werden.

3. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Knoten **Features** , und wählen Sie dann **Feature hinzufügen** aus.

     *Feature1. Feature* wird angezeigt.

4. Öffnen Sie das Kontextmenü für Feature1. Feature, und wählen Sie dann **Ereignis Empfänger hinzufügen** aus, um der Funktion ein Codemodul hinzuzufügen.

## <a name="add-code-to-the-feature-receiver"></a>Hinzufügen von Code zum Funktions Empfänger

Fügen Sie anschließend zwei Methoden im Funktionsempfänger Code hinzu: `FeatureActivated` und `FeatureDeactivating`. Diese Methoden lösen immer dann aus, wenn eine Funktion in SharePoint aktiviert bzw. deaktiviert wird.

1. Fügen Sie am Anfang der `Feature1EventReceiver`-Klasse den folgenden Code hinzu, um Variablen zu deklarieren, mit denen die SharePoint-Website und -Unterwebsite angegeben werden:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Ersetzen Sie die `FeatureActivated`-Methode durch den folgenden Code:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
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
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Ersetzen Sie die `FeatureDeactivating`-Methode durch den folgenden Code:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>Testen des Projekts

Wenn dem Funktionsempfänger der Code hinzugefügt wurde und der Datensammler ausgeführt wird, stellen Sie die SharePoint-Lösung bereit. Führen Sie sie aus, um die ordnungsgemäße Funktion zu testen.

> [!IMPORTANT]
> In diesem Beispiel wird ein Fehler im Ereignishandler „FeatureDeactivating“ ausgelöst. Im weiteren Verlauf dieser exemplarischen Vorgehensweise suchen Sie diesen Fehler anhand der vom Datensammler erstellten .iTrace-Datei.

1. Stellen Sie die Lösung für SharePoint bereit, und öffnen Sie die SharePoint-Website in einem Browser.

     Die Funktion wird automatisch aktiviert. Dadurch wird bewirkt, dass der Funktionsempfänger eine Ankündigung und eine Aufgabe hinzufügt.

2. Zeigen Sie den Inhalt der Listen mit Ankündigungen und Aufgaben an.

     Die Ankündigungsliste sollte eine neue Ankündigung mit dem Namen **aktivierte Funktion: IntelliTraceTest_Feature1 enthalten**, und die Aufgabenliste sollte eine neue Aufgabe mit dem Namen " **Feature deaktivieren: IntelliTraceTest_Feature1**" aufweisen. Wenn eines der Elemente fehlt, überprüfen Sie, ob die Funktion aktiviert ist. Aktivieren Sie sie andernfalls.

3. Deaktivieren Sie die Funktion, indem Sie die folgenden Schritte ausführen:

   1. Wählen Sie im Menü **Website Aktionen** in SharePoint die Option **Website Einstellungen** aus.

   2. Wählen Sie unter **Website Aktionen** den Link **Website Features verwalten** aus.

   3. Wählen Sie neben **intellitracetest Feature1** die Schaltfläche **Deaktivieren** aus.

   4. Wählen Sie auf der Seite Warnung den Link **Diese Funktion deaktivieren** aus.

      Vom Ereignishandler „FeatureDeactivating()“ wird ein Fehler ausgelöst.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Sammeln von IntelliTrace-Daten mithilfe von Microsoft Monitoring Agent

Wenn Sie Microsoft Monitoring Agent auf dem System installieren, auf dem SharePoint ausgeführt wird, können Sie SharePoint-Lösungen Debuggen, indem Sie Daten verwenden, die spezifischer als die von IntelliTrace zurückgegebenen generischen Informationen sind. Der Agent funktioniert außerhalb von Visual Studio, indem PowerShell-Cmdlets verwendet werden, um Debuginformationen zu sammeln, während die SharePoint-Lösung ausgeführt wird.

> [!NOTE]
> Die Konfigurationsinformationen in diesem Abschnitt beziehen sich auf dieses Beispiel. Weitere Informationen zu anderen Konfigurationsoptionen finden Sie unter [Verwenden des eigenständigen IntelliTrace-Sammlers](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. Richten Sie auf dem Computer, auf dem SharePoint ausgeführt wird, Microsoft Monitoring Agent ein, [und beginnen Sie mit der Überwachung Ihrer Lösung](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Deaktivieren Sie die Funktion:

   1. Wählen Sie im Menü **Website Aktionen** in SharePoint die Option **Website Einstellungen** aus.

   2. Wählen Sie unter **Website Aktionen** den Link **Website Features verwalten** aus.

   3. Wählen Sie neben **intellitracetest Feature1** die Schaltfläche **Deaktivieren** aus.

   4. Wählen Sie auf der Seite Warnung den Link **Diese Funktion deaktivieren** aus.

      Ein Fehler tritt auf (in diesem Fall aufgrund des Fehlers im Ereignishandler "FeatureDeactivating()").

3. Führen Sie im PowerShell-Fenster den Befehl " [beendet-webapplicationmonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) " aus, um die itrace-Datei zu erstellen, die Überwachung anzuhalten und die SharePoint-Lösung neu zu starten.

     "" **Beendet-webapplicationmonitoring***" \<SharePointSite> \\<sharepointappname \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Debuggen und korrigieren der SharePoint-Lösung

Jetzt können Sie die IntelliTrace-Protokolldatei in Visual Studio anzeigen, um den Fehler in der SharePoint-Lösung zu suchen und zu beheben.

1. Öffnen Sie im Ordner "\IntelliTraceLogs" die ITRACE-Datei-Datei in Visual Studio.

     Die Seite **IntelliTrace-Zusammenfassung** wird angezeigt. Da der Fehler nicht behandelt wurde, wird eine SharePoint-Korrelations-ID (eine GUID) im Bereich "nicht behandelte Ausnahme" des **Analyse** Abschnitts angezeigt. Wählen Sie die Schaltfläche " **CallStack** " aus, wenn Sie die Fehlermeldung anzeigen möchten, in der der Fehler auftrat.

2. Wählen Sie die Schaltfläche **Ausnahme Debuggen** .

     Wenn Sie dazu aufgefordert werden, laden Sie Symboldateien. Im **IntelliTrace** -Fenster wird die Ausnahme als "ausgelöst: Schwerwiegender Fehler aufgetreten!" hervorgehoben.

     Wählen Sie die Ausnahme im IntelliTrace-Fenster aus, um den Code mit dem Fehler anzuzeigen.

3. Beheben Sie den Fehler, indem Sie die SharePoint-Lösung öffnen und dann die **throw** -Anweisung am Anfang der Funktion "featueinlösen aktivieren ()" auskommentieren oder entfernen.

4. Erstellen Sie die Projektmappe in Visual Studio neu, und stellen Sie sie dann erneut für SharePoint bereit.

5. Deaktivieren Sie die Funktion, indem Sie die folgenden Schritte ausführen:

    1. Wählen Sie im Menü **Website Aktionen** in SharePoint die Option **Website Einstellungen** aus.

    2. Wählen Sie unter **Website Aktionen** den Link **Website Features verwalten** aus.

    3. Wählen Sie neben **intellitracetest Feature1** die Schaltfläche **Deaktivieren** aus.

    4. Wählen Sie auf der Seite Warnung den Link **Diese Funktion deaktivieren** aus.

6. Öffnen Sie die Aufgabenliste, und überprüfen Sie, ob der **Status** Wert der Aufgabe "deaktivieren" den Wert "abgeschlossen" hat und der Wert für " **% Complete** " 100% beträgt.

     Der Code wird jetzt ordnungsgemäß ausgeführt.

## <a name="see-also"></a>Siehe auch

- [Prüfen und Debuggen von SharePoint-Code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Exemplarische Vorgehensweise: Überprüfen von SharePoint-Code mithilfe von Komponenten Tests](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))