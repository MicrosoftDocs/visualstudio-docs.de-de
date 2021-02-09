---
title: LocationField-Element (Visual Studio-Projektvorlagen)
titleSuffix: ''
description: Informieren Sie sich über das LocationField-Element und darüber, wie es angibt, ob das Textfeld Neues Projekt Dialogfeld Speicherort für die Projektvorlage aktiviert, deaktiviert oder ausgeblendet ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cbd0d6ee6ede29be35437125f614512ff3bbeab3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915189"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField-Element (Visual Studio-Projektvorlagen)
Gibt an, ob das Textfeld **Speicherort** im Dialogfeld **Neues Projekt** für die Projektvorlage aktiviert, deaktiviert oder ausgeblendet ist.

 \<VSTemplate> \<TemplateData>
 \<LocationField>

## <a name="syntax"></a>Syntax

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie Sie im **neuen Projekt** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Gültige Textwerte sind:

- `Enabled`, das angibt, dass das Feld **Speicherort** des Dialog Felds **Neues Projekt** aktiviert ist.

- `Disabled`, das angibt, dass das Feld **Speicherort** des Dialog Felds **Neues Projekt** deaktiviert ist.

- `Hidden`, das angibt, dass das Feld **Speicherort** des Dialog Felds **Neues Projekt** ausgeblendet ist.

## <a name="remarks"></a>Bemerkungen
 Standardwert: `Enabled`.

 Das Textfeld **Speicherort** im Dialogfeld **Neues Projekt** ermöglicht es Benutzern, das Standardverzeichnis zu ändern, in dem neue Projekte gespeichert werden.

 Der im-Element angegebene Wert `Location` wird nur von dem Dialogfeld berücksichtigt, wenn es vom zugrunde liegenden Projekt System unterstützt wird.

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
        <LocationField>Disabled</LocationField>
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
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
