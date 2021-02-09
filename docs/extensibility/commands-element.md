---
title: Commands-Element | Microsoft-Dokumentation
description: 'Das Commands-Element stellt die Auflistung der Befehle auf der VSPackage-Symbolleiste dar und kann diese Abschnitte aufweisen: Menüs, Gruppen, Schaltflächen, Combos und Bitmaps.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90670188e3ce1aa621e53c69bad6f795ff30fd8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887431"
---
# <a name="commands-element"></a>Commands-Element
Stellt die Auflistung von Befehlen auf der VSPackage-Symbolleiste dar. Die Auflistung kann bis zu fünf Unterabschnitte aufweisen, wie im folgenden dargestellt: Menüs, Gruppen, Schaltflächen, Combos und Bitmaps.

 Jedes untergeordnete Unterabschnitts Element, z. b \<Menu> ., wird durch eine eindeutige Befehls-ID identifiziert, bei der es sich um eine GUID und einen numerischen Bezeichnerpaar handelt Der GUID identifiziert den "Befehlssatz" und wird verwendet, um logisch verwandte Befehle zu gruppieren. Das VSPackage sollte seinen eigenen Befehlssatz definieren, um Konflikte mit Befehls-IDs zu vermeiden, die von anderen VSPackages definiert werden.

## <a name="syntax"></a>Syntax

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|Paket|Eine GUID, die das VSPackage identifiziert, das die Befehle bereitstellt.<br /><br /> Beispiel: Package = "guidVsPackage1Pkg".|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Menüs-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die von einem VSPackage implementiert werden.|
|[Groups-Element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehls Gruppen in einem VSPackage definieren.|
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppiert Schaltflächen Elemente.|
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert Bitmap-Elemente.|
|[Combos-Element](../extensibility/combos-element.md)|Gruppiert Kombinations Elemente.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Commandtable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die die Befehle darstellen, die ein VSPackage für die IDE bereitstellt. Mögliche Elemente sind Menü Elemente, Menüs, Symbolleisten und Kombinations Felder.|

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird gezeigt, wie ein [Commands-Element](../extensibility/commands-element.md)verwendet wird.

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
