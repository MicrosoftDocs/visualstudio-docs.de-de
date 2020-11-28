---
title: 'Analysieren von Auslastungstestergebnissen: Diagrammansicht (Auslastungstest-Analyzer)'
description: Lernen Sie, Testergebnisse als Diagramme anzuzeigen. Jedes Diagramm wird in einem Bereich angezeigt, wobei der Diagrammname in einer Dropdownliste aufgeführt ist.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e30d81277ae28a3f5d6ca45a259fa66e0f4ee004
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441975"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analysieren von Auslastungstestergebnissen in der Diagrammansicht des Auslastungstest-Analyzers

Die Ergebnisse eines Auslastungstests werden als Daten in mehreren unterschiedlichen Bereichen angezeigt.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Klicken Sie auf der **Auslastungstest**-Symbolleiste auf die Option **Diagramme**, um die Testergebnisse als Diagramme anzuzeigen. Jedes einzelne Diagramm wird in einem Bereich angezeigt, wobei der Diagrammname zuoberst in einer Dropdownliste steht. Um ein anderes Diagramm im Bereich anzuzeigen, wählen Sie einen anderen Diagrammnamen aus der Liste aus.

Es können jeweils bis zu vier Diagrammbereiche angezeigt werden. Sie können zwischen verschiedenen Bereichslayouts umschalten, indem Sie die Schaltfläche auf der **Bereichslayout**-Symbolleiste verwenden.

Es werden mehrere integrierte Diagramme zur Verfügung gestellt. Sie können die integrierten Diagramme so verwenden wie sie sind oder anpassen. Darüber hinaus können Sie eigene Diagramme erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Löschen von Indikatoren in Diagrammen](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) und [How to: Create Custom Graphs (Vorgehensweise: Erstellen von benutzerdefinierten Diagrammen)](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Integrierte Diagramme

In der folgenden Tabelle sind die integrierten Diagramme aufgeführt, die für die Analyse von Auslastungstestergebnissen verfügbar sind.

|Diagrammname|Beschreibung|
|-|-|
|Schlüsselindikatoren|Indikatoren zur Beschreibung grundlegender Aspekte der Testleistung wie Benutzerauslastung, Durchsatz und Antwortzeit.|
|Testantwortzeit|Daten über die Zeitdauer, die zur Testausführung benötigt wird.|
|Seitenantwortzeit|Die durchschnittliche Antwortzeit für Webseiten, auf die während des Auslastungstests zugegriffen wird.|
|Getestetes System|Informationen über die Computer, auf denen die getestete Anwendung läuft. Dies schließt Daten über Arbeitsspeichernutzung, Prozessor, physischen Datenträger und Prozesse ein.<br /><br /> Standardmäßig werden nur Daten der Indikatoren Verfügbare MB und Prozessorzeit erfasst.|
|Controller und Agents|Informationen über die Computer, auf denen die Auslastungstests ausgeführt werden. Dies schließt Daten über Arbeitsspeichernutzung, Prozessor, physischen Datenträger und Prozesse ein.<br /><br /> Standardmäßig werden nur Daten der Indikatoren Verfügbare MB und Prozessorzeit erfasst.|
|Antwortzeit der Transaktion|Die durchschnittliche Antwortzeit für die während des Auslastungstests ausgeführten Transaktionen|

Sie können verschiedene Indikatoren im Diagramm anzeigen lassen, sowohl zur Laufzeit als auch nach Ausführung eines Tests.

> [!NOTE]
> Einem automatisch generierten Antwortzeitdiagramm können nur Leistungsindikatoren für die Antwortzeit hinzugefügt werden.

Die Indikatorinformationen werden sowohl im Diagramm als auch in der Legende unterhalb der Diagramme angezeigt. Außerdem können Sie einen Bereich des Diagramms vergrößern. Weitere Informationen finden Sie unter [Vorgehensweise: Vergrößern eines Diagrammbereichs](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>In Diagrammen angezeigte Zähler

In Diagrammen werden *Indikatoren* angezeigt. Indikatoren beziehen sich auf die während eines Auslastungstests erfassten Daten, beispielsweise Tests pro Sekunde oder durchschnittliche Testzeit. Weitere Informationen zu Indikatoren finden Sie unter [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

Die Legende der Indikatoren, die in den Diagrammen angezeigt werden, enthält mehrere Spalten mit nützlichen Daten zur Ausführung des Auslastungstests. Um die Anzeige von Daten im Diagramm zu deaktivieren, deaktivieren Sie das Kontrollkästchen in der entsprechenden Zeile der Legende.

Die Legende enthält folgende Spalten:

|Zähler|Der Name des Indikators|
|-|-|
|Instanz|Der Name der Indikatorinstanz.|
|Kategorie|Der Name der Indikatorkategorie.|
|Computer|Der Name des Computers, von dem Indikatordaten erfasst werden.|
|Farbe|Die Farbe der Linie im Diagramm.|
|Bereich|Gibt die Zahl an, die im Diagramm für diesen Indikator 100 darstellt. Beispiel: Bei einem Bereich mit einem oberen Wert von 10.000 entspricht die 100-Beschriftung oben im Diagramm 10.000.|
|Min.|Gibt den Mindestwert des Indikators in Millisekunden an.|
|Max.|Gibt den Maximalwert des Indikators in Millisekunden an.|
|Avg|Gibt den Durchschnittswert des Indikators in Millisekunden an.|
|Letzter|Zeigt den Wert des Indikators während des letzten Samplingintervalls in Millisekunden an.|

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-|-|
|**Anpassen der Diagramme mithilfe der Legende:** In der Legende der Diagrammansicht werden Informationen zu den einzelnen, einem Diagramm zugeordneten Leistungsindikatoren angezeigt. Mithilfe der Legende können Sie Leistungsindikatoren entfernen, Leistungsindikatoren im Diagramm hervorheben und die Zeichnungsoptionen anpassen.|-   [Using the Graphs View Legend to Analyze Load Tests (Verwenden der Legende der Diagrammansicht zum Analysieren von Auslastungstests)](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Anzeigen von Indikatoren in Diagrammen:** Sie können einem Diagramm für Auslastungstestergebnisse unterschiedliche Arten von Daten hinzufügen, indem Sie Indikatoren im Diagramm platzieren.|-   [Gewusst wie: Hinzufügen und Löschen von Indikatoren in Diagrammen](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Vergrößern von Diagrammen:** Nach Abschluss eines Auslastungstests können Sie die Zoomleisten zum Vergrößern und Anzeigen eines Bereichs im Diagramm verwenden. Durch das Vergrößern können Sie genauere Details der Daten anzeigen, die bei einem Auslastungstestlauf generiert wurden.|-   [Vorgehensweise: Vergrößern eines Diagrammbereichs](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Anordnen von Diagrammen (neben- bzw. untereinander):** Ihnen stehen mehrere Muster zur Verfügung, um Diagramme mit Auslastungstestergebnissen anzuordnen. Sie können bis zu vier Diagramme nebeneinander anordnen.||
|**Erstellen von benutzerdefinierten Diagrammen:** Sie können Diagramme entwerfen, in denen bestimmte Informationen zu Auslastungstestergebnissen angezeigt werden. Sie entwerfen ein benutzerdefiniertes Diagramm, indem Sie die Auslastungstestindikatoren angeben, die im Diagramm angezeigt werden.|-   [How to: Create Custom Graphs (Vorgehensweise: Erstellen von benutzerdefinierten Diagrammen)](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Exportieren der Leistungsindikatordaten des Diagramms:** Sie können die Diagrammdaten mithilfe der Schaltfläche **Diagrammdaten nach Excel exportieren** auf der Symbolleiste des **Auslastungstest-Analyzers** in Microsoft Excel exportieren, während die **Diagrammansicht** angezeigt wird.||

## <a name="related-tasks"></a>Verwandte Aufgaben

[Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[How to: Access Load Test Results for Analysis (Vorgehensweise: Zugreifen auf Auslastungstestergebnisse für die Analyse)](../test/how-to-access-load-test-results-for-analysis.md)

[Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Hinzufügen und Löschen von Indikatoren in Diagrammen](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [How to: Create Custom Graphs (Vorgehensweise: Erstellen von benutzerdefinierten Diagrammen)](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Vorgehensweise: Vergrößern eines Diagrammbereichs](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
