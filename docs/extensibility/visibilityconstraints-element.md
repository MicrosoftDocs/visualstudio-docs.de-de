---
title: Visibilityschränkt-Element | Microsoft-Dokumentation
description: Das visibilityschränkt-Element bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f50f23847da8f6d56da6763146efd147aebca8c6
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863914"
---
# <a name="visibilityconstraints-element"></a>Visibilityschränkt-Element
Das visibilityschränkt-Element bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten. Die Sichtbarkeit wird zuerst von der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) gesteuert, ohne das VSPackage zu laden.

## <a name="syntax"></a>Syntax

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Visibilityitem-Element](../extensibility/visibilityitem-element.md)|Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|
|[Visibilityeinschränkungen](../extensibility/visibilityconstraints-element.md)|Bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Commandtable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die die Befehle darstellen (z. b. Menü Elemente, Menüs, Symbolleisten und Kombinations Felder), die ein VSPackage für die IDE bereitstellt.|

## <a name="example"></a>Beispiel

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Weitere Informationen
- [Visibilityitem-Element](../extensibility/visibilityitem-element.md)
- [Visual Studio-Befehls Tabelle (. Vsct-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
