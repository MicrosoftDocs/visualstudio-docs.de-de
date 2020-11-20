---
title: Erstellen einer Erweiterung mit einem Menübefehl | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Erweiterung mit einem Menübefehl erstellen, der Notepad gestartet. Erstellen Sie einen Menübefehl, und ändern Sie dann den Menübefehls Handler.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00afdc31e72e4b0336db19939955a0b2360a00a1
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974267"
---
# <a name="create-an-extension-with-a-menu-command"></a>Erstellen einer Erweiterung mit einem Menübefehl

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine Erweiterung mit einem Menübefehl erstellen, der Notepad gestartet.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Erstellen eines Menübefehls

1. Erstellen Sie ein VSIX-Projekt mit dem Namen **firstmenucommand**. Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** ", indem Sie nach "VSIX" suchen.

::: moniker range="vs-2017"

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **firstcommand** hinzu. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Add**  >  **Neues Element** hinzufügen aus. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#**  >  -**Erweiterbarkeit** , und wählen Sie **benutzerdefinierter Befehl** aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in *FirstCommand.cs*.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierte Befehls Element Vorlage mit dem Namen **firstcommand** hinzu. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Add**  >  **Neues Element** hinzufügen aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#**  >  -**Erweiterbarkeit** , und wählen Sie dann **Befehl** aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in *FirstCommand.cs*.

::: moniker-end

3. Erstellen Sie das Projekt, und starten Sie das Debugging.

    Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. Öffnen Sie **in der experimentellen Instanz das**  >  Fenster Extras **Erweiterungen und Updates** . Hier sollte die **firstmenucommand** -Erweiterung angezeigt werden. (Wenn Sie **Erweiterungen und Updates** in ihrer funktionierenden Instanz von Visual Studio öffnen, wird **firstmenucommand** nicht angezeigt.)

::: moniker-end

::: moniker range=">=vs-2019"

4. Öffnen Sie in der experimentellen Instanz das Fenster **Erweiterungen**  >  **Verwalten Erweiterungen** . Hier sollte die **firstmenucommand** -Erweiterung angezeigt werden. (Wenn Sie **Erweiterungen verwalten** in ihrer funktionierenden Instanz von Visual Studio öffnen, wird **firstmenucommand** nicht angezeigt.)

::: moniker-end

Wechseln Sie nun zum **Menü Extras in der experimentellen** Instanz. Der Befehl " **firstcommand aufrufen** " sollte angezeigt werden. An diesem Punkt zeigt der Befehl ein Meldungs Feld an, das **firstcommand in firstmenucommand. firstcommand. MenuItemCallBack ()** anzeigt. Im nächsten Abschnitt erfahren Sie, wie Sie Notepad tatsächlich mit diesem Befehl starten.

## <a name="change-the-menu-command-handler"></a>Ändern des Menübefehls Handlers

Nun aktualisieren wir den Befehls Handler, um Notepad zu starten.

1. Das Debuggen wird beendet, und Sie gelangen zurück zu ihrer funktionierenden Instanz von Visual Studio. Öffnen Sie die Datei *FirstCommand.cs* , und fügen Sie die folgende using-Anweisung hinzu:

    ```csharp
    using System.Diagnostics;
    ```

2. Suchen Sie den privaten firstcommand-Konstruktor. An dieser Stelle wird der Befehl mit dem Befehls Dienst verknüpft, und der Befehls Handler wird angegeben. Ändern Sie den Namen des Befehls Handlers in startnotepad wie folgt:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Entfernen `Execute` Sie die-Methode, und fügen Sie eine- `StartNotepad` Methode hinzu, die nur den Notepad startet:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();

        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Probieren Sie es jetzt aus. Wenn **Sie mit** dem Debuggen des Projekts beginnen und auf Extras  >  **aufrufen firstcommand** klicken, sollte eine Instanz von Notepad angezeigt werden.

    Sie können eine Instanz der- <xref:System.Diagnostics.Process> Klasse verwenden, um eine beliebige ausführbare Datei auszuführen, nicht nur Notepad. Probieren Sie es `calc.exe` beispielsweise mit aus.

## <a name="clean-up-the-experimental-environment"></a>Bereinigen der experimentellen Umgebung

Wenn Sie mehrere Erweiterungen entwickeln oder nur Ergebnisse mit unterschiedlichen Versionen Ihres Erweiterungs Codes untersuchen, funktioniert Ihre experimentelle Umgebung möglicherweise nicht mehr so. In diesem Fall sollten Sie das Reset-Skript ausführen. Dies wird als **Zurücksetzen der experimentellen Instanz von Visual Studio** bezeichnet und als Teil des Visual Studio SDK ausgeliefert. Mit diesem Skript werden alle Verweise auf die Erweiterungen aus der experimentellen Umgebung entfernt, sodass Sie von Grund auf neu beginnen können.

Dieses Skript kann auf zwei Arten erreicht werden:

1. Suchen Sie auf dem Desktop **die experimentelle Instanz von Visual Studio zurücksetzen**.

2. Führen Sie die folgenden Befehle über die Befehlszeile aus:

    ```cmd
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Bereitstellen der Erweiterung

Nachdem Sie nun die Tool Erweiterung auf die gewünschte Weise ausgeführt haben, ist es an der Zeit, Sie mit Ihren Freunden und Kollegen zu teilen. Das ist ganz einfach, solange Visual Studio 2015 installiert ist. Sie müssen lediglich die von Ihnen erstellten *. vsix* -Datei an Sie senden. (Stellen Sie sicher, dass Sie im Releasemodus erstellt werden.)

Die *VSIX* -Datei für diese Erweiterung finden Sie im Verzeichnis " *firstmenucommand* bin". Insbesondere, wenn Sie die Releasekonfiguration erstellt haben, befindet Sie sich in:

*\<code directory>\Firstmenucommand\firstmenucommand\bin\release\firstmenucommand.vsix*

Um die Erweiterung zu installieren, muss Ihr Freund alle geöffneten Instanzen von Visual Studio schließen und dann auf die *VSIX* -Datei doppelklicken, um das **VSIX-Installations** Programm aufzurufen. Die Dateien werden in das Verzeichnis " *%LocalAppData%\microsoft\visualstudio \<version> \extensions* " kopiert.

Wenn Ihr Freund Visual Studio erneut aufbringt, finden Sie die Erweiterung "firstmenucommand" **unter Extras**  >  **Erweiterungen und Updates**. Sie können auch zu **Erweiterungen und Updates** wechseln, um die Erweiterung zu deinstallieren oder zu deaktivieren.

## <a name="next-steps"></a>Nächste Schritte

In dieser exemplarischen Vorgehensweise haben Sie nur einen kleinen Teil der Möglichkeiten einer Visual Studio-Erweiterung gezeigt. Im folgenden finden Sie eine kurze Liste anderer (relativ einfacher) Dinge, die Sie mit Visual Studio-Erweiterungen machen können:

1. Sie können mit einem einfachen Menübefehl viele weitere Aktionen ausführen:

   1. Eigenes Symbol hinzufügen: [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)

   2. Ändern Sie den Text des Menübefehls: [Ändern Sie den Text eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md) .

   3. Hinzufügen einer Menü Verknüpfung zu einem Befehl: [Binden von Tastenkombinationen an Menü Elemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Hinzufügen verschiedener Arten von Befehlen, Menüs und Symbolleisten: [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)

3. Hinzufügen von Tool Fenstern und Erweitern der integrierten Visual Studio-Tool Fenster: [erweitern und Anpassen von Tool Fenstern](../extensibility/extending-and-customizing-tool-windows.md)

4. Hinzufügen von IntelliSense, Code Vorschlägen und anderen Features zu vorhandenen Code-Editoren: [Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)

5. Fügen Sie der Erweiterung Optionen und Eigenschaften Seiten und Benutzereinstellungen hinzu: [Erweitern Sie Eigenschaften und das Eigenschaften Fenster](../extensibility/extending-properties-and-the-property-window.md) , und erweitern Sie [Benutzereinstellungen und-Optionen](../extensibility/extending-user-settings-and-options.md) .

   Andere Arten von Erweiterungen erfordern etwas mehr Arbeit, z. b. das Erstellen eines neuen Projekt Typs ([Erweitern von Projekten](../extensibility/extending-projects.md)), das Erstellen eines neuen Editor Typs ([Erstellen benutzerdefinierter Editoren und Designer](../extensibility/creating-custom-editors-and-designers.md)) oder das Implementieren der Erweiterung in einer isolierten Shell: [isolierte Visual Studio-Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
