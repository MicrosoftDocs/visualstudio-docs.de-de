---
title: Anzeigen von Threads im Debugger | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie das Fenster „Threads“ verwenden, um Threads zu untersuchen und zu steuern. Sie können Threads gruppieren, sortieren, kennzeichnen, anhalten, fortsetzen und suchen sowie Spalten auswählen und Aufruflisten anzeigen.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd11e722886b77e9faaace768cc30a74c759903f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884207"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Anzeigen von Threads im Visual Studio-Debugger mithilfe des Fensters „Threads“ (C#, Visual Basic, C++)
Im Fenster **Threads** können Sie Threads in der gedebuggten Anwendung überprüfen und diese bearbeiten. Eine Schritt-für-Schritt-Anleitung zur Verwendung des Fensters **Threads** finden Sie unter [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters „Threads“](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Verwenden des Fensters „Threads“
 Das Fenster **Threads** enthält eine Tabelle, in der jede Zeile einen separaten Thread in der Anwendung beschreibt. Standardmäßig sind in der Tabelle alle Threads in der Anwendung aufgelistet. Sie können die Liste jedoch filtern, sodass nur die für Sie relevanten Threads angezeigt werden. Jede Spalte beschreibt einen anderen Typ von Informationen. Sie können auch einige Spalten ausblenden. Wenn Sie alle Spalten einblenden, werden die folgenden Spalten von links nach rechts angezeigt:

- **Flag**: In dieser unbeschrifteten Spalte können Sie einen Thread markieren, der besondere Aufmerksamkeit erhalten soll. Weitere Informationen zum Kennzeichnen von Threads finden Sie unter [ Kennzeichnen von Threads und Aufheben der Kennzeichnung](../debugger/how-to-flag-and-unflag-threads.md).

- **Aktueller Thread**: In dieser unbeschrifteten Spalte wird der aktuelle Thread durch einen gelben Pfeil gekennzeichnet. Ein Pfeilumriss gibt den aktuellen Debuggerkontext für einen nicht aktuellen Thread an.

- **ID:** Zeigt die Identifikationsnummer für jeden Thread an.

- **Verwaltete ID**: Zeigt die verwalteten Identifikationsnummern für verwaltete Threads an.

- **Kategorie:** Zeigt die Kategorie von Threads als Benutzeroberflächenthreads, Remoteprozeduraufruf-Handler oder Arbeitsthreads an. In einer speziellen Kategorie wird der Hauptthread der Anwendung angegeben.

- **Name**: Identifiziert jeden Thread anhand des Namens, sofern er einen hat, oder als \<No Name>.

- **Standort**: Zeigt an, wo der Thread ausgeführt wird. Sie können diesen Speicherort erweitern, um die vollständige Aufrufliste für den Thread anzuzeigen.

- **Priorität:** Eine (standardmäßig ausgeblendete) erweiterte Spalte, welche die Priorität bzw. Rangfolge anzeigt, die das System dem einzelnen Thread zugewiesen hat.

- **Affinitätsmaske**: Eine (standardmäßig ausgeblendete) erweiterte Spalte, die die Prozessoraffinitätsmaske für jeden Thread anzeigt. In einem Multiprozessorsystem bestimmt die Affinitätsmaske die Prozessoren, auf denen ein Thread ausgeführt werden kann.

- **Angehaltene Anzahl**: Eine (standardmäßig ausgeblendete) erweiterte Spalte, die die Anzahl der angehaltenen Threads anzeigt. Dieser Zähler bestimmt, ob ein Thread ausgeführt werden kann. Weitere Informationen zur Anzahl der angehaltenen Threads finden Sie unter [Einfrieren und Reaktivieren von Threads](#freeze-and-thaw-threads).

- **Prozessname**: Eine (standardmäßig ausgeblendete) erweiterte Spalte, die den Prozess anzeigt, zu der jeder Thread gehört. Die Daten in dieser Spalte können nützlich sein, wenn Sie viele Prozesse debuggen.

- **Prozess-ID**: Eine (standardmäßig ausgeblendete) erweiterte Spalte, welche die Prozess-ID anzeigt, zu der jeder Thread gehört.

- **Transportqualifizierer**: Eine (standardmäßig ausgeblendete) erweiterte Spalte, die eindeutig den Computer identifiziert, mit dem der Debugger verbunden ist.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>So zeigen Sie das Fenster Threads im Unterbrechungs- oder Ausführmodus an

- Wenn sich Visual Studio im Debugmodus befindet, wählen Sie das Menü **Debuggen** aus, zeigen Sie auf **Windows**, und wählen Sie dann **Threads** aus.

### <a name="to-display-or-hide-a-column"></a>So blenden Sie Spalten ein oder aus

- Wählen Sie in der Symbolleiste am oberen Rand des Fensters **Threads** die Option **Spalten** aus. Wählen Sie dann den Namen der Spalte aus, die Sie einblenden möchten. Löschen Sie den Namen der Spalte, die Sie ausblenden möchten.

## <a name="display-flagged-threads"></a>Anzeigen gekennzeichneter Threads
 Einen Thread, der besondere Aufmerksamkeit erhalten soll, können Sie kennzeichnen, indem Sie ihn im Fenster **Threads** mit einem Symbol markieren. Weitere Informationen finden Sie unter [Vorgehensweise: Kennzeichnen von Threads und Aufheben der Kennzeichnung](../debugger/how-to-flag-and-unflag-threads.md). Im Fenster **Threads** können Sie festlegen, dass alle Threads oder nur die gekennzeichneten Threads angezeigt werden.

### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an

- Wählen Sie in der Symbolleiste am oberen Rand des Fensters **Threads** die Option **Nur gekennzeichnete Threads anzeigen** aus. (Wenn die Option abgeblendet ist, müssen Sie zuerst einige Threads markieren.)

## <a name="freeze-and-thaw-threads"></a>Einfrieren und Reaktivieren von Threads
 Wenn ein Thread eingefroren ist, wird die Threadausführung vom System auch dann nicht gestartet, wenn Ressourcen verfügbar sind.

 In nativem Code kann die Ausführung von Threads angehalten und fortgesetzt werden, indem die Windows-Funktionen `SuspendThread` bzw. `ResumeThread` aufgerufen werden. Rufen Sie alternativ die MFC-Funktionen [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) bzw. [CWinThread::ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread) auf. Wenn Sie `SuspendThread` oder `ResumeThread` aufrufen, ändert sich die *Angehaltene Anzahl*, die im Fenster **Threads** angezeigt wird. Die Anzahl der angehaltenen Threads ändert sich nicht, wenn Sie einen nativen Thread einfrieren oder reaktivieren. Im nativen Code kann ein Thread nur ausgeführt werden, wenn er reaktiviert ist und sein Wert für „Angehaltene Anzahl“ 0 (null) beträgt.

 In verwaltetem Code ändert sich die Anzahl der angehaltenen Threads, wenn Sie einen Thread einfrieren oder reaktivieren. Wenn Sie einen Thread in verwaltetem Code einfrieren, hat er für „Angehaltene Anzahl“ den Wert 1. Wenn Sie einen Thread in nativem Code einfrieren, hat er für „Angehaltene Anzahl“ den Wert 0, es sei denn, Sie haben den `SuspendThread`-Aufruf verwendet.

> [!NOTE]
> Beim Debuggen eines Aufrufs vom nativen Code in den verwalteten Code wird der verwaltete Code im selben physischen Thread ausgeführt wie der native Code, durch den er aufgerufen wurde. Durch Unterbrechen oder Sperren des systemeigenen Threads wird auch der verwaltete Code gesperrt.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>So können Sie die Ausführung eines Threads einfrieren oder reaktivieren

- Wählen Sie in der Symbolleiste am oberen Rand des Fensters **Threads** die Option **Threads einfrieren** oder **Threads reaktivieren** aus.

     Dieser Vorgang wirkt sich nur auf Threads aus, die im Fenster **Threads** ausgewählt sind.

### <a name="switch-to-another-thread"></a>Wechseln zu einem anderen Thread

Ein gelber Pfeil gibt den aktuellen Thread (und den Speicherort des Ausführungszeigers) an. Ein grüner Pfeil in Wellenform zeigt an, dass ein nicht aktueller Thread über den aktuellen Debuggerkontext verfügt.

#### <a name="to-switch-to-another-thread"></a>So wechseln Sie zu einem anderen Thread

- Führen Sie einen der folgenden Schritte aus:

  - Doppelklicken Sie auf einen beliebigen Thread.

  - Klicken Sie mit der rechten Maustaste auf einen Thread, und wählen Sie **Zu Thread wechseln** aus.

## <a name="group-and-sort-threads"></a>Gruppieren und Sortieren von Threads
 Beim Gruppieren von Threads wird in der Tabelle eine Überschrift für jede Gruppe angezeigt. Die Überschrift enthält eine Gruppenbeschreibung, z. B. **Arbeitsthread** oder **Nicht gekennzeichnete Threads**, und ein Struktursteuerelement. Die einzelnen Threads jeder Gruppe werden unter der Gruppenüberschrift angezeigt. Wenn Sie die einzelnen Threads einer Gruppe ausblenden möchten, können Sie die Gruppe mithilfe des Strukturansicht-Steuerelements reduzieren.

 Da die Gruppierung Vorrang gegenüber der Sortierung hat, können Sie Threads z. B. nach Kategorien gruppieren und anschließend in den einzelnen Kategorien nach ID sortieren.

### <a name="to-sort-threads"></a>So sortieren Sie Threads

1. Wählen Sie in der Symbolleiste oben im Fenster **Threads** die Schaltfläche am oberen Rand einer beliebigen Spalte aus.

     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.

2. Wenn Sie die Sortierreihenfolge umkehren möchten, klicken Sie noch mal auf Sie dieselbe Schaltfläche.

     Threads, die am Anfang der Liste angezeigt wurden, werden nun am Ende der Liste aufgeführt.

### <a name="to-group-threads"></a>So gruppieren Sie Threads

- Wählen Sie in der Symbolleiste des Fensters **Threads** die Liste **Gruppieren nach** aus, und wählen Sie anschließend die Kriterien aus, anhand derer Sie Threads gruppieren möchten.

### <a name="to-sort-threads-within-groups"></a>So sortieren Sie Threads innerhalb von Gruppen

1. Wählen Sie in der Symbolleiste am oberen Rand des Fensters **Threads** die Liste **Gruppieren nach** aus, und wählen Sie anschließend die Kriterien aus, anhand derer Sie Threads gruppieren möchten.

2. Wählen Sie im Fenster **Threads** die Schaltfläche am oberen Rand einer beliebigen Spalte aus.

     Die Threads werden jetzt nach den Werten in dieser Spalte sortiert.

### <a name="to-expand-or-collapse-all-groups"></a>So erweitern oder reduzieren Sie alle Gruppen

- Wählen Sie in der Symbolleiste am oberen Rand des Fensters **Threads** die Option **Gruppen erweitern** oder **Gruppen reduzieren** aus.

## <a name="search-for-specific-threads"></a>Suchen nach bestimmten Threads
 Im Fenster **Threads** können Sie nach Threads suchen, die einer bestimmten Zeichenfolge entsprechen. Wenn Sie nach Threads suchen, werden im Fenster alle Threads angezeigt, die mit der Suchzeichenfolge in einer beliebigen Spalte übereinstimmen. Zu diesen Informationen zählt der Threadspeicherort, der am oberen Rand der Aufrufliste in der Spalte **Speicherort** angezeigt wird. Standardmäßig wird nicht die vollständige Aufrufliste durchsucht.

### <a name="to-search-for-specific-threads"></a>So suchen Sie nach bestimmten Threads

1. Wechseln Sie auf der Symbolleiste am oberen Rand des Fensters **Threads** in das Feld **Suchen**, und führen Sie Folgendes aus:

     - Geben Sie eine Suchzeichenfolge ein, und drücken Sie dann die **EINGABETASTE**.

     \- oder –

     - Wählen Sie die Dropdownliste neben dem Feld **Suchen** aus, und wählen Sie dann eine Suchzeichenfolge aus einem früheren Suchvorgang aus.

2. (Optional) Wenn bei der Suche die vollständige Aufrufliste berücksichtigt werden soll, wählen Sie **Aufrufliste durchsuchen** aus.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Anzeigen von Threadaufruflisten und Wechseln zwischen Frames
In einem Multithreadprogramm verfügt jeder Thread über eine eigene Aufrufliste. Das Fenster **Threads** bietet eine benutzerfreundliche Möglichkeit, sich diese anzeigen zu lassen.

> [!TIP]
> Verwenden Sie das Fenster [Parallele Stapel](../debugger/get-started-debugging-multithreaded-apps.md), um eine visuelle Darstellung der Aufrufliste für die einzelnen Threads zu erhalten.

### <a name="to-view-the-call-stack-of-a-thread"></a>So zeigen Sie die Aufrufliste eines Threads an

- Wählen Sie in der Spalte **Speicherort** das umgekehrte Dreieck neben dem Threadspeicherort aus.

     Der Speicherort wird erweitert, und die Aufrufliste für den Thread wird angezeigt.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>So können Sie die Aufruflisten aller Threads anzeigen oder reduzieren

- Wählen Sie in der Symbolleiste am oberen Rand des Fensters **Threads** die Option **Expand Call Stacks** (Aufruflisten erweitern) oder **Collapse Call Stacks** (Aufruflisten reduzieren) aus.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debuggen von Multithreadanwendungen in Visual Studio](../debugger/get-started-debugging-multithreaded-apps.md)
