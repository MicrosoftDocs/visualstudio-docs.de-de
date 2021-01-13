---
title: Meldungsansicht | Microsoft-Dokumentation
description: Fenster, Threads und Prozesse verfügen jeweils über einen zugeordneten Nachrichtendatenstrom, der in einem Meldungsansichtsfenster angezeigt werden kann. Es wird beschrieben, wie Sie eine Meldungsansicht öffnen und steuern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 692902b2d2b612c71c2d1dc0f936c7550f430847
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903402"
---
# <a name="messages-view"></a>Meldungsansicht
Jedes Fenster verfügt über einen zugehörigen Meldungsdatenstrom. In einem Meldungsansichtsfenster wird dieser Meldungsdatenstrom angezeigt. Angezeigt werden das Fensterhandle, der Meldungscode und die Meldung. Sie können eine Meldungsansicht auch für einen Thread oder einen Prozess erstellen. Dadurch können Sie Meldungen anzeigen, die an alle Fenster gesendet werden, die sich im Besitz eines bestimmten Prozesses oder Threads befinden. Dies ist besonders hilfreich für die Erfassung von Fensterinitialisierungsmeldungen.

 Die folgende Abbildung zeigt ein typisches Meldungsansichtsfenster. Beachten Sie, dass die erste Spalte das Fensterhandle und die zweite Spalte einen Meldungscode (erläutert unter [Meldungscodes](../debugger/message-codes.md)) enthält. Rechts befinden sich die decodierten Meldungsparameter und die Rückgabewerte.

 ![Spy&#43;&#43;-Nachrichtenansicht](../debugger/media/spy--_messagesview.png "Spy++_MessagesView") Spy++-Nachrichtenansicht

## <a name="procedures"></a>Verfahren

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>So öffnen Sie eine Meldungsansicht für ein Fenster, einen Prozess oder einen Thread

1. Verschieben Sie den Fokus in ein [Fensteransichts](../debugger/windows-view.md)-, [Prozessansichts](../debugger/processes-view.md)- oder [Threadansichts](../debugger/threads-view.md)-Fenster.

2. Suchen Sie nach dem Knoten für das Element, dessen Meldungen Sie untersuchen möchten, und wählen Sie ihn aus.

3. Wählen Sie im Menü **Spy** die Option **Meldungen protokollieren** aus.

     Das Dialogfeld [Meldungsoptionen](../debugger/message-options-dialog-box.md) wird geöffnet.

4. Wählen Sie die Optionen für die Meldung aus, die Sie anzeigen möchten.

5. Drücken Sie **OK**, um mit der Protokollierung von Meldungen zu beginnen.

     Ein Meldungsansichtsfenster wird geöffnet, und der Spy++-Symbolleiste wird ein Menü **Meldungen** hinzugefügt. Abhängig von den ausgewählten Optionen wird der Meldungsdatenstrom in das aktive Meldungsansichtsfenster gestartet.

6. Wenn genügend Meldungen eingegangen sind, wählen Sie **Protokollierung beenden** im Menü **Meldungen** aus.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Steuern der Meldungsansicht](../debugger/how-to-control-messages-view.md): Erläutert die Verwaltung der Meldungsansicht.

 [Öffnen der Meldungsansicht über „Fenster suchen“](../debugger/how-to-open-messages-view-from-find-window.md): Erläutert, wie die Meldungsansicht im Dialogfeld „Fenster suchen“ geöffnet wird.

 [Suchen einer Meldung in der Meldungsansicht](../debugger/how-to-search-for-a-message-in-messages-view.md): Erläutert, wie Sie in der Meldungsansicht eine bestimmte Meldung finden.

 [Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md): Erläutert das Starten und Beenden der Meldungsprotokollierung.

 [Meldungscodes](../debugger/message-codes.md): Definiert die Codes, die in der Meldungsansicht aufgelistet werden.

 [Anzeigen von Meldungseigenschaften](../debugger/how-to-display-message-properties.md): Erläutert, wie Sie weitere Informationen zu einer Meldung anzeigen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Spy++-Ansichten](../debugger/spy-increment-views.md): Erläutert die Spy++-Strukturansichten von Fenstern, Meldungen, Prozessen und Threads.

 [Verwenden von Spy++](../debugger/using-spy-increment.md): Enthält eine Einführung in das Spy++-Tool und erläutert, wie es verwendet werden kann.

 [Dialogfeld „Meldungsoptionen“](../debugger/message-options-dialog-box.md): Dient zur Auswahl der in der aktiven Meldungsansicht angezeigten Meldungen.

 [Dialogfeld „Meldungssuche“](../debugger/message-search-dialog-box.md): Dient zum Suchen des Knotens für eine bestimmte Meldung in der Meldungsansicht.

 [Dialogfeld „Meldungseigenschaften“](../debugger/message-properties-dialog-box.md): Dient zum Anzeigen der Eigenschaften einer in der Meldungsansicht ausgewählten Meldung.

 [Spy++-Referenz](../debugger/spy-increment-reference.md): Enthält Abschnitte mit Beschreibungen der einzelnen Menüs und Dialogfelder von Spy++.