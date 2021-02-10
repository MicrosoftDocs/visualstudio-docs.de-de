---
title: AssignTargetPath-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Aufgabe „AssignTargetPath“, um eine Liste mit Dateien zu akzeptieren und TargetPath-Attribute hinzuzufügen, sofern diese nicht bereits angegeben wurden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f3a46b16bc689e0753b806c4239544e1ddbd73f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964939"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath-Aufgabe

Diese Aufgabe akzeptiert eine Liste von Dateien und fügt `<TargetPath>`-Attribute hinzu, wenn diese nicht bereits angegeben wurden.

## <a name="task-parameters"></a>Aufgabenparameter

In der folgenden Tabelle werden die Parameter der `AssignTargetPath` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`RootFolder`|Optionaler `string`-Eingabeparameter.<br /><br /> Enthält den Pfad zu dem Ordner, der die Ziellinks enthält.|
|`Files`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Eingabeparameter.<br /><br /> Enthält die eingehende Liste von Dateien.|
|`AssignedFiles`|Optional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]`-Ausgabeparameter.<br /><br /> Enthält die resultierende Liste von Dateien.|

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel führt die `AssignTargetPath`-Aufgabe aus, um ein Projekt zu konfigurieren.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyProject">
        <AssignTargetPath
RootFolder="Resources"
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
        </AssignTargetPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
