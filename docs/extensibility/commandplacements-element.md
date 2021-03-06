---
title: Commandplacement-Element | Microsoft-Dokumentation
description: Das commandplacement-Element gruppiert commandplacement-Elemente und andere commandplacement-Gruppierungen. Das commandplacement-Element ist optional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c43f2063062d96b8ab635e3d9786aead4b4c150
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889043"
---
# <a name="commandplacements-element"></a>Commandplacement-Element
Das commandplacement-Element gruppiert commandplacement-Elemente und andere commandplacement-Gruppierungen.

 Das commandplacement-Element ist optional. Wenn keine Befehle, Gruppen oder Menüs an einem sekundären Speicherort enthalten sein müssen, müssen Sie diesen Abschnitt nicht in die *vsct* -Datei einschließen.

## <a name="syntax"></a>Syntax

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|Bedingung|Dies ist optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|CommandPlacements|Gruppiert commandplacement-Elemente und andere commandplacement-Gruppierungen.|
|[Commandplacement-Element](../extensibility/commandplacement-element.md)|Ermöglicht das Einschließen von Schaltflächen, Gruppen und Menüs in mehr als eine Gruppe oder ein Menü.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Commandtable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen.|

## <a name="example"></a>Beispiel

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Weitere Informationen
- [Commandplacement-Element](../extensibility/commandplacement-element.md)
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
