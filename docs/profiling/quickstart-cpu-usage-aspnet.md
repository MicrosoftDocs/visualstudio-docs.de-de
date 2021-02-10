---
title: Analysieren der CPU-Auslastungsdaten (ASP.NET Core)
description: Messen der App-Leistung in ASP.NET Core-Apps mithilfe des Diagnosetools für die CPU-Auslastung
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 7170983732ff1350061629e1e8aa4ec88fad3fa1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952836"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Schnellstart: Analysieren der CPU-Auslastungsdaten in Visual Studio (ASP.NET Core)

Visual Studio enthält viele leistungsstarke Features, mit denen Sie Leistungsprobleme in Ihrer Anwendung besser analysieren können. In diesem Thema werden einige der grundlegenden Funktionen erläutert. Außerdem betrachten wir ein Tool, mit dem Leistungsengpässe aufgrund hoher CPU-Auslastung erkannt werden können. Die Diagnosetools werden für die .NET-Entwicklung in Visual Studio, darunter ASP.NET, sowie für die native/C++-Entwicklung unterstützt.

Der Diagnosehub bietet Ihnen viele weitere Optionen zum Ausführen und Verwalten Ihrer Diagnosesitzung. Wenn das hier beschriebene **CPU-Auslastungs-Tool** nicht die benötigten Daten zurückgibt, gibt es andere [Tools zur Profilerstellung](../profiling/profiling-feature-tour.md), mit denen sie andere hilfreiche Informationen erhalten. In vielen Fällen kann der Leistungsengpass Ihrer Anwendung durch etwas anderes als die CPU ausgelöst werden, z.B. durch den Speicher, das Rendern der Benutzeroberfläche oder die Anforderungszeit des Netzwerks. [PerfTips](../profiling/perftips.md), ein weiteres debuggerintegriertes Profilerstellungstool, ermöglicht Ihnen ebenfalls die Schritt-für-Schritt-Ausführung von Code und das Ermitteln, wie viel Zeit bestimmte Funktionen oder Codeblöcke beanspruchen.

Windows 8 und höher ist erforderlich, um die Profilerstellungstools mit dem Debugger auszuführen (Fenster **Diagnosetools**). Unter Windows 7 und höher können Sie das Post-Mortem-Tool [Leistungsprofiler](../profiling/profiling-feature-tour.md) verwenden.

## <a name="create-a-project"></a>Erstellen eines Projekts

1. Öffnen Sie Visual Studio, und erstellen Sie ein Projekt.

   ::: moniker range="vs-2017"
   Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

   Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual C#** , und klicken Sie auf **Web**. Klicken Sie im mittleren Bereich auf **ASP.NET-Web-Anwendung (.NET Core)** . Benennen Sie das Projekt dann mit *MyProfilingApp_MVC*.

   > [!NOTE]
   > Wenn Ihnen die Projektvorlage **ASP.NET-Webanwendung (.NET Core)** nicht angezeigt wird, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung** und anschließend auf **Ändern**.

   Wählen Sie im angezeigten Dialogfeld im mittleren Bereich **MVC** aus, und klicken Sie dann auf **OK**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Wenn das Startfenster nicht geöffnet ist, klicken Sie auf **Datei** > **Startfenster**.

   Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld *ASP.NET* ein. Wählen Sie anschließend in der Liste der Sprachen **C#** und dann aus der Liste der Plattformen **Windows** aus.

   Nachdem Sie die Sprach- und Plattformfilter angewendet haben, wählen Sie die Vorlage **ASP.NET-Webanwendung (.NET Core)** und dann **Weiter** aus.

   > [!NOTE]
   > Wenn Sie die Vorlage **ASP.NET-Webanwendung (.NET Core)** nicht sehen, können Sie sie über das Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus. Wählen Sie anschließend im Visual Studio-Installer die Workload **ASP.NET- und Webentwicklung** aus.

   Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname** *MyProfilingApp_MVC* ein. Wählen Sie anschließend **Erstellen** aus.

   Wählen Sie im Fenster, das angezeigt wird, die Option **Webanwendung (Model-View-Controller)** aus, und klicken Sie dann auf **Erstellen**.

   ::: moniker-end

   Visual Studio öffnet Ihr neues Projekt.

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Ordner „Models“ (Modelle) und anschließend auf **Hinzufügen** > **Klasse**.

1. Nennen Sie die neue Klasse `Data.cs`, und klicken Sie auf **Hinzufügen**.

1. Öffnen Sie im Projektmappen-Explorer `Models/Data.cs`, und fügen Sie am Anfang der Datei die folgende `using`-Anweisung hinzu:

    ```csharp
    using System.Threading;
    ```

1. Ersetzen Sie in „Data.cs“ den folgenden Code:

    ```csharp
    public class Data
    {
    }
    ```

    durch den folgenden:

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. Öffnen Sie im Projektmappen-Explorer *Controller/HomeControllers.cs*, und ersetzen Sie den folgenden Code:

   ::: moniker range="vs-2017"

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    durch den folgenden:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

    ::: moniker-end
    ::: moniker range="vs-2019"

    ```csharp
    public IActionResult Privacy()
    {
        return View();
    }
    ```

    durch den folgenden:

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>Schritt 1: Sammeln von Profilerstellungsdaten

1. Legen Sie in Ihrer App zuerst einen Haltepunkt auf diese Codezeile im `Simple`-Konstruktor fest:

    `for (int i = 0; i < 200; i++)`

    Legen Sie einen Haltepunkt fest, indem Sie in den Bundsteg links neben der Codezeile klicken.

1. Legen Sie als Nächstes einen weiteren Haltepunkt auf die schließende Klammer am Ende des `Simple`-Konstruktors fest:

     ![Haltepunkte für die Profilerstellung festlegen](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    Durch das Festlegen von zwei Haltepunkten können Sie die Datensammlung auf die Teile des Code begrenzen, die Sie analysieren möchten.

1. Das Fenster **Diagnosetools** wird bereits angezeigt, es sei denn, Sie haben es deaktiviert. Klicken Sie auf **Debuggen** > **Windows** > **Diagnosetools anzeigen**, um das Fenster erneut aufzurufen.

1. Klicken Sie auf **Debuggen** > **Debugging starten** (oder auf **Start** auf der Symbolleiste oder auf **F5**).

1. Wenn die Anwendung geladen wurde, klicken Sie oben auf der Webseite auf den entsprechenden Link, um den neuen Code auszuführen.

   ::: moniker range="vs-2017"
   Klicken Sie in Visual Studio 2017 auf den **Info**-Link, um den Code auszuführen.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Klicken Sie in Visual Studio 2019 auf den **Datenschutz**-Link, um den Code auszuführen.
   ::: moniker-end

1. Sehen Sie sich die Ansicht **Zusammenfassung** der Diagnosetools an.

1. Aktivieren Sie, während der Debugger angehalten ist, die Sammlung von CPU-Auslastungsdaten, indem Sie auf **CPU-Profilerstellung aufzeichnen** klicken. Öffnen Sie anschließend die Registerkarte **CPU-Auslastung**.

     ![Diagnosetools ermöglichen die CPU-Profilerstellung](../profiling/media/quickstart-cpu-usage-summary.png)

     Wenn die Datensammlung aktiviert ist, zeigt die Schaltfläche für das Aufzeichnen einen roten Kreis an.

     Wenn Sie auf **CPU-Profilerstellung aufzeichnen** klicken, zeichnet Visual Studio auf, welche Funktionen ausgeführt werden und wie lange dies dauert. Außerdem stellt das Programm ein Zeitachsendiagramm bereit, mit dem Sie bestimmte Segmente der Samplingsitzung genauer betrachten können. Diese gesammelten Daten können jedoch nur angezeigt werden, wenn die Anwendung an einem Haltepunkt angehalten wird.

6. Drücken Sie F5, um die App bis zum zweiten Haltepunkt auszuführen.

     Jetzt verfügen Sie über Leistungsdaten für Ihre Anwendung, die speziell für den Codebereich gelten, der zwischen den beiden Haltepunkten liegt.

     Der Profiler beginnt, Threaddaten vorzubereiten. Warten Sie, bis dieser Vorgang abgeschlossen ist.

     Das CPU-Auslastungstool zeigt den Bericht unter der Registerkarte **CPU-Auslastung** an.

     An diesem Punkt können Sie beginnen, die Daten zu analysieren.

## <a name="step-2-analyze-cpu-usage-data"></a>Schritt 2: Analysieren der CPU-Auslastungsdaten

Beginnen Sie bei der Datenanalyse am besten mit der Liste der Funktionen unter „CPU-Auslastung“, stellen Sie fest welche Funktionen die meisten Aufgaben ausführen, und betrachten Sie die einzelnen Funktionen näher.

1. Untersuchen Sie in der Liste der Funktionen die Funktionen, die am meisten Aufgaben ausführen.

     ![Registerkarte „CPU-Auslastung“ der Diagnosetools](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Die Auflistung der Funktionen beginnt mit der Funktion, die die meisten Aufgaben ausführt (sie sind nicht in der Reihenfolge der Aufrufe gelistet). Dadurch können Sie schnell feststellen, welche Funktionen am längsten ausgeführt werden.

2. Doppelklicken Sie in der Funktionsliste auf die `MyProfilingApp_MVC.Models.ServerClass::GetNumber`-Funktion.

    Dabei wird die Ansicht **Aufrufer/Aufgerufener** im linken Bereich geöffnet.

    ![Ansicht „Aufrufer/Aufgerufener“ der Diagnosetools](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    In dieser Ansicht wird die ausgewählte Funktion in der Überschrift und im Feld **Aktuelle Funktion** angezeigt (in diesem Beispiel `ServerClass::GetNumber`). Die Funktion, die die aktuelle Funktion aufgerufen hat, wird links unter **Calling Function** (Aufrufende Funktion) angezeigt, und alle Funktionen, die von der aktuellen Funktion aufgerufen wurden werden im Feld **Called Functions** (Aufgerufene Funktionen) auf der rechten Seite angezeigt. (Sie können beide Felder auswählen, um die aktuelle Funktion zu ändern.)

    In dieser Ansicht wird Ihnen die Gesamtzeit (ms) und der Prozentsatz der gesamten Ausführungszeit der App angezeigt, den die Funktion bis zum Abschluss eingenommen hat.

    Unter **Funktionsrumpf** wird ebenso die Gesamtzeit (und der Prozentsatz der Zeit) angezeigt, die im Funktionsrumpf aufgewendet wurde. Die Zeit, die in aufrufenden und aufgerufenen Funktionen aufgewendet wurde, ist nicht enthalten. (In dieser Abbildung wurden 2220 von 2235 ms im Funktionsrumpf aufgewendet, und die verbleibende Zeit (<20 ms) wurde im von dieser Funktion aufgerufenen externen Code aufgewendet). Die aktuellen Werte unterscheiden sich je nach Umgebung.

    > [!TIP]
    > Hohe Werte unter **Funktionsrumpf** deuten auf einen Leistungsengpass in der Funktion selbst hin.

## <a name="next-steps"></a>Nächste Schritte

- [Analysieren der Speicherauslastung](../profiling/memory-usage.md), um Leistungsengpässe zu erkennen
- [Analysieren der CPU-Auslastung](../profiling/cpu-usage.md) für weitere Informationen zum CPU-Auslastungs-Tool
- Analysieren der CPU-Auslastung, auch ohne Debugger oder dass eine ausgeführte App als Ziel gesetzt wird: Weitere Informationen finden Sie unter [Sammeln von Profilerstellungsdaten ohne das Debuggen](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) in [Ausführen von Profilerstellungstools mit oder ohne den Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Siehe auch

- [Profilerstellung in Visual Studio](../profiling/index.yml)
- [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)
