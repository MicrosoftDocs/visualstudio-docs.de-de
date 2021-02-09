---
title: Erstellungs. Vsct-Dateien | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie vsct-Dateien erstellen, die Menü Elemente, Symbolleisten und andere Benutzeroberflächen Elemente zur integrierten Entwicklungsumgebung (IDE) von Visual Studio hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c484c08b3335d51283f1f6e1a7b29757a2271aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906061"
---
# <a name="author-vsct-files"></a>Vsct-Dateien erstellen
In diesem Dokument wird gezeigt, wie Sie eine *vsct* -Datei zum Hinzufügen von Menü Elementen, Symbolleisten und anderen Elementen der Benutzeroberfläche zur integrierten Entwicklungsumgebung (IDE) von Visual Studio erstellen. Gehen Sie folgendermaßen vor, wenn Sie einem Visual Studio-Paket (VSPackage), das noch keine *vsct* -Datei enthält, Benutzeroberflächen Elemente hinzufügen.

 Für neue Projekte empfiehlt es sich, die Visual Studio-Paket Vorlage zu verwenden, da Sie eine *vsct* -Datei generiert, die je nach Ihrer Auswahl bereits über die erforderlichen Elemente für einen Menübefehl, ein Tool Fenster oder einen benutzerdefinierten Editor verfügt. Sie können diese *vsct* -Datei ändern, um die Anforderungen des VSPackage zu erfüllen. Weitere Informationen zum Ändern einer *vsct* -Datei finden Sie in den Beispielen in Erweitern von [Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Datei erstellen
 Erstellen einer *vsct* -Datei in diesen Phasen: Erstellen Sie die Struktur für Dateien und Ressourcen, deklarieren Sie die Benutzeroberflächen Elemente, platzieren Sie die Elemente der Benutzeroberfläche in der IDE, und fügen Sie spezielle Verhalten hinzu.

### <a name="file-structure"></a>Dateistruktur
 Die grundlegende Struktur einer *vsct* -Datei ist ein [commandtable](../../extensibility/commandtable-element.md) -Stamm Element, das ein [Commands](../../extensibility/commands-element.md) -Element und ein [Symbols](../../extensibility/symbols-element.md) -Element enthält.

#### <a name="to-create-the-file-structure"></a>So erstellen Sie die Dateistruktur

1. Fügen Sie dem Projekt eine *vsct* -Datei hinzu, indem Sie die Schritte unter Gewusst [wie: Erstellen einer vsct-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)ausführen.

2. Fügen Sie dem-Element die erforderlichen Namespaces hinzu `CommandTable` , wie im folgenden Beispiel gezeigt:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. `CommandTable`Fügen Sie im-Element ein-Element hinzu, `Commands` um alle benutzerdefinierten Menüs, Symbolleisten, Befehls Gruppen und Befehle zu hosten. Damit Ihre benutzerdefinierten Benutzeroberflächen Elemente geladen werden können, muss das-Attribut des- `Commands` Elements `Package` auf den Namen des Pakets festgelegt sein.

     `Commands`Fügen Sie nach dem-Element `Symbols` ein-Element hinzu, um die GUIDs für das Paket und die Namen und Befehls-IDs für die Benutzeroberflächen Elemente zu definieren.

### <a name="include-visual-studio-resources"></a>Visual Studio-Ressourcen einschließen
 Verwenden Sie das [extern](../../extensibility/extern-element.md) -Element, um auf die Dateien zuzugreifen, die Visual Studio-Befehle definieren, sowie die Menüs, die erforderlich sind, um die Benutzeroberflächen Elemente in der IDE zu platzieren Wenn Sie Befehle verwenden möchten, die außerhalb des Pakets definiert sind, verwenden Sie das [usedcommands](../../extensibility/usedcommands-element.md) -Element, um Visual Studio zu informieren.

#### <a name="to-include-visual-studio-resources"></a>So schließen Sie Visual Studio-Ressourcen ein

1. Fügen Sie am oberen Rand des- `CommandTable` Elements `Extern` für jede externe Datei, auf die verwiesen werden soll, ein-Element hinzu, und legen Sie das- `href` Attribut auf den Namen der Datei fest. Sie können auf die folgenden Header Dateien verweisen, um auf Visual Studio-Ressourcen zuzugreifen:

   - *Stdidcmd. h*: definiert IDs für alle Befehle, die von Visual Studio verfügbar gemacht werden.

   - *Vsshlids. h*: enthält Befehls-IDs für Visual Studio-Menüs.

2. Wenn das Paket Befehle aufruft, die von Visual Studio oder anderen Paketen definiert werden, fügen Sie `UsedCommands` nach dem-Element ein-Element hinzu `Commands` . Füllen Sie dieses Element mit einem [usedcommand](../../extensibility/usedcommand-element.md) -Element für jeden aufzurufenden Befehl auf, der nicht Teil des Pakets ist. Legen `guid` Sie die `id` Attribute und der `UsedCommand` Elemente auf die GUID-und ID-Werte der aufzurufenden Befehle fest.

   Weitere Informationen zum Suchen der GUIDs und IDs von Visual Studio-Befehlen finden Sie unter [GUIDs und IDs von Visual Studio-Befehlen](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Um Befehle aus anderen Paketen aufzurufen, verwenden Sie die GUID und die ID des Befehls, wie in der *vsct* -Datei für diese Pakete definiert.

### <a name="declare-ui-elements"></a>Benutzeroberflächen Elemente deklarieren
 Deklarieren Sie alle neuen Benutzeroberflächen Elemente im- `Symbols` Abschnitt der *vsct* -Datei.

#### <a name="to-declare-ui-elements"></a>So deklarieren Sie Benutzeroberflächen Elemente

1. `Symbols`Fügen Sie im-Element drei [guidsymbol](../../extensibility/guidsymbol-element.md) -Elemente hinzu. Jedes `GuidSymbol` Element verfügt über ein `name` -Attribut und ein- `value` Attribut. Legen Sie das- `name` Attribut so fest, dass es den Zweck des-Elements widerspiegelt. Das `value` Attribut nimmt eine GUID an. (Um eine GUID zu generieren, wählen Sie **im Menü Extras** die Option **GUID erstellen**, und wählen Sie dann **Registrierungs Format** aus.)

     Das erste `GuidSymbol` Element stellt das Paket dar und hat in der Regel keine untergeordneten Elemente. Das zweite `GuidSymbol` Element stellt den Befehlssatz dar und enthält alle Symbole, mit denen die Menüs, Gruppen und Befehle definiert werden. Das dritte `GuidSymbol` Element stellt den Image Speicher dar und enthält Symbole für alle Symbole für die Befehle. Wenn Sie über keine Befehle verfügen, die Symbole verwenden, können Sie das dritte `GuidSymbol` Element weglassen.

2. `GuidSymbol`Fügen Sie im-Element, das den Befehlssatz darstellt, mindestens ein [idsymbol](../../extensibility/idsymbol-element.md) -Element hinzu. Jedes dieser Elemente stellt ein Menü, eine Symbolleiste, eine Gruppe oder einen Befehl dar, die Sie der Benutzeroberfläche hinzufügen.

     `IDSymbol`Legen Sie für jedes Element das- `name` Attribut auf den Namen fest, den Sie verwenden, um auf das entsprechende Menü, die entsprechende Gruppe oder den entsprechenden Befehl zu verweisen, und legen Sie dann das- `value` Element auf eine hexadezimale Zahl fest, die die Befehls-ID darstellt. Es können nicht zwei `IDSymbol` Elemente mit demselben übergeordneten Element denselben Wert aufweisen.

3. Wenn für die Benutzeroberflächen Elemente Symbole erforderlich sind, fügen Sie `IDSymbol` dem `GuidSymbol` Element, das Ihren Image Speicher darstellt, ein Element für jedes Symbol hinzu.

### <a name="put-ui-elements-in-the-ide"></a>UI-Elemente in der IDE platzieren
 Die Elemente [Menüs](../../extensibility/menus-element.md), [Gruppen](../../extensibility/groups-element.md)und [Schalt](../../extensibility/buttons-element.md) Flächen enthalten die Definitionen für alle Menüs, Gruppen und Befehle, die im Paket definiert sind. Platzieren Sie diese Menüs, Gruppen und Befehle in der IDE entweder mithilfe eines über [geordneten](../../extensibility/parent-element.md) Elements, das Teil der Benutzeroberflächen-Element Definition ist, oder mithilfe eines [commandplacement](../../extensibility/commandplacement-element.md) -Elements, das an anderer Stelle definiert ist.

 Jedes `Menu` `Group` -,-und- `Button` Element verfügt über ein `guid` -Attribut und ein- `id` Attribut. Legen Sie das `guid` -Attribut immer so fest, dass es dem Namen des `GuidSymbol` Elements entspricht, das den Befehlssatz darstellt, und legen Sie das- `id` Attribut auf den Namen des Elements fest, `IDSymbol` das das Menü, die Gruppe oder den Befehl im `Symbols` Abschnitt darstellt.

#### <a name="to-define-ui-elements"></a>So definieren Sie Benutzeroberflächen Elemente

1. Wenn Sie neue Menüs, Untermenüs, Kontextmenüs oder Symbolleisten definieren, fügen Sie dem-Element ein- `Menus` Element hinzu `Commands` . Fügen Sie dann für jedes Menü, das erstellt werden soll, dem-Element ein [Menü](../../extensibility/menu-element.md) Element hinzu `Menus` .

    Legen `guid` Sie das-Attribut und das- `id` Attribut des-Elements fest `Menu` , und legen Sie dann das- `type` Attribut auf die gewünschte Art von Menü fest. Sie können auch das- `priority` Attribut festlegen, um die relative Position des Menüs in der übergeordneten Gruppe festzulegen.

   > [!NOTE]
   > Das `priority` -Attribut gilt nicht für Symbolleisten und Kontextmenüs.

2. Alle Befehle in der Visual Studio-IDE müssen von Befehls Gruppen gehostet werden, bei denen es sich um die direkt untergeordneten Elemente von Menüs und Symbolleisten handelt. Wenn Sie der IDE neue Menüs oder Symbolleisten hinzufügen, müssen diese neue Befehls Gruppen enthalten. Sie können auch Befehls Gruppen zu vorhandenen Menüs und Symbolleisten hinzufügen, sodass Sie Ihre Befehle visuell gruppieren können.

    Wenn Sie neue Befehls Gruppen hinzufügen, müssen Sie zuerst ein `Groups` -Element erstellen und diesem dann ein [Group](../../extensibility/group-element.md) -Element für jede Befehlsgruppe hinzufügen.

    Legen `guid` Sie das-Attribut und das- `id` Attribut für jedes `Group` Element fest, und legen Sie dann das-Attribut fest, `priority` um die relative Position der Gruppe im übergeordneten Menü herzustellen. Weitere Informationen finden Sie unter [Erstellen wiederverwendbarer Gruppen von Schalt](../../extensibility/creating-reusable-groups-of-buttons.md)Flächen.

3. Wenn Sie der IDE neue Befehle hinzufügen, fügen Sie dem-Element ein- `Buttons` Element hinzu `Commands` . Fügen Sie dann für jeden Befehl dem-Element ein [Button](../../extensibility/button-element.md) -Element hinzu `Buttons` .

   1. Legen `guid` Sie das-Attribut und das- `id` Attribut für jedes `Button` Element fest, und legen Sie das- `type` Attribut auf die gewünschte Art von Schaltfläche fest. Sie können auch das- `priority` Attribut festlegen, um die relative Position des Befehls in der übergeordneten Gruppe festzulegen.

       > [!NOTE]
       > Verwenden Sie dies `type="button"` für Standardmenü Befehle und Schaltflächen auf Symbolleisten.

   2. `Button`Fügen Sie im-Element ein [Strings](../../extensibility/strings-element.md) -Element hinzu, das ein [ButtonText](../../extensibility/buttontext-element.md) -Element und ein [CommandName](../../extensibility/commandname-element.md) -Element enthält. Das- `ButtonText` Element stellt die Text Bezeichnung für ein Menü Element oder die QuickInfo für eine Symbolleisten-Schaltfläche bereit. Das- `CommandName` Element stellt den Namen des Befehls bereit, der in der Befehlszeile verwendet werden soll.

   3. Wenn der Befehl ein Symbol enthält, erstellen Sie ein [Symbol](../../extensibility/icon-element.md) Element im `Button` -Element, und legen Sie dessen `guid` -und- `id` Attribute auf das- `Bitmap` Element für das Symbol fest.

       > [!NOTE]
       > Symbolleisten-Schaltflächen müssen Symbole aufweisen.

   Weitere Informationen finden Sie unter [MenuCommands im Vergleich zu olemenucommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

4. Wenn für einen ihrer Befehle Symbole erforderlich sind, fügen Sie dem-Element ein [Bitmaps](../../extensibility/bitmaps-element.md) -Element hinzu `Commands` . Fügen Sie dann für jedes Symbol dem-Element ein [Bitmap](../../extensibility/bitmap-element.md) -Element hinzu `Bitmaps` . Hier geben Sie den Speicherort der Bitmap-Ressource an. Weitere Informationen finden Sie unter [Hinzufügen von Symbolen zu Menübefehlen](../../extensibility/adding-icons-to-menu-commands.md).

   Sie können sich auf die Struktur der Struktur verlassen, um die meisten Menüs, Gruppen und Befehle ordnungsgemäß zu platzieren. Für sehr große Befehls Sätze oder wenn ein Menü, eine Gruppe oder ein Befehl an mehreren Stellen angezeigt werden muss, empfiehlt es sich, die Befehls Platzierung anzugeben.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Zum Platzieren von Benutzeroberflächen Elementen in der IDE

1. Erstellen Sie für die typische Verarbeitung ein `Parent` -Element in `Menu` jedem `Group` -,-und- `Command` Element, das im Paket definiert ist.

    Das Ziel des- `Parent` Elements ist das Menü oder die Gruppe, das das Menü, die Gruppe oder den Befehl enthält.

   1. Legen Sie das- `guid` Attribut auf den Namen des `GuidSymbol` Elements fest, das den Befehlssatz definiert. Wenn das Ziel Element nicht Teil Ihres Pakets ist, verwenden Sie die GUID für diesen Befehlssatz, wie in der entsprechenden *vsct* -Datei definiert.

   2. Legen Sie das-Attribut so fest, dass es `id` mit dem- `id` Attribut im Zielmenü oder in der Eine Auflistung der Menüs und Gruppen, die von Visual Studio verfügbar gemacht werden, finden Sie unter [GUIDs und IDs von Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) , [GUIDs und IDs von Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Wenn Sie über eine große Anzahl von Benutzeroberflächen Elementen in der IDE verfügen oder über Elemente verfügen, die an mehreren Stellen angezeigt werden sollen, definieren Sie Ihre Platzierung im [commandplacement](../../extensibility/commandplacements-element.md) -Element, wie in den folgenden Schritten gezeigt.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>So verwenden Sie die Befehls Platzierung zum Platzieren von Benutzeroberflächen Elementen in der IDE

1. Fügen Sie nach dem `Commands`-Element ein `CommandPlacements`-Element hinzu.

2. `CommandPlacements`Fügen Sie im-Element ein- `CommandPlacement` Element für jedes Menü, jede Gruppe oder jeden Befehl hinzu, der platziert werden soll.

    Jedes `CommandPlacement` Element oder `Parent` Element platziert ein Menü, eine Gruppe oder einen Befehl an einem IDE-Speicherort. Ein Benutzeroberflächen Element kann nur über ein übergeordnetes Element verfügen, aber es kann über mehrere Befehls Platzierungen verfügen. Fügen Sie `CommandPlacement` für jeden Speicherort ein-Element hinzu, um ein UI-Element an mehreren Speicherorten zu platzieren.

3. Legen `guid` Sie das-Attribut und das- `id` Attribut für jedes- `CommandPlacement` Element wie bei einem-Element auf das hostingmenü oder die hostinggruppe fest `Parent` . Sie können auch das- `priority` Attribut festlegen, um die relative Position des Benutzeroberflächen Elements festzulegen.

   Sie können die Platzierung durch die über-und Befehls Platzierung vermischen. Für sehr große Befehls Sätze wird jedoch empfohlen, nur die Befehls Platzierung zu verwenden.

### <a name="add-specialized-behaviors"></a>Hinzufügen spezieller Verhaltensweisen
 Sie können das [CommandFlag](../../extensibility/command-flag-element.md) -Element verwenden, um das Verhalten von Menüs und Befehlen zu ändern, um z. b. das Aussehen und die Sichtbarkeit zu ändern. Sie können sich auch darauf auswirken, wenn ein Befehl mit dem [visibilityeinschränselement](../../extensibility/visibilityconstraints-element.md) sichtbar ist, oder mithilfe des [KeyBinding](../../extensibility/keybindings-element.md) -Elements Tastenkombinationen hinzufügen. Bestimmte Arten von Menüs und Befehlen verfügen bereits über ein spezielles Verhalten, das bereits integriert ist.

#### <a name="to-add-specialized-behaviors"></a>So fügen Sie spezialisierte Verhalten hinzu

1. Wenn Sie ein UI-Element nur in bestimmten UI-Kontexten sichtbar machen möchten, z. b. Wenn eine Projekt Mappe geladen wird, verwenden Sie Sichtbarkeits Einschränkungen.

   1. Fügen Sie nach dem `Commands`-Element ein `VisibilityConstraints`-Element hinzu.

   2. Fügen Sie für jedes Benutzeroberflächen Element, das eingeschränkt werden soll, ein [visibilityitem](../../extensibility/visibilityitem-element.md) -Element hinzu.

   3. `VisibilityItem`Legen Sie für jedes Element das `guid` -Attribut und das- `id` Attribut auf das Menü, die Gruppe oder den Befehl fest, und legen Sie dann das `context` Attribut wie in der-Klasse definiert auf den gewünschten Benutzeroberflächen Kontext fest <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> .

2. Verwenden Sie mindestens eine der folgenden Befehlsflags, um die Sichtbarkeit oder Verfügbarkeit eines UI-Elements im Code festzulegen:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Weitere Informationen finden Sie unter dem [CommandFlag](../../extensibility/command-flag-element.md) -Element.

3. Verwenden Sie mindestens eine der folgenden Befehlsflags, um zu ändern, wie ein Element angezeigt wird, oder um seine Darstellung dynamisch zu ändern:

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   Weitere Informationen finden Sie unter dem [CommandFlag](../../extensibility/command-flag-element.md) -Element.

4. Verwenden Sie mindestens eine der folgenden Befehlsflags, um zu ändern, wie ein Element reagiert, wenn es Befehle empfängt:

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   Weitere Informationen finden Sie unter dem [CommandFlag](../../extensibility/command-flag-element.md) -Element.

5. Fügen Sie im- `ButtonText` Element für das Menü oder Menü Element ein kaufmännisches und-Zeichen (&) hinzu, um eine Menü abhängige Tastenkombination an ein Menü oder Element in einem Menü anzufügen. Das Zeichen, das auf das kaufmännische und-Zeichen folgt, ist die aktive Tastenkombination, wenn das übergeordnete Menü geöffnet ist.

6. Verwenden Sie das [KeyBinding](../../extensibility/keybindings-element.md) -Element, um eine Menü unabhängige Tastenkombination an einen Befehl anzufügen. Weitere Informationen finden Sie unter dem [KeyBinding](../../extensibility/keybinding-element.md) -Element.

7. Verwenden Sie das-Element, um den Menütext zu lokalisieren `LocCanonicalName` . Weitere Informationen finden Sie unter dem [Strings](../../extensibility/strings-element.md) -Element.

   Einige Menü-und Schaltflächen Typen enthalten spezielles Verhalten. In der folgenden Liste werden einige spezielle Menü-und Schaltflächen Typen beschrieben. Informationen zu anderen Typen finden Sie `types` in den Attribut Beschreibungen in den [Menü](../../extensibility/menu-element.md)-, [](../../extensibility/combo-element.md) [Schalt](../../extensibility/button-element.md)Flächen-und Kombinations Elementen.

   - Kombinations Feld: ein Kombinations Feld ist eine Dropdown Liste, die auf einer Symbolleiste verwendet werden kann. Wenn Sie der Benutzeroberfläche Kombinations Felder hinzufügen möchten, erstellen Sie ein [Combos](../../extensibility/combos-element.md) -Element im- `Commands` Element. Fügen Sie dann dem- `Combos` Element ein- `Combo` Element für jedes hinzu zufügende Kombinations Feld hinzu. `Combo` -Elemente verfügen über dieselben Attribute und untergeordneten Elemente wie `Button` -Elemente sowie über `DefaultWidth` -und- `idCommandList` Attribute. Das `DefaultWidth` -Attribut legt die Breite in Pixel fest, und das- `idCommandList` Attribut verweist auf eine Befehls-ID, die zum Auffüllen des Kombinations Felds verwendet wird.

   - Menü Controller: ein Menü Controller ist eine Schaltfläche, die einen Pfeil daneben enthält. Wenn Sie auf den Pfeil klicken, wird eine Liste geöffnet. Um der Benutzeroberfläche einen Menü Controller hinzuzufügen, erstellen Sie ein-Element, und legen Sie das zugehörige- `Menu` `type` Attribut `MenuController` `MenuControllerLatched` abhängig vom gewünschten Verhalten auf oder fest. Um einen Menü Controller aufzufüllen, legen Sie ihn als übergeordnetes Element eines- `Group` Elements fest. Im Menü Controller werden alle untergeordneten Elemente dieser Gruppe in der Dropdown Liste angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Vsct-XML-Schema Referenz](../../extensibility/vsct-xml-schema-reference.md)