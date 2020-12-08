---
title: Einstieg in das Programmieren von VSTO-Add-ins
description: Erfahren Sie, wie Sie mit VSTO-Add-Ins Microsoft Office Anwendungen automatisieren, Features der Anwendung erweitern und die Benutzeroberfläche der Anwendung anpassen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be4e129de68d2a7f7690ba24acc92fb09400cfb2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845114"
---
# <a name="get-started-programming-vsto-add-ins"></a>Einstieg in das Programmieren von VSTO-Add-ins
  Sie können mit VSTO-Add-Ins Microsoft Office-Anwendungen automatisieren, Funktionen der Anwendung erweitern und die Benutzeroberfläche der Anwendung anpassen. Informationen dazu, wie VSTO-Add-Ins mit anderen Typen von Office-Projektmappen verglichen werden, die Sie mithilfe von Visual Studio erstellen können, finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40;v&#41;Sto ](../vsto/office-solutions-development-overview-vsto.md)

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Erstellen von VSTO-Add-in-Projekten
 Erstellen Sie VSTO-Add-in-Projekte mit einer der VSTO-Add-in-Projektvorlagen im Dialogfeld **Neues Projekt** . Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien. Visual Studio stellt VSTO-Add-In-Projektvorlagen für die meisten Anwendungen in Office zur Verfügung.

 Weitere Informationen zum Erstellen eines VSTO-Add-in-Projekts finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).

## <a name="develop-vsto-add-in-projects"></a>Entwickeln von VSTO-Add-in-Projekten
 Wenn Sie ein VSTO-Add-in-Projekt erstellen, erstellt Visual Studio automatisch eine *ThisAddIn. vb* - [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Codedatei (in) oder eine *ThisAddIn.cs* -Codedatei (in c#). Diese Datei enthält die- `ThisAddIn` Klasse, die die Grundlage für das VSTO-Add-in bereitstellt. Sie können Member dieser Klasse verwenden, um Code auszuführen, wenn das VSTO-Add-In geladen oder entladen wird, um auf das Objektmodell der Hostanwendung zuzugreifen und um Funktionen der Anwendung zu erweitern. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatisieren von Anwendungen mithilfe der Objekt Modelle
 Die Objektmodelle von Microsoft Office-Anwendungen machen zahlreiche Typen verfügbar, mit denen Sie in einem VSTO-Add-In programmieren können. Sie können diese Typen verwenden, um die Anwendung zu automatisieren. So haben Sie die Möglichkeit, in Outlook programmgesteuert eine E-Mail zu erstellen und zu senden oder in Word ein Dokument zu öffnen und Inhalt hinzuzufügen. Weitere Informationen zum Zugreifen auf das Objektmodell der Host Anwendung im Code finden [Sie unter Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Weitere Informationen zu den Objektmodellen von bestimmten Microsoft Office-Anwendungen finden Sie unter den folgenden Themen:

- [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)

- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)

- [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)

- [InfoPath-Lösungen](../vsto/infopath-solutions.md)

- [PowerPoint-Lösungen](../vsto/powerpoint-solutions.md)

- [Projektmappen](../vsto/project-solutions.md)

- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Anpassen der Benutzeroberfläche von Anwendungen
 Es gibt verschiedene Möglichkeiten zum Anpassen der Benutzeroberfläche der Host Anwendung mithilfe eines VSTO-Add-Ins:

- Für Excel und Word können Sie Dokumenten verwaltete Steuerelemente hinzufügen. Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

- Sie können das Menüband anpassen, wenn die Anwendung dies unterstützt. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

- Sie können einen benutzerdefinierten Aufgabenbereich erstellen, wenn die Anwendung dies unterstützt. Weitere Informationen finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

- Für Outlook können Sie einen benutzerdefinierten Formularbereich erstellen. Weitere Informationen finden Sie unter [Erstellen von Outlook-Formular](../vsto/creating-outlook-form-regions.md)Bereichen.

- Für alle Microsoft Office-Anwendungen können Sie Windows Forms im VSTO-Add-In anzeigen.

  Weitere Informationen zum Anpassen der Benutzeroberfläche von Microsoft Office Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Nächste Schritte
 Wie Sie VSTO-Add-Ins erstellen können, wird in den folgenden exemplarischen Vorgehensweisen näher beschrieben:

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-In für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  In diesen exemplarischen Vorgehensweisen machen Sie sich mit den Office-Entwicklungstools in Visual Studio und dem Programmiermodell für VSTO-Add-Ins vertraut.

  Eine Liste der Themen, die Sie durch einige der allgemeinen Aufgaben in Office-Projekten führen, finden Sie unter [Allgemeine Aufgaben bei der Office-Programmierung](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Beginnen Sie &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
