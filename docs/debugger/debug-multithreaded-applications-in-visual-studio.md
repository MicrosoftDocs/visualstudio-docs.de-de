---
title: Debuggen von Multithreadanwendungen | Microsoft-Dokumentation
description: Debuggen Sie Multithreadanwendungen in Visual Studio. Sehen Sie sich die entsprechenden Tools und weitere Artikel zum Debuggen von Multithread-Apps an.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fed6580219964ab71f5a5010060c1af193375df
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727137"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuggen von Multithreadanwendungen in Visual Studio
Ein Thread ist eine Folge von Anweisungen, für die das Betriebssystem Prozessorzeit vergibt. Jeder Prozess, der im Betriebssystem ausgeführt wird, umfasst mindestens einen Thread. Prozesse, die über mehr als einen Thread verfügen, werden als Multithreadprozesse bezeichnet.

Auf Computern mit mehreren Prozessoren, Mehrkernprozessoren oder Hyperthreadingprozessen können mehrere gleichzeitige Threads ausgeführt werden. Die parallele Verarbeitung mit vielen Threads kann die Programmleistung erheblich verbessern, andererseits aber auch das Debuggen erschweren, da zahlreiche Threads nachverfolgt werden.

Durch Multithreading können neue potenzielle Fehlertypen eingeführt werden. Beispielsweise müssen zwei oder mehr Threads auf dieselbe Ressource zugreifen, während jeweils nur ein Thread sicher auf die Ressource zugreifen kann. Um sicherzustellen, dass immer nur ein Thread auf die Ressource zugreifen kann, ist eine Form des gegenseitigen Ausschlusses erforderlich. Wenn der gegenseitige Ausschluss nicht richtig implementiert wird, kann eine *Deadlock*-Bedingung entstehen, unter der kein Thread ausgeführt wird. Deadlocks können beim Debuggen ein schwerwiegendes Problem darstellen.

## <a name="tools-for-debugging-multithreaded-apps"></a>Tools zum Debuggen von Multithread-Apps

Visual Studio stellt verschiedene Tools für das Debuggen von Multithread-Apps bereit.

- Die wichtigsten Tools für das Debuggen von Threads sind das Fenster **Threads**, Threadmarker in Quellcodefenstern, das Fenster **Parallele Stapel**, das Fenster **Parallele Überwachung** sowie die Symbolleiste **Debugspeicherort**. Weitere Informationen zum Fenster **Threads** und zur Symbolleiste **Debugspeicherort** finden Sie unter [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters „Threads“](../debugger/how-to-use-the-threads-window.md). Informationen zum Verwenden der Fenster **Parallele Stapel** und **Parallele Überwachung** finden Sie unter [Erste Schritte zum Debuggen von Multithreadanwendungen (C#, Visual Basic, C++)](../debugger/get-started-debugging-multithreaded-apps.md). In beiden Themen wird gezeigt, wie Threadmarker verwendet werden.

- Bei Code, der die [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) oder [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/) verwendet, werden für das Debuggen hauptsächlich das Fenster **Parallele Stapel**, das Fenster **Parallele Überwachung** und das Fenster **Aufgaben** verwendet, das zudem JavaScript unterstützt. Informationen zu den ersten Schritten finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung in Visual Studio (C#, Visual Basic, C++)](../debugger/walkthrough-debugging-a-parallel-application.md) und [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application).

- Zum Debuggen von Threads auf der GPU wird hauptsächlich das Fenster **GPU-Threads** verwendet. Weitere Informationen finden Sie unter [How to: Use the GPU Threads window (Vorgehensweise: Verwenden des Fensters „GPU-Threads“)](../debugger/how-to-use-the-gpu-threads-window.md)

- Die wichtigsten Tools bei Prozessen sind das Dialogfeld **An Prozess anhängen**, das Fenster **Prozesse** und die Symbolleiste **Debugspeicherort**.

Visual Studio stellt auch leistungsstarke Breakpoints und Ablaufverfolgungspunkte bereit, die beim Debuggen von Multithreadanwendungen hilfreich sein können. Verwenden Sie Breakpointbedingungen und -filter, um Breakpoints in einzelnen Threads zu platzieren. Ablaufverfolgungspunkte ermöglichen es Ihnen, die Ausführung des Programms ohne Unterbrechung zu verfolgen, um Probleme wie Deadlocks zu untersuchen. Weitere Informationen finden Sie unter [Haltepunktaktionen und Ablaufverfolgungspunkte](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Das Debuggen einer Multithreadanwendung mit einer Benutzeroberfläche kann besonders schwierig sein. Sie könnten erwägen, die Anwendung auf einem zweiten Computer auszuführen und das Remotedebuggen zu verwenden. Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Artikel zum Debuggen von Multithread-Apps

 [Erste Schritte zum Debuggen von Multithreadanwendungen (C#, Visual Basic, C++)](../debugger/get-started-debugging-multithreaded-apps.md)

Dieser Artikel enthält eine Einführung in die Features für das Threaddebuggen, wobei der Schwerpunkt auf den Features im Fenster **Parallele Stapel** und **Parallele Überwachung** liegt.

 [Tools zum Debuggen von Threads und Prozessen in Visual Studio](../debugger/debug-threads-and-processes.md)

Unter diesem Link sind die Features der Tools zum Debuggen von Threads und Prozessen aufgeführt.

 [Debuggen mehrerer Prozesse](../debugger/debug-multiple-processes.md)

Erläutert das Debuggen mehrerer Prozesse.

 [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters „Threads“](../debugger/how-to-use-the-threads-window.md).

Dieser Artikel enthält eine exemplarische Vorgehensweise zur Verwendung des Fensters **Threads** und der Symbolleiste **Debugspeicherort**.

 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)

Exemplarische Vorgehensweise, in der erläutert wird, wie die Fenster **Parallele Stapel** und **Aufgaben** verwendet werden

 [How to: Switch to another thread while debugging (Vorgehensweise: Wechseln zu einem anderen Thread während des Debuggens)](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Hier werden verschiedene Möglichkeiten erläutert, mit dem Debugkontext zu einem anderen Thread zu wechseln.

 [How to: Flag and unflag threads (Vorgehensweise: Kennzeichnen von Threads und Aufheben der Kennzeichnung)](../debugger/how-to-flag-and-unflag-threads.md)

Markieren oder Kennzeichnen von Threads, die beim Debuggen besondere Aufmerksamkeit erhalten sollen.

 [How to: Debug on a high-performance cluster (Vorgehensweise: Debuggen auf einem Hochleistungscluster)](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Techniken zum Debuggen einer Anwendung, die auf einem Hochleistungscluster ausgeführt wird.

 [Tipps zum Debuggen von Threads in nativem Code](../debugger/tips-for-debugging-threads-in-native-code.md)

Einfache Techniken, die beim Debuggen systemeigener Threads hilfreich sein können.

 [How to: Set a thread name in native code (Vorgehensweise: Festlegen eines Threadnamens in nativem Code)](../debugger/how-to-set-a-thread-name-in-native-code.md)

Geben Sie Ihrem Thread einen Namen, der im Fenster **Threads** angezeigt wird.

 [How to: Set a thread name in managed code (Vorgehensweise: Festlegen eines Threadnamens in verwaltetem Code)](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Geben Sie Ihrem Thread einen Namen, der im Fenster **Threads** angezeigt wird.

## <a name="see-also"></a>Siehe auch

- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
- [Threading](/dotnet/standard/threading/index)
- [Multithreading in components (Multithreading in Komponenten)](/previous-versions/3es4b6yy(v=vs.140))
- [Multithreadingunterstützung für älteren Code (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Debug threads and processes (Debuggen von Threads und Prozessen)](../debugger/debug-threads-and-processes.md)
- [Remotedebuggen](../debugger/remote-debugging.md)