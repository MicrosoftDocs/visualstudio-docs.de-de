---
title: Erstellen Sie Ihre erste Anpassung auf Dokument Ebene für Excel
description: Erstellen Sie eine Anpassung auf Dokument Ebene für Microsoft Excel. Die Features, die Sie in dieser Art von Projektmappe erstellen, sind nur verfügbar, wenn eine bestimmte Arbeitsmappe geöffnet ist.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ae0f4982ca325970b8b7965c956a7d2dea4bf60f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966668"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Excel

  Diese exemplarische Vorgehensweise bietet eine Einführung zum Erstellen einer Anpassung auf Dokumentebene für Microsoft Office Excel. Die Features, die Sie in dieser Art von Projektmappe erstellen, sind nur verfügbar, wenn eine bestimmte Arbeitsmappe geöffnet ist. Sie können eine Anpassung auf Dokumentebene nicht verwenden, um anwendungsweite Änderungen vorzunehmen, z. B., um eine neue Registerkarte des Menübands anzuzeigen, wenn eine Arbeitsmappe geöffnet ist.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Excel-Arbeitsmappenprojekts.

- Hinzufügen von Text zu einem Arbeitsblatt, das im Visual Studio-Designer gehostet wird.

- Schreiben von Code, der das Excel-Objektmodell zum Hinzufügen von Text zum angepassten Arbeitsblatt verwendet, wenn dieses geöffnet wird.

- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.

- Bereinigen des abgeschlossenen Projekts zum Entfernen nicht benötigter Builddateien und Sicherheitseinstellungen vom Entwicklungscomputer.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen

 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen des Projekts

### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>So erstellen Sie ein neues Excel-Arbeitsmappenprojekt in Visual Studio

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.
::: moniker range="vs-2017"
3. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic** und dann **Office/SharePoint**.

4. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **VSTO-Add-ins** aus.

5. Wählen Sie in der Liste der Projektvorlagen ein Excel-VSTO-Arbeitsmappenprojekt aus.

6. Geben Sie im Feld **Name den Namen** **firstworkbookcustomia** ein.

7. Klicken Sie auf **OK**.

8. Wählen Sie im **Assistenten für Visual Studio-Tools für Office-Projekte** die Option **Neues Dokument erstellen** aus, und klicken Sie auf **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
3. Wählen Sie im Dialogfeld **Neues Projekt erstellen** das **Excel-VSTO** -Arbeitsmappenprojekt aus.

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Klicken Sie auf **Weiter**.

5. Geben Sie im Dialogfeld **Neues Projekt konfigurieren** im Feld **Name** den Text **firstworkbookcustomia** ein, und klicken Sie auf **Erstellen**.

6. Wählen Sie im **Assistenten für Visual Studio-Tools für Office-Projekte** die Option **Neues Dokument erstellen** aus, und klicken Sie auf **OK**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Projekt **firstworkbookcustomiund** fügt dem Projekt die folgenden Dateien hinzu.

   - *Firstworkbookcustomi.* xlsx: stellt die Excel-Arbeitsmappe im Projekt dar. Enthält alle Arbeitsblätter und Diagramme.

   - Sheet1 (*VB* -Datei für Visual Basic-oder *CS* -Datei für Visual c#): ein Arbeitsblatt, das die Entwurfs Oberfläche und den Code für das erste Arbeitsblatt in der Arbeitsmappe bereitstellt. Weitere Informationen finden Sie unter [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md).

   - Tabelle2 (*VB* -Datei für Visual Basic-oder *CS* -Datei für Visual c#): ein Arbeitsblatt, das die Entwurfs Oberfläche und den Code für das zweite Arbeitsblatt in der Arbeitsmappe bereitstellt.

   - Tabelle3 (*VB* -Datei für Visual Basic-oder *CS* -Datei für Visual c#): ein Arbeitsblatt, das die Entwurfs Oberfläche und den Code für das dritte Arbeitsblatt in der Arbeitsmappe bereitstellt.

   - ThisWorkbook (*VB* -Datei für Visual Basic-oder *CS* -Datei für Visual c#): enthält die Entwurfs Oberfläche und den Code für Anpassungen auf Arbeitsmappenebene. Weitere Informationen finden Sie unter [Arbeitsmappenhostelement](../vsto/workbook-host-item.md).

     Die Codedatei "Sheet1" wird automatisch im Designer geöffnet.

## <a name="close-and-reopen-worksheets-in-the-designer"></a>Schließen und erneutes Öffnen von Arbeitsblättern im Designer

 Wenn Sie eine Arbeitsmappe oder ein Arbeitsblatt absichtlich oder versehentlich im Designer schließen, während Sie das Projekt entwickeln, können Sie sie bzw. es erneut öffnen.

### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>So schließen Sie ein Arbeitsblatt im Designer und öffnen es erneut

1. Schließen Sie die Arbeitsmappe, indem Sie auf die Schaltfläche **Schließen** (X) für das Fenster "Designer" klicken.

2. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Codedatei **Sheet1** , und klicken Sie dann auf **Designer anzeigen**.

     \- oder -

     Doppelklicken Sie in **Projektmappen-Explorer** auf die **Sheet1** -Codedatei.

## <a name="add-text-to-a-worksheet-in-the-designer"></a>Hinzufügen von Text zu einem Arbeitsblatt im Designer

 Sie können die Benutzeroberfläche (User Interface, UI) Ihrer Anpassung gestalten, indem Sie das im Designer geöffnete Arbeitsblatt ändern. Beispielsweise können Sie Zellen Text hinzufügen, Formeln anwenden oder Excel-Steuerelemente hinzufügen. Weitere Informationen zur Verwendung des Designers finden Sie unter Office- [Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>So fügen Sie einem Arbeitsblatt mithilfe des Designers Text hinzu

1. Wählen Sie im Arbeitsblatt, das im Designer geöffnet ist, Zelle **a1** aus, und geben Sie dann den folgenden Text ein.

     **Dieser Text wurde mithilfe des Designers hinzugefügt.**

> [!WARNING]
> Wenn Sie diese Textzeile der Zelle **a2** hinzufügen, wird Sie von anderem Code in diesem Beispiel überschrieben.

## <a name="add-text-to-a-worksheet-programmatically"></a>Programm gesteuertes Hinzufügen von Text zu einem Arbeitsblatt

 Als Nächstes fügen Sie der Codedatei "Sheet1" Code hinzu. Der neue Code verwendet das Excel-Objektmodell, um der Arbeitsmappe eine zweite Textzeile hinzuzufügen. Standardmäßig enthält die Codedatei "Sheet1" den folgenden generierten Code:

- Eine partielle Definition der `Sheet1`-Klasse, die das Programmiermodell des Arbeitsblatts darstellt und den Zugriff auf das Excel-Objektmodell bereitstellt. Weitere Informationen finden Sie unter [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md) und [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md). Der Rest der `Sheet1` -Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.

- Die Ereignishandler `Sheet1_Startup` und `Sheet1_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihre Anpassung von Excel geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren der Anpassung, wenn sie geladen wird, und zum Bereinigen der von der Anpassung verwendeten Ressourcen, wenn sie entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>So fügen Sie dem Arbeitsblatt mithilfe von Code eine zweite Textzeile hinzu

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **Sheet1**, und klicken Sie dann auf **Code anzeigen**.

     Die Codedatei wird in Visual Studio geöffnet.

2. Ersetzen Sie den `Sheet1_Startup` -Ereignishandler durch den folgenden Code. Beim Öffnen von "Sheet1" wird dem Arbeitsblatt durch diesen Code eine zweite Textzeile hinzugefügt.

     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]

## <a name="test-the-project"></a>Testen des Projekts

### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe

1. Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen.

     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die der Arbeitsmappe zugeordnet ist. Visual Studio legt eine Kopie der Arbeitsmappe und der Assembly im Buildausgabeordner für das Projekt ab und konfiguriert die Sicherheitseinstellungen auf dem Entwicklungscomputer, damit die Anpassung ausgeführt werden kann. Weitere Informationen finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

2. Vergewissern Sie sich, dass der folgende Text in der Arbeitsmappe angezeigt wird.

     **Dieser Text wurde mithilfe des Designers hinzugefügt.**

     **Dieser Text wurde per Code hinzugefügt.**

3. Schließen Sie die Arbeitsmappe.

## <a name="clean-up-the-project"></a>Bereinigen des Projekts

 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, sollten Sie die Dateien im Buildausgabeordner und die Sicherheitseinstellungen entfernen, die durch den Buildvorgang erstellt wurden.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>So bereinigen Sie das abgeschlossene Projekt auf dem Entwicklungscomputer

1. Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.

## <a name="next-steps"></a>Nächste Schritte

 Da Sie nun eine grundlegende Anpassung auf Dokumentebene für Excel erstellt haben, können Sie mehr über die Entwicklung von Anpassungen in den folgenden Themen erfahren:

- Allgemeine Programmieraufgaben, die Sie in Anpassungen auf Dokument Ebene durchführen können: [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md).

- Programmieraufgaben, die für Anpassungen auf Dokument Ebene für Excel-Lösungen spezifisch sind: [Excel-Lösungen](../vsto/excel-solutions.md).

- Verwenden des Objektmodells von Excel: [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md).

- Anpassen der Benutzeroberfläche von Excel, z. b. durch Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder Erstellen eines eigenen Aktionsbereichs: [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

- Verwenden erweiterter Excel-Objekte, die von Office-Entwicklungs Tools in Visual Studio bereitgestellt werden, um Aufgaben auszuführen, die mithilfe des Excel-Objektmodells nicht möglich sind (z. b. das Hosting von verwalteten Steuerelementen in Dokumenten und das Binden von Excel-Steuerelementen an Daten mithilfe des Windows Forms Daten Bindungs Modells): [Automatisieren von Excel mithilfe](../vsto/automating-excel-by-using-extended-objects.md)von

- Erstellen und Debuggen von Anpassungen auf Dokument Ebene für Excel: [Erstellen Sie Office](../vsto/building-office-solutions.md)-Projektmappen.

- Bereitstellen von Anpassungen auf Dokument Ebene für Excel: bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Excel-Lösungen](../vsto/excel-solutions.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
- [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
