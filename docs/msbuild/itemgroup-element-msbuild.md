---
title: ItemGroup-Element (MSBuild) | Microsoft-Dokumentation
description: Erfahren Sie mehr über das ItemGroup-Element von MSBuild, das eine Reihe von benutzerdefinierten Item-Elementen enthält. Jedes Element muss ein untergeordnetes Element einer ItemGroup sein.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eff27467aeea5068f3ec086b490ca9c735861549
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913843"
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup-Element (MSBuild)

Enthält eine Reihe von benutzerdefinierten [Item](../msbuild/item-element-msbuild.md)-Elementen. Jedes Element, das in einem MSBuild-Projekt verwendet wird, muss als untergeordnetes Element eines `ItemGroup`-Elements angegeben werden.

\<Project>
\<ItemGroup>

## <a name="syntax"></a>Syntax

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Condition`|Optionales Attribut. Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|
|`Label`|Optionales Attribut. Identifiziert die `ItemGroup`. |

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Definiert die Eingaben für den Buildprozess. Es kann keine oder mehrere `Item`-Elemente in einer `ItemGroup` geben.|

### <a name="parent-elements"></a>Übergeordnete Elemente

| Element | Beschreibung |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Erforderliches Stammelement einer MSBuild-Projektdatei. |
| [Target](../msbuild/target-element-msbuild.md) | Ab.NET Framework 3.5 kann das `ItemGroup`-Element innerhalb eines `Target`-Elements angezeigt werden. Weitere Informationen finden Sie unter [Ziele](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel werden die benutzerdefinierten Elementsammlungen `Res` und `CodeFiles` gezeigt, die innerhalb eines `ItemGroup`-Element deklariert sind. Jedes der Elemente in der `Res`-Elementsammlung enthält ein benutzerdefiniertes untergeordnetes [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)-Element.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

In einer einfachen Projektdatei verwenden Sie normalerweise ein einzelnes `ItemGroup`-Element, Sie können aber auch mehrere `ItemGroup`-Elemente verwenden. Wenn mehrere `ItemGroup`-Elemente verwendet werden, werden Elemente in einer einzelnen `ItemGroup`kombiniert. Beispielsweise können einige Elemente in einem separaten `ItemGroup`-Element enthalten sein, das in einer importierten Datei definiert wird.

Auf ItemGroups können Bedingungen mithilfe des `Condition`-Attributs angewendet werden. In diesem Fall werden die Elemente der Elementliste nur dann hinzugefügt, wenn die Bedingung erfüllt ist. Weitere Informationen finden Sie unter [MSBuild-Bedingungen](msbuild-conditions.md).

Das Attribut `Label` wird in einigen Buildsystemen als Möglichkeit zur Steuerung des Buildverhaltens verwendet. Sie können es nur in Deklarationen als eine Möglichkeit nutzen, um verständlichere MSBuild-Skripts zu erstellen, oder als eine Steuerungseinstellung, um Buildaktionen zu beeinflussen.

## <a name="see-also"></a>Siehe auch

- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
- [Elemente](../msbuild/msbuild-items.md)
- [Gemeinsame MSBuild-Projektelemente](../msbuild/common-msbuild-project-items.md)
