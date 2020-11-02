---
title: GetOutOfDateItems-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Hilfsaufgabe „GetOutOfDateItems“, um Transaktionsprotokolle zu lesen und zu schreiben und um Elemente zurückzugeben, die nicht auf dem neuesten Stand sind.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 6cc80d4e1aa3580e0185460d19f78e9737b73220
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436823"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems-Aufgabe

Hilfsaufgabe zum Lesen alter Nachverfolgungsprotokolle, Schreiben neuer Nachverfolgungsprotokolle und Zurückgeben von Elementen, die nicht auf dem neuesten Stand sind.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **GetOutOfDateItems-Aufgabe** beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**CheckForInterdependencies**|Optionaler **bool** -Parameter.|
|**CommandMetadataName**|Optionaler **string** -Parameter|
|**DependenciesMetadataName**|Optionaler **string** -Parameter|
|**HasInterdependencies**|Optionaler **bool** -Ausgabeparameter|
|**OutOfDateSources**|Optionaler **ITaskItem[]** -Ausgabeparameter.|
|**OutputsMetadataName**|Erforderlicher **String** -Parameter.|
|**Sources**|Optionaler **ITaskItem[]** -Parameter.|
|**TLogDirectory**|Erforderlicher **String** -Parameter.|
|**TLogNamePrefix**|Erforderlicher **String** -Parameter.|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)