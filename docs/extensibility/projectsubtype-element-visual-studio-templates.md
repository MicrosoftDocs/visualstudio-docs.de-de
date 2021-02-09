---
title: ProjectSubType-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Erfahren Sie mehr über das ProjectSubType-Element und wie es die Vorlage in eine Unterkategorie des Werts klassifiziert, der im ProjectType-Element angegeben ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ee2e267461d37456c9a2e64c43ae104d19ee615
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911762"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType-Element (Visual Studio-Vorlagen)
Klassifiziert die Vorlage in eine Unterkategorie des Werts, der im-Element angegeben ist `ProjectType` .

 \<VSTemplate> \<TemplateData>
 \<ProjectSubType>

## <a name="syntax"></a>Syntax

```xml
<ProjectSubType> SubType </ProjectSubType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Dieser Wert gibt die Unterkategorie der Vorlage an.

## <a name="remarks"></a>Bemerkungen
 `ProjectSubType` ist ein optionales untergeordnetes Element von `TemplateData`.

 Das- `ProjectSubType` Element stellt eine Unterkategorie für das [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) -Element bereit. Dieser Wert kann Folgendes umfassen:

- `SmartDevice-NETCFv1`: Gibt an, dass die Vorlage auf die [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] Version 1,0 abzielt.

- `SmartDevice-NETCFv2`: Gibt an, dass die Vorlage auf die [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] Version 2,0 abzielt.

  Wenn eine Vorlage ein- `ProjectType` Element mit dem Wert enthält `Web` , gibt das- `ProjectSubType` Element die Programmiersprache der Vorlage an. Dieses Element kann die folgenden Werte aufweisen:

- `CSharp`: Gibt an, dass die Vorlage ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Webprojekt oder-Element erstellt.

- `VisualBasic`: Gibt an, dass die Vorlage ein [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Webprojekt oder-Element erstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Metadaten für eine Projektvorlage für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Geräte Anwendung, die auf [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] Version 2,0 abzielt.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
- [ProjectType-Element (Visual Studio-Vorlagen)](../extensibility/projecttype-element-visual-studio-templates.md)
