---
title: Protokollieren von Informationen mit Ablaufverfolgungspunkten | Microsoft-Dokumentation
ms.date: 10/28/2019
ms.topic: how-to
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 33b471122318038ab66bc4f73e437209c6da2ffe
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "89561337"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>Protokollieren von Informationen im Ausgabefenster mithilfe von Ablaufverfolgungspunkten in Visual Studio

Mit Ablaufverfolgungspunkten können Sie Informationen im Ausgabefenster protokollieren. Hierfür können Sie Bedingungen konfigurieren, sodass der Code nicht geändert oder angehalten werden muss. Dieses Feature wird für verwaltete Sprachen (C#, Visual Basic, F#), nativen Code und Sprachen wie JavaScript und Python unterstützt.

## <a name="let39s-take-an-example"></a>Beispiel

Das folgende Beispielprogramm ist eine einfache `for`-Schleife mit einer Zählervariable, die jedes Mal um 1 erhöht wird, wenn die Schleife eine weitere Iteration ausführt.

![Zählerbeispiel](../debugger/media/counterexample.png "Zählerbeispiel")

## <a name="set-tracepoints-in-source-code"></a>Festlegen von Ablaufverfolgungspunkten im Quellcode

Sie können Ablaufverfolgungspunkte festlegen, indem Sie eine Ausgabezeichenfolge unter dem Kontrollkästchen **Aktion** im Fenster **Haltepunkteinstellungen** festlegen.

1. Klicken Sie zunächst links auf dem Bundsteg auf die Zeilennummer, in der der Ablaufverfolgungspunkt festgelegt werden soll, um einen Ablaufverfolgungspunkt zu initialisieren.

   ![Initialisierung von Haltepunkten](../debugger/media/breakpointinitialization.png "Initialisierung von Haltepunkten")

2. Zeigen Sie auf den roten Kreis, und klicken Sie dann auf das Zahnradsymbol.
3. Daraufhin wird das Fenster **Haltepunkteinstellungen** geöffnet.

   ![Haltepunktfenster](../debugger/media/breakpointwindow.png "Haltepunktfenster")

4. Aktivieren Sie das Kontrollkästchen **Aktion** .

   ![Aktivierte Kontrollkästchen unter „Aktion“](../debugger/media/checkedactionsbox.png "Aktivierte Kontrollkästchen unter „Aktion“")

   Sie sehen, dass sich der rote Kreis in einen Diamanten ändert. Das bedeutet, dass der Haltepunkt in einen Ablaufverfolgungspunkt geändert wurde.

5. Geben Sie die Meldung ein, die Sie im Textfeld **Meldung im Ausgabefenster anzeigen:** protokollieren möchten. Weitere Informationen finden Sie in nachfolgenden Abschnitten in diesem Artikel.

   Der Ablaufverfolgungspunkt ist damit festgelegt. Klicken Sie auf die Schaltfläche &quot;Schließen&quot;, wenn Sie nur einige Informationen im Ausgabefenster protokollieren möchten.

6. Wenn Sie Bedingungen hinzufügen möchten, die bestimmen, ob und wann Ihre Meldung angezeigt wird, aktivieren Sie das Kontrollkästchen **Bedingungen** .

   ![Aktiviertes Kontrollkästchen „Bedingungen“](../debugger/media/checkedconditionsbox.png "Aktiviertes Kontrollkästchen „Bedingungen“")

   Es gibt drei mögliche Bedingungen: **Bedingter Ausdruck** , **Filter** und **Trefferanzahl** .

## <a name="actions-menu"></a>Menü „Aktionen“

Mit diesem Menü können Sie eine Meldung im Ausgabefenster protokollieren. Geben Sie die Zeichenfolgen ein, die im Meldungsfeld ausgegeben werden sollen (Anführungszeichen sind nicht erforderlich). Wenn Sie die Werte von Variablen anzeigen möchten, müssen Sie diese in geschweifte Klammern einschließen.

Wenn Sie z. B. den Wert der Variablen `counter` in der Ausgabekonsole anzeigen möchten, müssen Sie {counter} im Textfeld für die Meldung eingeben.

![Ausgabemeldung des Zählers](../debugger/media/counteroutputmessage.png "Ausgabemeldung des Zählers")

Wenn Sie auf **Schließen** klicken und anschließend den Debugger für das Programm starten ( **F5** ), wird im Ausgabefenster die folgende Ausgabe angezeigt:

![Aktionsmeldung im Ausgabefenster](../debugger/media/actionsmessageinoutputwindow.png "Aktionsmeldung im Ausgabefenster")

Sie können auch bestimmte Schlüsselwörter verwenden, um spezifischere Informationen anzuzeigen. Geben Sie das Schlüsselwort genau wie unten dargestellt ein. Schreiben Sie das Schlüsselwort in Großbuchstaben, und stellen Sie ihm $ voran.

| Stichwort | Anzeige |
| --- | --- |
| $ADDRESS | Aktuelle Anweisung |
| $CALLER | Aufrufen des Funktionsnamens |
| $CALLSTACK | Aufrufliste |
| $FUNCTION | Name der aktuellen Funktion |
| $PID | Prozess-ID |
| $PNAME | Prozessname |
| $TID | Thread-ID |
| $TNAME   | Threadname |
| $TICK | Taktanzahl (von Windows GetTickCount) |

## <a name="conditions-menu"></a>Menü „Bedingungen“

Mit Bedingungen können Sie Ihre Ausgabemeldungen filtern, sodass sie nur in bestimmten Fällen angezeigt werden. Dabei stehen Ihnen drei Überkategorien für Bedingungen zur Verfügung.

### <a name="conditional-expression"></a>Bedingter Ausdruck
Mit einem bedingten Ausdruck wird eine Ausgabemeldung nur angezeigt, wenn bestimmte Bedingungen erfüllt sind.

Bei diesen können Sie den Ablaufverfolgungspunkt so festlegen, dass eine Meldung ausgegeben wird, wenn eine bestimmte Bedingung erfüllt ist oder sich geändert hat. Wenn Sie z. B. nur den Wert des Zählers während der Iterationen der `for`-Schleife anzeigen möchten, können Sie die Option **Trifft zu** auswählen und dann `i%2 == 0` in das Textfeld für die Meldung eingeben.

![Bedingter Ausdruck wird erfüllt](../debugger/media/conditionalexpressionistrue.png "Bedingter Ausdruck wird erfüllt")

Wenn Sie den Wert des Zählers ausgeben möchten, wenn sich die Iterationen der `for`-Schleife ändert, wählen Sie die Option **Bei Änderung** aus, und geben Sie `i` in das Textfeld für die Meldung ein.

![Bedingter Ausdruck bei Änderung](../debugger/media/conditionalexpressionwhenchanged.png "Bedingter Ausdruck bei Änderung")

Das Verhalten der Option **Bei Änderung** unterscheidet sich je nach Programmiersprache.

- Bei nativem Code wird die erste Auswertung der Bedingung vom Debugger nicht als Änderung betrachtet. Der Ablaufverfolgungspunkt wird also bei der ersten Auswertung nicht beachtet.
- Bei verwaltetem Code wird der Ablaufverfolgungspunkt bei der ersten Auswertung beachtet, wenn **Bei Änderung** festgelegt ist.

Mehr gültige Ausdrücke beim Festlegen von Bedingungen finden Sie unter [Ausdrücke im Debugger](expressions-in-the-debugger.md).

### <a name="hit-count"></a>Trefferanzahl
Mit der Bedingung „Trefferanzahl“ können Sie festlegen, dass die Ausgabe nur gesendet wird, wenn für die Codezeile mit dem Ablaufverfolgungspunkt eine bestimmte Anzahl Ausführungen ermittelt wurde.

Bei der Trefferanzahl können Sie angeben, dass eine Meldung ausgegeben werden soll, wenn die Anzahl der Ausführungen der Codezeile mit dem Ablaufverfolgungspunkt dem festgelegten Wert für die Trefferanzahl entspricht, ein Vielfaches von diesem ist oder größer oder gleich diesem Wert ist. Wählen Sie die für Sie passende Option aus, und geben Sie einen Integerwert wie 5 in das Feld ein, der für die gewünschte Iteration steht.

![Trefferanzahl für bedingten Ausdruck](../debugger/media/conditionalexpressionhitcount.png "Trefferanzahl für bedingten Ausdruck")

### <a name="filter"></a>Filter
Bei einer Filterbedingung legen Sie fest, für welche Geräte, Prozesse oder Threads eine Ausgabe angezeigt wird.

![Filter für bedingten Ausdruck](../debugger/media/conditionalexpressionfilter.png "Filter für bedingten Ausdruck")

Filterausdrücke:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Schließen Sie Zeichenfolgen (wie Namen) in doppelte Anführungszeichen ein. Werte können ohne Anführungszeichen eingegeben werden. Sie können Klauseln mit `&` (`AND`), `||` (`OR`), `!` (`NOT`) und Klammern kombinieren.

## <a name="considerations"></a>Weitere Überlegungen

Ablaufverfolgungspunkte sollen das Debuggen zwar vereinfachen, doch es gibt bei deren Verwendung auch einiges zu beachten.

Wenn Sie eine Eigenschaft oder ein Attribut eines Objekts überprüfen, kann sich dessen Wert manchmal ändern. Wenn sich der Wert während der Überprüfung ändert, wird der Fehler jedoch nicht vom Feature für Ablaufverfolgungspunkte verursacht. Es ist eher so, dass die Verwendung von Ablaufverfolgungspunkten nicht verhindert, dass Werte bei der Überprüfung von Objekten versehentlich geändert werden.

Die Auswertung von Ausdrücken im Meldungsfeld **Aktion** kann sich von der Sprache unterscheiden, die Sie für die Entwicklung verwenden. Wenn Sie beispielsweise eine Zeichenfolge ausgeben möchten, müssen Sie eine Meldung nicht in Anführungszeichen einschließen, auch wenn das bei `Debug.WriteLine()` oder `console.log()` normalerweise erforderlich wäre. Außerdem kann sich die Syntax für geschweifte Klammern (`{ }`) in Ausgabeausdrücken von der Konvention zum Ausgeben von Werten in der Entwicklungssprache unterscheiden. Der Inhalt der geschweiften Klammern (`{ }`) sollte jedoch immer noch der Syntax Ihrer Entwicklungssprache entsprechend geschrieben werden.

Wenn Sie eine Liveanwendung debuggen und nach einem ähnlichen Feature suchen, können Sie sich das Feature für Protokollpunkte im Momentaufnahmedebugger ansehen. Der Momentaufnahmedebugger ist ein Tool, mit dem Probleme in Produktionsanwendungen untersucht werden können. Mit Protokollpunkten können Sie auch Meldungen an das Ausgabefenster senden, ohne den Quellcode ändern zu müssen oder die ausgeführte Anwendung zu beeinträchtigen. Weitere Informationen finden Sie unter [Debuggen einer Azure-Liveanwendungen](../debugger/debug-live-azure-applications.md).

## <a name="see-also"></a>Siehe auch

- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Debugtechniken und -tools, mit denen Sie besseren Code schreiben](../debugger/write-better-code-with-visual-studio.md)
- [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md)
- [Ausdrücke im Debugger](expressions-in-the-debugger.md)
- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
- [Debuggen einer Azure-Liveanwendungen](../debugger/debug-live-azure-applications.md)
