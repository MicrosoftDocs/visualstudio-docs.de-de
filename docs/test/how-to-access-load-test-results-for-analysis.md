---
title: Analysieren von Auslastungstestergebnissen
description: Lernen Sie, entweder automatisch über den Auslastungstest-Analyzer oder manuell für Tests über die Befehlszeile für die Analyse auf Auslastungstestergebnisse zuzugreifen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load test results, accessing
- Load Test Viewer
- load tests, accessing
- load tests, analyzing
- load tests, results
- Load Test Viewer, viewing
ms.assetid: b0a3e694-2894-479b-b270-7e61e9fafacd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 5d3d52266bf94c0badefb71d5109ad393e071db5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970451"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Vorgehensweise: Zugreifen auf Auslastungstestergebnisse für die Analyse

Wenn Sie einen Auslastungstest im Auslastungstest-Editor ausführen, werden die Auslastungstestergebnisse automatisch geöffnet, und der laufende Test wird im **Auslastungstest-Analyzer** angezeigt. Wenn Sie einen Auslastungstest von der Befehlszeile ausführen, müssen Sie auf die Auslastungstestergebnisse manuell zugreifen.

Das Auslastungstestergebnis für den abgeschlossenen Auslastungstest enthält Leistungsindikatorsamplings und Fehlerinformationen, die in regelmäßigen Abständen von den Testcomputern erfasst wurden. Im Verlauf eines Auslastungstestlaufs kann eine große Anzahl von Leistungsindikatorsamplings erfasst werden. Die Menge gesammelter Leistungsdaten hängt von der Länge des Testlaufs, dem Samplingintervall, der Anzahl von Testcomputern, der Anzahl erfasster Indikatoren, den konfigurierten Datensammlern und den Protokollierungsebenen ab. Bei einem großen Auslastungstest kann die gesammelte Menge von Leistungsdaten leicht mehrere Gigabytes betragen. Weitere Informationen finden Sie im Artikel zu [Testcontrollern und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>So greifen Sie auf ein Auslastungstestergebnis zu

1. Öffnen Sie in einem Webleistungs- und Auslastungstestprojekt einen Auslastungstest.

2. Klicken Sie auf der Symbolleiste des Auslastungstest-Editors auf die Schaltfläche **Ergebnisse öffnen und verwalten**.

     Das Dialogfeld **Ergebnisse öffnen und verwalten** wird angezeigt.

3. Wählen Sie unter **Enter a controller name to find load test results** (Controllernamen für die Suche nach Auslastungstestergebnissen eingeben) einen Controller aus. Wählen Sie **\<local> - No controller>** (<Lokal – Kein Controller>) aus, um auf lokal gespeicherte Ergebnisse zuzugreifen.

4. Wählen Sie unter **Show results for the following load test** (Ergebnisse für den folgenden Auslastungstest anzeigen) den Auslastungstest aus, dessen Ergebnisse angezeigt werden sollen. Wählen Sie **\<Show results for all tests>** aus, um alle Ergebnisse für alle Tests anzuzeigen.

     Wenn Auslastungstestergebnisse verfügbar sind, werden diese in der Liste **Auslastungstestergebnisse** angezeigt. Die Spalten lauten **Time**, **Duration**, **User**, **Outcome**, **Test**, and **Description** (Zeit, Dauer, Benutzer, Ergebnis, Test und Beschreibung). **Test** ist der Name des Tests und unter **Beschreibung** wird die optionale Beschreibung angegeben, die vor der Ausführung des Tests hinzugefügt wurde.

    > [!NOTE]
    > Die Ergebnisse werden mit den neuesten Ergebnissen am Anfang der Liste angezeigt.

5. Wählen Sie in der Liste **Auslastungstestergebnisse** die zu analysierenden Auslastungstestergebnisse aus, und klicken Sie auf **Öffnen**.

6. Der **Auslastungstest-Analyzer** wird angezeigt. Das ausgewählte Auslastungstestergebnis wird in der Zusammenfassungsansicht angezeigt. Weitere Informationen finden Sie unter [Übersicht der Auslastungstestergebnisse](../test/load-test-results-summary-overview.md).

     Im Dialogfeld **Ergebnisse öffnen und verwalten** können Sie andere Aspekte von Auslastungstests verwalten, etwa das Importieren, Exportieren und Entfernen von Auslastungstestergebnissen. Weitere Informationen finden Sie unter [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Siehe auch

- [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
