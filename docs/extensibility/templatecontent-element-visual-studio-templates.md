---
title: TemplateContent-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 577ce71d3900947cde1de9a1e913124ab778a1ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699230"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent-Element (Visual Studio-Vorlagen)

Gibt den Inhalt der Vorlage an.

Element Hierarchie:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>Syntax

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|Gibt an, ob die Projekt Mappe erstellt werden soll, wenn ein Projekt aus der Vorlage erstellt wird.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die Dateien oder Verzeichnisse an, die dem Projekt hinzugefügt werden sollen.|
|[Referenzen](../extensibility/references-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die für eine Element Vorlage erforderlichen Assemblyverweise an.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Optionales Element.<br /><br /> Gibt eine Datei an, die in der Vorlage enthalten ist.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt alle benutzerdefinierten Parameter an, die beim Erstellen eines Projekts oder Elements aus der Vorlage verwendet werden sollen.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Enthält alle Metadaten für die Projektvorlage, die Element Vorlage oder Starter Kit.|

## <a name="remarks"></a>Bemerkungen
 `TemplateContent` ist ein erforderliches Element.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Anwendung veranschaulicht.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
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

## <a name="see-also"></a>Weitere Informationen

- [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
