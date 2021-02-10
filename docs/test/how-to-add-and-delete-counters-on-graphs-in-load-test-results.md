---
title: Hinzufügen und Löschen von Indikatoren in Diagrammen in Auslastungstestergebnissen
description: Lernen Sie, einem Diagramm mithilfe des „Indikatorenfensters“ Leistungsindikatoren hinzuzufügen, und erfahren Sie mehr über die Eigenschaft „Samplingrate“.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: bbf233d025d168f3f9d197af5876a0d6e735a9e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942398"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>How to: Add and Delete Counters on Graphs in Load Test Results

Sie können das **Indikatorenfenster** verwenden, um einem Diagramm Leistungsindikatoren hinzuzufügen.

![Hinzufügen eines Zählers zu einem Diagramm](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Überlegungen zum Samplingintervall von Leistungsindikatoren**

Wählen Sie basierend auf der Länge des Auslastungstests einen Wert für die Eigenschaft **Samplingrate** in den Laufzeiteinstellungen des Auslastungstests aus. Eine kleinere Samplingrate (z. B. der Standardwert von fünf Sekunden) erfordert mehr Speicherplatz in der Datenbank für die Auslastungstestergebnisse. Bei längeren Auslastungstests wird durch eine höhere Samplingrate die gesammelte Datenmenge reduziert. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der Abtastrate](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Die folgende Tabelle enthält Richtlinien für die Samplingraten:

|Dauer des Auslastungstests|Empfohlene Samplingrate|
|-|-----------------------------|
|\< 1 Stunde|5 Sekunden|
|1 – 8 Stunden|15 Sekunden|
|8 – 24 Stunden|30 Sekunden|
|> 24 Stunden|60 Sekunden|

**Überlegungen zum Einschließen von Details der zeitlichen Steuerung zur Erfassung von prozentualen Daten**

In den Laufzeiteinstellungen im Auslastungstest-Editor ist eine Eigenschaft mit dem Namen **Speicher für Details der zeitlichen Steuerung** verfügbar. Wenn die Eigenschaft **Speicher für Details der zeitlichen Steuerung** aktiviert ist, werden die Zeiten für die Ausführung der einzelnen Tests, Transaktionen und Seiten beim Auslastungstest im entsprechenden Ergebnisrepository gespeichert. Dadurch können Daten für den 90. und 95. Prozentwert im **Auslastungstest-Analyzer** in den Tabellen „Tests“, „Transaktionen“ und „Seiten“ angezeigt werden.

Zum Aktivieren der Eigenschaft **Speicher für Details der zeitlichen Steuerung** sind zwei Optionen in den Laufzeiteinstellungseigenschaften verfügbar: **StatisticsOnly** und **AllIndividualDetails**. Mit beiden Optionen werden alle Einzeltests, Seiten und Transaktionen zeitlich gesteuert, und prozentuale Daten werden über die einzelnen Zeitsteuerungsdaten erfasst. Der Unterschied besteht darin, dass bei der Option **StatisticsOnly** die einzelnen Daten zur zeitlichen Steuerung aus dem Repository gelöscht werden, sobald die prozentualen Daten berechnet wurden. Dies reduziert den erforderlichen Speicherplatz im Repository, wenn Sie Details der zeitlichen Steuerung verwenden. Fortgeschrittene Benutzer möchten die Detaildaten der zeitlichen Steuerung jedoch möglicherweise mithilfe von SQL-Tools auf andere Weise verarbeiten. Wenn dies der Fall ist, sollte die Option **AllIndividualDetails** verwendet werden, damit die Detaildaten der zeitlichen Steuerung für diese Verarbeitung verfügbar sind. Wenn Sie die Eigenschaft auf **AllIndividualDetails** festlegen, können Sie zudem die Aktivitäten virtueller Benutzer nach Abschluss des Auslastungstests mithilfe des Diagramms für **Aktivitäten virtueller Benutzer** im **Auslastungstest-Analyzer** analysieren. Weitere Informationen finden Sie unter [Analysieren der Aktivität virtueller Benutzer in der Detailansicht](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Insbesondere bei langen Auslastungstests kann sehr viel Speicherplatz erforderlich sein, um Detaildaten der zeitlichen Steuerung im Ergebnisrepository für Auslastungstests zu speichern. Zudem nimmt das Speichern der Daten im Ergebnisrepository für Auslastungstests am Ende des Tests mehr Zeit in Anspruch, da die Daten bis zum Abschluss der Ausführung auf den Auslastungstests-Agents gespeichert werden. Bei der Beendigung des Auslastungstests werden die Daten im Repository gespeichert. Die Eigenschaft **Speicher für Details der zeitlichen Steuerung** ist standardmäßig aktiviert. Falls dies in Ihrer Testumgebung ein Problem ist, sollten Sie **Speicher für Details der zeitlichen Steuerung** auf **Keine** festlegen.

Weitere Informationen finden Sie unter [Gewusst wie: Angeben der Eigenschaft „Speicher für Details der zeitlichen Steuerung“](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>So zeigen Sie einen bestimmten Leistungsindikator in einem Auslastungstestdiagramm an

1. Klicken Sie nach Abschluss eines Auslastungstests oder nach dem Laden eines Auslastungstestergebnisses auf der Symbolleiste des Auslastungstest-Analyzers auf **Diagramme**.

     Der Bereich **Indikatoren** wird in der Diagrammansicht angezeigt.

    > [!NOTE]
    > Falls das **Indikatorenfenster** nicht angezeigt wird, klicken Sie auf der Symbolleiste auf **Indikatorenfenster anzeigen**.

2. Erweitern Sie im **Indikatorenfenster** Hierarchieknoten, bis Sie den gewünschten Leistungsindikator finden, der grafisch dargestellt werden soll.

     Um beispielsweise den Arbeitsspeicher anzuzeigen, der auf einem Testausführungscomputer verfügbar ist, erweitern Sie **Computer**, den Knoten des Computers und dann **Arbeitsspeicher**. Der Indikator **Verfügbare MB** wird angezeigt.

3. Klicken Sie auf das Diagramm, in dem der Leistungsindikator angezeigt werden soll.

4. Klicken Sie im Bereich **Indikatoren** mit der rechten Maustaste auf den Leistungsindikator, und klicken Sie auf **Indikator im Diagramm anzeigen**.

    > [!TIP]
    > Wenn die Daten des Leistungsindikators vorübergehend nicht im Diagramm angezeigt werden sollen, deaktivieren Sie in der Legende das Kontrollkästchen für den Leistungsindikator. So können die Statistiken für Minimal-, Maximal- und Mittelwert angezeigt werden, ohne die Trendlinie im Diagramm anzuzeigen. Dies kann beim Analysieren von Problemen nützlich sein, wenn das Diagramm mehrere überlappende Leistungsindikatorzeichnungen enthält. Weitere Informationen finden Sie unter [Verwenden der Legende der Diagrammansicht zum Analysieren von Auslastungstests](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5. Um die Leistungsindikatordaten aus dem Diagramm zu entfernen, klicken Sie in der Spalte **Indikator** der Legende mit der rechten Maustaste auf den Leistungsindikator, und klicken Sie auf **Löschen**.

     \- oder -

     Klicken Sie mit der rechten Maustaste auf die Datenlinie im Diagramm, und klicken Sie auf **Löschen**.

     \- oder -

     Klicken Sie in der Spalte **Indikator** der Legende oder in der Datenzeile im Diagramm auf den Leistungsindikator, und drücken Sie die **ENTF-TASTE**.

    > [!NOTE]
    > Es ist auch möglich, einen Leistungsindikator in der Legende, aber nicht im Diagramm anzuzeigen. Verwenden Sie dazu den Befehl **Indikator in Legende anzeigen**.

## <a name="see-also"></a>Weitere Informationen

- [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md)
- [How to: Create Custom Graphs (Vorgehensweise: Erstellen von benutzerdefinierten Diagrammen)](../test/how-to-create-custom-graphs-in-load-test-results.md)
