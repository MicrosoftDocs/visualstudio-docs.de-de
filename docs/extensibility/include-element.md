---
title: Include-Element | Microsoft-Dokumentation
description: Das Include-Element gibt eine Datei an, die sich im angegebenen Includepfad befinden kann, damit Sie in die aktuelle Datei eingefügt werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6d718178bf7490d29c0668d892add4c302b8925a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893632"
---
# <a name="include-element"></a>Include-Element
Das Include-Element gibt eine Datei an, die sich im angegebenen Includepfad befinden kann, damit Sie in die aktuelle Datei eingefügt werden kann.  Alle definierten Symbole und Typen werden Teil des kompilierten Ergebnisses.

## <a name="syntax"></a>Syntax

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|href|Erforderlich. Der Pfad zur Header Datei:<br /><br /> href = "stdidcmd. h"|
|Bedingung|Dies ist optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|Keine.|Keine|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Commandtable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen – d. h. Menü Elemente, Menüs, Symbolleisten und Kombinations Felder –, die ein VSPackage für die IDE bereitstellt.|

## <a name="example"></a>Beispiel

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Weitere Informationen
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
