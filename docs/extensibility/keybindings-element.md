---
title: KeyBinding-Element | Microsoft-Dokumentation
description: Das KeyBinding-Element gruppiert KeyBinding-Elemente und andere keybindungs Gruppierungen. Dieser Artikel enthält ein Beispiel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- KeyBindings
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBindings element (VSCT XML schema)
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 928637d8103a69eafd3bda4446a55bb7523f83a8
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616090"
---
# <a name="keybindings-element"></a>KeyBinding-Element
Das KeyBinding-Element gruppiert KeyBinding-Elemente und andere keybindungs Gruppierungen.

## <a name="syntax"></a>Syntax

```xml
<KeyBindings>
  <KeyBinding>... </KeyBinding>
  <KeyBinding>... </KeyBinding>
</KeyBindings>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[KeyBinding-Element](../extensibility/keybinding-element.md)|Gibt Tastenkombinationen für die Befehle an.|
|[Tasten Zuordnungen](../extensibility/keybindings-element.md)|Gruppiert KeyBinding-Elemente und andere keybindungs Gruppierungen.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Commandtable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen.|

## <a name="example"></a>Beispiel

```xml
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Siehe auch
- [KeyBinding-Element](../extensibility/keybinding-element.md)
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
