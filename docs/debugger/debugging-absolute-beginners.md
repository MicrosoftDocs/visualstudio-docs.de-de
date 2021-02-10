---
title: Debuggen von Code für Einsteiger
description: Wenn Sie den Debugger zum ersten Mal verwenden, sollten Sie sich mit einigen Grundsätzen auseinandersetzen, die beim Ausführen Ihrer App im Debugmodus mit Visual Studio nützlich sind.
ms.date: 02/14/2020
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fbb99d2b41a8a354ec450e99dab13efb6ec60248
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872923"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Debuggen für Einsteiger

Der Code, den wir als Softwareentwickler schreiben, verhält sich zweifellos nicht immer wie erwartet. Manchmal verhält er sich sogar völlig anders. In diesem Fall müssen Sie herausfinden, warum der Code sich anders verhält. Hierfür können Sie den Code zwar aufwändig durchgehen, es ist jedoch einfacher und effizienter, ein Tool dafür zu verwenden – den Debugger.

Ein Debugger kann jedoch leider nicht alle Probleme oder Fehler im Code erkennen. *Debuggen* bedeutet, dass Sie Ihren Code schrittweise in einem entsprechenden Tool wie Visual Studio ausführen, um die Stelle zu finden, an der Sie einen Fehler beim Programmieren gemacht haben. Dann können Sie entscheiden, welche Korrekturen Sie am Code vornehmen müssen. In vielen Debuggern können Sie temporäre Änderungen vornehmen und mit der Ausführung des Programms fortfahren.

Es erfordert Zeit und Übung, bis Sie den Debugger effektiv einsetzen können, letztendlich handelt es sich dabei allerdings um eine der wichtigsten Aufgaben eines Softwareentwicklers. In diesem Artikel werden Sie in die wichtigsten Aspekte des Debuggens eingeführt und erhalten Tipps, die Ihnen den Einstieg erleichtern.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Ermitteln des Problems durch Stellen der richtigen Fragen

Es ist wichtig, das Problem zu ermitteln, bevor Sie versuchen, es zu beheben. In Ihrem Code sind in der Vergangenheit sicherlich bereits Probleme aufgetreten, weshalb Sie sich nun in das Debuggen einlesen. Bevor Sie mit dem Debuggen beginnen, sollten Sie sicherstellen, dass Sie das Problem ermittelt haben, das Sie lösen möchten:

* Wie sollte sich der Code eigentlich verhalten?

* Wie hat er sich stattdessen verhalten?

    Wenn beim Ausführen Ihrer App ein Fehler (bzw. eine Ausnahme) aufgetreten ist, kann das sogar von Vorteil sein! Bei einer Ausnahme handelt es sich um ein unerwartetes Ereignis, das beim Ausführen von Code auftritt – üblicherweise ein Fehler. Ein Debugger kann Sie an die Stelle im Code führen, an der die Ausnahme aufgetreten ist, und Sie dabei unterstützen, eine Lösung zu finden.

    Wie wirkt sich das unerwartete Problem aus? Haben Sie bereits einen Verdacht, an welcher Stelle im Code das Problem aufgetreten ist? Wenn Ihr Code beispielsweise Text anzeigt, der Text aber falsch ist, wissen Sie, dass ein Fehler in Ihren Daten vorliegt oder der Code, mit dem der Anzeigetext festgelegt wurde, weist einen Fehler auf. Wenn Sie den Code mit einem Debugger schrittweise durchlaufen, können Sie jede Änderung an Ihren Variablen untersuchen, um herauszufinden, wann und wie falsche Werte zugewiesen wurden.

## <a name="examine-your-assumptions"></a>Überprüfen Ihrer Annahmen

Bevor Sie einen Fehler untersuchen, überdenken Sie die Annahmen, die dazu geführt haben, dass Sie ein bestimmtes Ergebnis erwarten. Unbekannte Annahmen können beim Ermitteln eines Problems im Weg stehen, auch wenn Sie die Ursache des Problems bereits im Debugger gefunden haben. Die Liste Ihrer Annahmen kann sehr lang sein. Im Folgenden finden Sie einige Fragen, die Sie sich stellen sollten, um Ihre Annahmen auf die Probe zu stellen.

* Verwenden Sie die richtige API (also die richtigen Objekte, Funktionen, Methoden oder Eigenschaften)? Die API, die Sie verwenden, verhält sich möglicherweise anders als erwartet. (Nachdem Sie den API-Aufruf im Debugger untersucht haben, müssen Sie zur Behebung des Problems möglicherweise die entsprechende Dokumentation zum Ermitteln der richtigen API durchlesen.)

* Verwenden Sie die API richtig? Möglicherweise verwenden Sie die richtige API, aber Sie verwenden sie falsch.

* Enthält der Code Tippfehler? Manche Rechtschreibfehler, z.B. im Namen einer Variable, sind schwer zu finden, insbesondere dann, wenn Sie mit Sprachen arbeiten, in denen die Variablen vor der Verwendung nicht deklariert werden müssen.

* Haben Sie eine Änderung an Ihrem Code vorgenommen, von der Sie davon ausgehen, dass Sie nichts mit dem aktuellen Problem zu tun hat?

* Enthält ein Objekt oder eine Variable einen anderen Wert (oder Werttyp) als erwartet?

* Kennen Sie den Zweck des Codes? Es ist schwieriger, Code zu debuggen, den eine andere Person geschrieben hat. Wenn Sie den Code nicht geschrieben haben, müssen Sie nachvollziehen, welchen Zweck der Code hat, bevor Sie diesen effektiv debuggen können.

    > [!TIP]
    > Wenn Sie Code schreiben, sollten Sie mit Code beginnen, der nicht zu umfangreich ist und funktioniert. (Guter Beispielcode ist in diesem Fall hilfreich.) Es ist manchmal einfacher, Probleme in umfangreichem oder kompliziertem Code zu finden, indem Sie mit einem kleinen Codeabschnitt beginnen, der die Kernaufgabe veranschaulicht, die erfüllt werden soll. Anschließend können Sie inkrementell Code ändern oder hinzufügen und den Code an jeder Stelle auf Fehler testen.

Sie können Probleme in Ihrem Code schneller finden, indem Sie Ihre Annahmen in Frage stellen. Möglicherweise können Sie dadurch auch Probleme schneller beheben.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Schrittweises Durchlaufen des Codes im Debugmodus zum Ermitteln der Stelle, an der das Problem aufgetreten ist

Wenn Sie eine App ausführen, sehen Sie Fehler und falsche Ergebnisse normalerweise erst, nachdem der Code ausgeführt wurde. Zudem kann ein Programm unerwartet beendet werden, ohne dass Sie den Grund dafür erfahren.

Das Ausführen einer App in einem Debugger (auch als *Debugmodus* bezeichnet) bedeutet, dass der Debugger alle Vorgänge während der Ausführung des Programms überwacht. Sie können die App zudem jederzeit pausieren, um ihren Zustand zu überprüfen, und den Code anschließend schrittweise durchlaufen, um jedes Detail in Echtzeit zu beobachten.

In Visual Studio starten Sie den Debugmodus, indem Sie **F5** drücken, den Menübefehl **Debuggen**  >  **Debuggen starten** oder die Schaltfläche **Debuggen starten** (![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debugging starten")) in der Debugsymbolleiste verwenden. Wenn Ausnahmen auftreten, führt die Ausnahmen-Hilfe von Visual Studio Sie zu der Stelle, an der die Ausnahme aufgetreten ist und zeigt weitere hilfreiche Informationen an. Weitere Informationen zum Behandeln von Ausnahmen in Ihrem Code finden Sie unter [Debugging techniques and tools (Debugverfahren und Tools)](../debugger/write-better-code-with-visual-studio.md).

Wenn keine Ausnahme ausgelöst wurde, haben Sie möglicherweise dennoch eine Idee, an welcher Stelle im Code Sie nach dem Problem suchen müssen. Hierfür verwenden Sie *Breakpoints* mit dem Debugger, damit Sie den Code gründlicher untersuchen können. Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Breakpoint gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie die Werte von Variablen, das Verhalten des Arbeitsspeichers oder die Sequenz, in der der Code ausgeführt wird, überprüfen.

In Visual Studio können Sie einen Breakpoint schnell festlegen, indem Sie neben einer Codezeile auf den linken Rand klicken. Alternativ können Sie auf eine Zeile zeigen und **F9** drücken.

Zur Veranschaulichung dieser Konzepte werden Sie durch Beispielcode geführt, der bereits Fehler enthält. Hier wird C# verwendet, die Features des Debuggers gelten jedoch auch für Visual Basic, C++, JavaScript, Python und andere unterstützte Sprachen.

### <a name="create-a-sample-app-with-some-bugs"></a>Erstellen einer Beispiel-App (mit Fehlern)

Nun erstellen wir eine Anwendung, die einige Fehler enthält.

1. Auf Ihrem Computer muss Visual Studio installiert sein, und in Visual Studio muss je nachdem, welchen Typ von App Sie erstellen möchten, entweder die Workload **.NET-Desktopentwicklung** oder die Workload **Plattformübergreifende .NET Core-Entwicklung** installiert sein.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.

    Wenn Sie die Workload installieren müssen und Visual Studio bereits installiert ist, klicken Sie auf **Extras** > **Tools und Features abrufen...** . Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **.NET-Desktopentwicklung** (oder **Plattformübergreifende .NET Core-Entwicklung**) aus, und klicken Sie dann auf **Anpassen**.

1. Öffnen Sie Visual Studio.

    ::: moniker range=">=vs-2019"
    Wählen Sie im Startfenster **Neues Projekt erstellen** aus. Geben Sie im Suchfeld den Begriff **Konsole** ein, und wählen Sie dann entweder **Konsolen-App (.NET Core)** oder **Konsolen-App (.NET Framework)** aus. Wählen Sie **Weiter** aus. Geben Sie einen Projektnamen wie **Konsolen-App-ErsteApp** ein, und klicken Sie dann auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Visual C#** **Konsolen-App** und dann im mittleren Bereich wahlweise **Konsolen-App (.NET Framework)** oder **Konsolen-App (.NET Core)** aus. Geben Sie einen Namen wie **Konsolen-App-ErsteApp** ein, und klicken Sie dann auf **OK**.
    ::: moniker-end

    Wenn die Projektvorlage **Konsolen-App (.NET Framework)** oder **Konsolen-App (.NET Core)** nicht angezeigt wird, navigieren Sie zu **Tools** > **Get Tools and Features** (Tools und Features abrufen), wodurch der Visual Studio-Installer geöffnet wird. Wählen Sie entweder die Workload **Plattformübergreifende .NET Core-Entwicklung** oder die Workload **.NET-Desktopentwicklung** aus, und klicken Sie dann auf **Anpassen**.

    Visual Studio erstellt das Konsolenprojekt, das im Projektmappen-Explorer (rechter Bereich) angezeigt wird.

1. Ersetzen Sie in der Datei *Program.cs* den gesamten Code durch den folgenden:

    ```csharp
    using System;
    using System.Collections.Generic;

    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }

            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };

                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }

                // Expected Output:
                //  Tadpole  400,  Spiral
                //  Pinwheel  25,  Spiral
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }

        public class Galaxy
        {
            public string Name { get; set; }

            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }

        }

        public class GType
        {
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Mit diesem Code sollen der Name der Galaxie, die Entfernung zur Galaxie und der Galaxietyp in einer Liste angezeigt werden. Beim Debuggen ist es wichtig, den Zweck des Codes nachvollziehen zu können. Hier finden Sie das Format für eine Zeile aus der Liste, die in der Ausgabe angezeigt werden soll:

    *Name der Galaxie*, *Entfernung*, *Galaxietyp*.

### <a name="run-the-app"></a>Ausführen der App

1. Drücken Sie die Taste **F5**, oder klicken Sie in der Symbolleiste „Debuggen“ (über dem Code-Editor) auf die Schaltfläche **Debuggen starten**![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debugging starten").

    Die App wird gestartet, und der Debugger zeigt keine Ausnahmen an. Die Ausgabe im Konsolenfenster entspricht jedoch nicht Ihren Erwartungen. Folgende Ausgabe wird erwartet:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Stattdessen wird allerdings Folgendes ausgegeben:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Wenn Sie sich die Ausgabe und den Code ansehen, wissen Sie, dass `GType` dem Namen der Klasse entspricht, in der der Galaxietyp gespeichert wird. Versuchen Sie nun, tatsächlich den Galaxietyp (z.B. „Spiral“) anzuzeigen, nicht den Namen der Klasse.

### <a name="debug-the-app"></a>Debuggen der App

1. Setzen Sie einen Breakpoint, während die App noch ausgeführt wird, indem Sie auf den linken Rand neben dem `Console.WriteLine`-Methodenaufruf in dieser Codezeile klicken.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    Wenn Sie einen Breakpoint festlegen, wird ein roter Punkt am linken Rand angezeigt.

    Da ein Problem in der Ausgabe erkennbar ist, sollten Sie mit dem Debuggen im vorangehenden Code beginnen, der die Ausgabe im Debugger festlegt.

1. Klicken Sie auf der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**).

    Die App hält an dem von Ihnen festgelegten Breakpoint an. Die gelbe Markierung gibt an, wo der Debugger angehalten wird (die gelbe Codezeile wurde noch nicht ausgeführt).

1. Zeigen Sie auf die `GalaxyType`-Variable auf der rechten Seite, und erweitern Sie `theGalaxy.GalaxyType` auf der linken Seite des Schraubenschlüsselsymbols. Sie können sehen, dass `GalaxyType` die Eigenschaft `MyGType` enthält und der Eigenschaftswert auf `Spiral` festgelegt ist.

    ![Screenshot des Visual Studio-Debuggers mit einer gelb hervorgehobenen Codezeile und einem unter der Eigenschaft „theGalaxy.GalaxyType“erweiterten Menü am Ende der Zeile.](../debugger/media/beginners-inspect-variable.png)

    Bei „Spiral“ handelt es sich um den Wert, der eigentlich in der Konsole hätte ausgegeben werden sollen. Es ist also ein guter Anfang, dass Sie während der Ausführung der App auf diesen Wert im Code zugreifen können. In diesem Szenario verwenden Sie die falsche API. Testen Sie nun, ob dieses Problem behoben werden kann, während der Code im Debugger ausgeführt wird.

1. Zeigen Sie in diesem Code während des Debuggens auf das Ende von `theGalaxy.GalaxyType`, und ändern Sie den Wert in `theGalaxy.GalaxyType.MyGType`. Sie können diese Änderung zwar vornehmen, aber der Code-Editor zeigt einen Fehler an, der besagt, dass der Code nicht kompiliert werden kann.

    ![Screenshot des Visual Studio-Debuggers mit einer rot hervorgehobenen Codezeile und einem Meldungsfeld „Bearbeiten und fortfahren“, bei dem die Schaltfläche „Bearbeiten“ ausgewählt ist.](../debugger/media/beginners-edit.png)

1. Klicken Sie im Meldungsfeld **Bearbeiten und Fortfahren** auf **Bearbeiten**. Sie sehen nun eine Fehlermeldung im Fenster **Fehlerliste**. Der Fehler gibt an, dass `'object'` keine Definition für `MyGType` enthält.

    ![Screenshot des Visual Studio-Debuggers mit einer rot hervorgehobenen Codezeile und einem Fenster „Fehlerliste“, in dem zwei Fehler aufgeführt sind.](../debugger/media/beginners-no-definition.png)

    Obwohl Sie jede Galaxie mit einem Objekt vom Typ `GType` (mit der Eigenschaft `MyGType`) festgelegt haben, erkennt der Debugger den Typ des `theGalaxy`-Objekts nicht als `GType`. Woran liegt das? Sehen Sie sich den Code an, mit dem der Galaxietyp festgelegt wird. Dabei werden Sie feststellen, dass die `GType`-Klasse eine `MyGType`-Eigenschaft enthält, aber dennoch stimmt etwas nicht. Die Lösung liegt in der Fehlermeldung zu `object`: Der Interpreter für die Sprache hält den Typ des Objekts für `object` anstatt für `GType`.

1. Wenn Sie den Code betrachten, der für das Festlegen des Galaxietyps verwendet wird, werden Sie feststellen, dass die `GalaxyType`-Eigenschaft der `Galaxy`-Klasse auf `object` statt `GType` festgelegt ist.

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Ändern Sie den vorangehenden Code folgendermaßen:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Klicken Sie in der Symbolleiste „Debuggen“ auf **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG**  +  **UMSCHALT**  +  **F5**), um den Code erneut zu kompilieren und neu zu starten.

    Wenn der Debugger nun bei `Console.WriteLine` anhält, können Sie auf `theGalaxy.GalaxyType.MyGType` zeigen und werden feststellen, dass der Wert ordnungsgemäß festgelegt wurde.

1. Entfernen Sie den Breakpoint, indem Sie auf den roten Punkt am linken Rand klicken (oder mit der rechten Maustaste darauf klicken und **Breakpoint** > **Delete Breakpoint** (Breakpoint > Breakpoint entfernen) auswählen), und drücken Sie dann **F5**, um den Vorgang fortzusetzen.

    Die App wird ausgeführt, und eine Ausgabe wird angezeigt. Diese sieht nun gut aus, aber Sie werden feststellen, dass der Galaxietyp von „Small Magellanic Cloud“ nicht wie erwartet als „Irregular“ angezeigt wird, sondern gar nicht.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Legen Sie einen Breakpoint in dieser Codezeile fest.

    ```csharp
    public GType(char type)
    ```

    In diesem Code wird der Galaxietyp festgelegt, deshalb sollten Sie sich diesen genauer ansehen.

1. Klicken Sie auf der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG**  +  **UMSCHALT**  +  **F5**), um den Code neu zu starten.

    Der Debugger hält in der Codezeile an, in der Sie den Breakpoint festgelegt haben.

1. Zeigen Sie auf die Variable `type`. Sie sehen, dass der Wert (dem Zeichencode nach) `S` ist. Für Sie ist jedoch der Wert `I` relevant, da Sie wissen, dass der Galaxietyp „Irregular“ ist.

1. Drücken Sie **F5**, und zeigen Sie erneut auf die Variable `type`. Wiederholen Sie diesen Schritt, bis der Wert `I` in der Variable `type` angezeigt wird.

    ![Screenshot des Visual Studio-Debuggers mit einer gelb hervorgehobenen Codezeile und einem kleinen Fenster, in dem der Wert der Variablen „type“ als „73 ‘I‘“ angezeigt wird.](../debugger/media/beginners-inspecting-data.png)

1. Drücken Sie nun **F11** (**Debuggen** > **Einzelschritt**), oder klicken Sie auf die Schaltfläche **Einzelschritt** in der Debugsymbolleiste.

    Durch **F11** durchläuft der Debugger eine Anweisung nach der anderen (und führt deren Code aus). Bei **F10** (**Prozedurschritt**) handelt es sich um einen ähnlichen Befehl, und beide Befehle sind sehr nützlich, wenn Sie lernen, wie der Debugger verwendet wird.

1. Drücken Sie **F11**, bis Sie bei der Codezeile in der `switch`-Anweisung angelangt sind, die den Wert „I“ enthalten sollte. Hier sehen Sie, dass das Problem durch einen Tippfehler erzeugt wird. Sie erwarten, dass der Code fortgesetzt wird, bis `MyGType` als „Irregular“ festgelegt wird. Stattdessen überspringt der Debugger diesen Code vollständig und hält im Abschnitt `default` der Anweisung `switch` an.

    ![Suche von Tippfehlern](../debugger/media/beginners-typo.png)

    Wenn Sie den Code betrachten, sehen Sie, dass in der `case 'l'`-Anweisung ein Tippfehler ist. Dort sollte `case 'I'` stehen.

1. Klicken Sie auf den Code für `case 'l'`, und ersetzen Sie diesen durch `case 'I'`.

1. Entfernen Sie den Breakpoint, und klicken Sie auf die Schaltfläche **Neu starten**, um die App neu zu starten.

    Die Fehler wurden nun behoben, und die erwartete Ausgabe wird angezeigt!

    Drücken Sie eine beliebige Taste, um die App zu beenden.

## <a name="summary"></a>Zusammenfassung

Wenn ein Problem auftritt, sollten Sie den Debugger und [Schrittbefehle](../debugger/navigating-through-code-with-the-debugger.md) wie **F10** und **F11** verwenden, um den Bereich im Code zu finden, der das Problem auslöst.

> [!NOTE]
> Wenn der Bereich mit dem Fehler schwer zu finden ist, legen Sie einen Breakpoint in dem Bereich des Codes fest, der ausgeführt wird, bevor das Problem auftritt, und verwenden Sie anschließend Schrittbefehle, bis das Problem auftritt. Sie können zudem [Ablaufverfolgungspunkte](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) verwenden, um Nachrichten im Fenster **Ausgabe** zu protokollieren. Mithilfe von protokollierten Meldungen (und mithilfe der noch nicht protokollierten Meldungen) können Sie den Bereich, in dem das Problem auftritt, häufig eingrenzen. Sie müssen diesen Vorgang hierfür möglicherweise mehrmals wiederholen.

Wenn Sie den Codebereich mit dem Problem ermitteln, verwenden Sie den Debugger, um es zu untersuchen. Untersuchen Sie den problematischen Code, während Sie die App im Debugger ausführen, um die Ursache des Problems zu ermitteln:

* [Untersuchen Sie die Variablen](../debugger/view-data-values-in-data-tips-in-the-code-editor.md), und überprüfen Sie, ob diese die Werte enthalten, die Sie enthalten sollten. Wenn Sie einen falschen Wert finden, sollten Sie ermitteln, wo dieser festgelegt wurde. Starten Sie hierfür den Debugger neu, oder überprüfen Sie die [Aufrufliste](../debugger/how-to-use-the-call-stack-window.md) (oder beides).

* Überprüfen Sie, ob die Anwendung den Code ausführt, den Sie erwarten. (In der Beispielanwendung haben Sie beispielsweise erwartet, dass der Code für die switch-Anweisung den Galaxietyp auf „Irregular“ festlegt, aber die App hat den Code wegen eines Tippfehlers übersprungen.)

> [!TIP]
> Verwenden Sie einen Debugger, um Fehler zu finden. Ein Debugger kann Fehler *nur dann* für Sie finden, wenn er den Zweck Ihres Codes kennt. Ein Tool kann den Zweck jedoch nur kennen, wenn Sie als Entwickler diesen eindeutig ausdrücken. Dies erreichen Sie mit dem Schreiben von [Komponententests](../test/improve-code-quality.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie einige grundlegende Konzepte für das Debuggen kennengelernt. Als Nächstes erfahren Sie mehr über den Debugger.

> [!div class="nextstepaction"]
> [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
