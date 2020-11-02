---
title: DownloadFile-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Parameter der MSBuild-Aufgabe „DownloadFile“, mit der angegebene Dateien unter Verwendung von HTTP heruntergeladen werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fda3edcd1c8bf173e1b70d8bf2d76d58f6e10d8d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436650"
---
# <a name="downloadfile-task"></a>DownloadFile-Aufgabe

Diese Aufgabe lädt die angegebenen Dateien mithilfe des Hypertext Transfer-Protokolls (HTTP) herunter.

>[!NOTE]
>Die DownloadFile-Aufgabe ist nur in MSBuild 15.8 und höher verfügbar.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der `DownloadFile` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`DestinationFileName`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter<br /><br /> Der Name, der für die heruntergeladene Datei verwendet werden soll.  Der Dateiname wird standardmäßig von `SourceUrl` oder vom Remoteserver abgeleitet.|
|`DestinationFolder`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt den Zielordner an, in den die Datei heruntergeladen werden soll.  Der Ordner wird erstellt, falls er noch nicht vorhanden ist.|
|`DownloadedFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt die Datei an, die heruntergeladen wird.|
|`Retries`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Anzahl der vorgesehenen Downloadversuche an, wenn alle vorherigen Versuche fehlgeschlagen sind. Der Standardwert ist 0 (null).|
|`RetryDelayMilliseconds`|Optionaler `Int32`-Parameter.<br /><br /> Gibt die Verzögerung zwischen jeglichen erforderlichen Wiederholungen in Millisekunden an. Diese wird standardmäßig auf 5000 festgelegt.|
|`SkipUnchangedFiles`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true` festgelegt ist, wird das Herunterladen der unveränderten Dateien übersprungen. Wird standardmäßig auf `true` festgelegt. In der `DownloadFile`-Aufgabe werden Dateien als unverändert betrachtet, wenn sie laut dem Remoteserver dieselbe Größe aufweisen und zur selben Zeit zuletzt geändert wurden. <br /><br />**Hinweis:** Nicht alle HTTP-Server geben das letzte Änderungsdatum von Dateien an. Dadurch wird die Datei erneut heruntergeladen.|
|`SourceUrl`|Erforderlicher `String`-Parameter.<br /><br /> Gibt die URL für den Download an.|

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

In folgendem Beispiel wird eine Datei heruntergeladen und in die `Content`-Elemente eingeschlossen, bevor das Projekt erstellt wird.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
