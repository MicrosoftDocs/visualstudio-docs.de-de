---
title: 'Tutorial „Python in Visual Studio“, Schritt 3: Interaktive REPL'
titleSuffix: ''
description: Dies ist Schritt 3 einer grundlegenden Einführung in Python-Funktionen in Visual Studio, in der das interaktive Python-REPL-Fenster erläutert wird.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c4ae447976798372e049df46552f8383389f7b3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920776"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Schritt 3: Verwenden des interaktiven REPL-Fensters

**Vorheriger Schritt: [Schreiben und Ausführen von Code](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

In Visual Studio bietet das **interaktive Fenster** für Python eine komfortable „Lesen-Auswerten-Ausgeben“-Schleife (REPL), die den üblichen „Bearbeiten-Erstellen-Debuggen“-Zyklus erheblich verkürzt. Das **interaktive** Fenster bietet alle Funktionen, die auch die REPL für die Python-Befehlszeile bietet. Es erleichtert auch das Austauschen von Code durch Quelldateien im Visual Studio-Editor, was über die Befehlszeile aufwändig wäre.

> [!NOTE]
> Bei Problemen mit REPL stellen Sie sicher, dass die Pakete `ipython` und `ipykernel` installiert sind, und Hilfe bei der Installation von Paketen finden Sie auf der Registerkarte [Python-Umgebungspakete](./python-environments-window-tab-reference.md#packages-tab).

1. Öffnen Sie das **interaktive** Fenster, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Python-Umgebung des Projekts klicken (z.B. **Python 3.6 (32-Bit)** , wie zuvor in einer Grafik gezeigt) und **Interaktives Fenster öffnen** auswählen. Alternativ können Sie im Hauptmenü von Visual Studio **Ansicht** > **Weitere Fenster** > **Interaktive Python-Fenster** auswählen.

1. Das **interaktive** Fenster wird unterhalb des Editors mit der standardmäßigen **>>>** -Python-REPL-Eingabeaufforderung geöffnet. In der Dropdownliste **Umgebung** können Sie einen bestimmten Interpreter für die Bearbeitung auswählen. Wenn Sie auch das **interaktive** Fenster vergrößern möchten, ziehen Sie die Trennlinie zwischen den beiden Fenstern in die entsprechende Richtung:

    ![Größe des interaktiven Python-Fensters durch Ziehen ändern](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Sie können die Größe aller Fenster in Visual Studio durch Verschieben der aneinander grenzenden Trennlinien verändern. Sie können auch Fenster aus dem Visual Studio-Rahmen herausziehen und sie dann innerhalb des Rahmens nach Ihren Wünschen anordnen. Ausführliche Informationen finden Sie unter [Anpassen der Fensterlayouts](../ide/customizing-window-layouts-in-visual-studio.md).

1. Geben Sie einige Anweisungen wie `print("Hello, Visual Studio")` und Ausdrücke wie `123/456` ein, um sofortige Ergebnisse anzuzeigen:

    ![Sofortige Ergebnisse im interaktiven Python-Fenster](media/vs-getting-started-python-12-interactive2.png)

1. Beim Schreiben einer mehrzeiligen Anweisung, wie einer Funktionsdefinition, wird im **interaktiven** Fenster die Python-Eingabeaufforderung **...** zum Fortsetzen der Zeilen angezeigt, die im Gegensatz zur Befehlszeilen-REPL automatischen Einzug bietet:

    ![Interaktives Python-Fenster mit Anweisungsfortsetzung](media/vs-getting-started-python-13-interactive3.png)

1. Das **interaktive** Fenster enthält einen vollständigen Verlauf aller Elemente, die Sie eingegeben haben, und verbessert das Befehlszeilen-REPL mit mehrzeiligen Verlaufselementen. Beispielsweise können Sie einfach die vollständige Definition der `f`-Funktion als einzelne Einheit zurückrufen und den Namen mühelos in `make_double` ändern, anstatt die Funktion Zeile für Zeile neu erstellen zu müssen.

1. Visual Studio kann mehrere Codezeilen aus einem Editor-Fenster an das **interaktive** Fenster senden. Mithilfe dieser Funktion können Sie Code in einer Quelldatei pflegen und ausgewählte Teile davon mühelos an das **interaktive** Fenster senden. Sie können dann mit solchen Codefragmenten in der schnellen REPL-Umgebung arbeiten, anstatt das gesamte Programm ausführen zu müssen. Um dieses Feature anzuzeigen, ersetzen Sie zunächst in der Datei *PythonApplication1.py* die Schleife `for` durch Folgendes:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Wählen Sie die Funktionsanweisungen `import`, `from` und `make_dot_string` in der *PY*-Datei aus. Klicken Sie mit der rechten Maustaste auf den ausgewählten Text, und wählen Sie **An interaktives Fenster senden** aus (oder drücken Sie **STRG**+**EINGABETASTE**). Das Codefragment wird direkt in das **interaktive** Fenster eingefügt und ausgeführt. Da der Code eine Funktion definiert hat, können Sie diese Funktion schnell testen, indem Sie sie mehrmals aufrufen:

    ![Code an das interaktive Fenster senden und diesen testen](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Wenn Sie im Editor **STRG**+**EINGABE** drücken, *ohne* eine Auswahl getroffen zu haben, wird die aktuelle Codezeile im **interaktiven** Fenster ausgeführt und die Einfügemarke automatisch in der nächsten Zeile positioniert. Mithilfe dieses Features können Sie durch wiederholtes Drücken von **STRG**+**EINGABE** auf einfache Weise schrittweise durch den Code gehen, was über die Python-Befehlszeile allein nicht möglich ist. Darüber hinaus können Sie damit schrittweise durch den Code gehen, ohne den Debugger auszuführen und ohne Ihr Programm vom Programmanfang neu starten zu müssen.

1. Sie können auch mehrzeiligen Code aus beliebigen Quellen kopieren und in das **interaktive** Fenster einfügen, z.B. den Codeausschnitt unten, was sich über die Python-Befehlszeilen-REPL schwierig gestaltet. Nach dem Einfügen führt das **interaktive** Fenster diesen Code genau so aus, wie wenn Sie ihn eingegeben hätten:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Einfügen von mehrere Codezeilen mit „An Interactive senden“](media/vs-getting-started-python-15-interactive5.png)

1. Wie Sie sehen, funktioniert dieser Code ordnungsgemäß, wird aber in nicht sehr ansprechender Form ausgegeben. Beim Verwenden eines anderen Schrittwerts in der `for`-Schleife würde die Kosinuswelle detaillierter angezeigt werden. Da sich die ganze `for`-Schleife als einzelne Einheit im REPL-Verlauf befindet, können Sie praktischerweise einfach zurückgehen, beliebige Änderungen vornehmen und die Funktion dann erneut testen. Drücken Sie zunächst die NACH-OBEN-TASTE, um die `for`-Schleife zurückzurufen. Drücken Sie dann entweder die NACH-LINKS-TASTE oder die NACH-RECHTS-TASTE, um im Code zu navigieren. Andernfalls wird mithilfe von NACH-OBEN und der NACH-UNTEN-TASTE weiterhin der Verlauf durchgegangen. Navigieren Sie zur gewünschten Stelle, und ändern Sie die `range`-Spezifikation in `range(0, 360, 12)` um. Drücken Sie danach an einer beliebigen Stelle im Code **STRG**+**EINGABE**, um die gesamte Anweisung erneut auszuführen:

    ![Eine vorherige Anweisung im interaktiven Fenster bearbeiten](media/vs-getting-started-python-16-interactive6.png)

1. Probieren Sie durch Wiederholen des Vorgangs verschiedene Schritteinstellungen aus, bis Sie den Wert gefunden haben, der für Sie am besten ist. Sie können auch veranlassen, dass die Welle wiederholt wird, indem Sie deren Bereich erweitern, z.B. `range(0, 1800, 12)`.

1. Wenn Sie zufrieden sind mit dem Code, den Sie im **Interactive-Fenster** geschrieben haben, wählen Sie ihn aus. Klicken Sie dann mit der rechten Maustaste auf den Code, und wählen Sie **Code kopieren** aus (**STRG**+**UMSCHALTTASTE**+**C**). Fügen Sie abschließend den ausgewählten Code in den Editor ein. Durch diese besondere Funktion werden in Visual Studio sowohl sämtliche Ausgaben als auch die Eingabeaufforderungen `>>>` und `...` automatisch ausgelassen. Die folgende Abbildung zeigt z.B. das Verwenden des **Code kopieren**-Befehls bei einer Auswahl, die Eingabeaufforderungen und Ausgaben enthält:

    ![Befehl „Code kopieren“ im interaktiven Fenster auf Auswahl mit Eingabeaufforderungen und Ausgaben anwenden](media/vs-getting-started-python-17-interactive7.png)

    Wenn Sie etwas in den Editor einfügen, wird nur der Code eingefügt:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Wenn Sie den exakten Inhalt des **interaktiven** Fensters kopieren möchten, einschließlich der Eingabeaufforderungen und Ausgaben, verwenden Sie einfach den Standardbefehl **Kopieren**.

1. Gerade haben Sie somit die schnelle REPL-Umgebung des **interaktiven** Fensters verwendet, um die Details für einen kleinen Abschnitt im Code zu erarbeiten. Danach haben Sie diesen Code bequem zur Quelldatei des Projekts hinzugefügt. Wenn Sie nun den Code mit **STRG**+**F5** (oder **Debuggen** > **Ohne Debugging starten**) erneut ausführen, werden Ihnen die gewünschten exakten Ergebnisse angezeigt.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Ausführen von Code im Debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Verwenden des interaktiven Fensters](python-interactive-repl-in-visual-studio.md)
- [Verwenden von IPython REPL](interactive-repl-ipython.md)