---
title: Ausführen von Lösungen in unterschiedlichen Versionen von Microsoft Office
description: Erfahren Sie, wie Sie Versionen von Microsoft Office Lösungen ausführen können, die mit Visual Studio 2010 oder höher erstellt wurden.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d70e61e318f0f6afd0a58ed35f912b6a5f2cda8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523540"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Ausführen von Lösungen in unterschiedlichen Versionen von Microsoft Office

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Ausführen von mit Visual Studio 2010 und höher erstellten Office-Projektmappen

|Office-Zielversion der Projektvorlage|Ziel .NET Framework des Projekts<sup>1</sup>|Office-Versionen, mit denen die Projektmappe ausgeführt werden kann|Erforderliche Laufzeit auf dem Computer des Endbenutzers|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Office 2016 und [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office System<sup>2</sup>|Visual Studio 2010 Tools for Office-Laufzeit|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office System<sup>2</sup>|Visual Studio 2010 Tools for Office-Laufzeit|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office-Laufzeit|
|2007 Microsoft Office System|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher,<br /><br /> oder<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office System|Visual Studio 2010 Tools for Office-Laufzeit|

 1. Die .NET Framework Version, auf die Ihr Projekt abzielt, ist auf Endbenutzer Computern erforderlich, damit die Lösung ausgeführt werden kann. Wenn Ihr Projekt beispielsweise auf den .NET Framework 3,5 abzielt, ist die .NET Framework 3,5 auf Endbenutzer Computern erforderlich. In diesem Beispiel wird die Projekt Mappe nicht ausgeführt, wenn nur das [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] auf Endbenutzer Computern installiert ist.

 2. In diesem Szenario wird die Projektmappe nur dann fehlerfrei im 2007 Microsoft Office System ausgeführt, wenn sie keine der neuen Funktionen in [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] enthält.

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Ausführen von Office-Projektmappen, die mit Visual Studio-Versionen vor Visual Studio 2010 erstellt wurden
 Microsoft Office-Anwendungen können auch mit früheren Versionen als Visual Studio 2010 erstellte Office-Projektmappen ausführen. In einigen Fällen erfordern diese Lösungen andere Versionen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Verschiedene Versionen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] können parallel auf demselben Computer installiert werden.

 Die folgende Tabelle zeigt, welche Versionen von Microsoft Office Lösungen ausführen können, die mit früheren Versionen von Visual Studio erstellt wurden, und welche Versionen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] und .NET Framework für jede Lösung erforderlich sind.

|Zum Erstellen der Lösung verwendete Edition von Visual Studio|Office-Zielversion der Projektvorlage|Office-Versionen, mit denen die Projektmappe ausgeführt werden kann|Erforderliche Laufzeit auf dem Computer des Endbenutzers|Erforderliche .NET Framework Version auf dem Endbenutzer Computer|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> oder<br /><br /> Visual Studio Team System 2008|2007 Microsoft Office System|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<sup>1</sup><br /><br /> 2007 Microsoft Office System|Visual Studio 2010-Tools für Office-Laufzeit<sup>1</sup><br /><br /> oder<br /><br /> Visual Studio Tools for Microsoft Office System (Version 3.0, Laufzeit)|.NET Framework 3.5|
|Eine der folgenden Editionen von Visual Studio 2005 mit installiertem VSTO 2005 SE<sup>2</sup> :<br /><br /> -Visual Studio 2005-Tools für Office<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|2007 Microsoft Office System|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (nur 32 Bit<sup>3</sup>)<br /><br /> 2007 Microsoft Office System|Laufzeit für Visual Studio 2005 Tools for Office Second Runtime|.NET Framework 2.0, .NET Framework 3.0 oder .NET Framework 3.5|
|Eine der folgenden Editionen von Visual Studio:<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Visual Studio 2005 Tools für Office (mit oder ohne VSTO 2005 SE<sup>2</sup> installiert)<br />-Visual Studio Team System 2005 (mit oder ohne VSTO 2005 SE<sup>2</sup> installiert)<br />-Visual Studio 2005 Professional mit VSTO 2005 SE<sup>2</sup> installiert|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (nur 32 Bit<sup>3</sup>)<br /><br /> 2007 Microsoft Office System<br /><br /> Microsoft Office 2003|Laufzeit für Visual Studio 2005 Tools for Office Second Runtime|.NET Framework 2.0, .NET Framework 3.0 oder .NET Framework 3.5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] Anwendungen enthalten die Visual Studio 2010-Tools für Office-Laufzeit. Daher verwenden diese Anwendungen in diesem Szenario immer die Visual Studio 2010-Tools für Office-Laufzeit anstelle der Visual Studio-Tools für das Microsoft Office System (Version 3,0 Runtime). Anwendungen im 2007 Microsoft Office System können Visual Studio 2010-Tools für Office-Laufzeit oder Visual Studio-Tools für Microsoft Office System (Laufzeit, Version 3.0) verwenden.

 2. VSTO 2005 SE ist ein kostenloses Visual Studio-Add-On, das VSTO-Add-In-Projektvorlagen für Microsoft Office 2003 und das Microsoft Office 2007-System bereitstellt. Die Installation kann mit Visual Studio 2005 Professional, Visual Studio 2005 Tools for Office oder einer Edition von Visual Studio Team System 2005 erfolgen. Weitere Informationen finden Sie unter [Visual Studio 2005 Tools for Office Second Edition](https://developer.microsoft.com/office/docs).

 3. Office-Projektmappen, die die Visual Studio 2005-Tools für Office Second Edition-Laufzeit erfordern, sind nicht mit 64-Bit-Versionen von [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] kompatibel. Um diese Projektmappen in der 64-Bit-Edition von [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] oder [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] auszuführen, müssen Sie das Projekt auf [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] oder ein Visual Studio 2008-Projekt aktualisieren, für das 2007 Microsoft Office System als Zielversion festgelegt wurde.

## <a name="see-also"></a>Weitere Informationen
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Übersicht über Visual Studio-Tools für Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio-Tools für Installationsszenarien für Office-Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
