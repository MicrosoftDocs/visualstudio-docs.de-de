---
title: Ändern des Texts eines Menübefehls | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Text Bezeichnung eines Menübefehls mithilfe des IMenuCommandService-diensdienstansehens ändern, indem Sie dieses Codebeispiel überprüfen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d22669e67becb62d5e90f58c0cdd6b572e684bcf
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974392"
---
# <a name="change-the-text-of-a-menu-command"></a>Ändern des Texts eines Menübefehls
In den folgenden Schritten wird gezeigt, wie die Text Bezeichnung eines Menübefehls mithilfe des- <xref:System.ComponentModel.Design.IMenuCommandService> Dienstanbieter geändert wird.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Ändern einer Menübefehls Bezeichnung mit IMenuCommandService

1. Erstellen Sie ein VSIX-Projekt `MenuText` mit dem Namen mit einem Menübefehl namens **changemenutext**. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Fügen Sie in der *vsct* -Datei dem `TextChanges` Menübefehl das-Flag hinzu, wie im folgenden Beispiel gezeigt.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. Erstellen Sie in der Datei *ChangeMenuText.cs* einen Ereignishandler, der aufgerufen wird, bevor der Menübefehl angezeigt wird.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    Sie können den Status des Menübefehls in dieser Methode auch aktualisieren, indem Sie die <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> Eigenschaften, und <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> für das- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Objekt ändern.

4. Ersetzen Sie im changemenutext-Konstruktor den ursprünglichen Befehls Initialisierungs-und Platzierungs Code durch Code, der ein-Element <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (anstelle eines) erstellt, `MenuCommand` das den Menübefehl darstellt, den Ereignishandler hinzufügt und den Menübefehl <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> an den Menübefehls Dienst übergibt.

    Dies sollte wie folgt aussehen:

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.

6. **Im Menü Extras** sollte ein Befehl mit dem Namen **changemenutext aufrufen** angezeigt werden.

7. Klicken Sie auf den Befehl. Das Meldungs Feld wird angezeigt, dass **MenuItemCallBack** aufgerufen wurde. Wenn Sie das Meldungs Feld schließen, sollten Sie sehen, dass der Name des Befehls im Menü Extras nun **neuer Text** ist.
