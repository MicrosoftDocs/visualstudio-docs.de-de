---
title: EnableLocationBrowseButton-Element (Visual Studio-Vorlagen)
description: Erfahren Sie mehr über das EnableLocationBrowseButton-Element und wie es angibt, ob die Schaltfläche "Durchsuchen" im Dialogfeld "Neues Projekt" verfügbar ist.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 463219218994c9ec1e0f8a5be6e43a0bfd3f5d49
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671258"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton-Element (Visual Studio-Vorlagen)
Gibt an, ob die Schaltfläche " **Durchsuchen** " im Dialogfeld " **Neues Projekt** " verfügbar ist, sodass Benutzer das Standardverzeichnis, in dem ein neues Projekt gespeichert wird, leicht ändern können.

 \<VSTemplate> \<TemplateData>
 \<EnableLocationBrowseButton>

## <a name="syntax"></a>Syntax

```xml
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
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

 Der Text muss entweder `true` oder lauten `false` und zeigt an, ob die Schaltfläche **Durchsuchen** im Dialogfeld **Neues Projekt** angezeigt werden soll.

## <a name="remarks"></a>Hinweise
 `EnableLocationBrowseButton` ist ein optionales Element. Der Standardwert ist `true` , wodurch die Schaltfläche **Durchsuchen** im Dialogfeld **Neues Projekt** angezeigt wird.

 Im Dialogfeld **Neues Projekt** gibt das Textfeld **Speicherort** das Verzeichnis an, in dem ein neues Projekt gespeichert wird. Mithilfe der Schaltfläche **Durchsuchen** können Sie dieses Verzeichnis ändern, indem Sie das Dialogfeld **Projekt Speicherort** anzeigen, mit dessen Hilfe Sie problemlos zu einem anderen Verzeichnis navigieren können, das auf Ihrem Computer verfügbar ist, und es dann als das Verzeichnis auswählen, in dem das neue Projekt gespeichert wird.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine Windows-Anwendung in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
