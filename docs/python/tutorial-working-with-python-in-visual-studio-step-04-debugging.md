---
title: 'Tutorial „Python in Visual Studio“, Schritt 4: Debuggen'
titleSuffix: ''
description: Dies ist Schritt 4 einer grundlegenden Einführung in Python-Funktionen in Visual Studio, in der das Ausführen von Python-Code im Debugger erläutert wird.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a66268d5d6bd200eb3ef0e2c8bcf53471e3a735f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839162"
---
# <a name="step-4-run-code-in-the-debugger"></a>Schritt 4: Ausführen von Code im Debugger

**Vorheriger Schritt: [Verwenden des interaktiven REPL-Fensters](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Zusätzlich zum Verwalten von Projekten, das mit seinen umfassenden Bearbeitungsfunktionen sehr benutzerfreundlich ist, und dem **interaktiven** Fenster stellt Visual Studio umfassende Debuggingfunktionen für Python-Code bereit. Im Debugger können Sie den Code, einschließlich jeder Iteration einer Schleife, schrittweise ausführen. Sie können das Programm auch jederzeit anhalten, wenn bestimmte Bedingungen erfüllt sind. Wenn das Programm im Debugger angehalten wird, können Sie den gesamten Programmstatus zu jedem Zeitpunkt untersuchen und den Wert der Variablen ändern. Aktionen dieser Art sind für das Finden von Programmfehlern essentiell und stellen zudem sehr nützliche Hilfsmittel für die sorgfältige Befolgung des genauen Programmflusses bereit.

1. Ersetzen Sie den Code in der Datei *PythonApplication1.py* durch den folgenden Code. Durch diese Codevariation wird `make_dot_string` erweitert, damit Sie die zugehörigen separaten Schritte im Debugger untersuchen können. Zudem wird die `for`-Schleife in einer `main`-Funktion platziert und explizit durch den Aufruf dieser Funktion ausgeführt:

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(rad) + 20)          # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Überprüfen Sie, ob der Code ordnungsgemäß funktioniert, indem Sie **F5** drücken oder den Menübefehl **Debuggen** > **Debuggen starten** auswählen. Durch diesen Befehl wird der Code im Debugger ausgeführt. Da Sie jedoch keine Maßnahmen ergriffen haben, um das Programm während seiner Ausführung anzuhalten, werden nur Wellenmuster für ein paar Iterationen ausgegeben. Drücken Sie eine beliebige Taste, um das Ausgabefenster zu schließen.

    > [!Tip]
    > Klicken Sie auf die Menübefehle **Extras** > **Optionen**, erweitern Sie den Knoten **Python**, wählen Sie die Option **Debuggen** aus, und deaktivieren Sie dann die Option **Auf Eingabe warten, wenn der Prozess normal beendet wird**, um das Ausgabefenster automatisch zu schließen, wenn das Programm abgeschlossen ist:
    >
    > ![Python-Debugoption zum Schließen des Ausgabefensters bei normaler Beendigung des Programms](media/vs-getting-started-python-22-debugging5.png)

1. Legen Sie in der `for`-Anweisung einen Haltepunkt fest, indem Sie auf den grauen Rand dieser Zeile klicken oder das Caretzeichen in dieser Zeile platzieren und den Befehl **Debuggen** > **Haltepunkt ein/aus** (**F9**) ausführen. Auf dem grauen Rand erscheint ein roter Punkt, der den Haltepunkt kennzeichnet (siehe Pfeil unten):

    ![Festlegen eines Haltepunkts](media/vs-getting-started-python-18-debugging1.png)

1. Starten Sie den Debugger erneut (**F5**), und Sie sehen, dass die Codeausführung in der Zeile mit diesem Haltepunkt stoppt. Hier können Sie die Aufrufliste und Variablen überprüfen. Im Bereich liegende Variablen werden im **Auto**-Fenster angezeigt, wenn sie definiert sind; Sie können auch zur Ansicht **Lokal** am unteren Rand des Fensters wechseln, um sämtliche Variablen anzuzeigen, die Visual Studio auch vor ihrer Definition im aktuellen Bereich (Funktionen inbegriffen) finden kann:

    ![Haltepunkt-Benutzeroberfläche für Python](media/vs-getting-started-python-19-debugging2b.png)

1. Beachten Sie die Symbolleiste „Debuggen“ (siehe unten) am oberen Rand des Visual Studio-Fensters. Diese Symbolleiste bietet schnellen Zugriff auf die am häufigsten verwendeten Befehle zum Debuggen (diese können auch im Menü **Debuggen** gefunden werden):

    ![Wichtige Debugging-Symbolleistenschaltflächen](media/vs-getting-started-python-20-debugging3.png)

    Von links nach rechts betrachtet lauten die Schaltflächen wie folgt:
    - **Fortfahren** (**F5**): Führt das Programm bis zum nächsten Haltepunkt oder bis zur Beendigung des Programms aus.
    - **Alle unterbrechen** (**STRG**+**ALT**+**UNTBR**): Hält ein Programm mit langer Ausführungszeit an.
    - **Debuggen beenden** (**UMSCHALT**+**F5**): Stoppt das Programm an einer beliebigen Stelle und beendet den Debugger.
    - **Neu starten** (**STRG**+**UMSCHALT**+**F5**): Stoppt das Programm an einer beliebigen Stelle und startet es im Debugger neu.
    - **Nächste Anweisung anzeigen** (**ALT**+**NUM** **&#42;**): Wechselt zur nächsten auszuführenden Codezeile. Dies ist besonders hilfreich, wenn Sie während einer Debugsitzung durch Ihren Code navigieren und schnell zu dem Punkt zurückkehren möchten, an dem der Debugger angehalten wurde.
    - **Schrittweise ausführen** (**F11**): Führt die nächste Codezeile aus und wechselt zu aufgerufenen Funktionen.
    - **Überspringen** (**F10**): Führt die nächste Codezeile aus, ohne zu aufgerufenen Funktionen zu wechseln.
    - **Rücksprung** (**UMSCHALT**+**F11**): Führt den Rest der aktuellen Funktion aus und wird im aufrufenden Code angehalten.

1. Überspringen Sie die `for`-Anweisung mithilfe der Schaltfläche **Überspringen**. *Stepping* bedeutet, dass der Debugger die aktuelle Codezeile einschließlich sämtlicher Funktionsaufrufe ausführt und anschließend sofort angehalten wird. Beachten Sie, wie die Variable `i` jetzt in den Fenstern **Lokal** und **Auto** definiert ist.

1. Überspringen Sie die nächste Codezeile, in der `make_dot_string` aufgerufen wird und die angehalten wird. **Überspringen** bedeutet hier insbesondere, dass der Debugger die gesamte Variable `make_dot_string` ausführt und bei der Rückgabe angehalten wird. Der Debugger wird nicht innerhalb dieser Funktion beendet, es sei denn, in dieser Funktion ist ein separater Haltepunkt vorhanden.

1. Überspringen Sie den Code mehrmals, und beobachten Sie, wie sich die Werte im Fenster **Lokal** oder **Auto** ändern.

1. Doppelklicken Sie im Fenster **Lokal** oder **Auto** in die Spalte **Wert** der `i`- oder `s`-Variablen, um den Wert zu bearbeiten. Drücken Sie die **EINGABETASTE**, oder klicken Sie auf einen beliebigen Bereich außerhalb dieses Werts, damit alle Änderungen übernommen werden.

1. Fahren Sie mithilfe von **Schrittweise ausführen** mit der ausführlichen Ausführung des Codes fort. **Schrittweise ausführen** bedeutet, dass der Debugger zu einem beliebigen Funktionsaufruf wechselt, zu dem ihm Debuginformationen vorliegen, z.B. `make_dot_string`. Wenn Sie sich in `make_dot_string` befinden, können Sie die zugehörigen lokalen Variablen untersuchen und den zugehörigen Code gezielt durchlaufen.

1. Fahren Sie mit der **schrittweisen Ausführung** fort, und beachten Sie, dass bei Erreichen des Endes von `make_dot_string` der nächste Schritt an die `for`-Schleife mit dem neuen Rückgabewert in der `s`-Variablen zurückgegeben wird. Beachten Sie bei der ausführlichen Ausführung der `print`-Anweisung, dass **Schrittweise ausführen** bei `print` nicht zu dieser Funktion wechselt. Grund hierfür ist, dass `print` nicht in Python geschrieben wurde, sondern es sich vielmehr um nativen Code in der Python-Laufzeit handelt.

1. Fahren Sie mit der Verwendung von **Schrittweise ausführen** fort, bis Sie sich erneut in `make_dot_string` befinden. Verwenden Sie anschließend **Rücksprung**, und achten Sie darauf, dass Sie zur `for`-Schleife zurückkehren. Über die Schaltfläche **Rücksprung** führt der Debugger den Rest der Funktion aus und wird anschließend automatisch im aufrufenden Code angehalten. Dies ist sehr hilfreich, wenn Sie einen Abschnitt einer langen Funktion schrittweise ausgeführt haben, die Sie debuggen möchten, den Rest jedoch nicht schrittweise ausführen möchten und im aufrufenden Code keinen expliziten Haltepunkt festlegen möchten.

1. Über die Schaltfläche **Fortfahren** (**F5**) können Sie die Ausführung des Programms fortsetzen, bis der nächste Haltepunkt erreicht ist. Da Sie in der `for`-Schleife einen Haltepunkt festgelegt haben, kommt es bei der nächsten Iteration zum Halt.

1. Die ausführliche Ausführung von Hunderten von Iterationen einer Schleife kann mühsam sein. Daher können Sie in Visual Studio eine *Bedingung* zu einem Haltepunkt hinzufügen. Der Debugger hält das Programm nur dann am Haltepunkt an, wenn die Bedingung erfüllt ist. So können Sie beispielsweise in der `for`-Anweisung eine Bedingung mit dem Haltepunkt verwenden, damit das Programm nur dann angehalten wird, wenn der Wert von `i` 1600 überschritten wird. Klicken Sie zum Festlegen einer Bedingung mit der rechten Maustaste auf den roten Punkt, der den Haltepunkt markiert, und wählen Sie **Bedingungen** (**ALT**+**F9** > **C**) aus. Geben Sie im Popupmenü **Haltepunkteinstellungen**, das angezeigt wird, `i > 1600` als Ausdruck ein, und wählen Sie **Schließen** aus. Drücken Sie zum Fortfahren auf **F5**, und beobachten Sie, ob das Programm vor dem nächsten Haltepunkt viele Iterationen ausführt.

    ![Festlegen einer Haltepunktbedingung](media/vs-getting-started-python-21-debugging4.png)

1. Wenn Sie das Programm bis zum Ende ausführen möchten, deaktivieren Sie den Haltepunkt, indem Sie mit der rechten Maustaste auf den Punkt im Rand klicken und **Haltepunkt deaktivieren** (**STRG**+**F9**) auswählen. Wählen Sie anschließend **Weiter** aus (oder drücken Sie **F5**), um das Programm auszuführen. Wenn das Programm beendet wird, beendet Visual Studio die zugehörige Debugsitzung und versetzt sie wieder in den Bearbeitungsmodus. Beachten Sie, dass Sie den Haltepunkt auch löschen können, indem Sie den Punkt auswählen, oder indem Sie mit der rechten Maustaste auf den Punkt klicken und **Haltepunkt löschen** auswählen. Dadurch werden jedoch auch alle von Ihnen festgelegten Bedingungen gelöscht.

> [!Tip]
> In einigen Situationen, z.B. bei Auftreten eines Fehlers beim Starten des Python-Interpreters, erscheint das Fenster „Ausgabe“ möglicherweise nur kurz und wird anschließend automatisch geschlossen, ohne dass Sie die Möglichkeit haben, Fehlermeldungen anzuzeigen. Klicken Sie in einem solchen Fall mit der rechten Maustaste im **Projektmappen-Explorer** auf das Projekt, wählen Sie **Eigenschaften** und die Registerkarte **Debuggen** aus, und fügen Sie anschließend `-i` zum Feld **Interpreterargumente** hinzu. Durch dieses Argument wird der Interpreter nach Abschluss des Programms in den interaktiven Modus versetzt. Das Fenster bleibt dabei geöffnet, bis Sie **STRG**+**Z** > **EINGABETASTE** zum Beenden drücken.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Installieren von Paketen in Ihrer Python-Umgebung](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Debuggen](debugging-python-in-visual-studio.md)
- Die vollständige Dokumentation zu Debugfeatures von Visual Studio finden Sie unter [Debugging in Visual Studio](../debugger/debugger-feature-tour.md).
