---
title: 'Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts für eine Website Definition | Microsoft-Dokumentation'
description: In dieser SharePoint-exemplarischen Vorgehensweise erfahren Sie, wie Sie eine einfache Site Definition erstellen, die ein visuelles Webpart mit einigen Steuerelementen enthält.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0411f027b105622d806e123bd80f38c4b05281ca
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913853"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts für eine Website Definition
  In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie eine grundlegende Site Definition erstellen, die ein visuelles Webpart mit einigen Steuerelementen enthält. Aus Gründen der Übersichtlichkeit hat das visuelle Webpart, das Sie erstellen, nur wenige Steuerelemente. Sie können jedoch anspruchsvollere SharePoint-Website Definitionen erstellen, die mehr Funktionalität enthalten.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer Site Definition mithilfe der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projektvorlage.

- Erstellen einer SharePoint-Website mithilfe einer Website Definition in SharePoint.

- Der Projekt Mappe wird ein visuelles Webpart hinzugefügt.

- Anpassen der Seite "default. aspx" der Website, indem Sie das neue visuelle Webpart hinzufügen.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von Microsoft Windows und SharePoint. Weitere Informationen finden Sie unter Anforderungen für die Entwicklung von SharePoint-Lösungen.

- Visual Studio.

## <a name="create-a-site-definition-solution"></a>Erstellen einer Site Definitions Lösung
 Erstellen Sie zuerst das Website Definitions Projekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>So erstellen Sie ein Website Definitions Projekt

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wenn die IDE für die Verwendung Visual Basic Entwicklungseinstellungen festgelegt ist, wählen Sie in der Menüleiste **Datei**  >  **neu Projekt** aus.

    Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Erweitern Sie den Knoten **Visual c#** oder den Knoten **Visual Basic** , erweitern Sie den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie in der Liste **Vorlagen** die **SharePoint 2010-Projekt** Vorlage aus.

4. Geben Sie im Feld **Name den Namen** **testsitedef** ein, und klicken Sie dann auf die Schaltfläche **OK** .

    Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

5. Geben Sie auf der Seite **Standort und Sicherheitsebene für Debugging angeben** die URL für die SharePoint-Website ein, auf der Sie die Website Definition debuggen möchten, oder verwenden Sie den Standard Speicherort (http://<em>System Name</em>/).

6. Wählen Sie im Abschnitt **Was ist die Vertrauens Ebene für diese SharePoint-Lösung?** das Optionsfeld **als Farm Lösung** bereitstellen aus.

    Alle Website Definitions Projekte müssen als Farm Lösungen bereitgestellt werden. Weitere Informationen zu Sandkasten Lösungen im Vergleich zu Farm Lösungen finden Sie unter [Überlegungen zu Sandkasten](../sharepoint/sandboxed-solution-considerations.md)Lösungen.

7. Klicken Sie auf die Schaltfläche **Fertig stellen**.

    Das Projekt wird in **Projektmappen-Explorer** angezeigt.

8. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten aus, und klicken Sie dann in der Menüleiste auf **Projekt**  >  **Neues Element hinzufügen**.

9. Erweitern Sie unter **Visual c#** oder **Visual Basic** den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

10. Wählen Sie im Bereich **Vorlagen** die Vorlage **Site Definition** aus, belassen Sie **Name** den Namen **SiteDefinition1**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

## <a name="create-a-visual-web-part"></a>Erstellen eines visuellen Webparts
 Erstellen Sie als nächstes ein visuelles Webpart, das auf der Hauptseite der Website Definition angezeigt wird.

#### <a name="to-create-a-visual-web-part"></a>So erstellen Sie ein visuelles Webpart

1. Wählen Sie in **Projektmappen-Explorer** die Schaltfläche **alle Dateien anzeigen** aus.

2. Wählen Sie den **SiteDefinition1** -Projekt Knoten aus, und wählen Sie dann in der Menüleiste **Projekt**  >  **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

3. Erweitern Sie den Knoten **Visual c#** oder den Knoten **Visual Basic** , erweitern Sie den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

4. Wählen Sie in der Liste der Vorlagen die Vorlage **visuelles Webpart** aus, behalten Sie den Standardnamen VisualWebPart1 bei, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Die Datei " *VisualWebPart1. ascx* " wird geöffnet.

5. Fügen Sie am unteren Rand von *VisualWebPart1. ascx* das folgende Markup hinzu, um dem Formular drei Steuerelemente hinzuzufügen: ein Textfeld, eine Schaltfläche und eine Bezeichnung:

    ```aspx-csharp
    <table>
      <tr>
        <td>
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>
        </td>
        <td>
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>
        </td>
        <td>
          <asp:Label runat="server" ID="lblName"></asp:Label>
        </td>
      </tr>
    </table>
    ```

6. Öffnen Sie unter *VisualWebPart1. ascx* die Datei *VisualWebPart1.ascx.cs* (für [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ) oder *VisualWebPart1. ascx. vb* (für [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), und fügen Sie dann den folgenden Code hinzu:

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     Dieser Code fügt Funktionen für den Schaltflächen Klick des Webparts hinzu.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Hinzufügen des visuellen Webparts zur Standard-ASPX-Seite
 Fügen Sie als nächstes das visuelle Webpart zur Standard-ASPX-Seite der Site Definition hinzu.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>So fügen Sie der Standard-ASPX-Seite ein visuelles Webpart hinzu

1. Öffnen Sie die Seite Default. aspx, und fügen Sie dann unter dem-Tag die folgende Zeile hinzu `WebPartPages` :

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Diese Zeile verknüpft den Namen mywebpartcontrols mit dem Webpart und seinem Code. Der *Namespace* -Parameter entspricht dem Namespace, der in der *VisualWebPart1. ascx* -Codedatei verwendet wird.

2. Ersetzen Sie nach dem `</asp:Content>` -Element den gesamten `ContentPlaceHolderId="PlaceHolderMain"` Abschnitt und seinen Inhalt durch den folgenden Code:

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Mit diesem Code wird ein Verweis auf das visuelle Webpart erstellt, das Sie zuvor erstellt haben.

3. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Knoten **SiteDefinition1** , und wählen Sie dann **als Start Element festlegen** aus.

## <a name="deploy-and-run-the-site-definition-solution"></a>Bereitstellen und Ausführen der Site Definitions Lösung
 Als Nächstes stellen Sie das Projekt in SharePoint bereit und führen dann das Projekt aus.

#### <a name="to-deploy-and-run-the-site-definition"></a>So stellen Sie die Websitedefinition bereit und führen sie aus

- Wählen Sie in der Menüleiste die Option **Build** bereitstellen  >  **testsitedef** aus.

- Drücken Sie die Taste **F5**.

     Visual Studio kompiliert den Code, fügt seine Features hinzu, packt alle Dateien in einer SharePoint-Lösungs Datei (WSP) und stellt die wsp-Datei für SharePoint Server bereit. SharePoint installiert dann die Dateien und aktiviert dann die Funktionen.

## <a name="create-a-site-based-on-the-site-definition"></a>Erstellen einer Website basierend auf der Site Definition
 Erstellen Sie als nächstes eine Website mithilfe der neuen Site Definition.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>So erstellen Sie eine Website mithilfe der Site Definition

1. Auf der SharePoint-Website wird die Seite neue SharePoint-Site angezeigt.

2. Geben Sie im Abschnitt **Titel und Beschreibung** **meine neue Website** für den Titel und eine Beschreibung der Site ein.

3. Geben Sie im Abschnitt **Website Adresse** im Feld **URL-Name den Namen** **mynewsite** ein.

4. Wählen Sie im Abschnitt **Vorlage** die Registerkarte **SharePoint-Anpassungen** aus.

5. Wählen Sie in der Liste **Vorlage auswählen** die Option **SiteDefinition1** aus.

6. Überlassen Sie die anderen Einstellungen die Standardwerte, und wählen Sie dann die Schaltfläche **Erstellen** aus.

     Die neue Website wird angezeigt.

## <a name="test-the-new-site"></a>Testen der neuen Website
 Testen Sie als nächstes die neue Website, um zu überprüfen, ob Sie ordnungsgemäß funktioniert.

#### <a name="to-test-the-new-site"></a>So testen Sie den neuen Standort

- Geben Sie auf der ASPX-Standardseite Text ein, und wählen Sie dann die Schaltfläche Bezeichnungs **Text ändern** neben dem Textfeld aus.

     Der Text wird in der Bezeichnung auf der rechten Seite der Schaltfläche angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
