---
title: Bitmap-Element | Microsoft-Dokumentation
description: Das Bitmap-Element definiert eine Bitmap. Die Bitmap wird entweder aus einer Ressource oder aus einer Datei geladen. Dieser Artikel enthält ein Beispiel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe9002c3da63e9570819588035395780715e1d64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941865"
---
# <a name="bitmap-element"></a>Bitmap-Element
Definiert eine Bitmap. Die Bitmap wird entweder aus einer Ressource oder aus einer Datei geladen.

## <a name="syntax"></a>Syntax

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. GUID des GUID-/ID-befehlsbezeichners.<br /><br /> Das GUID-Attribut für eine Bitmap ist keinem VSPackage oder einer anderen Befehlsgruppe zugeordnet.  Er sollte für die Bitmapdefinition eindeutig sein und sollte nicht für andere Zwecke verwendet werden.|
|resID|ID des GUID-/ID-befehlsbezeichners. Entweder die Resid oder das href-Attribut ist erforderlich.<br /><br /> Das Attribut Resid ist eine ganzzahlige Ressourcen-ID, die den bitmapstrip bestimmt, der während der Zusammenführung der Befehls Tabelle geladen werden soll.  Beim Laden der Befehls Tabelle werden die durch die Ressourcen-ID angegebenen Bitmaps aus der Ressource des gleichen Moduls geladen.|
|usedlist|Erforderlich, wenn das Resid-Attribut vorhanden ist. Wählt die verfügbaren Bilder in der bitmapleiste aus.|
|href|Der Pfad zur Bitmap. Entweder die Resid oder das href-Attribut ist erforderlich.<br /><br /> Der Include-Pfad wird nach der angezeigten Bilddatei durchsucht, die in die resultierende Binärdatei eingebettet ist.  Während der Zusammenführung der Befehls Tabelle wird das Image kopiert, und es ist keine zusätzliche Ressourcen Suche oder-Auslastung erforderlich.  Wenn das usedlist-Attribut nicht vorhanden ist, sind alle Images im Strip verfügbar. **Hinweis:**  Bilder können in einem von mehreren Formaten angegeben werden, die *BMP*, *PNG* und *GIF* enthalten.  Frühere Versionen des Compilers unterstützten keine 32-Bit-Bitmapbilder, die Alpha Informationen für partielle Transparenz enthielten. Die Problem Umgehung für diese Versionen besteht darin, das *PNG* -Format zu verwenden.|
|Bedingung|Dies ist optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert Bitmap-Elemente.|

## <a name="example"></a>Beispiel

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Weitere Informationen
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
