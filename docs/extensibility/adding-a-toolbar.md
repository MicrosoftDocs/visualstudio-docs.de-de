---
title: Hinzufügen einer Symbolleiste | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Symbolleiste mit Schaltflächen hinzufügen, die an Befehle an die integrierte Entwicklungsumgebung (IDE) von Visual Studio gebunden sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 62d32a07ec046bc42d69818346450e5a94a668ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951328"
---
# <a name="add-a-toolbar"></a>Hinzufügen einer Symbolleiste
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie der Visual Studio-IDE eine Symbolleiste hinzufügen.

 Eine Symbolleiste ist ein horizontaler oder vertikaler Strich, der Schaltflächen enthält, die an Befehle gebunden sind. Abhängig von der Implementierung kann eine Symbolleiste in der IDE neu positioniert, an einer beliebigen Seite des Haupt-IDE-Fensters angedockt oder vor anderen Fenstern angezeigt werden.

 Darüber hinaus können Benutzer mithilfe des Dialog Felds **Anpassen** Befehle zu einer Symbolleiste hinzufügen oder Sie daraus entfernen. In der Regel sind Symbolleisten in VSPackages Benutzer anpassbar. Die IDE verarbeitet alle Anpassungen, und das VSPackage antwortet auf Befehle. Das VSPackage muss nicht wissen, wo sich ein Befehl physisch befindet.

 Weitere Informationen zu Menüs finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Erstellen einer Erweiterung mit einer Symbolleiste
 Erstellen Sie ein VSIX-Projekt mit dem Namen `IDEToolbar` . Fügen Sie eine Menübefehls Element-Vorlage mit dem Namen **toolbartestcommand** hinzu. Weitere Informationen hierzu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Erstellen einer Symbolleiste für die IDE

1. Suchen Sie in *toolbartestcommandpackage. vsct* nach dem Abschnitt Symbole. Fügen Sie im guidsymbol-Element mit dem Namen "guidtoolbartestcommandpackagecmdset" wie folgt Deklarationen für eine Symbolleiste und eine Symbolleisten Gruppe hinzu.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Erstellen Sie am oberen Rand des Befehls Abschnitts einen Menübereich. Fügen Sie dem Abschnitt Menüs ein Menü Element hinzu, um die Symbolleiste zu definieren.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Symbolleisten können nicht wie Untermenüs eingefügt werden. Daher ist es nicht erforderlich, eine übergeordnete Gruppe zuzuweisen. Außerdem müssen Sie keine Priorität festlegen, da der Benutzer Symbolleisten verschieben kann. In der Regel wird die anfängliche Platzierung einer Symbolleiste Programm gesteuert definiert, nachfolgende Änderungen durch den Benutzer werden jedoch beibehalten.

3. Definieren Sie im Abschnitt [Gruppen](../extensibility/groups-element.md) nach dem vorhandenen Gruppen Eintrag ein [Group](../extensibility/group-element.md) -Element, das die Befehle für die Symbolleiste enthält.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Legen Sie die Schaltfläche auf der Symbolleiste ab. Ersetzen Sie im Abschnitt Buttons den übergeordneten Block in der Schaltfläche auf der Symbolleiste. Der resultierende Schaltflächen Block sollte wie folgt aussehen:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Wenn eine Symbolleiste keine Befehle enthält, wird Sie standardmäßig nicht angezeigt.

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

6. Klicken Sie mit der rechten Maustaste auf die Visual Studio-Menüleiste, um die Liste der Symbolleisten zu erhalten. Wählen Sie **Test Symbolleiste** aus.

7. Nun sollte die Symbolleiste als Symbol auf der rechten Seite des Symbols in Dateien suchen angezeigt werden. Wenn Sie auf das Symbol klicken, sollte ein Meldungs Feld mit dem Text **toolbartestcommandpackage angezeigt werden. In idetoolbar. toolbartestcommand. MenuItemCallBack ()**.

## <a name="see-also"></a>Weitere Informationen
- [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
