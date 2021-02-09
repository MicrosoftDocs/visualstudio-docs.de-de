---
title: ProjectTemplateLink-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Erfahren Sie mehr über das <element> -Element und wie es den Pfad zur VSTEMPLATE-Datei eines Projekts in einer Vorlage mit mehreren Projekten angibt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dba5063080fb45c366e7a1b76461b0a0d8978f7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915162"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink-Element (Visual Studio-Vorlagen)
Gibt den Pfad zur *VSTEMPLATE* -Datei eines Projekts in einer Vorlage mit mehreren Projekten an.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>
 \<ProjectTemplateLink>
noch \<VSTemplate>
 \<TemplateContent>
 \<ProjectCollection>
 \<SolutionFolder>
 \<ProjectTemplateLink>

## <a name="syntax"></a>Syntax

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|`ProjectName`|Optionales Attribut.<br /><br /> Gibt in einer Vorlage für mehrere Projekte den Namen für jedes einzelne Projekt an. Das Dialogfeld **Neues Projekt** kann einzelnen Projekten keine Namen zuweisen.|
|`CopyParameters`|Ermöglicht, dass alle Variablen in der Hauptgruppenvorlage in jede der verknüpften Vorlagen kopiert werden können.<br /><br /> Die Parameter in verknüpften Vorlagen enthalten ein Präfix `"$ext_*$"`. Wenn z. b. in der übergeordneten Gruppen Vorlage der-Parameter den `$projectname$` Wert **ExampleProject1** hat, wenn die verknüpfte Vorlage die Ausführung erhält, wird ein Parameter abgerufen, bei dem es sich um `$ext_projectname$` eine Kopie des `$projectname$` Parameters aus der übergeordneten Gruppen Vorlage handelt.<br /><br /> Dadurch können verknüpfte Vorlagen einige häufig verwendete Parameter freigeben, die sonst möglicherweise nur in der Vorlage der übergeordneten Gruppe erstellt werden.<br /><br /> Dieses Attribut ist optional und erhält automatisch den Wert `false`, wenn es nicht enthalten ist.<br /><br /> Eingeführt in Visual Studio 2013 Update 2. Weitere Informationen zum Verweisen auf die richtige Produktversion finden Sie unter Verweisassemblys, [die im Visual Studio 2013 SDK-Update 2](/previous-versions/dn632168(v=vs.120))|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Gruppiert Projekte in Vorlagen für mehrere Projekte.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Dieser Text gibt den Pfad zur *VSTEMPLATE* -Datei der Vorlage an.

## <a name="remarks"></a>Bemerkungen
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte. Das- `ProjectTemplateLink` Element wird verwendet, um den Speicherort der *VSTEMPLATE* -Datei für eines der Projekte in der Vorlage anzugeben. Die *VSTEMPLATE* -Datei einer Vorlage mit mehreren Projekten enthält ein- `ProjectTemplateLink` Element für jedes Projekt in der Vorlage. Weitere Informationen zu Vorlagen mit mehreren Projekten finden Sie unter Gewusst [wie: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine einfache *VSTEMPLATE* -Stammdatei für mehrere Projekte. In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`. Durch das `ProjectName`-Attribut im `ProjectTemplateLink`-Element wird der Name festgelegt, der dem Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zugewiesen wird. Wenn das `ProjectName` Attribut nicht vorhanden ist, wird der Name der *VSTEMPLATE* -Datei als Projektname verwendet.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Vorgehensweise: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md)