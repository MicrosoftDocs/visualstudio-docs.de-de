---
title: Verwenden des Fensters „Aufgaben“ | Microsoft-Dokumentation
description: Aufgaben sind asynchrone Vorgänge, die gleichzeitig ausgeführt werden können. Mehrere Aufgaben können auf demselben Thread ausgeführt werden. Verwenden Sie Aufgaben, um Informationen zu Aufgaben und WinJS.Promise-Objekten anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fcae019e8854ecee9cdc553eedd3e9d2d0f28a63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948582"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Verwenden des Fensters „Aufgaben“ (C#, Visual Basic, C++)

Das Fenster **Aufgaben** ähnelt dem Fenster **Threads**. In diesem Fenster werden jedoch Informationen zu jedem <xref:System.Threading.Tasks.Task?displayProperty=fullName>-, [task_handle](/cpp/parallel/concrt/reference/task-group-class)- oder [WinJS.Promise](/previous-versions/windows/apps/br211867(v=win.10))-Objekt anstatt für die einzelnen Threads angezeigt. Wie Threads stellen auch Aufgaben asynchrone Vorgänge dar, die gleichzeitig ausgeführt werden können. Es dürfen jedoch mehrere Aufgaben im selben Thread ausgeführt werden.

In verwaltetem Code können Sie das Fenster **Aufgaben** verwenden, wenn Sie mit<xref:System.Threading.Tasks.Task?displayProperty=fullName> -Objekten oder mit den **await**- und **async**-Schlüsselwörtern arbeiten (**Await** und **Async** in Visual Basic). Weitere Informationen zu Aufgaben in verwaltetem Code finden Sie unter [Parallele Programmierung in .NET](/dotnet/standard/parallel-programming/index).

In nativem Code können Sie das Fenster **Aufgaben** verwenden, wenn Sie mit [Aufgabengruppen](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [parallelen Algorithmen](/cpp/parallel/concrt/parallel-algorithms), [asynchronen Agents](/cpp/parallel/concrt/asynchronous-agents) und [einfachen Aufgaben](/cpp/parallel/concrt/task-scheduler-concurrency-runtime) arbeiten. Weitere Informationen zu Aufgaben in nativem Code finden Sie unter [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime).

In JavaScript können Sie das Fenster „Aufgaben“ verwenden, wenn Sie mit dem promise-Code `.then` arbeiten. Weitere Informationen finden Sie unter [Asynchrone Programmierung in JavaScript (UWP-Apps)](/previous-versions/windows/apps/hh700330(v=win.10)).

Sie können das Fenster **Aufgaben** immer dann verwenden, wenn die Ausführung im Debugger unterbrochen wird. Sie können darauf zugreifen, indem Sie im Menü **Debuggen** auf **Fenster** und anschließend auf **Aufgaben** klicken. In der folgenden Abbildung wird das Fenster **Aufgaben** im Standardmodus dargestellt.

![Fenster „Aufgaben“](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> In verwaltetem Code wird ein <xref:System.Threading.Tasks.Task>-Objekt mit dem Status [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>) oder [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) möglicherweise nicht im Fenster **Aufgaben** angezeigt, wenn sich verwaltete Threads in einem Standby- oder Verknüpfungszustand befinden.

## <a name="tasks-column-information"></a>Informationen in der Spalte „Aufgaben“

In den Spalten im Fenster **Aufgaben** sind die folgenden Informationen angegeben.

|Spaltenname|Beschreibung|
|-----------------|-----------------|
|**Flags**|Zeigt an, welche Aufgaben gekennzeichnet sind. Zudem können Sie Aufgaben kennzeichnen bzw. deren Kennzeichnung aufheben.|
|**Symbole**|Ein gelber Pfeil gibt die aktuelle Aufgabe an. Die aktuelle Aufgabe ist die oberste Aufgabe im aktuellen Thread.<br /><br /> Ein weißer Pfeil gibt die unterbrechende Aufgabe an, d. h., die Aufgabe, die beim Aufrufen des Debuggers aktuell war.<br /><br /> Das Pausensymbol gibt eine Aufgabe an, die vom Benutzer eingefroren wurde. Sie können eine Aufgabe einfrieren und deaktivieren, indem Sie in der Liste mit der rechten Maustaste darauf klicken.|
|**ID**|Eine vom System bereitgestellte Nummer für die Aufgabe. In nativem Code ist diese Nummer die Adresse der Aufgabe.|
|**Status**|Der aktuelle Zustand der Aufgabe (geplant, aktiv, blockiert, Deadlock, wartend oder abgeschlossen). Eine geplante Aufgabe wurde noch nicht ausgeführt und verfügt daher noch über keine Aufrufliste, keinen zugewiesenen Thread oder weitere Informationen.<br /><br /> Eine aktive Aufgabe hat vor dem Unterbrechen im Debugger Code ausgeführt.<br /><br /> Eine wartende oder blockierte Aufgabe ist blockiert, da sie auf das Signalisieren eines Ereignisses, das Aufheben einer Sperre oder das Abschließen einer anderen Aufgabe wartet.<br /><br /> Eine blockierte Aufgabe ist eine wartende Aufgabe, deren Thread an einem anderen Thread blockiert ist.<br /><br /> Zeigen Sie auf die Zelle **Status** für eine Aufgabe mit Deadlock oder eine wartende Aufgabe, um weitere Informationen zur Blockierung anzuzeigen **Warnung:**  Im Fenster **Aufgaben** werden Deadlocks nur für eine blockierte Aufgabe gemeldet, bei der eine Synchronisierungsprimitive verwendet wird, die von Wait Chain Traversal (WCT) unterstützt wird. Für ein <xref:System.Threading.Tasks.Task>-Objekt mit Deadlock, für das WCT verwendet wird, meldet der Debugger **Awaiting-deadlocked**. Für eine Aufgabe mit Deadlock, die von der Concurrency Runtime verwaltet wird, die nicht WCT verwendet, meldet der Debugger **Warten**. Weitere Informationen zu WCT finden Sie unter [Wait Chain Traversal](/windows/desktop/Debug/wait-chain-traversal).|
|**Startzeit**|Die Uhrzeit, zu der die Aufgabe aktiviert wurde.|
|**Dauer**|Die Anzahl von Sekunden, die die Aufgabe aktiv war.|
|**Abschlusszeit**|Die Uhrzeit, zu der die Aufgabe abgeschlossen wurde.|
|**Position**|Die aktuelle Position in der Aufrufliste der Aufgabe. Zeigen Sie auf diese Zelle, um die gesamte Aufrufliste für die Aufgabe anzuzeigen. Für geplante Aufgaben ist in dieser Spalte kein Wert vorhanden.|
|**Aufgabe**|Die ursprüngliche Methode und Argumente, die beim Erstellen an die Aufgabe übergeben wurden.|
|**AsyncState**|Für verwalteten Code ist dies der Aufgabenstatus. Standardmäßig ist diese Spalte ausgeblendet. Um diese Spalte anzuzeigen, öffnen Sie das Kontextmenü für einen der Spaltenheader. Wählen Sie **Spalten**, **AsyncState** aus.|
|**Parent**|Die ID der Aufgabe, von der diese Aufgabe erstellt wurde. Wenn diese Spalte leer ist, verfügt die Aufgabe über kein übergeordnetes Element. Dies gilt nur für verwaltete Programme.|
|**Threadzuweisung**|Die ID und der Name des Threads, in dem die Aufgabe ausgeführt wird.|
|**AppDomain**|Für verwalteten Code die Anwendungsdomäne, in der die Aufgabe ausgeführt wird.|
|**task_group**|Für nativen Code die Adresse des [task_group](/cpp/parallel/concrt/reference/task-group-class)-Objekts, von dem die Aufgabe geplant wurde. Für asynchrone Agents und einfache Aufgaben wird diese Spalte auf 0 festgelegt.|
|**Process**|Die ID des Prozesses, in dem die Aufgabe ausgeführt wird.|

 Sie können der Ansicht Spalten hinzufügen, indem Sie mit der rechten Maustaste auf eine Spaltenüberschrift klicken und die gewünschten Spalten auswählen. (Entfernen Sie Spalten, indem Sie die jeweilige Auswahl aufheben.) Sie können auch die Anordnung der Spalten ändern, indem Sie sie nach links oder rechts ziehen. Das Kontextmenü für Spalten wird in der folgenden Abbildung veranschaulicht.

 ![Ansicht „Kontextmenü“ im Fenster „Aufgaben“](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Sortieren von Aufgaben
 Wenn Sie Aufgaben nach Spaltenkriterien sortieren möchten, klicken Sie auf den Spaltenheader. Wenn Sie z. B. auf die Spaltenüberschrift **ID** klicken, können Sie die Aufgaben nach Aufgaben-ID sortieren: 1,2,3,4,5 usw. Klicken Sie erneut auf den Spaltenheader, um die Sortierreihenfolge umzukehren. Die aktuelle Sortierspalte und die Sortierreihenfolge werden durch einen Pfeil in der Spalte angegeben.

## <a name="grouping-tasks"></a>Gruppieren von Aufgaben
 Sie können Aufgaben nach jeder Spalte in der Listenansicht gruppieren. Wenn Sie beispielsweise mit der rechten Maustaste auf den Spaltenheader **Status** klicken und anschließend auf **Gruppieren nach** > **[*Status*]** klicken, können Sie alle Aufgaben gruppieren, die denselben Status aufweisen. So können Sie beispielsweise schnell wartende Aufgaben anzeigen lassen, damit Sie untersuchen können, aus welchen Gründen diese blockiert sind. Sie können auch Gruppen reduzieren, die während der Debugsitzung nicht von Interesse sind. Auf die gleiche Weise können Sie nach den anderen Spalten gruppieren. Eine Gruppe kann gekennzeichnet bzw. die Kennzeichnung einer Gruppe kann aufgehoben werden, indem Sie auf die Schaltfläche neben dem Gruppenheader klicken. In der folgenden Abbildung wird das Fenster **Aufgaben** im gruppierten Modus dargestellt.

 ![Gruppierter Modus im Fenster „Aufgaben“](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Ansicht über- und untergeordneter Elemente
 (Diese Ansicht ist nur für verwalteten Code verfügbar.) Wenn Sie mit der rechten Maustaste auf die Spaltenüberschrift **Status** klicken und anschließend auf **Gruppieren nach** > **Übergeordnetes Element** klicken, können Sie die Liste der Aufgaben in eine hierarchische Ansicht ändern, in der jede untergeordnete Aufgabe einen Unterknoten darstellt, der unter seinem übergeordneten Element ein- bzw. ausgeblendet werden kann.

## <a name="flagging-tasks"></a>Kennzeichnen von Aufgaben
 Sie können den Thread der Aufgabe kennzeichnen, für den eine Aufgabe ausgeführt wird. Wählen Sie hierzu das Aufgabenlistenelement aus und klicken dann im Kontextmenü auf **Zugewiesenen Thread kennzeichnen**. Sie können aber auch auf das Flagsymbol in der ersten Spalte klicken. Wenn Sie mehrere Aufgaben kennzeichnen, können Sie nach der Flagspalte sortieren, um alle gekennzeichneten Aufgaben an oberster Stelle anzuzeigen, sodass Sie sich auf die betreffenden Aufgaben konzentrieren können. Sie können auch das Fenster **Parallele Stapel** verwenden, um ausschließlich gekennzeichnete Aufgaben anzuzeigen. Damit können Sie Aufgaben herausfiltern, die für das Debugging nicht von Interesse sind. Flags werden nicht zwischen Debugsitzungen beibehalten.

## <a name="freezing-and-thawing-tasks"></a>Einfrieren und Reaktivieren von Aufgaben
 Sie können den Thread einfrieren, in dem eine Aufgabe ausgeführt wird. Klicken Sie dazu mit der rechten Maustaste auf das Aufgabenlistenelement, und klicken Sie anschließend auf **Zugewiesenen Thread einfrieren**. (Wenn eine Aufgabe bereits eingefroren ist, heißt der Befehl **Zugewiesenen Thread entsperren**.) Wenn Sie einen Thread einfrieren, wird dieser Thread nicht ausgeführt, wenn Sie Code nach dem aktuellen Breakpoint schrittweise durchlaufen. Durch den Befehl **Alle Threads mit Ausnahme des vorliegenden einfrieren** werden alle Threads mit Ausnahme des Threads eingefroren, der das Aufgabenlistenelement ausführt.

 In der folgenden Abbildung werden die anderen Menüelemente für die einzelnen Aufgaben angezeigt.

 ![Kontextmenü „Thread“ im Fenster „Aufgaben“](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Wechseln des aktiven Threads oder Frames

Mit dem Befehl **Zu Aufgabe wechseln** wird die aktuelle Aufgabe zur aktiven Aufgabe. Mit dem Befehl **Zu Rahmen wechseln** wird der ausgewählte Stapelrahmen zum aktiven Stapelrahmen. Der Debuggerkontext wechselt zur aktuellen Aufgabe oder zum ausgewählten Stapelrahmen.

## <a name="see-also"></a>Siehe auch

- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Parallele Programmierung](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Verwenden des Fensters "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)
- [Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung](../debugger/walkthrough-debugging-a-parallel-application.md)