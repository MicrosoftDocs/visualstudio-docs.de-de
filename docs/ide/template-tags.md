---
title: Hinzufügen oder Bearbeiten von Tags in Projektvorlagen
description: Erfahren Sie, wie Sie in Visual Studio Tags in Projektvorlagen hinzufügen oder bearbeiten.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jmartens
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: a5f8c3f6e96e8e593fe74fd58b3e8bafab0ad88e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950613"
---
# <a name="add-tags-to-project-templates"></a>Hinzufügen von Tags zu Projektvorlagen

Ab [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/), Version 16.1 Preview 2, können Sie Tags für Sprache, Plattform und Projekttyp zu Ihren Projektvorlagen hinzufügen. 

Tags werden an zwei Stellen im Dialogfeld **Neues Projekt** verwendet:

- Tags werden unter der Vorlagenbeschreibung angezeigt.

   ![Projektvorlage mit Tags im Dialogfeld „Neues Projekt“](media/npd-item-with-template-tags.png)

- Tags ermöglichen das Durchsuchen und Filtern der Vorlage.

   ![Suchen und Filtern im Dialogfeld „Neues Projekt“](media/npd-search-and-filter.png)

Sie können Tags hinzufügen, indem Sie die *.vstemplate*-XML-Datei aktualisieren. Sie können hierbei entweder in Visual Studio integrierte Vorlagentags verwenden oder benutzerdefinierte Vorlagentags erstellen. Vorlagentags werden nur im Dialogfeld **Neues Projekt** von Visual Studio 2019 angezeigt. Vorlagentags haben keine Auswirkung darauf, wie die Vorlage in Vorgängerversionen von Visual Studio gerendert wird.

## <a name="add-or-edit-tags"></a>Hinzufügen oder Bearbeiten von Tags

Möglicherweise möchten Sie Tags zur *.vstemplate*-XML-Datei Ihrer Projektvorlage hinzufügen oder bearbeiten, wenn Sie eine der folgenden Aufgaben ausführen:

* [Erstellen einer neuen Projektvorlage](how-to-create-project-templates.md) mithilfe des Assistenten zum Exportieren von Vorlagen
* [Aktualisieren einer vorhandenen Projektvorlage](how-to-update-existing-templates.md)
* [Erstellen einer neuen VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="syntax"></a>Syntax

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Attribute

In erweiterten Benutzerszenarien können die folgenden optionalen Attribute verwendet werden:

|Attribut|Beschreibung|
|---------------|-----------------|
|`Package`|Eine GUID, die die Visual Studio-Paket-ID angibt.|
|`ID`|Gibt die Visual Studio-Ressourcen-ID an.|

Syntax:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Elements

### <a name="child-elements"></a>Untergeordnete Elemente

Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Erforderlich) Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert

Ein Textwert ist erforderlich, es sei denn, es werden die Attribute `Package` und `ID` verwendet.

Der Text gibt den Namen der Vorlage an.

## <a name="built-in-tags"></a>Integrierte Tags

Visual Studio umfasst verschiedene integrierte Tags. Wenn Sie ein integriertes Tag hinzufügen, wird über das Tag eine lokalisierte Ressource gerendert. 

Die folgende Liste zeigt die in Visual Studio verfügbaren integrierten Tags. Zugehörige Werte werden in Klammern angezeigt.

| Tag für Sprache | Tag für Plattform | Tag für Projekttyp |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Cloud (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Console (`console`) |
| F# (`fsharp`) | iOS (`ios`) | Desktop (`desktop`) |
| Java (`java`) | Linux (`linux`) | Erweiterungen (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Spiele (`games`) |
| Python (`python`) | tvOS (`tvos`) | IoT (`iot`) |
| Abfragesprache (`querylanguage`) | Windows (`windows`) | Bibliothek (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Machine Learning (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Mobile (`mobile`) |
| | | Office (`office`) |
| | | Sonstige (`other`) |
| | | Service (`service`) |
| | | Test (`test`) |
| | | UWP (`uwp`) |
| | | Web (`web`) |

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Metadaten für eine Projektvorlage einer Visual C#-Anwendung:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>csharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
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
- [Erstellen von Projekt- und Elementvorlagen](creating-project-and-item-templates.md)
- [Anpassen von Projekt- und Elementvorlagen](customizing-project-and-item-templates.md)
- [Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)
