---
title: Diagnostizieren von Taskfehlern | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Fehlerdiagnose für MSBuild-Aufgaben durchführen, indem Sie die fehlerhafte Aufgabe, den Toolnamen und weitere Informationen ermitteln.
ms.custom: SEO-VS-2020
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eaf55cc529be8fc61e05d1a76096e26d965aa136
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796471"
---
# <a name="diagnosing-task-failures"></a>Diagnostizieren von Taskfehlern

`MSB6006` wird in folgendem Fall ausgegeben: Eine aus <xref:Microsoft.Build.Utilities.ToolTask> abgeleitete Klasse führt einen Toolprozess aus, der einen Exitcode ungleich null ausgibt, wenn der Task keinen spezifischeren Fehler protokolliert hat.

## <a name="identifying-the-failing-task"></a>Ermitteln des fehlerhaften Tasks

Bei einem Taskfehler muss zuerst herausgefunden werden, in welchem Task der Fehler auftritt.

Der Fehlertext gibt den Namen des Tools (entweder ein von der <xref:Microsoft.Build.Utilities.ToolTask.ToolName>-Implementierung des Tasks bereitgestellter Anzeigename oder der Name der ausführbaren Datei) und den numerischen Exitcode an. Beispiel:

```text
error MSB6006: "custom tool" exited with code 1.
```

Der Toolname lautet `custom tool` und der Exitcode `1`.

### <a name="command-line-builds"></a>Builds über die Befehlszeile

Wenn der Build so konfiguriert ist, dass eine Übersicht enthalten ist (Standardeinstellung), sieht die Übersicht folgendermaßen aus:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Dieses Ergebnis weist darauf hin, dass der Fehler in einem Task aufgetreten ist, der in Zeile 19 der Datei `S:\MSB6006_demo\MSB6006_demo.csproj` in einem Ziel namens `InvokeToolTask` im Projekt `S:\MSB6006_demo\MSB6006_demo.csproj` definiert wurde.

### <a name="in-visual-studio"></a>In Visual Studio

Die gleichen Informationen stehen in der Visual Studio-Fehlerliste in den Spalten `Project`, `File` und `Line` zur Verfügung.

## <a name="finding-more-failure-information"></a>Suchen nach weiteren Fehlerinformationen

Dieser Fehler wird ausgegeben, wenn der Task keinen spezifischen Fehler protokolliert hat. Der Grund hierfür ist häufig, dass der Task das von dem aufgerufenen Tool ausgegebene Fehlerformat nicht kennt.

Ordnungsgemäß konfigurierte Tools geben im Allgemeinen Kontext- oder Fehlerinformationen in ihren standardmäßigen Ausgabe- oder Fehlerstream aus, und Tasks erfassen und protokollieren diese Informationen in der Regel. Sehen Sie sich die Protokolleinträge vor dem Auftreten des Fehlers an, um weitere Informationen zu erhalten. Möglicherweise muss der Build mit einem höheren Protokolliergrad erneut ausgeführt werden, um diese Informationen beizubehalten.

## <a name="next-steps"></a>Nächste Schritte

Der zusätzliche Kontext oder weitere Fehlerinformationen in den Protokollen sollten auf die Ursache eines Problems hinweisen.

Wenn dies nicht der Fall ist, müssen Sie die möglichen Ursachen eingrenzen, indem Sie die Eigenschaften und Elemente untersuchen, die als Eingaben für den fehlerhaften Task verwendet wurden.
