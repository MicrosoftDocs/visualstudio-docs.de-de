---
title: Visibilityitem-Element | Microsoft-Dokumentation
description: Das visibilityitem-Element bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten. Einträge identifizieren einen Befehl oder ein Menü und einen zugeordneten Befehls Benutzeroberflächen Kontext.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3fa4c2910a1f694a822d2a31b5ad537c8104f99c
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221300"
---
# <a name="visibilityitem-element"></a>Visibilityitem-Element
Das- `VisibilityItem` Element bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten. Jeder Eintrag identifiziert einen Befehl oder ein Menü sowie einen zugeordneten Befehls Benutzeroberflächen Kontext. Visual Studio erkennt Befehle, Menüs und Symbolleisten sowie deren Sichtbarkeit, ohne die VSPackages zu laden, die Sie definieren. Die IDE verwendet die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode, um zu bestimmen, ob ein Befehls Benutzeroberflächen Kontext aktiv ist.

 Nachdem das VSPackage geladen wurde, erwartet Visual Studio, dass die Sichtbarkeit des Befehls durch das VSPackage anstelle von bestimmt wird `VisibilityItem` . Um die Sichtbarkeit des Befehls zu ermitteln, können Sie entweder den- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Ereignishandler oder die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode implementieren, je nachdem, wie Sie den Befehl implementiert haben.

 Ein Befehl oder ein Menü mit einem- `VisibilityItem` Element wird nur angezeigt, wenn der zugeordnete Kontext aktiv ist. Sie können einen einzelnen Befehl, ein Menü oder eine Symbolleiste mit einem oder mehreren Befehls Benutzeroberflächen Kontexten verknüpfen, indem Sie einen Eintrag für jede Befehls Kontext Kombination einschließen. Wenn ein Befehl oder ein Menü mehreren Befehls Benutzeroberflächen Kontexten zugeordnet ist, wird der Befehl oder das Menü angezeigt, wenn einer der zugeordneten Befehls Benutzeroberflächen Kontexte aktiv ist.

 Das `VisibilityItem` -Element gilt nur für Befehle, Menüs und Symbolleisten, nicht für Gruppen. Ein Element, das kein verwandtes Element besitzt, `VisibilityItem` ist sichtbar, wenn das übergeordnete Menü aktiv ist.

## <a name="syntax"></a>Syntax

```xml
<VisibilityItem
  guid="cmdGuidMyProductCommands"
  id="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. Der GUID des GUID-/ID-befehlsbezeichners.|
|id|Erforderlich. Die ID des GUID-/ID-befehlsbezeichners.|
|context|Erforderlich. Der UI-Kontext, in dem der Befehl sichtbar ist.|
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Visibilityschränkt-Element](../extensibility/visibilityconstraints-element.md)|Das `VisibilityConstraints` -Element bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten.|

## <a name="remarks"></a>Bemerkungen
 Die standardmäßigen Visual Studio-Benutzeroberflächen Kontexte werden im *Visual Studio SDK-Installationspfad*\visualstudiointegration\common\inc\vsshlids.h sowie in der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> -Klasse und der- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klasse definiert. In der-Klasse ist ein ausführlichere Satz von UI-Kontexten definiert <xref:Microsoft.VisualStudio.VSConstants> .

## <a name="example"></a>Beispiel

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Visibilityschränkt-Element](../extensibility/visibilityconstraints-element.md)
- [Visual Studio-Befehls Tabelle (. Vsct-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
