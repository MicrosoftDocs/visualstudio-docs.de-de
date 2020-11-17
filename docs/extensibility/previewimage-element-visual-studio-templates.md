---
title: PreviewImage-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das PreviewImage-Element und darüber, wie es den Dateinamen für das Vorschaubild angibt, das im Dialogfeld Neues Projekt oder neues Element hinzufügen angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 326588259203224d3f70b505af8437af22930faa
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672345"
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage-Element (Visual Studio-Vorlagen)
Gibt das Vorschaubild (als Dateiname) für das Vorschaubild an, das im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.

 \<VSTemplate> \<TemplateData>
 \<PreviewImage>

## <a name="syntax"></a>Syntax

```
<PreviewImage>"filename"</PreviewImage>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie Sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text muss eine Zeichenfolge sein, die einen Dateinamen darstellt.

## <a name="remarks"></a>Hinweise
 `PreviewImage` ist ein optionales Element.

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
