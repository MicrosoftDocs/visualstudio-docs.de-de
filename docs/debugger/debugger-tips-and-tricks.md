---
title: Tipps und Tricks im Debugger
description: Erfahren Sie mehr über einige der weniger bekannten Features, die vom Visual Studio-Debugger unterstützt werden.
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5b934c0e9532bd3bc1f53d9b00d1cc8273f4120
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872988"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Lernen Sie Produktivitätstipps und Tricks für den Debugger in Visual Studio kennen.

Lesen Sie dieses Thema, um einige Produktivitätstipps und Tricks für den Visual Studio-Debugger kennenzulernen. Einblicke in die grundlegenden Funktionen des Debuggers finden Sie unter [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md). In diesem Thema werden einige Aspekte behandelt, die nicht in der Featuretour enthalten sind.

## <a name="pin-data-tips"></a>Anheften von Datentipps

Wenn Sie während des Debuggens häufig auf Datentipps zeigen, sollten Sie den Datentipp für die Variable anheften, um sich schnellen Zugriff zu verschaffen. Die Variable bleibt auch nach einem Neustart angeheftet. Um den Datentipp anzuheften, klicken Sie auf das Anheftsymbol, während Sie darauf zeigen. Sie können mehrere Variablen anheften.

![Anheften eines Datentipps](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Bearbeiten des Codes und Fortsetzen des Debuggens (C#, VB, C++)

In den meisten Sprachen, die von Visual Studio unterstützt werden, können Sie den Code während einer Debugsitzung bearbeiten und das Debuggen fortsetzen. Wenn Sie dieses Feature verwenden möchten, klicken Sie mit dem Cursor auf den Code, während dieser im Debugger angehalten wurde, und bearbeiten Sie diesen. Drücken Sie **F5**, **F10** oder **F11**, um das Debuggen fortzusetzen.

![Bearbeiten und Fortsetzen des Debuggens](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Weitere Informationen zur Verwendung des Features finden Sie unter [Bearbeiten und Fortsetzen](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Bearbeiten von XAML-Code und Fortsetzen des Debuggens

Weitere Informationen zum Ändern von XAML-Code während einer Debugsitzung finden Sie unter [Schreiben und Debuggen von ausgeführtem XAML-Code durch Neuladen von XAML im laufenden Betrieb](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Debuggen von Problemen, die schwer zu reproduzieren sind

Wenn es schwierig oder zeitaufwändig ist, einen bestimmten Status in Ihrer App zu reproduzieren, überlegen Sie, ob die Verwendung eines bedingten Breakpoints hilfreich sein kann. Sie können [bedingte Breakpoints ](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) verwenden und Breakpoints filtern, um das Unterbrechen des App-Codes zu vermeiden, bis die App in den gewünschten Zustand wechselt (z. B. in einen Zustand, in dem eine Variable ungültige Daten speichert). Sie können Bedingungen mithilfe von Ausdrücken, Filtern, Trefferanzahlen usw. festlegen.

#### <a name="to-create-a-conditional-breakpoint"></a>So erstellen Sie einen bedingten Breakpoint

1. Klicken Sie mit der rechten Maustaste auf ein Breakpointsymbol (den roten Kreis), und wählen Sie **Bedingungen** aus.

2. Geben Sie im Fenster **Breakpointeinstellungen** einen Ausdruck ein.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Wenn Sie an einer anderen Art von Bedingung interessiert sind, wählen Sie im Dialogfeld **Breakpointeinstellungen** die Option **Filter** anstelle von **Bedingter Ausdruck** aus, und befolgen Sie dann die Filtertipps.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Konfigurieren der Daten, die im Debugger angezeigt werden sollen

Für C#, Visual Basic und C++ (nur C++/CLI-Code) können Sie dem Debugger über das Attribut [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) mitteilen, welche Informationen angezeigt werden sollen. Für C++ Code können Sie zu diesem Zweck [Natvis-Visualisierungen](create-custom-views-of-native-objects.md) verwenden.

## <a name="change-the-execution-flow"></a>Ändern des Ausführungsablaufs

Wenn der Debugger in einer Codezeile angehalten wurde, verwenden Sie die Maus, um den gelben Pfeilzeiger auf der linken Seite zu erfassen. Bewegen Sie den gelben Pfeilzeiger an einen anderen Punkt im Codeausführungspfad. Anschließend verwenden Sie F5 oder einen Schrittbefehl, um die Ausführung der App fortzusetzen.

![Verschieben des Ausführungszeigers](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Verschieben des Ausführungszeigers")

Durch Ändern des Ausführungsablaufs können Sie Aktionen ausführen wie das Testen verschiedener Pfade für die Codeausführung oder das erneute Ausführen von Code ohne Neustarten des Debuggers.

> [!WARNING]
> Bei dieser Funktion müssen Sie häufig vorsichtig vorgehen. Sie werden durch eine Warnung in der QuickInfo auf Probleme aufmerksam gemacht. Möglicherweise werden Ihnen auch andere Warnungen angezeigt. Durch das Verschieben des Zeigers kann Ihre App nicht auf einen früheren Anwendungsstatus zurückgesetzt werden.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Nachverfolgen eines Objekts außerhalb des Bereichs (C#, Visual Basic)

Es ist einfach, Variablen mit Debuggerfenstern anzuzeigen, etwa mit dem **Überwachungsfenster**. Wenn eine Variable jedoch den Bereich im **Überwachungsfenster** verlässt, werden Sie möglicherweise bemerken, dass sie ausgegraut angezeigt wird. In einigen App-Szenarien kann sich der Wert einer Variablen ändern, selbst wenn die Variable außerhalb des Bereichs liegt, und Sie möchten sie vielleicht genau beobachten (z. B. kann für eine Variable Garbage Collection ausgeführt werden). Sie können die Variable nachverfolgen, indem Sie im **Überwachungsfenster** eine Objekt-ID für sie erstellen.

#### <a name="to-create-an-object-id"></a>So erstellen Sie eine Objekt-ID

1. Legen Sie einen Breakpoint in der Nähe einer Variablen fest, die Sie nachverfolgen möchten.

2. Starten Sie den Debugger (**F5**), und halten Sie am Breakpoint an.

3. Suchen Sie die Variable im Fenster **Lokale Variablen** (**Debuggen > Windows > Lokale Variablen**), klicken Sie mit der rechten Maustaste auf die Variable, und wählen Sie dann **Objekt-ID erstellen** aus.

    ![Erstellen einer Objekt-ID](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Sie sollten ein **$** und eine Zahl im **Lokalfenster** einen Haltepunkt festlegen. Diese Variable ist die Objekt-ID.

5. Klicken Sie mit der rechten Maustaste auf die Objekt-ID-Variable, und wählen Sie **Überwachung hinzufügen** aus.

Weitere Informationen finden Sie unter [Erstellen einer Objekt-ID](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Anzeigen von Rückgabewerten für Funktionen

Wenn Sie Rückgabewerte für Ihre Funktionen anzeigen möchten, untersuchen Sie die Funktionen, die im Fenster **Auto** angezeigt werden, während Sie den Code schrittweise durchlaufen. Wenn Sie den Rückgabewert für eine Funktion anzeigen möchten, stellen Sie sicher, dass die Funktion, an der Sie interessiert sind, bereits ausgeführt wurde (drücken Sie ein Mal **F10**, wenn Sie die Ausführung aktuell beim Funktionsaufruf angehalten haben). Wenn das Fenster geschlossen ist, verwenden Sie **Debuggen > Windows > Auto**, um das Fenster **Auto** zu öffnen.

![Fenster „Auto“](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Außerdem können Sie Funktionen in das Fenster **Direkt** eingeben, um Rückgabewerte anzuzeigen. (Öffnen Sie es mit **Debuggen > Windows > Direkt**.)

![Direktfenster](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Sie können auch [Pseudovariablen](../debugger/pseudovariables.md) im Fenster **Überwachung** und **Direkt** (z. B. `$ReturnValue`) verwenden.

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Untersuchen von Zeichenfolgen in einer Schnellansicht

Beim Arbeiten mit Zeichenfolgen kann es hilfreich sein, die gesamte formatierte Zeichenfolge anzuzeigen. Um eine Nur-Text-, XML-, HTML- oder JSON-Zeichenfolge anzuzeigen, klicken Sie auf das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Symbol der Schnellansicht"), während Sie auf eine Variable mit einem Zeichenfolgenwert zeigen.

![Öffnen einer Zeichenfolgenschnellansicht](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Mithilfe einer Zeichenfolgenschnellansicht können Sie abhängig vom Typ der Zeichenfolge ermitteln, ob eine Zeichenfolge falsch formatiert ist. Beispielsweise gibt ein leeres Feld **Wert** an, dass die Zeichenfolge vom Typ der Schnellansicht nicht erkannt wird. Weitere Informationen finden Sie unter [Dialogfeld „Zeichenfolgenschnellansicht“](../debugger/string-visualizer-dialog-box.md).

![JSON-Zeichenfolgenschnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Für einige andere Typen (z. B. DataSet- und DataTable-Objekte), die in den Debuggerfenstern angezeigt werden, können Sie auch eine integrierte Schnellansicht öffnen.

## <a name="break-into-code-on-handled-exceptions"></a>Unterbrechen des Codes für behandelte Ausnahmen

Der Debugger unterbricht den Code bei nicht behandelten Ausnahmen. Behandelte Ausnahmen (z. B. Ausnahmen, die in einem `try/catch`-Block auftreten) können jedoch auch eine Fehlerquelle sein, die Sie möglicherweise bei ihrem Auftreten untersuchen möchten. Sie können den Debugger auch so konfigurieren, dass er Code für behandelte Ausnahmen unterbricht, indem Sie Optionen im Dialogfeld **Ausnahmeeinstellungen** konfigurieren. Öffnen Sie dieses Dialogfeld, indem Sie **Debuggen > Windows > Ausnahmeeinstellungen** auswählen.

Im Dialogfeld **Ausnahmeeinstellungen** können Sie den Debugger anweisen, den Code bei bestimmten Ausnahmen zu unterbrechen. In der Abbildung unten unterbricht der Debugger den Code immer dann, wenn eine `System.NullReferenceException` auftritt. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen](../debugger/managing-exceptions-with-the-debugger.md).

![Dialogfeld „Ausnahmeeinstellungen“](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Debuggen von Deadlocks und Racebedingungen

Wenn Sie die Arten von Problemen debuggen müssen, die bei Multithreadanwendungen häufig vorkommen, ist es manchmal hilfreich, den Speicherort der Threads während des Debuggens anzuzeigen. Dies ist problemlos möglich, indem Sie die Schaltfläche **Threads in Quelle anzeigen** verwenden.

#### <a name="to-show-threads-in-your-source-code"></a>So zeigen Sie Threads in Ihrem Quellcode an

1. Klicken Sie beim Debuggen auf der Symbolleiste **Debuggen** auf die Schaltfläche **Threads in Quelle anzeigen** ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile sehen Sie ein Symbol *Threadmarker* ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker"), das zwei Fäden ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Beachten Sie, dass ein Threadmarker möglicherweise teilweise durch einen Breakpoint verdeckt wird.

3. Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt. Anhand des DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads.

    Sie können den Speicherort der Threads auch im Fenster [Parallele Stapel](../debugger/get-started-debugging-multithreaded-apps.md) anzeigen.

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Untersuchen von Nutzlasten für Webdienste und Netzwerkressourcen (UWP)

In UWP-Apps können Sie mit der `Windows.Web.Http`-API ausgeführte Netzwerkvorgänge analysieren. Sie können dieses Tool verwenden, um Webdienste und Netzwerkressourcen zu debuggen. Um das Tool zu verwenden, wählen Sie **Debuggen > Leistungs-Profiler** aus. Wählen Sie **Netzwerk** aus, und klicken Sie dann auf **Starten**. Durchlaufen Sie in Ihrer Anwendung das Szenario, das `Windows.Web.Http` verwendet, und wählen Sie anschließend **Auflistung beenden** aus, um einen Bericht zu generieren.

![Profilerstellungstool „Netzwerkauslastung“](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Wählen Sie einen Vorgang in der Ansicht „Zusammenfassung“ aus, um mehr Details anzuzeigen.

![Ausführliche Informationen im Tool „Netzwerkauslastung“](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Weitere Informationen finden Sie unter [Netzwerkverwendung](../profiling/network-usage.md).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a> Informieren Sie sich darüber, wie der Debugger an Ihre App angefügt wird (C#, C++, Visual Basic, F#)

Zum Anfügen an die aktuell ausgeführte App lädt der Debugger Symboldateien (PDB-Dateien), die für genau denselben Build der App generiert werden, die Sie debuggen möchten. In einigen Szenarien können Kenntnisse zu Symboldateien hilfreich sein. Sie können untersuchen, wie Visual Studio Symboldateien lädt, indem Sie das Fenster **Module** verwenden.

Öffnen Sie während des Debuggens das Fenster **Module**, indem Sie **Debuggen > Windows > Module** auswählen. Im Fenster **Module** können Sie feststellen, welche Module der Debugger als Benutzercode oder als [*eigenen Code*](../debugger/just-my-code.md) behandelt. Außerdem wird der Symbolladestatus für das Modul angegeben. In den meisten Szenarien findet der Debugger automatisch Symboldateien für Benutzercode, aber wenn Sie .NET-Code, Systemcode oder Bibliothekscode von Drittanbietern schrittweise durchlaufen (oder debuggen) möchten, sind zusätzliche Schritte erforderlich, um die richtigen Symboldateien abzurufen.

![Anzeigen von Symbolinformationen im Fenster „Module“](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Sie können Symbolinformationen direkt aus dem Fenster **Module** laden, indem Sie mit der rechten Maustaste klicken dann und **Symbole laden** auswählen.

Manchmal liefern App-Entwickler Apps ohne die passenden Symboldateien aus (um den Speicherbedarf zu verringern), behalten jedoch eine Kopie der passenden Symboldateien für den Build, damit sie eine veröffentlichte Version später debuggen können.

Informationen dazu, wie der Debugger Code als Benutzercode klassifiziert, finden Sie unter [Nur eigenen Code](../debugger/just-my-code.md). Weitere Informationen zu Symboldateien finden Sie unter [Angeben von Symbol- (PDB-Dateien) und Quelldateien im Visual Studio Debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Weitere Informationen

Weitere Tipps und Tricks sowie ausführlichere Informationen finden Sie in den folgenden Blogbeiträgen:

- [7 weniger bekannte Hacks für das Debuggen in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 verborgene Schätze in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Siehe auch

[Tastenkombinationen](../ide/productivity-shortcuts.md)
