---
title: Verwenden des Diagramms für Aktivitäten virtueller Benutzer bei Auslastungstests
description: Lernen Sie, wie Sie mit dem Diagramm für Aktivitäten virtueller Benutzer Fehler isolieren, die für einzelne virtuelle Benutzer aufgetreten sind, die den Auslastungstest ausführten.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: afe692a8333ff93f764a308bae2c1366e353b4a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967929"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Exemplarische Vorgehensweise: Verwenden des Diagramms für Aktivitäten virtueller Benutzer zum Isolieren von Problemen

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie mit dem Diagramm für Aktivitäten virtueller Benutzer Fehler isolieren, die für einzelne virtuelle Benutzer aufgetreten sind, durch die der Auslastungstest ausgeführt wurde.

Mit dem Diagramm für Aktivitäten virtueller Benutzer können die Aktivitäten von virtuellen Benutzern dargestellt werden, die dem Auslastungstest zugeordnet sind. Jede Zeile im Diagramm stellt einen einzelnen virtuellen Benutzer dar. Das Diagramm für Aktivitäten virtueller Benutzer gibt genauen Aufschluss über die Aktionen der einzelnen virtuellen Benutzer während des Tests. So können Sie Leistungsprobleme isolieren, indem Sie Muster der Benutzeraktivität anzeigen, Muster laden, fehlgeschlagene oder langsame Tests in Zusammenhang setzen und Anforderungen mit anderen Aktivitäten virtueller Benutzer anzeigen. Das Diagramm für die Aktivitäten virtueller Benutzer ist erst nach dem Ausführen des Auslastungstests verfügbar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio Enterprise

- Schließen Sie diese Verfahren ab:

  - [Aufzeichnen und Ausführen eines Webleistungstests](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests)

  - [Erstellen und Ausführen eines Auslastungstests](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Öffnen der in vorherigen exemplarischen Vorgehensweisen erstellten Projektmappe „ColorWebApp“

1. Öffnen Sie Visual Studio.

2. Öffnen Sie die Projektmappe **ColorWebApp**, die *LoadTest1.loadtest* enthält. Dieser Auslastungstest ergibt sich aus der Durchführung der Schritte in den drei exemplarischen Vorgehensweisen, die am Anfang dieses Themas im Abschnitt zu den erforderlichen Komponenten und Voraussetzungen aufgeführt sind.

     Bei den verbleibenden Schritten in dieser exemplarischen Vorgehensweise wird von einer Webanwendung mit dem Namen ColorWebApp, einem Webleistungstest mit dem Namen *ColorWebAppTest.webtest* und einem Auslastungstest mit dem Namen *LoadTest1.loadtest* ausgegangen.

## <a name="run-the-load-test"></a>Auslastungstest ausführen

Führen Sie den Auslastungstest aus, um Aktivitätsdaten von virtuellen Benutzern zu sammeln.

- Klicken Sie in der Symbolleiste im **Auslastungstest-Editor** auf die Schaltfläche **Ausführen**. Die Ausführung von "LoadTest1" beginnt.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Isolieren von Problemen im Diagramm für Aktivitäten virtueller Benutzer

Nach dem Ausführen des Auslastungstests und dem Sammeln der Aktivitätsdaten von virtuellen Benutzern können die Daten in den Auslastungstestergebnissen mithilfe der Detailansicht des **Auslastungstest-Analyzers** im **Diagramm für Aktivitäten virtueller Benutzer** angezeigt werden. Darüber hinaus können mithilfe des **Diagramms für Aktivitäten virtueller Benutzer** Leistungsprobleme im Auslastungstest isoliert werden.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>So verwenden Sie das Diagramm für Aktivitäten virtueller Benutzer in den Auslastungstestergebnissen

1. Nachdem die Ausführung des Auslastungstests abgeschlossen wurde, wird die Seite **Zusammenfassung** für die Auslastungstestergebnisse im **Auslastungstest-Analyzer** angezeigt. Klicken Sie auf der Symbolleiste auf die Schaltfläche **Diagramme**.

     Die Ansicht "Diagramme" wird angezeigt.

2. Klicken Sie im Diagramm **Seitenantwortzeit** mit der rechten Maustaste auf eine Stelle neben einem der Symbole für Schwellenwertverletzungen, und wählen Sie die Option **Zu Benutzerdetail wechseln** aus.

    > [!NOTE]
    > Sie können die Schaltfläche **Details** in der Symbolleiste des **Auslastungstest-Editors** verwenden, um auch das Diagramm für Benutzeraktivitäten zu öffnen. Wenn Sie jedoch die Option **Zu Benutzerdetail wechseln** verwenden, wird im **Diagramm für Aktivitäten virtueller Benutzer** automatisch die Ansicht des Teils des Tests vergrößert, auf den Sie im Diagramm mit der rechten Maustaste geklickt haben.

     Die Detailansicht wird angezeigt, wobei im **Diagramm für Aktivitäten virtueller Benutzer** der Zeitraum im Mittelpunkt steht, an dem Schwellenwertverletzungen aufgetreten sind.

     Auf der y-Achse stellen die horizontalen Elemente einzelne virtuelle Benutzer dar. Die x-Achse zeigt die Zeitachse für den Auslastungstestlauf an.

3. Stellen Sie im Tool **Zoom zum Zeitraum** unter dem **Diagramm für Aktivitäten virtueller Benutzer** die linken und rechten Schieberegler so ein, dass sich beide in der Nähe des Symbols für die Schwellenwertverletzung befinden. Hierdurch wird die Zeitskala im **Diagramm für Aktivitäten virtueller Benutzer** geändert.

4. Aktivieren Sie in der **Detaillegende** das Kontrollkästchen **(Fehler hervorheben)**. Der virtuelle Benutzer, der die Schwellenwertverletzung verursacht hat, wird hervorgehoben.

5. Deaktivieren Sie im Bereich **Filterergebnisse** die Kontrollkästchen **Erfolgreiche Ergebnisse anzeigen** und **HttpError**, aber lassen Sie das Kontrollkästchen **ValidationRuleError** aktiviert.

     Im **Diagramm für Aktivitäten virtueller Benutzer** werden nur diejenigen virtuellen Benutzer angezeigt, die mehr als drei Sekunden auf der Seite *Red.aspx* verbracht haben. Dieser Wert wurde in der vorherigen exemplarischen Vorgehensweise über die Schwellenwertverletzung konfiguriert.

6. Zeigen Sie mit der Maus auf die horizontale Linie, die den virtuellen Benutzer mit dem Validierungsregelfehler für die Schwellenwertverletzung darstellt.

7. Eine QuickInfo mit den folgenden Informationen wird angezeigt:

    - **Benutzer-ID**

    - **Szenario**

    - **Test**

    - **Ergebnis**

    - **Network**

    - **Startzeit**

    - **Duration**

    - **Agent**

    - **Testprotokoll**

8. Beachten Sie, dass **Testprotokoll** ein Link ist. Klicken Sie auf den Link **Testprotokoll**.

9. Der Webleistungstest „ColorWebTest“, der dem Protokoll zugeordnet ist, wird im **Webleistungstestergebnis-Viewer** geöffnet. So können Sie isolieren, wo die Schwellenwertverletzungen aufgetreten sind.

     Sie können verschiedene Einstellungen in den Bereichen **Detaillegende** und **Filterergebnisse** verwenden, um Leistungsprobleme und Fehler in den Auslastungstests leichter zu isolieren. Experimentieren Sie mit diesen Einstellungen und mit dem Tool **Zoom zum Zeitraum**, um zu sehen, wie die Daten für virtuelle Benutzer im **Diagramm für Aktivitäten virtueller Benutzer** dargestellt werden.

## <a name="see-also"></a>Weitere Informationen

- [Analysieren der Aktivität virtueller Benutzer in der Detailansicht](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
- [How to: Erstellen einer Testeinstellung für einen verteilten Auslastungstest](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)
- [Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen](../test/collect-diagnostic-information-using-test-settings.md)
