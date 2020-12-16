---
title: 'Exemplarische Vorgehensweise: Abrufen von Code in einem VSTO-Add-in aus VBA'
description: Erfahren Sie, wie Sie ein Objekt in einem VSTO-Add-in für andere Microsoft Office Lösungen verfügbar machen, einschließlich Visual Basic for Applications (VBA) und com-VSTO-Add-Ins.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0cbf03ef234ea6cf4eab790d96082d23b7ed5199
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527284"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Exemplarische Vorgehensweise: Abrufen von Code in einem VSTO-Add-in aus VBA
  Diese exemplarische Vorgehensweise veranschaulicht, wie ein Objekt in einem VSTO-Add-In für andere Microsoft Office-Projektmappen verfügbar gemacht wird, einschließlich Visual Basic for Applications (VBA) und COM-VSTO-Add-Ins.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Obwohl in dieser exemplarischen Vorgehensweise speziell Excel verwendet wird, gelten die veranschaulichten Konzepte für alle VSTO-Add-In-Projektvorlagen, die von Visual Studio bereitgestellt werden.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Definieren einer Klasse, die für andere Office-Projektmappen verfügbar gemacht werden kann

- Verfügbarmachen der Klasse für andere Office-Projektmappen

- Aufrufen einer Methode der Klasse aus VBA-Code

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>Erstellen des VSTO-Add-in-Projekts
 Der erste Schritt ist das Erstellen eines VSTO-Add-In-Projekts für Excel.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein VSTO-Add-In-Projekt für Excel namens **ExcelImportData**, indem Sie die Excel-VSTO-Add-In-Projektvorlage verwenden. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Codedatei **ThisAddIn.cs** oder **ThisAddIn.vb** und fügt das **ExcelImportData** -Projekt dem **Projektmappen-Explorer** hinzu.

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definieren einer Klasse, die für andere Office-Projektmappen verfügbar gemacht werden kann
 Der Zweck dieser exemplarischen Vorgehensweise besteht im Aufrufen der `ImportData` -Methode einer Klasse mit dem Namen `AddInUtilities` in Ihrem VSTO-Add-In aus VBA-Code. Mit dieser Methode wird eine Zeichenfolge in die Zelle A1 des aktiven Arbeitsblatts geschrieben.

 Um die `AddInUtilities` -Klasse für andere Office-Projektmappen verfügbar zu machen, müssen Sie die Klasse öffentlich und für COM sichtbar machen. Außerdem müssen Sie die [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) -Schnittstelle in der Klasse verfügbar machen. Mit dem Code in der folgenden Prozedur wird eine Möglichkeit zum Erfüllen dieser Anforderungen veranschaulicht. Weitere Informationen finden Sie unter [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>So definieren Sie eine Klasse, die für andere Office-Projektmappen verfügbar gemacht werden kann

1. Klicken Sie im Menü **Projekt** auf **Klasse hinzufügen**.

2. Ändern Sie im Dialogfeld **Neues Element hinzufügen** den Namen der neuen Klasse in **AddInUtilities**, und klicken Sie auf **Hinzufügen**.

     Die Datei **AddInUtilities.cs** oder **AddInUtilities.vb** wird im Code-Editor geöffnet.

3. Fügen Sie am Anfang der Datei die folgenden-Direktiven hinzu.

     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]

4. Ersetzen Sie die `AddInUtilities` -Klasse durch den folgenden Code.

     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]

     Mit diesem Code wird die `AddInUtilities` -Klasse für COM sichtbar, und die `ImportData` -Methode wird der Klasse hinzugefügt. Zum Verfügbarmachen der [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) -Schnittstelle verfügt die `AddInUtilities` -Klasse auch über das <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> -Attribut und implementiert eine Schnittstelle, die für COM sichtbar ist.

## <a name="expose-the-class-to-other-office-solutions"></a>Verfügbar machen der Klasse für andere Office-Projektmappen
 Um die `AddInUtilities` -Klasse für andere Office-Projektmappen verfügbar zu machen, setzen Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> -Methode in der `ThisAddIn` -Klasse außer Kraft. Geben Sie bei der Außerkraftsetzung eine Instanz der `AddInUtilities` -Klasse zurück.

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>So machen Sie die AddInUtilities-Klasse für andere Office-Projektmappen verfügbar

1. Erweitern Sie im **Projektmappen-Explorer** die Option **Excel**.

2. Klicken Sie mit der rechten Maustaste auf **ThisAddIn.cs** bzw. **ThisAddIn.vb**, und klicken Sie dann auf **Code anzeigen**.

3. Fügen Sie der `ThisAddIn` -Klasse den folgenden Code hinzu.

     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]

4. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

     Überprüfen Sie, ob die Lösung ohne Fehler erstellt wurde.

## <a name="test-the-vsto-add-in"></a>Testen des VSTO-Add-ins
 Sie können die `AddInUtilities` -Klasse aus unterschiedlichen Arten von Office-Projektmappen aufrufen. In dieser exemplarischen Vorgehensweise verwenden Sie VBA-Code in einer Excel-Arbeitsmappe. Weitere Informationen zu den anderen Typen von Office-Projektmappen, die Sie ebenfalls verwenden können, finden Sie unter [callcode in VSTO-Add-Ins aus anderen Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)-Projektmappen.

### <a name="to-test-your-vsto-add-in"></a>So testen Sie Ihr VSTO-Add-In

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Speichern Sie in Excel die aktive Arbeitsmappe als Excel-Arbeitsmappe mit Makros (*.xlsm). Speichern Sie sie an einem geeigneten Speicherort, z. B. auf dem Desktop.

3. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Klicken Sie in der Gruppe **Code** auf **Visual Basic**.

     Der Visual Basic-Editor wird geöffnet.

5. Doppelklicken Sie im **Projektfenster** auf **DieseArbeitsmappe**.

     Die Codedatei für das `ThisWorkbook` -Objekt wird geöffnet.

6. Fügen Sie der Codedatei den folgenden VBA-Code hinzu. Mit diesem Code wird zuerst ein COMAddIn-Objekt abgerufen, das das **ExcelImportData** -VSTO-Add-in darstellt. Anschließend wird im Code die Object-Eigenschaft des COMAddIn-Objekts verwendet, um die-Methode aufzurufen `ImportData` .

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. Drücken Sie **F5**.

8. Überprüfen Sie, ob der Arbeitsmappe ein neues Arbeitsblatt mit dem Namen **Imported Data** hinzugefügt wurde. Überprüfen Sie auch, ob die Zelle A1 die Zeichenfolge **This is my data** enthält.

9. Beenden Sie Excel.

## <a name="next-steps"></a>Nächste Schritte
 In den folgenden Themen erhalten Sie weitere Informationen zum Programmieren von VSTO-Add-Ins:

- Verwenden Sie die `ThisAddIn` -Klasse zum Automatisieren der Hostanwendung und zum Durchführen anderer Aufgaben in VSTO-Add-In-Projekten. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Erstellen Sie einen benutzerdefinierten Aufgabenbereich in einem VSTO-Add-In. Weitere Informationen finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md) Bereiche und Gewusst [wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

- Passen Sie das Menüband in einem VSTO-Add-in an. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md) und Gewusst [wie: Einstieg in die Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).

## <a name="see-also"></a>Weitere Informationen
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Code in VSTO-Add-Ins aus anderen Office-Projektmappen aufzurufen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Entwickeln von Office-Lösungen](../vsto/developing-office-solutions.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterbarkeits Schnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
