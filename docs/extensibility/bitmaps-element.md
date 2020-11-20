---
title: Bitmaps-Element | Microsoft-Dokumentation
description: Das Bitmaps-Element gruppiert ein oder mehrere Bitmap-Elemente. Dieser Artikel enthält ein Beispiel für das Bitmaps-Element.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd3222e24c6e90380ec9c5836bed583ba95eaa68
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974578"
---
# <a name="bitmaps-element"></a>Bitmaps-Element
Gruppiert [Bitmap-Element](../extensibility/bitmap-element.md) Elemente.

## <a name="syntax"></a>Syntax

```
<Bitmaps>
  <Bitmap>... </Bitmap>
  <Bitmap>... </Bitmap>
</Bitmaps>
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
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert Bitmap-Elemente.|
|[Bitmap-Element](../extensibility/bitmap-element.md)|Definiert eine Bitmap.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Commands-Element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der VSPackage-Symbolleiste dar.|

## <a name="example"></a>Beispiel

```
<Bitmaps>
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
    usedList="1, 2, 3, 4"/>
</Bitmaps>
```

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
