---
title: PowerPoint-Lösungen
description: Erfahren Sie, dass Visual Studio Projektvorlagen bereitstellt, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft PowerPoint verwenden können.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4e297b0d269d5ff0bff0deeadd6bd346de00a324
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528037"
---
# <a name="powerpoint-solutions"></a>PowerPoint-Lösungen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office PowerPoint verwenden können. Mit VSTO-Add-Ins können Sie PowerPoint automatisieren, PowerPoint-Features erweitern oder die PowerPoint-Benutzeroberfläche anpassen.

 Weitere Informationen zu VSTO-Add-Ins finden Sie unter "Einstieg in die [Programmierung von VSTO-Add-ins](getting-started-programming-vsto-add-ins.md) und [Architektur von VSTO](architecture-of-vsto-add-ins.md)-Add-Ins". Wenn Sie noch nicht mit der Programmierung mit Microsoft Office vertraut sind, finden Sie weitere Informationen unter [Einstieg in &#40;Office-Entwicklung in Visual Studio&#41;](getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatisieren von PowerPoint mithilfe des PowerPoint-Objektmodells
 Das PowerPoint-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von PowerPoint verwenden können. Diese Typen ermöglichen Ihnen das Schreiben von Code zum Ausführen häufiger Aufgaben:

- Programmgesteuertes Erstellen und Formatieren von Präsentationen

- Hinzufügen oder Entfernen von Folien in Präsentationen

- Hinzufügen oder Ändern von Formen in einer Folie

  Wenn Sie über ein VSTO-Add-in auf das PowerPoint-Objektmodell zugreifen möchten, verwenden Sie das- `Application` Feld der- `ThisAddIn` Klasse im Projekt. Das- `Application` Feld gibt ein- [Anwendungs](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) Objekt zurück, das die aktuelle Instanz von PowerPoint darstellt. Weitere Informationen finden Sie unter [Program VSTO Add-ins](programming-vsto-add-ins.md).

  Bei einem Aufruf des PowerPoint-Objektmodells verwenden Sie Typen, die in der primären Interopassembly für PowerPoint bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in PowerPoint. Alle Typen in der primären Interopassembly für PowerPoint werden im Namespace [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) definiert. Weitere Informationen zu primären Interop-Assemblys finden Sie unter Übersicht über die Entwicklung von Office-Projektmappen [&#40;VSTO&#41;](office-solutions-development-overview-vsto.md) und [primäre](office-primary-interop-assemblies.md)Interopassemblys

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a> Verwenden der Dokumentation zum PowerPoint-Objektmodell
 Ausführliche Informationen zum PowerPoint-Objektmodell finden Sie in der Referenz für die primäre Interopassembly (PIA) für PowerPoint und der VBA-Objektmodellreferenz.

### <a name="primary-interop-assembly-reference"></a>Referenz zur primären Interopassembly
 In der Referenzdokumentation für die PowerPoint-PIA werden die Typen in der primären Interopassembly für PowerPoint beschrieben. Diese Dokumentation ist unter folgendem Speicherort verfügbar: [PowerPoint 2010 primärer interopassemblyverweis](office-primary-interop-assemblies.md).

 Weitere Informationen zum Entwurf der PowerPoint-Pia, z. b. zu den Unterschieden zwischen Klassen und Schnittstellen in der Pia und zur Implementierung von Ereignissen in der Pia, finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären Interop](/previous-versions/office/developer/office-2010/ff759900(v=office.14))-Assemblys von Office.

### <a name="vba-object-model-reference"></a>VBA-Objektmodell Referenz
 Die VBA-Objektmodellreferenz dokumentiert das PowerPoint-Objektmodell, das für VBA (Visual Basic for Applications)-Code verfügbar gemacht wird. Weitere Informationen finden Sie unter [PowerPoint 2010-Objektmodell Referenz](/office/vba/api/overview/PowerPoint/object-model).

 Alle Objekte und Member in der VBA-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly (PIA) für PowerPoint. Das Präsentationsobjekt in der VBA-Objektmodell Referenz entspricht z. b. dem [Präsentationstyp](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) in der PowerPoint-Pia. Obwohl die VBA-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA-Code in dieser Referenz in Visual Basic oder Visual C# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten VSTO-Add-In-Projekt für PowerPoint verwenden möchten.

## <a name="customize-the-user-interface-of-powerpoint"></a>Anpassen der Benutzeroberfläche von PowerPoint
 Sie können die Benutzeroberfläche von PowerPoint folgendermaßen ändern:

|Aufgabe|Weitere Informationen finden Sie unter|
|----------|--------------------------|
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](custom-task-panes.md)|
|Hinzufügen von benutzerdefinierten Registerkarten zum Menüband|[Übersicht über Menüband](ribbon-overview.md)|
|Hinzufügen benutzerdefinierter Gruppen zu einer integrierten Registerkarte auf dem Menüband|[Gewusst wie: Anpassen einer integrierten Registerkarte](how-to-customize-a-built-in-tab.md)|

 Weitere Informationen zum Anpassen der Benutzeroberfläche von PowerPoint und anderen Microsoft Office Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](office-ui-customization.md).

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für PowerPoint](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Einstieg in das Programmieren von VSTO-Add-ins](getting-started-programming-vsto-add-ins.md)
- [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](architecture-of-vsto-add-ins.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](how-to-create-office-projects-in-visual-studio.md)
- [Program mieren von VSTO-Add-ins](programming-vsto-add-ins.md)
- [Schreiben von Code in Office-Lösungen](writing-code-in-office-solutions.md)
- [Primäre Interopassemblys für Office](office-primary-interop-assemblies.md)
- [Office-Benutzeroberflächen Anpassung](office-ui-customization.md)
- [PowerPoint 2010 bei der Office-Entwicklung](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
