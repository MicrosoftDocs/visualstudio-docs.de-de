---
title: MakeDir-Aufgabe| Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild die MakeDir-Aufgabe verwendet, um Verzeichnisse und ggf. auch übergeordnete Verzeichnisse zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa7b853ea6706c4958635c399bbc6134e823223c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966226"
---
# <a name="makedir-task"></a>MakeDir-Aufgabe

Erstellt Verzeichnisse und ggf. übergeordnete Verzeichnisse

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der `MakeDir` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Directories`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Der Satz von zu erstellenden Verzeichnissen.|
|`DirectoriesCreated`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Die von dieser Aufgabe erstellten Verzeichnisse. Wenn bestimmte Verzeichnisse nicht erstellt werden konnten, enthält dieser Parameter möglicherweise nicht alle Elemente, die an den `Directories`-Parameter übergeben wurden.|

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird das von der Eigenschaft `OutputDirectory` angegebene Verzeichnis mit der `MakeDir`-Aufgabe erstellt.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
    </PropertyGroup>

    <Target Name="CreateDirectories">
        <MakeDir
            Directories="$(OutputDirectory)"/>
    </Target>

</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
