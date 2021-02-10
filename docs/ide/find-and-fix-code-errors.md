---
title: Beheben von Programmfehlern und Verbessern von Code
description: In diesem Artikel werden einige grundlegende Methoden beschrieben, wie Sie mit Visual Studio Probleme im Code finden und beheben können, einschließlich Buildfehler, Codeanalyse, des Debuggens von Tools und Komponententests.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6da05729be409b142f6c9cec2c543fb2b9171ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869426"
---
# <a name="make-code-work-in-visual-studio"></a>Erstellen von funktionierendem Code in Visual Studio

Visual Studio bietet einen leistungsfähigen integrierten Satz von Projektbuild- und Debugtools. In diesem Artikel erfahren Sie, wie Sie mit Visual Studio mithilfe der Buildausgabe, Codeanalyse, Debugtools und Komponententests Probleme im Code beheben können.

Sie haben also herausgefunden, wie der Editor funktioniert, und Code erstellt. Nun möchten Sie sicherstellen, dass der Code richtig funktioniert. In Visual Studio geschieht das wie bei den meisten IDEs in zwei Phasen: dem Erstellen des Codes zum Abfangen und Beheben von Projekt- und Compilerfehlern und dem Ausführen dieses Codes zum Auffinden von Laufzeitfehlern und dynamischen Fehlern.

## <a name="build-your-code"></a>Erstellen des Codes

Es gibt zwei grundlegende Arten der Buildkonfiguration: **Debug** und **Release**. Die **Debug**-Konfiguration erzeugt eine langsamere und größere ausführbare Datei, die für ein umfangreicheres interaktives Debuggen zur Laufzeit verwendet werden kann. Die ausführbare **Debug**-Datei sollte jedoch nie ausgeliefert werden. Mit der **Releasekonfiguration** wird eine schnellere, optimierte ausführbare Datei erstellt, die (zumindest aus Sicht des Compilers) ausgeliefert werden kann. Die Standardbuildkonfiguration ist **Debug**.

Projekte lassen sich am einfachsten mit **F7** erstellen. Sie können aber auch im Hauptmenü auf **Erstellen** > **Projektmappe erstellen** klicken.

![Visual Studio, Menüauswahl zur Projekterstellung](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Sie können den Buildprozess im Fenster **Ausgabe** am unteren Rand der Visual Studio-Benutzeroberfläche beobachten. Dort werden Fehler, Warnungen und Buildvorgänge angezeigt. Wenn Fehler (oder Warnungen über die konfigurierte Stufe hinaus) auftreten, schlägt der Build fehl. Sie können auf die Fehler und Warnungen klicken, um zu der Zeile zu wechseln, in der der Fehler aufgetreten ist. Erstellen Sie Ihr Projekt neu, indem Sie entweder **F7** erneut drücken (um nur die Dateien mit Fehlern neu zu kompilieren) oder indem Sie **STRG**+**ALT**+**F7** drücken (für eine vollständige Neuerstellung).

Im Ergebnisfenster unterhalb des Editors finden Sie zwei Fenster im Registerkartenformat: Das Fenster **Ausgabe** enthält die unformatierte Compilerausgabe (einschließlich Fehlermeldungen), und das Fenster **Fehlerliste** enthält eine sortierbare und filterfähige Liste aller Fehler und Warnungen.

Bei erfolgreicher Erstellung werden die Ergebnisse wie folgt im Fenster **Ausgabe** dargestellt:

![Visual Studio, erfolgreiche Buildausgabe](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Anzeigen der Fehlerliste

Sofern Sie keine Änderungen am Code vorgenommen haben, den Sie zuvor erfolgreich kompiliert hatten, tritt vermutlich ein Fehler auf. Wenn Sie noch nie programmiert haben, werden wahrscheinlich viele Fehler auftreten. Fehler sind manchmal offensichtlich, so z.B. einfache Syntaxfehler oder falsche Variablennamen. Wenn der Code schlecht lesbar ist, können Fehler jedoch sehr schwer zu finden sein. Für eine übersichtlichere Ansicht der Probleme navigieren Sie zum Ende des Fensters **Ausgabe** für den Build, und klicken Sie auf die Registerkarte **Fehlerliste**. Dadurch gelangen Sie zu einer besser angeordneten Ansicht der Fehler und Warnungen für das Projekt mit einigen zusätzlichen Optionen.

![Visual Studio, Ausgabe und Fehlerliste](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Klicken Sie im Fenster **Fehlerliste** auf die Zeile mit dem Fehler, um direkt in die Zeile zu springen, in der der Fehler aufgetreten ist. (Aktivieren Sie alternativ Zeilennummern, indem Sie **STRG**+**Q** drücken, **Zeilennummern** eingeben und dann aus den Ergebnissen die Option **Zeilennummern aktivieren oder deaktivieren** auswählen. Dies ist die schnellste Möglichkeit zum Aufrufen des Dialogfeldes **Optionen**, in dem Sie Zeilennummern aktivieren können.)

![Visual Studio, Editor mit Zeilennummern](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio, Option für Zeilennummern](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Mit **STRG**+**G** können Sie schnell in die Zeile springen, in der der Fehler aufgetreten ist.

Der Fehler wird durch eine rote Wellenlinie gekennzeichnet. Bewegen Sie den Mauszeiger darüber, um weitere Informationen anzuzeigen. Wenn Sie die Korrektur vornehmen, wird die Markierung aufgehoben. Es ist natürlich trotzdem möglich, dass Sie mit Ihrer Änderung einen neuen Fehler einfügen. (Dies wird als „Regression“ bezeichnet.)

![Visual Studio-Fehler, wenn darauf gezeigt wird](../ide/media/vs_ide_gs_debug_error_hover1.png)

Bearbeiten Sie die Fehlerliste, und beheben Sie alle Fehler im Code.

![Visual Studio, Fenster "Debugfehler"](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Detaillierte Anzeige der Fehler

Einige Fehler erscheinen Ihnen möglicherweise nicht sinnvoll, wenn sie wie vom Compiler formuliert angezeigt werden. In diesen Fällen benötigen Sie weitere Informationen. Über das Fenster **Fehlerliste** können Sie eine automatische Suche in Bing nach weiteren Informationen zum Fehler bzw. zur Warnung ausführen. Klicken Sie mit der rechten Maustaste auf die entsprechende Zeile, und klicken Sie im Kontextmenü auf **Hilfe zu Fehlern anzeigen**. Klicken Sie alternativ in der Spalte **Code** der **Fehlerliste** auf den als Hyperlink formatierten Fehlercodewert.

![Visual Studio, Fehlerliste "Bing-Suche"](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

Je nach Ihren Einstellungen zeigt entweder der Webbrowser die Suchergebnisse für den Fehlercode und -text an, oder es wird eine Registerkarte in Visual Studio geöffnet, die die Ergebnisse der Bing-Suche anzeigt. Die Ergebnisse stammen aus verschiedenen Quellen im Internet und sind möglicherweise nicht alle hilfreich.

## <a name="use-code-analysis"></a>Verwenden der Codeanalyse

Codeanalysetools suchen nach häufig auftretenden Codeproblemen, die Laufzeitfehler oder Probleme bei der Codeverwaltung hervorrufen können.

### <a name="c-and-visual-basic-code-analysis"></a>Codeanalyse in C# und Visual Basic

Visual Studio enthält mehrere integrierte [.NET Compiler Platform-Analysetools](../code-quality/roslyn-analyzers-overview.md), die C#- und Visual Basic-Code während der Eingabe untersuchen. Sie können aber auch zusätzliche Analysetools als Visual Studio-Erweiterung oder als NuGet-Paket installieren. Wenn Regelverstöße festgestellt werden, werden sie sowohl in der Fehlerliste gemeldet als auch im Code-Editor mit einer gewellten Linie unter dem fehlerhaften Code unterstrichen.

### <a name="c-code-analysis"></a>C++-Codeanalyse

Führen Sie zum Analysieren von C++-Code die [statische Codeanalyse](/cpp/code-quality/quick-start-code-analysis-for-c-cpp) aus. Sie sollten sich angewöhnen, sie auszuführen, nachdem Sie offensichtliche Fehler behoben haben, die ein erfolgreiches Erstellen verhindern würden. Es lohnt sich, sich die Zeit für die Warnungen zu nehmen. Sie vermeiden so, dass zu einem späteren Zeitpunkt Probleme auftreten, und lernen ggf. etwas über Stiltechniken beim Programmieren.

Drücken Sie **ALT**+**F11** (oder wählen Sie im oberen Menü **Analysieren** > **Codeanalyse für Projektmappe ausführen** aus), um die statische Codeanalyse zu starten.

![Visual Studio, Menüelement „Codeanalyse“](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Alle neuen oder aktualisierten Warnungen werden auf der Registerkarte **Fehlerliste** am unteren Rand der IDE angezeigt. Klicken Sie auf die Warnungen, um zu der betreffenden Stelle im Code zu springen.

![Visual Studio, Fehlerliste mit Warnungen](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Verwenden von Schnellaktionen zum Beheben oder Umgestalten von Code

Über [Schnelle Aktionen](../ide/quick-actions.md) (über das Glühbirnen- oder Schraubendrehersymbol verfügbar) können Sie eine Inline-Umgestaltung von Code vornehmen. Damit können allgemeine Warnungen in C#, C++ und Visual Basic schnell und effektiv behoben werden. Um darauf zuzugreifen, klicken Sie mit der rechten Maustaste auf die gewellte Linie, und klicken Sie auf **Schnelle Aktionen und Refactorings**. Wenn der Cursor sich in der Zeile mit der farbigen Wellenlinie befindet, können Sie auch **STRG**+ **.** drücken oder im Randbereich auf das Glühbirnen-, Fehlerglühbirnen- oder Schraubendrehersymbol klicken. Daraufhin wird eine Liste mit möglichen Korrekturen oder Umgestaltungen angezeigt, die Sie in dieser Codezeile vornehmen können.

![Visual Studio, Glühbirne mit Vorschau](../ide/media/quick-actions-options.png)

Schnelle Aktionen können immer dann verwendet werden, wenn Codeanalysetools feststellen, dass es eine Möglichkeit gibt, Fehler Ihres Codes zu beheben, diesen umzugestalten oder diesen zu verbessern. Klicken Sie mit der rechten Maustaste auf eine beliebige Codezeile, um das Kontextmenü zu öffnen, und klicken Sie auf **Schnelle Aktionen und Refactorings**. Wenn Optionen zum Umgestalten oder Verbessern verfügbar sind, werden diese angezeigt. Andernfalls wird die Nachricht **Keine schnellen Aktionen verfügbar** unten links in der IDE angezeigt.

![Text „Keine schnellen Aktionen verfügbar“](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Mit etwas Erfahrung können Sie rasch mithilfe der Pfeiltasten und **STRG**+ **.** überprüfen, ob Möglichkeiten zur Umgestaltung und Bereinigung Ihres Codes verfügbar sind.

::: moniker range="vs-2019"

## <a name="run-code-cleanup"></a>Ausführen der Codebereinigung

Mit der Schaltfläche **Codebereinigung** am unteren Rand des Editors bietet Visual Studio eine [bedarfsgesteuerte Formatierung Ihrer C#-Codedatei](code-styles-and-code-cleanup.md#apply-code-styles), einschließlich Codeformateinstellungen.

![Schaltfläche „Codebereinigung“ in Visual Studio 2019](media/execute-code-cleanup.png)

Zusätzlich zur Formatierung Ihrer Datei im Hinblick auf Leerzeichen, Einzüge usw. wendet die **Codebereinigung** auch eine Reihe von Codeformaten an, die Sie festlegen. Ihre Einstellungen für jedes Codeformat werden aus der [EditorConfig-Datei](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) gelesen, sofern für das Projekt eine vorhanden ist, oder aus den [Codeformateinstellungen](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) im Dialogfeld **Optionen**.

::: moniker-end

## <a name="debug-your-running-code"></a>Debuggen von ausgeführtem Code

Nachdem Sie Code erstellt und einige Bereinigungen durchgeführt haben, führen Sie ihn aus, indem Sie **F5** drücken oder auf **Debuggen** > **Debuggen starten** klicken. Dadurch wird Ihre App in einer Debugumgebung gestartet, damit Sie ihr Verhalten im Detail beobachten können. Die Visual Studio-IDE ändert sich während der Ausführung Ihrer App: Das Fenster **Ausgabe** wird (in der standardmäßigen Fensterkonfiguration) durch zwei neue ersetzt, und zwar die Registerkartenfenster **Auto/Lokal/Module/Überwachung** und **Aufrufliste/Haltepunkte/Ausnahmeeinstellungen/Ausgabe**. Diese Fenster enthalten mehrere Registerkarten, mit denen Sie Variablen, Threads, Aufruflisten und andere Verhaltensweisen während der Ausführung Ihrer App überprüfen und bewerten können.

![Visual Studio, Automatische und Aufruflistenfenster](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Beenden Sie die App, indem Sie **UMSCHALT**+**F5** drücken oder auf **Beenden**  klicken. Alternativ können Sie einfach das Hauptfenster (oder das Befehlszeilen-Dialogfeld) der App schließen.

Wenn Ihr Code ohne besondere Vorkommnisse genau wie erwartet ausgeführt wurde, sind Sie damit fertig! Wenn der Code jedoch nicht mehr reagiert oder abgestürzt, oder wenn Sie unerwartete Ergebnisse erhalten, müssen Sie die Ursache dieser Probleme suchen und die Fehler beheben.

### <a name="set-simple-breakpoints"></a>Festlegen einfacher Haltepunkte

[Breakpoints](../debugger/using-breakpoints.md) sind das einfachste und wichtigste Feature zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. Sie müssen ein Projekt nicht neu erstellen, nachdem Sie Breakpoints festgelegt oder entfernt haben.

Legen Sie einen Haltepunkt fest, indem Sie auf den äußeren Rand der Zeile klicken, in der Sie die Unterbrechung einfügen möchten, oder wählen Sie die Codezeile aus, und drücken Sie **F9**. Wenn Sie Code ausführen, wird er direkt vor der Ausführung der Anweisungen für diese Codezeile angehalten (oder *unterbrochen*).

![Visual Studio, Haltepunkt](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Für Folgendes werden Haltepunkte häufig verwendet:

- Sie können die Ursachen eines Absturzes oder nicht reagierenden Programmes eingrenzen, indem Sie im gesamten Code und um den Code für den Methodenaufruf Breakpoints platzieren, von dem Sie annehmen, dass er den Fehler verursacht. Wenn Sie den Code im Debugger ausführen, entfernen Sie die Haltepunkte, und platzieren Sie diese dann näher beieinander, bis Sie die fehlerhafte Codezeile finden. Im nächsten Abschnitt erfahren Sie, wie Sie Code im Debugger ausführen.

- Wenn Sie neuen Code einführen, platzieren Sie am Anfang einen Breakpoint, und führen Sie diesen Code aus, um sicherzustellen, dass er sich wie erwartet verhält.

- Wenn Sie kompliziertes Verhalten implementiert haben, legen Sie Breakpoints für den algorithmischen Code fest, damit Sie die Werte der Variablen und Daten überprüfen können, wenn das Programm unterbrochen wird.

- Wenn Sie Code in C oder C++ schreiben, verwenden Sie Breakpoints zum Anhalten des Codes, um die Adresswerte (suchen Sie nach NULL-Werten) und Verweiszähler beim Debuggen von speicherbezogenen Fehlern zu überprüfen.

Weitere Informationen finden Sie unter [Verwenden von Breakpoints im Visual Studio-Debugger](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Überprüfen von Code zur Laufzeit

Wenn der ausgeführte Code auf einen Haltepunkt trifft und anhält, wurde die gelb markierte Codezeile (die aktuelle Anweisung) noch nicht ausgeführt. In dieser Situation ist es empfehlenswert, die aktuelle Anweisung auszuführen und anschließend die geänderten Werte zu überprüfen. Sie können mehrere *step*-Befehle zum Ausführen von Code im Debugger verwenden. Ist der gekennzeichnete Code ein Methodenaufruf, durchlaufen Sie diesen schrittweise durch Drücken von **F11**. Sie können die Codezeile durch Drücken von **F10** auch *überspringen*. Zusätzliche Befehle und Details dazu, wie Code schrittweise durchlaufen wird, finden Sie unter [Navigate code with the debugger (Navigieren im Code mit dem Debugger)](../debugger/navigating-through-code-with-the-debugger.md).

![Screenshot des Visual Studio-Codefensters. Ein roter Punkt im linken Bundsteg zeigt einen Haltepunkt in der Codezeile an, die gelb markiert ist.](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Wie in der vorherigen Abbildung dargestellt, kann der Debugger mit **F10** oder **F11** zur nächsten Anweisung springen (da dies kein Methodenaufruf ist, bewirken beide Befehle dasselbe).

Während der Debugger angehalten ist, können Sie die Variablen und Aufruflisten untersuchen, um herauszufinden, was gerade vorgeht. Liegen die Werte in den erwarteten Bereichen? Werden die Aufrufe in der richtigen Reihenfolge ausgeführt?

![Screenshot des Visual Studio-Codefensters. In der gelb markierten Codezeile ist eine Variable ausgewählt, und eine Dropdownliste wird mit ihrem aktuellen Wert und den aktuellen Verweisen angezeigt.](../ide/media/vs_ide_gs_debug_inspect_value.png)

Zeigen Sie auf eine Variable, um den aktuellen Wert und die Verweise anzuzeigen. Wenn Sie einen nicht erwarteten Wert antreffen, enthält der vorhergehende oder der aufrufende Code möglicherweise einen Fehler. Weitere Informationen finden Sie unter [Tutorial: Weitere Informationen zum Debuggen mit Visual Studio](../debugger/debugger-feature-tour.md).

Darüber hinaus zeigt Visual Studio das Fenster **Diagnosetools** an, in dem Sie den CPU- und Speicherverbrauch Ihrer App im Zeitverlauf beobachten können. In einer späteren Entwicklungsphase können Sie mit diesen Tools nach unvorhergesehen hoher CPU-Auslastung oder Speicherzuweisung suchen. Zusammen mit dem Fenster **Überwachung** und Haltepunkten können Sie so sehr schnell ermitteln, wodurch eine unerwartete Auslastung oder nicht freigegebene Ressourcen verursacht werden. Weitere Informationen finden Sie unter [Tour zur Profilerstellungsfunktion](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Komponententests ausführen

Komponententests sind die erste Maßnahme zur Vorbeugung von Fehlern im Code. Bei korrekter Ausführung wird dabei eine einzelne „Codeeinheit“ getestet, in der Regel ist dies eine einzelne Funktion. Das Debuggen einer einzelnen Codeeinheit ist einfacher als das Debuggen eines vollständigen Programms. Visual Studio enthält die Komponententest-Frameworks von Microsoft für sowohl verwalteten als auch nativen Code. Verwenden Sie ein Unittest-Framework, um Komponententests zu erstellen, auszuführen und Berichte mit den Ergebnissen dieser Tests zu erstellen. Führen Sie Komponententests erneut durch, wenn Sie Änderungen vorgenommen haben, um zu testen, dass der Code weiterhin ordnungsgemäß ausgeführt wird. Mit Visual Studio Enterprise Edition können die Tests automatisch nach jedem Build ausgeführt werden.

Weitere Informationen finden Sie unter [Generieren intelligenter Komponententests für Ihren Code mit IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Weitere Informationen zu Komponententests in Visual Studio und wie diese Ihnen helfen, besseren Code zu erstellen, finden Sie unter [Unit Test Basics (Grundlagen zu Komponententests)](../test/unit-test-basics.md).

## <a name="see-also"></a>Siehe auch

- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Weitere Informationen zur Verwendung des Debuggers](../debugger/index.yml)
- [Generieren und Korrigieren von Code](../ide/code-generation-in-visual-studio.md)
