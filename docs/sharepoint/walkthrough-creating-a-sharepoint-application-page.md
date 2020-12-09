---
title: 'Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite | Microsoft-Dokumentation'
description: Erstellen Sie in dieser exemplarischen Vorgehensweise eine Anwendungsseite (spezialisierte Form einer ASP.NET-Seite), und Debuggen Sie Sie dann mithilfe einer lokalen SharePoint-Website.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95addb145312de85a3525c228297e7ff9636ea0d
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914880"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite

Eine Anwendungsseite ist eine spezielle Form einer ASP.NET-Seite. Anwendungsseiten enthalten Inhalt, der mit einer SharePoint-Masterseite zusammengeführt wird. Weitere Informationen finden Sie unter [Erstellen von Anwendungs Seiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie eine Anwendungsseite erstellen und sie dann mithilfe einer lokalen SharePoint-Website debuggen. Auf dieser Seite werden alle Elemente angezeigt, die die einzelnen Benutzer auf allen Websites der Serverfarm erstellt oder geändert haben.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines SharePoint-Projekts.
- Hinzufügen einer Anwendungsseite zum SharePoint-Projekt.
- Hinzufügen von ASP.NET-Steuerelementen zur Anwendungsseite.
- Hinzufügen von Code hinter den ASP.NET-Steuerelementen.
- Testen der Anwendungsseite.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen

- Unterstützte Editionen von Windows und SharePoint.

## <a name="create-a-sharepoint-project"></a>Erstellen eines SharePoint-Projekts

Erstellen Sie zunächst ein **leeres SharePoint-Projekt**. Später fügen Sie diesem Projekt ein **Anwendungs Seiten** Element hinzu.

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Öffnen Sie das Dialogfeld **Neues Projekt** , erweitern Sie den Knoten **Office/SharePoint** unter der Sprache, die Sie verwenden möchten, und wählen Sie dann den Knoten **SharePoint-Lösungen** aus.

3. Wählen Sie im Bereich **installierte Vorlagen von Visual Studio** die **Projektvorlage SharePoint 2010-Empty** aus. Nennen Sie das Projekt **mysharepointproject**, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt. Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe auswählen.

4. Wählen Sie das Optionsfeld **als Farm Lösung** bereitstellen, und klicken Sie dann auf die Schaltfläche **Fertig** stellen, um die standardmäßige lokale SharePoint-Website zu akzeptieren.

## <a name="create-an-application-page"></a>Erstellen einer Anwendungsseite

Fügen Sie dem Projekt ein **Anwendungs Seiten** Element hinzu, um eine Anwendungsseite zu erstellen.

1. Wählen Sie in **Projektmappen-Explorer** das Projekt **mysharepointproject** aus.

2. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

3. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die **Anwendungsseite (nur Farm Lösung** ) aus.

4. Nennen Sie die Seite **searchitems**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Der Visual Web Developer-Designer zeigt die Anwendungsseite in der **Quell** Ansicht an, wo Sie die HTML-Elemente der Seite sehen können. Der Designer zeigt das Markup für mehrere <xref:System.Web.UI.WebControls.Content>-Steuerelemente an. Jedes Steuerelement ist einem <xref:System.Web.UI.WebControls.ContentPlaceHolder>-Steuerelement zugeordnet, das auf der standardmäßigen Anwendungsmasterseite definiert ist.

## <a name="design-the-layout-of-the-application-page"></a>Entwerfen des Layouts der Anwendungsseite

Das Element Anwendungsseite ermöglicht Ihnen die Verwendung eines Designers, um der Anwendungsseite ASP.NET-Steuerelemente hinzuzufügen. Dieser Designer ist mit dem in Visual Web Developer verwendeten Designer identisch. Fügen Sie der **Quell** Ansicht des Designers eine Bezeichnung, eine Optionsfeld Liste und eine Tabelle hinzu, und legen Sie dann die Eigenschaften genauso fest wie beim Entwerfen einer beliebigen Standard-ASP.NET-Seite.

1. Wählen Sie in der Menüleiste **View**  >  **Toolbox** anzeigen aus.

2. Führen Sie im Knoten Standard der **Toolbox** einen der folgenden Schritte aus:

    - Öffnen **Sie das Kontext** Menü für das Bezeichnungs Element, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für die Zeile unter dem Content-Steuerelement **PlaceHolderMain** im Designer, und wählen Sie dann **Einfügen** aus.

    - Ziehen Sie das **Label** -Element aus der **Toolbox** auf den Text des Inhalts Steuer Elements **PlaceHolderMain** .

3. Wiederholen Sie den vorherigen Schritt, um ein **Dropdown List** -Element und ein **Tabellen** Element zum **PlaceHolderMain** -Inhalts Steuerelement hinzuzufügen.

4. Ändern Sie im Designer den Wert des- `Text` Attributs des Label-Steuer Elements, um **alle Elemente anzuzeigen**.

5. Oder ersetzen Sie im Designer das `<asp:DropDownList>`-Element durch folgendes XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Behandeln der Ereignisse von Steuerelementen auf der Seite

Behandeln Sie Steuerelemente auf einer Anwendungsseite ebenso wie bei einer ASP.NET-Seite. In diesem Verfahren behandeln Sie das `SelectedIndexChanged`-Ereignis der Dropdownliste.

1. Wählen Sie im Menü **Ansicht** die Option **Code** aus.

     Die Codedatei für die Anwendungsseite wird im Code-Editor geöffnet.

2. Füge der `SearchItems`-Klasse die folgende Methode hinzu. In diesem Code wird das <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged>-Ereignis der <xref:System.Web.UI.WebControls.DropDownList> behandelt, indem eine Methode aufgerufen wird, die Sie später in dieser exemplarischen Vorgehensweise erstellen.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Fügen Sie am Anfang der Codedatei für die Anwendungsseite die folgenden Anweisungen hinzu.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Füge der `SearchItems`-Klasse die folgende Methode hinzu. Diese Methode durchläuft alle Websites der Serverfarm und sucht nach Elementen, die vom aktuellen Benutzer erstellt oder geändert wurden.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Füge der `SearchItems`-Klasse die folgende Methode hinzu. Diese Methode zeigt Elemente an, die vom aktuellen Benutzer in der Tabelle erstellt oder geändert wurden.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Testen der Anwendungsseite

Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet, und die Anwendungsseite wird angezeigt.

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für die Anwendungsseite, und wählen Sie dann **als Start Element festlegen** aus.

2. Drücken Sie die Taste **F5**.

     Die SharePoint-Website wird geöffnet.

3. Wählen Sie auf der Seite Anwendung die Option **geändert von mir** aus.

     Die Anwendungsseite wird aktualisiert und zeigt alle Elemente an, die Sie auf allen Websites der Serverfarm geändert haben.

4. Wählen Sie auf der Seite Anwendung die Option **von mir erstellt** in der Liste aus.

     Die Anwendungsseite wird aktualisiert und zeigt alle Elemente an, die Sie auf allen Websites der Serverfarm erstellt haben.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SharePoint-Anwendungs Seiten finden Sie unter [Erstellen von Anwendungs Seiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Weitere Informationen zum Entwerfen von SharePoint-Seiteninhalten mit dem Visual Web Designer finden Sie in folgenden Themen:

- [Erstellen Sie Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Erstellen Sie wiederverwendbare Steuerelemente für Webparts oder Anwendungs Seiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Weitere Informationen

Vorgehens [Weise: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md) 
 [Anwendung_layouts Seitentyp](/previous-versions/office/aa979604(v=office.14))
