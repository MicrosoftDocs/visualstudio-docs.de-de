---
title: Numofparser categoriestorollup-Element (Vorlagen)
description: Informieren Sie sich über das Element "numofparser categoriestorollup" und darüber, wie es die Anzahl der übergeordneten Kategorien angibt, in denen die Vorlage im Dialogfeld "Neues Projekt" angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bcf11552ecd137f63f1f3ccca2b1d869f003b3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883076"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>Numofparser categoriestorollup-Element (Visual Studio-Vorlagen)
Gibt die Anzahl der übergeordneten Kategorien an, in denen die Vorlage im Dialogfeld **Neues Projekt** angezeigt wird.

 \<VSTemplate> \<TemplateData>
 \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>Syntax

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein- `integer` Wert ist erforderlich.

 Dieser Wert gibt die Anzahl der übergeordneten Kategorien an, in denen die Vorlage im Dialogfeld **Neues Projekt** angezeigt wird.

## <a name="remarks"></a>Bemerkungen
 `NumberOfParentCategoriesToRollUp` ist ein optionales Element.

## <a name="example"></a>Beispiel
 In diesem Beispiel werden die Metadaten für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows-Anwendung veranschaulicht. Wenn eine Vorlage mit diesen Metadaten zwei Ordner Ebenen unter dem Knoten der obersten Ebene platziert [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] , wird die Vorlage im Dialogfeld **Neues Projekt** im Knoten der obersten Ebene angezeigt. Wenn `NumberOfParentCategoriesToRollUp` nicht festgelegt ist, wird die Vorlage nur in dem Knoten angezeigt, in dem Sie sich physisch befindet.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
