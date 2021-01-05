---
title: Schema Referenz für das Visual Studio-Vorlagen Manifest | Microsoft-Dokumentation
description: Dieser Schema Verweis beschreibt das Format der Visual Studio-Vorlagen Manifest-Dateien, die für Visual Studio-Projekt-oder-Element Vorlagen generiert werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d712f2cb95b2df9680c4476805e9dfb6809cf038
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863837"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Schema Referenz für das Visual Studio-Vorlagen Manifest
Dieses Schema beschreibt das Format der *vstman*-Dateien (Visual Studio-Vorlagen Manifest), die für Visual Studio-Projekt-oder-Element Vorlagen generiert werden. Das Schema beschreibt auch den Speicherort und andere relevante Informationen zur Vorlage.

 : Da es separate Element-und Projektvorlagen Verzeichnisse gibt, sollte ein Manifest nie über eine Mischung aus Element-und Projektvorlagen verfügen.

> [!IMPORTANT]
> Dieses Manifest ist ab Visual Studio 2017 verfügbar.

## <a name="vstemplatemanifest-element"></a>Vstemplatemanifest-Element
 Das Stamm Element des Manifests.

### <a name="attributes"></a>Attribute

- **Version**: eine Zeichenfolge, die die Version des Vorlagen Manifests darstellt. Erforderlich.

- **Locale**: eine Zeichenfolge, die das Gebiets Schema oder die Gebiets Schemas des Vorlagen Manifests darstellt. Der Gebiets Schema Wert gilt für alle Vorlagen. Sie müssen für jedes Gebiets Schema ein separates Manifest verwenden. Optional.

### <a name="child-elements"></a>Untergeordnete Elemente

- **Vstemplatecontainer** Optionale.

- **Vstemplatedir** Optionale.

### <a name="parent-element"></a>Übergeordnetes Element
 Keine.

## <a name="vstemplatecontainer"></a>Vstemplatecontainer
 Der Container der Vorlagen Manifest-Elemente. Ein Manifest weist einen Vorlagen Container für jede Vorlage auf, die er definiert.

### <a name="attributes"></a>Attribute
 **Vstemplatetype**: ein Zeichen folgen Wert, der den Typ der Vorlage angibt ( `"Project"` , `"Item"` oder `"ProjectGroup"` ). Erforderlich

### <a name="child-elements"></a>Untergeordnete Elemente

- **Relativepathondisk**: der relative Pfad der Vorlagen Datei auf dem Datenträger. Dieser Speicherort definiert auch die Platzierung der Vorlage in der Vorlagen Struktur, die im Dialogfeld **Neues Projekt** oder **Neues Element** angezeigt wird. Bei Vorlagen, die als Verzeichnis und einzelne Dateien bereitgestellt werden, verweist dieser Pfad auf das Verzeichnis, das die Vorlagen Dateien enthält. Bei Vorlagen, die als *ZIP* -Datei bereitgestellt werden, sollte dieser Pfad der Pfad zur *ZIP* -Datei sein.

- * * Vstemplateheader: ein [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) -Element, das den Header beschreibt.

### <a name="parent-element"></a>Übergeordnetes Element
 **Vstemplatemanifest**

## <a name="vstemplatedir"></a>Vstemplatedir
 Beschreibt das Verzeichnis, in dem sich die Vorlage befindet. Ein Manifest kann mehrere **vstemplatedir** -Einträge enthalten, um lokalisierte Namen und Sortierreihenfolge für Verzeichnisse bereitzustellen und deren Darstellung in der Vorlagen Kategoriestruktur zu steuern.

 Aufgrund des Entwurfs sollten **vstemplatedir** -Einträge nur in nicht vom Gebiets Schema angegebenen Manifesten angezeigt werden.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

- **RelativePath**: der Pfad der Vorlage. Es kann nur ein Eintrag pro Pfad vorhanden sein, sodass der erste für alle Manifeste gewinnt.

- **LocalizedName**: ein **namedescriptionicon** -Element, das den lokalisierten Namen angibt. Optional.

- **Sortor der**: eine Zeichenfolge, die die Sortierreihenfolge angibt. Optional.

- **Parameterfolderoverridename**: der überschriebene Name des übergeordneten Ordners. Optional. Dieses Element hat ein **Name** -Attribut, bei dem es sich um einen Zeichen folgen Wert handelt, der den Namen angibt.

### <a name="parent-element"></a>Übergeordnetes Element
 **Vstemplatemanifest**

## <a name="namedescriptionicon"></a>Namedescriptionicon
 Gibt den Namen und die Beschreibung an, möglicherweise für lokalisierte Vorlagen. Siehe **LocalizedName** oben.

### <a name="attributes"></a>Attribute

- **Package**: ein Zeichen folgen Wert, der das Paket angibt. Optional.

- **ID**: ein Zeichen folgen Wert, der die ID angibt. Optional.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-element"></a>Übergeordnetes Element
 **LocalizedName**

## <a name="examples"></a>Beispiele
 Der folgende Code ist ein Beispiel für eine *vstman* -Datei der Projektvorlage.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Der folgende Code ist ein Beispiel für eine Element Vorlage *. vstman* -Datei.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```
