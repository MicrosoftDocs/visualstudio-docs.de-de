---
title: Analysieren von Auslastungstestergebnissen und -fehlern
description: Lernen Sie, Bereiche anzuzeigen, die Ihnen verschiedene Möglichkeiten zur Analyse der Ergebnisse einer Auslastungstestausführung bieten, wie z. B. ein Zeitverlaufsdiagramm oder detaillierte Tabellen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7787b3b0afaed0bc3592b458646b97151e309905
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442507"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht des Auslastungstest-Analyzers

Für die Auswertung der Ergebnisse eines Auslastungstestlaufs können verschiedene Bereiche angezeigt werden, die unterschiedliche Methoden der Datenanalyse ermöglichen. Sie können die Daten als Diagramm anzeigen, um zeitliche Verläufe zu identifizieren, oder Sie können die Daten als ausführlichen Tabellen anzeigen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Klicken Sie in der **Auslastungstest**-Symbolleiste auf **Tabellen**, um zur Tabellenansicht zu wechseln. Mithilfe der Dropdownliste **Tabelle** auf der Symbolleiste über dem Tabellenraster können Sie die Anzeige der verschiedenen Tabellen wechseln. In der Tabellenansicht können jeweils bis zu vier Tabellen angezeigt werden. Weitere Informationen finden Sie unter [Unterteilen von Auslastungstesttabellen](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) in diesem Thema.

Die meisten numerischen Werte in einer Leistungsindikatortabelle sind während des gesamten Auslastungstestlaufs kumulativ. Die Werte in den Spalten mit der Bezeichnung **Letzter** weichen hiervon ab, da diese den Wert aus dem letzten Samplingintervall darstellen.

> [!NOTE]
> Die Spalten mit der Bezeichnung **Letzter** sind nur verfügbar, wenn ein Auslastungstest ausgeführt wird. Nach Abschluss eines Auslastungstests sind diese Spalten nicht verfügbar.

Die meisten Tabellen können sortiert werden, indem Sie den Titel der Spalte wählen, nach der sortiert werden soll. In der Standardeinstellung werden in einigen Tabellen nicht alle verfügbaren Spalten angezeigt. Wenn Spalten verfügbar sind, können Sie diese den Tabellen hinzufügen. Um Spalten hinzuzufügen, klicken Sie mit der rechten Maustaste auf die Tabelle, und wählen Sie anschließend **Spalten hinzufügen/entfernen** aus.

> [!NOTE]
> Sie können die Daten aus einer Tabelle in andere Anwendungen, z. B. Excel, kopieren, um zusätzliche Analysen durchzuführen.

## <a name="the-load-test-tables"></a>Die Auslastungstesttabellen

In der folgenden Tabelle sind die Tabellen aufgeführt, die für die Analyse von Auslastungstestläufen verfügbar sind.

|Tabellenname|BESCHREIBUNG|
|-|-|
|Errors|Zeigt eine Liste mit Fehlern an, die während des Auslastungstestlaufs aufgetreten sind. Weitere Informationen finden Sie unter [Die Tabelle „Errors“](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) in diesem Artikel sowie unter [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Seiten|Zeigt eine Liste mit Seiten an, auf die während eines Auslastungstestlaufs zugegriffen wurde. Einige Daten dieser Tabelle sind nur nach Abschluss eines Auslastungstests verfügbar. Weitere Informationen finden Sie unter [How to: View Web Page Response (Vorgehensweise: Anzeigen der Antwortzeit von Websites)](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|Requests|Zeigt ausführliche Informationen zu einzelnen Anforderungen an, die während eines Auslastungstests ausgegeben wurden. Dies schließt alle HTTP-Anforderungen und abhängige Anforderungen, z. B. Bilder, ein. Weitere Informationen finden Sie unter [Die Tabelle „Requests“](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) in diesem Artikel.|
|SQL-Ablaufverfolgung|Zeigt die Ergebnisse der SQL-Ablaufverfolgung an. Diese Tabelle ist nur nach Abschluss eines Auslastungstests verfügbar. Außerdem muss die SQL-Ablaufverfolgung während des Tests aktiviert sein. Weitere Informationen finden Sie unter [Die Datentabelle „SQL Trace“](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) in diesem Artikel.|
|Tests|Zeigt ausführliche Informationen zu einzelnen Testläufen an, die während eines Auslastungstests ausgeführt wurden. Weitere Informationen finden Sie unter [Die Tabelle „Tests“](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) in diesem Artikel.|
|Schwellenwerte|Zeigt eine Liste mit Verletzungen von Schwellenwertregeln an, die während des Auslastungstestlaufs aufgetreten sind. Weitere Informationen finden Sie unter [Analysieren von Schwellenwertregelverstößen](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transaktionen|Zeigt eine Liste mit Transaktionen an, die während des Auslastungstestlaufs ausgeführt wurden. Weitere Informationen finden Sie unter [Die Tabelle „Transactions“](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) in diesem Artikel.|
|Agents|Zeigt nur an, wenn der Auslastungstest einen Testcontroller und Test-Agents verwendet. Zeigt eine Liste der Agents an, die während des Auslastungstestlaufs verwendet wurden. Die Tabelle "Agents" enthält, wie viele Anforderungen der Agent getestet hat und wie viele von diesen Anforderungen fehlerhaft waren. Darüber hinaus enthält die Tabelle "Agents" die Anzahl der Tests in der Auslastungstest-Testmischung, die der Agent getestet hat, und die Anzahl jener, die fehlerhaft waren.|
|Testdetails|Zeigt Details der in der Testmischung für den Auslastungstest enthaltenen Tests an. Die Details enthalten den Namen des Tests, das Szenario des Tests, die Zeit des Testbeginns, die Dauer der Ausführung des Tests und das Testergebnis, das angibt, ob der Test erfolgreich war oder fehlgeschlagen ist. Wenn bei dem Test ein Fehler aufgetreten ist, ist in der Spalte **Details** ein Link vorhanden. Sie können den Link auswählen, über den Sie den Webleistungstest-Editor mit der hervorgehobenen fehlgeschlagenen Anforderung aufrufen.|

## <a name="collect-percentile-data"></a>Sammeln von prozentualen Daten

In verschiedenen Auslastungstesttabellen können zusätzliche Spalten angezeigt werden, in denen prozentuale Daten und Antwortzeiten nach Netzwerkemulation gruppiert sind. Diese Daten werden in der Standardeinstellung nicht gesammelt. Prozentuale Daten sind nur verfügbar, wenn Sie Ergebnisse in einer Datenbank speichern, und nicht wenn Sie sie lokal speichern. Weitere Informationen finden Sie unter [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md). Um diese Daten zu sammeln, wählen Sie im **Auslastungstest-Editor** unter dem Knoten **Laufzeiteinstellungen** den Laufzeiteinstellungsknoten aus, den Sie ändern möchten. Wählen Sie im Fenster **Eigenschaften** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung****StatisticsOnly** oder **AllIndividualDetails** aus. Weitere Informationen finden Sie unter [How to: View Web Page Response (Vorgehensweise: Anzeigen der Antwortzeit von Websites)](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Die Tabelle „Requests“

In der Tabelle **Anforderungen** werden ausführliche Informationen zu einzelnen Anforderungen angezeigt, die während eines Auslastungstests ausgegeben wurden. Dies schließt alle HTTP-Anforderungen und abhängige Anforderungen, z. B. Bilder, ein. In der Tabelle sind Anforderungen nach Test und Szenario aufgelistet, da eine Anforderung in zahlreichen Tests und Szenarien enthalten sein kann.

In der folgenden Tabelle sind die Spalten der Tabelle **Anforderungen** aufgelistet:

|Column|BESCHREIBUNG|In der Standardeinstellung angezeigt|
|-|-|-|
|**Anforderung**|Die URL der Anforderung. Beispiel: *home.html* oder *orange-arrow.gif*.|Ja|
|**Szenario**|Der Name des Szenarios.|Ja|
|**Test**|Der Name des Tests.|Ja|
|**Gesamt**|Die Gesamtanzahl der Ausgabe dieser Webleistungstest-Anforderung während des Auslastungstestlaufs. Im Gesamtwert sind erfolgreiche und nicht erfolgreiche Anforderungen enthalten, jedoch keine zwischengespeicherten Anforderungen, da diese nicht an den Webserver übergeben werden.|Ja|
|**Erfolgreich**|Wie oft die Anforderung ausgegeben und erfolgreich ausgeführt wurde.|Nein|
|**Fehler**|Wie oft die Anforderung ausgegeben wurde und fehlgeschlagen ist. Die Einträge in dieser Spalte werden als Links angezeigt. Wählen Sie einen beliebigen Link, um im Dialogfeld **Auslastungstestfehler** eine Liste der einzelnen Fehler anzuzeigen. Weitere Informationen finden Sie unter [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Ja|
|**Zwischengespeichert**|Wie oft die Anforderung zwischengespeichert wurde.|Nein|
|**Anforderungen/Sekunde**|Die Rate der Anforderungen während des Auslastungstestlaufs pro Sekunde.|Nein|
|**Erfolgreich/Sekunde**|Die Rate der erfolgreich ausgeführten Instanzen dieser Anforderung während des Auslastungstestlaufs in Sekunden.|Nein|
|**Fehlgeschlagen/Sekunde**|Die Rate der fehlgeschlagenen Instanzen dieser Anforderung während des Auslastungstestlaufs in Sekunden.|Nein|
|**Zeit für erstes Byte**|Die durchschnittliche Dauer bis zum Empfang des ersten Byte der Anforderung, gemessen ab dem Zeitpunkt, an dem die Anforderung an den Webserver gesendet wurde. Die Zeiten werden in Sekunden angegeben.|Nein|
|**Antwortzeit**|Die durchschnittliche Dauer bis zum Empfang der gesamten Antwort auf eine Anforderung, gemessen ab dem Zeitpunkt, an dem die Anforderung an den Webserver gesendet wurde. Die Zeiten werden in Sekunden angegeben.|Ja|
|**Inhaltslänge**|Die durchschnittliche Inhaltslänge der Antwort auf die Anforderung. Die Inhaltslänge wird in Bytes angegeben.|Ja|

## <a name="the-tests-table"></a>Die Tabelle „Tests“

In der Tabelle **Tests** werden ausführliche Informationen zu einzelnen Tests angezeigt, die während eines Auslastungstests ausgeführt wurden. In der Tabelle werden Tests nach Test und Szenario aufgeführt, da ein Test in zahlreichen Szenarien enthalten sein kann.

In der folgenden Tabelle sind die Spalten der Tabelle **Tests** aufgelistet.

|Column|BESCHREIBUNG|In der Standardeinstellung angezeigt|
|-|-|-|
|**Test**|Der Name des Tests.|Ja|
|**Szenario**|Der Name des Szenarios.|Ja|
|**Gesamt**|Wie oft der Test in diesem Szenario ausgeführt wurde. Dieser Wert beinhaltet die Anzahl der erfolgreichen und fehlgeschlagenen Tests.|Ja|
|**Erfolgreich**|Wie oft der Test im Szenario erfolgreich ausgeführt wurde.|Ja|
|**Fehler**|Wie oft der Test im Szenario ausgeführt wurde und fehlgeschlagen ist. Die Einträge in dieser Spalte werden als Links angezeigt. Wählen Sie einen beliebigen Link, um im Dialogfeld **Auslastungstestfehler** eine Liste der einzelnen Fehler anzuzeigen. Weitere Informationen finden Sie unter [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Ja|
|**Tests/Sekunde**|Die Rate des Tests während des Auslastungstestlaufs pro Sekunde.|Ja|
|**Erfolgreich/Sekunde**|Die Rate der erfolgreich ausgeführten Instanzen des Tests während des Auslastungstestlaufs in Sekunden.|Nein|
|**Fehlgeschlagen/Sekunde**|Die Rate der fehlgeschlagenen Instanzen des Tests während des Auslastungstestlaufs in Sekunden.|Nein|
|**Testzeit**|Die durchschnittliche Ausführungsdauer des Tests während des Auslastungstestlaufs. Die Zeiten werden in Sekunden angegeben.|Ja|
|**90% Testzeit**|Der 90. Prozentwert der Testzeit.|Nein|
|**95% Testzeit**|Der 95. Prozentwert der Testzeit.|Ja|
|**Anforderungen/Test**|Die durchschnittliche Anzahl von Anforderungen im Test, wenn es sich um einen Webleistungstest handelt.|Nein|

## <a name="the-transactions-table"></a>Die Tabelle „Transactions“

In der Tabelle **Transaktionen** wird eine Liste von Transaktionen angezeigt, die während eines Auslastungstestlaufs ausgeführt wurden. Transaktionen verweisen entweder auf Transaktionen, die in einem Webleistungstest definiert sind, oder auf Zeitgeber, die in einem Komponententest definiert sind. Transaktionen verweisen nicht auf Datenbanktransaktionen.

In der folgenden Tabelle sind die Spalten der Tabelle **Transaktionen** aufgelistet.

> [!NOTE]
> Sie müssen zum Anzeigen aller Spalten die Eigenschaft "Speicher für Details der zeitlichen Steuerung" aktivieren, die der aktiven Testlaufeinstellung zugeordnet ist. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der Eigenschaft „Speicher für Details der zeitlichen Steuerung“ für die Einstellung der Auslastungstestausführung](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Column|BESCHREIBUNG|Sichtbar ohne zeitliche Steuerungsdetails|
|-|-|-|
|**Transaktion**|Der Name der Transaktion.|Ja|
|**Szenario**|Der Name des Szenarios.|Ja|
|**Test**|Der Name des Tests.|Ja|
|**Gesamt**|Die Gesamtanzahl von Transaktionen, die während des Auslastungstestlaufs ausgegeben wurden.|Ja|
|**Transaktionszeit**|Die Ausführungsdauer der Transaktion während des Auslastungstestlaufs. Für Webleistungstests wird die Reaktionszeit in der Berechnung berücksichtigt. Die Zeiten werden in Sekunden angegeben.|Nein|
|**Antwortzeit**|Die Antwortzeit der Webleistungstest-Transaktion in einem Auslastungstestlauf. Die Antwortzeit unterscheidet sich von der Transaktionszeit insofern, dass bei der Antwortzeit keine Reaktionszeiten berücksichtigt werden, die während der Transaktion aufgetreten sind. Die Zeiten werden in Sekunden angegeben.|Nein|
|**Durchschnittliche Transaktionszeit**|Die durchschnittliche Transaktionszeit. Diese Zeit schließt Reaktionszeiten ein. Wenn beispielsweise drei Anforderungen vorhanden sind und jede Anforderung Reaktionszeit beansprucht, beinhaltet diese Zeit die Reaktionszeiten und die zum Ausführen der Anforderungen tatsächlich benötigte Zeit.|Nein|
|**Durchschnittliche Antwortzeit**|Die durchschnittliche Antwortzeit einer Webleistungstest-Transaktion in einem Auslastungstestlauf. Die Antwortzeit unterscheidet sich von der Transaktionszeit insofern, dass bei der Antwortzeit keine Reaktionszeiten berücksichtigt werden, die während der Transaktion aufgetreten sind. Die Zeiten werden in Sekunden angegeben.|Nein|
|**Minimale Antwortzeit**|Dies schließt keine Reaktionszeiten ein.|Nein|
|**Maximale Antwortzeit**|Dies schließt keine Reaktionszeiten ein.|Nein|
|**Mittlere Antwortzeit**|Dies schließt keine Reaktionszeiten ein.|Nein|
|**90% Antwortzeit**|Der 90. Prozentwert der Transaktionszeit. Dies schließt keine Reaktionszeiten ein. **Hinweis:** Dies unterscheidet sich von Visual Studio Team System 2008 Test Load Agent. Dort wurde der Wert **90% Transaktionszeit** verwendet.|Nein|
|**95% Antwortzeit**|Der 95. Prozentwert der Transaktionszeit. Dies schließt keine Reaktionszeiten ein. **Hinweis:** Dies unterscheidet sich von Visual Studio Team System 2008 Test Load Agent. Dort wurde der Wert **95% Transaktionszeit** verwendet.|Nein|
|**99% Antwortzeit**|Der 99. Prozentwert der Transaktionszeit. Dies schließt keine Reaktionszeiten ein.|Nein|
|**Standardabweichung der Antwortzeit**|Dies schließt keine Reaktionszeiten ein.|Nein|

## <a name="the-errors-table"></a>Die Tabelle „Errors“

Wenn Sie einen Auslastungstest ausführen, können Sie die auftretenden Fehler analysieren. Das Analysieren der Fehler und das Einstellen der Tests sind ein wichtiger Teil des Auslastungstestprozesses. Wenn Fehler aufgetreten sind, erscheint ein **errors**-Link auf der Auslastungsteststatusleiste und gibt die Anzahl der aufgetretenen Fehler an. Um die Tabelle "Fehler" anzuzeigen, wählen Sie den Link aus.

In der Tabelle Errors sind die Fehler, die während eines Auslastungstests aufgetreten sind, nach Typ und Untertyp in Gruppen zusammengefasst. In der Tabelle wird außerdem eine Zeile **Gesamt** angezeigt, in der die Gesamtanzahl der aufgetretenen Fehler angegeben wird.

Die Tabelle Errors enthält folgende Spalten:

|Column|BESCHREIBUNG|Standardmäßig angezeigt|
|-|-|-|
|type|Der Typ des Fehlers. Beispielsweise HttpError.|Ja|
|Untertyp|Der Untertyp des Fehlers. Beispielsweise LoadTestException.|Ja|
|Anzahl|Die Anzahl der Fehler dieses Typs, die während des Auslastungstests auftraten. Die Einträge in dieser Spalte werden als Links angezeigt. Sie können jeden Link wählen, um eine Liste der einzelnen Fehler anzuzeigen.|Ja|
|Last Message|Eine Meldung mit einer Beschreibung des Fehlers. Zum Beispiel 404 - NotFound|Ja|

Weitere Informationen finden Sie unter [Arbeiten mit Auslastungstesttabellen](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Ausführen eines Drilldowns für die Fehlerliste

In der Tabelle Errors sind die Fehler nach Typ und Untertyp gruppiert. Zeigen Sie das Dialogfeld **Auslastungstestfehler** an, um eine Tabelle mit einzelnen Fehlern einzusehen. Um das Dialogfeld anzuzeigen, klicken Sie auf einen Link in der Spalte **Anzahl** der Tabelle „Fehler“. Das Dialogfeld kann auch angezeigt werden, indem Sie in der Tabelle „Fehler“ mit der rechten Maustaste auf eine Zeile mit Daten und dann auf **Fehler** klicken.

> [!NOTE]
> Nur die ersten 1.000 Instanzen jeder Kombination aus Fehlertyp und Untertyp werden erfasst. Im Dialogfeld **Auslastungstestfehler** werden höchstens die ersten 1.000 Fehlerinstanzen angezeigt.

Die Tabelle **Auslastungstestfehler** enthält folgende Spalten:

|Column|BESCHREIBUNG|
|-|-|
|**Time**|Der Zeitpunkt während des Auslastungstests, zu dem der Fehler auftrat|
|**Agent**|Der Name des Agent-Computers, auf dem der Fehler auftrat. Dies ist wichtig, wenn Sie Auslastungstests mithilfe von Testcontrollern und Test-Agents ausführen. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Der Name des Webleistungstests, in dem der Fehler auftrat.|
|**Szenario**|Der Name des Szenarios, in dem der Fehler auftrat|
|**Anforderung**|Die URL der Anforderung, in der der Fehler auftrat|
|**Type**|Der Typ des Fehlers. Beispielsweise HttpError.|
|**Untertyp**|Der Untertyp des Fehlers. Beispielsweise LoadTestException.|
|**Text**|Der Text der Fehlermeldung. Zum Beispiel 404 - NotFound|
|**Stapel**|Die Einträge in dieser Spalte sind entweder leer, oder das Wort **Stapel** ist als Link formatiert. Sie können den Link auswählen, um eine Stapelüberwachung des Fehlers anzuzeigen.|
|**Details**|Die Einträge in dieser Spalte sind entweder leer, oder das Wort **TestLog** ist als Link formatiert. Mit diesem Link können Sie Fehler im Auslastungstest isolieren. Wenn Sie beispielsweise den Link **TestLog** für einen Webleistungstest-Anforderungsfehler anklicken, werden die Ergebnisse für den Webleistungstest in der Webleistungstest-Ergebnisanzeige angezeigt, und der Anforderungsfehler wird hervorgehoben.|

> [!NOTE]
> Sie können die Tabelle sortieren, indem Sie die Spaltenüberschriften auswählen.

## <a name="the-sql-trace-data-table"></a>Die Datentabelle „SQL Trace“

Sie können während eines Auslastungstestlaufs SQL-Ablaufverfolgungsdaten zur späteren Analyse erfassen. Durch das Erfassen von Ablaufverfolgungsdaten können Sie in der getesteten SQL Server-Datenbank die Abfragen und gespeicherten Prozeduren ermitteln, die am langsamsten ausgeführt werden.

Bei aktivierter SQL-Ablaufverfolgung wird während des Auslastungstestlaufs eine Datei mit den Ablaufverfolgungsdaten erstellt. Diese Daten werden nach Abschluss des Testlaufs automatisch im Auslastungstest-Ergebnisspeicher gespeichert, und die Ablaufverfolgungsdatei wird gelöscht. Nach Abschluss des Auslastungstests analysieren Sie die Ablaufverfolgungsdaten in der Tabelle **SQL-Ablaufverfolgung**.

### <a name="to-view-sql-trace-data"></a>Anzeigen der SQL-Ablaufverfolgungsdaten

1. Wählen Sie im Auslastungstest-Analyzer auf der Symbolleiste die Option **Tabellen** aus, um sicherzustellen, dass das Tabellenraster angezeigt wird.

2. Wählen Sie in der Dropdownliste **Tabelle** die Option **SQL-Ablaufverfolgung** aus.

3. Die Ablaufverfolgungsdaten, die während des Testlaufs gesammelt wurden, werden im Raster angezeigt. In der Tabelle werden die langsamsten SQL-Vorgänge nach Dauer sortiert, wobei der langsamste Vorgang an erster Stelle steht. In der Regel sollten Sie zuerst die Spalte **Dauer** überprüfen. Die Daten werden in Millisekunden angezeigt.

   Die folgenden Spalten werden angezeigt:

    - **Ereignisklasse**

    - **Duration**

    - **CPU**

    - **Reads**

    - **Writes**

    - **TextData**

    - **StartTime**

    - **EndTime**

   Wenn Sie SQL-Ereignisse verfolgen möchten, die nicht mit den Daten in diesen Spalten angegeben werden, können Sie getrennt von Visual Studio eine eigene benutzerdefinierte SQL-Ablaufverfolgung mithilfe des SQL Profiler-Tools einrichten.

## <a name="tile-load-test-tables"></a>Unterteilen von Auslastungstesttabellen

Die Ergebnisse eines Auslastungstestlaufs können als ausführliche Tabellen angezeigt werden. Klicken Sie in der **Auslastungstest**-Symbolleiste auf **Tabellen**, um zur Tabellenansicht zu wechseln. Die verfügbaren Tabellen lauten **Errors**, **Pages**, **Requests**, **SQL Trace**, **Tests**, **Thresholds** und **Transactions**. Weitere Informationen finden Sie unter [Arbeiten mit Auslastungstesttabellen](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

In der Tabellenansicht können Sie bis zu vier Tabellen gleichzeitig anzeigen, ohne dass die Tabellen überlappen.

### <a name="to-tile-tables"></a>So ordnen Sie Tabellen neben- bzw. untereinander an

1. Klicken Sie auf der Symbolleiste des **Auslastungstest-Analyzers** auf **Tabellen**.

     Die Tabellenansicht wird geöffnet. Im Standardlayout werden zwei horizontale Bereiche angezeigt.

2. Klicken Sie auf der Symbolleiste des **Auslastungstest-Analyzers** auf die Schaltfläche **Layout**, und wählen Sie dann eine der folgenden Optionen aus:

    - **Ein Bereich**

    - **Zwei horizontale Bereiche**

    - **Drei horizontale Bereiche**

    - **Vier horizontale Bereiche**

3. Mithilfe der Dropdownliste über dem Tabellenraster in den einzelnen Bereichen können Sie zwischen den verschiedenen Tabellen wechseln.

    > [!NOTE]
    > Dieselbe Tabelle kann nicht in mehreren Bereichen gleichzeitig angezeigt werden. Wenn Sie die in einem Bereich angezeigte Tabelle in eine andere Tabelle ändern, die bereits in einem anderen Bereich angezeigt wird, wechseln die Tabellen einfach die Bereiche.

## <a name="see-also"></a>Siehe auch

- [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [How to: Access Load Test Results for Analysis (Vorgehensweise: Zugreifen auf Auslastungstestergebnisse für die Analyse)](../test/how-to-access-load-test-results-for-analysis.md)
- [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analysieren von Verstößen gegen Schwellenwertregeln](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Übersicht der Auslastungstestergebnisse](../test/load-test-results-summary-overview.md)
