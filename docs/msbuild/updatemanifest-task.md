---
title: UpdateManifest-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „UpdateManifest“ ausgewählte Eigenschaften in einem Manifest aktualisiert und eine erneute Signierung durchführt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8bb090b66a52e9c2931e8bf4afc878d87a0ae36
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902506"
---
# <a name="updatemanifest-task"></a>UpdateManifest-Aufgabe

Aktualisiert die ausgewählten Eigenschaften in einem Manifest und führt das Signieren erneut aus.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `UpdateManifest` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`ApplicationManifest`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt das Anwendungsmanifest an|
|`ApplicationPath`|Erforderlicher `String`-Parameter.<br /><br /> Gibt den Pfad für das Anwendungsmanifest an|
|`InputManifest`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt das upzudatende Manifest an|
|`OutputManifest`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt das Manifest an, das geupdatete Eigenschaften enthält|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Utilities.Task>-Klasse. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [Taskbasisklasse](../msbuild/task-base-class.md).

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)