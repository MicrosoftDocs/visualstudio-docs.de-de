---
title: 'Tutorial: Erste Schritte mit R'
description: Exemplarische Vorgehensweise zur Verwendung von R in Visual Studio, einschließlich Projekterstellung, interaktivem Fenster, Codebearbeitung und Debuggen.
ms.date: 06/29/2017
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8be766e078a04d713ed69aa0b9cc464433dcb73d
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761393"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Erste Schritte mit R Tools für Visual Studio

Sobald Sie R Tools für Visual Studio (RTVS) installiert haben (siehe [Installation](installing-r-tools-for-visual-studio.md)), erhalten Sie schnell einen Vorgeschmack der Funktionalität, die diese Tools bieten.

## <a name="create-an-r-project"></a>Erstellen eines R-Projekts

1. Öffnen Sie Visual Studio.
1. Klicken Sie auf **Datei** > **Neu** > **Projekt** (**STRG**+**UMSCHALTTASTE**+**N**).
1. Wählen Sie unter **Vorlagen** > **R** „R-Projekt“ aus, weisen Sie dem Projekt einen Namen und Speicherort zu, und klicken Sie auf **OK**:

   ![Dialogfeld „Neues Projekt“ für R in Visual Studio (RTVS in VS2017)](media/getting-started-01-new-project.png)

1. Sobald das Projekt erstellt wurde, sehen Sie die folgenden Fenster:

    - Auf der rechten Seite ist der Visual Studio-Projektmappen-Explorer dargestellt, in dem Sie Ihr Projekt innerhalb einer *Projektmappe* sehen. (Projektmappen können eine beliebige Anzahl von Projekten verschiedenen Typs enthalten. Informationen finden Sie unter [Projekte](r-projects-in-visual-studio.md).)
    - Oben links befindet sich eine neue R-Datei (`script.R`), wobei Sie Quellcode mit allen Bearbeitungsfunktionen von Visual Studio bearbeiten können.
    - Unten links sehen Sie das Fenster **R Interactive**, in dem Sie Code interaktiv entwickeln und testen können.

> [!Note]
> Sie können das **R Interactive**-Fenster verwenden, selbst wenn Sie keine Projekte geöffnet haben und auch wenn ein anderer Projekttyp geladen wird. Klicken Sie einfach bei Bedarf auf **R Tools** > **Fenster** > **R Interactive**.

## <a name="explore-the-interactive-window-and-intellisense"></a>Kennenlernen des R Interactive-Fensters und IntelliSense

1. Überprüfen Sie, ob das interaktive Fenster funktioniert, indem Sie `3 + 4` eingeben und dann die **EINGABETASTE** drücken, um das Ergebnis anzuzeigen:

    ![„R Interactive“-Fenster in Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Geben Sie etwas komplizierteres ein, `ds <- c(1.5, 6.7, 8.9) * 1:12`, und geben Sie `ds` ein, um das Ergebnis anzuzeigen:

    ![Zusätzliches interaktives Beispiel für R in Visual Studio](media/getting-started-03-interactive2.png)

1. Geben Sie `mean(ds)` ein, beachten Sie jedoch, dass sobald Sie `m` oder `me` eingeben, Visual Studio IntelliSense Optionen zur automatischen Vervollständigung bereitstellt. Wenn die gewünschte Vervollständigung in der Liste ausgewählt ist, drücken Sie die **TAB-TASTE**, um sie einzufügen. Sie können zudem Ihre Auswahl mit den Pfeiltasten oder der Maus bearbeiten.

    ![IntelliSense erscheint, wenn Sie Code eingeben](media/getting-started-04-intellisense1.png)

1. Nachdem Sie `mean` abgeschlossen haben, geben Sie die öffnende Klammer `(` ein, und achten Sie darauf, wie IntelliSense Ihnen Inline-Hilfe für die Funktion bietet:

    ![IntelliSense gibt Hilfestellung für eine Funktion](media/getting-started-05-intellisense2.png)

1. Schließen Sie die Zeile `mean(ds)` ab, und drücken Sie die EINGABETASTE, um das Ergebnis anzuzeigen (`[1] 39.51667`).

1. Das „Interactive“-Fenster wird mit Hilfe integriert, weshalb bei der Eingabe von `?mean` die Hilfe für diese Funktion im Fenster **R-Hilfe** in Visual Studio angezeigt wird. Weitere Informationen finden Sie unter [Help in R Tools for Visual Studio (Hilfe in R-Tools für Visual Studio)](getting-started-help.md).

    ![Fenster „R-Hilfe“ in Visual Studio](media/getting-started-06-help.png)

1. Einige Befehle, z.B. `plot(1:100)`, öffnen ein neues Fenster in Visual Studio, wenn die Ausgabe nicht direkt im interaktiven Fenster angezeigt werden kann:

    ![Screenshot eines Visual Studio R-Plotfensters, das die Ausgabe der graph-Funktion plot(1:100) zeigt.](media/getting-started-07-plot-window.png)

Mit dem interaktiven Fenster können Sie auch Ihre Versionsgeschichte überprüfen, Arbeitsbereiche laden und speichern, an den Debugger anfügen sowie mit Quellcodedateien interagieren, anstatt Kopieren und Einfügen zu verwenden. Weitere Informationen finden Sie unter [Arbeiten mit dem interaktiven R-Fenster](interactive-repl-for-r-in-visual-studio.md).

## <a name="experience-code-editing-features"></a>Features zur Codebearbeitung

Durch die kurze Arbeit mit dem interaktiven Fenster haben Sie grundlegende Bearbeitungsfunktionen kennengelernt, z.B. IntelliSense, die auch im Code-Editor funktionieren. Wenn Sie denselben Code wie zuvor eingeben, erhalten Sie die gleichen Aufforderungen für die automatische Vervollständigung und IntelliSense, jedoch nicht die Ausgabe.

Durch das Schreiben von Code in eine *R*-Datei können Sie Ihren gesamten Code auf einmal anzeigen und dadurch einfacher kleine Änderungen vornehmen. Dann können Sie die Ergebnisse schnell anzeigen, indem Sie den Code im interaktiven Fenster ausführen. Außerdem können Sie so viele Dateien in einem Projekt haben, wie Sie möchten. Wenn sich Code in einer Datei befindet, können Sie ihn auch im Debugger schrittweise ausführen (später in diesem Artikel beschrieben). Diese Funktionen sind sehr hilfreich, wenn es um das Entwickeln von Computeralgorithmen und das Schreiben von Code zum Bearbeiten von einem oder mehreren Datasets geht, besonders, wenn Sie alle Zwischenergebnisse untersuchen möchten.

Als Beispiel erstellen die folgenden Schritte einen kleinen Code zum Erforschen des [Zentralen Grenzwertsatzes](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). (Dieses Beispiel ist aus dem *R Cookbook* von Paul Teetor abgeleitet.)

1. Geben Sie im `script.R`-Editor den folgenden Code ein:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Wenn Ergebnisse schnell angezeigt werden sollen, wählen Sie den gesamten Code aus (**STRG**+**A**), drücken Sie **STRG**+**EINGABETASTE**, oder führen Sie einen Rechtsklick aus, und wählen Sie **Interaktiv ausführen** aus. Der gesamte ausgewählte Code wird im interaktiven Fenster ausgeführt, so als hätten Sie ihn manuell eingegeben, und das Ergebnis wird in einem Plotfenster angezeigt:

    ![Screenshot eines Visual Studio R-Plotfensters, das einen Graph der Bevölkerungsdichte zeigt.](media/getting-started-08-plot1.png)

1. Für eine einzelne Zeile drücken Sie einfach bei Bedarf **STRG**+**EINGABETASTE**, um diese im interaktiven Fenster auszuführen.

> [!Tip]
> Lernen Sie die Muster kennen, mit denen Sie Bearbeitungen durchführen und **STRG**+**EINGABETASTE** drücken (oder alles mit **STRG**+**A** auswählen und danach **STRG**+**EINGABETASTE** drücken), um den Code schnell auszuführen. Das ist viel effizienter, als wenn Sie für denselben Vorgang die Maus verwenden.
>
> Sie können zusätzlich das Plotfenster durch Drag & Drop aus dem Visual Studio-Rahmen nehmen und es beliebig auf Ihrem Bildschirm platzieren. Sie können dann die Größe des Plotfensters wie gewünscht ändern und es dann in einer Bild- oder PDF-Datei speichern.

1. Fügen Sie weitere Codezeilen hinzu, um einen zweiten Plot einzuschließen:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Drücken Sie erneut **STRG**+**A** und **STRG**+**EINGABETASTE**, um den Code auszuführen, sodass folgendes Ergebnis erzeugt wird:

    ![Aktualisierter dualer Plot in Visual Studio](media/getting-started-09-plot2.png)

1. Das Problem ist, dass der erste Plot die vertikale Skala bestimmt, weshalb der zweite Plot (mit `lines`) nicht passt. Sie müssen den `ylim`-Parameter auf dem `plot`-Aufruf festlegen, um dieses Problem zu beheben, aber Sie müssen für eine ordnungsgemäße Ausführung Code hinzufügen, um den maximalen vertikalen Wert zu berechnen. Dies Zeile für Zeile im interaktiven Fenster auszuführen, ist umständlich, da Sie den Code neu anordnen müssen, um `samp.means` zu verwenden, bevor Sie `plot` aufrufen. In einer Codedatei können Sie jedoch einfach die geeigneten Bearbeitungen ausführen:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. Drücken Sie wieder **STRG**+**A** und **STRG**+**EINGABETASTE**, um das Ergebnis anzuzeigen:

    ![Aktualisierter dualer Plot in Visual Studio, richtig skaliert](media/getting-started-10-plot3.png)

Sie können noch viel mehr im Editor tun. Weitere Informationen finden Sie unter [Editing R code (Bearbeiten von R-Code)](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md) und [Code snippets (Codeausschnitte)](code-snippets-for-r.md).

## <a name="debug-your-code"></a>Debuggen Ihres Codes

Eine der größten Stärken von Visual Studio ist die Debugger-Benutzeroberfläche. RTVS ist auf dieser starken Grundlage aufgebaut und kommt mit einer innovativen Benutzeroberfläche wie dem [Variablen-Explorer](variable-explorer.md). Fangen Sie nun mit dem Debuggen an.

1. Wenn Sie starten möchten, setzen Sie den aktuellen Arbeitsbereich zurück, um alles, was Sie bisher gemacht haben, zu löschen. Hierzu verwenden Sie den Menübefehl **R Tools** > **Sitzung** > **Zurücksetzen**. Standardmäßig wird alles, was Sie im interaktiven Fenster tun, in die aktuelle Sitzung übertragen, die dann auch vom Debugger verwendet wird. Durch das Zurücksetzen der Sitzung stellen Sie sicher, dass die Debugsitzung ohne bereits vorhandene Daten beginnt. Der Befehl **Zurücksetzen** beeinträchtigt jedoch nicht die Quelldatei *script.R*, da diese außerhalb des Arbeitsbereichs verwaltet und gespeichert wird.

1. Mit der im vorherigen Abschnitt erstellten Datei *script.R* legen Sie einen Breakpoint auf der Zeile fest, die mit `pop <-` beginnt, indem Sie das Caretzeichen auf dieser Zeile platzieren und **F9** drücken. Alternativ können Sie auch den Menübefehl **Debuggen** > **Toggle Breakpoint** (Breakpoint umschalten) auswählen. Alternativ können Sie auf den linken Rand (oder den Bundsteg) für diese Zeile klicken, wo sich der rote Punkt befindet, der den Haltepunkt anzeigt:

    ![Festlegen eines Haltepunkts im Editor](media/getting-started-11-debug1.png)

1. Starten Sie den Debugger mit dem Code in *script.R*, indem Sie entweder die Schaltfläche **Source startup file** (Quellstartdatei) auf der Symbolleiste verwenden, im Menü auf **Debuggen** > **Source startup file** (Quellstartdatei) klicken oder **F5** drücken. Visual Studio wird in den Debugmodus versetzt und beginnt damit, den Code auszuführen. Visual Studio hält jedoch auf der Zeile an, auf der Sie den Haltepunkt festgelegt haben.

    ![Anhalten am Haltepunkt im Visual Studio-Debugger](media/getting-started-12-debug2.png)

1. Während des Debuggens bietet Visual Studio die Möglichkeit, den Code zeilenweise durchzugehen. Sie können auch in Funktionen hineingehen, diese überspringen, oder aus ihnen heraus in den Aufrufkontext gehen. Diese Funktionen können – zusammen mit anderen – im Menü **Debuggen** im Kontextmenü im Editor gefunden werden, das Sie mit einem Rechtsklick öffnen, sowie in der Symbolleiste „Debuggen“:

    ![Symbolleiste „Debuggen“ in Visual Studio](media/getting-started-13-debug3.png)

1. Wenn an einem Haltepunkt angehalten wird, können Sie die Werte von Variablen untersuchen. Finden Sie das **Auto**-Fenster in Visual Studio, und wählen Sie die Registerkarte am unteren Rand mit dem Namen **Locals** (Lokale) aus. Das Fenster **Locals** (Lokale) zeigt lokale Variablen im Programm zum aktuellen Zeitpunkt an. Wenn Sie am zuvor festgelegten Haltepunkt angehalten haben, sehen Sie, dass die `pop`-Variable noch nicht definiert ist. Verwenden Sie nun den Befehl **Debuggen** > **Prozedurschritt** (**F10**). Anschließend wird der Wert für `pop` angezeigt:

    ![Fenster „R-Hilfe“ in Visual Studio](media/getting-started-14-debug4.png)

1. Um Variablen in unterschiedlichen Bereichen, einschließlich des globalen Bereichs und der Paketbereiche, zu untersuchen, können Sie den [Variablen-Explorer](variable-explorer.md) verwenden. Mithilfe des Variablen-Explorers können Sie auch in eine Tabellenansicht mit sortierbaren Spalten wechseln und Daten in eine CSV-Datei exportieren.

    ![Erweiterte Ansicht des Variablen-Explorers](media/variable-explorer-expanded-results.png)

1. Sie können weiter das Programm Zeile für Zeile durchlaufen oder auf **Fortsetzen** (**F5**) klicken, um es vollständig auszuführen (oder um zum nächsten Breakpoint zu gelangen).

Ausführlichere Details finden Sie unter [Debugging](debugging-r-in-visual-studio.md) und [Variable Explorer (Variablen-Explorer)](variable-explorer.md).

## <a name="next-steps"></a>Nächste Schritte

In dieser exemplarischen Vorgehensweise haben Sie die Grundlagen von R-Projekten, die Verwendung des interaktiven Fensters, die Codebearbeitung und das Debuggen in Visual Studio kennengelernt. Um weitere Funktionen kennenzulernen, sehen Sie sich die folgenden Artikel sowie Artikel an, die im Inhaltsverzeichnis aufgeführt sind:

- [Beispielprojekte](getting-started-samples.md)
- [Bearbeiten von Code](editing-r-code-in-visual-studio.md)
- [Debuggen](debugging-r-in-visual-studio.md)
- [Arbeitsbereiche](r-workspaces-in-visual-studio.md)
- [Visualisieren von Daten](visualizing-data-with-r-in-visual-studio.md)
