---
title: Icon-Element | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Icon-Element, das in Visual Studio-IDE-Erweiterungen verwendete Symbole darstellt, das Attribute für die verwendete Bitmap und den Slot im bitmapstrip umfasst.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ed5a4f64a2c80cfdc61b37a6a8bac72adc97a33
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993600"
---
# <a name="icon-element"></a>Icon-Element
Das GUID-Attribut des Symbols-Tags ist die GUID einer definierten Bitmap. Das- `id` Attribut wählt den Slot im bitmapstrip aus. Dieses Element ist optional. Wenn dieses Element nicht enthalten ist, wird der Wert von **guidofficeicon: msotcidnoicon** impliziert.

## <a name="syntax"></a>Syntax

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. Die GUID einer definierten Bitmap.|
|id|Erforderlich. Wählt den Slot im bitmapstrip aus.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Keine.|Keine.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Buttons-Element](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Weitere Informationen
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
