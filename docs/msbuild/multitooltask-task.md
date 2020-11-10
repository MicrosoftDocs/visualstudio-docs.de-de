---
title: MultiToolTask-Aufgabe | Microsoft-Dokumentation
description: Tabelle mit Beschreibungen der erforderlichen und optionalen Parameter der MSBuild-Aufgabe „MultiToolTask“
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), MultiToolTask task
- MultiToolTask task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d76aa3762b254ee35ada1e4e81fe857f509a4e5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048976"
---
# <a name="multitooltask-task"></a>MultiToolTask-Aufgabe

Keine Beschreibung

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **MultiToolTask** -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|Optionaler **string[]** -Parameter|
|**SemaphoreProcCount**|Optionaler **string** -Parameter|
|**SchedulerFunction**|Optionaler **string** -Parameter|
|**SchedulerVerbose**|Optionaler **bool** -Parameter.|
|**Sources**|Erforderlicher **ITaskItem[]** -Parameter.|
|**TaskAssemblyName**|Optionaler **string** -Parameter|
|**TaskName**|Erforderlicher **String** -Parameter.|
|**TrackerLogDirectory**|Erforderlicher **String** -Parameter.|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
