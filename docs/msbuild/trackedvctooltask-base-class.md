---
title: TrackedVCToolTask-Klasse | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Parameter, die die Basisklasse „TrackedVCToolTask“ den Aufgaben hinzufügt, die von ihr erben.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 01b55e0ad88cb520078479217306bac948e6cd60
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046997"
---
# <a name="trackedvctooltask-base-class"></a>TrackedVCToolTask-Basisklasse

Viele Aufgaben erben von der <xref:Microsoft.Build.Utilities.Task>-Klasse und der [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)-Klasse. Diese Klasse fügt den von [VCToolTask](../msbuild/vctooltask-base-class.md) abgeleiteten Aufgaben mehrere Parameter hinzu. Diese Parameter werden in diesem Dokument aufgeführt.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der **TrackedVCToolTask** -Basisklasse beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Optionaler **bool** -Parameter.|
|**EnableExecuteTool**|Optionaler **bool** -Parameter.|
|**ExcludedInputPaths**|Optionaler **ITaskItem[]** -Parameter.|
|**MinimalRebuildFromTracking**|Optionaler **bool** -Parameter.|
|**PathOverride**|Optionaler **string** -Parameter|
|**PostBuildTrackingCleanup**|Optionaler **bool** -Parameter.|
|**RootSource**|Optionaler **string** -Parameter|
|**SkippedExecution**|Optionaler **bool** -Ausgabeparameter|
|**SourcesCompiled**|Optionaler **ITaskItem[]** -Ausgabeparameter.|
|**TLogCommandFile**|Optionaler **ITaskItem** -Parameter|
|**TLogReadFiles**|Optionaler **ITaskItem[]** -Parameter.|
|**TLogWriteFiles**|Optionaler **ITaskItem[]** -Parameter.|
|**ToolArchitecture**|Optionaler **string** -Parameter|
|**TrackCommandLines**|Optionaler **bool** -Parameter.|
|**TrackFileAccess**|Optionaler **bool** -Parameter.|
|**TrackedInputFilesToIgnore**|Optionaler **ITaskItem[]** -Parameter.|
|**TrackedOutputFilesToIgnore**|Optionaler **ITaskItem[]** -Parameter.|
|**TrackerFrameworkPath**|Optionaler **string** -Parameter|
|**TrackerSdkPath**|Optionaler **string** -Parameter|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)<br/>
[Aufgaben](../msbuild/msbuild-tasks.md)
