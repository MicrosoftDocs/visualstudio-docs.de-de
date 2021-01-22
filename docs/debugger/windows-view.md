---
title: Fensteransicht | Microsoft-Dokumentation
description: In der Fensteransicht wird eine Struktur aller Fenster und Steuerelemente angezeigt. Verwenden Sie sie als Ausgangspunkt, um Informationen zu relevanten Fenstern zu erhalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.windowsview
helpviewer_keywords:
- Windows view
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 717c0f18d5443f712151a2f8318c56a8e738f6d7
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205371"
---
# <a name="windows-view"></a>Fensteransicht
Wenn Sie Spy + + zum ersten Mal öffnen, wird in der Fensteransicht eine Struktur aller Fenster und Steuerelemente im System angezeigt. Das Fensterhandle und der Klassenname werden angezeigt. Das aktuelle Desktopfenster befindet sich ganz oben in der Struktur. Alle anderen Fenster sind untergeordnete Fenster des Desktops und werden entsprechend der Standardfensterhierarchie aufgeführt. Gleichgeordnete Fenster werden in erweiterbaren Listen unter ihren übergeordneten Fenstern eingerückt angezeigt.

 Die folgende Abbildung zeigt eine typische Spy++-Fensteransicht, bei der der oberste Knoten erweitert ist.

 ![Spy&#43;&#43;-Windows-Ansicht](../debugger/media/spy--_windowsview.png "Spy++_WindowsView") Spy++-Windows-Ansicht

 Das aktuelle Desktopfenster befindet sich ganz oben in der Struktur. Alle anderen Fenster sind untergeordnete Fenster des Desktops und werden entsprechend der Standardfensterhierarchie aufgelistet, wobei gleichgeordnete Fenster in der Z-Reihenfolge sortiert sind. Sie können jeden übergeordneten Knoten der Struktur erweitern oder reduzieren, indem Sie neben dem Knoten auf das Symbol „+“ oder „-“ klicken.

 Wenn die Fensteransicht den Fokus besitzt, können Sie das Suchtool im [Dialogfeld „Fenstersuche“](../debugger/window-search-dialog-box.md) verwenden, um Informationen aus jedem in Ihrem System geöffneten Fenster anzuzeigen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [How to: Verwenden des Suchtools](../debugger/how-to-use-the-finder-tool.md): Zeigt, wie dieses Tool Fenster auf Eigenschaften oder Meldungen überprüft.

 [How to: Suchen nach einem Fenster in der Fensteransicht](../debugger/how-to-search-for-a-window-in-windows-view.md): Erläutert, wie Sie in der Fensteransicht ein bestimmtes Fenster suchen.

 [How to: Anzeigefenstereigenschaften](../debugger/how-to-display-window-properties.md): m-Prozeduren zum Öffnen des Dialogfelds „Fenstereigenschaften“.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Spy++-Ansichten](../debugger/spy-increment-views.md) Erläutert die Spy++-Strukturansichten von Fenstern, Meldungen, Prozessen und Threads.

 [Verwenden von Spy++](../debugger/using-spy-increment.md): Bietet eine Einführung in das Tool Spy++ und erläutert, wie es verwendet werden kann.

 [Dialogfeld „Fenster Suchen“](../debugger/find-window-dialog-box.md): Wird verwendet, um die Eigenschaften oder Meldungen eines bestimmten Fensters anzuzeigen.

 [Fenstersuche (Dialogfeld)](../debugger/window-search-dialog-box.md): Dient zum Suchen des Knotens für ein bestimmtes Fenster in der Fensteransicht.

 [Fenstereigenschaften (Dialogfeld )](../debugger/window-properties-dialog-box.md): Wird verwendet, um die Eigenschaften eines in der Fensteransicht ausgewählten Fensters anzuzeigen.

 [Spy++-Referenz](../debugger/spy-increment-reference.md): Enthält Abschnitte mit Beschreibungen der einzelnen Menüs und Dialogfelder von Spy++.