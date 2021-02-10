---
title: Elementdefinitionen | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild ItemGroup und ItemDefinitionGroup verwendet, um Metadaten für Elemente in Projektdateien zu deklarieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 754080defd50bc10af501fdbaf509bafe549dcbd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913968"
---
# <a name="item-definitions"></a>Elementdefinitionen

MSBuild 2.0 aktiviert die statische Deklaration von Elementen in Projektdateien mithilfe des Elements [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Metadaten können jedoch nur auf Elementebene hinzugefügt werden, auch wenn die Metadaten für alle Elemente gleich sind. In MSBuild 3.5 wurde das Projektelement [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) eingeführt, das diese Einschränkung aufhebt. Mit *ItemDefinitionGroup* können Sie einen Satz von Elementdefinitionen festlegen, um allen Elementen im benannten Elementtyp Standardwerte für Metadaten hinzuzufügen.

Das *ItemDefinitionGroup*-Element wird unmittelbar nach dem [Project](../msbuild/project-element-msbuild.md)-Element der Projektdatei angezeigt. Elementdefinitionen bieten die folgenden Funktionen:

- Sie können globale Standardmetadaten für Elemente außerhalb eines Ziels definieren. Das heißt, für alle Elemente des angegebenen Typs gelten die gleichen Metadaten.

- Elementtypen können mehrere Definitionen aufweisen. Wenn dem Typ weitere Metadatenspezifikationen hinzugefügt werden, hat die letzte Spezifikation Vorrang. \(Die Metadaten folgen der gleichen Importreihenfolge wie Eigenschaften.\)

- Metadaten können additiv sein. Zum Beispiel werden CDefines-Werte bedingt akkumuliert, abhängig von den festgelegten Eigenschaften. Beispielsweise `MT;STD_CALL;DEBUG;UNICODE`.

- Metadaten können entfernt werden.

- Bedingungen können verwendet werden, um das Einschließen der Metadaten zu steuern.

## <a name="item-metadata-default-values"></a>Standardwerte von Elementmetadaten

Elementmetadaten, die in ItemDefinitionGroup definiert werden, sind nur eine Deklaration der Standardmetadaten. Die Metadaten finden nur dann Anwendung, wenn Sie ein Element definieren, das zum Einschließen der Metadatenwerte ItemGroup verwendet.

> [!NOTE]
> In mehreren Beispielen in diesem Thema wird ein ItemDefinitionGroup-Element angezeigt, wobei die entsprechende ItemGroup-Definition aus Gründen der Übersichtlichkeit weggelassen wird.

Explizit in einem ItemGroup-Element definierte Metadaten haben Vorrang vor Metadaten in einem ItemDefinitionGroup-Element. Metadaten in einem ItemDefinitionGroup-Element werden nur auf nicht definierte Metadaten in einem ItemGroup-Element angewendet. Zum Beispiel:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemGroup>
    <i Include="a">
        <o>o1</o>
        <n>n2</n>
    </i>
</ItemGroup>
```

In diesem Beispiel wird das Standardmetadatum "m" auf das Element "i" angewendet, da das Metadatum "m" nicht explizit durch das Element "i" definiert wird. Das Standardmetadatum "n" wird jedoch nicht auf das Element "i" angewendet, da das Metadatum "n" bereits durch Element "i" definiert ist.

> [!NOTE]
> Bei XML-Elementen und XML-Parameternamen muss die Groß\-/Kleinschreibung beachtet werden. Bei Elementmetadaten und Element\//Eigenschaftennamen muss die Groß\-/Kleinschreibung nicht beachtet werden. Daher sollten ItemDefinitionGroup-Elemente, deren Namen sich nur durch die Groß-/Kleinschreibung unterscheiden, als gleiches ItemGroup behandelt werden.

## <a name="value-sources"></a>Wertquellen

Die Werte der in ItemDefinitionGroup definierten Metadaten können aus verschiedenen Quellen stammen:

- PropertyGroup-Eigenschaft

- Element aus ItemDefinitionGroup

- Elementtransformation für ein ItemDefinitionGroup-Element

- Umgebungsvariable

- Globale Eigenschaft (aus der *MSBuild.exe*-Befehlszeile)

- Reservierte Eigenschaft

- Bekannte Metadaten über ein Element aus ItemDefinitionGroup

- CDATA-Abschnitt \<\!\[CDATA\[anything here is not parsed\]\]\>

> [!NOTE]
> Elementmetadaten aus ItemGroup sind in einer ItemDefinitionGroup-Metadatendeklaration nicht nützlich, da ItemDefinitionGroup-Elemente vor ItemGroup-Elementen verarbeitet werden.

## <a name="additive-and-multiple-definitions"></a>Additive und mehrfache Definitionen

Wenn Sie Definitionen hinzufügen oder mehrere ItemDefinitionGroups verwenden, beachten Sie Folgendes:

- Dem Typ werden zusätzliche Metadatenspezifikationen hinzugefügt.

- Die letzte Spezifikation hat Vorrang.

Wenn Sie über mehrere ItemDefinitionGroups verfügen, werden die Metadaten jeder folgenden Spezifikation der vorhergehenden Definition hinzugefügt. Zum Beispiel:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <o>o1</o>
    </i>
</ItemDefinitionGroup>
```

In diesem Beispiel werden die Metadaten"o" zu "m" und "n" hinzugefügt.

Darüber hinaus können auch bereits definierte Metadatenwerte hinzugefügt werden. Zum Beispiel:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

In diesem Beispiel wird der bereits definierte Wert für die Metadaten „m“ \(m1\) dem neuen Wert \(m2\) hinzugefügt, sodass der Endwert „m1;m2“ lautet.

> [!NOTE]
> Dies kann auch im gleichen ItemDefinitionGroup auftreten.

Wenn Sie die bereits definierten Metadaten überschreiben, hat die letzte Spezifikation Vorrang. Im folgenden Beispiel ändert sich der endgültige Wert der Metadaten "m" von "m1" in "m1a".

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>m1a</m>
    </i>
</ItemDefinitionGroup>
```

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Verwenden von Bedingungen in ItemDefinitionGroup

Sie können Bedingungen in ItemDefinitionGroup verwenden, um das Einschließen von Metadaten zu steuern. Zum Beispiel:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

In diesem Fall werden die Standardmetadaten "m1" für Element "i" nur dann eingeschlossen, wenn der Wert der "Configuration"-Eigenschaft "Debug" lautet.

> [!NOTE]
> In Bedingungen werden nur lokale Metadatenverweise unterstützt.

Verweise auf Metadaten, die in einem früheren ItemDefinitionGroup definiert sind, sind für das Element lokal, nicht für die Definitionsgruppe. Das heißt, der Umfang der Verweise ist elementspezifisch. Zum Beispiel:

```xml
<ItemDefinitionGroup>
    <test>
        <yes>1</yes>
    </test>
    <i>
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>
    </i>
</ItemDefinitionGroup>

```

Im obigen Beispiel verweist Element „i“ auf das Element „test“ in seiner Bedingung. Diese Bedingung wird niemals „true“ ergeben, da MSBuild einen Verweis auf die Metadaten eines anderen Elements in einer ItemDefinitionGroup als leere Zeichenfolge interpretiert. Aus diesem Grund würde „m“ auf „m0“ festgelegt.

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

Im Beispiel oben würde für „m“ der Wert „m1“ festgelegt, da die Bedingung auf den Metadatenwert des Elements „i“ für Element „yes“ verweist.

## <a name="override-and-delete-metadata"></a>Außerkraftsetzen und Löschen von Metadaten

In einem ItemDefinitionGroup-Element definierte Metadaten können in einem späteren ItemDefinitionGroup-Element überschrieben werden, indem der Metadatenwert auf einen anderen Wert festgelegt wird. Sie können ein Metadatenelement auch löschen, indem Sie es auf einen leeren Wert festlegen. Zum Beispiel:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m></m>
    </i>
</ItemDefinitionGroup>
```

Das Element "i" enthält immer noch die Metadaten "m", sein Wert ist jetzt jedoch leer.

## <a name="scope-of-metadata"></a>Umfang der Metadaten

ItemDefinitionGroup weist einen globalen Gültigkeitsbereich für definierte und globale Eigenschaften auf, unabhängig davon, wo sie definiert sind. Standardmäßige Metadatendefinitionen in ItemDefinitionGroup können auf sich selbst verweisen. Nachfolgend wird beispielsweise ein einfacher Metadatenverweis verwendet:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Es kann auch ein qualifizierter Metadatenverweis verwendet werden:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Folgendes ist jedoch nicht gültig:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

Ab MSBuild 3.5 kann ItemGroup auch auf sich selbst verweisen. Zum Beispiel:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Siehe auch

- [Batchverarbeitung](../msbuild/msbuild-batching.md)
