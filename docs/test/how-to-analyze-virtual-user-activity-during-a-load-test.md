---
title: Analysieren der Aktivität virtueller Benutzer bei Auslastungstests
description: Lernen Sie, mit dem „Diagramm für Aktivitäten virtueller Benutzer“ anzuzeigen, ob die einzelnen virtuellen Benutzer während des Tests ausgeführt wurden, um die Muster der Benutzeraktivität und andere Informationen anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 353a38c17cdcd3358376547155750914e406f4be
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442390"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Vorgehensweise: Analysen der Aktivitäten virtueller Benutzer während eines Auslastungstests mithilfe des Diagramms für Aktivitäten virtueller Benutzer

Zeigen Sie die Aktivität des virtuellen Benutzers an, der mit Ihrem Auslastungstest verknüpft ist, indem Sie das **Diagramm für Aktivitäten virtueller Benutzer** verwenden. Jede Zeile im Diagramm stellt einen einzelnen virtuellen Benutzer dar. Das **Diagramm für Aktivitäten virtueller Benutzer** gibt genauen Aufschluss über die Aktionen der einzelnen virtuellen Benutzer während des Tests. Sie können Benutzeraktivitäts- und Auslastungsmuster erkennen, fehlgeschlagene oder langsame Tests in Zusammenhang setzen und Anforderungen bei anderen Aktivitäten virtueller Benutzer anzeigen. Das **Diagramm für die Aktivitäten virtueller Benutzer** ist erst nach dem Ausführen des Auslastungstests verfügbar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Die folgenden Prozeduren veranschaulichen das Anzeigen des **Diagramms für Aktivitäten virtueller Benutzer**, das Überprüfen einer Aktivität eines bestimmten Benutzers und das Verwenden der Filterung.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>So zeigen Sie das Diagramm für Aktivitäten virtueller Benutzer in den Auslastungstestergebnissen an

1. Konfigurieren Sie zum Anzeigen der virtuellen Benutzerdaten zunächst die Einstellung **Alle einzelnen Details** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung**, die dem Auslastungstest zugeordnet ist. Führen Sie anschließend den Auslastungstest aus.

2. Nach dem Ausführen des Auslastungstests wird die Zusammenfassungsseite mit den Testergebnissen angezeigt. Klicken Sie auf der Symbolleiste auf die Schaltfläche **Benutzerdetails**.

     - oder -

     Öffnen Sie die Diagrammansicht, indem Sie auf der Symbolleiste auf die Schaltfläche **Diagramme** klicken. Klicken Sie mit der rechten Maustaste auf ein Diagramm, und wählen Sie dann **Zu Benutzerdetail wechseln** aus.

     Wenn Sie diese Option verwenden, wird automatisch der Teil des **Diagramms für Aktivitäten virtueller Benutzer** vergrößert, auf den mit der rechten Maustaste geklickt wurde. Wenn sich der Zeiger z.B. ungefähr an der 30-Sekunden-Marke befindet, wird die Detailansicht in etwa an der 30-Sekunden-Marke im Tool **Zoom zum Zeitraum** am unteren Rand des **Diagramms für Aktivitäten virtueller Benutzer** angezeigt.

     Anschließend können Sie die Option zur Überprüfung bestimmter Benutzeraktivitätsdetails im **Diagramm für Aktivitäten virtueller Benutzer** verwenden.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>So überprüfen Sie eine bestimmte Benutzeraktivität im Diagramm für Aktivitäten virtueller Benutzer

1. Verwenden Sie das Tool „Zoom zum Zeitraum“ unten im **Diagramm für die Aktivitäten virtueller Benutzer**, um einen Bereich im Diagramm auszuwählen, in dem Sie die Details zu einem bestimmten Benutzer überprüfen möchten.

2. Zeigen Sie mit der Maus auf ein Detail im Diagramm. Die folgenden Informationen werden in der QuickInfo angezeigt:

   - **Benutzer-ID**

   - **Szenario**

   - **Test**

   - **URL** (wird nicht in einem Test oder einer Transaktion angezeigt)

   - **Ergebnis**

   - **Browser** (wird nicht in einem Test oder einer Transaktion angezeigt)

   - **Network**

   - **Startzeit**

   - **Duration**

   - **Agent**

   - **Testprotokoll** (Link zum Testprotokoll)

     > [!NOTE]
     > Wenn Sie auf den Link für das **Testprotokoll** klicken, wird zur Unterstützung des Debuggings der Anwendung das Webtestergebnis oder das Komponententestergebnis geöffnet, das dem Protokoll zugeordnet ist.

     Anschließend können Sie die Filter- und Hervorhebungsfunktionen für das **Diagramm für Aktivitäten virtueller Benutzer** verwenden.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>So verwenden Sie Filteroptionen im Diagramm für Aktivitäten virtueller Benutzer

1. Wählen Sie aus der Dropdownliste in der **Detaillegende** entweder **Test**, **Seite** oder **Transaktion** aus.

    **Bereich „Detaillegende“**

    ![Detaillegendenbereich](../test/media/ltest_detailslegend.png)

2. Aktivieren oder deaktivieren Sie die Kontrollkästchen für die Fehler, Protokolle, Tests, Suchvorgänge und ASPX-Seiten, die dem Auslastungstest zugeordnet sind.

    Das **Diagramm für Aktivitäten virtueller Benutzer** wird entsprechend aktualisiert.

    Das **Diagramm für Aktivitäten virtueller Benutzer** bietet die Möglichkeit, Tests, Seiten und Transaktionen auf Grundlage verschiedener Kriterien herauszufiltern. Sie können bestimmte Tests, alle erfolgreich verlaufenen Tests oder fehlgeschlagene Tests mit bestimmten Fehlern aus der Ansicht entfernen. Sie können auch alle Tests entfernen, für die keine Protokolle verfügbar sind.

    Sie können z.B. die Option **(Fehler hervorheben)** auswählen, durch die alle Fehler im Diagramm rot angezeigt werden. Sie können auch die Option **(Ergebnisse mit Protokollen hervorheben)** auswählen, um alle Testergebnisse mit Protokollen im Diagramm grün anzuzeigen.

    **Bereich „Filterergebnisse“**

    ![Filterergebnisbereich](../test/media/ltest_filterresults.png)

3. Aktivieren bzw. deaktivieren Sie in den **Filterergebnissen** die Kontrollkästchen für die folgenden Filteroptionen:

   - **Nur Ergebnisse mit Protokollen anzeigen**: zeigt nur Testergebnisse an, denen Testprotokolle zugeordnet sind.

   - **Erfolgreiche Ergebnisse anzeigen**: zeigt erfolgreiche Ergebnisse an.

   - **Ergebnisse mit Fehlern anzeigen** Zeigt Ergebnisse mit Fehlern an, die beim Debuggen hilfreich sein können.

     > [!NOTE]
     > Die unter dem Knoten **Ergebnisse mit Fehlern anzeigen** aufgeführte Liste von Fehlertypen kann genauer untersucht werden, indem Sie auf der Symbolleiste des **Webleistungstest-Ergebnisviewers** auf die Schaltfläche **Tabellen** klicken. Weitere Informationen finden Sie unter [Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     Das **Diagramm für Aktivitäten virtueller Benutzer** wird entsprechend aktualisiert.

## <a name="see-also"></a>Weitere Informationen

- [Analysieren der Aktivität virtueller Benutzer in der Detailansicht](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Exemplarische Vorgehensweise: Verwenden des Diagramms für Aktivitäten virtueller Benutzer zum Isolieren von Problemen](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)