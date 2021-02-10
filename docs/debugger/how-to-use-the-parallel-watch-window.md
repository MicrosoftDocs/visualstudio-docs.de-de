---
title: Festlegen einer Überwachung für Variablen in parallelen Threads | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie eine Überwachung für parallele Threads in Visual Studio einrichten. Sie können die Werte eines Ausdrucks für mehrere Threads gleichzeitig Anzeigen.
ms.custom: SEO-VS-2020
ms.date: 04/25/2017
ms.topic: how-to
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cea9fb1733e479f413368f0f4c5c9fccfc523f6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840950"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Festlegen einer Überwachung für Variablen in parallelen Threads in Visual Studio (C#, Visual Basic, C++)
Im parallelen Überwachungsfenster können Sie gleichzeitig die Werte anzeigen, die ein Ausdruck auf mehreren Threads enthält. Jede Zeile stellt einen Thread in einer Anwendung ausgeführten dar. Allerdings wird ein Thread möglicherweise in mehreren Zeilen angezeigt werden. Genauer gesagt stellt jede Zeile einen Funktionsaufruf dar, dessen Funktionssignatur der Funktion auf dem aktuellen Stapelrahmen entspricht. Sie können die Elemente in den Spalten sortieren, neu anordnen, entfernen und gruppieren. Sie können Threads kennzeichnen bzw. die Kennzeichnung aufheben, ihn einfrieren (anhalten) und reaktivieren (fortsetzen). Die folgenden Spalten werden im Fenster **Parallele Überwachung** angezeigt:

- Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.

- Die Spalte mit aktuellen Threads, in der ein gelber Pfeil einen aktuellen Thread kennzeichnet (ein grüner Pfeil mit einem geschweiften Ende zeigt an, dass ein nicht aktueller Thread über den aktuellen Debuggerkontext verfügt).

- Eine konfigurierbare Spalte, in der der Computer, der Prozess, die Kachel, die Aufgabe und der Thread angezeigt werden können.

  > [!TIP]
  > Sie müssen das Fenster **Aufgabe** öffnen, um die Aufgabeninformationen im Fenster **Parallele Überwachung** anzuzeigen.

- Die leeren Spalten *Überwachung hinzufügen*, in denen Ausdrücke zur Überwachung eingegeben werden können.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>So zeigen Sie das parallele Überwachungsfenster an

1. Legen Sie einen Haltepunkt im Code fest.

2. Klicken Sie in der Menüleiste auf **Debuggen** und dann auf **Debuggen starten**. Warten Sie, bis die Anwendung den Haltepunkt erreicht hat.

3. Klicken Sie in der Menüleiste auf **Debuggen**, **Fenster**, **Parallele Überwachung**, und wählen Sie dann ein Überwachungsfenster aus. Sie können bis zu vier Fenster öffnen.

### <a name="to-add-a-watch-expression"></a>So fügen Sie einen Überwachungsausdruck hinzu

- Wählen Sie eine der leeren Spalten *Überwachung hinzufügen* aus, und geben Sie dann einen Überwachungsausdruck ein.

### <a name="to-flag-or-unflag-a-thread"></a>So Kennzeichnen Sie einen Thread bzw. haben die Kennzeichnung auf

- Wählen Sie die Spalte zur Kennzeichnung für die Zeile (erste Spalte) aus, oder öffnen Sie das Kontextmenü für den Thread, und wählen Sie **Kennzeichnen** oder **Kennzeichnung aufheben** aus.

### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an

- Klicken Sie auf die Schaltfläche **Nur gekennzeichnete anzeigen** in der linken oberen Ecke des Fensters **Parallele Überwachung** aus.

### <a name="to-switch-to-another-thread"></a>So wechseln Sie zu einem anderen Thread

- Doppelklicken Sie auf die Spalte aktueller Threads (zweite Spalte). (Tastatur: Wählen Sie die Zeile aus, und drücken Sie die EINGABETASTE.)

### <a name="to-sort-a-column"></a>So sortieren Sie eine Spalte

- Wählen Sie Spaltenüberschrift aus.

### <a name="to-group-threads"></a>So gruppieren Sie Threads

- Öffnen Sie das Kontextmenü für das parallele Überwachungsfenster, wählen Sie die Option **Gruppieren nach** aus, und wählen Sie dann das entsprechende Untermenüelement aus.

### <a name="to-freeze-or-thaw-threads"></a>So frieren Sie Threads ein oder reaktivieren sie

- Öffnen Sie das Kontextmenü für die Zeile, und wählen Sie dann **Einfrieren** oder **Reaktivieren** aus.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>So exportieren Sie Daten in das parallele Überwachungsfenster

- Wählen Sie die Schaltfläche **In Excel öffnen** aus, und wählen Sie dann **Exportieren nach CSV** oder **In Excel öffnen** aus.

### <a name="to-filter-by-a-boolean-expression"></a>So filtern Sie nach einem booleschen Ausdruck

- Geben Sie im Feld **Nach booleschem Ausdruck filtern** einen booleschen Ausdruck ein. Vom Debugger wird der Ausdruck für jeden Threadkontext ausgewertet. Nur Zeilen mit einem Wert von `true` werden angezeigt.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [How to: Verwenden des Fensters „GPU-Threads“](../debugger/how-to-use-the-gpu-threads-window.md)
- [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)