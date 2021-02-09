---
title: Icon-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das Icon-Element und darüber, wie es den Pfad und den Dateinamen der Bilddatei angibt, die als Symbol fungiert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fced03b190ab46885c5d786b8374a05c3bd043b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883297"
---
# <a name="icon-element-visual-studio-templates"></a>Icon-Element (Visual Studio-Vorlagen)
Gibt den Pfad und den Dateinamen der Bilddatei an, die als Symbol dient, das im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** für die Vorlage angezeigt wird.

 \<VSTemplate> \<TemplateData>
 \<Icon>

## <a name="syntax"></a>Syntax

```
<Icon>
    IconFileName
</Icon>
```

```
<Icon Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|`Package`|Optionales Attribut für erweiterte Benutzer Szenarien.<br /><br /> Eine GUID, die die Visual Studio-Paket-ID angibt.|
|`ID`|Optionales Attribut für erweiterte Benutzer Szenarien.<br /><br /> Gibt die Visual Studio-Ressourcen-ID an.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich, es sei denn, die Attribute `Package` und `ID` werden verwendet.

 Der Text enthält den Pfad und den Dateinamen des Vorlagen Symbols, das im Dialogfeld **Neues Projekt** angezeigt wird.

## <a name="remarks"></a>Bemerkungen
 `Icon` ist ein erforderliches untergeordnetes Element von `TemplateData`.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Anwendung veranschaulicht.

```
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
