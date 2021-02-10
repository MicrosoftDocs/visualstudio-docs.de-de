---
title: FindInList-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die MSBuild-Aufgabe „FindInList“ verwenden, um in einer angegebenen Liste nach einem Element zu suchen, das über die entsprechende Elementspezifikation verfügt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45ad1cc57412161e2510f93cacb5a043be59802e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967552"
---
# <a name="findinlist-task"></a>FindInList-Aufgabe

Sucht in einer angegebenen Liste ein Element, das über die entsprechende Elementspezifikation verfügt

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der [FindInList-Aufgabe](../msbuild/findinlist-task.md) beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`CaseSensitive`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, wird die Groß- und Kleinschreibung bei der Suche berücksichtigt. Andernfalls ist die Groß- und Kleinschreibung unerheblich. Der Standardwert ist `true`.|
|`FindLastMatch`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird die letzte Übereinstimmung zurückgegeben. Ansonsten wird die erste Übereinstimmung zurückgegeben. Der Standardwert ist `false`.|
|`ItemFound`|Optionaler schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Parameter.<br /><br /> Das erste übereinstimmende Element in der Liste, sofern vorhanden|
|`ItemSpecToFind`|Erforderlicher `String`-Parameter.<br /><br /> Die zu suchende Elementspezifikation|
|`List`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Die Liste, in der nach der Elementspezifikation gesucht werden soll|
|`MatchFileNameOnly`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird nur gegen den Dateinamenteil der Elementspezifikation abgeglichen. Andernfalls wird die gesamte Elementspezifikation abgeglichen. Der Standardwert ist `true`sein.|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
