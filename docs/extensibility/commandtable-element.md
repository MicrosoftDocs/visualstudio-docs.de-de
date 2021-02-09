---
title: Commandtable-Element | Microsoft-Dokumentation
description: Commandtable ist das Stamm Element der vsct-Datei, das das Layout und den Typ der Befehle definiert, die ein VSPackage für die IDE bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79441880091088cf1d953c8925273e801dc0860d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887353"
---
# <a name="commandtable-element"></a>Commandtable-Element
Commandtable ist das Stamm Element der *vsct* -Datei. Dies ist die Datei, die das tatsächliche Layout und den Typ der Befehle definiert, die ein VSPackage für die IDE bereitstellt. Befehle können Menü Elemente, Menüs, Symbolleisten und Kombinations Felder enthalten. Weitere Informationen finden Sie unter [Visual Studio-Befehls Tabellen Dateien (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="syntax"></a>Syntax

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

| attribute | Beschreibung |
|-----------| - |
| xmlns | Erforderlich. XML-Namespaces:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = " <http://www.w3.org/2001/XMLSchema> " |
| language | Dies ist optional. Das Language-Attribut kann verwendet werden, um die Standardsprache aller \<Strings> Elemente in der Befehls Tabelle anzugeben.  Wenn die Sprache nicht angegeben wird, wird die Sprache des aktuellen Prozesses verwendet:<br /><br /> language = "en-US" |

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Extern-Element](../extensibility/extern-element.md)|Dies ist optional. Enthält Präprozessordirektiven für den Compiler.|
|[Include-Element](../extensibility/include-element.md)|Dies ist optional. Enthält Pfade zu allen Dateien, die in die Kompilierung eingeschlossen werden sollen.|
|[Define-Element](../extensibility/define-element.md)|Dies ist optional. Definiert ein Symbol anhand seines Namens und Werts.|
|[Commands-Element](../extensibility/commands-element.md)|Dies ist optional. Das übergeordnete Element, das alle Befehle für das VSPackage definiert, das alle anderen Elemente enthält.|
|[Commandplacement-Element](../extensibility/commandplacements-element.md)|Dies ist optional. Definiert, wo in der Befehlsleiste die Befehle platziert werden sollen.|
|[Visibilityschränkt-Element](../extensibility/visibilityconstraints-element.md)|Dies ist optional. Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|
|[KeyBinding-Element](../extensibility/keybindings-element.md)|Dies ist optional. Gibt ggf. die Tastenkombinationen für die Befehle an.|
|[Usedcommands-Element](../extensibility/usedcommands-element.md)|Dies ist optional. Ermöglicht einem VSPackage, optional seine eigene Version der Funktionalität zu implementieren, die ursprünglich von anderen VSPackages unterstützt wurde.|
|[Symbols-Element](https://www.microsoft.com/download/details.aspx?id=55984)|Dies ist optional. Enthält beliebige Symbol Daten-GUIDs, IDs usw. für den Compiler.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Keine||

## <a name="see-also"></a>Weitere Informationen
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
