---
title: Project-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 335a1e4efa62f07e10bb24b9971627d24bb13273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702001"
---
# <a name="project-element-visual-studio-templates"></a>Project-Element (Visual Studio-Vorlagen)
Gibt die Dateien oder Verzeichnisse an, die dem Projekt hinzugefügt werden sollen.

 \<VSTemplate> \<TemplateContent>
 \<Project>

## <a name="syntax"></a>Syntax

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|`File`|Erforderliches Attribut.<br /><br /> Gibt den Namen der Projektdatei in der *ZIP* -Datei der Vorlage an.|
|`ReplaceParameters`|Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob die Projektdatei Parameterwerte aufweist, die beim Erstellen eines Projekts aus der Vorlage ersetzt werden müssen. Der Standardwert ist `false`.|
|`TargetFileName`|Optionales Attribut.<br /><br /> Gibt den Namen der Projektdatei an, wenn ein Projekt aus der Vorlage erstellt wird.|
|`IgnoreProjectParameter`|Optionales Attribut.<br /><br /> Gibt an, ob das Projekt der aktuellen Projekt Mappe hinzugefügt werden soll. Wenn der Wert des benutzerdefinierten Parameters "$*mycustomparameter*$" in der Parameter Ersetzungs Datei vorhanden ist, wird das Projekt erstellt, aber nicht als Teil der aktuell geöffneten Projekt Mappe hinzugefügt.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Ordner](../extensibility/folder-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt einen Ordner an, der dem Projekt hinzugefügt werden soll.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt eine Datei an, die einem Projekt hinzugefügt werden soll.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element.|

## <a name="remarks"></a>Bemerkungen
 `Project` ist ein optionales untergeordnetes Element von `TemplateContent`.

 Das `Project` -Element wird zur Angabe eines Projekts verwendet und ist daher nur in Projektvorlagen gültig.

 `Project` Elemente können untergeordnete Elemente des [Ordners](../extensibility/folder-element-visual-studio-project-templates.md) oder [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) -Elemente enthalten, aber keine Kombination aus und untergeordneten `Folder` `ProjectItem` Elementen.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] benennt den Projekt Dateinamen automatisch basierend auf dem Namen um, der vom Benutzer im Dialogfeld **Neues Projekt** eingegeben wurde. Verwenden Sie das- `TargetFileName` Attribut, wenn Sie einen alternativen Dateinamen für Projektdateien angeben möchten, die mit der Vorlage erstellt werden.

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
- [ProjectItem-Element (Visual Studio-Projektvorlagen)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Folder-Element (Visual Studio-Projektvorlagen)](../extensibility/folder-element-visual-studio-project-templates.md)
