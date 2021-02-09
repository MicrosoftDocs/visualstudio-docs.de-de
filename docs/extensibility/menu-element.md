---
title: Menu-Element | Microsoft-Dokumentation
description: Das Menü Element definiert ein Menü Element. Die Menü Arten sind context, Menu, menucontroller, menucontrollerlatched, Toolbar und toolwindowtoolbar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a55b96e3947d8ca0605778ab927b4028b1a3ecd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886807"
---
# <a name="menu-element"></a>Menu-Element
Definiert ein Menü Element. Dies sind die sechs Arten von Menüs: Kontext, Menü, menucontroller, menucontrollerlatched, Symbolleiste und toolwindowtoolbar.

## <a name="syntax"></a>Syntax

```xml
<Menu guid="guidMyCommandSet" id="MyCommand" priority="0x100" type="button">
  <Parent>... </Parent>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Menu>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|guid|Erforderlich. GUID des GUID-/ID-befehlsbezeichners.|
|id|Erforderlich. ID des GUID-/ID-befehlsbezeichners.|
|priority|Dies ist optional. Ein numerischer Wert, der die relative Position eines Menüs in einer Gruppe von Menüs angibt.|
|Toolbarpriorityinband|Dies ist optional. Ein numerischer Wert, der die relative Position einer Symbolleiste in einem Band angibt, wenn das Fenster angedockt ist.|
|type|Dies ist optional. Ein-Enumerationswert, der die Art des-Elements angibt.<br /><br /> Wenn diese Option nicht vorhanden ist, wird der Standardtyp Menü angezeigt.<br /><br /> Kontext<br /> Ein Kontextmenü, das angezeigt wird, wenn ein Benutzer mit der rechten Maustaste auf ein Fenster klickt. Ein Kontextmenü weist die folgenden Eigenschaften auf:<br /><br /> : Verwendet nicht die Felder übergeordnet und **Priorität** , **Wenn das Menü** als Kontextmenü angezeigt werden soll.<br />-Kann als Untermenü und auch als Kontextmenü verwendet werden. In diesem Fall werden die Felder " **Gruppen-ID** " und " **Priorität** " berücksichtigt.<br />-Ist nicht immer verfügbar.<br /><br /> Ein Kontextmenü wird nur angezeigt, wenn die folgenden Bedingungen zutreffen:<br /><br /> -Das Fenster, in dem es gehostet wird, wird angezeigt.<br />-Ein Maus Handler im VSPackage erkennt einen Rechtsklick auf das Fenster und ruft dann eine Methode auf, die den Befehl behandelt.<br />-Das Kontextmenü wird angezeigt, indem die- <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> Methode (die empfohlene Vorgehensweise) oder die-Methode aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> .<br /><br /> Menü<br /> Stellt ein Dropdown Menü bereit. Ein Dropdown Menü weist die folgenden Eigenschaften auf:<br /><br /> -Respektiert das übergeordnete Element in seiner Definition.<br />-Muss über eine übergeordnete Gruppe oder eine commandplacement für eine Gruppe verfügen.<br />: Kann ein Untermenü in einer beliebigen anderen Art von Menü sein.<br />-Wird automatisch angezeigt, wenn das übergeordnete Menü angezeigt wird.<br />-Erfordert nicht die Implementierung eines VSPackage-Codes, damit er angezeigt wird.<br /><br /> Menucontroller<br /> Stellt ein Dropdown Menü mit einer Trenn Schaltfläche bereit, das in der Regel in Symbolleisten verwendet wird. Ein menucontroller-Menü weist die folgenden Eigenschaften auf:<br /><br /> -Muss in einem anderen Menü über Parent oder commandplacement enthalten sein.<br />-Respektiert das übergeordnete Element in seiner Definition.<br />: Kann über eine beliebige Art von Menü als übergeordnetes Element verfügen.<br />-Wird automatisch zur Verfügung gestellt, wenn das übergeordnete Menü angezeigt wird.<br />-Erfordert keine programmgesteuerte Unterstützung, damit das Menü angezeigt wird.<br /><br /> Ein Befehl aus dem Menü unterteilte Schaltfläche wird auf der Menü Schaltfläche angezeigt. Der angezeigte Befehl hat eine der folgenden Eigenschaften:<br /><br /> -Dies ist der letzte Befehl, der verwendet wurde, wenn der Befehl weiterhin angezeigt und aktiviert wird.<br />-Dies ist der erste angezeigte Befehl.<br /><br /> Menucontrollerlatched<br /> Enthält ein Dropdown Menü mit einer Trenn Schaltfläche, für das ein Befehl als Standardauswahl angegeben werden kann, indem der Befehl als "latched" markiert wird.<br /><br /> Bei einem Latch-Befehl handelt es sich um einen Befehl, der im Menü als ausgewählt gekennzeichnet ist, in der Regel durch Anzeigen eines Häkchens. Ein Befehl kann als "Latch" gekennzeichnet werden, wenn das OLECMDF_LATCHED-Flag in einer Implementierung der- `QueryStatus` Methode der-Schnittstelle darauf festgelegt ist <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Ein menucontrollerlatched-Menü weist die folgenden Eigenschaften auf:<br /><br /> -Muss in einem anderen Menü über eine übergeordnete Gruppe oder commandplacement enthalten sein.<br />-Respektiert das übergeordnete Element in seiner Definition.<br />: Kann über eine beliebige Art von Menü als übergeordnetes Element verfügen.<br />-Wird immer verfügbar gemacht, wenn das übergeordnete Menü angezeigt wird.<br />-Erfordert keine programmgesteuerte Unterstützung, damit das Menü angezeigt wird.<br /><br /> Ein Befehl aus dem Menü unterteilte Schaltfläche wird auf der Menü Schaltfläche angezeigt. Der angezeigte Befehl hat eine der folgenden Eigenschaften:<br /><br /> -Dies ist der erste angezeigte Befehl, der in einem latchmodus angezeigt wird.<br />-Dies ist der erste angezeigte Befehl.<br /><br /> Symbolleiste<br /> Stellt eine Symbolleiste bereit. Eine Symbolleiste weist die folgenden Eigenschaften auf:<br /><br /> -Ignoriert das übergeordnete Element in seiner Definition.<br />: Kann nicht selbst mithilfe von commandplacement als Untermenü einer beliebigen Gruppe erstellt werden.<br />-Kann immer angezeigt werden, indem Sie im Menü **Ansicht** auf **Symbolleisten** klicken.<br />-Kann mithilfe eines [visibilityitem](../extensibility/visibilityitem-element.md)angezeigt werden.<br />-Erfordert keinen Code, um ihn zu erstellen. Ein Beispiel zum Erstellen einer Symbolleiste finden [Sie unter Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).<br /><br /> Toolwindowtoolbar<br /> Stellt eine Symbolleiste bereit, die an ein bestimmtes Tool Fenster angefügt ist, ebenso wie eine Symbolleiste an die Entwicklungsumgebung angefügt wird.<br /><br /> -Ignoriert das übergeordnete Element in seiner Definition.<br />: Kann nicht selbst mithilfe von commandplacement als Untermenü einer beliebigen Gruppe erstellt werden.<br />-Wird nur angezeigt, wenn das Tool Fenster angezeigt wird, das die Symbolleiste hostet, und das VSPackage die Symbolleiste explizit dem Tool Fenster hinzufügt. Dies erfolgt in der Regel, wenn das Tool Fenster erstellt wird, indem die Symbolleisten Host-Eigenschaft (wie durch die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> Schnittstelle dargestellt) vom Tool Fensterrahmen erhalten und dann die-Methode aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> .|
|Bedingung|Dies ist optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|Parent|Dies ist optional. Das übergeordnete Element des Menü Elements.|
|CommandFlag|Erforderlich. Siehe [Befehlsflag-Element](../extensibility/command-flag-element.md). Die gültigen CommandFlag-Werte für ein Menü lauten wie folgt:<br /><br /> -   **AlwaysCreate**<br />-   **Defaultangedockt**<br />-   **Defaultinvisible** : dieses Flag wirkt sich nicht auf die Anzeige von Symbolleisten aus.<br />-   **DontCache**<br />-   **Dynamicvisibility** : dieses Flag wirkt sich nicht auf die Anzeige von Symbolleisten aus.<br />-   **Iconandtext**<br />-   **Nocustomize**<br />-   **Notintblist**<br />-   **Notoolbarclose**<br />-   **Textchanges Befehlsflag**<br />-   **Textisanchorcommand**|
|Zeichenfolgen|Erforderlich. Siehe [Strings-Element](../extensibility/strings-element.md). Das untergeordnete- `ButtonText` Element muss definiert werden.|
|Anmerkung|Optionaler Kommentar.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Menüs-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die von einem VSPackage implementiert werden.|

## <a name="example"></a>Beispiel

```
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"
  priority="0x0002" type="Menu">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"/>
  <CommandFlag>AlwaysCreate</CommandFlag>
  <Strings>
    <ButtonText>Edit Widget</ButtonText>
  </Strings>
</Menu>
```

## <a name="see-also"></a>Weitere Informationen
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
