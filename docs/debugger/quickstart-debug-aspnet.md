---
title: Debuggen von ASP.NET Core
description: Debuggen von ASP.NET Core mithilfe des Visual Studio-Debuggers
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 882a192a96764356e90d78498ef5ed5ccd29ce25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908348"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Schnellstart: Debuggen von ASP.NET Core mithilfe des Visual Studio-Debuggers

Der Visual Studio-Debugger umfasst viele nützliche Features zum Debuggen von Apps. In diesem Thema werden einige der grundlegenden Funktionen erläutert.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt

1. Öffnen Sie Visual Studio.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Geben Sie **STRG + Q** ein, um das Suchfeld zu öffnen, geben Sie **asp.net** ein, und wählen Sie **Vorlagen** und dann **Neue ASP.NET Core-Webanwendung erstellen** aus. Wählen Sie im angezeigten Dialogfeld **Erstellen** aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Visual C#** **Web** aus, und wählen Sie dann im mittleren Bereich **ASP.NET Core-Webanwendung** aus. Geben Sie einen Namen wie **MyDbgApp** ein, und klicken Sie auf **OK**.

    Wählen Sie im angezeigten Dialogfeld im mittleren Bereich **Webanwendung** aus, und klicken Sie dann auf **OK**.

    ![Auswählen einer Webanwendung](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    Wenn die Projektvorlage **ASP.NET Core-Webanwendung** nicht angezeigt wird, öffnen Sie unter **Tools** > **Tools und Features abrufen ...** den Visual Studio-Installer. Klicken Sie auf die Workload **ASP.NET und Webentwicklung**, und klicken Sie anschließend auf **Ändern**.

    Visual Studio erstellt daraufhin das Projekt.

1. Öffnen Sie die Datei „About.cshtml.cs“ (unter Pages/About.cshtml) im Projektmappen-Explorer, und ersetzen Sie den folgenden Code

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    durch den folgenden:

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen

Ein *Breakpoint* gibt an, an welcher Stelle Visual Studio ausgeführten Code anhalten soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. Es handelt sich dabei um ein grundlegendes Debugfeature.

1. Wenn Sie einen Breakpoint festlegen möchten, klicken Sie im Bundsteg auf den Bereich links neben der Funktion `doWork`. Alternativ können Sie aber auch die Codezeile auswählen und **F9** drücken.

    ![Haltepunkt festlegen](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Der Breakpoint wird links neben der öffnenden geschweiften Klammer (`{`) festgelegt.

1. Drücken Sie dann **F5**, oder klicken Sie auf **Debuggen > Debuggen starten**.

1. Klicken Sie oben auf der Webseite auf den Link **Info**, wenn die Webseite geladen wird.

    Der Debugger hält an dem Breakpoint an, den Sie festlegen. Der gelbe Pfeil deutet auf die Anweisung, bei der der Debugger und die App-Ausführung ausgesetzt werden. Die Zeile mit der öffnenden geschweiften Klammer (`{`) nach der Funktionsdeklaration `doWork` wurde noch nicht ausgeführt.

    ![Treffen eines Haltepunkts](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Verwenden Sie bei Breakpoints in einer Schleife oder Rekursion oder bei sehr vielen Breakpoints, die Sie häufig schrittweise durchlaufen, einen [bedingten Breakpoint](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression), damit die Codeausführung NUR unterbrochen wird, wenn bestimmte Bedingungen erfüllt sind. Damit sparen Sie Zeit und erleichtern sich möglicherweise das Debuggen von Problemen, die nur schwierig zu reproduzieren sind.

## <a name="navigate-code"></a>Navigieren durch den Code

Es gibt verschiedene Befehle, über die der Debugger zum Fortfahren angewiesen werden kann. In diesem Artikel wird ein nützlicher Befehl zur Codenavigation erläutert, der ab Visual Studio 2017 verfügbar ist.

Wenn der Vorgang am Breakpoint ausgesetzt wurde, zeigen Sie auf die Anweisung `return c2`, bis die grüne Schaltfläche **Run to click** (Ausführen bis Klick) ![Ausführen bis Klick](../debugger/media/dbg-tour-run-to-click.png) angezeigt wird, und klicken Sie dann auf diese.

![Ausführen bis Klick](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Dann wird die App weiter ausgeführt, und wird bei der Codezeile ausgesetzt, bei der Sie die Schaltfläche angeklickt haben.

Häufig werden die Tastaturbefehle **F10** und **F11** verwendet, um Code durchzugehen. Weitere ausführliche Anweisungen finden Sie unter [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Untersuchen von Variablen in einem Datentipp

1. Zeigen Sie in der aktuellen Codezeile (zu erkennen an dem gelben Ausführungszeiger) mit der Maus auf das `c2`-Objekt, um Datentipps anzuzeigen.

    ![Anzeigen eines Datentipps](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Der aktuelle Wert der Variable `c2` wird angezeigt, und Sie können die Eigenschaften untersuchen. Wenn Sie beim Debuggen einen nicht erwarteten Wert antreffen, enthalten die vorhergehenden oder die aufrufenden Codezeilen möglicherweise einen Fehler.

2. Erweitern Sie den Datentipp, um die Eigenschaftswerte des `c2`-Objekts einzusehen.

3. Wenn Sie den Datentipp anheften möchten, damit bei der Codeausführung weiterhin der Wert von `c2` angezeigt wird, klicken Sie auf das Stecknadelsymbol. (Sie können den angehefteten Datentipp an eine geeignete Stelle verschieben.)

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten von Code und Fortsetzen des Debuggens

Wenn Sie in einer Debugsitzung eine Änderung feststellen, die Sie in Ihrem Code testen möchten, ist dies auch kein Problem.

1. Klicken Sie in der `OnGet`-Methode auf die zweite Instanz von `result.First.Value`, und ändern Sie `result.First.Value` in `result.Last.Value`.

1. Drücken Sie wiederholt **F10** (oder klicken Sie auf **Debuggen > Prozedurschritt**), um den Debugger fortzusetzen und den bearbeiteten Code auszuführen.

    ![Bearbeiten und Fortfahren](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Bearbeiten und Fortfahren")

    Wenn Sie **F10** drücken, führt der Debugger jeweils nur eine Anweisung aus, überspringt Funktionen aber, anstatt diese schrittweise auszuführen (der Code, den Sie überspringen, wird weiter ausgeführt).

Weitere Informationen zum Bearbeiten und Fortfahren und zu Einschränkungen von Features finden Sie unter [Edit and Continue (Bearbeiten und Fortfahren)](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie den Debugger starten, Code schrittweise durchlaufen und Variablen untersuchen. Sie sollten sich einen allgemeinen Überblick über die Debugger-Features verschaffen und die zugehörigen Links aufrufen, um weitere Informationen hierzu zu erhalten.

> [!div class="nextstepaction"]
> [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
