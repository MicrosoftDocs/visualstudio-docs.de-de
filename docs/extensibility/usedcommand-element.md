---
title: Usedcommand-Element | Microsoft-Dokumentation
description: Mit dem usedcommand-Element kann ein VSPackage auf einen Befehl zugreifen, der in einer anderen vsct-Datei definiert ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c3f4a5f39e7cb999d9b3a86aa791464fca25645
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934102"
---
# <a name="usedcommand-element"></a>UsedCommand-Element
Ermöglicht einem VSPackage den Zugriff auf einen Befehl, der in einer anderen vsct-Datei definiert ist. Wenn das VSPackage z. b. den standardmäßigen **Kopier** Befehl verwendet, der durch die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell definiert ist, können Sie den Befehl einem Menü oder einer Symbolleiste hinzufügen, ohne ihn erneut zu implementieren.

## <a name="syntax"></a>Syntax

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. Der GUID des GUID-ID-Paars, das den Befehl identifiziert.|
|id|Erforderlich. Die ID des GUID-ID-Paars, das den Befehl identifiziert.|
|Bedingung|Dies ist optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Keine||

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Gruppiert usedcommand-Elemente und andere usedcommands-Gruppierungen.|

## <a name="remarks"></a>Bemerkungen
 Durch das Hinzufügen eines Befehls zum- `<UsedCommands>` Element wird der Umgebung von einem VSPackage mitgeteilt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , dass das VSPackage den Befehl erfordert. Sie sollten ein- `<UsedCommand>` Element für jeden Befehl hinzufügen, der für das Paket erforderlich ist, das möglicherweise nicht in allen Versionen und Konfigurationen von Visual Studio enthalten ist. Wenn das Paket z. b. einen für Visual C++ spezifischen Befehl aufruft, steht der Befehl Benutzern von Visual Web Developer nur dann zur Verfügung, wenn Sie ein- `<UsedCommand>` Element für den Befehl einschließen.

## <a name="example"></a>Beispiel

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Weitere Informationen
- [UsedCommands-Element](../extensibility/usedcommands-element.md)
- [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
