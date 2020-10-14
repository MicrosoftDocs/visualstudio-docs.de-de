---
title: Weitere Informationen zum Debuggen von Multithreadanwendungen
description: Debuggen mit den Fenstern „Parallele Stapel“ und „Parallele Überwachung“ in Visual Studio
ms.custom: ''
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30fd29357ab8b42ea6a8baa6412f9ccf7eafed28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350510"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Erste Schritte zum Debuggen von Multithreadanwendungen (C#, Visual Basic, C++)

Visual Studio bietet verschiedene Tools und Benutzeroberflächenelemente, die Sie beim Debuggen von Multithreadanwendungen unterstützen. In diesem Tutorial wird gezeigt, wie Threadmarker, das Fenster **Parallele Stapel**, das Fenster **Parallele Überwachung**, bedingte Haltepunkte und Filterhaltepunkte verwendet werden. Nach Abschluss dieses Tutorials sind Sie mit den Visual Studio-Funktionen zum Debuggen von Multithreadanwendungen vertraut.

Diese beiden Themen enthalten zusätzliche Informationen zur Verwendung anderer Multithread-Debuggingtools:

- Weitere Informationen zur Verwendung der Symbolleiste **Debugspeicherort** und des Fensters **Threads** finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Multithread-App](../debugger/how-to-use-the-threads-window.md).

- Ein Beispiel für die Verwendung von <xref:System.Threading.Tasks.Task> (verwalteter Code) und der Parallelitätslaufzeit (C++) finden Sie unter [Walkthrough: Debug a parallel application (Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung)](../debugger/walkthrough-debugging-a-parallel-application.md). Allgemeine Tipps zum Debuggen, die für die meisten Typen von Multithreadanwendungen gelten, finden Sie in diesem und auch in dem anderen Thema.

Zuerst benötigen Sie ein Projekt für eine Multithreadanwendung. Im Folgenden wird ein Beispiel aufgeführt.

## <a name="create-a-multithreaded-app-project"></a>Erstellen eines Multithreadanwendungs-Projekts

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.

   ::: moniker range=">=vs-2019"

   Wenn das Startfenster nicht geöffnet ist, klicken Sie auf **Datei** > **Startfenster**.

   Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld *Konsole* ein. Wählen Sie anschließend in der Liste mit den Sprachen die Option **C#** , **C++** oder **Visual Basic** und dann in der Liste mit den Plattformen **Windows** aus. 

   Nachdem Sie die Sprach- und Plattformfilter angewendet haben, wählen Sie die Vorlage **Konsolen-App (.NET Core)** oder für C++ **Konsolen-App** aus, und klicken Sie dann auf **Weiter**.

   > [!NOTE]
   > Wenn die richtige Vorlage nicht angezeigt wird, öffnen Sie unter **Tools** > **Tools und Features abrufen...** den Visual Studio-Installer. Wählen Sie die Workload **.NET-Desktopentwicklung** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

   Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname** *MyThreadWalkthroughApp* ein. Wählen Sie anschließend **Erstellen** aus.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** eine der folgenden Optionen aus:

   - Wählen Sie für eine C#-App unter **Visual C#** die Option **Windows-Desktop** und dann im mittleren Bereich **Konsolen-App (.NET Framework)** aus.
   - Wählen Sie für eine Visual Basic-App unter **Visual Basic** die Option **Windows-Desktop** und dann im mittleren Bereich **Konsolen-App (.NET Framework)** aus.
   - Klicken Sie für eine C++-App unter **Visual C++** auf **Windows-Desktop**, und wählen Sie dann im mittleren Bereich **Windows-Konsolenanwendung** aus.

   Wenn die Projektvorlage **Konsolen-App (.NET Core)** oder für C++ **Konsolen-App (.NET Framework)** nicht angezeigt wird, navigieren Sie zu **Tools** > **Tools und Features abrufen...** , um den Visual Studio-Installer zu öffnen. Wählen Sie die Workload **.NET-Desktopentwicklung** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

   Geben Sie dann einen Namen wie *MyThreadWalkthroughApp* ein, und klicken Sie auf **OK**.

   Klicken Sie auf **OK**.
   ::: moniker-end

   Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt. Abhängig von der ausgewählten Programmiersprache trägt die Quelldatei ggf. den Namen *Program.cs*, *MyThreadWalkthroughApp.cpp* oder *Module1.vb*.

1. Löschen Sie den Code, der in der Quelldatei angezeigt wird, und ersetzen Sie ihn durch das unten aufgeführte Codelistingbeispiel.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended. " + data);
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended. " + data)
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. Wählen Sie im Menü **Datei** den Befehl **Alle speichern** aus.

1. (Nur Visual Basic) Klicken Sie in Projektmappen-Explorer (rechter Bereich) mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus. Ändern Sie auf der Registerkarte **Anwendung** das **Startobjekt** in **Simple**.

## <a name="debug-the-multithreaded-app"></a>Debuggen einer Multithreadanwendung

1. Suchen Sie im Quellcode-Editor nach einem der folgenden Codeausschnitte:

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Klicken Sie mit der linken Maustaste auf den linken Bundsteg der Anweisung `Thread.Sleep` oder `std::this_thread::sleep_for`, um einen neuen Haltepunkt einzufügen.

    In diesem Bundsteg wird durch einen roten Kreis angezeigt, dass an dieser Stelle jetzt ein Haltepunkt festgelegt ist.

2. Klicken Sie im Menü **Debuggen** auf **Debuggen starten** (**F5**).

    Visual Studio erstellt die Projektmappe, die Anwendung wird mit dem angefügten Debugger ausgeführt, und die Anwendung wird am Haltepunkt angehalten.

3. Suchen Sie im Quellcode-Editor die Zeile, die den Haltepunkt enthält.

### <a name="discover-the-thread-marker"></a><a name="ShowThreadsInSource"></a>Ermitteln des Threadmarkers  

1. Wählen Sie beim Debuggen auf der Symbolleiste die Schaltfläche **Threads in Quelle anzeigen** aus ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Drücken Sie **F11**, um den Debugger eine Codezeile weiter laufen zu lassen.

3. Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile sehen Sie ein *Threadmarker*-Symbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker"), das zwei verdrillten Fäden ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Ein Threadmarker wird eventuell teilweise durch einen Haltepunkt verdeckt.

4. Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Anhand eines angezeigten DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads. In diesem Fall ist der Name wahrscheinlich `<noname>`.

5. Wählen Sie den Threadmarker aus, um die verfügbaren Optionen im Kontextmenü anzuzeigen.

### <a name="view-the-thread-locations"></a><a name="ParallelStacks"></a>Anzeigen der Threadpositionen

Im Fenster **Parallele Stapel** können Sie zwischen einer Threadsansicht und (für die taskbasierte Programmierung) der Tasksansicht wechseln, und Sie können Aufrufstapelinformationen für jeden Thread anzeigen. In dieser App können wir die Threadansicht verwenden.

1. Öffnen Sie das Fenster **Parallele Stapel**, indem Sie **Debuggen** > **Fenster** > **Parallele Stapel** wählen. Die Anzeige sollte dem Folgenden ähneln: Die genauen Informationen hängen von der aktuellen Position jedes Threads, Ihrer Hardware und Ihrer Programmiersprache ab.

    ![Fenster „Parallele Stapel“](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    In diesem Beispiel sind diese Informationen für verwalteten Code von links nach rechts dargestellt:

    - Der Hauptthread (linke Seite) hat bei `Thread.Start` angehalten, wobei der Endpunkt durch das Threadmarkersymbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker") angezeigt wird.
    - Zwei Threads haben `ServerClass.InstanceMethod` eingegeben, von denen einer der aktuelle Thread (gelber Pfeil) ist, während der andere Thread in `Thread.Sleep` angehalten wurde.
    - Ein neuer Thread (auf der rechten Seite) wird ebenfalls gestartet, aber bei `ThreadHelper.ThreadStart` angehalten.

2. Klicken Sie mit der rechten Maustaste auf Einträge im Fenster **Parallele Stapel**, um die verfügbaren Optionen im Kontextmenü anzuzeigen.

    Sie können über diese Kontextmenüs verschiedene Aktionen ausführen, aber für dieses Tutorial werden weitere dieser Details im Fenster **Parallelüberwachung** (nächste Abschnitte) gezeigt.

    > [!NOTE]
    > Wenn Sie eine Listenansicht mit Informationen zu jedem Thread anzeigen möchten, verwenden Sie stattdessen das Fenster **Threads**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Multithread-App](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Festlegen eines Überwachungselements für eine Variable

1. Öffnen Sie das Fenster **Parallele Überwachung**, indem Sie **Debuggen** > **Fenster** > **Parallele Überwachung** > **Parallele Überwachung 1** auswählen.

2. Wählen Sie die Zelle aus, in der Sie den `<Add Watch>`-Text (oder die leere Kopfzelle in der 4. Spalte) sehen, und geben Sie `data` ein.

    Die Werte für die Datenvariable für jeden Thread werden im Fenster angezeigt.

3. Wählen Sie die Zelle aus, in der Sie den `<Add Watch>`-Text (oder die leere Kopfzelle in der 5. Spalte) sehen, und geben Sie `count` ein.

    Die Werte für die Variable `count` für jeden Thread werden im Fenster angezeigt. Wenn noch nicht so viele Informationen angezeigt werden, drücken Sie mehrmals **F11**, um die Ausführung der Threads im Debugger zu beschleunigen.

    ![Fenster „Parallele Überwachung“](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Klicken Sie mit der rechten Maustaste auf eine der Zeilen im Fenster, um die verfügbaren Optionen anzuzeigen.

### <a name="flag-and-unflag-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung
Sie können Threads markieren, um wichtige Threads zu verfolgen und die anderen Threads zu ignorieren.

1. Halten Sie im Fenster **Parallele Überwachung** die **UMSCHALTTASTE** gedrückt, und wählen Sie mehrere Zeilen aus.

2. Klicken Sie mit der rechten Maustaste, und wählen Sie **Kennzeichnen** aus.

    Alle ausgewählten Threads werden gekennzeichnet. Nun können Sie nach gekennzeichneten Threads filtern.

3. Wählen Sie im Fenster **Parallele Überwachung** die Schaltfläche **Nur gekennzeichnete Threads anzeigen** aus ![Nur gekennzeichnete Threads anzeigen](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Anschließend wird nur der gekennzeichnete Thread in der Liste angezeigt.

    > [!TIP]
    > Nachdem Sie einige Threads gekennzeichnet haben, können Sie im Code-Editor mit der rechten Maustaste auf eine Codezeile klicken und **Threads bis zum Cursor ausführen** auswählen. Stellen Sie sicher, dass Sie Code auswählen, der von allen gekennzeichneten Threads erreicht wird. Visual Studio hält Threads in der ausgewählten Codezeile an, um die Ausführungsreihenfolge durch [Einfrieren und Reaktivieren von Threads](#bkmk_freeze) einfacher zu steuern.

4. Klicken Sie erneut auf die Schaltfläche **Nur gekennzeichnete Threads anzeigen**, um zurück zum Modus **Alle Threads anzeigen** zu wechseln.

5. Um die Kennzeichnung von Threads aufzuheben, klicken Sie mit der rechten Maustaste auf einen oder mehrere markierte Threads im Fenster **Parallele Überwachung** und wählen Sie **Kennzeichnung aufheben**.

### <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Einfrieren und Reaktivieren der Threadausführung

> [!TIP]
> Sie können Threads einfrieren und reaktivieren (anhalten und fortsetzen), um die Reihenfolge zu steuern, in der die Threads Aufgaben ausführen. Dies kann Ihnen helfen, Parallelitätsprobleme zu beheben, z. B. Deadlocks und Racebedingungen.

1. Klicken Sie im Fenster **Parallele Überwachung**, während alle Zeilen ausgewählt sind, mit der rechten Maustaste, und wählen Sie **Einfrieren** aus.

    In der zweiten Spalte wird für jede Zeile ein Pausensymbol angezeigt. Das Pausensymbol gibt an, dass der Thread eingefroren ist.

2. Deaktivieren Sie alle anderen Zeilen, indem Sie nur eine Zeile auswählen.

3. Klicken Sie mit der rechten Maustaste auf eine Zeile, und wählen Sie **Reaktivieren** aus.

    Das Pausensymbol wird in dieser Zeile entfernt, was bedeutet, dass der Thread nicht mehr eingefroren ist.

4. Wechseln Sie zum Code-Editor, und drücken Sie **F11**. Es wird nur der nicht eingefrorene Thread ausgeführt.

    Die App kann auch einige neue Threads instanziieren. Alle neuen Threads sind nicht gekennzeichnet und nicht eingefroren.

### <a name="follow-a-single-thread-with-conditional-breakpoints"></a><a name="bkmk_follow_a_thread"></a> Folgen eines einzelnen Threads mit bedingten Haltepunkten

Es kann hilfreich sein, der Ausführung eines einzelnen Threads im Debugger zu folgen. Eine Methode, um dies zu erreichen, ist das Einfrieren von Threads, an denen Sie nicht interessiert sind. In einigen Szenarios müssen Sie möglicherweise einem einzelnen Thread folgen, ohne andere Threads einzufrieren, z. B. um einen bestimmten Fehler zu reproduzieren. Wenn Sie einem Thread folgen möchten, ohne andere Threads einzufrieren, müssen Sie das Unterbrechen von Code vermeiden, außer in dem Thread, an dem Sie interessiert sind. Dies können Sie erreichen, indem Sie einen [bedingten Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) festlegen.

Sie können Haltepunkte für verschiedene Bedingungen festlegen, z. B. den Threadnamen oder die Thread-ID. Es kann hilfreich sein, die Bedingung für Daten festzulegen, von denen Sie wissen, dass sie für jeden Thread einzigartig sind. Dies ist ein gängiges Debugszenario, bei dem Sie mehr an einem bestimmten Datenwert als an einem bestimmten Thread interessiert sind.

1. Klicken Sie mit der rechten Maustaste auf den zuvor erstellten Haltepunkt und dann auf **Bedingungen**.

2. Geben Sie im Fenster **Haltepunkteinstellungen** für den bedingten Ausdruck `data == 5` ein.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Wenn Sie mehr an einem bestimmten Thread interessiert sind, dann verwenden Sie einen Threadnamen oder eine Thread-ID für die Bedingung. Wählen Sie dazu im Fenster **Haltepunkteinstellungen** die Option **Filter** anstelle von **Bedingter Ausdruck** aus, und folgen Sie den Filtertipps. Sie sollten Ihre Threads im Anwendungscode benennen, da sich die Thread-IDs ändern, wenn Sie den Debugger neu starten.

3. Schließen Sie das Fenster **Haltepunkteinstellungen**.

4. Wählen Sie die Schaltfläche ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp"), um Ihre Debugsitzung neu zu starten.

    Sie unterbrechen den Code im Thread, bei dem der Wert der Datenvariablen 5 ist. Suchen Sie im Fenster **Parallele Überwachung** nach dem gelben Pfeil, der den aktuellen Debuggerkontext anzeigt.

5. Nun können Sie Code überspringen (**F10**), Code schrittweise ausführen (**F11**) und der Ausführung des einzelnen Threads folgen.

    Solange die Haltepunktbedingung für den Thread eindeutig ist und der Debugger auf keine anderen Haltepunkte in anderen Threads trifft (ggf. müssen Sie diese deaktivieren), können Sie Code überspringen und Code schrittweise ausführen, ohne zu anderen Threads zu wechseln.

    > [!NOTE]
    > Wenn Sie den Debugger fortsetzen, werden alle Threads ausgeführt. Der Debugger unterbricht jedoch keinen Code in anderen Threads, es sei denn, einer der anderen Threads erreicht einen Haltepunkt.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [How to: Switch to another thread while debugging (Vorgehensweise: Wechseln zu einem anderen Thread während des Debuggens)](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [How to: Verwenden des Fensters „Parallele Stapel“](../debugger/using-the-parallel-stacks-window.md)
- [How to: Verwenden des Fensters „Parallele Überwachung“](../debugger/how-to-use-the-parallel-watch-window.md)