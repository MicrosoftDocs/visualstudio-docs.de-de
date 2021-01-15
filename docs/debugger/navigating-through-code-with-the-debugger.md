---
title: Navigieren durch Code mit dem Debugger | Microsoft-Dokumentation
description: 'In diesem Artikel erfahren Sie, wie Sie den Visual Studio-Debugger zum Behandeln von Problemen mit Ihrem Code verwenden. Zu den Themen gehören: der Wechsel zum Unterbrechungsmodus, die Einzelschrittausführung des Codes und die Ausführung bis zu einem Ziel.'
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/12/2018
ms.topic: how-to
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ffe163ab567de98161f185ba2f3d2522c505095
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975211"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Navigieren durch Code mit dem Visual Studio-Debugger

Mit dem Visual Studio-Debugger können Sie durch Code navigieren, um den Zustand einer App zu überprüfen und deren Ausführungsablauf anzuzeigen. Sie können Tastenkombinationen, Debugbefehle, Haltepunkte und andere Funktionen verwenden, um schnell zu dem Code zu gelangen, den Sie untersuchen möchten. Wenn Sie mit Debuggernavigationsbefehlen und Verknüpfungen vertraut sind, können Sie App-Probleme schneller und einfacher aufspüren und lösen.

> [!NOTE]
> Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md) sowie [Debugverfahren und -tools](../debugger/write-better-code-with-visual-studio.md) lesen, bevor Sie diesen Artikel durchgehen.

## <a name="get-into-break-mode"></a>Wechseln in den „Unterbrechungsmodus“

Im *Unterbrechungsmodus* wird die Ausführung der App angehalten, während Funktionen, Variablen und Objekte im Speicher verbleiben. Sobald sich der Debugger im Unterbrechungsmodus befindet, können Sie durch den Code navigieren. Die gängigsten Methoden für das Wechseln in den Unterbrechungsmodus sind folgende:

- Beginnen Sie mit der Codeausführung in Einzelschritten, indem Sie **F10** oder **F11** drücken. Auf diese Weise können Sie schnell den Einstiegspunkt Ihrer App finden. Sie können dann fortfahren, indem Sie Schrittbefehle drücken, um durch den Code zu navigieren.

- [Führen Sie beispielsweise bis zu einer bestimmten Position oder Funktion aus](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), indem Sie [einen Haltepunkt festlegen](using-breakpoints.md) und Ihre App starten.

   Im Code-Editor in Visual Studio können Sie z. B. den Befehl **Ausführen bis Cursor** verwenden, um die App mit angefügtem Debugger zu starten und in den Unterbrechungsmodus zu wechseln. Anschließend verwenden Sie **F11**, um im Code zu navigieren.

   ![Ausführen bis Cursor und schrittweises Ausführen von Code](../debugger/media/navigate-code-code-stepping.gif "Ausführen bis Cursor und schrittweises Ausführen von Code")

Sobald Sie sich im Unterbrechungsmodus befinden, können Sie eine Vielzahl von Befehlen verwenden, um durch den Code zu navigieren. Im Unterbrechungsmodus können Sie die Werte von Variablen überprüfen, um nach Verstößen oder Fehlern zu suchen. Bei manchen Projekttypen können Sie im Unterbrechungsmodus auch Anpassungen der App vornehmen.

Die meisten Debuggerfenster, wie z. B. die Fenster **Module** und **Überwachung**, sind nur verfügbar, wenn der Debugger an Ihre App angefügt ist. Manche Debuggerfunktionen, z. B. die Anzeige von Variablenwerten im Fenster **Lokal** oder die Auswertung von Ausdrücken im Fenster **Überwachung**, sind nur verfügbar, wenn der Debugger angehalten ist (d. h. im Unterbrechungsmodus).

> [!NOTE]
> Wenn Sie die Ausführung von Code unterbrechen, der keine Quell- oder Symboldateien (*PDB-Dateien*) geladen hat, wird im Debugger die Seite **Source Files Not Found** (Die Quelldateien wurden nicht gefunden) oder **Symbols Not Found** (Die Symbole wurden nicht gefunden) angezeigt, auf der Sie die Dateien suchen und laden können. Weitere Informationen finden Sie unter [Angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Wenn Sie die Symbol- oder Quelldateien nicht laden können, können Sie dennoch die Assemblyanweisungen im Fenster **Disassembly** debuggen.

## <a name="step-through-code"></a>Schritt-für-Schritt-Ausführung des Codes

Mithilfe der Schrittbefehle des Debuggers können Sie den Zustand Ihrer App untersuchen oder mehr über deren Ausführungsablauf erfahren.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Zeilenweises Ausführen von Code

Verwenden Sie **Debuggen** > **Einzelschritt**, oder drücken Sie **F11**, um beim Debuggen bei jeder Anweisung anzuhalten.

Der Debugger durchläuft Codeanweisungen und nicht physische Zeilen. Beispielsweise kann eine `if`-Klausel in eine Zeile geschrieben werden:

  ```csharp
  int x = 42;
  string s = "Not answered";
  if( int x == 42) s = "Answered!";
  ```

  ```vb
  Dim x As Integer = 42
  Dim s As String = "Not answered"
  If x = 42 Then s = "Answered!"
  ```

Wenn Sie diese Zeile jedoch schrittweise ausführen, behandelt der Debugger die Bedingung als einen Schritt und das Ergebnis als anderen Schritt. Im vorherigen Beispiel ist die Bedingung TRUE.

Bei einem geschachtelten Funktionsaufruf führt **Einzelschritt** die am tiefsten geschachtelte Funktion in Einzelschritten aus. Wenn Sie beispielsweise **Hineinspringen** für einen Aufruf wie `Func1(Func2())` verwenden, führt der Debugger die Funktion `Func2` schrittweise aus.

>[!TIP]
>Wenn Sie jede Codezeile ausführen, können Sie auf Variablen zeigen, um deren Werte anzuzeigen. Oder Sie verwenden die Fenster [Lokal](autos-and-locals-windows.md) und [Überwachung](watch-and-quickwatch-windows.md), um die Änderung der Werte anzuzeigen. Sie können die [Aufrufliste](how-to-use-the-call-stack-window.md) beim schrittweisen Ausführen von Funktionen auch visuell nachverfolgen. (Weitere Informationen, die nur für Visual Studio Enterprise gelten, finden Sie unter [Erstellen einer visuellen Zuordnung der Aufrufliste beim Debuggen (C#, Visual Basic, C++, JavaScript)](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> Durchlaufen von Code und Überspringen einiger Funktionen

Beim Debuggen machen Sie sich möglicherweise keine Gedanken über eine Funktion oder wissen, dass diese funktioniert, wie bei sorgfältig getestetem Bibliothekscode. Sie können die folgenden Befehle verwenden, um beim schrittweisen Ausführen Code zu überspringen. Die Funktionen werden weiterhin ausgeführt, aber der Debugger überspringt sie.

|Tastaturbefehl|Menübefehle für das Debuggen|Beschreibung|
|----------------------|------------------|-----------------|
|**F10**|**Prozedurschritt**|Wenn die aktuelle Zeile einen Funktionsaufruf enthält, führt **Überspringen** den Code aus und hält die Ausführung in der ersten Codezeile an, nachdem die aufgerufene Funktion Werte zurückgegeben hat.|
|**UMSCHALT**+**F11**|**Ausführen bis Rücksprung**|**Herausspringen** führt weiterhin Code aus und hält die Ausführung an, wenn die aktuelle Funktion Werte zurückgibt. Der Debugger überspringt die aktuelle Funktion.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Ausführen bis zu einer bestimmten Position oder Funktion

Möglicherweise ziehen Sie es vor, direkt bis zu einer bestimmten Position oder Funktion auszuführen, wenn Sie genau wissen, welchen Code Sie untersuchen oder wo Sie mit dem Debuggen beginnen möchten.

### <a name="run-to-a-breakpoint-in-code"></a>Ausführen bis zu einem Haltepunkt im Code

Klicken Sie auf den Rand ganz links neben der Codezeile, bei der Sie die Ausführung anhalten möchten, um einen einfachen Haltepunkt in Ihrem Code festzulegen. Sie können auch die entsprechende Zeile auswählen und **F9** drücken, auf **Debuggen** > **Haltepunkt umschalten** klicken oder mit der rechten Maustaste klicken und **Haltepunkt** > **Haltepunkt einfügen** auswählen. Der Haltepunkt wird als roter Punkt auf dem linken Rand neben der Codezeile angezeigt. Der Debugger hält die Ausführung an, kurz bevor die Zeile ausgeführt wird.

![Festlegen eines Breakpoints](../debugger/media/dbg_basics_setbreakpoint.png "Haltepunkt festlegen")

Haltepunkte in Visual Studio bieten einen umfangreichen Satz von zusätzlichen Funktionen, wie z. B. bedingte Haltepunkte und Ablaufverfolgungspunkte. Weitere Informationen finden Sie unter [Verwenden von Breakpoints im Visual Studio-Debugger](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Ausführen bis zu einem Funktionshaltepunkt

Sie können den Debugger anweisen, dass er ausführt, bis eine bestimmte Funktion erreicht wird. Sie können die Funktion anhand ihres Namens angeben oder in der Aufrufliste auswählen.

**Angeben eines Funktionshaltepunkts anhand des Namens**

1. Klicken Sie auf **Debuggen** > **Neuer Haltepunkt** > **Funktionshaltepunkt**.

1. Geben Sie im Dialogfeld **Neuer Funktionshaltepunkt** den Namen der Funktion ein, und wählen Sie die zugehörige Sprache aus.

   ![Dialogfeld „Neuer Funktionshaltepunkt“](../debugger/media/dbg_execution_newbreakpoint.png "Neuer Funktionshaltepunkt")

1. Klicken Sie auf **OK**.

Wenn die Funktion überladen ist oder sich in mehreren Namespaces befindet, können Sie im Fenster **Haltepunkte** den gewünschten auswählen.

![Überladene Funktionshaltepunkte](../debugger/media/dbg_execution_overloadedbreakpoints.png "Überladene Funktionshaltepunkte")

**Auswählen eines Funktionshaltepunkts aus der Aufrufliste**

1. Öffnen Sie während des Debuggens das Fenster **Aufrufliste**, indem Sie auf **Debuggen** > **Fenster** > **Aufrufliste** klicken.

1. Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf eine Funktion, und wählen Sie **Ausführen bis Cursor** aus, oder drücken Sie **STRG**+**F10**.

Weitere Informationen zur visuellen Nachverfolgung der Aufrufliste finden Sie unter [Erstellen einer visuellen Zuordnung der Aufrufliste beim Debuggen (C#, Visual Basic, C++, JavaScript)](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Ausführen bis zur Cursorposition

Wählen Sie zum Ausführen bis zur Cursorposition im Quellcode oder im Fenster **Aufrufliste** die Zeile aus, bei der Sie anhalten möchten, klicken Sie mit der rechten Maustaste, und wählen Sie **Ausführen bis Cursor** aus, oder drücken Sie **STRG**+**F10**. Das Auswählen von **Run To Cursor** (Ausführen bis Cursor) ist wie das Festlegen eines temporären Haltepunkts.

### <a name="run-to-click"></a>Ausführung bis Klick

Während die Ausführung im Debugger angehalten ist, können Sie im Quellcode oder im Fenster **Disassembly** auf eine Anweisung zeigen und das grüne Pfeilsymbol **Ausführung bis hier ausführen** auswählen. Wenn Sie **Run to Click** (Ausführen bis Klick) verwenden, müssen Sie keinen temporären Haltepunkt festlegen.

![Run to Click](../debugger/media/dbg-run-to-click.png "Ausführung bis Klick") (Ausführen bis Klick)

> [!NOTE]
> **Run to Click** (Ausführen bis Klick) ist ab [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] verfügbar.

### <a name="manually-break-into-code"></a>Manuelles Unterbrechen im Code

Klicken Sie auf **Debuggen** > **Alle unterbrechen**, oder drücken Sie **STRG**+**Alt**+**Unterbrechen**, um in einer ausgeführten App in der nächsten verfügbaren Codezeile zu unterbrechen.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Bewegen des Zeigers zum Ändern des Ausführungsablaufs

Während der Debugger angehalten ist, wird durch eine gelbe Pfeilspitze am Rand des Quellcodes oder des Fensters **Disassembly** die Position der nächsten auszuführenden Anweisung gekennzeichnet. Sie können die nächste auszuführende Anweisung ändern, indem Sie diese Pfeilspitze verschieben. Sie können einen Teil des Codes überspringen oder zu einer vorherigen Zeile zurückkehren. Das Verschieben des Zeigers ist zum Beispiel sinnvoll, um einen Codeabschnitt zu überspringen, von dem bereits bekannt ist, dass er einen Fehler enthält.

 ![Verschieben des Zeigers](../debugger/media/dbg_basics_example3.gif "Verschieben des Zeigers")

Zum Ändern der nächsten auszuführenden Anweisung muss sich der Debugger im Unterbrechungsmodus befinden. Ziehen Sie die gelbe Pfeilspitze im Quellcode oder im Fenster **Disassembly** auf eine andere Zeile, oder klicken Sie mit der rechten Maustaste auf die Zeile, die Sie als nächstes ausführen möchten, und klicken Sie auf **Nächste Anweisung festlegen**.

Der Programmzähler springt direkt zur neuen Position, und die Anweisungen zwischen dem alten und dem neuen Ausführungspunkt werden nicht ausgeführt. Wenn Sie den Ausführungspunkt jedoch zurück verschieben, werden die dazwischenliegenden Anweisungen nicht rückgängig gemacht.

>[!CAUTION]
>- Wenn Sie die nächste Anweisung in eine andere Funktion oder in einen anderen Gültigkeitsbereich verschieben, wird i. d. R. die Aufrufliste beeinträchtigt, wodurch ein Laufzeitfehler oder eine Ausnahme ausgelöst wird. Wenn Sie versuchen, die nächste Anweisung in einen anderen Gültigkeitsbereich zu verschieben, wird ein Dialogfenster mit einer Warnung geöffnet, in dem Sie den Vorgang abbrechen können.
>- In Visual Basic können Sie die nächste Anweisung nicht in einen anderen Bereich oder in eine andere Funktion verlegen.
>- In systemeigenem C++-Code kann das Festlegen der nächsten Anweisung bei aktivierter Laufzeitprüfung dazu führen, dass am Ende der Methode eine Ausnahme ausgelöst wird.
>- Wenn die Funktion "Bearbeiten und Fortfahren" aktiviert ist, schlägt das Ausführen der Option **Nächste Anweisung festlegen** fehl, wenn Sie Änderungen vorgenommen haben, die von "Bearbeiten und Fortfahren" nicht sofort neu zugeordnet werden können. Dies kann auftreten, wenn Sie z. B. Code in einem catch-Block bearbeitet haben. In diesem Fall wird die Fehlermeldung angezeigt, dass der Vorgang nicht unterstützt wird.
>- In verwaltetem Code können Sie die nächste Anweisung in folgenden Fällen nicht verschieben:
>   - Die nächste Anweisung und die aktuelle Anweisung befinden sich in verschiedenen Methoden.
>   - Das Debuggen wurde über Just-In-Time-Debuggen gestartet.
>   - Die Aufrufliste wird gerade entladen.
>   - Eine System.StackOverflowException oder eine System.Threading.ThreadAbortException wurden ausgelöst.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Debuggen von IDE-generiertem Code

Der Debugger versucht standardmäßig, durch Aktivieren der Einstellung *Nur eigenen Code* nur Ihren App-Code zu debuggen. Weitere Informationen über die Funktionsweise dieses Features für verschiedene Projekttypen und Sprachen und dessen Anpassung finden Sie unter [Nur eigenen Code](../debugger/just-my-code.md).

Sie können „Nur eigenen Code“ deaktivieren, um während des Debuggens Frameworkcode, Bibliothekscode von Drittanbietern oder Systemaufrufe zu überprüfen. Deaktivieren Sie unter **Extras** (oder **Debuggen**) > **Optionen** > **Debuggen** das Kontrollkästchen **Nur eigenen Code aktivieren**. Wenn „Nur eigenen Code“ deaktiviert ist, wird im Debuggerfenster IDE-generierter Code angezeigt, und der Debugger kann den IDE-generierten Code schrittweise ausführen.

> [!NOTE]
> Nur mein Code wird in Geräteprojekten nicht unterstützt.

### <a name="debug-system-code"></a>Debuggen von Systemcode

Wenn Sie Debugsymbole für Systemcode von Microsoft geladen haben und „Nur eigenen Code“ deaktiviert ist, können Sie einen Systemaufruf ebenso wie jeden anderen Aufruf schrittweise ausführen.

Informationen zum Laden von Microsoft-Symbolen finden Sie unter [Konfigurieren von Symbolspeicherorten und Laden von Optionen](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**So laden Sie Symbole für eine bestimmte Systemkomponente:**

1. Öffnen Sie während des Debuggens das Fenster **Module**, indem Sie auf **Debuggen** > **Fenster** > **Module** klicken oder **STRG**+**ALT**+**U** drücken.

1. Im Fenster **Module** können Sie feststellen, für welche Module Symbole in der Spalte **Symbolstatus** geladen sind. Klicken Sie mit der rechten Maustaste auf das Modul, für das Sie Symbole laden möchten, und dann auf **Symbole laden**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Schrittweise Ausführung von Eigenschaften und Operatoren in verwaltetem Code
 Standardmäßig überspringt der Debugger die Eigenschaften und Operatoren in verwaltetem Code. In den meisten Fällen sorgt dies für einen besseren Debugvorgang. Klicken Sie auf **Debuggen** > **Optionen**, um das schrittweise Ausführen von Eigenschaften oder Operatoren zu aktivieren. Deaktivieren Sie auf der Seite **Debuggen** > **Allgemein** das Kontrollkästchen **Eigenschaften und Operatoren überspringen (nur verwaltet)** .

## <a name="see-also"></a>Siehe auch
- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Debugging techniques and tools (Debugverfahren und -tools)](../debugger/write-better-code-with-visual-studio.md)
- [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md)
