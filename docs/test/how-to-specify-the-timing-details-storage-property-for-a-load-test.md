---
title: Eigenschaft „Speicher für Details der zeitlichen Steuerung“ für Laufzeiteinstellungen von Auslastungstests
description: Hier erfahren Sie, wie Sie die Eigenschaft „Speicher für Details der zeitlichen Steuerung“ für eine Laufzeiteinstellung bearbeiten. Die Werte „Alle einzelnen Details“, „Keine“ und „Nur Statistik“ sind zulässig.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f208dd19674a257381db6feeaf47df5d3951ff9d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969294"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Vorgehensweise: Angeben der Eigenschaft „Speicher für Details der zeitlichen Steuerung“ für die Einstellung der Auslastungstestausführung

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Einstellungen mit dem **Auslastungstest-Editor** entsprechend Ihren Testanforderungen und -zielen ändern.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Sie können den Wert der Eigenschaft **Speicher für Details der zeitlichen Steuerung** einer Laufzeiteinstellung im Fenster **Eigenschaften** bearbeiten. Die Eigenschaft **Speicher für Details der zeitlichen Steuerung** kann auf eine der folgenden Optionen festgelegt werden:

- **Alle einzelnen Details:** Sammelt und speichert einzelne Zeitsteuerungsdaten für alle Tests, Transaktionen und Seiten, die während des Tests ausgegeben werden.

  > [!NOTE]
  > Die Option **Alle einzelnen Details** muss aktiviert werden, um Informationen zu virtuellen Benutzerdaten in den Auslastungstestergebnissen zu aktivieren. Weitere Informationen finden Sie unter [Analysieren der Aktivität virtueller Benutzer in der Detailansicht](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Keine**: Es werden keine einzelnen Details zur zeitlichen Steuerung erfasst. Die Durchschnittswerte sind jedoch nach wie vor verfügbar.

- **Nur Statistik**: speichert einzelne Zeitsteuerungsdaten, jedoch nur als prozentuale Daten. Dadurch werden Speicherplatzressourcen gespart.

  **Überlegungen zur Eigenschaft „Speicher für Details der zeitlichen Steuerung“**

  Wenn die Eigenschaft **Speicher für Details der zeitlichen Steuerung** aktiviert ist, werden die Zeiten für die Ausführung der einzelnen Tests, Transaktionen und Seiten beim Auslastungstest im entsprechenden Ergebnisrepository gespeichert. Dadurch können Daten für den 90. und 95. Prozentwert im **Auslastungstest-Analyzer** in den Tabellen **Tests**, **Transaktionen** und **Seiten** angezeigt werden.

  Wenn die Eigenschaft **Speicher für Details der zeitlichen Steuerung** mit dem Wert **StatisticsOnly** oder **AllIndividualDetails** aktiviert wird, werden alle einzelnen Tests, Seiten und Transaktionen zeitlich gesteuert, und aus den einzelnen Zeitsteuerungsdaten werden prozentuale Daten berechnet. Der Unterschied besteht darin, dass bei der Option **StatisticsOnly** die einzelnen Daten zur zeitlichen Steuerung aus dem Repository gelöscht werden, nachdem die prozentualen Daten berechnet wurden. Dies reduziert den erforderlichen Speicherplatz im Repository, wenn Details der zeitlichen Steuerung verwendet werden. Möglicherweise möchten Sie die Detaildaten der zeitlichen Steuerung jedoch mithilfe von SQL-Tools auf andere Weise verarbeiten. In diesem Fall sollten Sie die Option **AllIndividualDetails** verwenden, damit die Zeitsteuerungsdaten für diese Verarbeitung verfügbar ist. Wenn Sie die Eigenschaft auf **AllIndividualDetails** festlegen, können Sie zudem die Aktivitäten virtueller Benutzer nach Abschluss des Auslastungstests mithilfe des **Diagramms für Aktivitäten virtueller Benutzer** im **Auslastungstest-Analyzer** analysieren. Weitere Informationen finden Sie unter [Analysieren der Aktivität virtueller Benutzer in der Detailansicht](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  Insbesondere bei langen Auslastungstests kann sehr viel Speicherplatz erforderlich sein, um Detaildaten der zeitlichen Steuerung im Ergebnisrepository für Auslastungstests zu speichern. Zudem nimmt das Speichern der Daten im Ergebnisrepository für Auslastungstests am Ende des Tests mehr Zeit in Anspruch, da die Daten bis zum Abschluss der Ausführung auf den Auslastungstests-Agents gespeichert werden. Bei der Beendigung des Tests werden die Daten dann im Repository gespeichert. Die Eigenschaft **Speicher für Details der zeitlichen Steuerung** ist standardmäßig aktiviert. Falls dies in Ihrer Testumgebung ein Problem ist, sollten Sie **Speicher für Details der zeitlichen Steuerung** auf **Keine** festlegen.

  Die Detaildaten der zeitlichen Steuerung werden während des Testlaufs in der Datei *LoadTestItemResults.dat* gespeichert und nach Abschluss des Auslastungstests an den Controller zurückgesendet. Bei einem langen Auslastungstest ist die Datei groß. Dies ist ein Problem, wenn nicht genügend Speicherplatz auf dem Agent-Computer verfügbar ist.

  Wenn Sie ein Projekt von einer früheren Version des Visual Studio-Auslastungstests aktualisieren, verwenden Sie die folgende Prozedur, um eine vollständige Detailsammlung zu aktivieren.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>So konfigurieren Sie die Speichereigenschaft für Zeitsteuerungsdetails in einem Auslastungstest

1. Öffnen Sie im Auslastungstest-Editor einen Auslastungstest.

2. Erweitern Sie den Knoten **Laufzeiteinstellungen** im Auslastungstest.

3. Wählen Sie die Laufzeiteinstellungen, die Sie konfigurieren möchten, z.B. **Run Settings1[Active]** (Laufzeiteinstellungen1[Aktiv]).

4. Öffnen Sie das Fenster **Eigenschaften**. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

5. Wählen Sie unter der Kategorie **Ergebnisse** die Eigenschaft **Speicher für Details der zeitlichen Steuerung** aus, und wählen Sie dann **Alle einzelnen Details** aus.

     Nachdem Sie die Einstellung **Alle einzelnen Details** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** konfiguriert haben, können Sie Ihren Auslastungstest ausführen und das **Diagramm für die Aktivitäten virtueller Benutzer** anzeigen. Weitere Informationen finden Sie unter [How to: Analyze What Virtual Users Are Doing During a Load Test (Vorgehensweise: Analysieren der Aktivitäten virtueller Benutzer während eines Auslastungstests)](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Weitere Informationen

- [Analysieren der Aktivität virtueller Benutzer in der Detailansicht](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Exemplarische Vorgehensweise: Verwenden des Diagramms für Aktivitäten virtueller Benutzer zum Isolieren von Problemen](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
