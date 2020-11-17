---
title: CustomParameter-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das CustomParameter-Element und darüber, wie es einen benutzerdefinierten Parameternamen und-Wert enthält, die beim Erstellen eines Projekts oder Elements aus der Vorlage verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c118bbc85064beb10b99641f0803af7af12d56
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671948"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter-Element (Visual Studio-Vorlagen)
Enthält einen benutzerdefinierten Parameternamen und-Wert, der verwendet werden soll, wenn ein Projekt oder ein Element aus der Vorlage erstellt wird.

## <a name="syntax"></a>Syntax

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Name`|Erforderlich. Der Name des Parameters. Das Format für Parameter ist "$*Name*$".|
|`Value`|Erforderlich. Der Ersatzwert für den Parameter.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Gruppiert die benutzerdefinierten Parameter, die an den Vorlagen-Assistenten übergeben werden, wenn der Assistent Parameter Ersetzungen vornimmt.|

## <a name="remarks"></a>Hinweise
 Wenn eine Vorlage `CustomParameter` Elemente enthält, wird jede Instanz, die das Attribut enthält, durch `Name` das- `Value` Attribut in den erstellten Projekt-oder Element Dateien ersetzt.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird gezeigt, wie mehrere benutzerdefinierte Parameter in einer Vorlage verwendet werden. Wenn ein Projekt oder Element aus einer Vorlage mit den folgenden benutzerdefinierten Parametern erstellt wird, werden alle Instanzen von `$color1$` und `$color2$` in den Vorlagen Dateien durch `Red` `Blue` bzw. ersetzt.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Siehe auch
- [CustomParameters-Element (Visual Studio-Vorlagen)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
