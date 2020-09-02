---
title: 'Gewusst wie: Verwenden des Fensters "parallele Überwachung" | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 734a55cb06ee46afc6fc3518d6dffe349690d3d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697497"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Gewusst wie: Verwenden des parallelen Überwachungsfensters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im parallelen Überwachungsfenster können Sie gleichzeitig die Werte anzeigen, die ein Ausdruck auf mehreren Threads enthält. Jede Zeile stellt einen Thread in einer Anwendung ausgeführten dar. Allerdings wird ein Thread möglicherweise in mehreren Zeilen angezeigt werden. Genauer gesagt stellt jede Zeile einen Funktionsaufruf dar, dessen Funktionssignatur der Funktion auf dem aktuellen Stapelrahmen entspricht. Sie können die Elemente in den Spalten sortieren, neu anordnen, entfernen und gruppieren. Sie können Threads kennzeichnen bzw. die Kennzeichnung aufheben, ihn einfrieren (anhalten) und reaktivieren (fortsetzen). Die folgenden Spalten werden im Fenster **Parallele Überwachung** angezeigt:  
  
- Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.  
  
- Die Framespalte, in der ein Pfeil den ausgewählten Frame angibt.  
  
- Eine konfigurierbare Spalte, in der der Computer, der Prozess, die Kachel, die Aufgabe und der Thread angezeigt werden können.  
  
  > [!TIP]
  > Sie müssen das Fenster **parallele Aufgabe** öffnen, um die Aufgabeninformationen im Fenster **parallele Überwachung** anzuzeigen.  
  
- Die **\<Add Watch>** Spalte, in der Sie die zu überwachenden Ausdrücke eingeben können.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>So zeigen Sie das parallele Überwachungsfenster an  
  
1. Legen Sie einen Haltepunkt im Code fest.  
  
2. Klicken Sie in der Menüleiste auf **Debuggen** und dann auf **Debuggen starten**. Warten Sie, bis die Anwendung den Haltepunkt erreicht hat.  
  
3. Klicken Sie in der Menüleiste auf **Debuggen**, **Fenster**, **Parallele Überwachung**, und wählen Sie dann ein Überwachungsfenster aus. Sie können bis zu vier Fenster öffnen.  
  
### <a name="to-add-a-watch-expression"></a>So fügen Sie einen Überwachungsausdruck hinzu  
  
- Wählen Sie **\<Add Watch>** einen Überwachungs Ausdruck aus, und geben Sie ihn an  
  
### <a name="to-flag-or-unflag-a-thread"></a>So Kennzeichnen Sie einen Thread bzw. haben die Kennzeichnung auf  
  
- Wählen Sie die Spalte Flag für die Zeile aus, oder öffnen Sie das Kontextmenü für den Thread, und wählen Sie **Flag** oder **Flag**aufheben aus.  
  
### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an  
  
- Wählen Sie in der oberen linken Ecke des Fensters **parallele Überwachung** die Schaltfläche nur gekennzeichnete anzeigen aus.  
  
### <a name="to-switch-frames"></a>So wechseln Sie Frames  
  
- Doppelklicken Sie auf die Framespalte. (Tastatur: Wählen Sie die Zeile aus, und drücken Sie die EINGABETASTE.)  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Gewusst wie: Verwenden des Fensters "GPU-Threads"](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
