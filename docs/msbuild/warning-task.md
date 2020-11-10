---
title: Warnungsaufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „Warning“ während eines Builds eine Warnung protokolliert, die auf einer ausgewerteten Bedingungsanweisung basiert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce7104c08ce8f18672bf4d2df93debc3c1d19983
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047815"
---
# <a name="warning-task"></a>Warnungsaufgabe

Protokolliert während eines Builds eine Warnung, die auf einer ausgewerteten Bedingungsanweisung basiert

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `Warning` -Aufgabe beschrieben.

| Parameter | Beschreibung |
|---------------| - |
| `Code` | Optionaler `String`-Parameter.<br /><br /> Der Warncode, der der Warnung zugeordnet werden soll. |
| `File` | Optionaler `String`-Parameter.<br /><br /> Gibt die relevante Datei an, falls vorhanden. Wenn keine Datei angegeben wird, wird die Datei verwendet, die die Warnungsaufgabe enthält. |
| `HelpKeyword` | Optionaler `String`-Parameter.<br /><br /> Das der Warnung zuzuordnende Hilfeschlüsselwort. |
| `Text` | Optionaler `String`-Parameter.<br /><br /> Der Warnungstext, den MSBuild protokolliert, wenn der `Condition`-Parameter als `true` ausgewertet wird. |

## <a name="remarks"></a>Hinweise

 Die `Warning`-Aufgabe ermöglicht es MSBuild-Projekten, zu prüfen, ob eine erforderliche Konfiguration oder Eigenschaft vorhanden ist, bevor der nächste Schritt des Buildvorgangs ausgeführt wird.

 Wenn der `Condition`-Parameter der `Warning`-Aufgabe `true` ergibt, wird der Wert des `Text`-Parameters protokolliert und der Build weiter ausgeführt. Wenn kein `Condition`-Parameter vorhanden ist, wird der Warnungstext protokolliert. Weitere Informationen zur Protokollierung finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

 Mithilfe des folgenden Codebeispiels können Sie nach Eigenschaften suchen, die in der Befehlszeile festgelegt sind. Wenn keine Eigenschaften festgelegt sind, löst das Projekt ein Warnungsereignis aus und protokolliert den Wert des `Text`-Parameters der `Warning`-Aufgabe.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Warning
            Text=" The 0 property was not set on the command line."
            Condition="'$(0)' == ''" />
        <Warning
            Text=" The FREEBUILD property was not set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Siehe auch

- [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
