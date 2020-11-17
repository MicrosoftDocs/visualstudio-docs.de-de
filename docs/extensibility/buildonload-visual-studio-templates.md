---
title: BuildOnLoad-Attribut und-Element (Visual Studio-Vorlagen)
titleSuffix: ''
description: Erfahren Sie mehr über das BuildOnLoad-Attribut und das-Element sowie darüber, wie es angibt, ob das Projekt sofort nach der Erstellung erstellt werden soll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37df139f890a7717287db675a3a4b7e4b250dbf3
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671604"
---
# <a name="buildonload-attribute-and-element"></a>BuildOnLoad-Attribut und-Element

Gibt an, ob das Projekt sofort nach der Erstellung erstellt werden soll. **BuildOnLoad** ist sowohl ein Attribut als auch ein Element.

Element Hierarchie:

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>Element Syntax

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert

Ein Textwert ist für das **BuildOnLoad** -Element erforderlich. Der Text muss entweder `true` oder sein `false` , um anzugeben, ob das Projekt sofort nach der Erstellung erstellt werden soll.

## <a name="remarks"></a>Hinweise

**BuildOnLoad** ist ein optionales Attribut. Standardwert: `false`.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die Metadaten für eine c#-Vorlage veranschaulicht, wenn **BuildOnLoad** als Element verwendet wird:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildOnLoad>true</BuildOnLoad>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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

- [Buildprojectonload-Element](buildprojectonload-element-visual-studio-templates.md)
- [TemplateContent-Element](../extensibility/templatecontent-element-visual-studio-templates.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
