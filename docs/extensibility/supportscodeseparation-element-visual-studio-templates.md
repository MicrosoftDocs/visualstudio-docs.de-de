---
title: SupportsCodeSeparation-Element (Visual Studio-Vorlagen)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4dfdf3244d09c5f3418c5403a32570c382c5365c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038464"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation-Element (Visual Studio-Vorlagen)
Gibt an, ob das Kontrollkästchen **Code in separaten Dateien platzieren** im Dialogfeld **Neues Element hinzufügen** aktiviert ist.

 \<VSTemplate> \<TemplateData>
 \<SupportsCodeSeparation>

## <a name="syntax"></a>Syntax

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie Sie im Dialogfeld **Neues Projekt** oder **Neues Element** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text muss entweder `true` oder lauten `false` , was angibt, ob das Kontrollkästchen **Code in separaten Dateien platzieren** im Dialogfeld **Neues Element hinzufügen** aktiviert ist.

## <a name="remarks"></a>Bemerkungen
 `SupportsCodeSeparation` ist ein optionales Element. Der Standardwert ist `false`.

 Das- `SupportsCodeSeparation` Element ist nur für Webelement Vorlagen verfügbar.

 Durch die Trennung von Code oder das Code Behind-Seiten Modell können Sie das Markup in einer Datei und den Programmiercode in einer anderen Datei speichern. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] und andere .NET-Sprachen verwenden dieses Modell.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird angegeben, dass die Option **Code in separaten Dateien platzieren** angezeigt werden soll.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
