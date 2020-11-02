---
title: GetOutputFileName-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Hilfsaufgabe „GetOutputFileName“, um Optionen für Ausgabedateinamen für „cl.exe“ und andere Tools anzugeben.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436779"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName-Aufgabe

Hilfsaufgabe zum Abrufen von Ausgabedateinamen für CL und andere Tools, die nur die Angabe des Ausgabeverzeichnisses oder des vollständigen Dateinamens zulassen.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **GetOutputFileName** -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**OutputExtension**|Erforderlicher **String** -Parameter.|
|**OutputFile**|Optionaler **string** -Ausgabeparameter|
|**OutputPath**|Optionaler **string** -Parameter|
|**SourceFile**|Erforderlicher **String** -Parameter.|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
