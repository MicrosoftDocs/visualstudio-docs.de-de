---
title: 'Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich'
description: Erstellen Sie einen benutzerdefinierten Aufgabenbereich, der Microsoft PowerPoint automatisiert, indem Sie Datumsangaben in eine Folie einfügen, wenn der Benutzer auf ein MonthCalendar-Steuerelement im benutzerdefinierten Aufgabenbereich klickt.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ed0d2ae6bf66e8f7375bde72aaec085463b9ca18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906617"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein benutzerdefinierter Aufgabenbereich erstellt wird, der PowerPoint automatisiert. Der benutzerdefinierte Aufgabenbereich fügt Daten in eine Folie ein, wenn der Benutzer auf ein <xref:System.Windows.Forms.MonthCalendar> -Steuerelement im benutzerdefinierten Aufgabenbereich klickt.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Obwohl in dieser exemplarischen Vorgehensweise speziell PowerPoint verwendet wird, gelten die Konzepte in dieser exemplarischen Vorgehensweise für alle oben aufgelisteten Anwendungen.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs

- Automatisieren von PowerPoint über den benutzerdefinierten Aufgabenbereich

- Anzeigen des benutzerdefinierten Aufgabenbereichs in PowerPoint

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft PowerPoint 2010 oder [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].

## <a name="create-the-add-in-project"></a>Erstellen des Add-in-Projekts
 Der erste Schritt besteht darin, ein VSTO-Add-in-Projekt für PowerPoint zu erstellen.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie mithilfe der PowerPoint-Add-In-Projektvorlage ein PowerPoint-VSTO-Add-In-Projekt mit dem Namen **MyAddIn**. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Codedatei **ThisAddIn.cs** oder **ThisAddIn.vb** und fügt dem **Projektmappen-Explorer** das **MyAddIn**-Projekt hinzu.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs
 Es gibt keinen visuellen Designer für benutzerdefinierte Aufgabenbereiche, Sie können aber dennoch ein Benutzersteuerelement mit dem gewünschten Layout entwerfen. Im weiteren Verlauf dieser exemplarischen Vorgehensweise fügen Sie dem benutzerdefinierten Aufgabenbereich das Benutzersteuerelement hinzu.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>So entwerfen Sie die Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs

1. Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.

2. Ändern Sie im Dialogfeld **Neues Element hinzufügen** den Namen des Benutzersteuerelements in **MyUserControl**, und klicken Sie auf **Hinzufügen**.

     Das Benutzersteuerelement wird im Designer geöffnet.

3. Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein **MonthCalendar** -Steuerelement auf das Benutzersteuerelement.

     Wenn der Umfang des **MonthCalendar** -Steuerelements größer als die Entwurfsoberfläche des Benutzersteuerelements ist, passen Sie die Größe des Benutzersteuerelements an das **MonthCalendar** -Steuerelement an.

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Automatisieren von PowerPoint über den benutzerdefinierten Aufgabenbereich
 Mit dem VSTO-Add-In soll in der ersten Folie der aktiven Präsentation ein ausgewähltes Datum eingefügt werden. Verwenden Sie das <xref:System.Windows.Forms.MonthCalendar.DateChanged> -Ereignis des Steuerelements, um das ausgewählte Datum bei jeder Änderung des Datums hinzuzufügen.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>So automatisieren Sie PowerPoint über den benutzerdefinierten Aufgabenbereich

1. Doppelklicken Sie im Designer auf das <xref:System.Windows.Forms.MonthCalendar> -Steuerelement.

     Die Datei **MyUserControl.cs** oder **MyUserControl.vb** wird geöffnet, und ein Ereignishandler für das <xref:System.Windows.Forms.MonthCalendar.DateChanged> -Ereignis wird erstellt.

2. Fügen Sie den folgenden Code ganz oben in der Datei ein. Dieser Code erstellt Aliase für die <xref:Microsoft.Office.Core> -und [PowerPoint](/previous-versions/office/developer/office-2010/ff763170%28v%3doffice.14%29) -Namespaces.

     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]

3. Fügen Sie der `MyUserControl` -Klasse den folgenden Code hinzu. Mit diesem Code wird ein [Shape](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) -Objekt als Member von deklariert `MyUserControl` . Im nächsten Schritt verwenden Sie diese [Form](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) , um einer Folie in der aktiven Präsentation ein Textfeld hinzuzufügen.

     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]

4. Ersetzen Sie den `monthCalendar1_DateChanged` -Ereignishandler durch den folgenden Code. Mit diesem Code wird in die erste Folie in der aktiven Präsentation ein Textfeld eingefügt, in das anschließend das aktuell ausgewählte Datum eingefügt wird. Im Code wird mithilfe des `Globals.ThisAddIn` -Objekts auf das PowerPoint-Objektmodell zugegriffen.

     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]

5. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das **MyAddIn** -Projekt, und klicken Sie dann auf **Erstellen**. Vergewissern Sie sich, dass das Projekt ohne Fehler erstellt wurde.

## <a name="display-the-custom-task-pane"></a>Anzeigen des benutzerdefinierten Aufgabenbereichs
 Um den benutzerdefinierten Aufgabenbereich beim Starten des VSTO-Add-Ins anzuzeigen, fügen Sie dem Aufgabenbereich das Benutzersteuerelement im <xref:Microsoft.Office.Tools.AddIn.Startup> -Ereignishandler des VSTO-Add-Ins hinzu.

### <a name="to-display-the-custom-task-pane"></a>So zeigen Sie den benutzerdefinierten Aufgabenbereich an

1. Erweitern Sie **PowerPoint** im **Projektmappen-Explorer**.

2. Klicken Sie mit der rechten Maustaste auf **ThisAddIn.cs** oder **ThisAddIn.vb** , und klicken Sie auf **Code anzeigen**.

3. Fügen Sie der `ThisAddIn` -Klasse den folgenden Code hinzu. Dieser Code deklariert Instanzen von `MyUserControl` und <xref:Microsoft.Office.Tools.CustomTaskPane> als Member der `ThisAddIn` -Klasse.

     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]

4. Ersetzen Sie den `ThisAddIn_Startup` -Ereignishandler durch den folgenden Code. Durch diesen Code wird ein neuer <xref:Microsoft.Office.Tools.CustomTaskPane> erstellt, indem der `MyUserControl` -Auflistung das `CustomTaskPanes` -Objekt hinzugefügt wird. Durch den Code wird auch der Aufgabenbereich angezeigt.

     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]

## <a name="test-the-add-in"></a>Testen des Add-ins
 Wenn Sie das Projekt ausführen, wird PowerPoint geöffnet, und das VSTO-Add-In zeigt den benutzerdefinierten Aufgabenbereich an. Klicken Sie auf das <xref:System.Windows.Forms.MonthCalendar> -Steuerelement, um den Code zu testen.

### <a name="to-test-your-vsto-add-in"></a>So testen Sie Ihr VSTO-Add-In

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Vergewissern Sie sich, dass der benutzerdefinierte Aufgabenbereich sichtbar ist.

3. Klicken Sie im <xref:System.Windows.Forms.MonthCalendar> -Steuerelement des Aufgabenbereichs auf ein Datum.

     Das Datum wird in die erste Folie der aktiven Präsentation eingefügt.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen über das Erstellen von benutzerdefinierten Aufgabenbereichen finden Sie in diesen Themen:

- Erstellen Sie einen benutzerdefinierten Aufgabenbereich in einem VSTO-Add-in für eine andere Anwendung. Weitere Informationen zu den Anwendungen, die benutzerdefinierte Aufgabenbereiche unterstützen, finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

- Erstellen einer Menübandschaltfläche, mit der ein benutzerdefinierter Aufgabenbereich ausgeblendet oder angezeigt werden kann. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Menü Band Schaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

- Erstellen eines benutzerdefinierten Aufgabenbereichs für jede E-Mail-Nachricht, die in Outlook geöffnet wird. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen von benutzerdefinierten Aufgabenbereichen mit e-Mails in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Weitere Informationen
- [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)
- [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Exemplarische Vorgehensweise: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Menü Band Schaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen mit e-Mails in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
