---
title: Hinzufügen eines Untermenüs zu einem Menü | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Untermenü erstellen, es der Visual Studio-Menüleiste hinzufügen und dem Untermenü einen neuen Befehl hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b784cae836f1a5cae520a9650c8f396ccc960a72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951510"
---
# <a name="add-a-submenu-to-a-menu"></a>Hinzufügen eines Untermenüs zu einem Menü
Diese exemplarische Vorgehensweise basiert auf der Demo in [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) , indem gezeigt wird, wie ein Untermenü zum Menü **Testmenü** hinzugefügt wird.

 Ein Untermenü ist ein sekundäres Menü, das in einem anderen Menü angezeigt wird. Ein Untermenü kann durch den Pfeil identifiziert werden, der dem Namen folgt. Wenn Sie auf den Namen klicken, werden das Untermenü und seine Befehle angezeigt.

 In dieser exemplarischen Vorgehensweise wird ein Untermenü in einem Menü auf der Visual Studio-Menüleiste erstellt und ein neuer Befehl in das Untermenü eingefügt. In der exemplarischen Vorgehensweise wird auch der neue Befehl implementiert.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Hinzufügen eines Untermenüs zu einem Menü

1. Führen Sie die Schritte unter [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) aus, um das Projekt und das Menü Element zu erstellen. Bei den Schritten in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Name des VSIX-Projekts ist `TopLevelMenu` .

2. Öffnen Sie die Datei " *testcommandpackage. vsct*". `<Symbols>`Fügen Sie im-Abschnitt ein `<IDSymbol>` -Element für das Untermenü hinzu, eines für die unter Menü Gruppe und eines für den Befehl, alle im `<GuidSymbol>` Knoten mit dem Namen "guidtoplevelmenucmdset". Dabei handelt es sich um denselben Knoten, der das `<IDSymbol>` -Element für das Menü der obersten Ebene enthält.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Fügen Sie das neu erstellte Untermenü zum- `<Menus>` Abschnitt hinzu.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     Das GUID-ID-Paar des übergeordneten Elements gibt die Menü Gruppe an, die in [der Visual Studio-Menüleiste einem Menü hinzugefügt](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)wurde, und ist ein untergeordnetes Element des Menüs der obersten Ebene.

4. Fügen Sie dem Abschnitt die in Schritt 2 definierte Menü Gruppe hinzu, `<Groups>` und legen Sie Sie als untergeordnetes Element des Untermenüs ab.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Fügen Sie dem-Abschnitt ein neues- `<Button>` Element hinzu `<Buttons>` , um den in Schritt 2 erstellten Befehl als Element im Untermenü zu definieren.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Die experimentelle Instanz sollte angezeigt werden.

7. Klicken Sie auf **testmenu** , um das neue Untermenü mit dem Namen **Untermenü** anzuzeigen. Klicken Sie auf **Untermenü** , um das Untermenü zu öffnen, und sehen Sie sich den neuen Befehl **Test Sub** an. Beachten Sie, dass durch Klicken auf den **Unterbefehl "Test** " nichts

## <a name="add-a-command"></a>Befehl hinzufügen

1. Öffnen Sie *TestCommand.cs* , und fügen Sie die folgende Befehls-ID nach der vorhandenen Befehls-ID ein.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Fügen Sie den Unterbefehl hinzu. Suchen Sie den befehlskonstruktor. Fügen Sie die folgenden Zeilen direkt nach dem Aufrufder- `AddCommand` Methode hinzu.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Der `SubItemCallback` Befehls Handler wird später definiert. Der Konstruktor sollte nun wie folgt aussehen:

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Fügen Sie `SubItemCallback()`hinzu. Dies ist die Methode, die aufgerufen wird, wenn auf den neuen Befehl im Untermenü geklickt wird.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        IVsUIShell uiShell = this.package.GetService<SVsUIShell, IVsUIShell>();
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

5. Klicken Sie im Menü **Testmenü** auf **Untermenü** , und klicken Sie dann auf **Unterbefehl testen**. Ein Meldungs Feld sollte angezeigt werden, und der Text "Test Befehl in TestCommand. subitemcallback ()" wird angezeigt.

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
