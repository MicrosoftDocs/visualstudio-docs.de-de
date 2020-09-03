---
title: Extern-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711485"
---
# <a name="extern-element"></a>Extern-Element
Das extern-Element verweist auf alle externen Header Dateien (*. h*), die zur Kompilierzeit mit der *vsct* -Datei zusammengeführt werden sollen. Die zusammen zuführenden Dateien müssen sich auf dem Includepfad befinden, der dem VSCT-Compiler übergeben wird oder auf den von einem [include-Element](../extensibility/include-element.md)verwiesen wird. Die Dateien können andere *vsct* -Dateien oder C++-Header Dateien sein.

 Definitionen in Header Dateien müssen das Format "#define [Symbol] [Wert]" aufweisen. der Wert ist möglicherweise ein anderes Symbol, wenn er zuvor definiert wurde. Definitionen können in Bedingungs Anweisungen von Befehls Elementen verwendet werden. Jedes Symbol, das nicht tatsächlich verwendet wird, wird verworfen.

 Commandtable-Element extern-Element

## <a name="syntax"></a>Syntax

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|href|Erforderlich. Der Pfad zur Header Datei:<br /><br /> href = "stdidcmd. h"|
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Optional. Die Standardsprache aller [\<Strings>](../extensibility/strings-element.md) Elemente in der Befehls Tabelle:<br /><br /> language = "en-US"|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Keine|Keine|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Commandtable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen – d. h. Menü Elemente, Menüs, Symbolleisten und Kombinations Felder –, die ein VSPackage für die IDE bereitstellt.|

## <a name="example"></a>Beispiel

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>Weitere Informationen
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
