---
title: Verfügbare Funktionen nach Office-Anwendung und Projekttyp
description: Erfahren Sie, wie Visual Studio verschiedene Typen von Projektvorlagen bietet, die verschiedene Geschäftsszenarien für Microsoft Office Anwendungen unterstützen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24db499602642f6ec980628d290ec8b5dd07fed3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847805"
---
# <a name="features-available-by-office-application-and-project-type"></a>Verfügbare Funktionen nach Office-Anwendung und Projekttyp
  Visual Studio verfügt über mehrere Arten von Projektvorlagen, die unterschiedliche Geschäftsszenarien für Microsoft Office-Anwendungen unterstützen, z. B.:

- Anpassungen auf Dokumentebene

- VSTO-Add-Ins

  Nicht alle Anwendungen können jeden Projekttyp verwenden. Beispielsweise sind Projekte auf Dokumentebene nur für Microsoft Office Word und Microsoft Office Excel verfügbar. Ebenso sind einige Funktionen nur für bestimmte Projekt- oder Anwendungstypen verfügbar. Der Aktionsbereich ist beispielsweise nur in Projekten auf Dokumentebene verfügbar, und Menübanderweiterungen stehen nur für einige Anwendungen zur Verfügung. Weitere Informationen zu den verschiedenen Projekttypen finden Sie unter Übersicht über die Entwicklung von Office-Projektmappen [&#40;VSTO-&#41;](../vsto/office-solutions-development-overview-vsto.md).

> [!NOTE]
> Office-Projektvorlagen sind nur in einigen Editionen von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügbar. Weitere Informationen finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)-Projektmappen.

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Projekttypen, die für verschiedene Microsoft Office Anwendungen verfügbar sind
 In der folgenden Tabelle sind die Anwendungen aufgeführt, die Sie für die einzelnen Projekttypen verwenden können.

|Projekttypen|Microsoft Office-Anwendung|
|-------------------|----------------------------------|
|Anpassungen auf Dokumentebene|Excel<br /><br /> Word|
|VSTO-Add-Ins|Excel<br /><br /> InfoPath (nur InfoPath 2013 und InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>In unterschiedlichen Projekttypen verfügbare Funktionen
 In der folgenden Tabelle ist aufgeführt, für welche Projekttypen die jeweilige Funktion bereitgestellt wird.

|Funktion|Projekttypen, die die Funktion bereitstellen|Weitere nützliche Informationen|
|-------------|--------------------------------------------|---------------------|
|Aktionsbereich|Projekte auf Dokumentebene|[Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)|
|ClickOnce-Bereitstellung.|VS-Projekte und Projekte auf Dokumentebene|[Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)|
|Benutzerdefinierte Aufgabenbereiche|VSTO-Add-In-Projekte für die folgenden Anwendungen:<br /><br /> -Excel<br />-InfoPath (nur InfoPath 2013 und InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Word|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|
|Benutzerdefinierte XML-Teile|Projekte auf Dokumentebene<br /><br /> Projekte auf Anwendungsebene für die folgenden Anwendungen:<br /><br /> -Excel<br />-PowerPoint<br />-Word|[Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md)|
|Datencache|Projekte auf Dokumentebene|[Zwischengespeicherte Daten in Anpassungen auf Dokument Ebene](../vsto/cached-data-in-document-level-customizations.md)|
|Machen Sie ein Objekt in einem VSTO-Add-in für andere Microsoft Office Lösungen verfügbar.|VSTO-Add-In-Projekte|[Code in VSTO-Add-Ins aus anderen Office-Projektmappen aufzurufen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Folgende Hoststeuerelemente:<br /><br /> -Diagramm<br />-ListObject<br />-NamedRange<br />-Inhalts Steuerelemente<br />-Lesezeichen|Projekte auf Dokumentebene<br /><br /> VSTO-Add-In-Projekte für Word und Excel|[Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)|
|Folgende Hoststeuerelemente:<br /><br /> -XmlMappedRange<br />-XmlNode<br />-XMLNodes|Projekte auf Dokumentebene|[Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)|
|Bereitstellung von mehreren Projekten|Projekte auf Dokumentebene<br /><br /> VSTO-Add-In-Projekte|[Exemplarische Vorgehensweise: Bereitstellen mehrerer Office-Lösungen in einem einzelnen ClickOnce-Installer](/previous-versions/dd465290(v=vs.110))|
|Outlook-Formularbereiche|VSTO-Add-In-Projekte für Outlook|[Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)|
|Aktionen nach der Bereitstellung|Projekte auf Dokumentebene<br /><br /> VSTO-Add-In-Projekte|[Exemplarische Vorgehensweise: Kopieren eines Dokuments nach einer ClickOnce-Installation auf den Endbenutzer Computer](/previous-versions/dd465291(v=vs.110))|
|Menübandanpassungen|Projekte auf Dokumentebene<br /><br /> VSTO-Add-In-Projekte für die folgenden Anwendungen:<br /><br /> -Excel<br />-InfoPath (nur InfoPath 2013 und InfoPath 2010)<br />-Outlook<br />-PowerPoint<br />-Projekt<br />-Visio<br />-Word|[Übersicht über Menüband](../vsto/ribbon-overview.md)|
|Visueller Dokumentdesigner|Projekte auf Dokumentebene|[Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Siehe auch
- [Beginnen Sie &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Zwischengespeicherte Daten in Anpassungen auf Dokument Ebene](../vsto/cached-data-in-document-level-customizations.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)