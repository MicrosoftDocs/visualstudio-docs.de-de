---
title: Elementmetadaten bei der Batchverarbeitung von Aufgaben | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild Elementmetadaten bei der Batchverarbeitung von Aufgaben verwendet, um Elementlisten in verschiedene Kategorien (Batches) zu unterteilen und mit jedem Batch einmalig eine Aufgabe auszuführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1d67f740857dc93b997e206c43dd52d9887f3e9
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903720"
---
# <a name="item-metadata-in-task-batching"></a>Elementmetadaten bei der Batchverarbeitung von Aufgaben

MSBuild kann Elementlisten anhand von Elementmetadatenelementen in verschiedene Kategorien oder Batches unterteilen und einmal mit jedem Batch eine Aufgabe ausführen. Es ist schwierig zu erkennen, welche Elemente mit welchem Batch übergeben werden. In diesem Artikel werden die folgenden häufig auftretenden Szenarios thematisiert, bei denen die Batchverarbeitung ein Bestandteil ist.

- Unterteilen einer Elementliste in Batches

- Unterteilen mehrerer Elementlisten in Batches

- Batchverarbeitung einzelner Elemente

- Filtern von Elementlisten

Weitere Informationen zur Batchverarbeitung mit MSBuild finden Sie unter [Batchverarbeitung](../msbuild/msbuild-batching.md).

## <a name="divide-an-item-list-into-batches"></a>Unterteilen einer Elementliste in Batches

Mithilfe der Batchverarbeitung können Sie anhand von Elementmetadatenelementen eine Elementliste in verschiedene Batches unterteilen und diese Batches anschließend einzeln an eine Aufgabe übergeben. Dieser Vorgang ist nützlich für die Erstellung von Satellitenassemblys.

Im untenstehenden Beispiel wird dargestellt, wie Sie eine Elementliste anhand von Elementmetadatenelementen in Batches unterteilen können. Die Elementliste `ExampColl` wird anhand des Elementmetadatenelements `Number` in drei Batches unterteilt. Durch das Vorhandensein von `%(ExampColl.Number)` im `Text`-Attribut wird MSBuild benachrichtigt, dass eine Batchverarbeitung ausgeführt werden sollte. Die Elementliste `ExampColl` ist anhand des Elementmetadatenelements `Number` in drei Batches unterteilt, und jeder Batch wird einzeln an eine Aufgabe übergeben.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>
    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

Die [Message Task](../msbuild/message-task.md) zeigt die folgenden Informationen an:

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>Unterteilen mehrerer Elementlisten in Batches

MSBuild kann mehrere Elementlisten anhand derselben Metadaten in Batches unterteilen. Dadurch können verschiedene Elementlisten einfacher in Batches unterteilt werden, um mehrere Assemblys zu erstellen. Beispielsweise kann eine Elementliste mit *CS* -Dateien, die in ein Anwendungs- und ein Assemblybatch unterteilt sind, sowie eine Elementliste mit Ressourcendateien, die in ein Anwendungs- und ein Assemblybatch unterteilt sind, vorhanden sein. In diesem Fall können Sie die Batchverarbeitung nutzen, um diese Elementlisten an eine Aufgabe zu übergeben und sowohl die Anwendung als auch die Assembly zu erstellen.

> [!NOTE]
> Wenn eine Elementliste, die an eine Aufgabe übergeben wird, keine Elemente mit dem Metadatenelement enthält, auf das verwiesen wird, werden sämtliche Elemente in dieser Elementliste an jeden Batch übergeben.

Im untenstehenden Beispiel wird dargestellt, wie Sie mehrere Elementlisten anhand von Elementmetadatenelementen in Batches unterteilen können. Die Elementlisten `ExampColl` und `ExampColl2` werden jeweils anhand des Elementmetadatenelements `Number` in drei Batches unterteilt. Durch das Vorhandensein von `%(Number)` im `Text`-Attribut wird MSBuild benachrichtigt, dass eine Batchverarbeitung ausgeführt werden sollte. Die Elementlisten `ExampColl` und `ExampColl2` werden jeweils anhand des Elementmetadatenelements `Number` in drei Batches unterteilt, und jeder Batch wird einzeln an eine Aufgabe übergeben.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>

        <ExampColl2 Include="Item4">
            <Number>1</Number>
        </ExampColl2>
        <ExampColl2 Include="Item5">
            <Number>2</Number>
        </ExampColl2>
        <ExampColl2 Include="Item6">
            <Number>3</Number>
        </ExampColl2>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>
    </Target>

</Project>
```

Die [Message Task](../msbuild/message-task.md) zeigt die folgenden Informationen an:

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>Batchverarbeitung einzelner Elemente nacheinander

Die Batchverarbeitung kann auch für bekannte Elementmetadaten durchgeführt werden, die jedem Element bei der Erstellung zugeordnet werden. Dadurch wird garantiert, dass jedes Element in einer Auflistung auch über Metadaten verfügt, die bei der Batchverarbeitung verwendet werden können. Jedes Element hat seinen eigenen `Identity`-Metadatenwert, der nützlich für die Unterteilung der in Elementlisten enthaltenen Elemente in separate Batches ist. Eine vollständige Liste bekannter Elementmetadaten finden Sie unter [Bekannte Elementmetadaten](../msbuild/msbuild-well-known-item-metadata.md).

Im untenstehenden Beispiel wird dargestellt, wie Sie die Elemente in einer Elementliste einzeln nacheinander in Batches unterteilen können. Da jedes Element seinen eigenen `Identity`-Metadatenwert hat, wird die Elementliste `ExampColl` in sechs Batches unterteilt, wobei jedes Batch jeweils ein Element der Elementliste enthält. Durch das Vorhandensein von `%(Identity)` im `Text`-Attribut wird MSBuild benachrichtigt, dass eine Batchverarbeitung ausgeführt werden sollte.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1"/>
        <ExampColl Include="Item2"/>
        <ExampColl Include="Item3"/>
        <ExampColl Include="Item4"/>
        <ExampColl Include="Item5"/>
        <ExampColl Include="Item6"/>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Identity: '%(Identity)' -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

Die [Message Task](../msbuild/message-task.md) zeigt die folgenden Informationen an:

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

## <a name="filter-item-lists"></a>Filtern von Elementlisten

Die Batchverarbeitung kann auch dafür genutzt werden, bestimmte Elemente einer Elementliste herauszufiltern, bevor sie an eine Aufgabe übergeben wird. Wenn Sie z.B. nach dem bekannten `Extension`-Elementmetadatenwert filtern, können Sie eine Aufgabe nur für Dateien ausführen, die eine spezifische Erweiterung enthalten.

Im untenstehenden Beispiel wird dargestellt, wie Sie zunächst eine Elementliste anhand eines Elementmetadatenelements in Batches unterteilen und anschließend diese Batches bei der Übergabe an eine Aufgabe filtern. Die Elementliste `ExampColl` wird anhand des Elementmetadatenelements `Number` in drei Batches unterteilt. Das `Condition`-Attribut einer Aufgabe gibt an, dass nur Batches mit einem `Number`-Elementmetadatenwert von `2` an die Aufgabe übergeben werden sollen.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>

    </ItemGroup>

    <Target Name="Exec">
        <Message
            Text = "Items in ExampColl: @(ExampColl)"
            Condition="'%(Number)'=='2'"/>
    </Target>

</Project>
```

Die [Message Task](../msbuild/message-task.md) zeigt die folgenden Informationen an:

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>Siehe auch

- [Bekannte Elementmetadaten](../msbuild/msbuild-well-known-item-metadata.md)
- [Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)
- [ItemMetadata-Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Batchverarbeitung](../msbuild/msbuild-batching.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
