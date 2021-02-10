---
title: Spy++-Symbolleiste | Microsoft-Dokumentation
description: In diesem Artikel finden Sie Informationen zu den Benutzeroberflächenelementen in der Spy++-Symbolleiste, die unter der Menüleiste angezeigt wird. Klicken Sie zum Anzeigen oder Ausblenden der Symbolleiste im Menü Ansicht auf Symbolleiste.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: af6db0f367c73804197ef35d0b3734d68f15a332
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903524"
---
# <a name="spy-toolbar"></a>Spy++-Symbolleiste
Die Symbolleiste wird in Spy++ unter der Menüleiste angezeigt. Klicken Sie zum Anzeigen oder Ausblenden der Symbolleiste im Menü **Ansicht** auf **Symbolleiste**.

 Auf der Symbolleiste sind die folgenden Steuerelemente verfügbar.

## <a name="uielement-list"></a>UIElement-Liste

|Schaltfläche|Effekt|
|------------|------------|
|![Spy&#43;&#43;-Schaltfläche „Fenster“](../debugger/media/icon_spy--_windows.gif "Icon_Spy++_Windows")|Zeigt eine Strukturansicht der Fenster und Steuerelemente im System an. Weitere Informationen finden Sie unter [Fensteransicht](../debugger/windows-view.md).|
|![Spy&#43;&#43-Schaltfläche „Prozesse“](../debugger/media/icon_spy--_processes.gif "Icon_Spy++_Processes")|Zeigt eine Strukturansicht der Prozesse im System an. Weitere Informationen finden Sie unter [Prozessansicht](../debugger/processes-view.md).|
|![Spy&#43;&#43;-Schaltfläche „Threads“](../debugger/media/icon_spy--_threads.gif "Icon_Spy++_Threads")|Zeigt eine Strukturansicht der Threads im System an. Weitere Informationen finden Sie unter [Threadansicht](../debugger/threads-view.md).|
|![Spy&#43;&#43;-Schaltfläche „Meldungen“](../debugger/media/icon_spy--_messages.gif "Icon_Spy++_Messages")|Erstellt ein Fenster zum Anzeigen von Fenstermeldungen und öffnet das Dialogfeld **Meldungsoptionen**, damit Sie das Fenster, dessen Meldungen angezeigt werden sollen, und andere Optionen auswählen können. Weitere Informationen finden Sie unter [Meldungsansicht](../debugger/messages-view.md).|
|![Spy&#43;&#43;-Schaltfläche „Protokollierung starten“](../debugger/media/icon_spy--_startlog.gif "Icon_Spy++_StartLog")|Startet die Meldungsprotokollierung und zeigt den Meldungsdatenstrom an. Dieses Steuerelement ist nur verfügbar, wenn ein **Meldungsfenster** das aktive Fenster ist. Weitere Informationen finden Sie unter [Vorgehensweise: Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43;&#43;-Schaltfläche „Protokollierung beenden“](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy++_StopLog")|Beendet die Meldungsprotokollierung und die Anzeige des Meldungsdatenstroms. Dieses Steuerelement ist nur verfügbar, wenn ein **Meldungsfenster** das aktive Fenster ist. Weitere Informationen finden Sie unter [Vorgehensweise: Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43;&#43;-Schaltfläche „Protokolloptionen“](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy++_LogOptions")|Zeigt das Dialogfeld [Meldungsoptionen](../debugger/message-options-dialog-box.md) an. Mithilfe dieses Dialogfelds können Sie Fenster und Nachrichtentypen für die Anzeige auswählen. Dieses Steuerelement ist nur verfügbar, wenn ein **Meldungsfenster** das aktive Fenster ist.|
|![Spy&#43;&#43;-Schaltfläche „Protokoll löschen“](../debugger/media/spy--_clearlog.gif "Spy++_ClearLog")|Löscht den Inhalt des aktiven **Meldungsfensters**. Dieses Steuerelement ist nur verfügbar, wenn ein **Meldungsfenster** das aktive Fenster ist.|
|![Spy&#43;&#43;-Schaltfläche „Fenster suchen“](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy++_FindWindow")|Öffnet das Dialogfeld [Fenster suchen](../debugger/find-window-dialog-box.md), in dem Sie Fenstersuchkriterien festlegen und Eigenschaften oder Meldungen anzeigen können. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Suchtools](../debugger/how-to-use-the-finder-tool.md).|
|![Spy&#43;&#43;-Schaltfläche „Erstes Fenster suchen“](../debugger/media/icon_spy--_window.gif "Icon_Spy++_Window")|Durchsucht die aktuelle Ansicht nach einem entsprechenden Fenster, Prozess, Thread oder einer entsprechenden Meldung.|
|![Spy&#43;&#43;-Schaltfläche „Nächstes Fenster suchen“](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy++_NextWindow")|Durchsucht die aktuelle Ansicht nach dem nächsten entsprechenden Fenster, Prozess, Thread oder der nächsten entsprechenden Meldung. Dieses Steuerelement (und der zugehörige Menübefehl) ist nur verfügbar, wenn ein gültiges Suchergebnis vorliegt, das nicht eindeutig ist. Beispiel: Wenn Sie ein Fensterhandle als Suchkriterium in der Fensterstruktur verwenden, werden eindeutige Ergebnisse generiert, da in der Fensterstruktur nur ein Fenster mit diesem Handle vorhanden ist. In diesem Fall ist **Weitersuchen** nicht verfügbar.|
|![Spy&#43;&#43;-Schaltfläche „Vorheriges Fenster suchen“](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy++_PrevWindow")|Durchsucht die aktuelle Ansicht nach dem vorherigen entsprechenden Fenster, Prozess, Thread oder einer entsprechenden Meldung. Dieses Steuerelement (und der zugehörige Menübefehl) ist nur verfügbar, wenn ein gültiges Suchergebnis vorliegt, das nicht eindeutig ist. Beispiel: Wenn Sie ein Fensterhandle als Suchkriterium in der Fensterstruktur verwenden, werden eindeutige Ergebnisse generiert, da in der Fensterstruktur nur ein Fenster mit diesem Handle vorhanden ist. In diesem Fall ist **Vorheriges Element suchen** nicht verfügbar.|
|![Spy&#43;&#43;-Schaltfläche „Eigenschaften-Explorer“](../debugger/media/icon_spy--_propexp.gif "Icon_Spy++_PropExp")|Zeigt die Eigenschaften des Fensters an, das in der Fensteransicht ausgewählt ist.|
|![Spy&#43;&#43;-Schaltfläche „Aktualisieren“](../debugger/media/icon_spy--_refresh.gif "Icon_Spy++_Refresh")|Aktualisiert die Systemansichten.|

## <a name="see-also"></a>Siehe auch
- [Verwenden von Spy++](../debugger/using-spy-increment.md)
- [Spy++-Ansichten](../debugger/spy-increment-views.md)
- [Spy++-Referenz](../debugger/spy-increment-reference.md)