---
title: 'Excel: Einstieg in das Programmieren von Anpassungen auf Dokument Ebene'
description: Erfahren Sie, was Sie wissen müssen, um mit der Erstellung von Anpassungen auf Dokument Ebene für Microsoft Office Excel mithilfe von Visual Studio zu beginnen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fb048fd015126e5438a007be1950cddffbac9e1
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846037"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Einstieg in das Programmieren von Anpassungen auf Dokument Ebene für Excel
  Wenn Sie gerade erst mit dem Erstellen von Anpassungen auf Dokument Ebene für Microsoft Office Excel mithilfe von Visual Studio beginnen, müssen Sie Folgendes wissen.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Informationen zur Funktionsweise von Anpassungen auf Dokument Ebene für Excel
 Eine Anpassung auf Dokument Ebene für Excel basiert auf einer einzelnen Arbeitsmappe. Damit die Anpassung verwendet werden kann, öffnet der Endbenutzer die Arbeitsmappe oder erstellt die Arbeitsmappe aus einer Excel-Vorlage. Ereignisse in der Arbeitsmappe, z. b. die Eingabe in Zellen oder das Klicken auf Schaltflächen und Menü Elemente, können Ereignis Behandlungsmethoden in der Assembly aufzurufen. Wenn die Arbeitsmappe geschlossen wird, sind die Funktionen, die von der Anpassung bereitgestellt werden, nicht mehr in Excel verfügbar, sondern nur in dem Dokument, in dem Sie enthalten sind.

 Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Erstellen von Projekten auf Dokument Ebene für Excel
 Um eine Anpassung auf Dokument Ebene für Excel zu erstellen, verwenden Sie die Excel-Arbeitsmappe oder Excel-Vorlagen-Projektvorlage im Dialogfeld **Neues Projekt** . Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien.

 Weitere Informationen zum Erstellen eines Projekts auf Dokument Ebene für Excel finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Program mieren von Excel-Arbeitsmappen mithilfe von Host Elementen und Host Steuerelementen
 *Host Elemente* und *Host Steuerelemente* sind Klassen, die das Programmiermodell für Anpassungen auf Dokument Ebene bereitstellen, die mit Visual Studio erstellt wurden.

 Host Elemente stellen einen Einstiegspunkt für Ihren Code bereit, und Sie können auch als Container für Host Steuerelemente und Windows Forms Steuerelemente fungieren. In Projekten auf Dokument Ebene für Excel werden diese Host Elemente durch die `ThisWorkbook` `Sheet1` Klassen,, `Sheet2` und dargestellt `Sheet3` .

 Host Steuerelemente basieren auf systemeigenen Excel-Objekten, z. b. Listen Objekten und Bereichen. Host Steuerelemente bieten ähnliche Funktionen wie die systemeigenen Excel-Objekte, Sie verfügen jedoch auch über neue Ereignisse, Designer Unterstützung und Daten Bindungs Funktion. Sie werden als First-Class-Objekte in Ihrem Projekt Code und in IntelliSense angezeigt, wodurch es einfacher ist, auf bestimmte Objekte direkt in Ihrem Code zu verweisen, ohne im Excel-Objektmodell navigieren zu müssen.

 Weitere Informationen finden Sie unter den folgenden Themen:

- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)

- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)

- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Anpassen der Benutzeroberfläche von Excel
 Die meisten Microsoft Office Lösungen ändern die Benutzeroberfläche (User Interface, UI) der Office-Anwendung, um Benutzern die Interaktion mit der Lösung zu ermöglichen. Es gibt viele Möglichkeiten, wie Sie die Benutzeroberfläche von Excel ändern können, indem Sie eine Anpassung auf Dokument Ebene verwenden. Beispielsweise können Sie dem Menüband Steuerelemente hinzufügen, oder Sie können einen Aktionsbereich anzeigen. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

 Sie können auch die Arbeitsmappe öffnen, die dem Projekt direkt in Visual Studio zugeordnet ist. Wenn die Arbeitsmappe in Visual Studio geöffnet ist, können Sie die Arbeitsmappe mithilfe der Excel-Benutzeroberfläche ändern. Sie können die Arbeitsmappe auch als Entwurfs Oberfläche verwenden, mit der Sie Steuerelemente auf Arbeitsblätter ziehen können. Weitere Informationen finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Verwenden der Datenbindung
 Die Host Steuerelemente sind auch in der Liste der Steuerelemente enthalten, die Sie aus dem **Datenquellen** Fenster ziehen können. Durch das Hinzufügen von Host Steuerelementen auf diese Weise werden diese automatisch an die Datenquelle gebunden, die Sie mithilfe des Fensters eingerichtet haben. Sie können Daten aus Datenbanken, Webdiensten und Geschäftsobjekten anzeigen, ohne Code schreiben zu müssen. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office](../vsto/binding-data-to-controls-in-office-solutions.md)-Projektmappen.

## <a name="next-steps"></a>Nächste Schritte
 Informationen zum Erstellen einer Anpassung auf Dokument Ebene für Excel finden Sie unter Exemplarische Vorgehensweise [: Erstellen der ersten Anpassung auf Dokument Ebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Diese exemplarische Vorgehensweise enthält eine Einführung in die Office-Entwicklungs Tools in Visual Studio und das Programmiermodell für Anpassungen auf Dokument Ebene in Excel.

 Eine Liste der Themen, die Sie durch einige der allgemeinen Aufgaben in Excel-Projekten führen, finden Sie unter [Allgemeine Aufgaben bei der Office-Programmierung](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
- [Excel-Lösungen](../vsto/excel-solutions.md)
- [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Exemplarische Vorgehensweisen mit Excel](../vsto/walkthroughs-using-excel.md)
- [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
