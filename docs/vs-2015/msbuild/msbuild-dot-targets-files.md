---
title: TARGETS-Dateien von MSBuild | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bab229a3246ac91eaa652be67e98a68aab40e820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841100"
---
# <a name="msbuild-targets-files"></a>.Targets-Dateien von MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sind mehrere TARGETS-Dateien verfügbar, die Elemente, Eigenschaften, Ziele und Aufgaben für allgemeine Szenarios enthalten. Diese Dateien werden in die meisten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektdateien automatisch importiert, um Lesbarkeit und Verwaltung zu vereinfachen.  
  
 Projekte importieren in der Regel mindestens eine TARGETS-Datei, um den entsprechenden Buildprozess zu definieren. Ein von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstelltes [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Projekt importiert Microsoft.CSharp.targets, die wiederum Microsoft.Common.targets importiert. Das [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Projekt definiert die jeweiligen Elemente und Eigenschaften dieses Projekts selbst. Die standardmäßigen Buildregeln für ein [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Projekt werden jedoch in den importierten TARGETS-Dateien definiert.  
  
 Der `$(MSBuildToolsPath)`-Wert gibt den Pfad dieser allgemeinen TARGETS-Dateien an. Handelt es sich um die `ToolsVersion` 4.0, befinden sich die Dateien im folgenden Speicherort: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
> Informationen zum Erstellen eigener Ziele finden Sie unter [Targets](../msbuild/msbuild-targets.md) (MSBuild-Ziele). Informationen dazu, wie Sie das- `Import` Element verwenden, um eine Projektdatei in eine andere Projektdatei einzufügen, finden Sie unter [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md) und Gewusst [wie: Verwenden desselben Ziels in mehreren Projektdateien](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Allgemeine TARGETS-Dateien  
  
|TARGETS-Datei|Beschreibung|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Definiert die Schritte im Standardbuildprozess für [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]- und [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Projekte.<br /><br /> Wird von Microsoft.CSharp.targets-Dateien und Microsoft.VisualBasic.targets-Dateien importiert, die die folgende Anweisung verwenden:`<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Definiert die Schritte im Standardbuildprozess für Visual C#-Projekte.<br /><br /> Wird von Visual C#-Projektdateien (CSPROJ) importiert, die die folgende Anweisung verwenden: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Definiert die Schritte im Standardbuildprozess für Visual Basic-Projekte.<br /><br /> Wird von Visual Basic-Projektdateien (VBPROJ) importiert, die die folgende Anweisung verwenden: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
