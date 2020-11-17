---
title: ProjectItem-Element (Visual Studio-Projektvorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das ProjectItem-Element für Projektvorlagen und darüber, wie es verschiedene Attribute annimmt, je nachdem, ob die Vorlage für ein Projekt oder ein Element vorgesehen ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2d41fe83b440e2a3b4bfebd4fac6f5d06094a4
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671323"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem-Element (Visual Studio-Projektvorlagen)
Gibt eine Datei an, die in der Projektvorlage enthalten ist.

> [!NOTE]
> Das- `ProjectItem` Element akzeptiert verschiedene Attribute, je nachdem, ob die Vorlage für ein Projekt oder ein Element vorgesehen ist. In diesem Thema wird das- `ProjectItem` Element für-Projektvorlagen erläutert. Eine Erläuterung des- `ProjectItem` Elements für Element Vorlagen finden Sie unter [ProjectItem-Element (Visual Studio-Element Vorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<ProjectItem>

## <a name="syntax"></a>Syntax

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attributes

| Attribut | Beschreibung |
|---------------------| - |
| `TargetFileName` | Optionales Attribut.<br /><br /> Gibt den Namen und den Pfad des Projekt Elements an, wenn ein Projekt aus der Vorlage erstellt wird. Dieses Attribut ist nützlich zum Erstellen einer Verzeichnisstruktur, die sich von der Verzeichnisstruktur in der *ZIP* -Datei der Vorlage unterscheidet, oder für die Verwendung von Parameter Ersetzung zum Erstellen eines Element namens. |
| `ReplaceParameters` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element über Parameterwerte verfügt, die beim Erstellen eines Projekts aus der Vorlage ersetzt werden müssen. Der Standardwert ist `false`. |
| `OpenInEditor` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element in seinem entsprechenden Editor in geöffnet werden soll, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Wenn ein Projekt aus der Vorlage erstellt wird.<br /><br /> Das `OpenInWebBrowser` -Attribut und das- `OpenInHelpBrowser` Attribut werden bei einem Element mit dem- `OpenInEditor` Wert ignoriert `true` .<br /><br /> Der Standardwert ist `false`. |
| `OpenInWebBrowser` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element im Webbrowser geöffnet werden soll, wenn ein Projekt aus der Vorlage erstellt wird.<br /><br /> Nur HTML-Dateien und Textdateien, die für das Projekt lokal sind, können im Webbrowser geöffnet werden. Externe URLs können nicht mit diesem Attribut geöffnet werden.<br /><br /> Der Standardwert ist `false`. |
| `OpenInHelpBrowser` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element im Help Viewer geöffnet werden soll, wenn ein Projekt aus der Vorlage erstellt wird.<br /><br /> Nur HTML-Dateien und Textdateien, die für das Projekt lokal sind, können im Hilfe Browser geöffnet werden. Externe URLs können nicht mit diesem Attribut geöffnet werden.<br /><br /> Der Standardwert ist `false`. |
| `OpenOrder` | Optionales Attribut.<br /><br /> Gibt einen numerischen Wert an, der die Reihenfolge darstellt, in der Elemente in den jeweiligen Editoren geöffnet werden. Alle Werte müssen ein Vielfaches von 10 sein. Elemente mit höheren `OpenOrder` Werten werden zuerst geöffnet. |

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Gibt die Dateien oder Verzeichnisse an, die dem Projekt hinzugefügt werden sollen.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Ein `string` , der den Namen oder Pfad zu einer Datei in der *ZIP* -Datei der Vorlage darstellt.

## <a name="remarks"></a>Hinweise
 `ProjectItem` ist ein optionales untergeordnetes Element von `Project` .

 Das- `TargetFileName` Attribut kann verwendet werden, um eine andere Verzeichnisstruktur als die Verzeichnisstruktur in der *ZIP* -Datei der Vorlage zu erstellen. Wenn z. b. die Datei " *MyFile. vb* " im Stammverzeichnis der *ZIP* -Datei der Vorlage vorhanden ist, Sie jedoch möchten, dass die Datei in einem Verzeichnis mit dem Namen " *CustomFiles* " in allen aus der Vorlage erstellten Projekten platziert wird, verwenden Sie den folgenden XML-Code:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 Das- `TargetFileName` Attribut kann auch zum Umbenennen von Dateien verwendet werden, die in ihren Dateinamen internationale Zeichen enthalten. Beispielsweise kann eine template *. zip* -Datei keine Dateinamen mit Unicode-Zeichen enthalten. Daher muss die Datei umbenannt werden, bevor Sie in eine *ZIP* -Datei komprimiert werden kann. Das- `TargetFileName` Attribut kann verwendet werden, um den Dateinamen wieder auf den ursprünglichen Unicode-Dateinamen festzulegen.

 Das- `TargetFileName` Attribut kann auch zum Umbenennen von Dateien mit Parametern verwendet werden. Im folgenden Verfahren wird erläutert, wie Sie die Datei *MyFile. vb*, die im Stammverzeichnis der *ZIP* -Datei der Vorlage vorhanden ist, in einen Dateinamen auf Grundlage des Projekt namens umbenennen.

### <a name="to-rename-files-with-parameters"></a>So benennen Sie Dateien mit Parametern um

1. Verwenden Sie den folgenden XML-Code in der *VSTEMPLATE* -Datei:

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Öffnen Sie die Projektdatei (*vbproj* für ein [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Projekt) in einem Text-Editor oder in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. Suchen Sie die Zeile in der Projektdatei, die in etwa wie folgt aussieht:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Ersetzen Sie die Codezeile durch den folgenden XML-Code:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Wenn ein Projekt aus dieser Vorlage erstellt wird, basiert der Dateiname auf dem Namen, den der Benutzer im Dialogfeld **Neues Projekt** eingegeben hat, wobei alle unsicheren Zeichen und Leerzeichen entfernt wurden. Weitere Informationen finden Sie unter [Vorlagen Parameter](../ide/template-parameters.md).

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
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
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
- [Vorlagenparameter](../ide/template-parameters.md)
- [ProjectItem-Element (Visual Studio-Element Vorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)
