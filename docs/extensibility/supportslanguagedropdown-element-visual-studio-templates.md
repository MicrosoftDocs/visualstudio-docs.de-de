---
title: SupportsLanguageDropDown-Element (Visual Studio-Vorlagen)
titleSuffix: ''
description: Informieren Sie sich über das SupportsLanguageDropDown-Element und darüber, wie es angibt, ob die Webelement Vorlage für mehrere Sprachen identisch ist, und ob die language-Option aktiviert ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b02e4b88b22257e7187e334f8c1064b68c6ef49d
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901725"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown-Element (Visual Studio-Vorlagen)

Gibt an, ob die Webelement Vorlage für mehrere Sprachen identisch ist und ob die **sprach** Option im Dialogfeld **Neues Element hinzufügen** aktiviert ist.

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>Syntax

```xml
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert

 Ein Textwert ist erforderlich.

 Der Text muss entweder `true` oder lauten `false` und gibt an, ob die **sprach** Option im Dialogfeld **Neues Element hinzufügen** verfügbar ist.

## <a name="remarks"></a>Hinweise

 `SupportsLanguageDropDown` ist ein optionales Element. Standardwert: `false`.

 Das- `SupportsLanguageDropDown` Element ist nur für Webelement Vorlagen verfügbar.

 Wenn der Wert für dieses Element auf festgelegt ist `true` , ist die Element Vorlage für alle Programmiersprachen identisch, und die **sprach** Option ist im Dialogfeld **Neues Element hinzufügen** aktiviert. Mit dieser Option können Sie die Programmiersprache des neuen Elements auswählen, das Sie aus der Vorlage erstellen möchten.

## <a name="example"></a>Beispiel

 Im folgenden Beispiel wird angegeben, dass die Dropdown Option **Sprache** angezeigt werden soll.

```xml
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
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
