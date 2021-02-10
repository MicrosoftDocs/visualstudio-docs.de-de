---
title: Vergleich von Eigenschaften und Elementen | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild-Eigenschaften und -Elemente Informationen an Aufgaben übergeben, Bedingungen auswerten und Werte speichern, auf die von der Projektdatei verwiesen werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 226b86d621de2faee5a71d9fdb3fea39f20b984e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888120"
---
# <a name="compare-properties-and-items"></a>Vergleich von Eigenschaften und Elementen

Sowohl MSBuild-Eigenschaften als auch MSBuild-Elemente werden verwendet, um Informationen an Aufgaben zu übergeben, Bedingungen auszuwerten und Werte zu speichern, auf die in der gesamten Projektdatei verwiesen werden kann.

- Eigenschaften sind Name/Wert-Paare. Weitere Informationen finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

- Elemente sind Objekte, die in der Regel Dateien darstellen. Elementobjekten können Metadatensammlungen zugeordnet sein. Metadaten sind Name/Wert-Paare. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

## <a name="scalars-and-vectors"></a>Skalare und Vektoren

Da MSBuild-Eigenschaften Name/Wert-Paare sind, die nur einen Zeichenfolgenwert aufweisen, werden sie häufig als *Skalar* bezeichnet. Da MSBuild-Elementtypen Listen von Elementen sind, werden sie häufig als *Vektor* bezeichnet. In der Praxis können Eigenschaften jedoch mehrere Werte darstellen, und Elementtypen können null oder ein Element aufweisen.

### <a name="target-dependency-injection"></a>Zielabhängigkeitsinjektion

Um zu verstehen, wie Eigenschaften mehrere Werte darstellen können, können Sie sich ein häufiges Verwendungsmuster für das Hinzufügen eines Ziels zu einer zu erstellenden Liste von Zielen vorstellen. Diese Liste wird in der Regel durch einen Eigenschaftswert dargestellt, wobei die Zielnamen durch Semikolons getrennt sind.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Die `BuildDependsOn`-Eigenschaft wird normalerweise als Argument eines Ziel-`DependsOnTargets`-Attributs verwendet, wodurch sie effektiv in eine Elementliste konvertiert wird. Diese Eigenschaft kann überschrieben werden, um ein Ziel hinzuzufügen oder die Ausführungsreihenfolge der Ziele zu ändern. Ein auf ein Objekt angewendeter

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

Der obige Code fügt das Ziel CustomBuild zur Zielliste hinzu, wodurch `BuildDependsOn` den Wert `BeforeBuild;CoreBuild;AfterBuild;CustomBuild` erhält.

Ab MSBuild 4.0 ist die Zielabhängigkeitsinjektion veraltet. Verwenden Sie stattdessen die Attribute `AfterTargets` und `BeforeTargets`. Weitere Informationen finden Sie unter [Buildreihenfolge für Ziele](../msbuild/target-build-order.md).

### <a name="conversions-between-strings-and-item-lists"></a>Konvertierungen zwischen Zeichenfolgen und Elementlisten

MSBuild führt nach Bedarf Konvertierungen von und nach Elementtypen und Zeichenfolgenwerten durch. Um zu verstehen, wie eine Elementliste zu einem Zeichenfolgenwert werden kann, können Sie sich vorstellen, was geschieht, wenn ein Elementtyp als Wert einer MSBuild-Eigenschaft verwendet wird:

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

Der Elementtyp OutputDir hat ein `Include`-Attribut mit dem Wert „KeyFiles\\;Certificates\\“. MSBuild analysiert diese Zeichenfolge, und es resultieren die beiden Elemente KeyFiles\ und Certificates\\. Wenn der Elementtyp OutputDir als Wert der Eigenschaft OutputDirList verwendet wird, konvertiert („vereinfacht“) MSBuild den Elementtyp in die durch Semikolons getrennte Zeichenfolge „KeyFiles\\;Certificates\\“.

## <a name="properties-and-items-in-tasks"></a>Eigenschaften und Elemente in Aufgaben

Eigenschaften und Elemente werden als Ein- und Ausgaben für MSBuild-Aufgaben verwendet. Weitere Informationen finden Sie unter [MSBuild-Aufgaben](../msbuild/msbuild-tasks.md).

Eigenschaften werden als Attribute an Aufgaben übergeben. Innerhalb der Aufgabe wird eine MSBuild-Eigenschaft durch einen Eigenschaftentyp dargestellt, dessen Wert in und aus einer Zeichenfolge konvertiert werden kann. Die unterstützten Eigenschaftentypen umfassen `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string` und alle Typen, die <xref:System.Convert.ChangeType%2A> verarbeiten kann.

Elemente werden als <xref:Microsoft.Build.Framework.ITaskItem>-Objekte an Aufgaben übergeben. In der Aufgabe stellt <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> den Wert des Elements dar, und <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> ruft dessen Metadaten ab.

Die Elementliste eines Elementtyps kann als Array von `ITaskItem`-Objekten übergeben werden. Ab .NET Framework 3.5 können Elemente mithilfe des `Remove`-Attributs aus einer Elementliste in einem Ziel entfernt werden. Da Elemente aus einer Elementliste entfernt werden können, kann ein Elementtyp über 0 (null) Elemente verfügen. Wenn eine Elementliste an eine Aufgabe übergeben wird, muss der Code in der Aufgabe diese Möglichkeit überprüfen.

## <a name="property-and-item-evaluation-order"></a>Auswertungsreihenfolge von Eigenschaften und Elementen

Während der Auswertungsphase eines Builds werden importierte Dateien in der Reihenfolge in den Build integriert, in der sie vorkommen. Eigenschaften und Elemente werden in drei Durchläufen in der folgenden Reihenfolge definiert:

- Eigenschaften werden in der Reihenfolge definiert und geändert, in der sie vorkommen.

- Elementdefinitionen werden in der Reihenfolge definiert und geändert, in der sie vorkommen.

- Elemente werden in der Reihenfolge definiert und geändert, in der sie vorkommen.

Während der Ausführungsphase eines Builds werden in Zielen definierte Eigenschaften und Elemente gemeinsam in einer einzigen Phase in der Reihenfolge ausgewertet, in der sie vorkommen.

Das stimmt allerdings nicht ganz. Wenn eine Eigenschaft, eine Elementdefinition oder ein Element definiert ist, wird der zugehörige Wert ausgewertet. Der Ausdrucksauswerter erweitert die Zeichenfolge, die den Wert angibt. Die Erweiterung der Zeichenfolge ist von der Build-Phase abhängig. Unten sehen Sie eine detailliertere Auswertungsreihenfolge für Eigenschaften und Elemente:

- Während der Auswertungsphase eines Builds:

  - Eigenschaften werden in der Reihenfolge definiert und geändert, in der sie vorkommen. Eigenschaftenfunktionen werden ausgeführt. Eigenschaftswerte der Form $(PropertyName) werden in Ausdrücken erweitert. Der Eigenschaftswert wird auf den erweiterten Ausdruck gesetzt.

  - Elementdefinitionen werden in der Reihenfolge definiert und geändert, in der sie vorkommen. Eigenschaftenfunktionen wurden bereits in Ausdrücken erweitert. Metadatenwerte werden auf die erweiterten Ausdrücke gesetzt.

  - Elementtypen werden in der Reihenfolge definiert und geändert, in der sie vorkommen. Elementwerte in der Form @(Elementtyp) werden erweitert. Elementtransformationen werden ebenfalls erweitert. Eigenschaftenfunktionen und -werte wurden bereits in Ausdrücken erweitert. Die Elementliste und die Metadatenwerte werden auf die erweiterten Ausdrücke gesetzt.

- Während der Auswertungsphase eines Builds:

  - Eigenschaften und Elemente, die in Zielen definiert sind, werden zusammen in der Reihenfolge ausgewertet, in der sie vorkommen. Eigenschaftenfunktionen werden ausgeführt, und Eigenschaftswerte werden in Ausdrücken erweitert. Elementwerte und Elementtransformationen werden ebenfalls erweitert. Die Eigenschaftswerte, Elementtypwerte und Metadatenwerte werden auf die erweiterten Ausdrücke gesetzt.

### <a name="subtle-effects-of-the-evaluation-order"></a>Geringfügige Auswirkungen der Auswertungsreihenfolge

In der Auswertungsphase eines Builds erfolgt die Auswertung von Eigenschaften vor der Auswertung von Elementen. Trotzdem können Eigenschaften Werte besitzen, die scheinbar von Elementwerten abhängen. Betrachten Sie folgendes Skript.

```xml
<ItemGroup>
    <KeyFile Include="KeyFile.cs">
        <Version>1.0.0.3</Version>
    </KeyFile>
</ItemGroup>
<PropertyGroup>
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
</PropertyGroup>
<Target Name="AfterBuild">
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Beim Ausführen der Meldungsaufgabe wird folgende Meldung angezeigt:

```
KeyFileVersion: 1.0.0.3
```

Dies liegt daran, dass der Wert von `KeyFileVersion` eigentlich die Zeichenfolge „\@(Schlüsseldatei->'%(Version)')“ ist. Element und Elementtransformationen wurden nicht erweitert, als die Eigenschaft ursprünglich definiert wurde, sodass der `KeyFileVersion`-Eigenschaft der Wert der nicht erweiterten Zeichenfolge zugewiesen wurde.

Wenn während der Ausführungsphase des Builds die Meldungsaufgabe verarbeitet wird, erweitert MSBuild die Zeichenfolge „\@(Schlüsseldatei->'%(Version)')“, sodass sie „1.0.0.3“ ergibt.

Beachten Sie, dass dieselbe Meldung auch dann angezeigt würde, wenn die Reihenfolge der Eigenschaften- und Elementgruppen umgekehrt würde.

Im zweiten Beispiel sollten Sie beachten, was passieren kann, wenn sich die Eigenschaften- und Elementgruppen innerhalb von Zielen befinden:

```xml
<Target Name="AfterBuild">
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Die Meldungsaufgabe zeigt folgende Meldung an:

```
KeyFileVersion:
```

Dies liegt daran, dass während der Ausführungsphase des Builds innerhalb von Zielen definierte Eigenschaften- und Elementgruppen gleichzeitig von oben nach unten ausgewertet werden. Wenn `KeyFileVersion` definiert ist, ist `KeyFile` unbekannt. Daher wird die Elementtransformation auf eine leere Zeichenfolge erweitert.

In diesem Fall wird beim Umkehren der Reihenfolge der Eigenschaften- und Elementgruppen die ursprüngliche Meldung wiederhergestellt:

```xml
<Target Name="AfterBuild">
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Der Wert von `KeyFileVersion` wird auf „1.0.0.3“ und nicht auf „\@(Schlüsseldatei->'%(Version)')“ gesetzt. Die Meldungsaufgabe zeigt folgende Meldung an:

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>Siehe auch

- [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)
