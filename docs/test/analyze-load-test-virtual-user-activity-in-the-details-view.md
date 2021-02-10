---
title: Analysieren des Auslastungstests über die Aktivität des virtuellen Benutzers
description: Erfahren Sie mehr über die Detailansicht, in der das Diagramm für Aktivitäten virtueller Benutzer angezeigt wird. Analysieren Sie, was einzelne virtuelle Benutzer während des Auslastungstests getan haben.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f7ae7afa183e2f23a46c8aa4c0b175aecdb44bd1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948087"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analysieren der Aktivität virtueller Benutzer bei Auslastungstests in der Detailansicht des Auslastungstest-Analyzers

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Diagramm für Aktivitäten virtueller Benutzer**

![Diagramm für Aktivitäten virtueller Benutzer](../test/media/virtual_actchart.png)

In der **Detailansicht** wird das **Diagramm für Aktivitäten virtueller Benutzer** angezeigt, das zur visuellen Analyse der Aktivitäten verwendet wird, die die einzelnen virtuellen Benutzer während des Auslastungstests ausgeführt haben. Im **Diagramm für Aktivitäten virtueller Benutzer** können Sie Benutzeraktivitäts- und Auslastungsmuster erkennen, fehlgeschlagene oder langsame Tests in Zusammenhang setzen und Anforderungen bei anderen Aktivitäten virtueller Benutzer anzeigen. Anhand des **Diagramms für Aktivitäten virtueller Benutzer** können Sie auch Spitzen in der CPU-Auslastung und Tiefstände bei den Anforderungen pro Sekunde erkennen und nachvollziehen, welche Tests oder Seiten während der Spitzen und Tiefstände ausgeführt wurden.

> [!NOTE]
> Bevor Sie den Auslastungstest ausführen, für den Sie das **Diagramm für Aktivitäten virtueller Benutzer** verwenden möchten, müssen Sie mithilfe des Auslastungstest-Editors überprüfen, ob die Eigenschaft **Speicher für Details der zeitlichen Steuerung** auf **AllIndividualDetails** festgelegt ist.

**Bereich „Detaillegende“**

![Detaillegendenbereich](../test/media/ltest_detailslegend.png)

Der Bereich „Detaillegende“ wird im **Diagramm für Aktivitäten virtueller Benutzer** angezeigt. Im Bereich "Detaillegende" können Sie Tests, Seiten und Transaktionen auf Grundlage unterschiedlicher Kriterien herausfiltern. Sie können z. B. bestimmte Tests aus der Ansicht bzw. alle erfolgreich verlaufenen Tests oder Tests entfernen, die aufgrund bestimmter Fehler fehlgeschlagen sind. Sie können auch alle Tests entfernen, für die keine Protokolle verfügbar sind.

Sie können fehlgeschlagene Tests markieren, woraufhin alle fehlgeschlagenen Tests rot hervorgehoben werden. Sie können auch Tests hervorheben, für die Testprotokolle vorhanden sind. Tests mit Protokollen erhalten die Farbe Grün.

**Bereich „Filterergebnisse“**

![Filterergebnisbereich](../test/media/ltest_filterresults.png)

Der Bereich „Filterergebnisse“ wird im **Diagramm für Aktivitäten virtueller Benutzer** angezeigt. Im Bereich "Filterergebnisse" können Sie Ergebnisse wie folgt filtern:

- **Nur Ergebnisse mit Protokollen anzeigen**: zeigt nur Testergebnisse an, denen Testprotokolle zugeordnet sind.

- **Erfolgreiche Ergebnisse anzeigen**: zeigt erfolgreiche Ergebnisse an.

- **Ergebnisse mit Fehlern anzeigen**: zeigt Ergebnisse mit Fehlern an, die beim Debuggen hilfreich sein können.

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-|-|
|**Ausführen des Auslastungstests:** Nachdem Sie einen Auslastungstest erstellt und ihn so konfiguriert haben, dass Daten zu den Aktivitäten virtueller Benutzer gesammelt werden, müssen Sie den Test vollständig ausführen, um das **Diagramm für Aktivitäten virtueller Benutzer** anzuzeigen.||
|**Anzeigen der Auslastungstestergebnisse, die Daten zu den Aktivitäten virtueller Benutzer enthalten:** Nach dem Erstellen, Konfigurieren und vollständigen Ausführen des Auslastungstests können Sie die Aktivitätsdaten virtueller Benutzer anzeigen, indem Sie das **Diagramm für Aktivitäten virtueller Benutzer** verwenden.|-   [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Vorgehensweise: Analysen der Aktivitäten virtueller Benutzer während eines Auslastungstests mithilfe des Diagramms für Aktivitäten virtueller Benutzer](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isolieren von Leistungsproblemen bei Auslastungstests:** Sie können mithilfe des **Diagramms für Aktivitäten virtueller Benutzer** Leistungsprobleme im Auslastungstest isolieren.|-   [Exemplarische Vorgehensweise: Verwenden des Diagramms für Aktivitäten virtueller Benutzer zum Isolieren von Problemen](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Siehe auch

- [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
