---
title: Übersicht über Office-Projektvorlagen
description: Erfahren Sie, wie die Microsoft Office Entwicklertools in Visual Studio Projektvorlagen zum Erstellen verschiedener Typen von Office-Projektmappen enthalten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af01bf165c823ce34957e4a9eba38ef90c5344a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892033"
---
# <a name="office-project-templates-overview"></a>Übersicht über Office-Projektvorlagen
  Die Entwicklertools für Microsoft Office in Visual Studio enthalten Projektvorlagen für das Erstellen folgender Typen von Office-Lösungen:

- [Anpassungen auf Dokumentebene](#DocLevel)

- [VSTO-Add-Ins](#AppLevel)

  Einen ausführlichen Vergleich dieser Arten von Office-Projektmappen finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO-&#41;](../vsto/office-solutions-development-overview-vsto.md).

  Die Office-Projektvorlagen sind im Dialogfeld **Neues Projekt** unter dem Knoten **Office** im **Visual C#** -Sprachknoten und im **Visual Basic** -Sprachknoten verfügbar. Jede Vorlage generiert ein Projekt mit der entsprechenden Konfiguration für die Zielanwendung, einschließlich der Assemblyverweise und Debugeinstellungen.

  Jedes Projekt enthält Dateien und Code, die bzw. der Ihnen als Ausgangspunkt für eine bestimmte Art von Projektmappe dienen. Der generierte Code für jedes Projekt schließt Ereignishandler zum Starten und Herunterfahren ein. Sie können diesen Ereignishandlern Code hinzufügen, um die Projektmappe zu initialisieren, wenn sie geladen wird, und um die Projektmappe zu bereinigen, wenn sie entladen wird. Weitere Informationen finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md) und [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

> [!NOTE]
> Die Office-Entwicklertools sind in bestimmten Editionen von Visual Studio enthalten. Weitere Informationen finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)-Projektmappen.

## <a name="document-level-customizations"></a><a name="DocLevel"></a> Anpassungen auf Dokument Ebene
 Der **Office** -Knoten im Dialogfeld **Neues Projekt** stellt die folgenden Projektvorlagen bereit, um Ihnen den Einstieg für Anpassungen auf Dokumentebene für Word und Excel zu erleichtern:

- **Word 2013- und 2016-VSTO-Dokument**

- **Word 2013- und 2016-VSTO-Vorlage**

- **Excel 2013- und 2016-VSTO-Arbeitsmappe**

- **Excel 2013- und 2016-VSTO-Vorlage**

- **Word 2010-VSTO-Dokument**

- **Word 2010-VSTO-Vorlage**

- **Excel 2010-VSTO-Arbeitsmappe**

- **Excel 2010-VSTO-Vorlage**

  Die Projektvorlagen für Word-Dokumente und Excel-Arbeitsmappen enthalten Code, der Ihnen das Erstellen einer Projektmappe erleichtern soll, die auf einem bestimmten Dokument oder einer bestimmten Arbeitsmappe basiert. In diesen Typen von Projektmappen wird der Code nur ausgeführt, wenn das zugehörige Dokument in Word oder Excel geöffnet ist.

  Die Word-Vorlagen- und Excel-Vorlagen-Projektvorlagen verhalten sich ebenso wie die Projektvorlagen für Word-Dokumente und Excel-Arbeitsmappen. Die Word-Vorlagen- und Excel-Vorlagen-Projektvorlagen erleichtern Benutzern jedoch die Erstellung neuer lokaler Dokumente oder Arbeitsmappenkopien der benutzerdefinierten Vorlage in der Projektmappe. Die Funktionen in der Projektmappe sind in dem neuen Dokument verfügbar, das der Benutzer aus der Vorlage erstellt.

> [!NOTE]
> Word-Vorlagen, die auf Erweiterungen durch verwalteten Code verweisen, können nicht als globale VSTO-Add-Ins verwendet werden. Die Assembly wird nicht aufgerufen, wenn die Vorlage aus dem Start Verzeichnis von Word geladen wird. Weitere Informationen finden Sie unter [Einschränkungen von globalen Vorlagen und Excel-Add-Ins (XLA-Dateien)](#Limitations).

 Weitere Informationen für die ersten Schritte mit diesen Projekttypen finden Sie in den folgenden Themen:

- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)

- [Word-Lösungen](../vsto/word-solutions.md)

- [Excel-Lösungen](../vsto/excel-solutions.md)

- [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

- [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)

## <a name="vsto-add-ins"></a><a name="AppLevel"></a> VSTO-Add-ins
 Der **Office/SharePoint** -Knoten im Dialogfeld **Neues Projekt** stellt die folgenden Projektvorlagen bereit, um Ihnen den Einstieg in das Erstellen von VSTO-Add-Ins zu erleichtern:

- **Excel 2013- und 2016-VSTO-Add-In**

- **InfoPath 2013-VSTO-Add-In**

- **Outlook 2013- und 2016-VSTO-Add-In**

- **PowerPoint 2013- und 2016-Add-In**

- **Project 2013- und 2016-Add-In**

- **Visio 2013- und 2016-Add-In**

- **Word 2013- und 2016-Add-In**

- **Excel 2010-Add-In**

- **InfoPath 2010-Add-In**

- **Outlook 2010-Add-In**

- **PowerPoint 2010-Add-In**

- **Project 2010-Add-In**

- **Visio 2010-Add-In**

- **Word 2010-Add-In**

  Wenn Sie ein Projekt erstellen, das auf einer dieser Projektvorlagen basiert, wird der Code in der Projektmappe ausgeführt, wenn die zugehörige Anwendung geöffnet ist. Im Gegensatz zu Projekten auf Dokumentebene ist der Code keinem einzelnen Dokument zugeordnet.

  Weitere Informationen für die ersten Schritte mit diesen Projekttypen finden Sie in den folgenden Themen:

- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)

- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

## <a name="document-vs-template-solutions"></a>Dokument-und Vorlagen Lösungen
 Wenn Sie eine Projektmappe für ein Word-Dokument oder eine Excel-Arbeitsmappe entwerfen, müssen Sie sich entscheiden, wie Sie dieses Dokument am besten für Benutzer zur Verfügung stellen.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Möglicherweise möchten Sie jedem Benutzer eine Kopie eines Dokuments zur Verfügung stellen. Erstellen Sie in diesem Fall die Projektmappe mit einem Excel- oder Word-Dokument-Projekt.

 In anderen Fällen möchten Sie eventuell eine Vorlage auf einem Server bereitstellen, damit jeder Benutzer die Vorlage öffnen und eine lokale Kopie als Dokument speichern kann. Erstellen Sie in diesem Fall die Projektmappe mit einem Excel- oder Word-Vorlagen-Projekt.

## <a name="comparison"></a>Vergleich
 In der folgenden Tabelle werden die Unterschiede zwischen Dokumenten und Vorlagen erläutert.

|Dokumente|Vorlagen|
|---------------|---------------|
|Benutzer können ein Dokument öffnen und ändern, sofern es nicht schreibgeschützt ist. Alle gespeicherten Änderungen werden im Original beibehalten.|Benutzer können eine Vorlage öffnen, um eine lokale Kopie als neues Dokument zu erstellen. Das Original kann nur mit besonderen Berechtigungen geändert werden.|
|Beim Öffnen löst das Dokument das <xref:Microsoft.Office.Tools.Word.Document.Open> -Ereignis aus.|Beim Öffnen löst die Vorlage das <xref:Microsoft.Office.Tools.Word.Document.New> -Ereignis aus.|

## <a name="limitations-of-global-templates-and-excel-add-ins-xla-files"></a><a name="Limitations"></a> Einschränkungen von globalen Vorlagen und Excel-Add-Ins (XLA-Dateien)
 Dokumente, Arbeitsmappen und Vorlagen funktionieren als globale Vorlagen oder Excel-VSTO-Add-Ins (XLA-Dateien) möglicherweise nicht ordnungsgemäß.

## <a name="word-templates"></a>Word-Vorlagen
 Weist eine Microsoft Office Word-Vorlage Erweiterungen durch verwalteten Code auf, wird die Projektassembly nicht aufgerufen, wenn die Vorlage als globale Vorlage angefügt oder aus dem Startverzeichnis von Word geladen wird. Außerdem erkennt das Dokument das Format einer Vorlage nicht, die zu einer Office-Projektmappe gehört.

## <a name="excel-add-ins-xla-files"></a>Excel-Add-Ins (XLA-Dateien)
 Es ist kein Office-Projekt zum Erstellen eines Excel-VSTO-Add-Ins (*XLA* -Datei) vorhanden. Es ist möglich, eine Arbeitsmappe als XLA-Datei zu speichern, doch dieser Vorgang wird nicht unterstützt. Daher wird davon abgeraten. Wenn Sie eine Arbeitsmappe mit Erweiterungen durch verwalteten Code als **Microsoft Office Excel-Add-In Datei ( \* . xla)** speichern, können Sie Sie im Dialogfeld **Add-ins** auswählen, das auf eine andere Arbeitsmappe angewendet werden soll. In einigen Fällen wird der Code nach Anwendung des VSTO-Add-Ins in der Ziel Arbeitsmappe ausgeführt, aber eine solche Verwendung der Office-Projekt Mappe wird nicht unterstützt.

## <a name="see-also"></a>Weitere Informationen
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Entwickeln von Office-Lösungen](../vsto/developing-office-solutions.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Einstieg in das Programmieren von Anpassungen auf Dokument Ebene für Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Einstieg in das Programmieren von Anpassungen auf Dokument Ebene für Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
