---
title: Erstellen eines Silverlight-Webparts, das odata für SharePoint anzeigt
titleSuffix: ''
description: Erstellen Sie ein Silverlight-Webpart, das odata für SharePoint anzeigt. Passen Sie die Silverlight-Anwendung an, und ändern und testen Sie das Silverlight-WebPart.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee35ecc9cfa49f445e93677df9d2917150bc1e74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847829"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das odata für SharePoint anzeigt
  SharePoint 2010 macht seine Listen Daten mithilfe von odata verfügbar. In SharePoint wird der odata-Dienst vom Rest-Dienst listData. svc implementiert. Diese exemplarische Vorgehensweise veranschaulicht, wie ein SharePoint-Webpart erstellt wird, das eine Silverlight-Anwendung hostet. Die Silverlight-Anwendung zeigt die SharePoint-Ankündigungs Listen Informationen mithilfe von "listData. svc" an. Weitere Informationen finden Sie unter [SharePoint Foundation-Rest-Schnittstelle](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) und [Open Data Protocol](https://www.odata.org/).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von Microsoft Windows und SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Erstellen einer Silverlight-Anwendung und eines Silverlight-Webparts
 Erstellen Sie zunächst in Visual Studio eine Silverlight-Anwendung. Die Silverlight-Anwendung ruft Daten mithilfe des listData. svc-Dienes aus der SharePoint-Ankündigungsliste ab.

> [!NOTE]
> Keine Versionen von Silverlight vor 4,0 unterstützen die erforderlichen Schnittstellen für Verweise auf SharePoint-Listen Daten.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>So erstellen Sie eine Silverlight-Anwendung und ein Silverlight-Webpart

1. Wählen Sie in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus, um das Dialogfeld **Neues Projekt** anzuzeigen.

2. Erweitern Sie den **SharePoint** -Knoten entweder unter **Visual c#** oder **Visual Basic**, und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie im Bereich Vorlagen die Vorlage **SharePoint 2010 Silverlight-Webpart** aus.

4. Geben Sie im Feld **Name die Bezeichnung** **slwebparttest** ein, und klicken Sie dann auf die Schaltfläche **OK** .

    Das Dialogfeld **Anpassungs-Assistent für SharePoint** wird angezeigt.

5. Geben Sie auf der Seite **Standort und Sicherheitsebene für Debugging angeben** die URL für die SharePoint-Serversite ein, auf der Sie die Website Definition debuggen möchten, oder verwenden Sie den Standard Speicherort (http://<em>Systemname</em>/).

6. Wählen Sie im Abschnitt **Was ist die Vertrauens Ebene für diese SharePoint-Lösung?** das Optionsfeld **als Farm Lösung** bereitstellen aus.

    Obwohl in diesem Beispiel eine Farm Lösung verwendet wird, können Silverlight-webpartprojekte entweder als Farm-oder als Sandkasten Lösungen bereitgestellt werden. Weitere Informationen zu Sandkasten Lösungen und Farm Lösungen finden Sie unter [Überlegungen zu Sandkasten](../sharepoint/sandboxed-solution-considerations.md)Lösungen.

7. Wählen Sie im Abschnitt **wie möchten Sie den Silverlight-Webpart** der Seite " **Silverlight-Konfigurationsinformationen angeben** " die Option **neues Silverlight-Projekt erstellen aus, und ordnen Sie es dem Optionsfeld Webpart** zu.

8. Ändern Sie den **Namen** in **slapplication**, legen Sie für **Sprache** entweder **Visual Basic** oder **Visual c#** fest, und legen Sie dann **Silverlight-Version** auf **Silverlight 4,0** fest.

9. Klicken Sie auf die Schaltfläche **Fertig stellen**. Die Projekte werden in **Projektmappen-Explorer** angezeigt.

     Die Projekt Mappe enthält zwei Projekte: eine Silverlight-Anwendung und ein Silverlight-WebPart. Die Silverlight-Anwendung ruft die Listen Daten aus SharePoint ab und zeigt Sie an, und der Silverlight-Webpart hostet die Silverlight-Anwendung, sodass Sie Sie in SharePoint anzeigen können.

## <a name="customize-the-silverlight-application"></a>Anpassen der Silverlight-Anwendung
 Fügen Sie der Silverlight-Anwendung Code und Entwurfs Elemente hinzu.

#### <a name="to-customize-the-silverlight-application"></a>So passen Sie die Silverlight-Anwendung an

1. Fügen Sie in der Silverlight-Anwendung einen Assemblyverweis auf System. Windows. Data hinzu. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen oder Entfernen von verweisen mithilfe des Dialog Felds "Verweis hinzufügen](/previous-versions/wkze6zky(v=vs.140))".

2. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für **Verweise**, und wählen Sie dann **Dienstverweis hinzufügen** aus.

    > [!NOTE]
    > Wenn Sie Visual Basic verwenden, müssen Sie oben in **Projektmappen-Explorer** das Symbol **alle Dateien anzeigen** auswählen, um den Knoten **Verweise** anzuzeigen.

3. Geben Sie im Dialogfeld **Dienstverweis hinzufügen** in das Feld Adresse die URL Ihrer SharePoint-Website ein, z **http://MySPSite** . b., und klicken Sie dann auf die Schaltfläche **Gehe** zu.

     Wenn Silverlight den SharePoint-odata-Dienst "listData. svc" eingibt, wird die Adresse durch die vollständige Dienst-URL ersetzt. In diesem Beispiel http://myserver wird zu http://myserver/_vti_bin/ListData.svc .

4. Wählen Sie die Schaltfläche **OK** aus, um dem Projekt den Dienst Verweis hinzuzufügen, und verwenden Sie den Standard Dienstnamen ServiceReference1.

5. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

6. Fügen Sie dem Projekt eine neue Datenquelle auf Grundlage des SharePoint-Dienstanbieter hinzu. Wählen Sie hierzu in der Menüleiste die Option   >  **Weitere Windows**-  >  **Datenquellen** anzeigen aus.

     Das Fenster **Datenquellen** zeigt alle verfügbaren SharePoint-Listen Daten an, z. b. Tasks, Ankündigungen und Kalender.

7. Fügen Sie der Silverlight-Anwendung die Daten der Ankündigungsliste hinzu. Sie können "Ankündigungen" aus dem **Datenquellen** Fenster auf den Silverlight-Designer ziehen.

     Dadurch wird ein Raster Steuerelement erstellt, das an die Ankündigungsliste der SharePoint-Website gebunden ist.

8. Ändern Sie die Größe des Raster Steuer Elements an die Silverlight-Seite.

9. Fügen Sie in der MainPage. XAML-Codedatei (*MainPage.XAML.cs* für Visual c# oder *MainPage. XAML. vb* für Visual Basic) die folgenden Namespace Verweise hinzu.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. Fügen Sie am Anfang der Klasse die folgenden Variablen Deklarationen hinzu.

    ```vb
    Private context As TeamSiteDataContext
    Private myCollectionViewSource As CollectionViewSource
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()
    ```

    ```csharp
    private TeamSiteDataContext context;
    private CollectionViewSource myCollectionViewSource;
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();
    ```

11. Ersetzen Sie die `UserControl_Loaded` Prozedur durch Folgendes:

    ```vb
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)
        ' The URL for the OData service.
        ' Replace <server name> in the next line with the name of your SharePoint server.
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))

        ' Do not load your data at design time.
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then
            'Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)
            announcements.LoadAsync(context.Announcements)
        End If
    End Sub
    ```

    ```csharp
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)
    {
        // The URL for the OData service.
        // Replace <server name> in the next line with the name of your
        // SharePoint server.
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));

        // Do not load your data at design time.
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))
        {
            //Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);
            announcements.LoadAsync(context.Announcements);
        }
    }
    ```

     Stellen Sie sicher, dass Sie den Platzhalter "Server *Name* " durch den Namen des Servers ersetzen, auf dem SharePoint ausgeführt wird.

12. Fügen Sie die folgende Fehler Behandlungs Prozedur hinzu.

    ```vb
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)
        ' Handle any errors.
        If e.[Error] Is Nothing Then
            myCollectionViewSource.Source = announcements
        Else
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))
        End If
    End Sub

    ```

    ```csharp
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)
    {
        // Handle any errors.
        if (e.Error == null)
        {
            myCollectionViewSource.Source = announcements;
        }
        else
        {
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));
        }
    }
    ```

## <a name="modify-the-silverlight-web-part"></a>Ändern des Silverlight-Webparts
 Ändern Sie eine Eigenschaft im Silverlight-Webpartprojekt, um das Silverlight-Debugging zu aktivieren.

#### <a name="to-modify-the-silverlight-web-part"></a>So ändern Sie das Silverlight-Webpart

1. Öffnen Sie das Kontextmenü für das Silverlight-**Webpartprojekt (slwebparttest**), und wählen Sie dann **Eigenschaften** aus.

2. Wählen Sie im Fenster **Eigenschaften** die Registerkarte **SharePoint** aus.

3. Wenn Sie nicht bereits ausgewählt ist, aktivieren Sie das Kontrollkästchen **Silverlight-Debugging aktivieren (anstelle von Skript Debugging)** .

4. Speichern Sie das Projekt.

## <a name="test-the-silverlight-web-part"></a>Testen des Silverlight-Webparts
 Testen Sie das neue Silverlight-Webpart in SharePoint, um sicherzustellen, dass die SharePoint-Listen Daten ordnungsgemäß angezeigt werden.

#### <a name="to-test-the-silverlight-web-part"></a>So testen Sie das Silverlight-Webpart

1. Drücken Sie die Taste **F5** , um die SharePoint-Lösung zu erstellen und auszuführen.

2. Wählen Sie in SharePoint im Menü **Website Aktionen** die Option **neue Seite** aus.

3. Geben Sie im Dialogfeld **neue Seite** einen Titel ein, z. b. **SL Webpart Test**, und wählen Sie dann die Schaltfläche **Erstellen** aus.

4. Wählen Sie im Seiten-Designer auf der Registerkarte **Bearbeitungs Tools** die Option **Einfügen** aus.

5. Wählen Sie auf der Registerkarten Leiste **Webpart** aus.

6. Wählen Sie im Feld **Kategorien** den **benutzerdefinierten** Ordner aus.

7. Wählen Sie in der Liste **Webparts** den Silverlight-Webpart aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** , um das Webpart dem Designer hinzuzufügen.

8. Nachdem Sie alle Ergänzungen auf der gewünschten Webseite vorgenommen haben, wählen Sie die Registerkarte **Seite** aus, und klicken Sie dann auf der Symbolleiste auf die Schaltfläche **& schließen speichern** .

     Das Silverlight-Webpart sollte nun Ankündigungs Daten von der SharePoint-Website anzeigen. Standardmäßig wird die Seite in der Liste der Website Seiten in SharePoint gespeichert.

    > [!NOTE]
    > Beim Zugriff auf Daten in Silverlight über Domänen hinweg schützt Silverlight gegen Sicherheitsrisiken, die verwendet werden können, um Webanwendungen auszunutzen. Wenn beim Zugriff auf Remote Daten in Silverlight Probleme auftreten, finden Sie weitere Informationen unter [Bereitstellen eines Dienstes über Domänen Grenzen hinweg](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95)).

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungs Paketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)