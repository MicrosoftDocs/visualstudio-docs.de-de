---
title: Anzeigen benutzerdefinierter Aufgabenbereiche mit e-Mail-Nachrichten in Outlook
description: Erfahren Sie, wie Sie eine eindeutige Instanz eines benutzerdefinierten Aufgabenbereichs für jede e-Mail-Nachricht in Microsoft Outlook anzeigen, die erstellt oder geöffnet wird.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ac14eff05c6f776181c20acde4cff4e2ed7a87b6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522706"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen mit e-Mails in Outlook
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie eine eindeutige Instanz eines benutzerdefinierten Aufgabenbereichs mit jeder erstellten oder geöffneten e-Mail angezeigt wird. Benutzer können den benutzerdefinierten Aufgabenbereich über eine Schaltfläche auf dem Menüband jeder E-Mail anzeigen oder ausblenden.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Wenn Sie einen benutzerdefinierten Aufgabenbereich mit mehreren Explorer- oder Inspektor-Fenstern anzeigen möchten, müssen Sie eine Instanz des benutzerdefinierten Aufgabenbereichs für jedes geöffnete Fenster erstellen. Weitere Informationen zum Verhalten von benutzerdefinierten Aufgabenbereichen in Outlook-Fenstern finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

> [!NOTE]
> In dieser exemplarischen Vorgehensweise wird der VSTO-Add-In-Code in kleinen Abschnitten dargestellt, um die dem Code zugrunde liegende Logik einfacher zu erläutern.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs

- Erstellen einer benutzerdefinierten Menüband-Benutzeroberfläche

- Anzeigen der benutzerdefinierten Menüband-Benutzeroberfläche mit e-Mail.

- Erstellen einer Klasse zum Verwalten von Inspektor-Fenstern und benutzerdefinierten Aufgabenbereichen

- Initialisieren und Bereinigen von Ressourcen, die durch das VSTO-Add-In verwendet werden

- Synchronisieren der Umschaltfläche des Menübands mit dem benutzerdefinierten Aufgabenbereich

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] oder Microsoft Outlook 2010.

## <a name="create-the-project"></a>Erstellen des Projekts
 Benutzerdefinierte Aufgabenbereiche werden in VSTO-Add-Ins implementiert. Erstellen Sie zunächst ein VSTO-Add-in-Projekt für Outlook.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein **Outlook-Add-In** -Projekt mit dem Namen **OutlookMailItemTaskPane**. Verwenden Sie die Projektvorlage **Outlook-Add-In** . Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Codedatei *ThisAddIn.cs* oder *ThisAddIn.vb* und fügt dem **Projektmappen-Explorer** das **OutlookMailItemTaskPane**-Projekt hinzu.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs
 Es gibt keinen visuellen Designer für benutzerdefinierte Aufgabenbereiche, Sie können aber dennoch ein Benutzersteuerelement mit der gewünschten Benutzeroberfläche entwerfen. Der benutzerdefinierte Aufgabenbereich in diesem VSTO-Add-In entspricht einer einfachen Benutzeroberfläche, die ein <xref:System.Windows.Forms.TextBox> -Steuerelement enthält. Im weiteren Verlauf dieser exemplarischen Vorgehensweise fügen Sie dem benutzerdefinierten Aufgabenbereich das Benutzersteuerelement hinzu.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>So entwerfen Sie die Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs

1. Klicken Sie im **Projektmappen-Explorer** auf das Projekt **OutlookMailItemTaskPane** .

2. Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.

3. Ändern Sie im Dialogfeld **Neues Element hinzufügen** den Namen des Benutzersteuerelements in **TaskPaneControl**, und klicken Sie dann auf **Hinzufügen**.

     Das Benutzersteuerelement wird im Designer geöffnet.

4. Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein **TextBox** -Steuerelement auf das Benutzersteuerelement.

## <a name="design-the-user-interface-of-the-ribbon"></a>Entwerfen der Benutzeroberfläche des Menübands
 Eines der Ziele dieses VSTO-Add-Ins besteht darin, Benutzern die Möglichkeit zu geben, den benutzerdefinierten Aufgabenbereich im Menüband jeder e-Mail-Nachricht auszublenden oder anzuzeigen. Wenn Sie die Benutzeroberfläche bereitstellen möchten, erstellen Sie eine benutzerdefinierte Menüband-Benutzeroberfläche mit einer Umschaltfläche, über die Benutzer den benutzerdefinierten Aufgabenbereich durch Klicken anzeigen oder ausblenden können.

### <a name="to-create-a-custom-ribbon-ui"></a>So erstellen Sie eine benutzerdefinierte Menüband-Benutzeroberfläche

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband (Visueller Designer)** aus.

3. Ändern Sie den Namen des neuen Menübands in **ManageTaskPaneRibbon**, und klicken Sie auf **Hinzufügen**.

     Die Datei *ManageTaskPaneRibbon.cs* oder *ManageTaskPaneRibbon.vb* wird im Menüband-Designer geöffnet. Sie enthält eine Standardregisterkarte und eine Gruppe.

4. Klicken Sie im Menüband-Designer auf **group1**.

5. Legen Sie im Fenster **Eigenschaften** die **Label** -Eigenschaft auf **Aufgabenbereich-Manager** fest.

6. Ziehen Sie ein ToggleButton-Steuerelement von der Registerkarte **Steuerelemente für Office-Menübänder** der **Toolbox** auf die Gruppe **Task Pane Manager** .

7. Klicken Sie auf **toggleButton1**.

8. Legen Sie im Fenster **Eigenschaften** die **Label** -Eigenschaft auf **Aufgabenbereich anzeigen** fest.

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Anzeigen der benutzerdefinierten Menüband-Benutzeroberfläche mit e-Mail
 Der in dieser exemplarischen Vorgehensweise erstellte benutzerdefinierte Aufgabenbereich ist so konzipiert, dass er nur in Inspektor-Fenstern angezeigt wird, die E-Mails enthalten. Lesen Sie die Eigenschaften daher so fest, dass die benutzerdefinierte Menüband-Benutzeroberfläche nur in diesen Fenstern angezeigt wird.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>So zeigen Sie die benutzerdefinierte Menüband-Benutzeroberfläche mit e-Mail an

1. Klicken Sie im Menüband-Designer auf das Menüband **ManageTaskPaneRibbon** .

2. Klicken Sie im Fenster **Eigenschaften** auf die Dropdownliste neben **RibbonType**, und wählen Sie **Microsoft.Outlook.Mail.Compose** und **Microsoft.Outlook.Mail.Read** aus.

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Erstellen einer Klasse zum Verwalten von Inspektor-Fenstern und benutzerdefinierten Aufgabenbereichen
 Es gibt mehrere Fälle, in denen das VSTO-Add-in angeben muss, welcher benutzerdefinierte Aufgabenbereich einer bestimmten e-Mail-Nachricht zugeordnet ist. Dazu gehören folgende Situationen:

- Wenn der Benutzer eine e-Mail-Nachricht schließt. In diesem Fall muss das VSTO-Add-In den entsprechenden benutzerdefinierten Aufgabenbereich entfernen, um sicherzustellen, dass die vom VSTO-Add-In verwendeten Ressourcen ordnungsgemäß bereinigt werden.

- Der Benutzer schließt den benutzerdefinierten Aufgabenbereich. In diesem Fall muss das VSTO-Add-in den Zustand der UMSCHALT Fläche auf dem Menüband der e-Mail aktualisieren.

- , Wenn der Benutzer im Menüband auf die UMSCHALT Fläche klickt. In diesem Fall muss das VSTO-Add-In den entsprechenden Aufgabenbereich anzeigen oder ausblenden.

  Damit das VSTO-Add-in nachverfolgen kann, welcher benutzerdefinierte Aufgabenbereich den einzelnen geöffneten e-Mails zugeordnet ist, erstellen Sie eine benutzerdefinierte Klasse, die Paare von-und-Objekten umschließt <xref:Microsoft.Office.Interop.Outlook.Inspector> <xref:Microsoft.Office.Tools.CustomTaskPane> . Diese Klasse erstellt ein neues benutzerdefiniertes Aufgabenbereichs Objekt für jede e-Mail-Nachricht und löscht den benutzerdefinierten Aufgabenbereich, wenn die entsprechende e-Mail-Nachricht geschlossen wird.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>So erstellen Sie eine Klasse zum Verwalten von Inspektor-Fenstern und benutzerdefinierten Aufgabenbereichen

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei *ThisAddIn.cs* oder *ThisAddIn.vb* , und klicken Sie dann auf **Code anzeigen**.

2. Fügen Sie am Anfang der Datei die folgenden Anweisungen ein.

     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]

3. Fügen Sie der Datei *ThisAddIn.cs* oder *ThisAddIn.vb* folgenden Code außerhalb der `ThisAddIn` -Klasse hinzu (für Visual C# fügen Sie diesen Code im `OutlookMailItemTaskPane` -Namespace hinzu). Die `InspectorWrapper` -Klasse verwaltet ein Paar von <xref:Microsoft.Office.Interop.Outlook.Inspector> - und <xref:Microsoft.Office.Tools.CustomTaskPane> -Objekten. Sie schließen die Definition dieser Klasse in den folgenden Schritten ab.

     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]

4. Fügen Sie nach dem Code, den Sie im vorherigen Schritt hinzugefügt haben, den folgenden Konstruktor hinzu. Dieser Konstruktor erstellt und initialisiert einen neuen benutzerdefinierten Aufgabenbereich, der dem übergebenen <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekt zugeordnet ist. In C# fügt der Konstruktor außerdem Ereignishandler an das <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> -Ereignis des <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekts und das <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> -Ereignis des <xref:Microsoft.Office.Tools.CustomTaskPane> -Objekts an.

     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]

5. Fügen Sie nach dem Code, den Sie im vorherigen Schritt hinzugefügt haben, die folgende Methode hinzu. Diese Methode ist ein Ereignishandler für das <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> -Ereignis des in der <xref:Microsoft.Office.Tools.CustomTaskPane> -Klasse enthaltenen `InspectorWrapper` -Objekts. Dieser Code aktualisiert den Zustand der Umschaltfläche, sobald der Benutzer den benutzerdefinierten Aufgabenbereich öffnet oder schließt.

     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]

6. Fügen Sie nach dem Code, den Sie im vorherigen Schritt hinzugefügt haben, die folgende Methode hinzu. Diese Methode ist ein Ereignishandler für das- <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> Ereignis des <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekts, das die aktuelle e-Mail-Nachricht enthält. Der Ereignishandler gibt Ressourcen frei, wenn die e-Mail-Nachricht geschlossen wird. Der Ereignishandler entfernt auch den aktuellen benutzerdefinierten Aufgabenbereich aus der `CustomTaskPanes` -Auflistung. Dadurch wird verhindert, dass mehrere Instanzen des benutzerdefinierten Aufgabenbereichs angezeigt werden, wenn die nächste e-Mail geöffnet wird.

     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]

7. Fügen Sie nach dem Code, den Sie im vorherigen Schritt hinzugefügt haben, den folgenden Code hinzu. Weiter unten in dieser exemplarischen Vorgehensweise rufen Sie diese Eigenschaft von einer Methode in der benutzerdefinierten Menüband-Benutzeroberfläche auf, um den benutzerdefinierten Aufgabenbereich anzuzeigen oder auszublenden.

     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Initialisieren und Bereinigen von Ressourcen, die vom Add-in verwendet werden
 Fügen Sie der `ThisAddIn` -Klasse Code hinzu, durch den das VSTO-Add-In beim Laden initialisiert und die vom VSTO-Add-In verwendeten Ressourcen beim Entladen des Add-Ins bereinigt werden. Sie initialisieren das VSTO-Add-in, indem Sie einen Ereignishandler für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> -Ereignis einrichten und alle vorhandenen e-Mail-Nachrichten an diesen Ereignishandler übergeben. Sobald das VSTO-Add-In entladen wird, trennen Sie den Ereignishandler und bereinigen die vom VSTO-Add-In verwendeten Objekte.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>So initialisieren und bereinigen Sie die vom VSTO-Add-In verwendeten Ressourcen

1. Suchen Sie in der Datei *ThisAddIn.cs* oder *ThisAddIn.vb* die Definition der `ThisAddIn` -Klasse.

2. Fügen Sie der `ThisAddIn` -Klasse die folgenden Deklarationen hinzu:

   - Das `inspectorWrappersValue` -Feld enthält alle vom VSTO-Add-In verwalteten <xref:Microsoft.Office.Interop.Outlook.Inspector> - und `InspectorWrapper` -Objekte.

   - Das `inspectors` -Feld behält einen Verweis auf die Auflistung von Inspektor-Fenstern in der aktuellen Outlook-Instanz. Dieser Verweis verhindert, dass der Garbage Collector den Arbeitsspeicher freigibt, der den Ereignishandler für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> -Ereignis enthält, das Sie im nächsten Schritt deklarieren.

     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]

3. Ersetzen Sie die `ThisAddIn_Startup`-Methode durch den folgenden Code. Dieser Code fügt einen Ereignishandler an das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> -Ereignis an und übergibt alle vorhandenen <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekte an den Ereignishandler. Wenn der Benutzer das VSTO-Add-in nach der bereits Ausführung von Outlook lädt, verwendet das VSTO-Add-in diese Informationen, um benutzerdefinierte Aufgabenbereiche für alle bereits geöffneten e-Mail-Nachrichten zu erstellen.

    [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
    [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]

4. Ersetzen Sie die `ThisAddIn_ShutDown`-Methode durch den folgenden Code. Dieser Code trennt den <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> -Ereignishandler und bereinigt die vom VSTO-Add-In verwendeten Objekte.

    [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
    [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]

5. Fügen Sie der <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> -Klasse den folgenden `ThisAddIn` -Ereignishandler hinzu. Wenn eine neue eine <xref:Microsoft.Office.Interop.Outlook.Inspector> e-Mail-Nachricht enthält, erstellt die Methode eine Instanz eines neuen- `InspectorWrapper` Objekts, um die Beziehung zwischen der e-Mail und dem entsprechenden Aufgabenbereich zu verwalten.

    [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
    [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]

6. Fügen Sie der `ThisAddIn` -Klasse folgende Eigenschaft hinzu. Diese Eigenschaft macht das private `inspectorWrappersValue` -Feld für Code außerhalb der `ThisAddIn` -Klasse verfügbar.

    [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
    [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]

## <a name="checkpoint"></a>Prüfpunkt
 Erstellen Sie Ihr Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.

### <a name="to-build-your-project"></a>So erstellen Sie das Projekt

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **OutlookMailItemTaskPane** , und klicken Sie dann auf **Erstellen**. Vergewissern Sie sich, dass das Projekt ohne Fehler kompiliert wurde.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Synchronisieren der UMSCHALT Fläche des Menübands mit dem benutzerdefinierten Aufgabenbereich
 Die Umschaltfläche erscheint gedrückt, wenn der Aufgabenbereich sichtbar ist, und nicht gedrückt, wenn der Aufgabenbereich ausgeblendet ist. Wenn Sie den Zustand der Schaltfläche mit dem benutzerdefinierten Aufgabenbereich synchronisieren möchten, ändern Sie den <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> -Ereignishandler der Umschaltfläche.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>So synchronisieren Sie den benutzerdefinierten Aufgabenbereich mit der Umschaltfläche

1. Doppelklicken Sie im Menüband-Designer auf die Umschaltfläche **Aufgabenbereich anzeigen** .

     Visual Studio generiert automatisch einen Ereignishandler namens `toggleButton1_Click`, der das <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> -Ereignis der Umschaltfläche verarbeitet. Visual Studio öffnet außerdem die Datei *ManageTaskPaneRibbon.cs* oder *ManageTaskPaneRibbon.vb* im Code-Editor.

2. Fügen Sie die folgenden Anweisungen am Anfang der Datei *ManageTaskPaneRibbon.cs* oder *ManageTaskPaneRibbon.vb* ein.

     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]

3. Ersetzen Sie den `toggleButton1_Click` -Ereignishandler durch den folgenden Code. Wenn der Benutzer auf die Umschaltfläche klickt, wird der benutzerdefinierte Aufgabenbereich, der dem aktuellen Inspektor-Fenster zugeordnet ist, durch diese Methode angezeigt oder ausgeblendet.

     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]

## <a name="test-the-project"></a>Testen des Projekts
 Sobald Sie das Debuggen des Projekts starten, wird Outlook geöffnet und das VSTO-Add-In geladen. Das VSTO-Add-in zeigt mit jeder geöffneten e-Mail eine eindeutige Instanz des benutzerdefinierten Aufgabenbereichs an. Erstellen Sie mehrere neue e-Mail-Nachrichten zum Testen des Codes.

### <a name="to-test-the-vsto-add-in"></a>So testen Sie das VSTO-Add-In

1. Drücken Sie **F5**.

2. Klicken Sie in Outlook auf **neu** , um eine neue e-Mail-Nachricht zu erstellen.

3. Klicken Sie im Menüband der e-Mail auf die Registerkarte **Add-ins** , und klicken Sie dann auf die Schaltfläche **Aufgabenbereich anzeigen** .

    Überprüfen Sie, ob ein Aufgabenbereich mit dem Titel **mein Aufgaben** Bereich mit der e-Mail-Nachricht angezeigt wird.

4. Geben Sie im Aufgabenbereich **Erster Aufgabenbereich** in das Textfeld ein.

5. Schließen Sie den Aufgabenbereich.

    Überprüfen Sie, ob sich der Zustand der Schaltfläche **Aufgabenbereich anzeigen** ändert, sodass sie nicht mehr gedrückt erscheint.

6. Klicken Sie erneut auf die Schaltfläche **Aufgabenbereich anzeigen** .

    Stellen Sie sicher, dass der Aufgabenbereich geöffnet wird und das Textfeld weiterhin die Zeichenfolge **Erster Aufgabenbereich** enthält.

7. Klicken Sie in Outlook auf **neu** , um eine zweite e-Mail-Nachricht zu erstellen.

8. Klicken Sie im Menüband der e-Mail auf die Registerkarte **Add-ins** , und klicken Sie dann auf die Schaltfläche **Aufgabenbereich anzeigen** .

    Überprüfen Sie, ob ein Aufgabenbereich mit dem Titel **mein Aufgaben** Bereich mit der e-Mail-Nachricht angezeigt wird und das Textfeld in diesem Aufgabenbereich leer ist.

9. Geben Sie im Aufgabenbereich **Zweiter Aufgabenbereich** in das Textfeld ein.

10. Ändern des Fokus auf die erste e-Mail-Nachricht.

     Vergewissern Sie sich, dass der Aufgabenbereich, der dieser e-Mail-Nachricht zugeordnet ist, weiterhin den **ersten Aufgaben** Bereich im Textfeld anzeigt.

    Das VSTO-Add-In behandelt auch komplexere Szenarien, die Sie ausprobieren können. Beispielsweise können Sie das Verhalten beim Anzeigen von e-Mails testen, indem Sie die Schaltflächen **nächstes Element** und **Vorheriges Element** verwenden. Sie können das Verhalten auch testen, wenn Sie das VSTO-Add-in entladen, mehrere e-Mail-Nachrichten öffnen und das VSTO-Add-in erneut laden.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen über das Erstellen von benutzerdefinierten Aufgabenbereichen finden Sie in diesen Themen:

- Erstellen Sie einen benutzerdefinierten Aufgabenbereich in einem VSTO-Add-in für eine andere Anwendung. Weitere Informationen zu den Anwendungen, die benutzerdefinierte Aufgabenbereiche unterstützen, finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

- Automatisieren einer Microsoft Office-Anwendung mithilfe eines benutzerdefinierten Aufgabenbereichs. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Automatisieren einer Anwendung aus einem benutzerdefinierten Aufgaben](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)Bereich.

- Erstellen einer Menübandschaltfläche in Excel, über die ein benutzerdefinierter Aufgabenbereich ausgeblendet oder angezeigt werden kann. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Menü Band Schaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

## <a name="see-also"></a>Weitere Informationen
- [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)
- [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Exemplarische Vorgehensweise: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Menü Band Schaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
