---
title: GetFrameworkSdkPath-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die MSBuild-Aufgabe „GetFrameworkSdkPath“ verwenden, um den Pfad zum Windows SDK abzurufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0fe468f593d085c10f8d077246af6858d0571fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914641"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath-Aufgabe

Ruft den Pfad zum Windows Software Development Kit (SDK) ab.
## <a name="task-parameters"></a>Aufgabenparameter

In der folgenden Tabelle werden die Parameter der `GetFrameworkSdkPath` -Aufgabe beschrieben.
In der folgenden Tabelle werden die Parameter der `GetFrameworkSdkPath` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Optionaler schreibgeschützter `String`-Parameter<br /><br /> Gibt den Pfad zum .NET SDK-Version 2.0 zurück, falls vorhanden Andernfalls wird `String.Empty` zurückgegeben.|
|`FrameworkSdkVersion35Path`|Optionaler schreibgeschützter `String`-Parameter<br /><br /> Gibt den Pfad zum .NET SDK-Version 3.5 zurück, falls vorhanden Andernfalls wird `String.Empty` zurückgegeben.|
|`FrameworkSdkVersion40Path`|Optionaler schreibgeschützter `String`-Parameter<br /><br /> Gibt den Pfad zum .NET SDK-Version 4.0 zurück, falls vorhanden Andernfalls wird `String.Empty` zurückgegeben.|
|`Path`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält den Pfad zum neuesten .NET SDK, wenn eine Version vorhanden ist. Andernfalls wird `String.Empty` zurückgegeben.|

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird mit der Aufgabe `GetFrameworkSdkPath` der Pfad zum Windows SDK in der `SdkPath`-Eigenschaft gespeichert.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkSdkPath>
            <Output
                TaskParameter="Path"
                PropertyName="SdkPath" />
        </GetFrameworkSdkPath>
        <Message Text="$(SdkPath)"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
