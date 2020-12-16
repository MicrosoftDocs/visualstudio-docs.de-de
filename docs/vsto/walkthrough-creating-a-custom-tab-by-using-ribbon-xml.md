---
title: 'Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML'
description: Erfahren Sie, wie Sie der Registerkarte "Add-Ins" Schaltflächen hinzufügen und Microsoft Word mithilfe von Menüband (XML) automatisieren können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e81d20dc179df76b759223c1460ca13bfceb5706
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524883"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine benutzerdefinierte Registerkarte des Menübands mithilfe des Elements **Menüband (XML)** erstellt wird.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen von Schaltflächen zur Registerkarte " **Add-ins** ". Die Registerkarte **Add-ins** ist die Standard Registerkarte, die in der Menüband-XML-Datei definiert ist.

- Automatisieren von Microsoft Office Word mithilfe der Schaltflächen auf der Registerkarte **Add-ins** .

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Erstellen des Projekts
 Der erste Schritt besteht im Erstellen eines VSTO-Add-In-Projekts für Word. Die Registerkarte **Add-ins** wird später in diesem Dokument angepasst.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen **Sie ein Word-Add-in-** Projekt mit dem Namen **MyRibbonAddIn**.

     Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Öffnet die Codedatei **ThisAddIn.cs** oder **ThisAddIn. vb** und fügt das Projekt **MyRibbonAddIn** **Projektmappen-Explorer** hinzu.

## <a name="create-the-vsto-add-ins-tab"></a>Erstellen der Registerkarte "VSTO-Add-Ins"
 Fügen Sie dem Projekt ein **Menüband (XML)** -Element hinzu, um die Registerkarte **Add-ins** zu erstellen. Später in dieser exemplarischen Vorgehensweise werden Sie dieser Registerkarte einige Schaltflächen hinzufügen.

### <a name="to-create-the-add-ins-tab"></a>So erstellen Sie die Registerkarte "Add-Ins"

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband (XML)** aus.

3. Ändern Sie den Namen des neuen Menübands in **MyRibbon**, und klicken Sie dann auf **Hinzufügen**.

     Die Datei **MyRibbon.cs** oder **MyRibbon. vb** wird im Designer geöffnet. Eine XML-Datei mit dem Namen **MyRibbon.xml** wird ebenfalls dem Projekt hinzugefügt.

4. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **ThisAddIn.cs** oder **ThisAddIn. vb**, und klicken Sie dann auf **Code anzeigen**.

5. Fügen Sie der Klasse **ThisAddin** den folgenden Code hinzu. Mit diesem Code wird die `CreateRibbonExtensibilityObject`-Methode überschrieben und der Office-Anwendung die Menüband-XML-Klasse zurückgegeben.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **MyRibbonAddIn** , und klicken Sie dann auf **Erstellen**. Vergewissern Sie sich, dass das Projekt ohne Fehler erstellt wurde.

## <a name="add-buttons-to-the-add-ins-tab"></a>Hinzufügen von Schaltflächen zur Registerkarte Add-ins
 Das Ziel dieses VSTO-Add-Ins besteht darin, Benutzern eine Möglichkeit bereitzustellen, dem aktiven Dokument Textbausteine und eine bestimmte Tabelle hinzuzufügen. Zum Bereitstellen der Benutzeroberfläche fügen Sie der Registerkarte **Add-ins** zwei Schaltflächen hinzu, indem Sie die Menüband-XML-Datei ändern. Später in dieser exemplarischen Vorgehensweise definieren Sie Rückrufmethoden für die Schaltflächen. Weitere Informationen zur Menüband-XML-Datei finden Sie unter [Menüband-XML](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>So fügen Sie der Registerkarte Add-ins Schaltflächen hinzu

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **MyRibbon.xml** und klicken Sie dann auf **Öffnen**.

2. Ersetzen Sie den Inhalt des **Register** Karten Elements durch den folgenden XML-Code. Mit diesem XML wird die Bezeichnung der Standard Steuerelement Gruppe in **Content** geändert, und es werden zwei neue Schaltflächen mit den Bezeichnungen **Text einfügen** und **Tabelle einfügen** hinzugefügt.

    ```xml
    <tab idMso="TabAddIns">
        <group id="ContentGroup" label="Content">
            <button id="textButton" label="Insert Text"
                 screentip="Text" onAction="OnTextButton"
                 supertip="Inserts text at the cursor location."/>
            <button id="tableButton" label="Insert Table"
                 screentip="Table" onAction="OnTableButton"
                 supertip="Inserts a table at the cursor location."/>
        </group>
    </tab>
    ```

## <a name="automate-the-document-by-using-the-buttons"></a>Automatisieren des Dokuments mithilfe der Schaltflächen
 Sie müssen `onAction` Rückruf Methoden für die Schaltflächen **Text einfügen** und **Tabelle einfügen** hinzufügen, um Aktionen auszuführen, wenn der Benutzer darauf klickt. Weitere Informationen zu Rückruf Methoden für Menüband-Steuerelemente finden Sie unter [Menüband-XML](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>So fügen Sie Rückrufmethoden für die Schaltflächen hinzu

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **MyRibbon.cs** oder **MyRibbon. vb**, und klicken Sie dann auf **Öffnen**.

2. Fügen Sie den folgenden Code am Anfang der Datei **MyRibbon.cs** oder **MyRibbon. vb** ein. Dieser Code erstellt einen Alias für den Namespace <xref:Microsoft.Office.Interop.Word>.

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. Füge der `MyRibbon`-Klasse die folgende Methode hinzu. Dies ist eine Rückruf Methode für die Schaltfläche **Text einfügen** , mit der dem aktiven Dokument an der aktuellen Position des Cursors eine Zeichenfolge hinzugefügt wird.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. Füge der `MyRibbon`-Klasse die folgende Methode hinzu. Dies ist eine Rückruf Methode für die Schaltfläche **Tabelle einfügen** , die dem aktiven Dokument an der aktuellen Position des Cursors eine Tabelle hinzufügt.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>Testen des VSTO-Add-Ins
 Wenn Sie das Projekt ausführen, wird Word geöffnet, und die Registerkarte mit dem Namen **Add-ins** wird auf dem Menüband angezeigt. Klicken Sie auf die Schaltflächen **Text einfügen** und **Tabelle einfügen** auf der Registerkarte **Add-ins** , um den Code zu testen.

### <a name="to-test-your-vsto-add-in"></a>So testen Sie Ihr VSTO-Add-In

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Vergewissern Sie sich, dass die Registerkarte **Add-ins** im Menüband angezeigt wird.

3. Klicken Sie auf die Registerkarte **Add-Ins** .

4. Vergewissern Sie sich, dass die **Inhalts** Gruppe auf dem Menüband angezeigt wird.

5. Klicken Sie in der Gruppe **Inhalt** auf die Schaltfläche **Text einfügen** .

     Eine Zeichenfolge wird dem Dokument an der aktuellen Position des Cursors hinzugefügt.

6. Klicken Sie auf die Schaltfläche **Tabelle einfügen** in der Gruppe **Inhalt** .

     Eine Tabelle wird dem Dokument an der aktuellen Position des Cursors hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zum Anpassen der Office-Benutzeroberfläche finden Sie in diesen Themen:

- Passen Sie das Menüband einer anderen Office-Anwendung an. Weitere Informationen zu den Anwendungen, die das Anpassen des Menübands unterstützen, finden Sie unter Übersicht über das [Menüband](../vsto/ribbon-overview.md).

- Passen Sie das Menüband einer Office-Anwendung mithilfe des Menüband-Designers an. Weitere Informationen finden Sie unter [Ribbon Designer](../vsto/ribbon-designer.md).

- Erstellen eines benutzerdefinierten Aktionsbereichs. Weitere Informationen finden Sie unter [Übersicht über den Aktions](../vsto/actions-pane-overview.md)Bereich.

- Anpassen der Benutzeroberfläche von Microsoft Office Outlook mithilfe von Outlook-Formularbereichen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
