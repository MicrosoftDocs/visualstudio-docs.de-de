---
title: 'Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel'
description: Erstellen Sie ein Add-in auf Anwendungsebene für Microsoft Excel. Die von Ihnen erstellten Funktionen sind für die Anwendung selbst verfügbar, unabhängig davon, welche Arbeitsmappen geöffnet sind.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f04532e627a694e8a234f1842995b92a707e537
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527912"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel
  Diese exemplarische Vorgehensweise zur Einführung veranschaulicht, wie Sie ein Add-In auf Anwendungsebene für Microsoft Office Excel erstellen. Die Funktionen, die Sie in dieser Art von Projektmappe erstellen, sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welche Arbeitsmappen geöffnet sind.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen Sie ein Excel-VSTO-Add-In-Projekt für Excel.

- Schreiben Sie Code, in dem das Excel-Objektmodell zum Hinzufügen von Text zu einer Arbeitsmappe beim Speichern verwendet wird.

- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.

- Bereinigen des abgeschlossenen Projekts, damit das VSTO-Add-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen des Projekts

#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>So erstellen Sie ein neues Excel-VSTO-Add-In-Projekt in Visual Studio

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic** und dann **Office/SharePoint**.

4. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.

5. Wählen Sie in der Liste mit den Projektvorlagen **Excel 2010-Add-In** oder **Excel 2013-Add-In** aus.

6. Geben Sie im Feld **Name** den Text **FirstExcelAddIn** ein.

7. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das **FirstExcelAddIn** -Projekt und öffnet die Codedatei "ThisAddIn" im Editor.

## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Schreiben von Code zum Hinzufügen von Text zur gespeicherten Arbeitsmappe
 Als Nächstes fügen Sie der Codedatei "ThisAddIn" Code hinzu. Der neue Code verwendet das Objektmodell von Excel, um einen Textbaustein in die erste Zeile des aktiven Arbeitsblatts einzufügen. Das aktive Arbeitsblatt ist das Arbeitsblatt, das geöffnet ist, wenn Benutzer die Arbeitsmappe speichern. Standardmäßig enthält die Codedatei "ThisAddIn" den folgenden generierten Code:

- Eine Teildefinition der `ThisAddIn` -Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Objektmodell von Excel. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Der Rest der- `ThisAddIn` Klasse wird in einer ausgeblendeten Codedatei definiert, die nicht geändert werden sollte.

- Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO-Add-In von Excel geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO-Add-Ins, wenn es geladen wird, und zum Bereinigen von Ressourcen, die vom Add-In verwendet werden, wenn es entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>So fügen Sie der gespeicherten Arbeitsmappe eine Textzeile hinzu

1. Fügen Sie in der Codedatei „ThisAddIn“ der `ThisAddIn` -Klasse den folgenden Code hinzu. Mit dem neuen Code wird ein Ereignishandler für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> -Ereignis definiert, das ausgelöst wird, wenn eine Arbeitsmappe gespeichert wird.

    Wenn der Benutzer eine Arbeitsmappe speichert, fügt der Ereignishandler am Anfang des aktiven Arbeitsblatts neuen Text hinzu.

    [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]

2. Wenn Sie C# verwenden, fügen Sie dem `ThisAddIn_Startup` -Ereignishandler den folgenden erforderlichen Code hinzu. Dieser Code wird verwendet, um den `Application_WorkbookBeforeSave` -Ereignishandler mit dem <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> -Ereignis zu verbinden.

    [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]

   Um die Arbeitsmappe beim Speichern zu ändern, wurden in den vorherigen Codebeispielen die folgenden Objekte verwendet:

- Das `Application` -Feld der `ThisAddIn` -Klasse. Das Feld `Application` gibt ein <xref:Microsoft.Office.Interop.Excel.Application> -Objekt zurück, das für die aktuelle Instanz von Excel steht.

- Der `Wb` -Parameter des Ereignishandlers für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> -Ereignis. Der Parameter `Wb` ist ein <xref:Microsoft.Office.Interop.Excel.Workbook> -Objekt, das für die gespeicherte Arbeitsmappe steht. Weitere Informationen finden Sie unter [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).

## <a name="test-the-project"></a>Testen des Projekts

### <a name="to-test-the-project"></a>So testen Sie das Projekt

1. Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen.

     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die im Buildausgabeordner des Projekts enthalten ist. Visual Studio erstellt auch einen Satz von Registrierungseinträgen, mit deren Hilfe Excel das VSTO-Add-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO-Add-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

2. Speichern Sie die Arbeitsmappe in Excel.

3. Stellen Sie sicher, dass der Arbeitsmappe der folgende Text hinzugefügt wurde.

     **Dieser Text wurde per Code hinzugefügt.**

4. Schließen Sie Excel.

## <a name="clean-up-the-project"></a>Bereinigen des Projekts
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO-Add-In-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO-Add-In weiterhin jedes Mal ausgeführt, wenn Sie Excel auf dem Entwicklungscomputer öffnen.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>So bereinigen Sie das abgeschlossene Projekt auf dem Entwicklungscomputer

1. Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie nun ein einfaches VSTO-Add-In für Excel erstellt haben, können Sie in den folgenden Themen mehr über die Entwicklung von VSTO-Add-Ins erfahren:

- Allgemeine Programmieraufgaben, die Sie in VSTO-Add-Ins ausführen können: [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).

- Programmieraufgaben, die für Excel-VSTO-Add-ins spezifisch sind: [Excel-Lösungen](../vsto/excel-solutions.md).

- Verwenden des Objektmodells von Excel: [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).

- Anpassen der Benutzeroberfläche (UI) von Excel, z. b. durch Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder Erstellen eines eigenen benutzerdefinierten Aufgabenbereichs: [Anpassung der Office](../vsto/office-ui-customization.md)-Benutzeroberfläche.

- Erstellen und Debuggen von VSTO-Add-Ins für Excel: [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen

- Bereitstellen von VSTO-Add-Ins für Excel: bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel-Lösungen](../vsto/excel-solutions.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
