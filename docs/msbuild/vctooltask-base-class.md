---
title: VCToolTask-Klasse | Microsoft-Dokumentation
description: Erfahren Sie mehr über verschiedene Parameter, die die Basisklasse „VCToolTask“ den Aufgaben hinzufügt, die von ihr erben.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b2e45d7c672ebc2177c2bb197399133e7b077a5c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046739"
---
# <a name="vctooltask-base-class"></a>VCToolTask-Basisklasse

Viele Aufgaben erben von der <xref:Microsoft.Build.Utilities.Task>-Klasse und der [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)-Klasse. Diese Klasse fügt den Aufgaben, die ihr abgeleitet werden, mehrere Parameter hinzu. Diese Parameter werden in diesem Dokument aufgeführt.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **VCToolTask** -Basisklasse beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Optionaler **Dictionary\<string, ToolSwitch>** -Parameter.|
|**AdditionalOptions**|Optionaler **string** -Parameter|
|**EffectiveWorkingDirectory**|Optionaler **string** -Parameter|
|**EnableErrorListRegex**|Optionaler **bool** -Parameter.<br/><br/>Der Standardwert ist `true`.|
|**ErrorListRegex**|Optionaler **ITaskItem[]** -Parameter.|
|**ErrorListListExclusion**|Optionaler **ITaskItem[]** -Parameter.|
|**GenerateCommandLine**|Optionaler **string** -Parameter<br/><br/>Verwendet die Werte **CommandLineFormat** *format* [Standardwert = CommandLineFormat.ForBuildLog] und **EscapeFormat** *escapeFormat* [Standardwert = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Optionaler **string** -Parameter<br/><br/>Verwendet die Werte **string[]** *switchesToRemove* , **CommandLineFormat** *format* [Standardwert = CommandLineFormat.ForBuildLog] und **EscapeFormat** *escapeFormat* [Standardwert = EscapeFormat.Default].|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)<br/>
[Aufgaben](../msbuild/msbuild-tasks.md)
