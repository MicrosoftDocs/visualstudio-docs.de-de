---
title: TARGETS-Dateien von MSBuild | Microsoft-Dokumentation
description: Erfahren Sie mehr über MSBuild-TARGETS-Dateien, die Elemente, Eigenschaften, Ziele und Aufgaben für allgemeine Szenarien enthalten.
ms.custom: SEO-VS-2020
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d25605c83126c41a24f55775d9633e6e4212909c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046363"
---
# <a name="msbuild-targets-files"></a>TARGETS-Dateien von MSBuild

MSBuild umfasst mehrere *TARGETS* -Dateien, die Elemente, Eigenschaften, Ziele und Aufgaben für allgemeine Szenarien enthalten. Diese Dateien werden in die meisten Visual Studio-Projektdateien automatisch importiert, um Lesbarkeit und Verwaltung zu vereinfachen.

 Projekte importieren in der Regel mindestens eine *TARGETS* -Datei, um den entsprechenden Buildprozess zu definieren. Beispielweise importiert ein mit Visual Studio erstelltes C#-Projekt die Datei *Microsoft.CSharp.targets* , die wiederum *Microsoft.Common.targets* importiert. Das C#-Projekt selbst definiert die jeweiligen Elemente und Eigenschaften dieses Projekts. Die standardmäßigen Buildregeln für ein C#-Projekt werden jedoch in den importierten *TARGETS* -Dateien definiert.

 Der `$(MSBuildToolsPath)`-Wert gibt den Pfad dieser allgemeinen *TARGETS* -Dateien an. Für `ToolsVersion` 4.0 befinden die Dateien sich an folgendem Speicherort: *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\*

> [!NOTE]
> Informationen zum Erstellen eigener Ziele finden Sie unter [Targets](../msbuild/msbuild-targets.md) (MSBuild-Ziele). Wie Sie mithilfe des `Import`-Elements eine Projektdatei in eine andere Projektdatei einfügen können, wird unter [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md) und [Vorgehensweise: Verwenden desselben Ziels in mehreren Projektdateien](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md) erklärt.

## <a name="common-targets-files"></a>Allgemeine TARGETS-Dateien

| *TARGETS* -Datei | Beschreibung |
|---------------------------------| - |
| *Microsoft.Common.targets* | Definiert die Schritte im Standardbuildprozess für Visual Basic- und C#-Projekte.<br /><br /> Wird von *Microsoft.CSharp.targets* -Dateien und *Microsoft.VisualBasic.targets* -Dateien importiert, die die folgende Anweisung enthalten: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Definiert die Schritte im Standardbuildprozess für Visual C#-Projekte.<br /><br /> Wird von Visual C#-Projektdateien ( *CSPROJ* ) importiert, die die folgende Anweisung enthalten: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Definiert die Schritte im Standardbuildprozess für Visual Basic-Projekte.<br /><br /> Wird von Visual Basic-Projektdateien ( *VBPROJ* ) importiert, die die folgende Anweisung enthalten: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

Bei *Directory.Build.targets* handelt es sich um eine benutzerdefinierte Datei, die Anpassungen für Projekte in einem Verzeichnis bereitstellt. Diese Datei wird automatisch aus *Microsoft.Common.targets* importiert, wenn die Eigenschaft **ImportDirectoryBuildTargets** nicht auf **FALSE** festgelegt wird. Weitere Informationen finden Sie unter [Anpassen des Builds](customize-your-build.md).

## <a name="see-also"></a>Siehe auch

- [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
