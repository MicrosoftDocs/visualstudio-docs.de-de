---
title: 'Tutorial: Debuggen von Visual Basic-Code'
description: Lernen Sie Funktionen des Visual Studio-Debuggers kennen, und erfahren Sie, wie Sie den Debugger starten, den Code durchlaufen und Daten in einer Visual Basic-Anwendung überprüfen.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 02/03/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- VB
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b4cb6cbdaee7e5bed6cb80cea1f431a6db4d286e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915045"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Tutorial: Informationen zum Debuggen von Visual Basic-Code mit Visual Studio

In diesem Artikel werden die Funktionen des Visual Studio-Debuggers in einer ausführlichen exemplarischen Vorgehensweise vorgestellt. Einen allgemeineren Überblick über die Funktionen des Debuggers finden Sie unter [Ein erster Blick auf den Visual Studio-Debugger](../../debugger/debugger-feature-tour.md). Wenn Sie *Ihre App debuggen*, bedeutet dies in der Regel, dass Sie Ihre Anwendung mit dem angefügten Debugger ausführen. Wenn Sie dies machen, bietet der Debugger viele Möglichkeiten zum Ermitteln des Status Ihres Codes während der Ausführung. Sie können Ihren Code schrittweise durchlaufen und die Werte prüfen, die in Variablen gespeichert sind, Sie können die Überwachung von Variablen festlegen, um zu sehen, wenn sich Werte ändern, und Sie können den Ausführungspfad Ihres Codes prüfen und feststellen, ob ein Codezweig ausgeführt wird usw. Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../../debugger/debugging-absolute-beginners.md) lesen, bevor Sie diesen Artikel durchgehen.

Auch wenn die Demo-App Visual Basic verwendet, beziehen sich die meisten Features auf C#, C++, F#, Python, JavaScript und andere von Visual Studio unterstützte Programmiersprachen. F# unterstützt „Bearbeiten und Fortfahren“ nicht. Das Fenster **Auto** wird weder von JavaScript noch F# unterstützt). Die Screenshots wurden in Visual Basic erstellt.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten des Debuggers und Treffen der Breakpoints.
> * Erlernen von Befehlen zum Durchlaufen des Codes im Debugger
> * Überprüfen von Variablen im Fenster für Datentipps und im Debugger-Fenster
> * Überprüfen der Aufrufliste

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"

Sie müssen Visual Studio 2019 und die Workload **Plattformübergreifende .NET Core-Entwicklung** installiert haben.

::: moniker-end
::: moniker range="vs-2017"

Sie müssen Visual Studio 2017 und die Workload **Plattformübergreifende .NET Core-Entwicklung** installiert haben.

::: moniker-end

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

Wenn Sie die Workload installieren müssen, Visual Studio aber bereits besitzen, navigieren Sie zu **Tools** > **Tools und Features abrufen…** . Dadurch wird der Visual Studio-Installer geöffnet. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die .NET Core-Konsolenanwendung erstellen. Der Projekttyp enthält, schon bevor Sie mit der Bearbeitung beginnen, alle Vorlagendateien, die Sie benötigen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual Basic**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie das Projekt *get-started-debugging*.

     Falls Sie die Projektvorlage **Konsolenanwendung (.NET Core)** nicht finden, klicken Sie auf den Link **Visual Studio-Installer öffnen** auf der linken Seite des Dialogfelds **Neues Projekt**.

     Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

::: moniker-end

::: moniker range="vs-2019"

1. Öffnen Sie Visual Studio 2019.

   Wenn das Startfenster nicht geöffnet ist, klicken Sie auf **Datei** > **Startfenster**.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

1. Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld *Konsole* ein. Wählen Sie anschließend in der Liste der Sprachen **Visual Basic** und dann aus der Liste der Plattformen **Windows** aus. 

   Nachdem Sie die Sprach- und Plattformfilter angewendet haben, wählen Sie die Vorlage **Konsolen-App (.NET Core)** und dann **Weiter** aus.

   ![Auswählen der Visual Basic-Vorlage für die Konsolen-App (.NET Core)](../visual-basic/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Wenn Sie die **Konsolen-App (.NET Core)** nicht sehen, können Sie sie aus dem Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus. Wählen Sie anschließend im Visual Studio-Installer die Workload **Plattformübergreifende .NET Core-Entwicklung** aus.

1. Geben Sie anschließend im Fenster **Neues Projekt konfigurieren** im Feld **Projektname** den Name *get-started-debugging* ein. Wählen Sie anschließend **Erstellen** aus.

   Visual Studio öffnet Ihr neues Projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Erstellen der Anwendung

1. Ersetzen Sie in der Datei *Program.vb* den gesamten Code durch den folgenden:

    ```vb
    Imports System

    Class ArrayExample
        Public Shared Sub Main()
            Dim letters As Char() = {"f"c, "r"c, "e"c, "d"c, " "c, "s"c, "m"c, "i"c, "t"c, "h"c}
            Dim name As String = ""
            Dim a As Integer() = New Integer(9) {}

            For i As Integer = 0 To letters.Length - 1
                name += letters(i)
                a(i) = i + 1
                SendMessage(name, a(i))
            Next

            Console.ReadKey()
        End Sub

        Private Shared Sub SendMessage(ByVal name As String, ByVal msg As Integer)
            Console.WriteLine("Hello, " & name & "! Count to " & msg)
        End Sub
    End Class
    ```

## <a name="start-the-debugger"></a>Starten Sie den Debugger.

1. Drücken Sie **F5** (**Debuggen > Debuggen starten**), oder wählen Sie auf der Symbolleiste „Debuggen“ die Schaltfläche **Debuggen starten**![Debuggen starten](../../debugger/media/dbg-tour-start-debugging.png "Debugging starten") aus.

     Durch Drücken der Taste **F5** wird die App mit dem an den App-Prozess angefügten Debugger gestartet. Bisher haben Sie jedoch nichts weiter gemacht, um den Code zu untersuchen. Die App wird lediglich geladen, und Ihnen wird die Konsolenausgabe angezeigt.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     In diesem Tutorial werfen wir einen genaueren Blick auf diese App mit dem Debugger und schauen uns die Funktionen des Debuggers an.

2. Durch Drücken der roten Stopptaste ![Debuggen beenden](../../debugger/media/dbg-tour-stop-debugging.png "Debuggen beenden") können Sie den Debugger beenden. Alternativ können Sie die Tastenkombination **UMSCHALT** + **F5** verwenden.

3. Drücken Sie im Konsolenfenster auf eine Taste, um das Konsolenfenster zu schließen.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Breakpoints und Starten des Debuggers

1. Legen Sie in der `For`-Schleife der Funktion `Main` einen Breakpoint fest, indem Sie auf den linken Rand der folgenden Codezeile klicken:

    `name += letters(i)`

    An der Stelle, an die Sie den Haltepunkt setzen, wird ein roter Kreis ![Haltepunkt](../../debugger/media/dbg-breakpoint.png "Haltepunkt") angezeigt.

    Haltepunkte sind ein einfaches und wichtiges Feature zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird.

2. Drücken Sie **F5**, oder klicken Sie auf die Schaltfläche **Debuggen starten**![Debuggen starten](../../debugger/media/dbg-tour-start-debugging.png "Debugging starten"). Daraufhin wird die App gestartet, und der Debugger führt den Code bis zu der Codezeile aus, in der Sie den Breakpoint festgelegt haben.

    ![Festlegen und Treffen eines Haltepunkts](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    Der gelbe Pfeil stellt die Anweisung dar, an der der Debugger angehalten hat. An der gleichen Stelle wird auch die Ausführung der App unterbrochen (diese Anweisung wurde noch nicht ausgeführt).

     Wenn die App noch nicht ausgeführt wird, kann der Debugger durch Drücken der Taste **F5** gestartet werden und hält am ersten Haltepunkt an. Andernfalls wird durch Drücken der Taste **F5** die Ausführung der App bis zum nächsten Haltepunkt fortgesetzt.

    Breakpoints sind eine nützliche Funktion, wenn Ihnen die Codezeile oder der Codeabschnitt bekannt ist, die bzw. den Sie genauer untersuchen möchten. Informationen zu den verschiedenen verfügbaren Typen von Haltepunkten, wie z. B. bedingte Haltepunkte, finden Sie unter [Verwenden von Haltepunkten im Visual Studio-Debugger](../../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navigieren durch Code im Debugger mithilfe von Schrittbefehlen

In der Regel verwenden wir an dieser Stelle Tastenkombinationen, da auf diese Weise eine schnelle Ausführung Ihrer App im Debugger möglich ist (entsprechende Befehle, wie z.B. Menübefehle, werden in Klammern angezeigt).

1. Drücken Sie zweimal **F11**, oder klicken Sie auf **Debuggen > Schrittweise ausführen**, während der Debugger in der `For`-Schleife der `Main`-Methode pausiert, damit der Debugger beim `SendMessage`-Methodenaufruf weiter ausgeführt wird.

     Nachdem Sie zweimal **F11** gedrückt haben, sollten Sie sich in dieser Codezeile befinden:

     `SendMessage(name, a(i))`

1. Drücken Sie noch mal **F11**, um die `SendMessage`-Methode schrittweise auszuführen.

     Daraufhin wechselt der gelbe Zeiger in die `SendMessage`-Methode.

     ![Verwenden von F11 für schrittweise Codeausführung](../visual-basic/media/get-started-f11-vb.png "Schrittweise ausführen (F10)")

     Durch Drücken der Taste F11 wird der Befehl **Einzelschritt** ausgeführt, und die App wird Anweisung für Anweisung ausgeführt. Das Drücken der Taste F11 bietet eine gute Möglichkeit, den Ausführungsablauf am ausführlichsten zu überprüfen. (Wenn Sie den Code schneller durchlaufen möchten, zeigen wir Ihnen auch einige andere Optionen.) Standardmäßig überspringt der Debugger Nichtbenutzercode (weitere Einzelheiten hierzu finden Sie unter [Nur eigenen Code](../../debugger/just-my-code.md)).

     Angenommen, Sie haben die Untersuchung der `SendMessage`-Methode abgeschlossen und möchten die Methode beenden, aber nicht den Debugger. Dies ist mit dem Befehl **Ausführen bis Rücksprung** möglich.

1. Drücken Sie **UMSCHALT** + **F11** (oder klicken Sie auf **Debuggen > Ausführen bis Rücksprung**).

     Mit diesem Befehl wird die Ausführung der App so lange fortgesetzt (und der Debugger weiter ausgeführt), bis die aktuelle Methode oder Funktion wieder ausgeführt wird.

     Der Debugger befindet sich nun wieder in der `For`-Schleife der `Main`-Methode und wurde beim Methodenaufruf von `SendMessage` angehalten.

1. Drücken Sie mehrmals auf **F11**, bis Sie noch mal zum Methodenaufruf von `SendMessage` gelangen.

1. Während der Debugger beim Methodenaufruf angehalten wurde, drücken Sie einmal auf **F10** (oder klicken Sie auf **Debuggen > Überspringen**).

     ![Verwenden von F10 für Prozedurschritt](../visual-basic/media/get-started-step-over-vb.png "Prozedurschritt (F10)")

     Beachten Sie, dass der Debugger dieses Mal die `SendMessage`-Methode nicht schrittweise ausführt. Durch Drücken der Taste **F10** fährt der Debugger in Ihrem App-Code fort, ohne dass Funktionen oder Methoden schrittweise ausgeführt werden (der Code wird immer noch ausgeführt). Durch Drücken von **F10** im `SendMessage`-Methodenaufruf (anstelle von **F11**) wurde der Implementierungscode für `SendMessage` übersprungen (der für uns gerade möglicherweise nicht von Interesse ist). Weitere Informationen zu den verschiedenen Möglichkeiten, durch den Code zu navigieren, finden Sie unter [Navigieren durch Code mit dem Visual Studio-Debugger](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Navigieren durch Code mithilfe von „Ausführung bis Klick“

1. Drücken Sie **F5**, um noch mal zum Haltepunkt zu springen.

1. Scrollen Sie im Code-Editor nach unten, und zeigen Sie mit dem Cursor so lange auf die `Console.WriteLine`-Methode in der `SendMessage`-Methode, bis links die grüne Schaltfläche **Run to Click** (Ausführung bis Klick) ![Symbol für „Ausführung bis Klick“](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") angezeigt wird. Die QuickInfo für die Schaltfläche zeigt „Ausführung bis hier ausführen“ an.

     ![Verwenden der Funktion „Ausführung bis Klick“](../visual-basic/media/get-started-run-to-click-vb.png "Ausführung bis Klick")

   > [!NOTE]
   > Die Schaltfläche **Ausführung bis Klick** ist neu in [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Wenn Ihnen die Schaltfläche mit dem grünen Pfeil nicht angezeigt wird, verwenden Sie in diesem Beispiel stattdessen die Taste **F11**, damit der Debugger an der richtigen Stelle fortfährt.

2. Klicken Sie auf die Schaltfläche **Ausführung bis Klick**![Ausführung bis Klick](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Daraufhin wechselt der Debugger zur `Console.WriteLine`-Methode.

    Die Verwendung dieser Schaltfläche ist mit dem Festlegen eines temporären Breakpoints vergleichbar. **Ausführung bis Klick** ist praktisch, um schnell durch einen sichtbaren Bereich mit App-Code zu navigieren (Sie können in eine beliebige geöffnete Datei klicken).

## <a name="restart-your-app-quickly"></a>Schnelles Neustarten Ihrer App

Klicken Sie auf der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**).

Durch das Klicken auf **Neu starten** sparen Sie im Vergleich zum Beenden der App und dem erneuten Starten des Debuggers Zeit. Der Debugger hält am ersten Breakpoint an, der bei der Codeausführung erreicht wird.

Der Debugger hält wieder an dem von Ihnen zuvor in der `For`-Schleife festgelegten Haltepunkt an.

## <a name="inspect-variables-with-data-tips"></a>Untersuchen von Variablen mithilfe von Datentipps

Funktionen, mit denen Sie Variablen untersuchen können, zählen zu den nützlichsten Funktionen des Debuggers. Es gibt verschiedene Möglichkeiten, Variablen zu untersuchen. Beim Debuggen eines Problems wird häufig versucht herauszufinden, ob Variablen die Werte speichern, die diese zu einem bestimmten Zeitpunkt erwartungsgemäß aufweisen.

1. Wenn der Debugger bei der `name += letters[i]`-Anweisung angehalten wurde, zeigen Sie auf die `letters`-Variable. Daraufhin wird Ihnen der Standardwert der Variablen angezeigt, bei dem es sich um den Wert des ersten Elements im Array `"f"c` handelt.

1. Zeigen Sie als Nächstes auf die `name`-Variable. Daraufhin wird Ihnen der aktuelle Variablenwert angezeigt: eine leere Zeichenfolge.

1. Drücken Sie mehrmals auf **F5** (oder **Debuggen** > **Weiter**), um mehrmals die `For`-Schleife zu durchlaufen. Dabei pausiert der Debugger jedes Mal am Haltepunkt, sodass Sie auf die `name`-Variable zeigen und ihren Wert überprüfen können.

     ![Einen Datentipp anzeigen](../visual-basic/media/get-started-data-tip-vb.png "Einen Datentipp anzeigen")

     Der Wert der Variable ändert sich bei jeder Iteration der `For`-Schleife, von `f` in `fr` in `fre` usw.

     Beim Debuggen möchten Sie häufig Eigenschaftswerte von Variablen schnell überprüfen können, um zu sehen, ob sie die Werte speichern, die sie speichern möchten. Die Datentipps sind eine gute Möglichkeit dafür.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Untersuchen von Variablen über die Fenster „Auto“ und „Lokal“

1. Schauen Sie sich das Fenster **Auto** unten im Code-Editor an.

    Falls dieses geschlossen ist, öffnen Sie es während einer Unterbrechung im Debugger. Klicken Sie dazu auf **Debuggen** > **Fenster** > **Auto**.

    Im Fenster **Auto** werden Ihnen Variablen und der zugehörige aktuelle Wert angezeigt. Im **Auto**-Fenster werden alle Variablen angezeigt, die auf der aktuellen Zeile oder der vorangehenden Zeile verwendet werden (lesen Sie dazu die Dokumentation für sprachspezifisches Verhalten).

1. Schauen Sie sich als Nächstes das Fenster **Lokal** auf einer Registerkarte neben dem Fenster **Auto** an.

1. Klappen Sie die `letters`-Variable auf, um die darin enthaltenen Elemente anzuzeigen.

     ![Untersuchen von Variablen im Fenster „Lokale Variablen“](../visual-basic/media/get-started-locals-window-vb.png "Lokalfenster")

    Im Fenster **Lokal** werden Ihnen die Variablen angezeigt, die sich im aktuellen [Bereich](https://www.wikipedia.org/wiki/Scope_(computer_science)) befinden, also im aktuellen Ausführungskontext.

## <a name="set-a-watch"></a>Festlegen von Überwachung

1. Klicken Sie im Hauptfenster des Code-Editors mit der rechten Maustaste auf die `name`-Variable, und wählen Sie **Überwachung hinzufügen** aus.

    Das Fenster **Überwachung** wird unten im Code-Editor geöffnet. Sie können über das Fenster **Überwachung** eine Variable (oder einen Ausdruck) angeben, die Sie im Auge behalten möchten.

    Nun haben Sie festgelegt, dass die `name`-Variable überwacht werden soll, und Sie können seine Wertänderung sehen, wenn Sie durch den Debugger navigieren. Im Gegensatz zu den anderen Variablenfenstern werden im Fenster **Überwachung** immer die Variablen angezeigt, die von Ihnen überwacht werden (wenn sie außerhalb des gültigen Bereichs liegen, sind sie ausgegraut).

## <a name="examine-the-call-stack"></a>Überprüfen der Aufrufliste

1. Klicken Sie, nachdem in der `For`-Schleife angehalten wurde, auf das Fenster **Aufrufliste**. Dieses Fenster ist standardmäßig im unteren rechten Bereich geöffnet.

    Falls dieses geschlossen ist, öffnen Sie es während einer Unterbrechung im Debugger. Klicken Sie dazu auf **Debuggen** > **Fenster** > **Aufrufliste**.

2. Drücken Sie einige Male die Taste **F11**, bis der Debugger bei der `SendMessage`-Methode anhält. Schauen Sie sich das Fenster **Aufrufliste** an.

    ![Untersuchen der Aufrufliste](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

    Im Fenster **Aufrufliste** wird die Reihenfolge angezeigt, in der Methoden und Funktionen aufgerufen werden. In der obersten Zeile wird die aktuelle Funktion (in dieser App die `SendMessage`-Methode) angezeigt. In der zweiten Zeile wird angezeigt, dass `SendMessage` über die `Main`-Methode aufgerufen wurde usw.

   > [!NOTE]
   > Das Fenster **Aufrufliste** ist mit der Debugperspektive in einigen IDEs wie Eclipse vergleichbar.

    Die Aufrufliste bietet eine nützliche Möglichkeit zum Untersuchen und Verstehen des Ausführungsablaufs einer App.

    Sie können auf eine Codezeile doppelklicken, um diesen Quellcode anzuzeigen. Dadurch wird auch der aktuelle Bereich geändert, der vom Debugger untersucht wird. Durch diese Aktion wird der Debugger nicht weiter ausgeführt.

    Sie können auch über die Kontextmenüs im Fenster **Aufrufliste** weitere Aktionen ausführen. So können Sie beispielsweise Haltepunkte in bestimmte Funktionen einfügen, den Debugger über **Ausführen bis Cursor** weiter ausführen und Quellcode untersuchen. Weitere Informationen finden Sie unter [View the call stack and use the Call Stack window in the debugger Examine the Call Stack (Vorgehensweise: Untersuchen der Aufrufliste)](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Ändern des Ausführungsablaufs

1. Drücken Sie zweimal auf **F11**, um die `Console.WriteLine`-Methode auszuführen.

1. Wenn der Debugger im Methodenaufruf von `SendMessage` angehalten wurde, ziehen Sie den gelben Pfeil (den Ausführungszeiger) mit der Maus nach links und um eine Zeile nach oben zurück zu `Console.WriteLine`.

1. Drücken Sie die Taste **F11**.

    Der Debugger führt die `Console.WriteLine`-Methode erneut aus (dies wird Ihnen in der Ausgabe im Konsolenfenster angezeigt).

    Durch Ändern des Ausführungsablaufs können Sie Aktionen ausführen wie das Testen verschiedener Pfade für die Codeausführung oder das erneute Ausführen von Code ohne Neustarten des Debuggers.

    > [!WARNING]
    > Bei dieser Funktion müssen Sie häufig vorsichtig vorgehen. Sie werden durch eine Warnung in der QuickInfo auf Probleme aufmerksam gemacht. Möglicherweise werden Ihnen auch andere Warnungen angezeigt. Durch das Verschieben des Zeigers können Sie Ihre Anwendung nicht auf einen früheren App-Status zurücksetzen.

1. Drücken Sie die Taste **F5**, um die Ausführung der App fortzusetzen.

    Damit haben Sie das Tutorial erfolgreich abgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie den Debugger starten, Code schrittweise durchlaufen und Variablen untersuchen. Sie sollten sich einen allgemeinen Überblick über die Debugger-Features verschaffen und die zugehörigen Links aufrufen, um weitere Informationen hierzu zu erhalten.

> [!div class="nextstepaction"]
> [Erster Einblick in den Debugger](../../debugger/debugger-feature-tour.md)
