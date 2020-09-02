---
title: Erweitern von Menüs und Befehlen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83d9dc45863f1ed1b5e11c17b9e922b62b0186dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204524"
---
# <a name="extending-menus-and-commands"></a>Erweitern von Menüs und Befehlen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Befehlen können Sie Visual Studio Aktionen und Prozesse hinzufügen. In den meisten Fällen werden Befehle in Menüs oder Symbolleisten angezeigt. Die VSPackage-Projektvorlage zeigt, wie ein sehr grundlegender Befehl implementiert wird. Eine etwas längere, aber immer noch grundlegende Implementierung finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Weitere Informationen zu Befehlen, Menüs und Symbolleisten in Visual Studio finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Befehle, Menüs und Symbolleisten sind in der vsct-Datei definiert, die Teil von VSPackage-Projekten ist. Informationen über die Visual Studio-IDE und die vsct-Datei finden Sie unter Gewusst [wie: Hinzufügen von Elementen der Benutzeroberfläche durch VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 In den folgenden Themen wird erläutert, wie verschiedene Arten von Befehlen, Menüs und Symbolleisten hinzugefügt werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Hinzufügen eines Menüs zur Visual Studio-Menüleiste](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Erläutert, wie ein Menü in der oberen Visual Studio-Menüleiste hinzugefügt wird.  
  
 [Binden von Tastenkombinationen an Menüelemente](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Erläutert das Hinzufügen einer Tastenkombination (z. b. STRG + 3) zu einem Menü Element.  
  
 [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)  
 Erläutert, wie dem oberen Menü ein Untermenü hinzugefügt wird.  
  
 [Hinzufügen einer Liste „Zuletzt verwendet“ zu einem Untermenü](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Erläutert das Hinzufügen einer zuletzt verwendeten Liste.  
  
 [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../extensibility/creating-reusable-groups-of-buttons.md)  
 Beschreibt das Gruppieren von Befehls Elementen, sodass Sie in mehreren Menüs enthalten sein können.  
  
 [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md)  
 Beschreibt das Hinzufügen eines Symbols zu einem Befehl sowohl auf einer Symbolleiste als auch in einem Menü.  
  
 [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md)  
 Beschreibt die Verwendung des- `TextChanges` Flags, um zu ermöglichen, dass ein Menü Element dynamisch geändert wird.  
  
 [Ändern der Darstellung eines Befehls](../extensibility/changing-the-appearance-of-a-command.md)  
 Beschreibt das dynamische aktivieren oder Deaktivieren eines Befehls.  
  
 [Aktualisieren der Benutzeroberfläche](../extensibility/updating-the-user-interface.md)  
 Beschreibt, wie eine Aktualisierung der Benutzeroberfläche erzwungen wird, um aktuelle Änderungen widerzuspiegeln.  
  
 [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md)  
 Erläutert, wie Menübefehle lokalisiert werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte
