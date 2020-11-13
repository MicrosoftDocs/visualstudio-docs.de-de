---
title: MSBuild-Elemente | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das Include-Attribut der ItemGroup von MSBuild verwenden, um Dateien anzugeben, die in einem Build enthalten sein sollen.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a28823a1a492cb1e8d5f434f98248fecc5d84e47
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904504"
---
# <a name="msbuild-items"></a>MSBuild-Elemente

MSBuild-Elemente sind Eingaben in das Buildsystem. In der Regel handelt es sich dabei um Dateien (die Dateien sind im `Include`-Attribut angegeben). Elemente werden auf Grundlage benutzerdefinierter Elementnamen in Elementtypen gruppiert. Elementtypen sind benannte Listen von Elementen, die als Parameter für Aufgaben verwendet werden können. In den Aufgaben werden die Schritte des Buildprozesses mithilfe der Elementwerte ausgeführt.

 Da Elemente anhand des Elementtyps benannt werden, zu dem sie gehören, können die Begriffe „Element“ und „Elementwert“ synonym verwendet werden.

## <a name="create-items-in-a-project-file"></a>Erstellen von Elementen in einer Projektdatei

 Elemente werden in der Projektdatei als untergeordnete Elemente eines [ItemGroup](../msbuild/itemgroup-element-msbuild.md)-Elements deklariert. Der Name des untergeordneten Elements ist der Typ des Elements. Durch das `Include`-Attribut des Elements wird angegeben, welche Elemente (Dateien) in den jeweiligen Elementtyp aufgenommen werden sollen. Im folgenden XML wird z.B. der mit `Compile` benannte Elementtyp erstellt, der zwei Dateien umfasst.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Das Element *file2.cs* ersetzt das Element *file1.cs* nicht. Stattdessen wird der Dateiname an die Liste der Werte für den `Compile`-Elementtyp angefügt.

 Das folgende XML erstellt den gleichen Elementtyp, indem beide Dateien in einem `Include`-Attribut deklariert werden. Achten Sie darauf, dass die Dateinamen durch ein Semikolon voneinander getrennt sind.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

Das `Include`-Attribut ist ein Pfad, der relativ zum Ordner der Projektdatei „$(MSBuildProjectPath)“ interpretiert wird. Dies gilt auch dann, wenn sich das Element in einer importierten Datei, wie etwa einer *TARGETS* -Datei, befindet.

## <a name="create-items-during-execution"></a>Erstellen von Elementen während der Ausführung

 Elementen außerhalb von [Ziel](../msbuild/target-element-msbuild.md)-Elementen werden während der Auswertungsphase eines Builds Werte zugewiesen. Während der anschließenden Ausführungsphase können Elemente wie folgt erstellt oder geändert werden:

- Jede Aufgabe kann ein Element ausgeben. Das [Aufgabe](../msbuild/task-element-msbuild.md)-Element muss über ein untergeordnetes [Ausgabe](../msbuild/output-element-msbuild.md)-Element mit einem `ItemName`-Attribut verfügen, damit ein Element ausgegeben werden kann.

- Die [CreateItem](../msbuild/createitem-task.md)-Aufgabe kann ein Element ausgeben. Diese Verwendung ist veraltet.

- Ab .NET Framework 3.5 enthalten `Target`-Elemente möglicherweise [ItemGroup](../msbuild/itemgroup-element-msbuild.md)-Elemente, die Item-Elemente enthalten.

## <a name="reference-items-in-a-project-file"></a>Verweisen auf Elemente in einer Projektdatei

 Verwenden Sie die Syntax @(\<ItemType>), um auf Elementtypen in der gesamten Projektdatei zu verweisen. Auf den Elementtyp aus dem vorherigen Beispiel würden Sie z.B. mithilfe von `@(Compile)` verweisen. Mithilfe dieser Syntax können Sie Elemente an Aufgaben übergeben, indem Sie den Elementtyp als einen Parameter dieser Aufgabe angeben. Weitere Informationen finden Sie unter [Vorgehensweise: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md).

 Standardmäßig sind die Elemente eines Elementtyps durch Semikolons (;) getrennt, wenn er erweitert wird. Sie können die Syntax @(\<ItemType>, '\<separator>') verwenden, um ein anderes Trennzeichen als das Standardtrennzeichen anzugeben. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen einer durch Trennzeichen getrennten Elementliste](../msbuild/how-to-display-an-item-list-separated-with-commas.md).

## <a name="use-wildcards-to-specify-items"></a>Verwenden von Platzhaltern zum Angeben von Elementen

Sie können die Platzhalterzeichen `**`, `*` und `?` verwenden, um eine Gruppe von Dateien als Eingaben für einen Build anzugeben. So müssen Sie nicht alle Dateien separat auflisten.

- Das Platzhalterzeichen `?` entspricht einem einzelnen Zeichen.
- Das Platzhalterzeichen `*` entspricht 0 (null) oder mehr Zeichen.
- Die Platzhalterzeichenfolge `**` entspricht einem partiellen Pfad.

Sie können z.B. alle `.cs`-Dateien im Verzeichnis der Projektdatei angeben, indem Sie das folgende Element in der Projektdatei verwenden.

```xml
<CSFile Include="*.cs"/>
```

Das folgende Element wählt alle `.vb`-Dateien auf Laufwerk `D:` aus:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Wenn Sie literale Zeichen `*` oder `?` in ein Element ohne Platzhaltererweiterung aufnehmen möchten, müssen Sie [die Platzhalterzeichen mit Escapezeichen versehen](../msbuild/how-to-escape-special-characters-in-msbuild.md).

Weitere Informationen zu Platzhalterzeichen finden Sie unter [Vorgehensweise: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md).

## <a name="use-the-exclude-attribute"></a>Verwenden des Exclude-Attributs

 Item-Elemente können das `Exclude`-Attribut enthalten, das bestimmte Elemente (Dateien) aus dem Elementtyp ausschließt. Das `Exclude`-Attribut wird normalerweise zusammen mit Platzhalterzeichen verwendet. Der folgende XML-Code fügt z.B. dem CSFile-Elementtyp alle *CS* -Dateien außer *DoNotBuild.cs* hinzu, die sich im Verzeichnis befinden.

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 Das `Exclude`-Attribut wirkt sich nur auf Elemente aus, die über das `Include`-Attribut in dem Item-Element hinzugefügt wurden, das beide enthält. Im folgenden Beispiel würde die im vorherigen Item-Element hinzugefügte Datei *Form1.cs* also nicht ausgeschlossen werden.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Weitere Informationen finden Sie unter [Vorgehensweise: Ausschließen von Dateien aus dem Buildvorgang](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Elementmetadaten

 Zusätzlich zu den Informationen aus den Attributen `Include` und `Exclude` können Elemente Metadaten enthalten. Diese Metadaten können von Aufgaben verwendet werden, die weitere Informationen zu den Elementen oder zur Batchverarbeitung von Aufgaben und Zielen benötigen. Weitere Informationen finden Sie unter [MSBuild Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md).

 Bei Metadaten handelt es sich um eine Auflistung von Schlüssel-Wert-Paaren, die in der Projektdatei als untergeordnete Elemente eines Item-Elements deklariert sind. Der Name des untergeordneten Elements entspricht dem Metadatennamen, und der Wert des untergeordneten Elements entspricht dem Metadatenwert.

 Die Metadaten sind dem Item-Element zugeordnet, in dem sie enthalten sind. Der folgende XML-Code fügt z.B. den Elementen *one.cs* und *two.cs* des CSFile-Elementtyps `Culture`-Metadaten mit dem Wert `Fr` hinzu.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Ein Element kann über 0 (null) oder mehr Metadatenwerte verfügen. Metadaten lassen sich immer ändern. Wenn Sie Metadaten auf einen leeren Wert festlegen, entfernen Sie sie unwiderruflich aus dem Build.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Verweisen auf Elementmetadaten in einer Projektdatei

 Mithilfe der Syntax %(\<ItemMetadataName>) kann in der gesamten Projektdatei auf Elementmetadaten verwiesen werden. Bei Mehrdeutigkeiten können Sie mit dem Namen des Elementtyps einen Verweis qualifizieren. Sie können z. B. %(\<ItemType.ItemMetaDataName>) angeben. Im folgenden Beispiel erfolgt die Batchverarbeitung des Nachrichtentasks mithilfe der Anzeigemetadaten. Weitere Informationen zur Verwendung von Elementmetadaten für die Batchverarbeitung finden Sie unter [Item Metadata in Task Batching (Elementmetadaten bei der Batchverarbeitung von Aufgaben)](../msbuild/item-metadata-in-task-batching.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Stuff Include="One.cs" >
            <Display>false</Display>
        </Stuff>
        <Stuff Include="Two.cs">
            <Display>true</Display>
        </Stuff>
    </ItemGroup>
    <Target Name="Batching">
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>
    </Target>
</Project>
```

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Bekannte Elementmetadaten

 Wenn einem Elementtypen ein Element hinzugefügt wird, werden diesem Element bekannte Metadaten zugewiesen. So verfügen z. B. alle Elemente über die bekannten Metadaten %(\<Filename>), deren Wert dem Dateinamen des Elements entspricht (ohne Erweiterung). Weitere Informationen finden Sie unter [Well-known Item Metadata (Bekannte Elementmetadaten)](../msbuild/msbuild-well-known-item-metadata.md).

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Umwandeln von Elementtypen mithilfe von Metadaten

 Elementlisten können mithilfe von Metadaten in neue Elementlisten umgewandelt werden. Sie können z.B. mit dem Ausdruck `@(CppFiles -> '%(Filename).obj')` einen `CppFiles`-Elementtyp, der über Elemente in Form von *CPP* -Dateien verfügt, in eine entsprechende Liste von *OBJ* -Dateien umwandeln.

 Der folgende Code erstellt einen `CultureResource`-Elementtyp, der Kopien aller `EmbeddedResource`-Elemente mit `Culture`-Metadaten enthält. Der `Culture`-Metadatenwert ist nun der Wert der neuen Metadaten `CultureResource.TargetDirectory`.

```xml
<Target Name="ProcessCultureResources">
    <ItemGroup>
        <CultureResource Include="@(EmbeddedResource)"
            Condition="'%(EmbeddedResource.Culture)' != ''">
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>
        </CultureResource>
    </ItemGroup>
</Target>
```

 Weitere Informationen finden Sie unter [Transformationen](../msbuild/msbuild-transforms.md).

## <a name="item-definitions"></a>Elementdefinitionen

 Ab .NET Framework 3.5 können Sie jedem Elementtypen mit dem [ItemDefinitionGroup-Element](../msbuild/itemdefinitiongroup-element-msbuild.md) Standardmetadaten hinzufügen. Standardmetadaten sind genau wie bekannte Metadaten allen Elementen des jeweils angegebenen Elementtyps zugeordnet. Standardmetadaten können in einer Elementdefinition explizit überschrieben werden. Der folgende XML-Code vergibt z.B. an die `Compile`-Elemente *one.cs* und *three.cs* die Metadaten `BuildDay` mit dem Wert „Monday“. Der Code vergibt an das Element *two.cs* die Metadaten `BuildDay` mit dem Wert „Tuesday“.

```xml
<ItemDefinitionGroup>
    <Compile>
        <BuildDay>Monday</BuildDay>
    </Compile>
</ItemDefinitionGroup>
<ItemGroup>
    <Compile Include="one.cs;three.cs" />
    <Compile Include="two.cs">
        <BuildDay>Tuesday</BuildDay>
    </Compile>
</ItemGroup>
```

 Weitere Informationen finden Sie unter [Item Definitions (Elementdefinitionen)](../msbuild/item-definitions.md).

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Attribute für Elemente im ItemGroup-Element eines Ziels

 Ab .NET Framework 3.5 enthalten `Target`-Elemente möglicherweise [ItemGroup](../msbuild/itemgroup-element-msbuild.md)-Elemente, die Item-Elemente enthalten. Die Attribute in diesem Abschnitt sind gültig, wenn sie für ein Element in einem `ItemGroup` angegeben werden, das ein `Target` ist.

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Entfernen des Attributs

 Das `Remove`-Attribut entfernt bestimmte Elemente (Dateien) aus dem Elementtyp. Dieses Attribut wurde in .NET Framework 3.5 eingeführt (nur von Zielen innerhalb). Sowohl die Ziele innerhalb als auch außerhalb werden ab MSBuild 15.0 unterstützt.

 Das folgende Beispiel veranschaulicht das Entfernen aller *CONFIG* -Dateien aus dem Compile-Elementtyp.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a>KeepMetadata-Attribut

 Wenn ein Element in einem Ziel erstellt wird, enthält das Item-Element möglicherweise das `KeepMetadata`-Attribut. Wenn dieses Attribut angegeben wird, werden nur die Metadaten aus dem Quellelement in das Zielelement übertragen, die in der durch Semikolons getrennten Liste von Namen angegeben sind. Wird für dieses Attribut ein leerer Wert angegeben, ist dies, als wäre nichts angegeben worden. Das `KeepMetadata`-Attribut wurde in .NET Framework 4.5 eingeführt.

 Das folgende Beispiel veranschaulicht, wie das `KeepMetadata`-Attribut verwendet wird.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0">

    <ItemGroup>
        <FirstItem Include="rhinoceros">
            <Class>mammal</Class>
            <Size>large</Size>
        </FirstItem>

    </ItemGroup>
    <Target Name="MyTarget">
        <ItemGroup>
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />
        </ItemGroup>

        <Message Text="FirstItem: %(FirstItem.Identity)" />
        <Message Text="  Class: %(FirstItem.Class)" />
        <Message Text="  Size:  %(FirstItem.Size)"  />

        <Message Text="SecondItem: %(SecondItem.Identity)" />
        <Message Text="  Class: %(SecondItem.Class)" />
        <Message Text="  Size:  %(SecondItem.Size)"  />
    </Target>
</Project>

<!--
Output:
  FirstItem: rhinoceros
    Class: mammal
    Size:  large
  SecondItem: rhinoceros
    Class: mammal
    Size:
-->
```

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> RemoveMetadata-Attribut

 Wenn ein Element in einem Ziel erstellt wird, enthält das Item-Element möglicherweise das `RemoveMetadata`-Attribut. Wenn dieses Attribut angegeben wird, werden alle Metadaten aus dem Quellelement in das Zielelement übertragen. Davon ausgenommen sind Metadaten, deren Namen in der durch Semikolons getrennten Liste von Namen enthalten sind. Wird für dieses Attribut ein leerer Wert angegeben, ist dies, als wäre nichts angegeben worden. Das `RemoveMetadata`-Attribut wurde in .NET Framework 4.5 eingeführt.

 Das folgende Beispiel veranschaulicht, wie das `RemoveMetadata`-Attribut verwendet wird.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <MetadataToRemove>Size;Material</MetadataToRemove>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)" />
        <Message Text="  Size:     %(Item1.Size)" />
        <Message Text="  Color:    %(Item1.Color)" />
        <Message Text="  Material: %(Item1.Material)" />
        <Message Text="Item2: %(Item2.Identity)" />
        <Message Text="  Size:     %(Item2.Size)" />
        <Message Text="  Color:    %(Item2.Color)" />
        <Message Text="  Material: %(Item2.Material)" />
    </Target>
</Project>

<!--
Output:
  Item1: stapler
    Size:     medium
    Color:    black
    Material: plastic
  Item2: stapler
    Size:
    Color:    black
    Material:
-->
```

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> KeepDuplicates-Attribut

 Wenn ein Element in einem Ziel erstellt wird, enthält das Item-Element möglicherweise das `KeepDuplicates`-Attribut. `KeepDuplicates` ist ein `Boolean`-Attribut, das angibt, ob ein Element der Zielgruppe hinzugefügt werden soll, wenn es sich um ein exaktes Duplikat eines bereits vorhandenen Elements handelt.

 Wenn Quell- und Zielelement denselben Include-Wert, aber unterschiedliche Metadaten aufweisen, wird das Element auch dann hinzugefügt, wenn für `KeepDuplicates``false` festgelegt wurde. Wird für dieses Attribut ein leerer Wert angegeben, ist dies, als wäre nichts angegeben worden. Das `KeepDuplicates`-Attribut wurde in .NET Framework 4.5 eingeführt.

 Das folgende Beispiel veranschaulicht, wie das `KeepDuplicates`-Attribut verwendet wird.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Item1 Include="hourglass;boomerang" />
        <Item2 Include="hourglass;boomerang" />
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item1 Include="hourglass" KeepDuplicates="false" />
            <Item2 Include="hourglass" />
        </ItemGroup>

        <Message Text="Item1: @(Item1)" />
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />
        <Message Text="Item2: @(Item2)" />
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />
    </Target>
</Project>

<!--
Output:
  Item1: hourglass;boomerang
    hourglass  Count: 1
    boomerang  Count: 1
  Item2: hourglass;boomerang;hourglass
    hourglass  Count: 2
    boomerang  Count: 1
-->
```

## <a name="updating-metadata-on-items-in-an-itemgroup-outside-of-a-target"></a>Aktualisieren von Metadaten für Elemente in einer ItemGroup außerhalb eines Ziels

Für Elemente außerhalb von Zielen können vorhandene Metadaten über das `Update`-Attribut aktualisiert werden. Dieses Attribut ist **nicht** für Elemente unter Zielen verfügbar.

```xml
<Project>
    <PropertyGroup>
        <MetadataToUpdate>pencil</MetadataToUpdate>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Color>red</Color>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="notebook">
            <Size>SMALL</Size>
            <Color>YELLOW</Color>
        </Item2>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="$(MetadataToUpdate);stapler;er*r;@(Item2)" Price="10" Material="">
            <Color>RED</Color>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: RED
    Material:
    Price: 10
Item1: pencil
    Size: small
    Color: RED
    Material:
    Price: 10
Item1: eraser
    Size:
    Color: RED
    Material:
    Price: 10
Item1: notebook
    Size: large
    Color: RED
    Material:
    Price: 10
-->
```

:::moniker range=">=vs-2019"
In MSBuild (Version 16.6 und höher) unterstützt das `Update`-Attribut qualifizierte Metadatenverweise, um das Importieren von Metadaten aus mindestens zwei Elementen zu vereinfachen.

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item3 Include="notebook">
            <Size>SMALL</Size>
            <Color>BLUE</Color>
            <Price>20</Price>
        </Item3>

        <!-- Metadata can be expressed either as attributes or as elements -->
        <Item1 Update="@(Item2);er*r;@(Item3)" Size="%(Size)" Color="%(Item2.Color)" Price="%(Item3.Price)" Model="2020">
            <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: medium
    Color: black
    Material: plastic
    Price:
    Model:
Item1: pencil
    Size: small
    Color: RED
    Material: Premium PLASTIC
    Price:
    Model: 2020
Item1: eraser
    Size: small
    Color:
    Material: gum
    Price:
    Model: 2020
Item1: notebook
    Size: large
    Color:
    Material: paper
    Price: 20
    Model: 2020
-->
```

Anmerkungen:
- Nicht qualifizierte Metadaten (% (M)) werden an den zu aktualisierenden Elementtyp (`Item1` im Beispiel oben) gebunden. Qualifizierte Metadaten (`%(Item2.Color)`) werden innerhalb des Satzes der erfassten übereinstimmenden Elementtypen aus dem Aktualisierungsausdruck gebunden.
- Wenn ein Element mehrmals innerhalb von und zwischen mehreren referenzierten Elementen übereinstimmt:
  - Das letzte Vorkommen jedes referenzierten Elementtyps wird erfasst (also ein erfasstes Element pro Elementtyp).
  - Dies entspricht dem Verhalten der Batchverarbeitung von Aufgabenelementen unter den Zielen.
- Hier können%()-Verweise eingefügt werden:
  - Metadaten
  - Metadatenbedingungen
- Beim Abgleich von Metadatennamen wird nicht zwischen Groß- und Kleinschreibung unterschieden.
:::moniker-end

## <a name="updating-metadata-on-items-in-an-itemgroup-of-a-target"></a>Aktualisieren von Metadaten für Elemente in einer ItemGroup eines Ziels

Metadaten können auch in Zielen mit einer weniger ausdrucksstarken Syntax als `Update` geändert werden:

```xml
<Project>
    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
        <Item1 Include="pencil">
            <Size>small</Size>
            <Color>yellow</Color>
            <Material>wood</Material>
        </Item1>
        <Item1 Include="eraser">
            <Size>small</Size>
            <Color>red</Color>
            <Material>gum</Material>
        </Item1>
        <Item1 Include="notebook">
            <Size>large</Size>
            <Color>white</Color>
            <Material>paper</Material>
        </Item1>

        <Item2 Include="pencil">
            <Size>MEDIUM</Size>
            <Color>RED</Color>
            <Material>PLASTIC</Material>
            <Price>10</Price>
        </Item2>

        <Item2 Include="ruler">
            <Color>GREEN</Color>
        </Item2>

    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <!-- Metadata can be expressed either as attributes or as elements -->
            <Item1 Size="GIGANTIC" Color="%(Item2.Color)">
                <Material Condition="'%(Item2.Material)' != ''">Premium %(Item2.Material)</Material>
            </Item1>
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)
    Size: %(Item1.Size)
    Color: %(Item1.Color)
    Material: %(Item1.Material)
    Price: %(Item1.Price)
    Model: %(Item1.Model)" />
    </Target>
</Project>

<!--  
Item1: stapler
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: pencil
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: eraser
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
Item1: notebook
    Size: GIGANTIC
    Color: GREEN
    Material: Premium PLASTIC
    Price:
    Model:
-->
```

## <a name="see-also"></a>Siehe auch

- [Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)
- [Gemeinsame MSBuild-Projektelemente](../msbuild/common-msbuild-project-items.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [How to: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md)
- [How to: Ausschließen von Dateien aus dem Buildvorgang](../msbuild/how-to-exclude-files-from-the-build.md).
- [How to: Anzeigen einer durch Trennzeichen getrennten Elementliste](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Elementdefinitionen](../msbuild/item-definitions.md)
- [Batchverarbeitung](../msbuild/msbuild-batching.md)
