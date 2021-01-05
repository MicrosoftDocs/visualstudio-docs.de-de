---
title: Symbols-Element | Microsoft-Dokumentation
description: Das Symbols-Element definiert GUIDs und IDs, die von anderen vsct-Elementen verwendet werden. Dieser Artikel enthält ein Beispiel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e86406c4c10c2f65e8e43d8f3cb67f413ed3c63
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715560"
---
# <a name="symbols-element"></a>Symbols-Element
Definiert GUIDs und IDs, die von anderen vsct-Elementen verwendet werden. Bei nicht verwaltetem Code stammen diese Informationen in der Regel aus den Header Dateien, die durch das [extern-Element](../extensibility/extern-element.md)angegeben werden. Verwalteter Code verwendet die untergeordneten Elemente des Symbols-Elements, um diese Informationen zu definieren.

 Wenn Sie eine vsct-Datei aus einer vorhandenen CTO-Datei erstellen, werden die Symbole als untergeordnete Elemente des Elements "Symbols" generiert. Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen einer. Vsct-Datei aus einer vorhandenen. CTO-Datei](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Das Symbols-Element sollte nicht mit dem [define-Element](../extensibility/define-element.md)verwechselt werden, das Name-Wert-Paare für die Verwendung durch den Präprozessor definiert.

## <a name="syntax"></a>Syntax

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|Keine||

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|GuidSymbol|Definiert ein GUID-Symbol. "Guidsymbol" hat zwei erforderliche Attribute: "Name" und "Value". Der Name ist der Name des Symbols, und der Wert ist der Wert der GUID als Zeichenfolge.<br /><br /> Beispiel: \<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Definiert ein Symbol. Idsymbol verfügt über zwei erforderliche Attribute: Name und Wert. Der Name ist der Name des Symbols, und der Wert ist der Wert des Symbols als Zeichenfolge.<br /><br /> Beispiel: \<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Das Stamm Element der vsct-Datei.|

## <a name="example"></a>Beispiel

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>Weitere Informationen
- [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
