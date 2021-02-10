---
title: Verwenden von GPU-Threads im Debugger | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie das Fenster „GPU-Threads“ verwenden, um Threads zu untersuchen und mit diesen zu arbeiten, die auf der GPU in der Anwendung ausgeführt werden, die Sie in Visual Studio debuggen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04a480daae7f5883cad9fa74e9d51d4df0f4485f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840963"
---
# <a name="how-to-use-the-gpu-threads-window-c"></a>Vorgehensweise: Verwenden des Fensters „GPU-Threads“ (C++)
Im Fenster "GPU-Threads" können Sie Threads in der debuggten GPU überprüfen und diese bearbeiten. Weitere Informationen zu den Anwendungen, die in der GPU ausgeführt werden, finden Sie unter [Übersicht über C++ AMP](/cpp/parallel/amp/cpp-amp-overview).

 Das GPU-Threadfenster enthält eine Tabelle, in der jede Zeile einen Satz GPU-Threads darstellt, die in allen Spalten über die gleichen Werte verfügen. Sie können Elemente in den Spalten sortieren, neu anordnen, entfernen und gruppieren. Sie können Threads aus dem GPU-Threadfenster heraus kennzeichnen, die Kennzeichnung aufheben, sie einfrieren (anhalten), und reaktivieren (fortsetzen). Die folgenden Spalten werden im GPU-Threadfenster angezeigt:

- Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.

- Die Spalte für den aktuellen Thread, in der ein gelber Pfeil den aktuellen Thread kennzeichnet.

- Die Spalte **Threadanzahl**, in der die Anzahl von Threads an derselben Position angezeigt wird.

- Die Spalte **Zeile**, in der die Codezeile angezeigt wird, in der sich die jeweilige Threadgruppe befindet.

- Die Spalte **Adresse**, in der die Anweisungsadresse angezeigt wird, in der sich die jeweilige Threadgruppe befindet. Standardmäßig ist diese Spalte ausgeblendet.

- Die Spalte **Position**, in der die Position im Quellcode angegeben ist.

- Die Spalte **Status**, in der angegeben ist, ob der Thread aktiv, blockiert oder nicht gestartet bzw. abgeschlossen ist.

- Die Spalte **Kachel**, in der der Kachelindex für die Threads in der Zeile angezeigt wird.

  Im Header der Tabelle werden die Kachel und der Thread, die dargestellt werden, angezeigt.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-gpu-threads-window"></a>So öffnen Sie das GPU-Threadfenster

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften** aus.

2. Wählen Sie im Fenster **Eigenschaftenseiten** für das Projekt unter **Konfigurationseigenschaften** die Option **Debuggen** aus.

3. Wählen Sie in der Liste **Zu startender Debugger** die Option **Lokaler Windows-Debugger** aus. Wählen Sie in der Liste **Debuggertyp** die Option **Nur GPU** aus. Sie müssen für diesen Debugger festlegen, im Code, der auf der GPU ausgeführt wird, am Haltepunkt zu unterbrechen.

4. Klicken Sie auf die Schaltfläche **OK** .

5. Legen Sie einen Haltepunkt im GPU-Code fest.

6. Klicken Sie in der Menüleiste auf **Debuggen** und dann auf **Debuggen starten**. Warten Sie, bis die Anwendung den Haltepunkt erreicht hat.

7. Klicken Sie in der Menüleiste auf **Debuggen**, **Fenster** und **GPU-Threads**.

### <a name="to-switch-to-a-different-thread"></a>So wechseln zu einem anderen Thread

- Doppelklicken Sie auf die Spalte. (Tastatur: Wählen Sie die Zeile aus, und drücken Sie die EINGABETASTE.)

### <a name="to-display-a-particular-tile-and-thread"></a>So zeigen Sie eine bestimmte Kachel und einen bestimmten Thread an

1. Klicken Sie im GPU-Threadfenster auf die Schaltfläche **Threadumschaltung erweitern**.

2. Geben Sie die Kachel- und Threadwerte in den Textfeldern an.

3. Wählen Sie die Schaltfläche mit dem Pfeil darauf aus.

### <a name="to-display-or-hide-a-column"></a>So blenden Sie Spalten ein oder aus

- Öffnen Sie das Kontextmenü für das GPU-Threadfenster, klicken Sie auf die Option **Spalten**, und wählen Sie anschließend die Spalte aus, die Sie anzeigen oder ausblenden möchten.

### <a name="to-sort-by-a-column"></a>So sortieren Sie nach Spalte

- Wählen Sie Spaltenüberschrift aus.

### <a name="to-group-threads"></a>So gruppieren Sie Threads

- Öffnen Sie das Kontextmenü für das GPU-Threadfenster, klicken Sie auf **Gruppieren nach**, und wählen Sie dann einen der angezeigten Spaltennamen aus. Wählen Sie **Keine**, um die Gruppierung der Threads aufzuheben.

### <a name="to-freeze-or-thaw-a-row-of-threads"></a>So können Sie eine Threadzeile einfrieren oder reaktivieren

- Öffnen Sie das Kontextmenü für die Zeile, und wählen Sie dann **Einfrieren** oder **Reaktivieren** aus.

### <a name="to-flag-or-unflag-a-row-of-threads"></a>So können Sie Threadzeile kennzeichnen oder die Kennzeichnung aufheben

- Wählen Sie die Spalte zur Kennzeichnung für den Thread aus, oder öffnen Sie das Kontextmenü für den Thread, und wählen Sie **Kennzeichnen** oder **Kennzeichnung aufheben** aus.

### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an

- Wählen Sie im GPU-Threadfenster die Schaltfläche "Kennzeichnen" aus.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [How to: Verwenden des Fensters „Parallele Überwachung“](../debugger/how-to-use-the-parallel-watch-window.md)
- [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)