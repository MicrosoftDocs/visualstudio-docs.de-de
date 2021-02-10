---
title: 'Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project'
description: Erstellen Sie ein Add-in auf Anwendungsebene für Microsoft Project. Diese Funktion ist für die Anwendung selbst verfügbar, unabhängig davon, welche Projekte geöffnet sind.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f35649db5f61cb545bb3550980b3d6b9a8742cd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966499"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project
  In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein VSTO-Add-in für Microsoft Office Projekt erstellen. Die Features, die Sie in dieser Art von Projektmappe erstellen, sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welche Projekte geöffnet sind. Weitere Informationen finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO-&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines VSTO-Add-In-Projekts für Project.

- Schreiben von Code, der das Objektmodell von Project verwendet, um eine Aufgabe zu einem neuen Projekt hinzuzufügen.

- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.

- Bereinigen des abgeschlossenen Projekts, damit das VSTO-Add-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] oder [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen des Projekts

### <a name="to-create-a-new-project-in-visual-studio"></a>So erstellen Sie ein neues Projekt in Visual Studio

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic** und dann **Office/SharePoint**.

4. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.

5. Wählen Sie in der Liste mit den Projektvorlagen **Project 2010-Add-In** oder **Project 2013-Add-In** aus.

6. Geben Sie im Feld **Name** den Text **FirstProjectAddIn** ein.

7. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das **FirstProjectAddIn** -Projekt und öffnet die Codedatei **ThisAddIn** im Editor.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Schreiben von Code, der einem Projekt eine neue Aufgabe hinzufügt
 Als Nächstes fügen Sie der Codedatei "ThisAddIn" Code hinzu. Der neue Code verwendet das Objektmodell von Project, um eine neue Aufgabe zu einem Projekt hinzuzufügen. Standardmäßig enthält die Codedatei "ThisAddIn" den folgenden generierten Code:

- Eine Teildefinition der `ThisAddIn` -Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Objektmodell von Project. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Der Rest der- `ThisAddIn` Klasse wird in einer ausgeblendeten Codedatei definiert, die nicht geändert werden sollte.

- Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO-Add-In von Project geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO-Add-Ins, wenn es geladen wird, und zum Bereinigen der vom VSTO-Add-In verwendeten Ressourcen, wenn es entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="to-add-a-task-to-a-new-project"></a>So fügen Sie eine Aufgabe zu einem neuen Projekt hinzu

1. Fügen Sie in der Codedatei „ThisAddIn“ der `ThisAddIn` -Klasse den folgenden Code hinzu. Dieser Code definiert einen Ereignishandler für das `NewProject`-Ereignis der `Microsoft.Office.Interop.MSProject.Application`-Klasse.

    Wenn der Benutzer ein neues Projekt erstellt, fügt dieser Ereignishandler eine Aufgabe zum Projekt hinzu.

    [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]

   In diesem Codebeispiel werden die folgenden Objekte verwendet, um das Projekt zu ändern:

- Das `Application` -Feld der `ThisAddIn` -Klasse. Das `Application`-Feld gibt ein `Microsoft.Office.Interop.MSProject.Application`-Objekt zurück, das für die aktuelle Instanz von Project steht.

- Der- `pj` Parameter des Ereignis Handlers für das NewProject-Ereignis. Der `pj`-Parameter ist ein `Microsoft.Office.Interop.MSProject.Project`-Objekt, das das Projekt darstellt. Weitere Informationen finden Sie unter [Project Solutions](../vsto/project-solutions.md).

1. Wenn Sie C# verwenden, fügen Sie dem `ThisAddIn_Startup` -Ereignishandler den folgenden Code hinzu. Dieser Code verbindet den `Application_Newproject` Ereignishandler mit dem NewProject-Ereignis.

     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]

## <a name="test-the-project"></a>Testen des Projekts
 Wenn Sie das Projekt erstellen und ausführen, stellen Sie sicher, dass die neue Aufgabe in dem sich ergebenden neuen Projekt angezeigt wird.

### <a name="to-test-the-project"></a>So testen Sie das Projekt

1. Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen. Microsoft Project startet und öffnet automatisch ein neues leeres Projekt.

     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die im Buildausgabeordner des Projekts enthalten ist. Visual Studio erstellt auch einen Satz von Registrierungseinträgen, mit deren Hilfe Project das VSTO-Add-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO-Add-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Übersicht über den Buildprozess für Office-Lösungen](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).

2. Stellen Sie sicher, dass dem leeren Projekt eine neue Aufgabe hinzugefügt wird.

3. Stellen Sie sicher, dass der folgende Text im Feld **Aufgabenname** der Aufgabe angezeigte.

     **Dieser Text wurde per Code hinzugefügt.**

4. Schließen Sie Microsoft Project.

## <a name="clean-up-the-project"></a>Bereinigen des Projekts
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO-Add-In-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO-Add-In jedes Mal ausgeführt, wenn Sie Microsoft Project auf dem Entwicklungscomputer öffnen.

### <a name="to-clean-up-your-project"></a>So bereinigen Sie das Projekt

1. Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie nun ein einfaches VSTO-Add-In für Project erstellt haben, können Sie in den folgenden Themen mehr über die Entwicklung von VSTO-Add-Ins erfahren:

- Allgemeine Programmieraufgaben, die Sie in VSTO-Add-Ins für Project ausführen können: [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).

- Verwenden des Objektmodells von Project: [Projekt](../vsto/project-solutions.md)Mappen.

- Erstellen und Debuggen von VSTO-Add-Ins für Project: [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen

- Bereitstellen von VSTO-Add-Ins für Project: bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Projektmappen](../vsto/project-solutions.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
