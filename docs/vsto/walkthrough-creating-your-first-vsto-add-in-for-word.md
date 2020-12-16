---
title: 'Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Word'
description: Erstellen Sie ein Add-in auf Anwendungsebene für Microsoft Word. Diese Funktion ist für die Anwendung selbst verfügbar, unabhängig davon, welche Dokumente geöffnet sind.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc136b1c58f9c627787045b1259d07e27a6b8ad
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527874"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Word
  Diese exemplarischen Vorgehensweise bietet eine Einführung in das Erstellen eines VSTO-Add-Ins für Microsoft Office Word. Die Features, die Sie in dieser Art von Projektmappe erstellen, sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welche Dokumente geöffnet sind.

 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines VSTO-Add-In-Projekts.

- Schreiben von Code, in dem das Word-Objektmodell zum Hinzufügen von Text zu einem Dokument beim Speichern verwendet wird.

- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.

- Bereinigen des abgeschlossenen Projekts, damit das VSTO-Add-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Erstellen des Projekts

### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>So erstellen Sie ein neues Word VSTO-Add-In-Projekt in Visual Studio

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic** und dann **Office/SharePoint**.

4. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.

5. Wählen Sie in der Liste der Projektvorlagen ein Word VSTO-Add-In-Projekt aus.

6. Geben Sie im Feld **Name den Namen** **FirstWordAddIn** ein.

7. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das **FirstWordAddIn** -Projekt und öffnet die Codedatei "ThisAddIn" im Editor.

## <a name="write-code-to-add-text-to-the-saved-document"></a>Schreiben von Code zum Hinzufügen von Text zum gespeicherten Dokument
 Als Nächstes fügen Sie der Codedatei "ThisAddIn" Code hinzu. Der neue Code verwendet das Word-Objektmodell, um jedem gespeicherten einen Textbaustein hinzuzufügen. Standardmäßig enthält die Codedatei "ThisAddIn" den folgenden generierten Code:

- Eine Teildefinition der `ThisAddIn` -Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Objektmodell von Word. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Der Rest der- `ThisAddIn` Klasse wird in einer ausgeblendeten Codedatei definiert, die nicht geändert werden sollte.

- Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO-Add-In von Word geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO-Add-Ins, wenn es geladen wird, und zum Bereinigen der vom VSTO-Add-In verwendeten Ressourcen, wenn es entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>So fügen Sie dem gespeicherten Dokument einen Textabsatz hinzu

1. Fügen Sie in der Codedatei „ThisAddIn“ der `ThisAddIn` -Klasse den folgenden Code hinzu. Mit dem neuen Code wird ein Ereignishandler für das Ereignis <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> definiert, das ausgelöst wird, wenn ein Dokument gespeichert wird.

    Wenn der Benutzer ein Dokument speichert, fügt der Ereignishandler am Anfang des Dokuments neuen Text hinzu.

    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]

   > [!NOTE]
   > Dieser Code verwendet den Indexwert 1, um auf den ersten Absatz in der Auflistung <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> zuzugreifen. Obwohl Visual Basic und Visual C# auf Null basierende Arrays verwenden, ist die untere Arraygrenze der meisten Auflistungen im Word-Objektmodell 1. Weitere Informationen finden Sie unter [Schreiben von Code in Office](../vsto/writing-code-in-office-solutions.md)-Projektmappen.

2. Wenn Sie C# verwenden, fügen Sie dem `ThisAddIn_Startup` -Ereignishandler den folgenden erforderlichen Code hinzu. Dieser Code wird verwendet, um den `Application_DocumentBeforeSave` -Ereignishandler mit dem <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> -Ereignis zu verbinden.

    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]

   Zum  Ändern des Dokuments beim Speichern wurden in den vorherigen Codebeispielen die folgenden Objekte verwendet:

- Das `Application` -Feld der `ThisAddIn` -Klasse. Das Feld `Application` gibt ein <xref:Microsoft.Office.Interop.Word.Application>-Objekt zurück, das die aktuelle Instanz von Word darstellt.

- Der `Doc` -Parameter des Ereignishandlers für das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> -Ereignis. Der Parameter `Doc` ist ein <xref:Microsoft.Office.Interop.Word.Document>-Objekt, das das gespeicherte Dokument darstellt. Weitere Informationen finden Sie unter [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).

## <a name="test-the-project"></a>Testen des Projekts

### <a name="to-test-the-project"></a>So testen Sie das Projekt

1. Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen.

     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die im Buildausgabeordner des Projekts enthalten ist. Visual Studio erstellt außerdem einen Satz von Registrierungseinträgen, mit deren Hilfe Word das VSTO-Add-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO-Add-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

2. Speichern Sie das aktive Dokument in Word.

3. Stellen Sie sicher, dass dem Dokument der folgende Text hinzugefügt wurde.

     **Dieser Text wurde per Code hinzugefügt.**

4. Schließen Sie Word.

## <a name="clean-up-the-project"></a>Bereinigen des Projekts
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO-Add-In-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO-Add-In weiterhin jedes Mal ausgeführt, wenn Sie Word auf dem Entwicklungscomputer öffnen.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>So bereinigen Sie das abgeschlossene Projekt auf dem Entwicklungscomputer

1. Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie nun ein einfaches VSTO-Add-In für Word erstellt haben, können Sie in den folgenden Themen mehr über die Entwicklung von VSTO-Add-Ins erfahren:

- Allgemeine Programmieraufgaben, die Sie in VSTO-Add-Ins ausführen können: [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).

- Programmieraufgaben, die für Word-VSTO-Add-ins spezifisch sind: [Word](../vsto/word-solutions.md)-Projektmappen.

- Verwenden des Word-Objektmodells: [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).

- Anpassen der Benutzeroberfläche von Word, z. b. durch Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder Erstellen eines eigenen benutzerdefinierten Aufgabenbereichs: [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

- Erstellen und Debuggen von VSTO-Add-Ins für Word: [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen

- Bereitstellen von VSTO-Add-Ins für Word: bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Word-Lösungen](../vsto/word-solutions.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
