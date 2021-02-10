---
title: Sortor der-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Erfahren Sie mehr über das sortor der-Element und darüber, wie es einen Wert angibt, der zum Anordnen der Vorlage verwendet wird, wie Sie im Dialogfeld Neues Projekt oder neues Element hinzufügen angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a086f2ae678541ce28e9ede874c4198e349f438
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942918"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder-Element (Visual Studio-Vorlagen)
Gibt einen Wert an, der verwendet wird, um die Vorlage neben anderen Vorlagen in derselben Kategorie anzuordnen, wie Sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.

 \<VSTemplate> \<TemplateData>
 \<SortOrder>

## <a name="syntax"></a>Syntax

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Ein `integer` , das den Sortierreihen folgen Wert darstellt.

## <a name="remarks"></a>Bemerkungen
 `SortOrder` ist ein optionales Element. Der Standardwert ist 100, und alle Werte müssen ein Vielfaches von 10 sein.

 Das- `SortOrder` Element wird für vom Benutzer erstellte Vorlagen ignoriert. Alle vom Benutzer erstellten Vorlagen sind alphabetisch sortiert.

 Vorlagen mit niedrigen Sortierreihenfolge-Werten werden im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** vor Vorlagen mit Werten für hohe Sortierreihenfolge angezeigt.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine Standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Klassen Vorlage veranschaulicht.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 In diesem Beispiel ist das- `SortOrder` Element relativ hoch. Es ist wahrscheinlich, dass andere [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Element Vorlagen einen `SortOrder` niedrigeren Wert als aufweisen `290` und vor dieser Vorlage im Dialogfeld **Neues Element** angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
