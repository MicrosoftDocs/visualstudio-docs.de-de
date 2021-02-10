---
title: Hinzufügen eines Befehls zum Projektmappen-Explorer Symbolleiste | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Schaltfläche hinzufügen, die einen Befehl auf der Projektmappen-Explorer Symbolleiste in Visual Studio ausführt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 305966a4cd4ec67994ac3dbd6c7ba0e25a14172f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951692"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Hinzufügen eines Befehls zum Projektmappen-Explorer Symbolleiste
In dieser exemplarischen Vorgehensweise wird das Hinzufügen einer Schaltfläche zur **Projektmappen-Explorer** Symbolleiste erläutert.

 Jeder Befehl auf einer Symbolleiste oder einem Menü wird in Visual Studio als Schaltfläche bezeichnet. Wenn auf die Schaltfläche geklickt wird, wird der Code im Befehls Handler ausgeführt. In der Regel werden verwandte Befehle gruppiert, um eine Gruppe zu bilden. Menüs oder Symbolleisten fungieren als Container für Gruppen. Priorität bestimmt die Reihenfolge, in der einzelne Befehle in einer Gruppe im Menü oder auf der Symbolleiste angezeigt werden. Sie können verhindern, dass eine Schaltfläche auf der Symbolleiste oder im Menü angezeigt wird, indem Sie die Sichtbarkeit steuern. Ein Befehl, der in einem `<VisibilityConstraints>` Abschnitt der *vsct* -Datei aufgelistet ist, wird nur im zugeordneten Kontext angezeigt. Die Sichtbarkeit kann nicht auf Gruppen angewendet werden.

 Weitere Informationen zu Menüs, Symbolleisten Befehlen und *vsct* -Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Verwenden Sie XML-Befehls Tabellen Dateien (*vsct*) anstelle von Befehls Tabellen Konfigurationsdateien (*. CTC*), um zu definieren, wie Menüs und Befehle in ihren VSPackages angezeigt werden. Weitere Informationen finden Sie unter [Visual Studio Command Table (. Vsct-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl
 Erstellen Sie ein VSIX-Projekt mit dem Namen `SolutionToolbar` . Fügen Sie eine Menübefehls Element-Vorlage mit dem Namen **ToolBarButton** hinzu. Weitere Informationen hierzu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Hinzufügen einer Schaltfläche zur Projektmappen-Explorer Symbolleiste
 In diesem Abschnitt der exemplarischen Vorgehensweise wird gezeigt, wie Sie der **Projektmappen-Explorer** Symbolleiste eine Schaltfläche hinzufügen. Wenn auf die Schaltfläche geklickt wird, wird der Code in der Rückruf Methode ausgeführt.

1. Wechseln Sie in der Datei *toolbarbuttonpackage. vsct* zum  `<Symbols>` Abschnitt. Der `<GuidSymbol>`  Knoten enthält die Menü Gruppe und den Befehl, die von der Paket Vorlage generiert wurden. Fügen Sie `<IDSymbol>` diesem Knoten ein Element hinzu, um die Gruppe zu deklarieren, die Ihren Befehl enthalten soll.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. `<Groups>`Definieren Sie im-Abschnitt nach dem vorhandenen Gruppen Eintrag die neue Gruppe, die Sie im vorherigen Schritt deklariert haben.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Legen Sie das übergeordnete GUID: ID-Paar auf fest `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` , und legen Sie diese Gruppe auf der **Projektmappen-Explorer** Symbolleiste ab. Wenn Sie einen Wert mit hoher Priorität festlegen, wird dieser nach den anderen Befehls Gruppen platziert.

3. `<Buttons>`Ändern Sie im-Abschnitt die übergeordnete ID des generierten `<Button>` Eintrags, um die Gruppe widerzuspiegeln, die Sie im vorherigen Schritt definiert haben. Das geänderte `<Button>` Element sollte wie folgt aussehen:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.

     Auf der **Projektmappen-Explorer** Symbolleiste sollte die neue Befehls Schaltfläche rechts neben den vorhandenen Schaltflächen angezeigt werden. Das Schaltflächen Symbol ist das durchgestrichen.

5. Klicken Sie auf die Schaltfläche neu.

     Ein Dialogfeld, in dem die Meldung **toolbarbuttonpackage innerhalb von solutiontoolbar. ToolBarButton. MenuItemCallBack ()** angezeigt wird, sollte angezeigt werden.

## <a name="control-the-visibility-of-a-button"></a>Steuern der Sichtbarkeit einer Schaltfläche
 In diesem Abschnitt der exemplarischen Vorgehensweise wird gezeigt, wie Sie die Sichtbarkeit einer Schaltfläche auf einer Symbolleiste steuern können. Durch Festlegen eines Kontexts auf ein oder mehrere Projekte im- `<VisibilityConstraints>` Abschnitt der Datei " *solutiontoolbar. vsct* " wird eine Schaltfläche so eingeschränkt, dass Sie nur angezeigt wird, wenn ein Projekt oder Projekte geöffnet sind.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>So zeigen Sie eine Schaltfläche an, wenn ein oder mehrere Projekte geöffnet sind

1. `<Buttons>`Fügen Sie im-Abschnitt von *toolbarbuttonpackage. vsct* dem vorhandenen `<Button>` -Element zwischen den Tags und zwei Befehlsflags hinzu `<Strings>` `<Icons>` .

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Die `DefaultInvisible` -und- `DynamicVisibility` Flags müssen festgelegt werden, damit Einträge im- `<VisibilityConstraints>` Abschnitt wirksam werden können.

2. Erstellen Sie einen `<VisibilityConstraints>` Abschnitt mit zwei `<VisibilityItem>` Einträgen. Fügen Sie den neuen Abschnitt direkt hinter das `</Commands>` Endtag ein.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    Jedes Sichtbarkeits Element stellt eine Bedingung dar, unter der die angegebene Schaltfläche angezeigt wird. Wenn Sie mehrere Bedingungen anwenden möchten, müssen Sie mehrere Einträge für die gleiche Schaltfläche erstellen.

3. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.

    Die **Projektmappen-Explorer** Symbolleiste enthält nicht die Schaltfläche durchgestrichen.

4. Öffnen Sie eine beliebige Projekt Mappe, die ein Projekt enthält.

    Die Schaltfläche durchgestrichen wird auf der Symbolleiste rechts neben den vorhandenen Schaltflächen angezeigt.

5. Klicken Sie im Menü **Datei** auf **Projektmappe schließen**. Die Schaltfläche wird nicht mehr auf der Symbolleiste angezeigt.

   Die Sichtbarkeit der Schaltfläche wird von gesteuert, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bis das VSPackage geladen wurde. Nachdem das VSPackage geladen wurde, wird die Sichtbarkeit der Schaltfläche durch das VSPackage gesteuert.  Weitere Informationen finden Sie unter [MenuCommands im Vergleich zu olemenucommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)