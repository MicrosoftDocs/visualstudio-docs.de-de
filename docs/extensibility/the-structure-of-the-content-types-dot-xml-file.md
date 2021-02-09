---
title: Die Struktur der [Content_Types]. XML-Datei | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Struktur der Inhaltstypen Datei, die Informationen zu den Arten von Inhalten in einem VSIX-Paket enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38348661946be3894332d49177f972410563b716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895206"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Die Struktur der [Content_types].xml-Datei
Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio verwendet die Datei [Content_Types]. XML, um das Paket zu installieren, aber die Datei selbst wird nicht installiert.

> [!NOTE]
> Obwohl sich dieses Thema nur auf [content_type]. XML-Dateien bezieht, die in VSIX-Paketen verwendet werden, ist der Dateityp [Content_Types]. XML Teil des OPC-Standards *(Open Packaging Conventions)* . Weitere Informationen finden Sie unter [OPC: ein neuer Standard zum Verpacken Ihrer Daten](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) auf der MSDN-Website.

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden das root-Element und seine Attribute und untergeordneten Elemente beschrieben.

### <a name="root-element"></a>Root-Element

|Element|Beschreibung|
|-------------|-----------------|
|`Types`|Enthält untergeordnete Elemente, die die Dateitypen im VSIX-Paket auflisten.|

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|`Xmlns`|(Erforderlich) Der Speicherort des Schemas, das für diese [Content_Types]. XML-Datei verwendet wird.|

### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen

| Wert | Beschreibung |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Der Speicherort des Inhaltstypen Schemas. |

### <a name="child-elements"></a>Untergeordnete Elemente
 Das `Types`-Element kann eine beliebige Anzahl von `Default`-Elementen enthalten.

|Element|Beschreibung|
|-------------|-----------------|
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp im Paket muss über ein eigenes- `Default` Element verfügen.|

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|`Extension`|Die Dateinamenerweiterung einer Datei im VSIX-Paket.|
|`ContentType`|Beschreibt die Art des Inhalts, der der Dateinamenerweiterung zugeordnet ist.|

### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen
 In Visual Studio werden die folgenden `ContentType` Werte für die zugeordneten `Extension` Typen erkannt.

|Erweiterung|ContentType|
|---------------|-----------------|
|txt|text/plain|
|pkgdef|text/plain|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm oder HTML|text/html|
|RTF|Anwendung/RTF|
|pdf|application/pdf|
|GIF|image/gif|
|JPG oder JPEG|Bild/jpg|
|tiff|image/tiff|
|VSIX|application/zip|
|zip|application/zip|
|DLL-Datei|application/octet-stream|
|alle anderen Dateitypen|application/octet-stream|

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung
 In der folgenden [Content_Types]. XML-Datei wird ein typisches VSIX-Paket beschrieben.

### <a name="code"></a>Code

```
<?xml version="1.0" encoding="utf-8" ?>
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
    <Default Extension="vsixmanifest" ContentType="text/xml" />
    <Default Extension="dll" ContentType="application/octet-stream" />
    <Default Extension="png" ContentType="application/octet-stream" />
    <Default Extension="txt" ContentType="text/plain" />
    <Default Extension="pkgdef" ContentType="text/plain" />
</Types>
```

## <a name="see-also"></a>Siehe auch
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)
- [VSIX-Erweiterungs Schema 1,0-Referenz](/previous-versions/dd393700(v=vs.110))
- [OPC: ein neuer Standard zum Verpacken von Daten](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)