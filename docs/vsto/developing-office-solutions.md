---
title: Entwickeln von Office-Lösungen
description: Erfahren Sie, wie Sie ein Projekt mithilfe von Office-Entwicklertools in Visual Studio entwerfen. Erfahren Sie außerdem, wie Sie mit der Implementierung des Codes und der benutzerdefinierten Benutzeroberfläche beginnen.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbfe569e587c53aede6d550bc20527ad8d0fd328
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844997"
---
# <a name="develop-office-solutions"></a>Entwickeln von Office-Lösungen
  Nachdem Sie ein Projekt mit den Office Developer Tools in Visual Studio entworfen und die Projektdateien eingerichtet haben, können Sie damit beginnen, sich auf das Implementieren des Codes und der benutzerdefinierten Benutzeroberfläche (UI) zu konzentrieren.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="office-solutions-programming-model"></a>Programmiermodell für Office-Lösungen
 Über das Office-Objektmodell werden viele verschiedene Objekte für die Programmierung verfügbar gemacht. Wenn Sie Office-Projektmappen mit verwaltetem Code programmieren, schreiben Sie Code, bei dem Typen in den primären Interopassemblys von Office verwendet werden. In Projektmappen, die Sie mit Office-Projektvorlagen in Visual Studio erstellen, können Sie Code auch direkt für generierte Klassen in Ihrem Projekt schreiben. Weitere Informationen finden Sie unter [Schreiben von Code in Office](../vsto/writing-code-in-office-solutions.md)-Projektmappen.

## <a name="program-different-types-of-office-solutions"></a>Program mieren verschiedener Typen von Office-Projektmappen
 Der Typ der Projektmappe, den Sie erstellen, bestimmt, welche Funktionen Sie in Ihrem Projekt verwenden können. Beispielsweise können Sie Anpassungen auf Dokumentebene Windows Forms-Steuerelemente und erweiterte Office-Steuerelemente (als *Hoststeuerelemente* bezeichnet) hinzufügen, indem Sie die Elemente zur Entwurfszeit aus der **Werkzeugpalette** in Visual Studio ziehen. Wenn Sie aber ein VSTO-Add-In entwickeln, können Sie diese Arten von Steuerelementen Dokumenten zur Laufzeit nur hinzufügen, indem Sie Code schreiben.

 Weitere Informationen zu Funktionen, die speziell für verschiedene Typen von Projektmappen gelten, finden Sie unter den folgenden Themen:

- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).

- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md).

- [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

  Hintergrundinformationen zum Planen von Office-Projektmappen und-Prozeduren, die Sie beim Erstellen von Projekten unterstützen, finden Sie unter [Entwerfen und Erstellen von Office](../vsto/designing-and-creating-office-solutions.md)

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)|Hier werden verschiedene Aspekte des Schreibens von Code in Office-Projektmappen beschrieben.|
|[Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)|Enthält eine Übersicht über das Programmiermodell von VSTO-Add-Ins und die zugehörigen Programmieraufgaben.|
|[Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)|Enthält eine Übersicht über das Programmiermodell von Anpassungen auf Dokumentebene und die zugehörigen Programmieraufgaben.|
|[Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)|Hier werden die verschiedenen Wege beschrieben, wie Sie die Benutzeroberfläche von Office-Anwendungen anpassen können, indem Sie VSTO-Add-Ins und Anpassungen auf Dokumentebene verwenden.|
|[Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)|Hier werden die unterschiedlichen Wege beschrieben, wie Sie in Office-Projektmappen mit Daten arbeiten können, z. B. das Binden von Daten an Steuerelemente und das Zwischenspeichern von Daten in Anpassungen auf Dokumentebene.|
|[Auswirkungen von Autosave auf Office-Projektmappen](./how-autosave-impacts-office-solutions.md)|Beschreibt Anpassungen, die Sie möglicherweise an Office-Projektmappen vornehmen müssen, wenn die automatische Speicherung aktiviert ist.|
|[Problembehandlung für Office-Lösungen](../vsto/troubleshooting-office-solutions.md)|Enthält Tipps zur Lösung von allgemeinen Problemen, die beim Erstellen von Office-Projektmappen auftreten können.|
|[Threading Unterstützung in Office](../vsto/threading-support-in-office.md)|Hier erhalten Sie einen Überblick über die Arbeit mit mehreren Threads in Office-Projektmappen.|
|[Barrierefreiheit in Office-Projekten](../vsto/accessibility-in-office-projects.md)|Beschreibt die Barrierefreiheitsfunktionen, die in Office-Projektmappen verfügbar sind.|

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Gewusst wie: Lesen von und Schreiben in Dokumenteigenschaften](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [Gewusst wie: Ausrichten der mehrsprachigen Office-Benutzeroberfläche](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
