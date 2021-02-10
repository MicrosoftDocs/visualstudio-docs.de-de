---
title: Hinzufügen eines Menüs zur Visual Studio-Menüleiste | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Menü in der Menüleiste der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6bd568e53c3a74819f642f0593524b314e065afb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951562"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Hinzufügen eines Menüs zur Visual Studio-Menüleiste

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein Menü zur Menüleiste der integrierten Entwicklungsumgebung (IDE) von Visual Studio hinzufügen. Die IDE-Menüleiste enthält Menü Kategorien wie z. b. **Datei**, **Bearbeiten**, **Ansicht**, **Fenster** und **Hilfe**.

Bevor Sie der Visual Studio-Menüleiste ein neues Menü hinzufügen, sollten Sie überprüfen, ob die Befehle in einem vorhandenen Menü platziert werden sollen. Weitere Informationen zur Befehls Platzierung finden Sie unter [Menüs und Befehle für Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Menüs werden in der *vsct* -Datei des Projekts deklariert. Weitere Informationen zu Menüs und *vsct* -Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

Wenn Sie diese exemplarische Vorgehensweise durcharbeiten, können Sie ein Menü mit dem Namen **Testmenü** erstellen, das einen Befehl enthält.

:::moniker range=">=vs-2019"
> [!NOTE]
> Ab Visual Studio 2019 werden die Menüs der obersten Ebene, die von Erweiterungen beigetragen werden, im Menü **Erweiterungen** abgelegt.
:::moniker-end

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Erstellen eines VSIX-Projekts, das über eine benutzerdefinierte Befehls Element Vorlage verfügt

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `TopLevelMenu` . Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** ", indem Sie nach "VSIX" suchen.  Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

::: moniker range="vs-2017"

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **TestCommand** hinzu. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >   **Neues Element** hinzufügen aus. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#/Erweiterbarkeit** , und wählen Sie **benutzerdefinierter Befehl** aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in *TestCommand.cs*.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **TestCommand** hinzu. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >   **Neues Element** hinzufügen aus. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#/Erweiterbarkeit** , und wählen Sie dann **Befehl** aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in *TestCommand.cs*.

::: moniker-end

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Erstellen eines Menüs auf der IDE-Menüleiste

::: moniker range="vs-2017"

1. Öffnen Sie in **Projektmappen-Explorer** die Datei " *testcommandpackage. vsct*".

    Am Ende der Datei befindet sich ein `<Symbols>` Knoten, der mehrere `<GuidSymbol>` Knoten enthält. Fügen Sie im Knoten mit dem Namen `guidTestCommandPackageCmdSet` ein neues Symbol wie folgt hinzu:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Erstellen Sie `<Menus>` direkt zuvor einen leeren Knoten im `<Commands>` Knoten `<Groups>` . `<Menus>`Fügen Sie im-Knoten `<Menu>` wie folgt einen-Knoten hinzu:

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    Der `guid` -Wert und der- `id` Wert des Menüs geben den Befehlssatz und das jeweilige Menü im Befehlssatz an.

    Die `guid` -und-Werte der über `id` geordneten positionieren das Menü im-Abschnitt der Visual Studio-Menüleiste, die die Menüs Tools und Add-Ins enthält.

    Das- `<ButtonText>` Element gibt an, dass der Text im Menü Element angezeigt werden soll.

3. Suchen Sie im `<Groups>` `<Group>` -Abschnitt nach, und ändern Sie das-Element so, dass `<Parent>` es auf das soeben hinzugefügte Menü verweist:

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Dadurch wird der Gruppen Teil des neuen Menüs.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie in **Projektmappen-Explorer** die Datei " *toplevelmenupackage. vsct*".

    Am Ende der Datei befindet sich ein `<Symbols>` Knoten, der mehrere `<GuidSymbol>` Knoten enthält. Fügen Sie im Knoten mit dem Namen `guidTopLevelMenuPackageCmdSet` ein neues Symbol wie folgt hinzu:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Erstellen Sie `<Menus>` direkt zuvor einen leeren Knoten im `<Commands>` Knoten `<Groups>` . `<Menus>`Fügen Sie im-Knoten `<Menu>` wie folgt einen-Knoten hinzu:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    Der `guid` -Wert und der- `id` Wert des Menüs geben den Befehlssatz und das jeweilige Menü im Befehlssatz an.

    Die `guid` -und-Werte der über `id` geordneten positionieren das Menü im-Abschnitt der Visual Studio-Menüleiste, die die Menüs Tools und Add-Ins enthält.

    Das- `<ButtonText>` Element gibt an, dass der Text im Menü Element angezeigt werden soll.

3. Suchen Sie im `<Groups>` `<Group>` -Abschnitt nach, und ändern Sie das-Element so, dass `<Parent>` es auf das soeben hinzugefügte Menü verweist:

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Dadurch wird der Gruppen Teil des neuen Menüs.

::: moniker-end

4. Suchen Sie im- `<Buttons>` Abschnitt nach dem- `<Button>` Knoten. Ändern Sie dann im- `<Strings>` Knoten das- `<ButtonText>` Element in `Test Command` .

    Beachten Sie, dass die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paket Vorlage ein-Element generiert hat `Button` , dessen übergeordnetes Element auf festgelegt ist `MyMenuGroup` . Daher wird dieser Befehl im Menü angezeigt.

## <a name="build-and-test-the-extension"></a>Erstellen und Testen der Erweiterung

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Eine Instanz der experimentellen Instanz sollte angezeigt werden.

::: moniker range="vs-2017"

2. Die Menüleiste in der experimentellen Instanz sollte ein Menü Menü Menü " **Test** " enthalten.

::: moniker-end

::: moniker range=">=vs-2019"

2. Das Menü **Erweiterungen** in der experimentellen Instanz sollte ein Menü Menü Menü " **Test** " enthalten.

::: moniker-end

3. Klicken Sie im Menü **Test** auf **Test Befehl**.

    Es sollte ein Meldungs Feld angezeigt werden, in dem die Meldung "TestCommand in toplevelmenu. TestCommand. MenuItemCallBack ()" angezeigt wird.

## <a name="see-also"></a>Weitere Informationen

- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
