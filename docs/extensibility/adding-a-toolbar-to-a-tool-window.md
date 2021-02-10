---
title: Hinzufügen einer Symbolleiste zu einem Tool Fenster | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Symbolleiste mit Schaltflächen, die an Befehle gebunden sind, an ein Tool Fenster in der integrierten Entwicklungsumgebung (IDE) von Visual Studio hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c0152de94eb74fff902ced4d61c749f7cca3a277
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951341"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Hinzufügen einer Symbolleiste zu einem Tool Fenster
In dieser exemplarischen Vorgehensweise wird gezeigt, wie einem Tool Fenster eine Symbolleiste hinzugefügt wird.

 Eine Symbolleiste ist ein horizontaler oder vertikaler Strich, der auf Befehle gebundene Schaltflächen enthält. Die Länge einer Symbolleiste in einem Tool Fenster entspricht immer der Breite oder Höhe des Tool Fensters, je nachdem, wo die Symbolleiste angedockt ist.

 Im Gegensatz zu Symbolleisten in der IDE muss eine Symbolleiste in einem Tool Fenster angedockt werden und kann nicht verschoben oder angepasst werden. Wenn das VSPackage in umanaged Code geschrieben wird, kann die Symbolleiste an einem beliebigen Rand angedockt werden.

 Weitere Informationen zum Hinzufügen einer Symbolleiste finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Erstellen einer Symbolleiste für ein Tool Fenster

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `TWToolbar` , das sowohl einen Menübefehl namens **twtestcommand** als auch ein Tool Fenster mit dem Namen **testtoolwindow** enthält. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md) und [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md). Sie müssen die Befehls Element Vorlage hinzufügen, bevor Sie die Tool Fenster Vorlage hinzufügen.

2. Suchen Sie in der Datei " *twtestcommandpackage. vsct*" nach dem Abschnitt "Symbole". Deklarieren Sie im Knoten "guidsymbol" mit dem Namen "guidtwtestcommandpackagecmdset" wie folgt eine Symbolleiste und eine Symbolleisten Gruppe.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. Erstellen Sie am oberen Rand des `Commands` Abschnitts einen `Menus` Abschnitt. Fügen Sie ein- `Menu` Element zum Definieren der Symbolleiste hinzu.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Symbolleisten können nicht wie Untermenüs eingefügt werden. Daher müssen Sie kein übergeordnetes Element zuweisen. Außerdem müssen Sie keine Priorität festlegen, da der Benutzer Symbolleisten verschieben kann. In der Regel wird die anfängliche Platzierung einer Symbolleiste Programm gesteuert definiert, nachfolgende Änderungen durch den Benutzer werden jedoch beibehalten.

4. Definieren Sie im Abschnitt Gruppen eine Gruppe, in der die Befehle für die Symbolleiste enthalten sein sollen.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Ändern Sie im Schaltflächen Abschnitt das übergeordnete Element des vorhandenen Button-Elements in die Symbolleisten Gruppe, sodass die Symbolleiste angezeigt wird.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Wenn eine Symbolleiste keine Befehle enthält, wird Sie standardmäßig nicht angezeigt.

     Da die neue Symbolleiste dem Tool Fenster nicht automatisch hinzugefügt wird, muss die Symbolleiste explizit hinzugefügt werden. Dies wird im nächsten Abschnitt erläutert.

## <a name="add-the-toolbar-to-the-tool-window"></a>Hinzufügen der Symbolleiste zum Tool Fenster

1. Fügen Sie in *TWTestCommandPackageGuids.cs* die folgenden Zeilen hinzu.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. Fügen Sie in *TestToolWindow.cs* die folgende using-Anweisung hinzu.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. Fügen Sie im testtoolwindow-Konstruktor die folgende Zeile hinzu.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Testen der Symbolleiste im Tool Fenster

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.

2. Klicken Sie im Menü Ansicht > **andere Fenster** auf Tool **Fenster testen** , um das Tool Fenster anzuzeigen.

     Oben links im Tool Fenster sollte eine Symbolleiste angezeigt werden (Sie sieht wie das Standard Symbol aus), direkt unterhalb des Titels.

3. Klicken Sie auf der Symbolleiste auf das Symbol, um die Nachricht **twtestcommandpackage in twtoolbar. twtestcommand. MenuItemCallBack ()** anzuzeigen.

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md)
