---
title: Analysieren von Auslastungstestergebnissen
description: Lernen Sie, wie mit dem Auslastungstest-Analyzer Engpässe gesucht, Fehler ermittelt und Verbesserungen in Ihrer App gemessen werden können.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f33898aa1c3c08179f1438a7c6e6e11a75587bc
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442481"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analysieren von Auslastungstestergebnissen mithilfe des Auslastungstest-Analyzers

Mit dem **Auslastungstest-Analyzer** können Engpässe gesucht, Fehler ermittelt und Verbesserungen in Ihrer App gemessen werden.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Analysieren Sie Auslastungstestergebnisse wie folgt:

- Überwachen eines Auslastungstests während der Ausführung

- Analysieren eines abgeschlossenen Auslastungstests

- Anzeigen von Ergebnissen vorheriger Auslastungstests

Sie können auch Berichte erstellen, in denen zwei oder mehr Berichte verglichen werden, um eine Trendanalyse für Projektbeteiligte freizugeben. Weitere Informationen finden Sie unter [Reporting Load Tests Results for Test Comparisons or Trend Analysis (Erstellen von Berichten zu Auslastungstestergebnissen für Testvergleiche oder die Trendanalyse)](../test/compare-load-test-results.md).

Sie können diese Aufgaben unabhängig davon vornehmen, ob der Auslastungstest in Visual Studio Enterprise oder über die Befehlszeile bzw. auf einem einzelnen Computer oder einem Remotecomputer ausgeführt wird.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Unterschiede zwischen dem Analysieren eines laufenden und eines abgeschlossenen Auslastungstests

Wenn Sie einen Auslastungstest ausführen, wird der **Auslastungstest-Analyzer** auf einer separaten Registerkarte mit dem Namen und der Startzeit des Auslastungstests angezeigt (z.B. **LoadTest1 [12:40]**). Beim Ausführen eines Auslastungstests wird ein Teil der Leistungsindikatordaten im Arbeitsspeicher beibehalten. Diese Daten können während des Auslastungstests überwacht werden. Nach Abschluss eines Auslastungstests kann die vollständige Datenmenge aus der Datenbank analysiert werden. Die während eines Auslastungstests und nach Abschluss eines Auslastungstests angezeigten Daten unterscheiden sich. Daten für Antwortzeiten von 90 % und 95 % werden z. B. erst berechnet, nachdem der Auslastungstest abgeschlossen wurde. Unterschiede bestehen auch hinsichtlich der Funktion der Tools, die zum Analysieren der Daten zur Verfügung stehen.

Wenn Sie den Auslastungstest ausführen, sind zwei Ansichten verfügbar: **Diagrammansicht** und **Tabellenansicht**. Die **Diagrammansicht** ermöglicht es Ihnen, gesammelte Leistungsindikatoren grafisch darzustellen. Die **Tabellenansicht** liefert Informationen zu den einzelnen gesammelten Tests, Seiten, Transaktionen und Anforderungen. Zudem wird eine Tabelle mit den Fehlern angezeigt.

Standardmäßig wird nach Abschluss des Auslastungstestlaufs die **Zusammenfassungsansicht** angezeigt. Sie können mithilfe der Symbolleiste zwischen den Ansichten **Zusammenfassung**, **Diagramme**, **Tabellen** und **Details** wechseln. Der **Auslastungstest-Analyzer** kann auch mit den üblichen Verfahren zum Bearbeiten von Fenstern in Visual Studio angedockt oder unverankert verwendet werden. Beim Analysieren abgeschlossener Auslastungstestläufe können Sie mehrere **Auslastungstest-Analyzer** gleichzeitig öffnen, um die verschiedenen Testläufe zu vergleichen.

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-|-|
|**Zugriff auf die Ergebnisse des Auslastungstests:** Wenn Sie einen Auslastungstest im Auslastungstest-Editor ausführen, werden die Auslastungstestergebnisse automatisch geöffnet, und der laufende Test wird im **Auslastungstest-Analyzer** angezeigt.|-   [Vorgehensweise: Zugreifen auf Auslastungstestergebnisse für die Analyse](../test/how-to-access-load-test-results-for-analysis.md)|
|**Hinzufügen von Analysenotizen zum Auslastungstest:** Sie können dem Auslastungstest Kommentare hinzufügen, wenn Sie die Analyse durchführen. Die Kommentare werden zusammen mit dem Auslastungstestergebnis permanent gespeichert. Die eingegebene Beschreibung wird auch in der Spalte **Beschreibung** für den Auslastungstest im Dialogfeld **Open and Manage Test Results** (Auslastungstestergebnisse öffnen und verwalten) im Auslastungstest-Editor angezeigt.<br /><br /> Weitere Informationen finden Sie unter [How to: Access Load Test Results for Analysis (Vorgehensweise: Zugreifen auf Auslastungstestergebnisse für die Analyse)](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Darüber hinaus werden die Kommentare angezeigt, wenn Sie einen Excel-Bericht für die Auslastungstestergebnisse erstellen.<br /><br /> Weitere Informationen finden Sie unter [Reporting Load Tests Results for Test Comparisons or Trend Analysis (Berichterstellung für Auslastungstestergebnisse für Testvergleiche oder die Trendanalyse)](../test/compare-load-test-results.md).||
|**Analysieren der Ergebnisse des Auslastungstests:** Nach dem Zugriff auf die Daten des Auslastungstestlaufs können die dabei gesammelten Daten analysiert werden. Sie können eine Zusammenfassung des Auslastungstests anzeigen, um einen schnellen Überblick über die Ergebnisse zu erhalten. In der Zusammenfassung des Auslastungstests werden die wichtigsten Ergebnisse in einem kompakten und leicht lesbaren Format dargestellt.<br /><br /> Sie können die Zusammenfassung des Auslastungstests ausdrucken. Dies ist hilfreich, wenn Sie Ergebnisse an Projektbeteiligte weitergeben möchten.<br /><br /> Sie können die Details der Auslastungstestergebnisse mithilfe der Diagramme und Tabellen in den Ergebnissen analysieren. Dazu zählen die Tabellen **Errors**, **Pages**, **Requests**, **SQL Trace**, **Tests**, **Thresholds** und **Transactions**.|-   [Load Test Results Summary Overview (Zusammenfassung der Auslastungstestergebnisse – Übersicht)](../test/load-test-results-summary-overview.md)<br />-   [How to: View Web Page Response (Vorgehensweise: Anzeigen der Antwortzeit von Webseiten)](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analyzing Threshold Rule Violations (Analysieren von Verstößen gegen die Schwellenwertregel)](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analysieren der Aktivität virtueller Benutzer in den Auslastungstestergebnissen zur Isolierung von Leistungsproblemen:** Mit dem Diagramm für die Aktivitäten virtueller Benutzer können die Aktionen virtueller Benutzer während eines Auslastungstests grafisch dargestellt werden. So können Sie Spitzen in der CPU-Auslastung oder Rückgänge bei den Anforderungen pro Sekunde isolieren und feststellen, welche Tests oder Seiten während der jeweiligen Phasen ausgeführt werden.|-   [Analyzing Virtual User Activity in the Details View (Analysieren der Aktivität virtueller Benutzer in der Detailansicht)](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
