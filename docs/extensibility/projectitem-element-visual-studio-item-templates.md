---
title: ProjectItem-Element (Visual Studio-Element Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das ProjectItem-Element für Element Vorlagen und darüber, wie es verschiedene Attribute annimmt, je nachdem, ob die Vorlage für ein Projekt oder ein Element vorgesehen ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 431f1d5f81827b47b57a53dbe411a2a7e8a57941
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672332"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem-Element (Visual Studio-Element Vorlagen)
Gibt eine Datei an, die in der Element Vorlage enthalten ist.

> [!NOTE]
> Das- `ProjectItem` Element akzeptiert verschiedene Attribute, je nachdem, ob die Vorlage für ein Projekt oder ein Element vorgesehen ist. In diesem Thema wird das- `ProjectItem` Element für Item erläutert. Eine Erläuterung des- `ProjectItem` Elements für Projektvorlagen finden Sie unter [ProjectItem-Element (Visual Studio-Projektvorlagen)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate> \<TemplateContent>
 \<ProjectItem>

## <a name="syntax"></a>Syntax

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attributes

| Attribut | Beschreibung |
|---------------------| - |
| `SubType` | Optionales Attribut.<br /><br /> Gibt den Untertyp eines Elements in einer Element Vorlage mit mehreren Dateien an. Dieser Wert wird verwendet, um den Editor zu bestimmen, der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Öffnen des Elements verwendet. |
| `CustomTool` | Optionales Attribut.<br /><br /> Legt das CustomTool für das Element in der Projektdatei fest. |
| `ItemType` | Optionales Attribut.<br /><br /> Legt den ItemType für das Element in der Projektdatei fest. |
| `ReplaceParameters` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element über Parameterwerte verfügt, die beim Erstellen eines Projekts aus der Vorlage ersetzt werden müssen. Der Standardwert ist `false`. |
| `TargetFileName` | Optionales Attribut.<br /><br /> Gibt den Namen des Elements an, das aus der Vorlage erstellt wird. Dieses Attribut eignet sich für die Verwendung von Parameter Ersetzung zum Erstellen eines Element namens. |

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage an.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Ein `string` , der den Namen einer Datei in der *ZIP* -Datei der Vorlage darstellt.

## <a name="remarks"></a>Hinweise
 `ProjectItem` ist ein optionales untergeordnetes Element von `TemplateContent` .

 Das- `TargetFileName` Attribut kann zum Umbenennen von Dateien mit Parametern verwendet werden. Wenn z. b. die Datei " *MyFile. vb* " im Stammverzeichnis der *ZIP* -Datei der Vorlage vorhanden ist, Sie jedoch möchten, dass die Datei basierend auf dem Dateinamen, der vom Benutzer im Dialogfeld " **Neues Element hinzufügen** " angegeben wird, benannt wird, verwenden Sie den folgenden XML-Code:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Wenn ein Element aus dieser Vorlage erstellt wird, basiert der Dateiname auf dem Namen, den der Benutzer im Dialogfeld **Neues Element hinzufügen** eingegeben hat. Dies ist beim Erstellen von Element Vorlagen mit mehreren Dateien hilfreich. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Element Vorlagen](../ide/how-to-create-multi-file-item-templates.md) und [Vorlagen Parametern](../ide/template-parameters.md)mit mehreren Dateien.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für die Standardelement Vorlage für eine- [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Klasse veranschaulicht.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [How to: Erstellen von Elementvorlagen mit mehreren Dateien](../ide/how-to-create-multi-file-item-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
