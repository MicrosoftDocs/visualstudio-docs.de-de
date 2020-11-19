---
title: Sdkreferenzierelement (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das sdkreferenzierungselement und darüber, wie es angibt, dass die Element Vorlage eine SDK-Referenz verwendet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a1272a4765559fcfcde1aa60c57099b5d707f46
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901686"
---
# <a name="sdkreference-element-visual-studio-templates"></a>SDKReference-Element (Visual Studio-Vorlagen)
Gibt an, dass die Elementvorlage eine SDK-Referenz verwendet.

## <a name="syntax"></a>Syntax

```xml
<VSTemplate>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>SDKname</SDKReference>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Referenz](../extensibility/reference-element-visual-studio-templates.md)|Gibt den Assemblyverweis an, der hinzugefügt wird, wenn das Element einem Projekt hinzugefügt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

## <a name="remarks"></a>Hinweise
 Dieser Text gibt die SDK-Referenz an, die einem Projekt beim Instanziieren der Elementvorlage hinzugefügt werden soll.

```xml
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
    <TemplateData> . . . </TemplateData>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>
...
```

## <a name="see-also"></a>Weitere Informationen
- [References-Element (Visual Studio-Vorlagen)](../extensibility/references-element-visual-studio-templates.md)
- [Reference-Element (Visual Studio-Vorlagen)](../extensibility/reference-element-visual-studio-templates.md)
- [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
- [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
