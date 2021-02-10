---
title: Elementmetadaten bei der Batchverarbeitung von Zielen | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild Elementmetadaten bei der Batchverarbeitung von Zielen verwendet, um eine Abhängigkeitsanalyse für die Ein- und Ausgaben eines Buildziels auszuführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3389d24ded805c7b1f8bbb8d31daef0cbef1a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913915"
---
# <a name="item-metadata-in-target-batching"></a>Elementmetadaten bei der Batchverarbeitung von Zielen

MSBuild kann eine Abhängigkeitsanalyse für die Ein- und Ausgaben eines Buildziels ausführen. Wenn ermittelt wird, dass die Ein- oder Ausgaben des Ziels auf dem neuesten Stand sind, wird das Ziel übersprungen und der Build fortgesetzt. `Target`-Elemente verwenden die `Inputs`- und `Outputs`-Attribute, um die Elemente festzulegen, die bei der Abhängigkeitsanalyse überprüft werden.

Wenn ein Ziel eine Aufgabe enthält, die Batchelemente als Eingaben oder Ausgaben verwendet, sollte in den `Inputs`- oder `Outputs`-Attributen von Element `Target` im Ziel die Batchverarbeitung genutzt werden, damit MSBuild Elementbatches überspringen kann, die bereits auf dem neuesten Stand sind.

## <a name="batch-targets"></a>Ziele für die Batchverarbeitung

Das folgende Beispiel enthält die Elementliste `Res`, die mithilfe der `Culture`-Elementmetadaten in zwei Batches aufgeteilt wird. Jeder Batch wird der `AL`-Aufgabe übergeben, die jeweils eine Ausgabeassembly erstellt. Durch die Batchverarbeitung von `Outputs`-Attributen des `Target`-Elements kann MSBuild vor dem Ausführen des Ziels ermitteln, ob jeder Batch aktuell ist. Ohne die Batchverarbeitung von Zielen würden beide Elementbatches immer dann von der Aufgabe ausgeführt werden, wenn das Ziel ausgeführt wird.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Res Include="Strings.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Strings.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.jp.resources">
            <Culture>jp</Culture>
        </Res>
    </ItemGroup>

    <Target Name="Build"
        Inputs="@(Res)"
        Outputs="%(Culture)\MyApp.resources.dll">

        <AL Resources="@(Res)"
            TargetType="library"
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [How to: Inkrementelles Erstellen](../msbuild/how-to-build-incrementally.md)
- [Batchverarbeitung](../msbuild/msbuild-batching.md)
- [Target-Element (MSBuild)](../msbuild/target-element-msbuild.md)
- [Elementmetadaten bei der Batchverarbeitung von Aufgaben](../msbuild/item-metadata-in-task-batching.md)
