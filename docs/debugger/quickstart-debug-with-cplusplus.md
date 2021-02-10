---
title: Debuggen mit C++
description: Debuggen von nativem Code mithilfe des Visual Studio-Debuggers
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 8735ecd409eca2801b42b11bd3928a00e5191bf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840898"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Schnellstart: Debuggen mit C++ mithilfe des Visual Studio-Debuggers

Der Visual Studio-Debugger umfasst viele nützliche Features zum Debuggen von Apps. In diesem Thema werden einige der grundlegenden Funktionen erläutert.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt

1. Öffnen Sie Visual Studio, und erstellen Sie ein Projekt.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Geben Sie **STRG + Q** ein, um das Suchfeld zu öffnen, geben Sie **C++** ein, und wählen Sie **Vorlagen** und dann **Neues Konsolen-App-Projekt erstellen** aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Visual C++****Windows Desktop** und dann im mittleren Bereich **Windows-Konsolenanwendung** aus. Geben Sie dann einen Namen wie **MyDbgApp** ein, und klicken Sie auf **OK**.
    ::: moniker-end

    Wenn die Projektvorlage **Windows-Konsolenanwendung** nicht angezeigt wird, öffnen Sie unter **Tools** > **Tools und Features abrufen ...** den Visual Studio-Installer. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Desktopentwicklung mit C++**, und klicken Sie dann auf **Ändern**.

    Visual Studio erstellt daraufhin das Projekt.

1. Ersetzen Sie in „MyDbgApp.cpp“ den folgenden Code

    ```c++
    int main()
    {
        return 0;
    }
    ```

    durch den folgenden (`#include "stdafx.h"` nicht entfernen):

    ```c++
    #include <list>
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen

Ein *Breakpoint* gibt an, an welcher Stelle Visual Studio ausgeführten Code anhalten soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. Es handelt sich dabei um ein grundlegendes Debugfeature.

1. Wenn Sie einen Breakpoint festlegen möchten, klicken Sie im Bundsteg auf den Bereich links neben dem Funktionsaufruf `doWork`. Alternativ können Sie aber auch die Codezeile auswählen und **F9** drücken.

    ![Festlegen eines Breakpoints](../debugger/media/dbg-qs-set-breakpoint.png "Haltepunkt festlegen")

2. Drücken Sie dann **F5**, oder klicken Sie auf **Debuggen > Debuggen starten**.

    ![Erreichen eines Breakpoints](../debugger/media/dbg-qs-hit-breakpoint.png "Treffen eines Haltepunkts")

    Der Debugger hält an dem Breakpoint an, den Sie festlegen. Der gelbe Pfeil deutet auf die Anweisung, bei der der Debugger und die App-Ausführung ausgesetzt werden. Die Zeile mit dem Funktionsaufruf `doWork` wurde noch nicht ausgeführt.

    > [!TIP]
    > Verwenden Sie bei Breakpoints in einer Schleife oder Rekursion oder bei sehr vielen Breakpoints, die Sie häufig schrittweise durchlaufen, einen [bedingten Breakpoint](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression), damit die Codeausführung NUR unterbrochen wird, wenn bestimmte Bedingungen erfüllt sind. Wenn Sie mit einem bedingten Breakpoint arbeiten, sparen Sie Zeit und erleichtern sich möglicherweise das Debuggen von Problemen, die nur schwierig zu reproduzieren sind.

    Wenn Sie versuchen, in C++ Fehler zu debuggen, die im Zusammenhang mit dem Arbeitsspeicher stehen, können Sie Breakpoints auch dazu verwenden, Adresswerte (suchen Sie nach NULL-Werten) und die Anzahl von Verweisen zu untersuchen.

## <a name="navigate-code"></a>Navigieren durch den Code

Es gibt verschiedene Befehle, über die der Debugger zum Fortfahren angewiesen werden kann. In diesem Artikel wird ein nützlicher Befehl zur Codenavigation erläutert, der ab Visual Studio 2017 verfügbar ist.

Wenn der Vorgang am Breakpoint ausgesetzt wurde, zeigen Sie auf die Anweisung `c1.push_back(20)`, bis die grüne Schaltfläche **Run to click** (Ausführen bis Klick) ![Ausführen bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick") angezeigt wird, und klicken Sie dann auf diese.

![Ausführen bis Klick](../debugger/media/dbg-qs-run-to-click.png "Ausführen bis Klick")

Dann wird die App weiter ausgeführt, ruft `doWork` auf, und wird bei der Codezeile ausgesetzt, bei der Sie die Schaltfläche angeklickt haben.

Häufig werden die Tastaturbefehle **F10** und **F11** verwendet, um Code durchzugehen. Weitere ausführliche Anweisungen finden Sie unter [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Untersuchen von Variablen in einem Datentipp

1. Zeigen Sie in der aktuellen Codezeile (zu erkennen an dem gelben Ausführungszeiger) mit der Maus auf das `c1`-Objekt, um Datentipps anzuzeigen.

    ![Anzeigen eines Datentipps](../debugger/media/dbg-qs-data-tip.png "Anzeigen eines Datentipps")

    Der aktuelle Wert der Variable `c1` wird angezeigt, und Sie können die Eigenschaften untersuchen. Wenn Sie beim Debuggen einen nicht erwarteten Wert antreffen, enthalten die vorhergehenden oder die aufrufenden Codezeilen möglicherweise einen Fehler.

2. Erweitern Sie den Datentipp, um die Eigenschaftswerte des `c1`-Objekts einzusehen.

3. Wenn Sie den Datentipp anheften möchten, damit bei der Codeausführung weiterhin der Wert von `c1` angezeigt wird, klicken Sie auf das Stecknadelsymbol. (Sie können den angehefteten Datentipp an eine geeignete Stelle verschieben.)

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten von Code und Fortsetzen des Debuggens

Wenn Sie in einer Debugsitzung eine Änderung feststellen, die Sie in Ihrem Code testen möchten, ist dies auch kein Problem.

1. Klicken Sie auf die zweite Instanz von `c2.front()`, und ändern Sie `c2.front()` in `c2.back()`.

2. Drücken Sie wiederholt **F10** (oder klicken Sie auf **Debuggen > Prozedurschritt**), um den Debugger fortzusetzen und den bearbeiteten Code auszuführen.

    ![Bearbeiten und Fortfahren](../debugger/media/dbg-qs-edit-and-continue.gif "Bearbeiten und Fortfahren")

    Wenn Sie **F10** drücken, führt der Debugger jeweils nur eine Anweisung aus, überspringt Funktionen aber, anstatt diese schrittweise auszuführen (der Code, den Sie überspringen, wird weiter ausgeführt).

Weitere Informationen zum Bearbeiten und Fortfahren und zu Einschränkungen von Features finden Sie unter [Edit and Continue (Bearbeiten und Fortfahren)](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie den Debugger starten, Code schrittweise durchlaufen und Variablen untersuchen. Sie sollten sich einen allgemeinen Überblick über die Debugger-Features verschaffen und die zugehörigen Links aufrufen, um weitere Informationen hierzu zu erhalten.

> [!div class="nextstepaction"]
> [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
