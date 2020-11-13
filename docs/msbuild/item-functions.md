---
title: Elementfunktionen | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild-Code in Aufgaben und Zielen Elementfunktionen aufrufen kann, um Informationen zu den Elementen des Projekts zu erhalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94b94ef7b17633ab78f7eb91f61dd67ea2c8021d
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904626"
---
# <a name="item-functions"></a>Elementfunktionen

Code in Aufgaben und Zielen kann Elementfunktionen aufrufen, um Informationen zu den Elementen im Projekt zu erhalten (MSBuild 4.0 und höher). Diese Funktionen vereinfachen das Abrufen von distinct-Elementen, und mit ihnen erfolgt der Abruf schneller als beim Durchlaufen der Elemente.

## <a name="string-item-functions"></a>Zeichenfolgenelementfunktionen

Sie können Zeichenfolgenmethoden und -eigenschaften in .NET Framework für jeden Elementwert verwenden. Geben Sie für <xref:System.String>-Methoden den Methodennamen an. Geben Sie für <xref:System.String>-Eigenschaften den Eigenschaftennamen hinter „get_“ an.

Für Elemente mit mehreren Zeichenfolgen wird die Zeichenfolgenmethode oder -eigenschaft für jede Zeichenfolge ausgeführt.

Das folgende Beispiel veranschaulicht die Verwendung dieser Zeichenfolgenelementfunktionen.

```xml
<ItemGroup>
    <theItem Include="andromeda;tadpole;cartwheel" />
</ItemGroup>

<Target Name = "go">
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />
    <Message Text="Length   @(theItem->get_Length())" />
    <Message Text="Chars    @(theItem->get_Chars(2))" />
</Target>

  <!--
  Output:
    IndexOf  3;-1;2
    Replace  andromeda;pinwheel;cartwheel
    Length   9;7;9
    Chars    d;d;r
  -->
```

## <a name="intrinsic-item-functions"></a>Intrinsische Elementfunktionen

In der unten stehenden Tabelle werden die systeminternen Funktionen aufgelistet, die für Elemente zur Verfügung stehen.

|Funktion|Beispiel|Beschreibung|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Gibt die Anzahl der Elemente zurück|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Gibt das entsprechende `Path.DirectoryName`-Objekt für jedes Element zurück|
|`Distinct`|`@(MyItem->Distinct())`|Gibt Elemente zurück, die eindeutige `Include`-Werte aufweisen Metadaten werden ignoriert. Beim Vergleich wird die Groß- und Kleinschreibung nicht berücksichtigt.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Gibt Elemente zurück, die eindeutige `itemspec`-Werte aufweisen Metadaten werden ignoriert. Beim Vergleich wird die Groß- und Kleinschreibung berücksichtigt.|
|`Reverse`|`@(MyItem->Reverse())`|Gibt die Elemente in umgekehrter Reihenfolge zurück|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Gibt einen `boolean`-Wert zurück, der angibt, ob ein Element einen angegebenen Metadatennamen und -wert aufweist. Beim Vergleich wird die Groß- und Kleinschreibung nicht berücksichtigt.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Gibt Elemente mit gelöschten Metadaten zurück. Nur das `itemspec`-Objekt wird beibehalten.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Gibt Elemente zurück, die den angegebenen Metadatennamen aufweisen Beim Vergleich wird die Groß- und Kleinschreibung nicht berücksichtigt.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Gibt die Werte der Metadaten zurück, die den Metadatennamen aufweisen|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Gibt Elemente zurück, die den angegebenen Metadatennamen und -wert aufweisen. Beim Vergleich wird die Groß- und Kleinschreibung nicht berücksichtigt.|

In folgendem Beispiel wird veranschaulicht, wie Sie systeminterne Elementfunktionen verwenden können.

```xml
<ItemGroup>
    <TheItem Include="first">
        <Plant>geranium</Plant>
    </TheItem>
    <TheItem Include="second">
        <Plant>algae</Plant>
    </TheItem>
    <TheItem Include="third">
        <Plant>geranium</Plant>
    </TheItem>
</ItemGroup>

<Target Name="go">
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />
    <Message Text=" " />
    <Message Text="Count:   @(theItem->Count())" />
    <Message Text="Reverse: @(theItem->Reverse())" />
</Target>

  <!--
  Output:
    MetaData:    geranium;algae;geranium
    HasMetadata: first;second;third
    WithMetadataValue: first;third

    Count:   3
    Reverse: third;second;first
  -->
```

## <a name="msbuild-condition-functions"></a>MSBuild-Bedingungsfunktionen

Die Funktionen `Exists` und `HasTrailingSlash` sind keine Elementfunktionen. Sie können mit dem `Condition`-Attribut verwendet werden. Weitere Informationen finden Sie unter [MSBuild-Bedingungen](msbuild-conditions.md).

## <a name="see-also"></a>Siehe auch

- [Elemente](../msbuild/msbuild-items.md)
