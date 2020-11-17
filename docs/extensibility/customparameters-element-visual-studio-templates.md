---
title: CustomParameters-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das CustomParameters-Element und darüber, wie die benutzerdefinierten Parameter gruppiert werden, die an den Vorlagen-Assistenten übergeben werden, wenn der Assistent Parameter Ersetzungen vornimmt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c78c8a038df33d9b548229966402d0058f53144
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671478"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters-Element (Visual Studio-Vorlagen)
Gruppiert die benutzerdefinierten Parameter, die an den Vorlagen-Assistenten übergeben werden, wenn der Assistent Parameter Ersetzungen vornimmt.

## <a name="syntax"></a>Syntax

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Enthält einen benutzerdefinierten Parameternamen und-Wert, der verwendet werden soll, wenn ein Projekt oder ein Element aus der Vorlage erstellt wird. Es kann keine oder mehrere `CustomParameter`-Elemente in einem `CustomParameters`-Element geben.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage an.|

## <a name="remarks"></a>Bemerkungen

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird gezeigt, wie mehrere benutzerdefinierte Parameter in einer Vorlage verwendet werden. Wenn ein Projekt oder Element aus einer Vorlage mit den folgenden benutzerdefinierten Parametern erstellt wird, werden alle Instanzen von `$color1$` und `$color2$` in den Vorlagen Dateien durch `Red` `Blue` bzw. ersetzt.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Siehe auch
- [CustomParameter-Element (Visual Studio-Vorlagen)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
