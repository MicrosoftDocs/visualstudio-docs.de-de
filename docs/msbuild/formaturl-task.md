---
title: FormatUrl-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die MSBuild-Aufgabe „FormatUrl“ verwenden, um eine Eingabe-URL in ein gültiges URL-Ausgabeformat zu konvertieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9a05ce16289c012b067faa5bc302a3921cbe1c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888094"
---
# <a name="formaturl-task"></a>FormatUrl-Aufgabe

Konvertiert eine URL in ein gültiges URL-Format

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `FormatUrl` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`InputUrl`|Optionaler `String`-Parameter.<br /><br /> Gibt die zu formatierende URL an|
|`OutputUrl`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die formatierte URL an|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)