---
title: Analysieren von Verletzungen der Schwellenwertregeln in Auslastungstests
description: Lernen Sie, Verstöße gegen von Ihnen festgelegte Schwellenwertregeln anzuzeigen, damit Sie die Verstöße analysieren können.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49fe5893254083dd83551ef5f43fffcc295a992a
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442702"
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analysieren von Verletzungen der Schwellenwertregeln in Auslastungstests mithilfe des Auslastungstest-Analyzers

Schwellenwertregeln sind bestimmten Leistungsindikatoren zugeordnet. Verletzungen weisen darauf hin, dass ein Leistungsindikator einen festgelegten Wert über- oder unterschritten hat. Wenn Sie einen Auslastungstest ausführen, können auftretende Verletzungen der zuvor festgelegten Schwellenwertregeln analysiert werden.

Sind Verletzungen aufgetreten, wird ein Link der **Schwellenwertverletzungen** in der Statusleiste des **Auslastungstest-Analyzers** mit der Anzahl der aufgetretenen Verletzungen angegeben. Klicken Sie auf den Link, um die Schwellenwertverletzungs-Tabelle anzuzeigen. Die Schwellenwertverletzungen können auch im Fenster **Indikatoren** und im Diagramm angezeigt werden.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="view-threshold-violations-in-the-table"></a>Anzeigen von Schwellenwertverletzungen in der Tabelle

In der Schwellenwertverletzungs-Tabelle werden die ersten 1.000 Verletzungen angezeigt. Die Tabelle enthält folgende Spalten:

|Column|BESCHREIBUNG|In der Standardeinstellung angezeigt|
|-|-|-|
|Time|Der Zeitpunkt während des Auslastungstests, an dem die Verletzung auftrat|Ja|
|Computer|Der Name des getesteten Computers, auf dem die Verletzung auftrat **Hinweis**: Dies ist wichtig, wenn Sie Auslastungstests auf Rigs ausführen.|Ja|
|Kategorie|Die Kategorie des Leistungsindikators, dessen Schwellenwert verletzt wurde|Ja|
|Leistungsindikator|Der Name des Leistungsindikators, dessen Schwellenwert verletzt wurde|Ja|
|Instanz|Die Instanz des Leistungsindikators, dessen Schwellenwert verletzt wurde|Ja|
|Nachricht|Eine Meldung mit einer Beschreibung der Schwellenwertverletzung Beispiel: **Der Wert 5 überschreitet den kritischen Schwellenwert 0**.|Ja|

> [!NOTE]
> Sie können die Tabelle sortieren, indem Sie die Spaltenüberschriften auswählen.

Weitere Informationen finden Sie unter [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Anzeigen von Schwellenwertverletzungen im Indikatorenfenster

Schwellenwertverletzungen können im **Indikatorenfenster** in der Struktur angezeigt werden, in der die Leistungsindikatoren für den Auslastungstest aufgeführt sind. Schwellenwertverletzungen werden im **Indikatorenfenster** durch Symbole dargestellt. Folgende Symbole werden verwendet:

Folgende Symbole werden verwendet:

![Keine Schwellenwertverletzung](../test/media/icon_ltest_1.gif) Keine Schwellenwertverletzung.

![Kritische Schwellenwertverletzung im letzten Intervall](../test/media/icon_ltest_2.gif) Eine kritische Schwellenwertverletzung ist im letzten Intervall aufgetreten.

![Kritische Schwellenwertverletzung in einem vorherigen Intervall](../test/media/icon_ltest_3.gif) Eine kritische Schwellenwertverletzung ist in einem vorherigen Intervall aufgetreten.

![Warnschwellenwertverletzung im letzten Intervall](../test/media/icon_ltest_4.gif) Eine Warnung für eine Schwellenwertverletzung ist im letzten Intervall aufgetreten.

![Warnschwellenwertverletzung in einem vorherigen Intervall](../test/media/icon_ltest_5.gif) Eine Warnung für eine Schwellenwertverletzung ist in einem vorherigen Intervall aufgetreten.

Optional können Schwellenwertverletzungen auch im Diagramm angezeigt werden. Das Schwellenwertsymbol wird im Diagramm neben dem Datenpunkt angezeigt, bei dem die Schwellenwertverletzung aufgetreten ist.

In der Indikatorstruktur werden Symbole für Schwellenwertverletzungen von den einzelnen Indikatorknoten auf den Stammknoten übertragen. So werden Sie auf Verletzungen von Indikatoren hingewiesen, die möglicherweise nicht in der Struktur sichtbar sind, wenn diese nicht erweitert wurde.

## <a name="view-threshold-violations-on-the-graph"></a>Anzeigen von Schwellenwertverletzungen im Diagramm

Schwellenwertverletzungen können im Diagramm angezeigt werden. Wie im **Indikatorenfenster** werden Schwellenwertverletzungen im Diagramm durch Symbole dargestellt. Die Symbole werden im Diagramm neben den Datenpunkten angezeigt, an denen die Schwellenwertverletzung auftrat. Wenn eine Schwellenwertverletzung für einen Indikator auftritt, der nicht im Diagramm angezeigt wird, können Sie den Indikator dem Diagramm hinzufügen, indem Sie ihn aus dem **Indikatorenfenster** in das Diagramm ziehen.

Weitere Informationen finden Sie unter [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Weitere Informationen

- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
