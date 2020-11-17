---
title: Kreatenewfolder-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das Element "kreatenewfolder" und dessen Bestimmung, ob das Zielverzeichnis, in dem das Projekt erstellt werden soll, nicht vorhanden ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15633c2f701c813ca24c5484fd4108a86c57b05b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671578"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>Kreatenewfolder-Element (Visual Studio-Vorlagen)
Bestimmt, ob geprüft werden soll, dass das Zielverzeichnis, indem das Projekt erstellt werden soll, nicht existiert. Wenn das Verzeichnis existiert, kann ein neues Verzeichnis für das Projekt erstellt werden. Diese Einstellung wird in der Regel vom `NewProjectRequiresNewFolder(VsTemplate)`-Registrierungs-Flag überschrieben (`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`), das alle gängigen Projekttypen verwenden, um zu bestimmen, ob ein neues Projekt in einem neuen Verzeichnis erstellt werden soll.

 \<VSTemplate> \<TemplateData>
 \<CreateNewFolder>

## <a name="syntax"></a>Syntax

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>type
 `Boolean`

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

 Der Text muss `true` oder `false` sein, um anzugeben, ob ein neuer Containerordner beim Erstellen eines Projekts anhand einer Vorlage angelegt werden soll.

## <a name="remarks"></a>Hinweise
 `CreateNewFolder` ist ein optionales Element. Der Standardwert ist `true`.

 Der im `CreateNewFolder`-Element angegebene Wert wird nur von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] berücksichtigt, wenn das zugrunde liegende Projektsystem ihn unterstützt.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird festgelegt, dass kein neuer Ordner angelegt wird, wenn ein Projekt anhand einer Vorlage erstellt wird.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
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
