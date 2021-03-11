---
title: 'DA0039: Sehr hohes Maß an Sperrkonflikten | Microsoft-Dokumentation'
description: Die zusammen mit den Profilerstellungsdaten erfassten Systemleistungsdaten deuten darauf hin, dass während der Anwendungsausführung ein übermäßig hohes Maß an Sperrkonflikten aufgetreten ist.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 656f9dbc3994ed47e6d7cd8077191b23aa9ead6a
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465921"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039: Sehr hohes Maß an Sperrkonflikten

|Element|Wert|
|-|-|
|Regel-ID|DA0039|
|Kategorie|.NET Framework-Verwendung|
|Profilerstellungsmethoden|Sampling<br /><br /> Instrumentierung<br /><br /> .NET-Arbeitsspeicher|
|Meldung|Ein sehr hohes Maß an .NET-Sperrkonflikten wurde festgestellt. Untersuchen Sie die Ursache für diesen Sperrkonflikt durch Ausführen eines Nebenläufigkeitsprofils.|
|Regeltyp|Warnung|

 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 25 Samplings erfasst werden, damit diese Regel ausgelöst wird.

## <a name="cause"></a>Ursache
 Die zusammen mit den Profilerstellungsdaten erfassten Systemleistungsdaten deuten darauf hin, dass während der Anwendungsausführung ein übermäßig hohes Maß an Sperrkonflikten aufgetreten ist. Wiederholen Sie die Profilerstellung mit der Nebenläufigkeitsmethode, um die Ursache der Konflikte zu ermitteln.

## <a name="rule-description"></a>Regelbeschreibung
 Sperren werden verwendet, um in einer Multithreadanwendung kritische Codeabschnitte zu schützen, die seriell von jeweils einem Thread ausgeführt werden müssen. Von der Microsoft .NET Common Language Runtime (CLR) wird ein vollständiger Satz von Synchronisierungs- und Sperrprimitiven bereitgestellt. Von der Programmiersprache C# wird beispielsweise eine lock-Anweisung (SyncLock in Visual Basic) unterstützt. Von einer verwalteten Anwendung können die Methoden „Monitor.Enter“ und „Monitor.Exit“ im Namespace „System.Threading“ aufgerufen werden, um direkt eine Sperre einzurichten oder freizugeben. Von .NET Framework werden zusätzliche Synchronisierungs- und Sperrprimitive unterstützt – z.B. Klassen, von denen Mutexe, ReaderWriterLocks und Semaphore unterstützt werden. Weitere Informationen finden Sie unter [Overview of Synchronization Primitives (Übersicht über Synchronisierungsprimitive)](/dotnet/standard/threading/overview-of-synchronization-primitives) im .NET Framework Developer Network auf der MSDN-Website. Die .NET Framework-Klassen selbst befinden sich auf Ebenen, die den in das Betriebssystem Windows integrierten Synchronisierungsdiensten niedrigerer Ebenen übergeordnet sind. Dazu gehören Objekte für kritische Abschnitte sowie viele verschiedene Wait- und Ereignissignalisierungsfunktionen. Weitere Informationen finden Sie im Abschnitt [Synchronization (Synchonisierung)](/windows/win32/sync/synchronization) zur Win32- und COM-Entwicklung in der MSDN Library.

 Sowohl den .NET Framework-Klassen als auch den nativen Windows-Objekten, die für die Synchronisierung und für Sperren verwendet werden, liegen freigegebene Speicherbereiche zugrunde, die mithilfe von Interlocked-Vorgängen geändert werden müssen. Von Interlocked-Vorgängen werden hardwarespezifische Anweisungen verwendet, die in freigegebenen Speicherbereichen ausgeführt werden, um deren Zustand mithilfe von unteilbaren Vorgängen zu ändern. Unteilbare Vorgänge sind für alle Prozessoren des Computers garantiert konsistent. Sperren und WaitHandles sind .NET-Objekte, von denen automatisch Interlocked-Vorgänge verwendet werden, wenn sie festgelegt oder zurückgesetzt werden. Unter Umständen sind in der Anwendung auch andere Datenstrukturen mit freigegebenem Speicher vorhanden, für die ebenfalls Interlocked-Vorgänge verwendet werden müssen, um eine threadsichere Aktualisierung zu gewährleisten. Weitere Informationen finden Sie unter [Interlocked-Vorgänge](/dotnet/api/system.threading.interlocked) im Abschnitt „.NET Framework“ der MSDN Library.

 Synchronisierung und Sperrung sind Mechanismen, mit denen sichergestellt wird, dass Multithreadanwendungen ordnungsgemäß ausgeführt werden. Jeder Thread einer Multithreadanwendung ist eine unabhängige Ausführungseinheit, die vom Betriebssystem unabhängig geplant wird. Zu einem Sperrkonflikt kommt es immer dann, wenn für einen Thread, von dem versucht wird, eine Sperre einzurichten, eine Verzögerung auftritt, da die Sperre von einem anderen Thread zurückgehalten wird.

 Sperren sind häufig geschachtelt. Eine Schachtelung tritt auf, wenn von einem Thread, von dem ein kritischer Abschnitt ausgeführt wird, eine Funktion ausgeführt wird, für die eine weitere Sperre erforderlich ist. Ein gewisses Maß an Sperrschachtelungen lässt sich nicht vermeiden. Durch den kritischen Abschnitt wird möglicherweise eine .NET Framework-Methode aufgerufen, deren Threadsicherheit auf Sperren beruht. Der Aufruf einer Framework-Methode, von der mithilfe eines anderen Sperrhandles ebenfalls eine Sperre eingerichtet wird und der aus einem kritischen Abschnitt in der Anwendung erfolgt, hat eine Schachtelung der Sperren zur Folge. Geschachtelte Sperrbedingungen können zu Leistungsproblemen führen, die sich meist nur sehr schwer nachvollziehen und beheben lassen.

 Diese Regel wird ausgelöst, wenn die während der Profilerstellung ermittelten Werte auf ein sehr hohes Maß an Sperrkonflikten hindeuten. Durch Sperrkonflikte verzögert sich die Ausführung von Threads, von denen auf die Sperre gewartet wird. Es empfiehlt sich, selbst eine recht geringe Anzahl von Sperrkonflikten in Komponenten- oder Auslastungstests zu untersuchen, die auf weniger leistungsfähiger Hardware ausgeführt werden.

> [!NOTE]
> Wenn die Rate der gemeldeten Sperrkonflikte in den Daten für die Profilerstellung zwar beträchtlich, aber nicht übermäßig hoch ist, wird anstelle dieser Warnmeldung die Informationsmeldung [DA0038: Hohes Maß an Sperrkonflikten](../profiling/da0038-high-rate-of-lock-contentions.md) angezeigt.

## <a name="how-to-investigate-a-warning"></a>Vorgehensweise zur Überprüfung einer Warnung
 Doppelklicken Sie auf die Meldung, um zur Ansicht [Markierungen](../profiling/marks-view.md) der Profilerstellungsdaten zu navigieren.  Suchen Sie die Spalte **NET CLR-Sperren und Threads\Konfliktrate/s**. Überprüfen Sie, ob Sperrkonflikte in bestimmten Phasen der Programmausführung besonders häufig auftreten.

 Diese Regel wird nur ausgelöst, wenn nicht die Nebenläufigkeitsmethode zur Profilerstellung verwendet wird. Die Nebenläufigkeitsmethode zur Profilerstellung ist das am besten geeignete Tool, um Leistungsprobleme im Zusammenhang mit Sperrkonflikten in der Anwendung zu untersuchen. Sammeln Sie Nebenläufigkeitsprofilerstellungsdaten, um das Sperrverhalten der Anwendung nachvollziehen zu können. Ermitteln Sie hierzu, für welche Sperren eine hohe Anzahl von Konflikten vorliegt, um wie viel sich die Threadausführungszeit durch das Warten auf Sperren mit Konflikten verlängert und welcher Code impliziert wird. In Nebenläufigkeitsprofilen werden Daten zu allen Sperrkonflikten gesammelt. Dies schließt auch das Sperrverhalten von nativen Windows-Funktionen, .NET Framework-Klassen und beliebigen anderen Bibliotheken von Drittanbietern ein, auf die von der Anwendung verwiesen wird. Informationen zur Parallelitätsprofilerstellung mithilfe der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-IDE finden Sie unter [Sammeln von Parallelitätsdaten zu Threads und Prozessen](../profiling/collecting-thread-and-process-concurrency-data.md). Links zu Informationen zur Parallelitätsprofilerstellung über die Befehlszeile finden Sie im Abschnitt **Erfassen von Daten zu Ressourcenkonflikten und Threadaktivitäten mit der Parallelitätsmethode** unter [Verwenden von Profilerstellungsmethoden zum Sammeln von Leistungsdaten über die Befehlszeile](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).
