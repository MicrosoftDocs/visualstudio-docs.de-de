---
title: Erweitern von Menüs und Befehlen | Microsoft-Dokumentation
description: Erfahren Sie mehr über Befehle, die Visual Studio Aktionen und Prozesse hinzufügen. Die VSPackage-Projektvorlage zeigt, wie ein sehr grundlegender Befehl implementiert wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d99b1b0f5ba0f80af3aadcff0404357b57fbe265
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994601"
---
# <a name="extend-menus-and-commands"></a>Erweitern von Menüs und Befehlen
Mit Befehlen können Sie Visual Studio Aktionen und Prozesse hinzufügen. In den meisten Fällen werden Befehle in Menüs oder Symbolleisten angezeigt. Die VSPackage-Projektvorlage zeigt, wie ein sehr grundlegender Befehl implementiert wird. Eine etwas längere, aber immer noch grundlegende Implementierung finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

 Weitere Informationen zu Befehlen, Menüs und Symbolleisten in Visual Studio finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).

 Befehle, Menüs und Symbolleisten sind in der *vsct* -Datei definiert, die Teil von VSPackage-Projekten ist. Informationen über die Visual Studio-IDE und die *vsct* -Datei finden Sie unter Gewusst [wie: Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 In den folgenden Themen wird erläutert, wie verschiedene Arten von Befehlen, Menüs und Symbolleisten hinzugefügt werden.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Erläutert, wie ein Menü in der oberen Visual Studio-Menüleiste hinzugefügt wird.

- [Binden von Tastenkombinationen an Menü Elemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Erläutert das Hinzufügen einer Tastenkombination (z. b. STRG + 3) zu einem Menü Element.

- [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md) Erläutert, wie dem oberen Menü ein Untermenü hinzugefügt wird.

- [Hinzufügen einer zuletzt verwendeten Liste zu einem Untermenü](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Erläutert das Hinzufügen einer zuletzt verwendeten Liste.

- [Erstellen wiederverwendbarer Gruppen von Schalt](../extensibility/creating-reusable-groups-of-buttons.md) Flächen Beschreibt das Gruppieren von Befehls Elementen, sodass Sie in mehreren Menüs enthalten sein können.

- [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md) Beschreibt das Hinzufügen eines Symbols zu einem Befehl sowohl auf einer Symbolleiste als auch in einem Menü.

- [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md) Beschreibt die Verwendung des- `TextChanges` Flags, um zu ermöglichen, dass ein Menü Element dynamisch geändert wird.

- [Ändern des Erscheinungs](../extensibility/changing-the-appearance-of-a-command.md) Bilds eines Befehls Beschreibt das dynamische aktivieren oder Deaktivieren eines Befehls.

- [Aktualisieren der Benutzeroberfläche](../extensibility/updating-the-user-interface.md) Beschreibt, wie eine Aktualisierung der Benutzeroberfläche erzwungen wird, um aktuelle Änderungen widerzuspiegeln.

- [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md) Erläutert, wie Menübefehle lokalisiert werden.
