---
title: 'Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook'
description: Erstellen Sie ein Add-in auf Anwendungsebene für Microsoft Outlook. Diese Funktion ist für die Anwendung selbst verfügbar, unabhängig davon, welches Outlook-Element geöffnet ist.
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
- Outlook [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7950858d3205cf910eb09e5b0a99b5f67c71c4bd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524229"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook
  Diese exemplarische Vorgehensweise veranschaulicht die Erstellung eines VSTO-Add-Ins für Microsoft Office Outlook. Die in dieser Art von Projektmappe erstellten Features sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welches Outlook-Element geöffnet sind. Weitere Informationen finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO-&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines VSTO-Add-In-Projekts für Outlook

- Schreiben von Code, der das Outlook-Objektmodell verwendet, um der Betreffzeile und dem Textkörper einer neuen E-Mail Text hinzuzufügen

- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.

- Bereinigen des abgeschlossenen Projekts, damit das VSTO-Add-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-the-project"></a>Erstellen des Projekts

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>So erstellen Sie ein neues Outlook-Projekt in Visual Studio

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic** und dann **Office/SharePoint**.

4. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.

5. Wählen Sie in der Liste der Projektvorlagen ein Outlook-VSTO-Add-In-Projekt aus.

6. Geben Sie im Feld **Name** den Text **FirstOutlookAddIn** ein.

7. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das **FirstOutlookAddIn** -Projekt und öffnet die Codedatei " **ThisAddIn** " im Editor.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Schreiben von Code, der jeder neuen e-Mail-Nachricht Text hinzufügt
 Als Nächstes fügen Sie der Codedatei "ThisAddIn" Code hinzu. Der neue Code verwendet das Outlook-Objektmodell, um jeder neuen E-Mail Text hinzuzufügen. Standardmäßig enthält die Codedatei "ThisAddIn" den folgenden generierten Code:

- Eine Teildefinition der `ThisAddIn` -Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Outlook-Objektmodell. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Der Rest der- `ThisAddIn` Klasse wird in einer ausgeblendeten Codedatei definiert, die nicht geändert werden sollte.

- Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO-Add-In von Outlook geladen oder entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO-Add-Ins, wenn es geladen wird, und zum Bereinigen der vom VSTO-Add-In verwendeten Ressourcen, wenn es entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>So fügen Sie der Betreffzeile und dem Textkörper jeder neuen E-Mail Text hinzu

1. Deklarieren Sie in der ThisAddIn-Codedatei ein Feld namens `inspectors` in der `ThisAddIn` -Klasse. Das `inspectors` -Feld behält einen Verweis auf die Auflistung von Inspektor-Fenstern in der aktuellen Outlook-Instanz. Dieser Verweis verhindert, dass der Garbage Collector den Speicher freigibt, der den Ereignishandler für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> -Ereignis enthält.

    [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]

2. Ersetzen Sie die `ThisAddIn_Startup`-Methode durch den folgenden Code. Dieser Code fügt einen Ereignishandler an das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> -Ereignis an.

    [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
    [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]

3. Fügen Sie in der Codedatei „ThisAddIn“ der `ThisAddIn` -Klasse den folgenden Code hinzu. Dieser Code definiert einen Ereignishandler für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> -Ereignis.

    Wenn der Benutzer eine neue E-Mail erstellt, fügt dieser Ereignishandler der Betreffzeile und dem Textkörper der Nachricht Text hinzu.

    [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
    [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]

   Zum Ändern der einzelnen neuen E-Mails werden in den vorherigen Codebeispielen die folgenden Objekte verwendet:

- Das `Application` -Feld der `ThisAddIn` -Klasse. Das `Application` -Feld gibt ein <xref:Microsoft.Office.Interop.Outlook.Application> -Objekt zurück, das für die aktuelle Instanz von Outlook steht.

- Der `Inspector` -Parameter des Ereignishandlers für das <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> -Ereignis. Der `Inspector` -Parameter ist ein <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekt, das das Inspektorfenster der neuen E-Mail darstellt. Weitere Informationen finden Sie unter [Outlook-Lösungen](../vsto/outlook-solutions.md).

## <a name="test-the-project"></a>Testen des Projekts
 Wenn Sie das Projekt erstellen und ausführen, stellen Sie sicher, dass der Text in der Betreffzeile und dem Textkörper der neuen E-Mail angezeigt wird.

### <a name="to-test-the-project"></a>So testen Sie das Projekt

1. Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen.

     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die im Buildausgabeordner des Projekts enthalten ist. Visual Studio erstellt auch einen Satz von Registrierungseinträgen, mit deren Hilfe Outlook das VSTO-Add-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO-Add-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Übersicht über den Buildprozess für Office-Lösungen](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).

2. Erstellen Sie in Outlook eine neue E-Mail.

3. Stellen Sie sicher, dass der folgende Text sowohl der Betreffzeile als auch dem Textkörper der Nachricht hinzugefügt wird.

     **Dieser Text wurde per Code hinzugefügt.**

4. Schließen Sie Outlook.

## <a name="clean-up-the-project"></a>Bereinigen des Projekts
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO-Add-In-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO-Add-In jedes Mal ausgeführt, wenn Sie Outlook auf dem Entwicklungscomputer öffnen.

### <a name="to-clean-up-your-project"></a>So bereinigen Sie das Projekt

1. Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie nun ein einfaches VSTO-Add-In für Outlook erstellt haben, erfahren Sie in den folgenden Themen mehr über die Entwicklung von VSTO-Add-Ins:

- Allgemeine Programmieraufgaben, die Sie ausführen können, indem Sie VSTO-Add-Ins für Outlook verwenden. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Verwenden des Outlook-Objektmodells. Weitere Informationen finden Sie unter [Outlook-Lösungen](../vsto/outlook-solutions.md).

- Anpassen der Outlook-Benutzeroberfläche (UI) beispielsweise durch das Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder durch das Erstellen eines eigenen benutzerdefinierten Aufgabenbereichs. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

- Erstellen und Debuggen von VSTO-Add-Ins für Outlook. Weitere Informationen finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

- Bereitstellen von VSTO-Add-Ins für Outlook. Weitere Informationen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Outlook-Lösungen](../vsto/outlook-solutions.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
