---
title: Hinzufügen einer zuletzt verwendeten Liste zu einem Untermenü | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine dynamische Liste hinzufügen, die die zuletzt verwendeten Menübefehle zu einem Untermenü in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0de48e30ea20ab2f7df4e512312978e4faa3a46b
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597925"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Hinzufügen einer zuletzt verwendeten Liste zu einem Untermenü
Diese exemplarische Vorgehensweise baut auf den Demos in [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)auf und zeigt, wie eine dynamische Liste zu einem Untermenü hinzugefügt wird. Die dynamische Liste bildet die Grundlage für das Erstellen einer Liste mit den zuletzt verwendeten (MRU).

Eine dynamische Menü Liste beginnt mit einem Platzhalter in einem Menü. Jedes Mal, wenn das Menü angezeigt wird, fordert die integrierte Entwicklungsumgebung (IDE) von Visual Studio das VSPackage nach allen Befehlen an, die im Platzhalter angezeigt werden sollen. Eine dynamische Liste kann an beliebiger Stelle in einem Menü auftreten. Dynamische Listen werden jedoch in der Regel in Untermenüs oder in den untersten Menüs gespeichert und angezeigt. Wenn Sie diese Entwurfsmuster verwenden, aktivieren Sie die dynamische Liste der Befehle, um Sie zu erweitern und zu verkleinern, ohne dass sich dies auf die Position anderer Befehle im Menü auswirkt. In dieser exemplarischen Vorgehensweise wird die dynamische MRU-Liste am unteren Rand eines vorhandenen Untermenüs angezeigt, getrennt vom Rest des Untermenüs durch eine Zeile.

Technisch gesehen kann eine dynamische Liste auch auf eine Symbolleiste angewendet werden. Diese Verwendung wird jedoch davon abgeraten, da eine Symbolleiste unverändert bleiben sollte, es sei denn, der Benutzer führt bestimmte Schritte zum Ändern aus.

In dieser exemplarischen Vorgehensweise wird eine MRU-Liste mit vier Elementen erstellt, deren Reihenfolge jedes Mal geändert wird, wenn eine von Ihnen ausgewählt ist (das ausgewählte Element wird an den Anfang der Liste verschoben).

Weitere Informationen zu Menüs und *vsct* -Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Voraussetzungen
Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Erstellen einer Erweiterung

- Befolgen Sie die Verfahren unter [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md) , um das Untermenü zu erstellen, das in den folgenden Prozeduren geändert wird.

  Bei den Prozeduren in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Name des VSPackage lautet `TestCommand` . Dies ist der Name, der in [der Visual Studio-Menüleiste einem Menü hinzugefügt](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)wird.

## <a name="create-a-dynamic-item-list-command"></a>Befehl zum Erstellen einer dynamischen Elementliste

1. Öffnen Sie die Datei " *testcommandpackage. vsct*".

2. `Symbols`Fügen Sie im-Abschnitt im `GuidSymbol` Knoten guidtestcommandpackagecmdset das Symbol für die `MRUListGroup` Gruppe und den `cmdidMRUList` Befehl wie folgt hinzu.

    ```xml
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. `Groups`Fügen Sie im Abschnitt nach den vorhandenen Gruppen Einträgen die deklarierte Gruppe hinzu.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

4. `Buttons`Fügen Sie im-Abschnitt nach den vorhandenen Schaltflächen Einträgen einen Knoten hinzu, der den neu deklarierten Befehl darstellt.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"
        type="Button" priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />
        <CommandFlag>DynamicItemStart</CommandFlag>
        <Strings>
            <CommandName>cmdidMRUList</CommandName>
            <ButtonText>MRU Placeholder</ButtonText>
        </Strings>
    </Button>
    ```

    Mit dem- `DynamicItemStart` Flag kann der Befehl dynamisch generiert werden.

5. Erstellen Sie das Projekt, und starten Sie das Debuggen, um die Anzeige des neuen Befehls zu testen.

    Klicken Sie im Menü **Testmenü** auf das neue Untermenü **unter Menü**, um den neuen Befehl **MRU-Platzhalter** anzuzeigen. Nachdem eine dynamische MRU-Liste mit Befehlen in der nächsten Prozedur implementiert wurde, wird diese Befehls Bezeichnung jedes Mal, wenn das Untermenü geöffnet wird, durch diese Liste ersetzt.

## <a name="filling-the-mru-list"></a>Auffüllen der MRU-Liste

1. Fügen Sie in *TestCommandPackageGuids.cs* nach den vorhandenen Befehls-IDs in der Klassendefinition die folgenden Zeilen hinzu `TestCommandPackageGuids` .

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. Fügen Sie in *TestCommand.cs* die folgende using-Anweisung hinzu.

    ```csharp
    using System.Collections;
    ```

3. Fügen Sie den folgenden Code im TestCommand-Konstruktor nach dem letzten AddCommand-Befehl hinzu. `InitMRUMenu`Wird später definiert.

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Fügen Sie den folgenden Code in die Klasse TestCommand ein. Dieser Code initialisiert die Liste der Zeichen folgen, die die Elemente darstellen, die in der MRU-Liste angezeigt werden sollen.

    ```csharp
    private int numMRUItems = 4;
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;
    private ArrayList mruList;

    private void InitializeMRUList()
    {
        if (null == this.mruList)
        {
            this.mruList = new ArrayList();
            if (null != this.mruList)
            {
                for (int i = 0; i < this.numMRUItems; i++)
                {
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,
                        "Item {0}", i + 1));
                }
            }
        }
    }
    ```

5. Fügen Sie nach der- `InitializeMRUList` Methode die- `InitMRUMenu` Methode hinzu. Hierdurch werden die Menübefehle der MRU-Liste initialisiert.

    ```csharp
    private void InitMRUMenu(OleMenuCommandService mcs)
    {
        InitializeMRUList();
        for (int i = 0; i < this.numMRUItems; i++)
        {
            var cmdID = new CommandID(
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);
            var mc = new OleMenuCommand(
                new EventHandler(OnMRUExec), cmdID);
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);
            mcs.AddCommand(mc);
        }
    }
    ```

    Sie müssen ein Menübefehls Objekt für jedes mögliche Element in der MRU-Liste erstellen. Die IDE Ruft die- `OnMRUQueryStatus` Methode für jedes Element in der MRU-Liste auf, bis keine weiteren Elemente mehr vorhanden sind. In verwaltetem Code ist die einzige Möglichkeit für die IDE, dass keine weiteren Elemente vorhanden sind, zuerst alle möglichen Elemente zu erstellen. Wenn Sie möchten, können Sie zusätzliche Elemente als zuerst als nicht sichtbar markieren, indem Sie `mc.Visible = false;` nach dem Erstellen des Menübefehls verwenden. Diese Elemente können später mithilfe von in der-Methode sichtbar gemacht werden `mc.Visible = true;` `OnMRUQueryStatus` .

6. Fügen Sie nach der- `InitMRUMenu` Methode die folgende `OnMRUQueryStatus` Methode hinzu. Dies ist der Handler, der den Text für jedes MRU-Element festlegt.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Fügen Sie nach der- `OnMRUQueryStatus` Methode die folgende `OnMRUExec` Methode hinzu. Dies ist der Handler für die Auswahl eines MRU-Elements. Diese Methode verschiebt das ausgewählte Element an den Anfang der Liste und zeigt dann das ausgewählte Element in einem Meldungs Feld an.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
                for (int i = MRUItemIndex; i > 0; i--)
                {
                    this.mruList[i] = this.mruList[i - 1];
                }
                this.mruList[0] = selection;
                System.Windows.Forms.MessageBox.Show(
                    string.Format(CultureInfo.CurrentCulture,
                                  "Selected {0}", selection));
            }
        }
    }
    ```

## <a name="testing-the-mru-list"></a>Testen der MRU-Liste

1. Erstellen Sie das Projekt, und starten Sie das Debugging.

2. Klicken Sie im Menü **Testmenü** auf **TestCommand aufrufen**. Dadurch wird ein Meldungs Feld angezeigt, das angibt, dass der Befehl ausgewählt wurde.

    > [!NOTE]
    > Dieser Schritt ist erforderlich, um zu erzwingen, dass das VSPackage geladen und die MRU-Liste ordnungsgemäß angezeigt wird. Wenn Sie diesen Schritt überspringen, wird die MRU-Liste nicht angezeigt.

3. Klicken Sie im Menü **Test** auf **Untermenü**. Eine Liste mit vier Elementen wird am Ende des Untermenüs unter einem Trennzeichen angezeigt. Wenn Sie auf **Element 3** klicken, wird ein Meldungs Feld angezeigt, und der Text, das **ausgewählte Element 3**, wird angezeigt. (Wenn die Liste der vier Elemente nicht angezeigt wird, stellen Sie sicher, dass Sie die Anweisungen im vorherigen Schritt befolgt haben.)

4. Öffnen Sie das Untermenü erneut. Beachten Sie, dass **Element 3** nun am Anfang der Liste steht und die anderen Elemente eine Position nach unten verschoben wurden. Klicken Sie erneut auf **Element 3** , und beachten Sie, dass im Meldungs Feld weiterhin das **ausgewählte Element 3** angezeigt wird. Dadurch wird angegeben, dass der Text ordnungsgemäß an die neue Position mit der Befehls Bezeichnung verschoben wurde.

## <a name="see-also"></a>Siehe auch
- [Dynamisches Hinzufügen von Menü Elementen](../extensibility/dynamically-adding-menu-items.md)
