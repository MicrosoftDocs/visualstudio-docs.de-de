---
title: InfoPath-Projektmappen
description: Erfahren Sie, wie Sie Visual Studio zum Erstellen von VSTO-Add-Ins für Microsoft InfoPath 2013 und InfoPath 2010 verwenden können.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3feab4a4b66ed2d6cf96fbccc8aaf1fb7de3bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962365"
---
# <a name="infopath-solutions"></a>InfoPath-Projektmappen
  In Visual Studio werden Projektvorlagen bereitgestellt, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office InfoPath 2013 und InfoPath 2010 verwenden können. InfoPath ist in Office 2016 nicht verfügbar.

> [!NOTE]
> Sie können weiterhin ein VSTO-Add-in für InfoPath erstellen, auch wenn Sie Office 2016 installiert haben. Installieren Sie InfoPath 2013 oder Office 2013 einfach zusätzlich zu Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 VSTO-Add-Ins für InfoPath ähneln VSTO-Add-Ins für andere Microsoft Office-Anwendungen. Diese Typen von Projektmappen bestehen aus einer Assembly, die von der Anwendung geladen wird. Endbenutzer können auf die Funktionen dieser Assembly zugreifen, unabhängig davon, welches Formular bzw. welche Formularvorlage geöffnet ist. Weitere Informationen zu VSTO-Add-Ins finden Sie unter "Einstieg in die [Programmierung von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architektur von VSTO](../vsto/architecture-of-vsto-add-ins.md)-Add-Ins".

> [!NOTE]
> Visual Studio 2015 enthält nicht die InfoPath-Formularvorlagenprojekte, die in früheren Versionen von Visual Studio bereitgestellt wurden. Sie können auch Visual Studio 2015 nicht verwenden, um ein in einer früheren Version von Visual Studio erstelltes InfoPath-Formularvorlagenprojekt zu öffnen oder zu bearbeiten. Ein InfoPath-Formularvorlagenprojekt kann jedoch mit Visual Studio Tools for Applications geöffnet und bearbeitet werden. Weitere Informationen finden Sie unter [Arbeiten mit VSTO 2008-Projekten in InfoPath 2010.](/archive/blogs/infopath/working-with-vsto-2008-projects-in-infopath-2010).

## <a name="automate-infopath-by-using-an-add-in"></a>Automatisieren von InfoPath mithilfe eines Add-ins
 Verwenden Sie zum Zugreifen auf das InfoPath-Objektmodell von einem Office VSTO-Add-In aus, das mit Office-Entwicklungstools in Visual Studio erstellt wurde, das `Application` -Feld der `ThisAddIn` -Klasse im Projekt. Das `Application` -Feld gibt ein <xref:Microsoft.Office.Interop.InfoPath.Application> -Objekt zurück, das die aktuelle Instanz von InfoPath darstellt. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Wenn Sie von einem VSTO-Add-in aus das InfoPath-Objektmodell abrufen, verwenden Sie Typen, die in der primären Interopassembly für InfoPath bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in InfoPath. Alle Typen in der primären Interopassembly für InfoPath werden im <xref:Microsoft.Office.Interop.InfoPath> -Namespace definiert. Weitere Informationen zur primären Interopassembly für InfoPath finden Sie unter [Informationen zur primären Interopassembly für Microsoft Office InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly). Weitere Informationen zu primären Interop-Assemblys im Allgemeinen finden Sie unter Übersicht über die Entwicklung von Office-Projektmappen [&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) und [primäre](../vsto/office-primary-interop-assemblies.md)Interopassemblys

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Anpassen der Benutzeroberfläche von InfoPath mithilfe eines Add-ins
 Wenn Sie ein VSTO-Add-in für InfoPath erstellen, haben Sie mehrere verschiedene Optionen zur Anpassung der Benutzeroberfläche. In der folgenden Tabelle werden einige dieser Optionen aufgeführt.

|Aufgabe|Weitere Informationen finden Sie unter|
|----------|--------------------------|
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|
|Hinzufügen benutzerdefinierter Registerkarten zum Menüband in InfoPath|[Anpassen eines Menübands für InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Weitere Informationen zum Anpassen der Benutzeroberfläche von InfoPath und anderen Microsoft Office Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Weitere Informationen
- [Informationen zur primären Interopassembly Microsoft Office InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)
- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
- [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [InfoPath 2010 bei der Office-Entwicklung](/previous-versions/office/developer/office-2010/ff604966(v=office.14))