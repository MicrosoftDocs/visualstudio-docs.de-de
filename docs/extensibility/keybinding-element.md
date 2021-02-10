---
title: KeyBinding-Element | Microsoft-Dokumentation
description: Das KeyBinding-Element gibt Tastenkombinationen für die Befehle an. Befehlen können sowohl einfache als auch Dual-Key-Bindungen zugeordnet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ce96da36a8c6eff0fda71d8a5d077721876ab8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943347"
---
# <a name="keybinding-element"></a>KeyBinding-Element
Das KeyBinding-Element gibt Tastenkombinationen für die Befehle an.

 Befehlen können sowohl einfache als auch Dual-Key-Bindungen zugeordnet werden. Ein Beispiel für eine einzelne tastenbindung ist **STRG** + **S** für den **Save** -Befehl. Dual-Key-Bindungen erfordern zwei aufeinander folgende Tastenkombinationen, um einen Befehl zu initiieren. Ein Beispiel für eine Dual-Key-Bindung ist <strong>STRG *+</strong> k <strong>,</strong>STRG <strong>+</strong> k** zum Festlegen eines Lesezeichens.

## <a name="syntax"></a>Syntax

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich.|
|id|Erforderlich.|
|Editor|Erforderlich. Die Editor-GUID gibt den Bearbeitungs Kontext an, für den diese Tastenkombination aktiviert wird. Der Wert des globalen Bindungs Bereichs ist "guidVSStd97".|
|key1|Erforderlich. Zu den gültigen Werten gehören alle typbaren alphanumerischen Werte und zweistellige hexadezimal Werte, denen 0x und [VK_constants](/windows/desktop/inputdev/virtual-key-codes)vorangestellt sind.|
|mod1|Dies ist optional. Eine beliebige Kombination von **STRG**, **alt** und **UMSCHALT** durch Leerzeichen voneinander getrennt.|
|Schlüssel2|Dies ist optional. Zu den gültigen Werten gehören alle typbaren alphanumerischen Werte und zweistellige hexadezimal Werte, denen 0x und [VK_constants](/windows/desktop/inputdev/virtual-key-codes)vorangestellt sind.|
|mod2|Dies ist optional. Eine beliebige Kombination von **STRG**, **alt** und **UMSCHALT** durch Leerzeichen voneinander getrennt.|
|Emulator|Dies ist optional.|
|Bedingung|Dies ist optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Parent||
|Anmerkung||

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[KeyBinding-Element](../extensibility/keybindings-element.md)|Gruppiert KeyBinding-Elemente und andere keybindungs Gruppierungen.|

## <a name="example"></a>Beispiel

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Weitere Informationen
- [KeyBinding-Element](../extensibility/keybindings-element.md)
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
