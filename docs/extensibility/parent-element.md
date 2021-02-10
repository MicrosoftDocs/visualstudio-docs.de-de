---
title: Übergeordnetes Element | Microsoft-Dokumentation
description: Das übergeordnete-Element gibt an, dass ein Element ein übergeordnetes Element einer Schaltfläche, eines Kombinations Felds, eines Menüs oder einer Gruppe ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e34b857d26be49bb98096c6b0ba85ff8049290b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968982"
---
# <a name="parent-element"></a>Übergeordnetes Element
Das übergeordnete Element einer Schaltfläche oder eines Kombinations Felds darf nur eine Gruppe sein. Das übergeordnete Element eines Menüs oder einer Gruppe kann ein beliebiges anderes Menü oder eine andere Gruppe sein. In einem [commandplacement-Element](../extensibility/commandplacement-element.md)ist dieses Element erforderlich. in allen anderen Instanzen ist es optional. Wenn dieses Element weggelassen wird, wird das übergeordnete Element von `Group_Undefined:0` impliziert.

## <a name="syntax"></a>Syntax

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. GUID des Befehls Bezeichners GUID/ID.|
|id|Erforderlich. ID des Befehls Bezeichners GUID/ID.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Commandtable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen, die ein VSPackage für die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) bereitstellt. Beispielsweise Menü Elemente, Menüs, Symbolleisten und Kombinations Felder.|
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppiert [Schaltflächen Element](../extensibility/button-element.md) -Elemente.|
|[Menüs-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die von einem VSPackage implementiert werden.|
|[Groups-Element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehls Gruppen eines VSPackage definieren.|

## <a name="see-also"></a>Weitere Informationen
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
