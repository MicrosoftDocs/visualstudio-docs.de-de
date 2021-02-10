---
title: MSBuild-Batchverarbeitung | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild Elementlisten basierend auf den Elementmetadaten in verschiedene Kategorien oder Batches unterteilt und ein Ziel oder eine Aufgabe einmal mit jedem Batch ausführt.
ms.custom: SEO-VS-2020
ms.date: 06/09/2020
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d14a979a166f7378c288453530b46b8ec6c98828
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919196"
---
# <a name="msbuild-batching"></a>MSBuild-Batchverarbeitung

MSBuild unterteilt Elementlisten basierend auf den Elementmetadaten in verschiedene Kategorien oder Batches und führt ein Ziel oder eine Aufgabe einmal mit jedem Batch aus.

## <a name="task-batching"></a>Aufgabenbatchverarbeitung

Durch die Aufgabenbatchverarbeitung können Sie Ihre Projektdateien vereinfachen, indem Sie Elementlisten in verschiedene Batches unterteilen und jeden dieser Batches separat an eine Aufgabe übergeben können. Dies bedeutet, dass die Aufgabe und ihre Attribute für eine Projektdatei nur einmal deklariert werden müssen, obwohl sie mehrmals ausgeführt werden können.

Sie geben an, dass MSBuild die Batchverarbeitung mit einer Aufgabe ausführen soll, indem Sie die Notation `%(ItemMetaDataName)` in einem der Attribute der Aufgabe verwenden. Im folgenden Beispiel wird die Elementliste `Example` basierend auf dem Metadatenwert des Elements `Color` in Batches aufgeteilt, und alle Batches werden separat an die Aufgabe `MyTask` übergeben.

> [!NOTE]
> Wenn Sie an keiner anderen Stelle in den Attributen der Aufgabe auf die Elementliste verweisen oder der Metadatenname möglicherweise mehrdeutig ist, können Sie die Notation %(<ItemCollection.ItemMetaDataName>) verwenden, um den Metadatenwert des Elements vollständig für die Batchverarbeitung zu qualifizieren.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Weitere Beispiele für die Batchverarbeitung finden Sie unter [Elementmetadaten bei der Aufgabenbatchverarbeitung](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Zielbatchverarbeitung

MSBuild überprüft, ob die Ein- und Ausgaben eines Ziels aktuell sind, bevor das Ziel ausgeführt wird. Wenn die Ein- und Ausgaben aktuell sind, wird das Ziel übersprungen. Wenn eine Aufgabe innerhalb eines Ziels die Batchverarbeitung verwendet, muss MSBuild bestimmen, ob die Ein- und Ausgaben für jeden Batch mit Elementen aktuell sind. Andernfalls wird das Ziel jedes Mal ausgeführt, wenn es erreicht wird.

Im folgenden Beispiel wird ein `Target`-Element dargestellt, das ein `Outputs`-Attribut mit der Notation `%(ItemMetadataName)` enthält. MSBuild unterteilt die `Example`-Elementliste basierend auf den Metadaten des `Color`-Elements in Batches und analysiert die Zeitstempel der Ausgabedateien jedes Batchs. Wenn die Ausgaben eines Batchs nicht aktuell sind, wird das Ziel ausgeführt. Andernfalls wird das Ziel übersprungen.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Ein weiteres Beispiel für die Zielbatchverarbeitung finden Sie unter [Elementmetadaten bei der Zielbatchverarbeitung](../msbuild/item-metadata-in-target-batching.md).

## <a name="item-and-property-mutations"></a>Änderungen von Elementen und Eigenschaften

In diesem Abschnitt wird beschrieben, wie die Auswirkungen des Änderns von Eigenschaften und/oder der Metadaten von Elementen bei der Batchverarbeitung von Zielen oder Aufgaben zu verstehen sind.

Da die Batchverarbeitung von Zielen und Aufgaben zwei verschiedene MSBuild-Vorgänge sind, ist es wichtig, genau zu verstehen, welche Form der Batchverarbeitung MSBuild im jeweiligen Fall wählt. Wenn die Batchverarbeitungssyntax `%(ItemMetadataName)` in einer Aufgabe in einem Ziel, aber nicht in einem Attribut für das Ziel angezeigt wird, verwendet MSBuild die Aufgabenbatchverarbeitung. Die einzige Möglichkeit, die Zielbatchverarbeitung anzugeben, ist die Verwendung der Batchverarbeitungssyntax für ein Zielattribut, normalerweise das Attribut `Outputs`.

Sowohl bei der Ziel- als auch bei der Aufgabenbatchverarbeitung kann davon ausgegangen werden, dass die Batches unabhängig voneinander ausgeführt werden. Alle Batches beginnen mit einer Kopie desselben Anfangszustands der Werte für Eigenschaften und Metadaten von Elementen. Alle Änderungen von Eigenschaftswerten während der Batchverarbeitung sind für andere Batches nicht sichtbar. Betrachten Sie das folgende Beispiel:

```xml
  <ItemGroup>
    <Thing Include="2" Color="blue" />
    <Thing Include="1" Color="red" />
  </ItemGroup>

  <Target Name="DemoIndependentBatches">
    <ItemGroup>
      <Thing Condition=" '%(Color)' == 'blue' ">
        <Color>red</Color>
        <NeededColorChange>true</NeededColorChange>
      </Thing>
    </ItemGroup>
    <Message Importance="high"
             Text="Things: @(Thing->'%(Identity) is %(Color); needed change=%(NeededColorChange)')"/>
  </Target>
```

Ausgabe:

```output
Target DemoIndependentBatches:
  Things: 2 is red; needed change=true;1 is red; needed change=
```

`ItemGroup` im Ziel ist implizit eine Aufgabe, und bei `%(Color)` im Attribut `Condition` erfolgt eine Aufgabenbatchverarbeitung. Es gibt zwei Batches: eines für rot und das andere für blau. Die Eigenschaft `%(NeededColorChange)` wird nur festgelegt, wenn die Metadaten von `%(Color)` blau sind. Die Einstellung wirkt sich nur auf das einzelne Element aus, das der Bedingung bei Ausführung des blauen Batches entsprach. Das Attribut `Text` der Aufgabe `Message` löst trotz der Syntax `%(ItemMetadataName)` keine Batchverarbeitung aus, da es innerhalb einer Elementtransformation verwendet wird.

Batches werden unabhängig, aber nicht parallel ausgeführt. Das ist ein Unterschied, wenn Sie auf Metadatenwerte zugreifen, die sich bei der Batchausführung ändern. Für den Fall, dass Sie eine Eigenschaft basierend auf einigen Metadaten in der Batchausführung festlegen, würde die Eigenschaft die *letzte* Wertgruppe verwenden:

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

Nach der Batchausführung behält die Eigenschaft den endgültigen Wert `%(MetadataValue)` bei.

Obwohl Batches unabhängig ausgeführt werden, ist es wichtig, den Unterschied zwischen der Ziel- und der Aufgabenbatchverarbeitung zu berücksichtigen und zu wissen, welcher Typ für Ihre Situation gilt. Betrachten Sie das folgende Beispiel, um die Bedeutung dieser Unterscheidung besser zu verstehen.

Aufgaben können implizit statt explizit sein, was verwirrend sein kann, wenn die Aufgabenbatchverarbeitung mit impliziten Aufgaben erfolgt. Wenn ein Element des Typs `PropertyGroup` oder `ItemGroup` in einem Element des Typs `Target` vorkommt, wird jede Eigenschaftsdeklaration in der Gruppe implizit wie eine separate Aufgabe des Typs [CreateProperty](createproperty-task.md) oder [CreateItem](createitem-task.md) behandelt. Das bedeutet, dass das Verhalten bei einer Zielbatchverarbeitung anders ist als bei einer Nicht-Zielbatchverarbeitung (d. h., wenn die Syntax `%(ItemMetadataName)` im Attribut `Outputs` fehlt). Bei der Zielbatchverarbeitung wird `ItemGroup` einmal pro Ziel ausgeführt. Wenn für das Ziel keine Batchverarbeitung erfolgt, werden die impliziten Äquivalente der Aufgaben `CreateItem` oder `CreateProperty` mithilfe der Aufgabenbatchverarbeitung von Aufgaben als Batch verarbeitet. Das Ziel wird also nur einmal ausgeführt, und jedes Element oder jede Eigenschaft in der Gruppe wird separat mithilfe der Aufgabenbatchverarbeitung als Batch verarbeitet.

Die folgende Abbildung veranschaulicht die Zielbatchverarbeitung gegenüber der Aufgabenbatchverarbeitung für den Fall, dass die Metadaten verändert wurden. Stellen Sie sich eine Situation vor, in der Sie die Ordner A und B mit einigen Dateien haben:

```
A\1.stub
B\2.stub
B\3.stub
```

Sehen Sie sich nun die Ausgabe dieser beiden ähnlichen Projekte an.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build" Outputs="%(StubDirs.Identity)">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

Ausgabe:

```output
Test1:
  >> A\ 'A\' 'A'
Test1:
  >> B\ 'B\' 'B'
```

Entfernen Sie nun das Attribut `Outputs`, das die Zielbatchverarbeitung angegeben hat.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

Ausgabe:

```output
Test1:
  >> A\ 'B\' 'B'
  >> B\ 'B\' 'B'
```

Beachten Sie, dass die Überschrift `Test1` nur einmal ausgegeben wurde, im vorherigen Beispiel jedoch zweimal. Das bedeutet, dass für das Ziel keine Batchverarbeitung erfolgt.  Das führt dazu, dass die Ergebnisse verwirrend unterschiedlich ausfallen.

Der Grund dafür ist, dass bei der Verwendung der Zielbatchverarbeitung jedes Zielbatch alles im Ziel mit seiner eigenen unabhängigen Kopie aller Eigenschaften und Elemente ausführt. Wenn Sie jedoch das Attribut `Outputs` weglassen, werden die einzelnen Zeilen in der Eigenschaftsgruppe als unterschiedliche, potenzielle Batchaufgaben verarbeitet. In diesem Fall erfolgt für die Aufgabe `ComponentDir` eine Batchverarbeitung (mit der Syntax `%(ItemMetadataName)`). Dadurch wird bewirkt, dass zum Zeitpunkt, an dem die Zeile `ComponentName` ausgeführt wird, beide Batches der Zeile `ComponentDir` abgeschlossen sind und der zweite, der ausgeführt wurde, den Wert ermittelt hat, wie in der zweiten Zeile zu sehen ist.

## <a name="property-functions-using-metadata"></a>Eigenschaftenfunktionen mit Metadaten

Die Batchverarbeitung kann von den Eigenschaftenfunktionen kontrolliert werden, die Metadaten enthalten. Ein auf ein Objekt angewendeter

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

<xref:System.IO.Path.Combine%2A> wird verwendet, um den Stammpfad eines Ordners mit dem Elementpfad einer Kompilierung zu kombinieren.

Eigenschaftenfunktionen werden möglicherweise nicht innerhalb der Metadatenwerte angezeigt. Ein auf ein Objekt angewendeter

`%(Compile.FullPath.Substring(0,3))`

ist nicht zulässig.

Weitere Informationen zu Eigenschaftenfunktionen finden Sie unter [Eigenschaftenfunktionen](../msbuild/property-functions.md).

## <a name="see-also"></a>Siehe auch

- [ItemMetadata-Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)
