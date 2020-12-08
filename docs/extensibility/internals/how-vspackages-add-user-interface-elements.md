---
title: Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages | Microsoft-Dokumentation
description: Erfahren Sie, wie VSPackages Benutzeroberflächen Elemente (UI), wie Menüs, Symbolleisten und Tool Fenster, zu Visual Studio hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3e2fe51c365e3e6936a73aef9d4de9d52024d47
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761087"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages
Mit einem VSPackage können Benutzeroberflächen Elemente (UI), z. b. Menüs, Symbolleisten und Tool Fenster, mithilfe der *vsct* -Datei zu Visual Studio hinzugefügt werden.

Entwurfs Richtlinien für Benutzeroberflächen Elemente finden Sie unter [Richtlinien](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)für die Benutzeroberfläche von Visual Studio.

## <a name="the-visual-studio-command-table-architecture"></a>Die Visual Studio-Befehls Tabellen Architektur
Wie bereits erwähnt, unterstützt die Architektur der Befehls Tabelle die vorstehenden architektonischen Prinzipien. Die folgenden Datensätze hinter den Abstraktionen, Datenstrukturen und Tools der Befehls Tabellen Architektur lauten wie folgt:

- Es gibt drei grundlegende Arten von Elementen: Menüs, Befehle und Gruppen. Menüs können in der Benutzeroberfläche als Menüs, Untermenüs, Symbolleisten oder Tool Fenster angezeigt werden. Befehle sind Prozeduren, die der Benutzer in der IDE ausführen kann, und Sie können als Menü Elemente, Schaltflächen, Listenfelder oder andere Steuerelemente verfügbar gemacht werden. Gruppen sind Container für Menüs und Befehle.

- Jedes Element wird durch eine Definition angegeben, die das Element beschreibt, seine Priorität in Bezug auf andere Elemente und die Flags, die das Verhalten ändern.

- Jedes Element verfügt über eine Platzierung, die das übergeordnete Element des Elements beschreibt. Ein Element kann über mehrere übergeordnete Elemente verfügen, damit es an mehreren Positionen in der Benutzeroberfläche angezeigt werden kann.

Jeder Befehl muss über eine Gruppe als übergeordnetes Element verfügen, auch wenn er das einzige untergeordnete Element in dieser Gruppe ist. Jedes Standardmenü muss auch über eine übergeordnete Gruppe verfügen. Symbolleisten und Tool Fenster fungieren als eigene übergeordnete Elemente. Eine Gruppe kann als übergeordnetes Element die Visual Studio-Hauptmenüleiste oder ein beliebiges Menü, eine Symbolleiste oder ein Tool Fenster aufweisen.

### <a name="how-items-are-defined"></a>Definieren von Elementen
Eine *vsct* -Datei wird in XML formatiert. Er definiert die Benutzeroberflächen Elemente für ein Paket und bestimmt, wo diese Elemente in der IDE angezeigt werden. Jedem Menü, jeder Gruppe oder jedem Befehl im Paket wird zunächst eine GUID und ID im Abschnitt zugewiesen `Symbols` . Im restlichen Verlauf der *vsct* -Datei werden alle Menüs, Befehle und Gruppen anhand der Kombination aus GUID und ID identifiziert. Das folgende Beispiel zeigt einen typischen `Symbols` Abschnitt, der von der Visual Studio-Paket Vorlage generiert wird, wenn ein **Menübefehl** in der Vorlage ausgewählt wird.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}">
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

Das Element der obersten Ebene des `Symbols` Abschnitts ist das [guidsymbol-Element](../../extensibility/guidsymbol-element.md). `GuidSymbol` -Elemente ordnen Namen GUIDs zu, die von der IDE verwendet werden, um Pakete und deren Komponenten Teile zu identifizieren.

> [!NOTE]
> GUIDs werden automatisch von der Visual Studio-Paket Vorlage generiert. Sie können auch eine eindeutige GUID erstellen, indem Sie **im Menü Extras** auf **GUID erstellen** klicken.

Das erste `GuidSymbol` Element, `guid<PackageName>Pkg` , ist die GUID des Pakets selbst. Dies ist die GUID, die von Visual Studio verwendet wird, um das Paket zu laden. In der Regel verfügen Sie über keine untergeordneten Elemente.

Gemäß der Konvention werden Menüs und Befehle unter einem zweiten `GuidSymbol` Element gruppiert, `guid<PackageName>CmdSet` und Bitmaps befinden sich unter einem dritten `GuidSymbol` Element, `guidImages` . Sie müssen diese Konvention nicht einhalten, aber jedes Menü, jede Gruppe, jeder Befehl und jede Bitmap muss ein untergeordnetes Element eines- `GuidSymbol` Elements sein.

Im zweiten- `GuidSymbol` Element, das den Paket Befehlssatz darstellt, sind mehrere- `IDSymbol` Elemente. Jedes [idsymbol-Element](../../extensibility/idsymbol-element.md) ordnet einem numerischen Wert einen Namen zu und stellt möglicherweise ein Menü, eine Gruppe oder einen Befehl dar, der Teil des Befehlssatzes ist. Die `IDSymbol` Elemente im dritten `GuidSymbol` Element stellen Bitmaps dar, die als Symbole für Befehle verwendet werden können. Da GUID/ID-Paare in einer Anwendung eindeutig sein müssen, können zwei untergeordnete `GuidSymbol` Elemente desselben Elements nicht denselben Wert aufweisen.

### <a name="menus-groups-and-commands"></a>Menüs, Gruppen und Befehle
Wenn ein Menü, eine Gruppe oder ein Befehl eine GUID und ID hat, kann es der IDE hinzugefügt werden. Jedes Benutzeroberflächen Element muss über Folgendes verfügen:

- Ein- `guid` Attribut, das mit dem Namen des Elements übereinstimmt `GuidSymbol` , unter dem das UI-Element definiert ist.

- Ein `id` Attribut, das mit dem Namen des zugeordneten Elements übereinstimmt `IDSymbol` .

Zusammen bilden das `guid` -Attribut und das- `id` Attribut die *Signatur* des Benutzeroberflächen Elements.

- Ein- `priority` Attribut, das die Platzierung des Benutzeroberflächen Elements im übergeordneten Menü oder in der zugehörigen Gruppe bestimmt.

- Ein über [geordnetes Element](../../extensibility/parent-element.md) `guid` mit-und- `id` Attributen, die die Signatur des übergeordneten Menüs oder der übergeordneten Gruppe angeben.

#### <a name="menus"></a>Menüs
Jedes Menü ist als [Menü Element](../../extensibility/menu-element.md) im `Menus` Abschnitt definiert. Menüs müssen `guid` `id` die Attribute,, und `priority` sowie ein- `Parent` Element sowie die folgenden zusätzlichen Attribute und untergeordneten Elemente aufweisen:

- Ein- `type` Attribut, das angibt, ob das Menü in der IDE als Menü oder als Symbolleiste angezeigt werden soll.

- Ein [Strings-Element](../../extensibility/strings-element.md) , das [ein ButtonText-Element](../../extensibility/buttontext-element.md)enthält, das den Titel des Menüs in der IDE angibt, und ein [CommandName-Element](../../extensibility/commandname-element.md), das den Namen angibt, der im **Befehls** Fenster für den Zugriff auf das Menü verwendet wird.

- Optionale Flags. Ein [CommandFlag-Element](../../extensibility/command-flag-element.md) kann in einer Menü Definition angezeigt werden, um seine Darstellung oder das Verhalten in der IDE zu ändern.

Jedes `Menu` Element muss über eine Gruppe als übergeordnetes Element verfügen, es sei denn, es handelt sich um ein Andock bares Element wie eine Symbolleiste. Ein Andock bares Menü ist ein eigenes übergeordnetes Element. Weitere Informationen zu Menüs und Werten für das- `type` Attribut finden Sie in der Dokumentation zum [Menü Element](../../extensibility/menu-element.md) .

Das folgende Beispiel zeigt ein Menü, das in der Visual Studio **-Menüleiste neben dem Menü** Extras angezeigt wird.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu" id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Gruppen
Eine Gruppe ist ein Element, das im- `Groups` Abschnitt der *vsct* -Datei definiert ist. Gruppen sind nur Container. Sie werden nicht in der IDE angezeigt, außer als Trennlinie in einem Menü. Daher wird ein [Group-Element](../../extensibility/group-element.md) nur durch die Signatur, die Priorität und das übergeordnete Element definiert.

Eine Gruppe kann über ein Menü, eine andere Gruppe oder selbst als übergeordnetes Element verfügen. Das übergeordnete Element ist jedoch in der Regel ein Menü oder eine Symbolleiste. Das Menü im vorherigen Beispiel ist ein untergeordnetes Element der `IDG_VS_MM_TOOLSADDINS` -Gruppe, und diese Gruppe ist ein untergeordnetes Element der Visual Studio-Menüleiste. Die Gruppe im folgenden Beispiel ist ein untergeordnetes Element des Menüs im vorherigen Beispiel.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Da es Teil eines Menüs ist, würde diese Gruppe in der Regel Befehle enthalten. Es könnte jedoch auch andere Menüs enthalten. So werden Untermenüs definiert, wie im folgenden Beispiel gezeigt.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu" priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Befehle
Ein Befehl, der der IDE zur Verfügung gestellt wird, wird entweder als [Schaltflächen Element](../../extensibility/button-element.md) oder als Kombinations [Element](../../extensibility/combo-element.md)definiert. Damit der Befehl in einem Menü oder einer Symbolleiste angezeigt wird, muss er über eine Gruppe als übergeordnetes Element verfügen.

##### <a name="buttons"></a>Schaltflächen
Schaltflächen werden im `Buttons` Abschnitt definiert. Alle Menü Elemente, Schaltflächen oder anderen Elemente, auf die ein Benutzer klickt, um einen einzelnen Befehl auszuführen, werden als Schaltfläche betrachtet. Einige Schaltflächen Typen können auch Listen Funktionen enthalten. Schaltflächen verfügen über dieselben erforderlichen und optionalen Attribute wie Menüs, und Sie können auch über ein [Symbol Element](../../extensibility/icon-element.md) verfügen, das die GUID und die ID der Bitmap angibt, die die Schaltfläche in der IDE darstellt. Weitere Informationen zu Schaltflächen und deren Attributen finden Sie in der Dokumentation zu den [Buttons-Elementen](../../extensibility/buttons-element.md) .

Die Schaltfläche im folgenden Beispiel ist ein untergeordnetes Element der-Gruppe im vorherigen Beispiel und würde in der IDE als Menü Element im übergeordneten Menü dieser Gruppe angezeigt werden.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

##### <a name="combos"></a>Combos
Combos sind im Abschnitt definiert `Combos` . Jedes `Combo` Element stellt ein Dropdown-Listenfeld in der IDE dar. Abhängig vom Wert des-Attributs des Kombinations Felds kann das Listenfeld von Benutzern beschreibbar sein `type` . Combos haben dieselben Elemente und Verhalten wie Schaltflächen und können auch über die folgenden zusätzlichen Attribute verfügen:

- Ein- `defaultWidth` Attribut, das die Pixel Breite angibt.

- Ein `idCommandList` Attribut, das eine Liste mit den Elementen angibt, die im Listenfeld angezeigt werden. Die Befehlsliste muss im gleichen Knoten deklariert werden `GuidSymbol` , der das Kombinations Feld enthält.

Im folgenden Beispiel wird ein Kombinations Element definiert.

```xml
<Combos>
  <Combo guid="guidFirstToolWinCmdSet"
         id="cmdidWindowsMediaFilename"
         priority="0x0100" type="DynamicCombo"
         idCommandList="cmdidWindowsMediaFilenameGetList"
         defaultWidth="130">
    <Parent guid="guidFirstToolWinCmdSet"
            id="ToolbarGroupID" />
    <CommandFlag>IconAndText</CommandFlag>
    <CommandFlag>CommandWellOnly</CommandFlag>
    <CommandFlag>StretchHorizontally</CommandFlag>
    <Strings>
      <CommandName>Filename</CommandName>
      <ButtonText>Enter a Filename</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

##### <a name="bitmaps"></a>Bitmaps
Befehle, die zusammen mit einem Symbol angezeigt werden, müssen ein `Icon` Element enthalten, das mithilfe ihrer GUID und ID auf eine Bitmap verweist. Jede Bitmap ist als [Bitmap-Element](../../extensibility/bitmap-element.md) im- `Bitmaps` Abschnitt definiert. Die einzigen erforderlichen Attribute für eine `Bitmap` Definition sind `guid` und `href` , die auf die Quelldatei verweist. Wenn es sich bei der Quelldatei um einen Ressourcen Streifen handelt, ist auch ein **usedlist** -Attribut erforderlich, um die verfügbaren Images im Strip aufzulisten. Weitere Informationen finden Sie in der Dokumentation zum [Bitmap-Element](../../extensibility/bitmap-element.md) .

### <a name="parenting"></a>Geordnet
Die folgenden Regeln steuern, wie ein Element ein anderes Element als übergeordnetes Element abrufen kann.

|Element|Definiert in diesem Abschnitt der Befehls Tabelle.|Kann enthalten sein (als übergeordnetes Element oder durch Platzierung im- `CommandPlacements` Abschnitt oder beides).|Kann enthalten (als übergeordnetes Element bezeichnet)|
|-------------| - | - | - |
|Group|[Groups-Element](../../extensibility/groups-element.md), IDE, andere VSPackages|Ein Menü, eine Gruppe, das Element selbst|Menüs, Gruppen und Befehle|
|Menü|[Menüs-Element](../../extensibility/menus-element.md), IDE, andere VSPackages|1 bis *n* Gruppen|0 bis *n* Gruppen|
|Symbolleiste|[Menüs-Element](../../extensibility/menus-element.md), IDE, andere VSPackages|Das Element selbst.|0 bis *n* Gruppen|
|Menübefehl|[Buttons-Element](../../extensibility/buttons-element.md), IDE, andere VSPackages|1 bis *n* Gruppen, das Element selbst|-0 bis *n* Gruppen|
|Schaltfläche|[Buttons-Element](../../extensibility/buttons-element.md), IDE, andere VSPackages|1 bis *n* Gruppen, das Element selbst||
|Kombinationsdiagramm|[Combos-Element](../../extensibility/combos-element.md), IDE, andere VSPackages|1 bis *n* Gruppen, das Element selbst||

### <a name="menu-command-and-group-placement"></a>Menü-, Befehls-und Gruppenplatzierung
Ein Menü, eine Gruppe oder ein Befehl kann an mehreren Orten in der IDE angezeigt werden. Damit ein Element an mehreren Speicherorten angezeigt wird, muss es dem `CommandPlacements` Abschnitt als [commandplacement-Element](../../extensibility/commandplacement-element.md)hinzugefügt werden. Alle Menüs, Gruppen oder Befehle können als Befehls Platzierung hinzugefügt werden. Symbolleisten können jedoch nicht auf diese Weise positioniert werden, da Sie nicht an mehreren kontextabhängigen Orten vorkommen können.

Befehls Platzierungen verfügen über die `guid` `id` Attribute, und `priority` . Die GUID und die ID müssen mit denen des Elements, das positioniert ist, identisch sein. Das- `priority` Attribut bestimmt die Platzierung des Elements in Bezug auf andere Elemente. Wenn die IDE zwei oder mehr Elemente mit der gleichen Priorität zusammenfasst, sind Ihre Platzierungs Vorgänge nicht definiert, da die IDE nicht garantiert, dass Paket Ressourcen bei jedem Erstellen des Pakets in derselben Reihenfolge gelesen werden.

Wenn ein Menü oder eine Gruppe an mehreren Speicherorten angezeigt wird, werden alle untergeordneten Elemente des Menüs oder der Gruppe in jeder Instanz angezeigt.

## <a name="command-visibility-and-context"></a>Befehls Sichtbarkeit und Kontext
Wenn mehrere VSPackages installiert sind, kann die IDE durch eine multifusion von Menüs, Menü Elementen und Symbolleisten gruppiert werden. Um dieses Problem zu vermeiden, können Sie die Sichtbarkeit einzelner Benutzeroberflächen Elemente mithilfe von *Sichtbarkeits Einschränkungen* und Befehlsflags steuern.

### <a name="visibility-constraints"></a>Sichtbarkeits Einschränkungen
Eine Sichtbarkeits Einschränkung wird als [visibilityitem-Element](../../extensibility/visibilityitem-element.md) im- `VisibilityConstraints` Abschnitt festgelegt. Eine Sichtbarkeits Einschränkung definiert bestimmte UI-Kontexte, in denen das Ziel Element sichtbar ist. Ein Menü oder Befehl, der in diesem Abschnitt enthalten ist, ist nur sichtbar, wenn einer der definierten Kontexte aktiv ist. Wenn in diesem Abschnitt nicht auf ein Menü oder einen Befehl verwiesen wird, ist es standardmäßig immer sichtbar. Dieser Abschnitt gilt nicht für Gruppen.

`VisibilityItem` -Elemente müssen wie folgt drei Attribute aufweisen: `guid` und `id` des Ziel Benutzeroberflächen Elements und `context` . Das `context` -Attribut gibt an, wann das Ziel Element sichtbar ist, und nimmt einen beliebigen gültigen Benutzeroberflächen Kontext als Wert an. Die UI-Kontext Konstanten für Visual Studio sind Member der- <xref:Microsoft.VisualStudio.VSConstants> Klasse. Jedes `VisibilityItem` Element kann nur einen Kontextwert annehmen. Wenn Sie einen zweiten Kontext anwenden möchten, erstellen Sie ein zweites `VisibilityItem` Element, das auf das gleiche Element zeigt, wie im folgenden Beispiel gezeigt.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

### <a name="command-flags"></a>Befehlsflags
Die folgenden Befehlsflags können sich auf die Sichtbarkeit der Menüs und Befehle auswirken, auf die Sie angewendet werden.

`AlwaysCreate` Das Menü wird auch dann erstellt, wenn es keine Gruppen oder Schaltflächen enthält.

Gültig für: `Menu`

`CommandWellOnly` Wenden Sie dieses Flag an, wenn der Befehl nicht im Menü der obersten Ebene angezeigt wird und Sie es für zusätzliche Shellanpassungen verfügbar machen möchten, z. b. für die Bindung an einen Schlüssel. Nachdem das VSPackage installiert wurde, kann ein Benutzer diese Befehle anpassen, indem er das Dialogfeld **Optionen** öffnet und dann die Befehls Platzierung unter der Kategorie **Tastatur Umgebung** bearbeitet. Hat keine Auswirkung auf die Platzierung von Kontextmenüs, Symbolleisten, Menü Controllern oder Untermenüs.

Gültig für: `Button` , `Combo`

`DefaultDisabled` Standardmäßig ist der Befehl deaktiviert, wenn das VSPackage, das den Befehl implementiert, nicht geladen wurde oder die QueryStatus-Methode nicht aufgerufen wurde.

Gültig für: `Button` , `Combo`

`DefaultInvisible` Standardmäßig ist der Befehl unsichtbar, wenn das VSPackage, das den Befehl implementiert, nicht geladen wurde oder die QueryStatus-Methode nicht aufgerufen wurde.

Sollte mit dem-Flag kombiniert werden `DynamicVisibility` .

Gültig für: `Button` , `Combo` , `Menu`

`DynamicVisibility` Die Sichtbarkeit des Befehls kann mithilfe der- `QueryStatus` Methode oder einer Kontext-GUID, die im-Abschnitt enthalten ist, geändert werden `VisibilityConstraints` .

Gilt für Befehle, die in Menüs und nicht in Symbolleisten angezeigt werden. Symbolleisten Elemente der obersten Ebene können deaktiviert, jedoch nicht ausgeblendet werden, wenn das `OLECMDF_INVISIBLE` Flag von der-Methode zurückgegeben wird `QueryStatus` .

In einem Menü gibt dieses Flag auch an, dass es automatisch ausgeblendet werden soll, wenn seine Member ausgeblendet sind. Dieses Flag wird normalerweise Untermenüs zugewiesen, da die Menüs der obersten Ebene bereits über dieses Verhalten verfügen.

Sollte mit dem-Flag kombiniert werden `DefaultInvisible` .

Gültig für: `Button` , `Combo` , `Menu`

`NoShowOnMenuController` Wenn ein Befehl mit diesem Flag auf einem Menü Controller positioniert ist, wird der Befehl nicht in der Dropdown Liste angezeigt.

Gültig für: `Button`

Weitere Informationen zu Befehlsflags finden Sie in der Dokumentation zum [CommandFlag-Element](../../extensibility/command-flag-element.md) .

#### <a name="general-requirements"></a>Allgemeine Anforderungen
Der Befehl muss die folgende Reihe von Tests durchlaufen, bevor er angezeigt und aktiviert werden kann:

- Der Befehl ist ordnungsgemäß positioniert.

- Das `DefaultInvisible` Flag ist nicht festgelegt.

- Das übergeordnete Menü oder die Symbolleiste ist sichtbar.

- Der Befehl ist aufgrund eines Kontext Eintrags im [visibilityeinschränkungs-Element](../../extensibility/visibilityconstraints-element.md) Abschnitt nicht unsichtbar.

- VSPackage-Code, der die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle implementiert, zeigt den Befehl an und aktiviert ihn. Der Schnittstellen Code hat ihn abgefangen und darauf reagiert.

- Wenn ein Benutzer auf den Befehl klickt, wird er der Prozedur unterzogen, die unter [Routing Algorithmus](../../extensibility/internals/command-routing-algorithm.md)beschrieben wird.

## <a name="call-pre-defined-commands"></a>Vordefinierte Befehle abrufen
Das [usedcommands-Element](../../extensibility/usedcommands-element.md) ermöglicht VSPackages den Zugriff auf Befehle, die von anderen VSPackages oder der IDE bereitgestellt werden. Erstellen Sie zu diesem Zweck ein [usedcommand-Element](../../extensibility/usedcommand-element.md) , das die GUID und die ID des zu verwendenden Befehls enthält. Dadurch wird sichergestellt, dass der Befehl von Visual Studio geladen wird, auch wenn er nicht Teil der aktuellen Visual Studio-Konfiguration ist. Weitere Informationen finden Sie unter [usedcommand-Element](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Darstellung des Schnittstellen Elements
Überlegungen zum auswählen und Positionieren von Befehls Elementen:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet viele Benutzeroberflächen Elemente, die je nach Platzierung unterschiedlich angezeigt werden.

- Ein Benutzeroberflächen Element, das mit dem-Flag definiert wird, `DefaultInvisible` wird nicht in der IDE angezeigt, es sei denn, es wird entweder von der VSPackage-Implementierung der- <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> Methode oder einem bestimmten UI-Kontext im- `VisibilityConstraints` Abschnitt angezeigt.

- Möglicherweise wird auch ein erfolgreich positionierter Befehl nicht angezeigt. Dies liegt daran, dass die IDE einige Befehle automatisch blendet oder anzeigt, abhängig von den Schnittstellen, die das VSPackage nicht implementiert hat (oder nicht). Beispielsweise bewirkt eine VSPackage-Implementierung einiger buildschnittstellen, dass buildbezogene Menü Elemente automatisch angezeigt werden.

- Das Anwenden des- `CommandWellOnly` Flags in der Definition des Elements der Benutzeroberfläche bedeutet, dass der Befehl nur durch Anpassung hinzugefügt werden kann.

- Befehle können nur in bestimmten UI-Kontexten verfügbar sein, z. b. nur dann, wenn ein Dialogfeld angezeigt wird, wenn sich die IDE in der Entwurfs Ansicht befindet.

- Damit bestimmte Benutzeroberflächen Elemente in der IDE angezeigt werden, müssen Sie eine oder mehrere Schnittstellen implementieren oder Code schreiben.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)
