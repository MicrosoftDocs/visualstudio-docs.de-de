---
title: Kreatanplace-Element (Visual Studio-Vorlagen)
description: Erfahren Sie mehr über das Element "kreatanplace" und wie es angibt, ob das Projekt erstellt und die Parameter Ersetzung an einem bestimmten oder temporären Speicherort durchgeführt werden soll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51348e8304b67314ffd19d0aec15d43d904ee651
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671981"
---
# <a name="createinplace-element-visual-studio-templates"></a>Kreatanplace-Element (Visual Studio-Vorlagen)
Gibt an, ob das Projekt erstellt und die Parameter Ersetzung am angegebenen Speicherort durchgeführt werden soll, oder ob die Parameter Ersetzung an einem temporären Speicherort durchgeführt und das Projekt am angegebenen Speicherort gespeichert werden soll.

 \<VSTemplate> \<TemplateData>
 \<CreateInPlace>

## <a name="syntax"></a>Syntax

```
<CreateInPlace> true/false </CreateInPlace>
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
 Ein Textwert ist erforderlich.

 Der Text muss entweder `true` oder `false` sein. Gibt `true` an, dass das Projekt erstellt und die Parameter Ersetzung an der im Dialogfeld **Neues Projekt** angegebenen Position ausgeführt wird. Wenn `false` der Wert ist, wird die Parameter Ersetzung an einem temporären Speicherort durchgeführt, und das Projekt wird dann an den angegebenen Speicherort kopiert.

## <a name="remarks"></a>Hinweise
 `CreateInPlace` ist ein optionales Element. Standardwert: `true`.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Vorlage veranschaulicht.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateInPlace>false</CreateInPlace>
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
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
