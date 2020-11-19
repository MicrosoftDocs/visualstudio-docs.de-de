---
title: References-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das References-Element und darüber, wie die Assemblyverweise gruppiert werden, die die Vorlage Projekten hinzufügt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2576a56bf223fd1b3a1ba4903595cc25144011ec
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903743"
---
# <a name="references-element-visual-studio-templates"></a>References-Element (Visual Studio-Vorlagen)
Gruppiert die Assemblyverweise, die von der Vorlage Projekten hinzugefügt werden.

 \<VSTemplate> \<TemplateContent>
 \<References>

## <a name="syntax"></a>Syntax

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Referenz](../extensibility/reference-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Assemblyverweis an, der hinzugefügt wird, wenn das Element einem Projekt hinzugefügt wird. Es muss ein oder mehrere- `Reference` Elemente in einem-Element vorhanden sein `References` .|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage an.|

## <a name="remarks"></a>Hinweise
 `References` ist ein optionales untergeordnetes Element von `TemplateContent`.

 Das `Reference` -Element und das- `References` Element können nur in *. vstemplate* -Dateien mit dem- `Type` Attribut Wert verwendet werden `Item` .

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht das-Element einer Element `TemplateContent` Vorlage. Dieses XML fügt Verweise auf die *System.dll* und *System.Data.dll* Assemblys hinzu.

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
