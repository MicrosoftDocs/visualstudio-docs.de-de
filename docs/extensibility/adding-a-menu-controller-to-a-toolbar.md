---
title: Hinzufügen eines Menü Controllers zu einer Symbolleiste | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einen Menü Controller erstellen und zu einer Symbolleisten-Symbolleiste in Visual Studio hinzufügen und anschließend die Menü Controller Befehle implementieren und testen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82da331d93a2208b76bb953f3a6a489913c907ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951523"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Hinzufügen eines Menü Controllers zu einer Symbolleiste
Diese exemplarische Vorgehensweise basiert auf der exemplarischen Vorgehensweise zum [Hinzufügen einer Symbolleiste zu einem Tool Fenster](../extensibility/adding-a-toolbar-to-a-tool-window.md) und zeigt, wie Sie der Symbolleiste des Tool Fensters einen Menü Controller hinzufügen. Die hier gezeigten Schritte können auch auf die Symbolleiste angewendet werden, die auf der exemplarischen Vorgehensweise zum [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md) erstellt wird.

Ein Menü Controller ist ein Split-Steuerelement. Auf der linken Seite des Menü Controllers wird der zuletzt verwendete Befehl angezeigt, und Sie können ihn ausführen, indem Sie darauf klicken. Die Rechte Seite des Menü Controllers ist ein Pfeil, der, wenn Sie darauf klicken, eine Liste zusätzlicher Befehle öffnet. Wenn Sie auf einen Befehl in der Liste klicken, wird der Befehl ausgeführt, und der Befehl wird auf der linken Seite des Menü Controllers ersetzt. Auf diese Weise verhält sich der Menü Controller wie eine Befehls Schaltfläche, die immer den zuletzt verwendeten Befehl aus einer Liste anzeigt.

Menü Controller können in Menüs angezeigt werden, werden jedoch am häufigsten auf Symbolleisten verwendet.

## <a name="prerequisites"></a>Voraussetzungen
Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Erstellen eines Menü Controllers

1. Befolgen Sie die unter [Hinzufügen einer Symbolleiste zu einem Tool Fenster](../extensibility/adding-a-toolbar-to-a-tool-window.md) beschriebenen Verfahren zum Erstellen eines Tool Fensters, das über eine Symbolleiste verfügt.

2. Wechseln Sie in *twtestcommandpackage. vsct* zum Abschnitt "Symbole". Deklarieren Sie im guidsymbol-Element mit dem Namen " **guidtwtestcommandpackagecmdset**" den Menü Controller, die Menü Controller Gruppe und drei Menü Elemente.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. Legen Sie im Abschnitt Menüs nach dem letzten Menüeintrag den Menü Controller als Menü fest.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    Die `TextChanges` -und- `TextIsAnchorCommand` Flags müssen eingeschlossen werden, damit der Menü Controller den zuletzt ausgewählten Befehl widerspiegeln kann.

4. Fügen Sie im Abschnitt Gruppen nach dem letzten Gruppen Eintrag die Menü Controller Gruppe hinzu.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Wenn Sie den Menü Controller als übergeordnetes Element festlegen, werden alle in dieser Gruppe platzierten Befehle im Menü Controller angezeigt. Das- `priority` Attribut wird ausgelassen, wodurch der Standardwert 0 (null) festgelegt wird, da es sich hierbei um die einzige Gruppe auf dem Menü Controller handelt.

5. Fügen Sie im Abschnitt Buttons nach dem letzten Schaltflächen Eintrag ein Schaltflächen Element für jedes Ihrer Menü Elemente hinzu.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. An diesem Punkt können Sie sich den Menü Controller ansehen. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

   1. Öffnen Sie im Menü **Ansicht/andere Fenster** den Befehl **Test Tool Window**.

   2. Der Menü Controller wird im Tool Fenster auf der Symbolleiste angezeigt.

   3. Klicken Sie auf den Pfeil auf der rechten Seite des Menü Controllers, um die drei möglichen Befehle anzuzeigen.

      Beachten Sie, dass beim Klicken auf einen Befehl der Titel des Menü Controllers geändert wird, um diesen Befehl anzuzeigen. Im nächsten Abschnitt fügen wir den Code hinzu, um diese Befehle zu aktivieren.

## <a name="implement-the-menu-controller-commands"></a>Implementieren der Menü Controller Befehle

1. Fügen Sie in *TWTestCommandPackageGuids.cs* nach den vorhandenen Befehls-IDs Befehls-IDs für Ihre drei Menü Elemente hinzu.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. Fügen Sie in *TWTestCommand.cs* den folgenden Code am Anfang der Klasse hinzu `TWTestCommand` .

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. Fügen Sie im twtestcommand-Konstruktor nach dem letzten Aufrufe der- `AddCommand` Methode Code hinzu, um die Ereignisse für jeden Befehl durch die gleichen Handler weiterzuleiten.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Fügen Sie der **twtestcommand** -Klasse einen Ereignishandler hinzu, um den ausgewählten Befehl als aktiviert zu markieren.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Fügen Sie einen Ereignishandler hinzu, der eine MessageBox anzeigt, wenn der Benutzer einen Befehl auf dem Menü Controller auswählt:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Testen des Menü Controllers

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

2. Öffnen Sie im Menü **Ansicht/andere Fenster** das **Test Tool Fenster** .

    Der Menü Controller wird in der Symbolleiste im Tool Fenster angezeigt und zeigt **MC Element 1** an.

3. Klicken Sie auf die Schaltfläche des Menü Controllers links neben dem Pfeil.

    Es sollten drei Elemente angezeigt werden, von denen das erste ausgewählt ist, und ein Hervorhebungs Feld um das Symbol angezeigt wird. Klicken Sie auf **MC Element 3**.

    Es wird ein Dialogfeld mit der Meldung angezeigt, dass **Sie Menü Controller Element 3 ausgewählt** haben. Beachten Sie, dass die Meldung dem Text auf der Schaltfläche des Menü Controllers entspricht. Die Schaltfläche "Menü Controller" zeigt nun **MC-Element 3** an.

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen einer Symbolleiste zu einem Tool Fenster](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)
