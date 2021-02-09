---
title: Benutzerdefinierten Aufgabenbereich mit Menü Band Schaltfläche synchronisieren
description: Erfahren Sie, wie Sie einen benutzerdefinierten Aufgabenbereich erstellen können, den Benutzer durch Klicken auf eine UMSCHALT Fläche auf dem Menüband ausblenden oder anzeigen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9ac8c4ef96a421ece6c0591d4340d570d71c08e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846282"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>Exemplarische Vorgehensweise: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Menü Band Schaltfläche
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein benutzerdefinierter Aufgabenbereich erstellt wird, den Benutzer durch Klicken auf eine UMSCHALT Fläche auf dem Menüband ausblenden oder anzeigen können. Sie sollten immer ein UI-Element erstellen, z. B. eine Schaltfläche, auf die Benutzer klicken können, um Ihren benutzerdefinierten Aufgabenbereich anzeigen oder ausblenden zu können, da Microsoft Office-Anwendung keine Standardmethode für Benutzer bereitstellen, um benutzerdefinierte Aufgabenbereiche anzuzeigen oder auszublenden.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Obwohl in dieser exemplarischen Vorgehensweise speziell Excel verwendet wird, gelten die Konzepte in dieser exemplarischen Vorgehensweise für alle oben aufgelisteten Anwendungen.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Entwerfen der Benutzeroberfläche (UI) des benutzerdefinierten Aufgabenbereichs

- Hinzufügen einer Umschaltfläche zum Menüband

- Synchronisieren der Umschaltfläche mit dem benutzerdefinierten Aufgabenbereich

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel oder Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].

## <a name="create-the-add-in-project"></a>Erstellen des Add-in-Projekts
 In diesem Schritt erstellen Sie ein VSTO-Add-in-Projekt für Excel.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Add-In-Projekt für Excel namens **SynchronizeTaskPaneAndRibbon**, indem Sie die Add-In-Projektvorlage für Excel verwenden. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Codedatei **ThisAddIn.cs** oder **ThisAddIn.vb** und fügt das Projekt **SynchronizeTaskPaneAndRibbon** dem **Projektmappen-Explorer** hinzu.

## <a name="add-a-toggle-button-to-the-ribbon"></a>Hinzufügen einer UMSCHALT Fläche zum Menüband
 Eine der Entwurfsrichtlinien für Office-Anwendungen besagt, dass Benutzer immer die Möglichkeit haben sollen, die Benutzeroberfläche von Office-Anwendungen zu steuern. Damit Benutzer den benutzerdefinierten Aufgabenbereich steuern können, können Sie eine Menübandumschaltfläche hinzufügen, die den Aufgabenbereich anzeigt oder ausblendet. Fügen Sie zum Erstellen einer Umschaltfläche dem Projekt ein Element von **Menüband (Visueller Designer)** hinzu. Der Designer unterstützt Sie beim Hinzufügen und Anordnen von Steuerelementen, Festlegen von Steuerelementeigenschaften und Behandeln von Ereignissen von Steuerelementen. Weitere Informationen finden Sie unter [Menüband-Designer](../vsto/ribbon-designer.md).

### <a name="to-add-a-toggle-button-to-the-ribbon"></a>So fügen Sie eine UMSCHALT Fläche zum Menüband hinzu

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband (Visueller Designer)** aus.

3. Ändern Sie den Namen des neuen Menübands in **ManageTaskPaneRibbon**, und klicken Sie auf **Hinzufügen**.

     Die Datei **ManageTaskPaneRibbon.cs** oder **ManageTaskPaneRibbon.vb** wird im Menüband-Designer geöffnet. Sie enthält eine Standardregisterkarte und eine Gruppe.

4. Klicken Sie im Menüband-Designer auf **group1**.

5. Legen Sie im Fenster **Eigenschaften** die **Label** -Eigenschaft auf **Aufgabenbereich-Manager** fest.

6. Ziehen Sie ein **ToggleButton** -Steuerelement von der Registerkarte **Steuerelemente für Office-Menübänder** der **Toolbox** auf die Gruppe **Aufgabenbereich-Manager** .

7. Klicken Sie auf **toggleButton1**.

8. Legen Sie im Fenster **Eigenschaften** die **Label** -Eigenschaft auf **Aufgabenbereich anzeigen** fest.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs
 Es gibt keinen visuellen Designer für benutzerdefinierte Aufgabenbereiche, Sie können aber dennoch ein Benutzersteuerelement mit dem gewünschten Layout entwerfen. Im weiteren Verlauf dieser exemplarischen Vorgehensweise fügen Sie dem benutzerdefinierten Aufgabenbereich das Benutzersteuerelement hinzu.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>So entwerfen Sie die Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs

1. Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.

2. Ändern Sie im Dialogfeld **Neues Element hinzufügen** den Namen des neuen Benutzersteuerelements in **TaskPaneControl**, und klicken Sie dann auf **Hinzufügen**.

     Das Benutzersteuerelement wird im Designer geöffnet.

3. Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein **TextBox** -Steuerelement auf das Benutzersteuerelement.

## <a name="create-the-custom-task-pane"></a>Erstellen des benutzerdefinierten Aufgabenbereichs
 Um den benutzerdefinierten Aufgabenbereich beim Starten des VSTO-Add-Ins zu erstellen, fügen Sie dem Aufgabenbereich das Benutzersteuerelement im <xref:Microsoft.Office.Tools.AddIn.Startup> -Ereignishandler des VSTO-Add-Ins hinzu. Standardmäßig wird der benutzerdefinierte Aufgabenbereich nicht angezeigt. Später in dieser exemplarischen Vorgehensweise fügen Sie Code hinzu, mit dem der Aufgabenbereich angezeigt oder ausgeblendet wird, wenn der Benutzer auf die UMSCHALT Fläche klickt, die Sie dem Menüband hinzugefügt haben.

### <a name="to-create-the-custom-task-pane"></a>So erstellen Sie den benutzerdefinierten Aufgabenbereich

1. Erweitern Sie im **Projektmappen-Explorer** die Option **Excel**.

2. Klicken Sie mit der rechten Maustaste auf **ThisAddIn.cs** oder **ThisAddIn.vb** , und klicken Sie auf **Code anzeigen**.

3. Fügen Sie der `ThisAddIn` -Klasse den folgenden Code hinzu. Durch diesen Code wird eine Instanz von `TaskPaneControl` als Member von `ThisAddIn`deklariert.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]

4. Ersetzen Sie den `ThisAddIn_Startup` -Ereignishandler durch den folgenden Code. Dieser Code fügt das `TaskPaneControl` -Objekt zum `CustomTaskPanes` -Feld hinzu, zeigt aber nicht den benutzerdefinierten Aufgabenbereich an (standardmäßig ist die <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> -Eigenschaft der <xref:Microsoft.Office.Tools.CustomTaskPane> -Klasse **false**). Der Visual C#-Code fügt dem <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> -Ereignis auch einen Ereignishandler an.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]

5. Füge der `ThisAddIn`-Klasse die folgende Methode hinzu. Diese Methode behandelt das <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> -Ereignis. Wenn der Benutzer den Aufgabenbereich durch Klicken auf die Schaltfläche **Schließen** (X) schließt, aktualisiert diese Methode den Zustand der Umschaltfläche im Menüband.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]

6. Fügen Sie der `ThisAddIn` -Klasse folgende Eigenschaft hinzu. Diese Eigenschaft stellt das private `myCustomTaskPane1` -Objekt für andere Klassen bereit. Weiter unten in dieser exemplarischen Vorgehensweise werden Sie Code zur `MyRibbon` -Klasse hinzufügen, der diese Eigenschaft verwendet.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]

## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>Ausblenden und Anzeigen des benutzerdefinierten Aufgabenbereichs mit der UMSCHALT Fläche
 Im letzte Schritt wird Code hinzugefügt, der den benutzerdefinierten Aufgabenbereich anzeigt oder ausblendet, wenn der Benutzer im Menüband auf die Umschaltfläche klickt.

### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>So zeigen Sie den benutzerdefinierten Aufgabenbereich mithilfe der Umschaltfläche an oder blenden ihn aus

1. Doppelklicken Sie im Menüband-Designer auf die Umschaltfläche **Aufgabenbereich anzeigen** .

     Visual Studio generiert automatisch einen Ereignishandler namens `toggleButton1_Click`, der das <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> -Ereignis der Umschaltfläche verarbeitet. Visual Studio öffnet außerdem die Datei *MyRibbon.cs* oder *MyRibbon.vb* im Code-Editor.

2. Ersetzen Sie den `toggleButton1_Click` -Ereignishandler durch den folgenden Code. Wenn der Benutzer auf die Umschaltfläche klickt, zeigt dieser Code den benutzerdefinierten Aufgabenbereich an oder blendet ihn aus, je nachdem, ob die Umschaltfläche gedrückt wird oder nicht.

     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]

## <a name="test-the-add-in"></a>Testen des Add-ins
 Wenn Sie das Projekt ausführen, wird Excel geöffnet, ohne den benutzerdefinierten Aufgabenbereich anzuzeigen. Klicken Sie im Menüband auf die UMSCHALT Fläche, um den Code zu testen.

### <a name="to-test-your-vsto-add-in"></a>So testen Sie Ihr VSTO-Add-In

1. Drücken Sie **F5** , um das Projekt auszuführen.

     Vergewissern Sie sich, dass Excel geöffnet wird und die Registerkarte **Add-ins** im Menüband angezeigt wird.

2. Klicken Sie im Menüband auf die Registerkarte **Add-ins** .

3. Klicken Sie auf die Gruppe **Aufgabenbereich-Manager** und dann auf die Umschaltfläche **Aufgabenbereich anzeigen** .

     Überprüfen Sie, ob der Aufgabenbereich abwechselnd angezeigt und ausgeblendet wird, wenn Sie auf die Umschaltfläche klicken.

4. Wenn der Aufgabenbereich angezeigt wird, klicken Sie in der Ecke des Aufgabenbereichs auf die Schaltfläche **Schließen** (X).

     Stellen Sie sicher, dass die Umschaltfläche als nicht gedrückt angezeigt wird.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen über das Erstellen von benutzerdefinierten Aufgabenbereichen finden Sie in diesen Themen:

- Erstellen Sie einen benutzerdefinierten Aufgabenbereich in einem VSTO-Add-in für eine andere Anwendung. Weitere Informationen zu den Anwendungen, die benutzerdefinierte Aufgabenbereiche unterstützen, finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

- Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Automatisieren einer Anwendung aus einem benutzerdefinierten Aufgaben](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)Bereich.

- Erstellen eines benutzerdefinierten Aufgabenbereichs für jede E-Mail-Nachricht, die in Outlook geöffnet wird. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen von benutzerdefinierten Aufgabenbereichen mit e-Mails in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Weitere Informationen
- [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)
- [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen mit e-Mails in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
