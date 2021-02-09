---
title: Outlook-Projektmappen
description: Erfahren Sie, wie Sie mit VSTO-Add-ins Outlook automatisieren, Outlook-Features erweitern oder die Outlook-Benutzeroberfläche anpassen können.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 86fa849641894576f141ce9bc76eccaf72424d47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882439"
---
# <a name="outlook-solutions"></a>Outlook-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office Outlook verwenden können. Mit VSTO-Add-Ins können Sie Outlook automatisieren, Outlook-Features erweitern oder die Benutzeroberfläche (User Interface, UI) von Outlook anpassen. Weitere Informationen zu VSTO-Add-Ins finden Sie unter [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>Erstellen eines Outlook VSTO-Add-in-Projekts
 Erstellen Sie Outlook-Projekte mithilfe der Projektvorlage **Outlook-Add-In** im Dialogfeld **Neues Projekt** . Diese Vorlage enthält die erforderlichen Assemblyverweise und Projektdateien.

 Weitere Informationen zum Erstellen eines VSTO-Add-in-Projekts finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).

## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO-Add-in-Programmiermodell
 Wenn Sie ein VSTO-Add-In-Projekt für Outlook erstellen, generiert Visual Studio eine Klasse mit dem Namen `ThisAddIn`, die die Grundlage für die Projektmappe darstellt. Diese Klasse bietet einen Ausgangspunkt für das Schreiben des Codes, und sie macht auch das Outlook-Objektmodell für das VSTO-Add-In verfügbar.

 Weitere Informationen zur `ThisAddIn` -Klasse und anderen Funktionen, die Sie in einem VSTO-Add-in verwenden können, finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatisieren von Outlook mithilfe des Outlook-Objektmodells
 Das Outlook-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Outlook verwenden können. Diese Typen ermöglichen Ihnen das Schreiben von Code zum Ausführen häufiger Aufgaben:

- Programmgesteuertes Erstellen und Senden von E-Mails

- Senden neuer Besprechungsanfragen

- Suchen nach Elementen in Outlook-Ordnern

  Weitere Informationen finden Sie unter [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Anpassen der Benutzeroberfläche einer Outlook-Anwendung

|Aufgabe|Weitere Informationen finden Sie unter|
|----------|--------------------------|
|Fügen Sie dem Menüband eines Outlook-Inspektors benutzerdefinierte Registerkarten hinzu.|[Übersicht über Menüband](../vsto/ribbon-overview.md)|
|Hinzufügen benutzerdefinierter Gruppen zu einer integrierten Registerkarte in einem Outlook-Inspektor|[Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|
|Hinzufügen eines benutzerdefinierten Aufgabenbereichs, der in einem Outlook-Inspektor angezeigt wird|[Benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.|
|Hinzufügen eines Formularbereichs, der erweitert wird oder vorhandene Outlook-Formulare ersetzt.|[Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)|

 Weitere Informationen zum Anpassen der Benutzeroberfläche von Outlook und anderen Microsoft Office Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)|Bietet einen Überblick über die Objekte, die vom Outlook-Objektmodell bereitgestellt werden.|
|[Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)|Erläutert die von Visual Studio bereitgestellten Tools, die Ihnen das Entwerfen, Entwickeln und Debuggen von Formularbereichen erleichtern.|
|[Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-In für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Erläutert das Erstellen eines VSTO-Add-Ins für Microsoft Office Outlook.|
|[Outlook 2010 in der Office-Entwicklung](/previous-versions/office/developer/office-2010/ff458122(v=office.14))|Der Bereich der MSDN Library, in dem Sie Artikel und Referenzdokumentation zum Entwickeln von Outlook-Projektmappen finden (nicht spezifisch für die Office-Entwicklung mit Visual Studio).|
