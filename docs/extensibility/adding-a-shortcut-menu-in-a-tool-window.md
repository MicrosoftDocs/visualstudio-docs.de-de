---
title: Hinzufügen eines Kontextmenüs in einem Tool Fenster | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einem Tool Fenster in Visual Studio ein Kontextmenü hinzufügen, das angezeigt wird, wenn mit der rechten Maustaste auf eine Schaltfläche, ein Textfeld oder einen Fenster Hintergrund geklickt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a35652c0eacf22a46eed3f3fc64c3bcc0d6d10ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951536"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Hinzufügen eines Kontextmenüs in einem Tool Fenster
Diese exemplarische Vorgehensweise enthält ein Kontextmenü in einem Tool Fenster. Ein Kontextmenü ist ein Menü, das angezeigt wird, wenn ein Benutzer mit der rechten Maustaste auf eine Schaltfläche, ein Textfeld oder einen Fenster Hintergrund klickt. Befehle in einem Kontextmenü Verhalten sich genauso wie Befehle in anderen Menüs oder Symbolleisten. Um ein Kontextmenü zu unterstützen, geben Sie es in der *vsct* -Datei an, und zeigen Sie es als Antwort auf das Klicken mit der rechten Maustaste an.

Ein Tool Fenster besteht aus einem WPF-Benutzer Steuerelement in einer benutzerdefinierten Tool Fenster Klasse, die von erbt <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein Kontextmenü als Visual Studio-Menü erstellen, indem Sie Menü Elemente in der *vsct* -Datei deklarieren und dann das verwaltete Paket Framework verwenden, um Sie in der Klasse zu implementieren, die das Tool Fenster definiert. Dieser Ansatz ermöglicht den Zugriff auf Visual Studio-Befehle, Benutzeroberflächen Elemente und das Automatisierungs Objektmodell.

Wenn das Kontextmenü nicht auf die Visual Studio-Funktionalität zugreifen kann, können Sie alternativ die- <xref:System.Windows.FrameworkElement.ContextMenu%2A> Eigenschaft eines XAML-Elements im Benutzer Steuerelement verwenden. Weitere Informationen finden Sie unter [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Voraussetzungen
Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Erstellen des Kontextmenü Pakets für das Tool Fenster

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `TWShortcutMenu` , und fügen Sie ihm eine Tool Fenster Vorlage mit dem Namen **ShortcutMenu** hinzu. Weitere Informationen zum Erstellen eines Tool Fensters finden Sie unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Angeben des Kontextmenüs
Mit einem Kontextmenü, wie dem in dieser exemplarischen Vorgehensweise gezeigten Kontextmenü, kann der Benutzer aus einer Liste von Farben auswählen, die zum Ausfüllen des Hintergrunds des Tool Fensters verwendet werden.

1. Suchen Sie in *shortcutmenupackage. vsct* im guidsymbol-Element namens guidshortcutmenupackagecmdset, und deklarieren Sie das Kontextmenü, die Kontextmenü Gruppe und Menü Optionen. Das guidsymbol-Element sollte nun wie folgt aussehen:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Erstellen Sie direkt vor dem Buttons-Element ein Menüs-Element, und definieren Sie dann das Kontextmenü.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Ein Kontextmenü weist kein übergeordnetes Element auf, da es nicht Teil eines Menüs oder einer Symbolleiste ist.

3. Erstellen Sie ein groups-Element mit einem Group-Element, das die Kontextmenü Elemente enthält, und verknüpfen Sie die Gruppe mit dem Kontextmenü.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Definieren Sie im Element Buttons die einzelnen Befehle, die im Kontextmenü angezeigt werden. Das Buttons-Element sollte wie folgt aussehen:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. Fügen Sie in *ShortcutMenuCommand.cs* die Definitionen für die Befehlssatz-GUID, das Kontextmenü und die Menü Elemente hinzu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Dabei handelt es sich um dieselben Befehls-IDs, die im Abschnitt "Symbole" der Datei " *shortcutmenupackage. vsct* " definiert sind. Die Kontext Gruppe ist hier nicht enthalten, da Sie nur in der *vsct* -Datei erforderlich ist.

## <a name="implementing-the-shortcut-menu"></a>Implementieren des Kontextmenüs
 In diesem Abschnitt werden das Kontextmenü und seine Befehle implementiert.

1. In *ShortcutMenu.cs* kann das Tool Fenster den Menübefehls Dienst erhalten, aber das Steuerelement, das darin enthalten ist, ist nicht möglich. Die folgenden Schritte zeigen, wie Sie den Menübefehls Dienst dem Benutzer Steuerelement zur Verfügung stellen.

2. Fügen Sie in *ShortcutMenu.cs* die folgenden using-Direktiven hinzu:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Überschreiben Sie die Initialize ()-Methode des Tool Fensters, um den Menübefehls Dienst zu erhalten und das Steuerelement hinzuzufügen. übergeben Sie dabei den Menübefehls Dienst an den Konstruktor:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. Entfernen Sie im ShortcutMenu-Tool Fenster-Konstruktor die Zeile, in der das Steuerelement hinzugefügt wird. Der Konstruktor sollte nun wie folgt aussehen:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. Fügen Sie in *ShortcutMenuControl.XAML.cs* ein privates Feld für den Menübefehls Dienst hinzu, und ändern Sie den Steuerelement-Konstruktor, sodass er den Menübefehls Dienst übernimmt. Verwenden Sie dann den Menübefehls Dienst, um die Kontextmenü Befehle hinzuzufügen. Der shortcutmenucontrol-Konstruktor sollte jetzt wie der folgende Code aussehen. Der Befehls Handler wird später definiert.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. Fügen Sie in *shortcutmenucontrol. XAML* <xref:System.Windows.UIElement.MouseRightButtonDown> dem Element der obersten Ebene ein-Ereignis hinzu <xref:System.Windows.Controls.UserControl> . Die XAML-Datei sollte nun wie folgt aussehen:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. Fügen Sie in *ShortcutMenuControl.XAML.cs* einen Stub für den Ereignishandler hinzu.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Fügen Sie der gleichen Datei die folgenden using-Direktiven hinzu:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Implementieren Sie das- `MyToolWindowMouseRightButtonDown` Ereignis wie folgt.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    Dadurch wird ein- <xref:System.ComponentModel.Design.CommandID> Objekt für das Kontextmenü erstellt, die Position des Mausklicks identifiziert und das Kontextmenü an dieser Stelle mithilfe der- <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> Methode geöffnet.

10. Implementieren Sie den Befehls Handler.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    In diesem Fall behandelt nur eine Methode Ereignisse für alle Menü Elemente, indem identifiziert <xref:System.ComponentModel.Design.CommandID> und die Hintergrundfarbe entsprechend festgelegt wird. Wenn die Menü Elemente nicht verknüpfte Befehle enthielt, haben Sie für jeden Befehl einen separaten Ereignishandler erstellt.

## <a name="test-the-tool-window-features"></a>Testen der Tool Fenster Funktionen

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.

2. Klicken Sie in der experimentellen Instanz auf Ansicht > **Weitere Fenster**, und klicken Sie dann auf **ShortcutMenu**. Dadurch sollte das Tool Fenster angezeigt werden.

3. Klicken Sie mit der rechten Maustaste in den Text des Tool Fensters. Ein Kontextmenü mit einer Liste von Farben sollte angezeigt werden.

4. Klicken Sie im Kontextmenü auf eine Farbe. Die Hintergrundfarbe des Tool Fensters sollte in die ausgewählte Farbe geändert werden.

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
- [Verwenden von und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)
