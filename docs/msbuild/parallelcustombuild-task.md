---
title: ParallelCustomBuild-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „ParallelCustomBuild“ parallele Instanzen der Aufgabe „CustomBuild“ ausführt.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: f4491d0a5e9c9d3a2554bd32211fd1fa8f7be2d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048896"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild-Aufgabe

Führen Sie parallele Instanzen der [CustomBuild Aufgabe](../msbuild/custombuild-task.md) aus.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **ParallelCustomBuild** -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**BreakOnFirstFailure**|Optionaler **bool** -Parameter.|
|**MaxItemsInBatch**|Optionaler **int** -Parameter.|
|**MaxProcesses**|Optionaler **int** -Parameter.|
|**Sources**|Erforderlicher **ITaskItem[]** -Parameter.|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)