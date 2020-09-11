---
title: Die Struktur der [Content_Types]. XML-Datei | Microsoft-Dokumentation
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e96af4936f27d869409a7215c720d9bb64e4128
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012516"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Die Struktur der [Content_types].xml-Datei
Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio verwendet die Datei [Content_Types]. XML, um das Paket zu installieren, aber die Datei selbst wird nicht installiert.

> [!NOTE]
> Obwohl sich dieses Thema nur auf [content_type]. XML-Dateien bezieht, die in VSIX-Paketen verwendet werden, ist der Dateityp [Content_Types]. XML Teil des OPC-Standards *(Open Packaging Conventions)* . Weitere Informationen finden Sie unter [OPC: ein neuer Standard zum Verpacken Ihrer Daten](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) auf der MSDN-Website.

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden das root-Element und seine Attribute und untergeordneten Elemente beschrieben.

### <a name="root-element"></a>Root-Element

|Element|BESCHREIBUNG|
|-------------|-----------------|
|`Types`|Enthält untergeordnete Elemente, die die Dateitypen im VSIX-Paket auflisten.|

### <a name="attributes"></a>Attributes

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`Xmlns`|(Erforderlich) Der Speicherort des Schemas, das für diese [Content_Types]. XML-Datei verwendet wird.|

### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen

| Wert | BESCHREIBUNG |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Der Speicherort des Inhaltstypen Schemas. |

### <a name="child-elements"></a>Untergeordnete Elemente
 Das `Types`-Element kann eine beliebige Anzahl von `Default`-Elementen enthalten.

|Element|BESCHREIBUNG|
|-------------|-----------------|
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp im Paket muss über ein eigenes- `Default` Element verfügen.|

### <a name="attributes"></a>Attributes

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`Extension`|Die Dateinamenerweiterung einer Datei im VSIX-Paket.|
|`ContentType`|Beschreibt die Art des Inhalts, der der Dateinamenerweiterung zugeordnet ist.|

### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen
 In Visual Studio werden die folgenden `ContentType` Werte für die zugeordneten `Extension` Typen erkannt.

|Durchwahl|ContentType|
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

### <a name="description"></a>BESCHREIBUNG
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