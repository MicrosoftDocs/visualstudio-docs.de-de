---
title: Anzeigen von Threads im Fenster „Parallele Stapel“ | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie parallele Stapel verwenden, um das Debuggen von Multithreadanwendungen zu unterstützen. Sie können Stapelinformationen für alle Threads sowie aufgabenorientierte Aufruflisteninformationen anzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7b92f4e2faf2043c26c7119b6f9754edd3bdc990
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884389"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Anzeigen von Threads und Tasks im Fenster „Parallele Stapel“ (C#, Visual Basic, C++)

Das Fenster **Parallele Stapel** ist beim Debuggen von Multithreadanwendungen hilfreich. Das Fenster enthält mehrere Ansichten:

- In der [Threadansicht](#threads-view) werden Informationen zur Aufrufliste für alle Threads in der App angezeigt. Sie können zwischen Threads und Stapelrahmen in diesen Threads navigieren.

- In der [Aufgabenansicht](#tasks-view) werden aufgabenorientierte Aufruflisteninformationen angezeigt.
  - In verwaltetem Code werden in der **Aufgabenansicht** Aufruflisten von <xref:System.Threading.Tasks.Task?displayProperty=fullName>-Objekten angezeigt.
  - In nativem Code werden in der **Aufgabenansicht** Aufruflisten von [Aufgabengruppen](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [parallelen Algorithmen](/cpp/parallel/concrt/parallel-algorithms), [asynchronen Agents](/cpp/parallel/concrt/asynchronous-agents) und [einfachen Aufgaben](/cpp/parallel/concrt/task-scheduler-concurrency-runtime) angezeigt.

- In der [Methodenansicht](#method-view) wird die Aufrufliste einer ausgewählten Methode pivotiert.

## <a name="use-the-parallel-stacks-window"></a>Verwenden des Fensters „Parallele Stapel“

Sie müssen sich in einer Debugsitzung befinden, um das Fenster **Parallele Stapel** zu öffnen. Klicken Sie auf **Debuggen** > **Fenster** > **Parallele Stapel**.

### <a name="toolbar-controls"></a>Symbolleisten-Steuerelemente

Das Fenster **Parallele Stapel** enthält die folgenden Symbolleisten-Steuerelemente:

![Symbolleiste im Fenster "Parallele Stapel"](../debugger/media/parallel_stackstoolbar.png "Symbolleiste „Parallele Stapel“")

|Symbol|Steuerelement|Beschreibung|
|-|-|-|
|![Kombinationsfeld Threads/Aufgaben](media/parallel_toolbar1.png "Kombinationsfeld Threads/Aufgaben")|Kombinationsfeld **Threads**/**Aufgaben**|Schaltet die Ansicht zwischen Aufruflisten von Threads und Aufruflisten von Aufgaben um. Weitere Informationen finden Sie unter [Aufgabenansicht](#tasks-view) und [Threadansicht](#threads-view).|
|![Symbol „Nur gekennzeichnete Elemente anzeigen“](media/parallel_toolbar2.png "Symbol „Nur gekennzeichnete Elemente anzeigen“")|Nur gekennzeichnete Elemente anzeigen|Mit dieser Option werden nur Aufruflisten für die Threads angezeigt, die in anderen Debuggerfenstern wie den Fenstern **GPU-Threads** und **Parallele Überwachung** gekennzeichnet wurden.|
|![Symbol „Methodenansicht umschalten“](media/parallel_toolbar3.png "Symbol „Methodenansicht umschalten“")|**Methodenansicht** umschalten|Mit dieser Option können Sie zwischen der Aufruflistenansicht und der **Methodenansicht** wechseln. Weitere Informationen finden Sie unter [Methodenansicht](#method-view).|
|![Symbol „Automatisches Scrollen zum aktuellen Stapelrahmen“](media/parallel_toolbar4.png "Symbol „Automatisches Scrollen zum aktuellen Stapelrahmen“")|Automatischen Bildlauf zu aktuellem Stapelrahmen durchführen|Mit dieser Option können Sie im Graph automatisch zum aktuellen Stapelrahmen scrollen. Dieses Feature ist nützlich, wenn Sie den aktuellen Stapelrahmen über andere Fenster ändern oder wenn Sie einen neuen Haltepunkt in großen Graphen erreichen.|
|![Symbol „Zoomsteuerung umschalten“](media/parallel_toolbar5.png "Symbol „Zoomsteuerung umschalten“")|Zoomsteuerung ein- bzw. ausschalten|Mit dieser Option wird das Zoomsteuerelement auf der linken Seite des Fensters ein- und ausgeblendet. <br /><br />Unabhängig davon, ob das Zoomsteuerelement angezeigt wird, können Sie auch herein- und herauszoomen, indem Sie **STRG** drücken und das Mausrad drehen oder indem Sie **STRG**+**UMSCHALT**+ **+** zum Hereinzoomen und **STRG**+**UMSCHALT**+ **-** zum Herauszoomen drücken. |

### <a name="stack-frame-icons"></a>Stapelrahmensymbole
Die folgenden Symbole geben Informationen zu den aktiven und aktuellen Stapelrahmen in allen Ansichten an:

|Symbol|Beschreibung|
|-|-|
|![Gelber Pfeil](media/icon_parallelyellowarrow.gif)|Dieses Symbol gibt die aktuelle Position (aktiver Stapelrahmen) des aktuellen Threads an.|
|![Threadsymbol](media/icon_parallelthreads.gif)|Dieses Symbol gibt die aktuelle Position (aktiver Stapelrahmen) von nicht aktuellen Threads an.|
|![Grüner Pfeil](media/icon_parallelgreenarrow.gif)|Dieses Symbol gibt den aktuellen Stapelrahmen an (aktueller Debuggerkontext). Der Methodenname wird immer fett formatiert.|

### <a name="context-menu-items"></a>Kontextmenüelemente
Die folgenden Kontextmenüelemente sind verfügbar, wenn Sie mit der rechten Maustaste auf eine Methode in den Ansichten **Threads** oder **Aufgaben** klicken. Die letzten sechs Elemente sind mit denen im [Aufruflistenfenster](how-to-use-the-call-stack-window.md) identisch.

![Kontextmenü im Fenster "Parallele Stapel"](../debugger/media/parallel_contmenu.png "Kontextmenü im Fenster "Parallele Stapel"")

|Menüelement|Beschreibung|
|-|-|
|**Kennzeichnen**|Kennzeichnet das ausgewählte Element.|
|**Kennzeichnung aufheben**|Hebt die Kennzeichnung des ausgewählten Elements auf.|
|**Einfrieren**|Friert das ausgewählte Element ein.|
|**Reaktivieren**|Reaktiviert das ausgewählte Element.|
|**Zu Rahmen wechseln**|Dieses Element ist identisch mit dem entsprechenden Menübefehl im Fenster **Aufrufliste**. Im Fenster **Parallele Stapel** kann sich eine Methode jedoch in mehreren Rahmen befinden. Sie können den Rahmen auswählen, der im untergeordneten Menü des Elements enthalten sein soll. Wenn sich einer der Stapelrahmen im aktuellen Thread befindet, wird dieser Rahmen standardmäßig im untergeordneten Menü ausgewählt.|
|**Zur Aufgabe wechseln** oder **Gehe zu Thread**|Mit diesem Menüelement wechseln Sie zwischen den Ansichten **Aufgabe** und **Threads**. Dabei wird derselbe Stapelrahmen hervorgehoben.|
|**Gehe zu Quellcode**|Mit diesem Menüelement navigieren Sie zur entsprechenden Position im Quellcodefenster. |
|**Zu Disassemblierung wechseln**|Mit diesem Menüelement navigieren Sie zur entsprechenden Position im Fenster **Disassemblierung**.|
|**Externen Code anzeigen**|Blendet externen Code ein bzw. aus.|
|**Hexadezimale Anzeige**|Schaltet zwischen dezimaler und hexadezimaler Anzeige um.|
|**Threads in Quelle anzeigen**|Mit diesem Menüelement wird die Position des Threads im Quellcodefenster hervorgehoben. |
|**Symbolladeinformationen**|Mit diesem Menüelement wird das Dialogfeld **Symbolladeinformationen** geöffnet.|
|**Symboleinstellungen**|Mit diesem Menüelement wird das Dialogfeld **Symboleinstellungen** geöffnet. |

## <a name="threads-view"></a>Threadansicht

In der Ansicht **Threads** werden der Stapelrahmen und der Aufrufpfad des aktuellen Threads blau hervorgehoben. Die aktuelle Position des Threads wird vom gelben Pfeil angezeigt.

Doppelklicken Sie auf eine andere Methode, um den aktuellen Stapelrahmen zu ändern. Dies kann auch zu einem Wechsel des aktuellen Threads führen, je nachdem, ob die ausgewählte Methode Teil des aktuellen oder eines anderen Threads ist.

Wenn der Graph der Ansicht **Threads** zu groß ist, um in das Fenster zu passen, wird im Fenster das Steuerelement **Vogelperspektive** angezeigt. Sie können den Rahmen im Steuerelement bewegen, um zu verschiedenen Abschnitten des Graphen zu navigieren.

In der folgenden Abbildung wird ein Thread gezeigt, der von der Main-Methode zu einem Übergang von verwaltetem zu nativem Code wechselt. In der aktuellen Methode befinden sich sechs Threads. Ein Thread wird mit „Thread.Sleep“ fortgesetzt, während ein anderer mit „Console.WriteLine“ und dann mit „SyncTextWriter.WriteLine“ fortfährt.

 ![Ansicht „Threads“ im Fenster „Parallele Stapel“](../debugger/media/parallel_stack1.png "Ansicht "Threads" im Fenster "Parallele Stapel"")

In der folgenden Tabelle werden die Hauptfeatures der Ansicht **Threads** beschrieben:

|Legende|Elementname|BESCHREIBUNG|
|-|-|-|
|1|Aufruflistensegment oder -knoten|Dieses Element enthält eine Reihe von Methoden für einen oder mehrere Threads. Wenn keine Pfeillinien mit dem Rahmen verbunden sind, zeigt der Rahmen den gesamten Aufrufpfad für die Threads an.|
|2|Blaue Hervorhebung|Gibt den Aufrufpfad des aktuellen Threads an.|
|3|Pfeillinien|Diese verbinden Knoten, um den gesamten Aufrufpfad für den Thread bzw. die Threads darzustellen.|
|4|Knotenheader|Dieses Element zeigt die Anzahl der Prozesse und Threads für den Knoten an.|
|5|Methode|Stellt einen oder mehrere Stapelrahmen in derselben Methode dar.|
|6|QuickInfo zur Methode|Dieses Element wird angezeigt, wenn Sie auf eine Methode zeigen. In der **Threadansicht** zeigt die QuickInfo alle Threads in einer Tabelle ähnlich wie im Fenster **Threads** an. |

## <a name="tasks-view"></a>Aufgabenansicht
Wenn Ihre App <xref:System.Threading.Tasks.Task?displayProperty=fullName>-Objekte (verwalteter Code) oder `task_handle`-Objekte (nativer Code) verwendet, um Parallelität auszudrücken, können Sie die Ansicht **Aufgaben** verwenden. In der **Aufgabenansicht** werden Aufruflisten von Aufgaben anstelle von Threads angezeigt.

In der Ansicht **Aufgaben**:

- werden Aufruflisten von Threads nicht angezeigt, die keine Aufgaben ausführen.
- werden Aufruflisten von Threads, die Aufgaben ausführen, oben und unten abgeschnitten, um die relevantesten Rahmen für Aufgaben anzuzeigen.
- werden die Aufruflisten dieser Aufgaben in separaten Knoten angezeigt, wenn sich mehrere Aufgaben in einem Thread befinden.

Wechseln Sie zurück zur Ansicht **Threads**, indem Sie mit der rechten Maustaste in einen Stapelrahmen klicken und **Gehe zu Thread** auswählen, um die gesamte Aufrufliste anzuzeigen.

In der folgenden Abbildung wird die Ansicht **Threads** oben und die dazugehörige Ansicht **Aufgaben** unten veranschaulicht.

![Ansichten „Threads und Aufgaben“](../debugger/media/parallel_threads-tasks.png "Ansichten „Threads und Aufgaben“")

Zeigen Sie auf eine Methode, um eine QuickInfo mit zusätzlichen Informationen anzuzeigen. In der Ansicht **Aufgaben** zeigt die QuickInfo ähnlich wie im Fenster **Aufgaben** alle Aufgaben in einer Tabelle.

In der folgenden Abbildung werden die QuickInfo für eine Methode in der Ansicht **Threads** oben und die dazugehörige Ansicht **Aufgaben** unten angezeigt.

![QuickInfos „Threads und Aufgaben“](../debugger/media/parallel_threads-tasks-tooltips.png "QuickInfos „Threads und Aufgaben“")

## <a name="method-view"></a>Methodenansicht
Über die Ansichten **Threads** und **Aufgaben** können Sie den Graphen zur aktuellen Methode pivotieren, indem Sie in der Symbolleiste auf das Symbol **Methodenansicht umschalten** klicken. In der **Methodenansicht** werden alle Methoden für sämtliche Threads in einem Blick angezeigt, die entweder Aufrufer oder Aufgerufene der aktuellen Methode sind. In der folgenden Abbildung wird veranschaulicht, wie die gleichen Informationen in der Ansicht **Threads** links und der **Methodenansicht** rechts dargestellt werden.

![Ansichten „Threads“ und „Methode“](../debugger/media/parallel_methodview.png "Ansichten „Threads“ und „Methode“")

Wenn Sie zu einem neuen Stapelrahmen wechseln, legen Sie diese Methode als aktuelle Methode fest und die **Methodenansicht** zeigt alle Aufrufer und Aufgerufenen für die neue Methode an. Dabei werden möglicherweise einige Threads in der Ansicht eingeblendet oder ausgeblendet, je nachdem, ob die betreffende Methode in ihren Aufruflisten enthalten ist. Klicken Sie wieder auf das Symbol **Methodenansicht** in der Symbolleiste, um zur Aufruflistenansicht zurückzukehren.

## <a name="see-also"></a>Siehe auch
- [Erste Schritte zum Debuggen von Multithreadanwendungen (C#, Visual Basic, C++)](../debugger/get-started-debugging-multithreaded-apps.md)
- [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Parallele Programmierung](/dotnet/standard/parallel-programming/index)
- [Use the Tasks window (Verwenden des Fensters „Aufgaben“)](../debugger/using-the-tasks-window.md)
- [Task class (Task-Klasse)](../extensibility/debugger/task-class-internal-members.md)
