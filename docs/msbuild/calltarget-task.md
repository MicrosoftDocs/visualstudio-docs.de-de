---
title: CallTarget-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die MSBuild-Aufgabe „CallTarget“ verwenden, um die angegebenen Ziele in der Projektdatei aufzurufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efeca838050c9024ad3768b2ac7f73ce7dd06720
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353290"
---
# <a name="calltarget-task"></a>CallTarget-Aufgabe

Ruft die angegebenen Ziele in der Projektdatei ab.

## <a name="task-parameters"></a>Aufgabenparameter

 In der folgenden Tabelle werden die Parameter der `CallTarget` -Aufgabe beschrieben.

| Parameter | Beschreibung |
|---------------------------| - |
| `RunEachTargetSeparately` | Optionaler `Boolean`-Eingabeparameter.<br /><br /> Bei Festlegung auf `true`, wird die MSBuild-Engine einmal pro Ziel aufgerufen. Bei Festlegung auf `false`, wird die MSBuild-Engine einmal aufgerufen, um alle Ziele zu erstellen. Der Standardwert ist `false`. |
| `TargetOutputs` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Ausgaben aller erstellten Ziele. |
| `Targets` | Optionaler `String[]`-Parameter.<br /><br /> Gibt das Ziel oder die Ziele an, die erstellt werden sollen. |
| `UseResultsCache` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird das zwischengespeicherte Ergebnis zurückgegeben, sofern es vorhanden ist.<br /><br /> **Hinweis** Wenn eine MSBuild-Aufgabe ausgeführt wird, wird deren Ausgabe in einem Gültigkeitsbereich als eine Liste von Buildelementen zwischengespeichert (ProjectFileName, GlobalProperties)[TargetNames]. |

## <a name="remarks"></a>Hinweise

 Wenn ein in `Targets` angegebenes Ziel fehlschlägt und `RunEachTargetSeparately``true` ist, fährt die Aufgabe mit dem Erstellen der verbleibenden Ziele fort.

 Wenn Sie die Standardziele erstellen möchten, verwenden Sie die [MSBuild-Aufgabe](../msbuild/msbuild-task.md), und legen Sie den `Projects`-Parameter auf `$(MSBuildProjectFile)` fest.

Bei Verwendung von `CallTarget` wertet MSBuild das aufgerufene Ziel in einem neuen Bereich aus und nicht in dem Bereich, aus dem es aufgerufen wurde. Das bedeutet, dass alle Änderungen an Elementen und Eigenschaften im aufgerufenen Ziel für das aufrufende Ziel nicht sichtbar sind.  Verwenden Sie zur Übergabe von Informationen an das aufrufende Ziel den Ausgabeparameter `TargetOutputs`.

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

 Über das folgende Beispiel wird `TargetA` in `CallOtherTargets` aufgerufen.

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Ziele](../msbuild/msbuild-targets.md)
