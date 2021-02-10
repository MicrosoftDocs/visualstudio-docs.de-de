---
title: FormatVersion-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie mehr über die verschiedenen Möglichkeiten, mit denen die MSBuild-Aufgabe „FormatVersion“ die Revisionsnummer an die Versionsnummer anfügt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6444811750a59de5488b8ca3614f9926d472746
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905487"
---
# <a name="formatversion-task"></a>FormatVersion-Aufgabe

Fügt die Revisionsnummer an die Versionsnummer an.

- Fall 1: Eingabe: Version=\<undefined>; Revision=\<don't care>; Output: OutputVersion="1.0.0.0"

- Fall 2: Input: Version="1.0.0.*" Revision="5" Output: OutputVersion="1.0.0.5"

- Fall 3: Eingabe: Version = "1.0.0.0" Revision =\<don't care>; Output: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `FormatVersion` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`FormatType`|Optionaler `String`-Parameter.<br /><br /> Gibt den Formattyp an<br /><br /> – "Version" = Version<br />– "Path" = "." durch "_" ersetzen|
|`OutputVersion`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die Ausgabeversion an, die die Revisionsnummer beinhaltet|
|`Revision`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Revision an, die an die Version angefügt werden soll|
|`Version`|Optionaler `String`-Parameter.<br /><br /> Gibt die zu formatierende Versionsnummernzeichenfolge an|

## <a name="remarks"></a>Bemerkungen

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
