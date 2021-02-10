---
title: Messen der CPU-Auslastung in Ihren Apps
description: Analysieren von Problemen mit der CPU-Leistung in Ihrer Anwendung mit dem im Debugger integrierten Diagnosetool.
ms.custom: seodec18
ms.date: 04/03/2019
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a18302067749e3b4fc70b08519056dc391d3dca4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936885"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>Messen der Anwendungsleistung durch Analyse der CPU-Nutzung

Suchen Sie Leistungsprobleme beim Debuggen mit dem in den Debugger integrierten Diagnosetool für die **CPU-Auslastung**.  Sie können die CPU-Auslastung auch ohne einen angefügten Debugger analysieren oder indem Sie eine ausgeführte App als Ziel festlegen. Weitere Informationen finden Sie unter [Ausführen von Profilerstellungstools mit oder ohne Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Wenn der Debugger angehalten wird, sammelt das **CPU-Auslastung**-Tool im Diagnosetools-Fenster Informationen zu den in der Anwendung ausgeführten Funktionen. Das Tool listet auch die Funktionen auf, die Aufgaben ausgeführt haben. Außerdem wird ein Zeitachsendiagramm zur Verfügung gestellt, das Sie verwenden können, um sich auf bestimmte Segmente der Samplingsitzung zu konzentrieren.

> [!Important]
> Die in den Debugger integrierten Diagnosetools werden für die .NET-Entwicklung in Visual Studio, darunter ASP.NET, ASP.NET Core und native/C++-Entwicklung unterstützt. Windows 8 und höher ist erforderlich, um die Profilerstellungstools mit dem Debugger auszuführen (Fenster **Diagnosetools**).

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Erfassen von CPU-Auslastungsdaten
> * Analysieren der CPU-Auslastungsdaten

Wenn Sie von der **CPU-Auslastung** nicht die benötigten Daten erhalten, stehen andere [Leistungs-Profiler](../profiling/profiling-feature-tour.md#post_mortem) zur Verfügung, um andere Arten von hilfreichen Informationen zu erhalten. In vielen Fällen kann der Leistungsengpass Ihrer Anwendung durch etwas anderes als die CPU ausgelöst werden, z.B. durch den Speicher, das Rendern der Benutzeroberfläche oder die Anforderungszeit des Netzwerks.

## <a name="step-1-collect-profiling-data"></a>Schritt 1: Sammeln von Profilerstellungsdaten

1. Öffnen Sie das Projekt, das Sie in Visual Studio debuggen möchten, und legen Sie in Ihrer App einen Haltepunkt an dem Punkt fest, an dem Sie die CPU-Auslastung untersuchen möchten.

2. Legen Sie einen zweiten Haltepunkt am Ende der Funktion oder des Codebereichs an, den Sie analysieren möchten.

    Durch das Festlegen von zwei Haltepunkten können Sie die Datensammlung auf die Teile des Code begrenzen, die Sie analysieren möchten.

3. Das Fenster **Diagnosetools** wird automatisch angezeigt, es sei denn, Sie haben es deaktiviert. Klicken Sie auf **Debuggen** > **Windows** > **Diagnosetools anzeigen**, um das Fenster erneut aufzurufen.

4. Mithilfe der Einstellung **Auswahltools** auf der Symbolleiste können Sie auswählen, ob Sie die **CPU-Auslastung**, [Speicherauslastung](../profiling/Memory-Usage.md) oder beides anzeigen möchten. Wenn Sie Visual Studio Enterprise ausführen, können Sie IntelliTrace unter **Extras** > **Optionen** > **IntelliTrace** aktivieren oder deaktivieren.

     ![Fenster „Diagnosetools“](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     Wir werden hauptsächlich die CPU-Auslastung betrachten, stellen Sie also sicher, dass **CPU-Auslastung** aktiviert ist (ist standardmäßig aktiviert).

5. Klicken Sie auf **Debuggen** > **Debugging starten** (oder auf **Start** auf der Symbolleiste oder auf **F5**).

     Wenn das Laden der Anwendung abgeschlossen ist, wird die Zusammenfassungsansicht der Diagnosetools angezeigt. Wenn Sie das Fenster öffnen müssen, klicken Sie auf **Debuggen** > **Windows** > **Diagnosetools anzeigen**.

     ![Registerkarte „Zusammenfassung“ der Diagnosetools](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Weitere Informationen zu den Ereignissen finden Sie unter [Searching and filtering the Events tab of the Diagnostic Tools window (Suchen und Filtern auf der Registerkarte „Ereignisse“ im Fenster „Diagnosetools“)](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

6. Führen Sie das Szenario aus, bei dem Ihr erster Haltepunkt erreicht wird.

7. Aktivieren Sie während der Debugger angehalten wird die Sammlung von CPU-Auslastungsdaten, und öffnen Sie anschließend die Registerkarte **CPU-Auslastung**.

     ![Diagnosetools ermöglichen die CPU-Profilerstellung](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     Wenn Sie **CPU-Profilerstellung aufzeichnen** auswählen, zeichnet Visual Studio die Funktionen auf und wie lange die Ausführung dauert. Sie können diese gesammelten Daten nur anzeigen lassen, wenn Ihre Anwendung an einem Haltepunkt angehalten wird.

8. Drücken Sie F5, um die App bis zum zweiten Haltepunkt auszuführen.

     Jetzt verfügen Sie über Leistungsdaten für Ihre Anwendung, die speziell für den Codebereich gelten, der zwischen den beiden Haltepunkten liegt.

     Der Profiler beginnt, Threaddaten vorzubereiten. Warten Sie, bis dieser Vorgang abgeschlossen ist.

     ![Vorbereitung der Threads durch die Diagnosetools](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     Das CPU-Auslastungstool zeigt den Bericht unter der Registerkarte **CPU-Auslastung** an.

     ![Registerkarte „CPU-Auslastung“ der Diagnosetools](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. Wenn Sie einen spezifischeren Codebereich zur Analyse auswählen möchten, wählen Sie einen Bereich in der CPU-Zeitachse aus (es muss ein Bereich sein, der Profilerstellungsdaten anzeigt).

     ![Auswählen eines Zeitraums in den Diagnosetools](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     An diesem Punkt können Sie beginnen, die Daten zu analysieren.

     > [!TIP]
     >  Wenn Sie versuchen, Leistungsprobleme zu identifizieren, sollten Sie mehrere Messungen erfassen. Die Leistung variiert natürlich von Ausführung zu Ausführung, und Codepfade werden aufgrund der einmaligen Initialisierungslast bei der ersten Ausführung langsam ausgeführt, z. B. aufgrund des Ladens von DLL-Dateien, der Just-In-Time-Kompilierung von Methoden und der Initialisierung der Caches. Indem Sie mehrere Messungen erfassen, erhalten Sie einen besseren Überblick über die Spanne und den Durchschnitt der angezeigten Metriken, wodurch Sie die erste Ausführung mit der gleichmäßigen Leistung eines Codebereichs vergleichen können.

## <a name="step-2-analyze-cpu-usage-data"></a>Schritt 2: Analysieren der CPU-Auslastungsdaten

Beginnen Sie bei der Datenanalyse am besten mit der Liste der Funktionen unter „CPU-Auslastung“, stellen Sie fest welche Funktionen die meisten Aufgaben ausführen, und betrachten Sie die einzelnen Funktionen näher.

1. Untersuchen Sie in der Liste der Funktionen die Funktionen, die am meisten Aufgaben ausführen.

    ![Liste der Funktionen für die CPU-Auslastung in den Diagnosetools](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Die Auflistung der Funktionen beginnt mit der Funktion, die die meisten Aufgaben ausführt (sie sind nicht in der Reihenfolge der Aufrufe gelistet). Dadurch können Sie schnell feststellen, welche Funktionen am längsten ausgeführt werden.

2. Doppelklicken Sie in der Liste der Funktionen auf eine der Funktionen Ihrer App, die viele Aufgaben ausführt.

    Wenn Sie auf eine Funktion doppelklicken, öffnet sich die Ansicht **Aufrufer/Aufgerufener** im linken Bereich.

    ![Ansicht „Aufrufer/Aufgerufener“ der Diagnosetools](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    In dieser Ansicht erscheint die ausgewählte Funktion in der Überschrift und im Feld **Aktuelle Funktion** ( in diesem Beispiel „GetNumber“). Die Funktion, die die aktuelle Funktion aufgerufen hat, wird links unter **Aufrufende Funktion** angezeigt, und alle Funktionen, die von der aktuellen Funktion aufgerufen wurden werden im Feld **Aufgerufene Funktionen** auf der rechten Seite angezeigt. (Sie können beide Felder auswählen, um die aktuelle Funktion zu ändern.)

    In dieser Ansicht wird Ihnen die Gesamtzeit (ms) und der Prozentsatz der gesamten Ausführungszeit der App angezeigt, den die Funktion bis zum Abschluss eingenommen hat.
    Unter **Funktionsrumpf** wird ebenso die Gesamtzeit (und der Prozentsatz der Zeit) angezeigt, die im Funktionsrumpf aufgewendet wurde. Die Zeit, die in aufrufenden und aufgerufenen Funktionen aufgewendet wurde, ist nicht enthalten. (In diesem Beispiel wurden 2367 von 2389 ms im Funktionsrumpf aufgewendet, und die verbleibenden 22 ms wurden im von dieser Funktion aufgerufenen externen Code aufgewendet).

    > [!TIP]
    > Hohe Werte unter **Funktionsrumpf** deuten auf einen Leistungsengpass in der Funktion selbst hin.

3. Eine allgemeinere Übersicht, die die Reihenfolge, in der die Funktionen aufgerufen werden, darstellt, wählen Sie aus der Dropdownliste am oberen Rand des Bereichs **Aufrufstruktur** aus.

    Jeder nummerierte Bereich in der Abbildung bezieht sich auf einen Schritt in der Prozedur.

    ::: moniker range=">=vs-2019"
    ![Aufrufstruktur in den Diagnosetools](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Aufrufstruktur in den Diagnosetools](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |Bild|Beschreibung|
    |-|-|
    |![Schritt 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Der oberste Knoten in CPU-Auslastungsaufrufstrukturen ist ein Pseudoknoten.|
    |![Schritt 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Wenn die Option [Externen Code anzeigen](#view-external-code) deaktiviert ist, ist in den meisten Apps der Knoten der zweiten Ebene ein **[External Code]** -Knoten, der den System- und Frameworkcode enthält, der die App startet und beendet, die Benutzeroberfläche zeichnet, die Threadplanung steuert und andere Dienste der unteren Ebene für die App bereitstellt.|
    |![Schritt 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Die untergeordneten Elemente des Knotens der zweiten Ebene sind die Benutzercodemethoden und asynchronen Routinen, die vom System- und Frameworkcode der zweiten Ebene aufgerufen oder erstellt werden.|
    |![Schritt 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Untergeordnete Knoten einer Methode enthalten Daten nur für die Aufrufe der übergeordneten Methode. Wenn **Externen Code anzeigen** deaktiviert ist, können App-Methoden auch den Knoten **[Externer Code]** enthalten.|

    Hier finden Sie weitere Informationen zu den Spaltenwerten:

    - Mit dem Wert **Gesamt-CPU** wird das Pensum angegeben, das von der Funktion und den von der Funktion aufgerufenen Funktionen bewältigt wurde. Hohe Werte bei „Gesamt-CPU“ deuten auf die insgesamt aufwändigsten Funktionen hin.

    - Mit dem Wert **Eigen-CPU** wird das bewältigte Pensum des Codes im Funktionsrumpf angegeben. Das Pensum der Funktionen, die durch den Code aufgerufen wurden, ist nicht enthalten. Hohe Werte bei **Eigen-CPU** deuten auf einen Leistungsengpass in der Funktion selbst hin.

    - **Module** Der Name des Moduls mit der Funktion oder die Anzahl der Module, die die Funktionen in einem Knoten vom Typ [Externer Code] enthalten.

    ::: moniker range=">=vs-2019"
    Um die Funktionsaufrufe anzuzeigen, die den höchsten Prozentsatz der CPU in der Ansicht der Aufrufstruktur verwenden, klicken Sie auf **Langsamsten Pfad erweitern**.

    ![Langsamster Pfad in den Diagnosetools](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > Wenn Sie in der Aufrufstruktur Code sehen, der als „broken“ oder „unwalkable stack“ markiert ist, bedeutet dies, dass Ereignisse aus der Ereignisablaufverfolgung für Windows wahrscheinlich gelöscht wurden. Versuchen Sie, die gleiche Ablaufverfolgung ein zweites Mal zu erfassen, um das Problem zu beheben.

## <a name="view-external-code"></a>Anzeigen von externem Code

Externer Code umfasst Funktionen in System- und Frameworkkomponenten, die vom Code ausgeführt werden, den Sie schreiben. Externer Code umfasst Funktionen, die die App starten und beenden, die Benutzeroberfläche zeichnen, das Threading steuern und der App andere hardwarenahe Dienste bereitstellen. In den meisten Fällen sind Sie nicht an externem Code interessiert, weshalb das CPU-Auslastungstool die externen Funktionen einer Benutzermethode im Knoten **[Externer Code]** sammelt.

Wenn Sie die Aufrufpfade von externem Code anzeigen möchten, wählen Sie aus der Liste **Filteransicht** die Option **Externen Code anzeigen** und dann **Übernehmen** aus.

![Anzeigen der Filteransicht und anschließendes Anzeigen von externem Code](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

Achten Sie darauf, dass viele externe Codeaufrufketten tief verschachtelt sind, sodass die Breite der Spalte mit dem Funktionsnamen die Anzeigebreite aller außer sehr großer Computerbildschirme überschreiten kann. In diesem Fall werden Funktionsnamen als **[…]** angezeigt.

Verwenden Sie das Suchfeld, um nach einem gewünschten Knoten zu suchen, und verwenden Sie dann die horizontale Bildlaufleiste, um die Daten sichtbar zu machen.

> [!TIP]
> Vergewissern Sie sich bei der Profilerstellung für externen Code, von dem Windows-Funktionen aufgerufen werden, dass Sie über die neuesten *PDB*-Dateien verfügen. Ohne diese Dateien werden in den Berichtsansichten kryptische und schwer verständliche Namen von Windows-Funktionen aufgeführt. Weitere Informationen zum Sicherstellen, dass Sie über die erforderlichen Dateien verfügen, finden Sie unter [Angeben von Symbol- (PDB) und Quelldateien im Debugger](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie CPU-Auslastungsdaten gesammelt und analysiert werden. Wenn Sie die [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md) bereits abgeschlossen haben, sollten Sie sich einen Überblick darüber verschaffen, wie die Speicherauslastung in Ihren Apps analysiert werden kann.

> [!div class="nextstepaction"]
> [Profilerstellung zur Arbeitsspeicherverwendung in Visual Studio](../profiling/memory-usage.md)
