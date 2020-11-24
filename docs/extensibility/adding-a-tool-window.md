---
title: Hinzufügen eines Tool Fensters | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Tool Fenster erstellen und in Visual Studio integrieren, indem Sie dem Tool Fenster ein-Steuerelement und eine Symbolleiste mit einem Befehl hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184e04e74e2065ea2a9e1bcd41b2e878981dd218
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597989"
---
# <a name="add-a-tool-window"></a>Hinzufügen eines Tool Fensters

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie ein Tool Fenster erstellen und es auf folgende Weise in Visual Studio integrieren:

- Fügen Sie dem Tool Fenster ein-Steuerelement hinzu.

- Fügen Sie einem Tool Fenster eine Symbolleiste hinzu.

- Fügen Sie der Symbolleiste einen Befehl hinzu.

- Implementieren Sie die Befehle.

- Legen Sie die Standardposition für das Tool Fenster fest.

## <a name="prerequisites"></a>Voraussetzungen

Das Visual Studio SDK ist als optionales Feature in Visual Studio-Setup enthalten. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Erstellen eines Tool Fensters

1. Erstellen Sie ein Projekt namens **firsttoolwin** mithilfe der VSIX-Vorlage, und fügen Sie eine benutzerdefinierte Tool Fenster-Element Vorlage namens **firsttoolwindow** hinzu.

    > [!NOTE]
    > Weitere Informationen zum Erstellen einer Erweiterung mit einem Tool Fenster finden Sie unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Hinzufügen eines Steuer Elements zum Tool Fenster

1. Entfernen Sie das Standard Steuerelement. Öffnen Sie *firsttoolwindowcontrol. XAML* , und löschen Sie die Schaltfläche **Klicken Sie!** Schaltfläche.

2. Erweitern Sie in der **Toolbox** den Abschnitt **alle WPF** -Steuerelemente, und ziehen Sie das Steuer **Element Media Element** in das Formular **firsttoolwindowcontrol** . Wählen Sie das Steuerelement aus, und benennen Sie im **Eigenschaften** Fenster dieses Element **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Hinzufügen einer Symbolleiste zum Tool Fenster
Indem Sie eine Symbolleiste auf folgende Weise hinzufügen, gewährleisten Sie, dass die Farbverläufe und Farben mit dem Rest der IDE konsistent sind.

1. Öffnen Sie in **Projektmappen-Explorer** die Datei *firsttoolwindowpackage. vsct*. Die *vsct* -Datei definiert die grafischen Benutzeroberflächen Elemente (GUI) in Ihrem Tool Fenster mithilfe von XML.

2. Suchen Sie im- `<Symbols>` Abschnitt nach dem `<GuidSymbol>` Knoten, dessen- `name` Attribut ist `guidFirstToolWindowPackageCmdSet` . Fügen Sie der `<IDSymbol>` Liste der Elemente in diesem Knoten die folgenden zwei Elemente hinzu `<IDSymbol>` , um eine Symbolleiste und eine Symbolleisten Gruppe zu definieren.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Erstellen Sie direkt oberhalb des Abschnitts einen Abschnitt, der dem folgenden `<Buttons>` `<Menus>` ähnelt:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Es gibt mehrere verschiedene Arten von Menüs. Dieses Menü ist eine Symbolleiste in einem Tool Fenster, das durch das zugehörige-Attribut definiert wird `type` . Die `guid` -und- `id` Einstellungen bilden die voll qualifizierte ID der Symbolleiste. In der Regel `<Parent>` ist der eines Menüs die enthaltende Gruppe. Eine Symbolleiste wird jedoch als eigenes übergeordnetes Element definiert. Daher wird derselbe Bezeichner für das `<Menu>` -Element und das- `<Parent>` Element verwendet. Das `priority` Attribut ist nur "0".

4. Symbolleisten ähneln Menüs in vielerlei Hinsicht. So können z. b., wie ein Menü möglicherweise Gruppen von Befehlen hat, Symbolleisten auch Gruppen enthalten. (In Menüs werden die Befehls Gruppen durch horizontale Linien getrennt. Auf Symbolleisten werden die Gruppen nicht durch visuelle unter Teiler getrennt.)

    Fügen Sie einen `<Groups>` Abschnitt hinzu, der ein- `<Group>` Element enthält. Dadurch wird die Gruppe definiert, deren ID Sie im `<Symbols>` Abschnitt deklariert haben. Fügen Sie den `<Groups>` Abschnitt direkt nach dem- `<Menus>` Abschnitt hinzu.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Wenn Sie die übergeordnete GUID und die ID auf die GUID und die ID der Symbolleiste festlegen, fügen Sie die Gruppe der Symbolleiste hinzu.

## <a name="add-a-command-to-the-toolbar"></a>Fügen Sie der Symbolleiste einen Befehl hinzu.

Fügen Sie der Symbolleiste einen Befehl hinzu, der als Schaltfläche angezeigt wird.

1. Deklarieren Sie im- `<Symbols>` Abschnitt die folgenden idsymbol-Elemente direkt nach den Deklarationen der Symbolleiste und der Symbolleiste.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Fügen Sie im-Abschnitt ein Button-Element hinzu `<Buttons>` . Dieses Element wird auf der Symbolleiste im Tool Fenster mit einem **Suchsymbol** (Lupensymbol) angezeigt.

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. Öffnen Sie *FirstToolWindowCommand.cs* , und fügen Sie die folgenden Zeilen in der-Klasse direkt nach den vorhandenen Feldern hinzu.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Dadurch sind die Befehle im Code verfügbar.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Hinzufügen einer Media Player-Eigenschaft zu firsttoolwindowcontrol
In den Ereignis Handlern für die Symbolleisten-Steuerelemente muss Ihr Code auf das Media Player-Steuerelement zugreifen können, das ein untergeordnetes Element der firsttoolwindowcontrol-Klasse ist.

Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf *firsttoolwindowcontrol. XAML*, klicken Sie auf **Code anzeigen**, und fügen Sie der firsttoolwindowcontrol-Klasse den folgenden Code hinzu.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Instanziieren des Tool Fensters und der Symbolleiste
Fügen Sie eine Symbolleiste und einen Menübefehl hinzu, der das Dialogfeld " **Datei öffnen** " aufruft und die ausgewählte Mediendatei wieder gibt.

1. Öffnen Sie *FirstToolWindow.cs* , und fügen Sie die folgenden `using` Anweisungen hinzu:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Fügen Sie in der firsttoolwindow-Klasse einen öffentlichen Verweis auf das firsttoolwindowcontrol-Steuerelement hinzu.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Legen Sie diese Steuerelement Variable am Ende des Konstruktors auf das neu erstellte Steuerelement fest.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Instanziieren Sie die Symbolleiste innerhalb des Konstruktors.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. An diesem Punkt sollte der firsttoolwindow-Konstruktor wie folgt aussehen:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Fügen Sie der Symbolleiste den Menübefehl hinzu. Fügen Sie in der FirstToolWindowCommand.cs-Klasse die folgende using-Direktive hinzu:

    ```csharp
    using System.Windows.Forms;
    ```

7. Fügen Sie in der firsttoolwindowcommand-Klasse am Ende der ShowToolWindow ()-Methode den folgenden Code hinzu. Der ButtonHandler-Befehl wird im nächsten Abschnitt implementiert.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>So implementieren Sie einen Menübefehl im Tool Fenster

1. Fügen Sie in der firsttoolwindowcommand-Klasse eine ButtonHandler-Methode hinzu, die das Dialogfeld " **Datei öffnen** " aufruft. Wenn eine Datei ausgewählt wurde, wird die Mediendatei wiedergegeben.

2. Fügen Sie in der firsttoolwindowcommand-Klasse einen privaten Verweis auf das Fenster firsttoolwindow hinzu, das in der FindToolWindow ()-Methode erstellt wird.

    ```csharp
    private FirstToolWindow window;
    ```

3. Ändern Sie die ShowToolWindow ()-Methode, um das Fenster festzulegen, das Sie oben definiert haben (damit der Befehls Handler für ButtonHandler auf das Fenster Steuerelement zugreifen kann. Hier ist die Complete ShowToolWindow ()-Methode.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. Fügen Sie die ButtonHandler-Methode hinzu. Es wird ein OpenFileDialog-Dialogfeld erstellt, in dem der Benutzer die wieder zugebende Mediendatei angeben kann. Anschließend wird die ausgewählte Datei wiedergegeben.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Festlegen der Standardposition für das Tool Fenster

Geben Sie als nächstes einen Standard Speicherort in der IDE für das Tool Fenster an. Konfigurationsinformationen für das Tool Fenster befinden sich in der Datei *FirstToolWindowPackage.cs* .

1. Suchen Sie in *FirstToolWindowPackage.cs* das- <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> Attribut in der- `FirstToolWindowPackage` Klasse, die den Typ firsttoolwindow an den-Konstruktor übergibt. Um eine Standardposition anzugeben, müssen Sie dem Konstruktor im folgenden Beispiel weitere Parameter hinzufügen.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Der erste benannte Parameter ist `Style` , und sein Wert ist. `Tabbed` Dies bedeutet, dass das Fenster eine Registerkarte in einem vorhandenen Fenster ist. Die Andock Position wird durch den- `Window` Parameter angegeben, in diesem Fall die GUID der **Projektmappen-Explorer**.

    > [!NOTE]
    > Weitere Informationen zu den Windows-Typen in der IDE finden Sie unter <xref:EnvDTE.vsWindowType> .

## <a name="test-the-tool-window"></a>Testen des Tool Fensters

1. Drücken Sie **F5** , um eine neue Instanz des experimentellen Visual Studio-Builds zu öffnen.

2. Zeigen Sie im Menü **Ansicht** auf **Weitere Fenster** , und klicken Sie dann auf **erstes Tool Fenster**.

    Das Media Player-Tool Fenster sollte an derselben Position wie **Projektmappen-Explorer** geöffnet werden. Wenn Sie immer noch an derselben Position wie zuvor angezeigt wird, setzen Sie das Fenster Layout zurück (Fenster **/Fenster Layout zurücksetzen**).

3. Klicken Sie im Tool Fenster auf die Schaltfläche (mit dem **Such** Symbol). Wählen Sie eine unterstützte Sound-oder Videodatei aus, z. b. *c:\Windows\Media\chimes.wav*, und drücken Sie dann **Öffnen**.

    Sie sollten den Glocke-Sound hören.

## <a name="see-also"></a>Siehe auch
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
