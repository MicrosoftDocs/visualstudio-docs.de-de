---
title: CustomBuild-Aufgabe | Microsoft-Dokumentation
description: In diesem Artikel wird die MSBuild-Aufgabe „CustomBuild“ beschrieben, die von MSBuild verwendet wird, um die Anpassung des C++-Buildprozesses zu unterstützen.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796549"
---
# <a name="custombuild-task"></a>CustomBuild-Aufgabe

Umschließt das Microsoft C++-Compilertool (cmd.exe). Diese Klasse wird von [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md) abgeleitet, ermittelt jedoch keine Abhängigkeiten mit der Dateinachverfolgung. Alle Abhängigkeiten sollten explizit als AdditionalDependencies festgelegt werden, um eine ordnungsgemäße Funktion von inkrementellen Builds sicherzustellen.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **CustomBuild-Aufgabe** beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**BuildSuffix**|Optionaler **string** -Parameter|
|**Sources**|Erforderlicher **ITaskItem[]** -Parameter.|
|**TrackerLogDirectory**|Optionaler **string** -Parameter|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
