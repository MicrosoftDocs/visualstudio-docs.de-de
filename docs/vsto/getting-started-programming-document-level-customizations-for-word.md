---
title: Einstieg in das Programmieren von Anpassungen auf Dokument Ebene für Word
description: Erfahren Sie, was Sie wissen müssen, um mit der Erstellung von Anpassungen auf Dokument Ebene für Microsoft Office Word mithilfe von Visual Studio zu beginnen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9420ab02b5f402dd39e5ca1713b911a10932dfb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845179"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Einstieg in das Programmieren von Anpassungen auf Dokument Ebene für Word
  Wenn Sie gerade erst mit dem Erstellen von Anpassungen auf Dokument Ebene für Microsoft Office Word mithilfe von Visual Studio beginnen, müssen Sie Folgendes wissen.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Verstehen, wie Anpassungen auf Dokument Ebene für Word funktionieren
 Jede von Ihnen erstellte Wort Anpassung basiert auf einem einzelnen Dokument. Damit die Anpassung verwendet werden kann, öffnet der Endbenutzer das Dokument oder erstellt das Dokument aus einer Word-Vorlage. Ereignisse im Dokument, z. b. das Verschieben des Cursors in bestimmte Bereiche oder das Klicken auf Schaltflächen und Menü Elemente, können Ereignis Behandlungsmethoden in der Assembly aufzurufen. Wenn das Dokument geschlossen wird, sind die Funktionen, die von der Anpassung bereitgestellt werden, nicht mehr in Word verfügbar.

 Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Erstellen von Projekten auf Dokument Ebene für Word
 Um eine Anpassung auf Dokument Ebene für Word zu erstellen, verwenden Sie die Word-Dokument-oder Word-Vorlagen-Projektvorlage im Dialogfeld **Neues Projekt** . Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien.

 Weitere Informationen zum Erstellen eines Projekts auf Dokument Ebene für Word finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Program mieren von Word-Dokumenten mithilfe von Host Steuerelementen für Host Elemente
 *Host Elemente* und *Host Steuerelemente* sind Klassen, die das Programmiermodell für Anpassungen auf Dokument Ebene bereitstellen.

 Host Elemente stellen einen Einstiegspunkt für Ihren Code bereit, und Sie können auch als Container für Host Steuerelemente und Windows Forms Steuerelemente fungieren. In Projekten auf Dokument Ebene für Word wird das-Host Element durch die- `ThisDocument` Klasse dargestellt.

 Host Steuerelemente basieren auf nativen Word-Objekten, z. b. Inhalts Steuerelementen, Lesezeichen und XML-Knoten. Host Steuerelemente bieten ähnliche Funktionen wie die systemeigenen Word-Objekte, haben aber auch neue Ereignisse, Designer Unterstützung und Daten Bindungs Funktion. Sie werden als First-Class-Objekte im Projekt Code und in IntelliSense angezeigt, wodurch es einfacher ist, auf bestimmte Objekte direkt in Ihrem Code zu verweisen, ohne im Word-Objektmodell navigieren zu müssen.

 Weitere Informationen finden Sie unter den folgenden Themen:

- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)

- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)

- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Benutzeroberfläche von Word anpassen
 Die meisten Microsoft Office Lösungen ändern die Benutzeroberfläche (User Interface, UI) der Office-Anwendung, um Benutzern die Interaktion mit der Lösung zu ermöglichen. Es gibt viele Möglichkeiten, wie Sie die Benutzeroberfläche von Word ändern können, indem Sie eine Anpassung auf Dokument Ebene verwenden. Beispielsweise können Sie dem Menüband Steuerelemente hinzufügen, und Sie können einen Aktionsbereich anzeigen. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

 Sie können das Dokument, das dem Projekt zugeordnet ist, auch direkt in Visual Studio öffnen. Wenn das Dokument in Visual Studio geöffnet ist, können Sie das Dokument mithilfe der Word-Benutzeroberfläche ändern. Sie können das Dokument auch als Entwurfs Oberfläche verwenden, die es Ihnen ermöglicht, Steuerelemente auf das Dokument zu ziehen. Weitere Informationen finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Binden von Steuerelementen an Daten
 Die Inhalts Steuerelemente und das- <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement sind in der Liste der Steuerelemente enthalten, die Sie aus dem **Datenquellen** Fenster ziehen können. Durch das Hinzufügen von Inhalts Steuerelementen und Lesezeichen auf diese Weise werden diese automatisch an die Datenquelle gebunden, die Sie mithilfe des-Fensters eingerichtet haben. Sie können Daten aus Datenbanken, Diensten und Geschäftsobjekten anzeigen, ohne Code schreiben zu müssen. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office](../vsto/binding-data-to-controls-in-office-solutions.md)-Projektmappen.

## <a name="next-steps"></a>Nächste Schritte
 Informationen zum Erstellen einer Anpassung auf Dokument Ebene für Word finden Sie unter Exemplarische Vorgehensweise [: Erstellen der ersten Anpassung auf Dokument Ebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). In dieser exemplarischen Vorgehensweise werden die Office-Entwicklungs Tools in Visual Studio und das Programmiermodell für Word-Anpassungen auf Dokument Ebene vorgestellt.

 Eine Liste der Themen, die Sie durch einige der allgemeinen Aufgaben in Word-Projekten führen, finden Sie unter [Allgemeine Aufgaben bei der Office-Programmierung](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
- [Word-Lösungen](../vsto/word-solutions.md)
- [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Exemplarische Vorgehensweisen mit Word](../vsto/walkthroughs-using-word.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
