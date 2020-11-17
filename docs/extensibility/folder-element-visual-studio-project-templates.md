---
title: Folder-Element (Visual Studio-Projektvorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das Folder-Element und darüber, wie es einen Ordner angibt, der dem Projekt hinzugefügt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3f357f6c48280d12e4ddab6135245e699d0a44
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672716"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder-Element (Visual Studio-Projektvorlagen)
Gibt einen Ordner an, der dem Projekt hinzugefügt wird.

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<Folder>

## <a name="syntax"></a>Syntax

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attributes

|Attribut|Beschreibung|
|---------------|-----------------|
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Projekt Ordners.|
|`TargetFolderName`|Optionales Attribut.<br /><br /> Gibt den Namen an, der dem Ordner zugewiesen werden soll, wenn ein Projekt aus der Vorlage erstellt wird. Dieses Attribut eignet sich für die Verwendung der Parameter Ersetzung, um einen Ordnernamen zu erstellen oder einen Ordner mit einer internationalen Zeichenfolge zu benennen, die nicht direkt in der *ZIP* -Datei verwendet werden kann.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|`Folder`|Gibt einen Ordner an, der dem Projekt hinzugefügt werden soll. `Folder` -Elemente können untergeordnete `Folder` Elemente enthalten.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Gibt eine Datei an, die dem Projekt hinzugefügt werden soll.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Optionales untergeordnetes Element von [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Hinweise
 `Folder` ist ein optionales untergeordnetes Element von `Project` .

 Sie können eine der folgenden Methoden verwenden, um Projekt Elemente in Ordner in einer Vorlage zu organisieren:

- Schließen Sie die Ordner in die *ZIP* -Datei der Vorlage ein, und fügen Sie Sie dem Projekt in der *VSTEMPLATE* -Datei hinzu, indem Sie den Pfad zur Datei in den `ProjectItem` Elementen ohne `Folder` Elemente angeben. Dies ist die empfohlene Methode. Beispiel:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Schließen Sie die Ordner in die *ZIP* -Datei der Vorlage ein, und fügen Sie Sie dem Projekt in der *VSTEMPLATE* -Datei mit `Folder` Elementen hinzu. Beispiel:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Schließen Sie keine Ordner in die *ZIP* -Datei der Vorlage ein, sondern fügen Sie mithilfe des- `TargetFileName` Attributs des-Elements Ordner hinzu `ProjectItem` . Zum Beispiel:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows-Anwendung veranschaulicht.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [ProjectItem-Element (Visual Studio-Element Vorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)
