---
title: 'Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für PowerPoint'
description: Erstellen Sie ein Add-in auf Anwendungsebene für Microsoft PowerPoint. Diese Funktion ist für die Anwendung selbst verfügbar, unabhängig davon, welche Präsentationen geöffnet sind.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c73c5ab61c51ca4be749e9bf14700c7bea64023e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966538"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für PowerPoint
  In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein VSTO-Add-in für Microsoft Office PowerPoint erstellen. Die Funktionen, die Sie in dieser Art von Projektmappe erstellen, sind für die Anwendung selbst verfügbar. Dabei spielt es keine Rolle, welche Präsentationen geöffnet sind. Weitere Informationen finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO-&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines PowerPoint-VSTO-Add-In-Projekts für PowerPoint

- Schreiben von Code, der das PowerPoint-Objektmodell verwendet, um jeder neuen Folie ein Textfeld hinzuzufügen

- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.

- Bereinigen des Projekts, sodass das VSTO-Add-In nicht mehr automatisch auf Ihrem Entwicklungscomputer ausgeführt wird

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>Erstellen des Projekts

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic** und dann **Office/SharePoint**.

4. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.

5. Wählen Sie in der Liste der Projektvorlagen ein PowerPoint-VSTO-Add-In-Projekt aus.

6. Geben Sie im Feld **Name den Namen** **FirstPowerPointAddIn** ein.

7. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das **FirstPowerPointAddIn** -Projekt und öffnet die Codedatei " **ThisAddIn** " im Editor.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>Schreiben von Code, der jeder neuen Folie Text hinzufügt
 Als Nächstes fügen Sie der Codedatei "ThisAddIn" Code hinzu. Der neue Code, verwendet das PowerPoint-Objektmodell, um jeder neuen Folie ein Textfeld hinzuzufügen. Standardmäßig enthält die Codedatei "ThisAddIn" den folgenden generierten Code:

- Eine Teildefinition der `ThisAddIn` -Klasse. Diese Klasse stellt einen Einstiegspunkt für Ihren Code bereit und ermöglicht den Zugriff auf das Objektmodell von PowerPoint. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Der Rest der- `ThisAddIn` Klasse wird in einer ausgeblendeten Codedatei definiert, die nicht geändert werden sollte.

- Die Ereignishandler `ThisAddIn_Startup` und `ThisAddIn_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihr VSTO-Add-In von PowerPoint geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren des VSTO-Add-Ins, wenn es geladen wird, und zum Bereinigen der vom VSTO-Add-In verwendeten Ressourcen, wenn es entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="to-add-a-text-box-to-each-new-slide"></a>So fügen Sie jeder neuen Folie ein Textfeld hinzu

1. Fügen Sie in der Codedatei „ThisAddIn“ der `ThisAddIn` -Klasse den folgenden Code hinzu. Dieser Code definiert einen Ereignishandler für das [Microsoft.Office.Interop.PowerPoint.EApplication_Event. presentationnewfolie](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) -Ereignis des [Anwendungs](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) Objekts.

    Wenn der Benutzer der aktiven Präsentation eine neue Folie hinzufügt, fügt dieser Ereignishandler oben auf der neuen Folie ein Textfeld hinzu und fügt Text in das Textfeld ein.

    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]

2. Wenn Sie C# verwenden, fügen Sie dem `ThisAddIn_Startup` -Ereignishandler den folgenden Code hinzu. Dieser Code ist erforderlich, um den `Application_PresentationNewSlide` Ereignishandler mit dem [Microsoft.Office.Interop.PowerPoint.EApplication_Event. presentationnewfolie](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) -Ereignis zu verbinden.

    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]

   Zum Ändern der einzelnen neuen Folien wurden in den vorherigen Codebeispielen die folgenden Objekte verwendet:

- Das `Application` -Feld der `ThisAddIn` -Klasse. Das- `Application` Feld gibt ein [Anwendungs](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) Objekt zurück, das die aktuelle Instanz von PowerPoint darstellt.

- Der- `Sld` Parameter des Ereignis Handlers für das [Microsoft.Office.Interop.PowerPoint.EApplication_Event. presentationnewfolie](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) -Ereignis. Der- `Sld` Parameter ist ein [Folien](/previous-versions/office/developer/office-2010/ff763417(v=office.14)) Objekt, das die neue Folie darstellt. Weitere Informationen finden Sie unter [PowerPoint-Lösungen](../vsto/powerpoint-solutions.md).

## <a name="test-the-project"></a>Testen des Projekts
 Überprüfen Sie, wenn Sie das Projekt erstellen und ausführen, ob in neuen Folien, die Sie einer Präsentation hinzufügen, das Textfeld angezeigt wird.

### <a name="to-test-the-project"></a>So testen Sie das Projekt

1. Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen.

     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die in den Buildausgabeordner des Projekts eingefügt wird. Visual Studio erstellt auch einen Satz von Registrierungseinträgen, mit deren Hilfe PowerPoint das VSTO-Add-In ermitteln und laden kann. Die Sicherheitseinstellungen auf dem Entwicklungscomputer werden so konfiguriert, dass das VSTO-Add-In ausgeführt werden kann. Weitere Informationen finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

2. Fügen Sie in PowerPoint der aktiven Präsentation eine neue Folie hinzu.

3. Stellen Sie sicher, dass einem neuen Textfeld am oberen Rand der Folie der folgende Text hinzugefügt wird.

     **Dieser Text wurde per Code hinzugefügt.**

4. Schließen Sie PowerPoint.

## <a name="clean-up-the-project"></a>Bereinigen des Projekts
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, entfernen Sie die VSTO-Add-In-Assembly, die Registrierungseinträge und die Sicherheitseinstellungen vom Entwicklungscomputer. Andernfalls wird das VSTO-Add-In jedes Mal ausgeführt, wenn Sie PowerPoint auf dem Entwicklungscomputer öffnen.

### <a name="to-clean-up-your-project"></a>So bereinigen Sie das Projekt

1. Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie nun ein einfaches VSTO-Add-In für PowerPoint erstellt haben, können Sie in den folgenden Themen mehr über die Entwicklung von VSTO-Add-Ins erfahren:

- Allgemeine Programmieraufgaben, die Sie in VSTO-Add-Ins für PowerPoint ausführen können. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

- Verwenden des Objektmodells von PowerPoint. Weitere Informationen finden Sie unter [PowerPoint-Lösungen](../vsto/powerpoint-solutions.md).

- Anpassen der Benutzeroberfläche (UI) von PowerPoint beispielsweise durch das Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder durch das Erstellen eines eigenen benutzerdefinierten Aufgabenbereichs. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

- Erstellen und Debuggen von VSTO-Add-Ins für PowerPoint. Weitere Informationen finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

- Bereitstellen von VSTO-Add-Ins für PowerPoint. Weitere Informationen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [PowerPoint-Lösungen](../vsto/powerpoint-solutions.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
