---
title: Debuggen einer Multithread-App
description: Debuggen mithilfe des Fensters „Threads“ und der Symbolleiste „Debugspeicherort“ in Visual Studio
ms.date: 02/14/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cbde477e076203625e35ebf0109ed344679563f8
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683312"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Exemplarische Vorgehensweise: Debuggen einer Multithread-App mithilfe des Fensters „Threads“ (C#, Visual Basic, C++)

Mehrere Visual Studio-Benutzeroberflächenelemente helfen Ihnen beim Debuggen von Multithread-Apps. In diesem Artikel werden Multithread-Debugfunktionen im Code-Editor-Fenster, auf der Symbolleiste **Debugspeicherort** und im Fenster **Threads** vorgestellt. Weitere Informationen zu anderen Tools zum Debuggen von Multithread-Apps finden Sie unter [Erste Schritte beim Debuggen von Multithread-Apps](../debugger/get-started-debugging-multithreaded-apps.md).

Das Durcharbeiten dieses Tutorials dauert nur einige Minuten und vermittelt Ihnen die Grundlagen des Debuggens von Multithread-Apps.

## <a name="create-a-multithreaded-app-project"></a>Erstellen eines Multithread-App-Projekts

Erstellen Sie das folgende Multithread-App-Projekt für die Verwendung in diesem Tutorial:

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.

   ::: moniker range=">=vs-2019"

   Wenn das Startfenster nicht geöffnet ist, klicken Sie auf **Datei** > **Startfenster**.

   Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld *Konsole* ein. Wählen Sie anschließend in der Liste der Sprachen **C#** oder **C++** und dann in der Liste der Plattformen **Windows** aus. 

   Nachdem Sie die Sprach- und Plattformfilter angewendet haben, wählen Sie **Konsolen-App** für .NET Core oder für C++ und dann **Weiter** aus.

   > [!NOTE]
   > Wenn die richtige Vorlage nicht angezeigt wird, öffnen Sie unter **Tools** > **Tools und Features abrufen...** den Visual Studio-Installer. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** oder **Desktopentwicklung mit C++** aus, und klicken Sie dann auf **Anpassen**.

   Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname** *MyThreadWalkthroughApp* ein. Klicken Sie anschließend je nach verfügbarer Option entweder auf **Weiter** oder auf **Erstellen**.

   Wählen Sie für .NET Core entweder das empfohlene Zielframework (.NET Core 3.1) oder .NET 5 aus, und klicken Sie dann auf **Erstellen**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** eine der folgenden Optionen aus:

   - Wählen Sie für eine C#-App unter **Visual C#** die Option **Windows-Desktop** und dann im mittleren Bereich **Konsolen-App (.NET Framework)** aus.
   - Klicken Sie für eine C++-App unter **Visual C++** auf **Windows-Desktop**, und wählen Sie dann im mittleren Bereich **Windows-Konsolenanwendung** aus.

   Wenn die Projektvorlage **Konsolen-App (.NET Framework)** oder für C++ die Projektvorlage **Konsolen-App** nicht angezeigt wird, navigieren Sie zu **Tools** > **Tools und Features abrufen**, um den Visual Studio-Installer zu öffnen. Wählen Sie die Workload **.NET-Desktopentwicklung** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

   Geben Sie dann einen Namen wie *MyThreadWalkthroughApp* ein, und klicken Sie auf **OK**.

   Klicken Sie auf **OK**.
   ::: moniker-end

   Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt. Abhängig von der ausgewählten Programmiersprache trägt die Quelldatei ggf. den Namen *Program.cs*, *MyThreadWalkthroughApp.cpp* oder *Module1.vb*.

1. Ersetzen Sie den Code in der Quelldatei durch den C#- oder C++-Beispielcode aus [Erste Schritte beim Debuggen von Multithread-Apps](../debugger/get-started-debugging-multithreaded-apps.md).

1. Wählen Sie **Datei** > **Alle speichern** aus.

## <a name="start-debugging"></a>Debugging starten

1. Suchen Sie im Quellcode nach den folgenden Zeilen:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Legen Sie einen Breakpoint in der Zeile `Console.WriteLine();` fest, indem Sie im linken Bundsteg klicken oder die Zeile auswählen und **F9** drücken.

   Der Breakpoint wird als roter Kreis im linken Bundsteg neben der Codezeile angezeigt.

1. Wählen Sie **Debuggen** > **Debuggen starten** aus, oder drücken Sie **F5**.

   Die App wird im Debugmodus gestartet und am Breakpoint angehalten.

1. Öffnen Sie im Unterbrechungsmodus das Fenster **Threads**, indem Sie **Debuggen** > **Windows** > **Threads** auswählen. Sie müssen sich in einer Debugsitzung befinden, um **Threads** und andere Debugfenster öffnen oder anzeigen zu können.

## <a name="examine-thread-markers"></a>Untersuchen von Threadmarkern

1. Suchen Sie im Quellcode nach der Zeile `Console.WriteLine();`.

   1. Klicken Sie mit der rechten Maustaste in das Fenster **Threads**, und wählen Sie im Menü **Threads in Quelle anzeigen** ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") aus.

   Der Bundsteg neben der Quellcodezeile zeigt nun einen *Threadmarkersymbol* ![Threadmarker](../debugger/media/dbg-thread-marker.png "Threadmarker")an. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde. Wenn an der Position mehrere angehaltene Threads vorhanden sind, wird das Symbol für ![mehrere Threads](../debugger/media/dbg-multithreaded-show-threads.png "Mehrere Threads") angezeigt.

1. Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt, in dem der Name und die Thread-ID für den beendeten Thread oder die beendeten Threads angezeigt werden. Die Threadnamen können `<No Name>` lauten.

   >[!TIP]
   >Um namenlose Threads zu identifizieren, können Sie diese im Fenster **Threads** umbenennen. Klicken Sie mit der rechten Maustaste auf den Thread, und wählen Sie **Umbenennen** aus.

1. Klicken Sie mit der rechten Maustaste auf den Threadmarker im Quellcode, um die verfügbaren Optionen im Kontextmenü anzuzeigen.

## <a name="flag-and-unflag-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung

Sie können Threads kennzeichnen, um die Threads nachzuverfolgen, auf die Sie besonders achten möchten.

Kennzeichnen Sie Threads im Quellcode-Editor oder im Fenster **Threads**, oder heben Sie dort die Kennzeichnung auf. Wählen Sie, ob nur gekennzeichnete Threads oder alle Threads in der Symbolleiste **Debugspeicherort** oder im Fenster **Threads** angezeigt werden sollen. Die Auswahl an einer beliebigen Position wirkt sich auf alle Positionen aus.

### <a name="flag-and-unflag-threads-in-source-code"></a>Kennzeichnen von Threads im Quellcode und Aufheben der Kennzeichnung

1. Öffnen Sie die Symbolleiste **Debugspeicherort**, indem Sie **Anzeigen** > **Symbolleisten** > **Debugspeicherort** auswählen. Sie können auch mit der rechten Maustaste im Symbolleistenbereich klicken und dann **Debugspeicherort** auswählen.

1. Die Symbolleiste **Debugspeicherort** weist drei Felder auf: **Prozess**, **Thread** und **Stapelrahmen**. Öffnen Sie die Liste **Thread**, und beachten Sie, wie viele Threads vorhanden sind. In der Liste **Thread** wird der derzeit ausgeführte Thread durch ein **>** -Symbol gekennzeichnet.

1. Zeigen Sie im Quellcodefenster auf ein Threadmarkersymbol im Bundsteg, und wählen Sie das Flagsymbol (oder eines der leeren Flagsymbole) im DataTip aus. Das Flagsymbol wird rot.

   Sie können auch mit der rechten Maustaste auf ein Threadmarkersymbol klicken, auf **Flag** zeigen und dann einen Thread auswählen, der über das Kontextmenü gekennzeichnet werden soll.

1. Wählen Sie auf der Symbolleiste **Debugspeicherort** das **Nur gekennzeichnete Threads anzeigen**-Symbol ![Gekennzeichnete Threads anzeigen](../debugger/media/dbg-threads-show-flagged.png "Gekennzeichnete Threads anzeigen") rechts neben dem Feld **Thread** aus. Das Symbol ist ausgegraut, es sei denn, mindestens ein Thread ist gekennzeichnet.

   Nur der gekennzeichnete Thread wird jetzt in der Dropdownliste **Thread** auf der Symbolleiste angezeigt. Um erneut alle Threads anzuzeigen, aktivieren Sie das Symbol **Nur gekennzeichnete Threads anzeigen** erneut.

   >[!TIP]
   >Nachdem Sie einige Threads gekennzeichnet haben, können Sie den Cursor im Code-Editor platzieren, mit der rechten Maustaste klicken und Gekennzeichnete **Threads bis zum Cursor ausführen** auswählen. Stellen Sie sicher, dass Sie Code auswählen, der von allen gekennzeichneten Threads erreicht wird. **Gekennzeichnete Threads bis zum Cursor ausführen** hält Threads in der ausgewählten Codezeile an, um die Ausführungsreihenfolge durch [Einfrieren und Reaktivieren von Threads](#bkmk_freeze) einfacher zu steuern.

1. Um den gekennzeichneten bzw. nicht gekennzeichneten Status des aktuell ausgeführten Threads umzuschalten, wählen Sie auf der linken Seite der Schaltfläche **Nur gekennzeichnete Threads anzeigen** die Schaltfläche **Flagzustand des aktuellen Threads umschalten** der Symbolleiste für ein einzelnes Flag aus. Das Kennzeichnen des aktuellen Threads ist hilfreich für die Suche nach dem aktuellen Thread, wenn nur gekennzeichnete Threads angezeigt werden.

1. Um die Kennzeichnung für einen Thread zu entfernen, bewegen Sie den Mauszeiger über den Threadmarker im Quellcode, und wählen Sie das rote Flagsymbol aus, um es zu löschen, oder klicken Sie mit der rechten Maustaste auf den Threadmarker und wählen dann **Kennzeichnung aufheben** aus.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Kennzeichnen und Aufheben der Kennzeichnung von Threads im Fenster „Threads“

Im Fenster **Threads** werden neben gekennzeichneten Threads rote Flagsymbole angezeigt, während nicht gekennzeichnete Threads, wenn Sie angezeigt werden, leere Symbole aufweisen.

![Fenster „Threads“](../debugger/media/dbg-threads-window.png "Fenster 'Threads'")

Wählen Sie ein Flagsymbol aus, um den Threadzustand je nach aktuellem Status in gekennzeichnet oder nicht gekennzeichnet zu ändern.

Sie können auch mit der rechten Maustaste auf eine Zeile klicken und **Kennzeichnen**, **Kennzeichnung aufheben** oder **Kennzeichnung aller Threads aufheben** im Kontextmenü auswählen.

Die Symbolleiste des Fensters **Threads** umfasst außerdem eine Schaltfläche **Nur gekennzeichnete Threads anzeigen**, bei der es sich um das rechte der beiden Flagsymbole handelt. Sie funktioniert genauso wie die Schaltfläche auf der Symbolleiste **Debugspeicherort**, und beide Schaltflächen steuern die Anzeige an beiden Speicherorten.

### <a name="other-threads-window-features"></a>Features des Fensters „Andere Threads“

Wählen Sie im Fenster **Threads** die Kopfzeile einer beliebigen Spalte aus, um die Threads nach dieser Spalte zu sortieren. Klicken Sie erneut, um die Sortierreihenfolge umzukehren. Wenn alle Threads angezeigt werden, werden die Threads durch Auswählen der Flagsymbolspalte nach dem Status „Gekennzeichnet“ oder „Nicht gekennzeichnet“ sortiert.

Die zweite Spalte des Fensters **Threads** (ohne Kopfzeile) ist die Spalte **Aktueller Thread**. Ein gelber Pfeil in dieser Spalte markiert den aktuellen Ausführungspunkt.

Die Spalte **Position** zeigt an, wo die einzelnen Threads im Quellcode vorkommen. Wählen Sie den Erweiterungspfeil neben dem Eintrag **Position** aus, oder zeigen Sie auf den Eintrag, um eine partielle Aufrufliste für diesen Thread anzuzeigen.

>[!TIP]
>Um eine grafische Ansicht der Aufruflisten für Threads zu erhalten, verwenden Sie das Fenster [Parallele Stapel](../debugger/using-the-parallel-stacks-window.md). Wählen Sie zum Öffnen des Fensters während des Debuggens **Debuggen**> **Windows** > **Parallele Stapel** aus.

Neben **Kennzeichnen**, **Kennzeichnung aufheben** und **Kennzeichnung aller Threads aufheben** enthält das Kontextmenü für **Thread**-Elemente Folgendes:

- Die Schaltfläche **Threads in Quelle anzeigen**.
- **Hexadezimale Anzeige**: Ändert die **Thread-ID** s im Fenster **Threads** aus einem dezimalen in ein hexadezimales Format.
- [Zu Thread wechseln](#switch-to-another-thread): Schaltet die Ausführung sofort auf diesen Thread um.
- **Umbenennen**: Ändert den Threadnamen.
- Die Befehle [Einfrieren und Reaktivieren](#bkmk_freeze).

## <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Einfrieren und Reaktivieren der Threadausführung

Sie können Threads einfrieren und reaktivieren oder anhalten und fortsetzen, um die Reihenfolge zu steuern, in der die Threads Aufgaben ausführen. Das Einfrieren und Reaktivieren von Threads kann Ihnen helfen, Parallelitätsprobleme zu beheben, z. B. Deadlocks und Racebedingungen.

> [!TIP]
> Wenn Sie einem einzelnen Thread folgen möchten, ohne andere Threads einzufrieren (dabei handelt es sich ebenfalls um ein häufiges Debugszenario), finden Sie weitere Informationen unter [Erste Schritte beim Debuggen von Multithread-Anwendungen](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**So fixieren Sie Threads und heben die Fixierung auf:**

1. Klicken Sie im Fenster **Threads** mit der rechten Maustaste auf einen beliebigen Thread, und klicken Sie dann auf **Einfrieren**. Ein Symbol **Anhalten** in der Spalte **Aktueller Thread** zeigt an, dass der Thread eingefroren ist.

1. Wählen Sie **Spalten** in der Symbolleiste des Fensters **Threads** aus, und wählen Sie dann **Angehaltene Anzahl** aus, um die Spalte **Angehaltene Anzahl** anzuzeigen. Der Wert für „Angehaltene Anzahl“ für den eingefrorenen Thread ist **1**.

1. Klicken Sie mit der rechten Maustaste auf den eingefrorenen Thread, und klicken Sie dann auf **Reaktivieren**.

   Das Symbol **Anhalten** wird nicht mehr angezeigt, und der Wert von **Angehaltene Anzahl** ändert sich in **0**.

## <a name="switch-to-another-thread"></a>Wechseln zu einem anderen Thread

Wenn Sie versuchen, zu einem anderen Thread zu wechseln, wird möglicherweise ein Fenster **Die Anwendung befindet sich im Unterbrechungsmodus** angezeigt. Dieses Fenster informiert sie, dass der Thread keinen Code aufweist, den der aktuelle Debugger anzeigen kann. Beispielsweise debuggen Sie verwalteten Code, aber der Thread ist nativer Code. Das Fenster enthält Vorschläge zur Behebung des Problems.

**So wechseln Sie zu einem anderen Thread:**

1. Notieren Sie sich im Fenster **Threads** die aktuelle Thread-ID, bei der es sich um den Thread mit einem gelben Pfeil in der Spalte **Aktueller Thread** handelt. Sie möchten zurück zu diesem Thread wechseln, um Ihre App fortzusetzen.

1. Klicken Sie mit der rechten Maustaste auf einen anderen Thread, und wählen Sie aus dem Kontextmenü **Zu Thread wechseln** aus.

1. Beachten Sie, dass sich die Position des gelben Pfeils im Fenster **Threads** geändert hat. Der ursprüngliche aktuelle Threadmarker bleibt ebenfalls (als Kontur) erhalten.

   Sehen Sie sich die QuickInfo für den Threadmarker im Quellcode-Editor an, und klicken Sie in der Dropdownliste **Thread** auf die Symbolleiste **Debugspeicherort**. Beachten Sie, dass sich der aktuelle Thread auch dort geändert hat.

1. Wählen Sie auf der Symbolleiste **Debugspeicherort** einen anderen Thread aus der Liste **Thread** aus. Beachten Sie, dass sich der aktuelle Thread auch an den anderen beiden Positionen ändert.

1. Klicken Sie im Quellcode-Editor mit der rechten Maustaste auf einen Threadmarker, zeigen Sie auf **Zu Thread wechseln**, und wählen Sie einen anderen Thread aus der Liste aus. Beobachten Sie, dass sich der aktuelle Thread an allen drei Positionen ändert.

Mit dem Threadmarker im Quellcode können Sie nur zu Threads wechseln, die an der jeweiligen Position angehalten wurden. Über das **Threadfenster** und die Symbolleiste **Debugspeicherort** können Sie zu jedem beliebigen Thread wechseln.

Sie haben nun die Grundlagen des Debuggens von Multithread-Apps kennengelernt. Sie können Threads mithilfe des Fensters **Threads**, der Liste **Thread** auf der Symbolleiste **Debugspeicherort** oder mit Threadmarkern im Quellcode-Editor beobachten, kennzeichnen bzw. ihre Kennzeichnung aufheben und einfrieren bzw. reaktivieren.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [How to: Switch to another thread while debugging (Vorgehensweise: Wechseln zu einem anderen Thread während des Debuggens)](../debugger/how-to-switch-to-another-thread-while-debugging.md)
