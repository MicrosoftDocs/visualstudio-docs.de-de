---
title: Emulieren eines realen Verwendungsszenarios einer Website für Auslastungstests
description: Verwenden Sie Auslastungsmodelloptionen, um die realen Erwartungen an eine Website oder Anwendung, für die Sie einen Auslastungstest ausführen, genauer vorauszusagen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: e79d6e92df6f2b22fdced488b74f072b57fb8d84
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887860"
---
# <a name="test-mix-models-overview"></a>Testmischungsmodelle – Übersicht

Sie können Auslastungsmodelloptionen verwenden, um die realen Erwartungen an eine Website oder Anwendung, für die Sie einen Auslastungstest ausführen, genauer vorauszusagen. Dies ist wichtig, da ein Auslastungstest, der nicht auf einem genauen Auslastungsmodell basiert, irreführende Ergebnisse generieren kann.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="test-mix-model-enhancements"></a>Verbesserungen hinsichtlich des Testmischungsmodells

Mit dem Auslastungstest-Editor oder dem Assistenten für Testmischungsmodelle können Sie die folgenden Testmischungstypen für ein Auslastungstestszenario angeben. Weitere Informationen finden Sie unter [Ändern des Testmischungsmodells in einem Szenario](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Sie können eine der folgenden Testmischungsmodelloptionen für das Auslastungstestszenario angeben:

- **Auf Grundlage der Gesamtzahl der Tests:** Bestimmt, welcher Webleistungs- oder Komponententest ausgeführt wird, wenn ein virtueller Benutzer eine Testiteration startet. Am Ende des Auslastungstests stimmt die Häufigkeit der Ausführung eines bestimmten Tests mit der zugewiesenen Testverteilung überein. Verwenden Sie dieses Testmischungsmodell, wenn die Testmischung auf Transaktionsprozentsätzen in einem IIS-Protokoll oder in Produktionsdaten basiert. Weitere Informationen finden Sie in [Prozentsatz nach gestarteten Tests](#BasedOnTestsStarted).

- **Auf Grundlage der Anzahl der virtuellen Benutzer:** Bestimmt den Prozentsatz von virtuellen Benutzern, die einen bestimmten Webleistungs- oder Komponententest ausführen werden. An jedem Punkt im Auslastungstest stimmt die Anzahl der Benutzer, die einen bestimmten Test ausführen, mit der zugewiesenen Verteilung überein. Verwenden Sie dieses Testmischungsmodell, wenn die Testmischung auf dem Prozentsatz von Benutzern, die einen bestimmten Test ausführen, basiert. Weitere Informationen finden Sie unter [Prozentsatz nach virtuellen Benutzern](#PercentageBasedonVirtualUsers).

- **Auf Grundlage der Benutzergeschwindigkeit:** Im Verlauf des Auslastungstests wird jeder Webleistungstest oder Komponententest so oft wie angegeben pro Benutzer und pro Stunde ausgeführt. Verwenden Sie dieses Testmischungsmodell, wenn Sie möchten, dass virtuelle Benutzer im Laufe des Auslastungstests Tests mit einer bestimmten Geschwindigkeit ausführen. Weitere Informationen finden Sie unter [Bestimmen der Geschwindigkeit bei der Testmischung](#PacingTestMix).

    > [!TIP]
    > Wann wählen Sie **Testmischungsprozentsatz** und wann **Prozentsatz nach virtuellen Benutzern** aus? Der Unterschied zwischen diesen beiden Auswahlmöglichkeiten kommt zum Tragen, wenn einige Tests in der Testmischung länger dauern als andere Tests. In dieser Situation sollten Sie vorzugsweise **Prozentsatz nach virtuellen Benutzern** auswählen. Durch diese Auswahl können Sie einen Testlauf vermeiden, bei dem eine hohe Wahrscheinlichkeit besteht, dass zu viele Benutzer Tests von langer Dauer ausführen. Wenn die Tests jedoch alle eine ähnliche Dauer haben, ist die Auswahl von **Testmischungsprozentsatz** sicherer.

- **Auf Grundlage der sequenziellen Reihenfolge:** Jeder virtuelle Benutzer führt die Webleistungstests oder Komponententests in der Reihenfolge aus, in der sie im Szenario definiert sind. Der virtuelle Benutzer durchläuft die Tests in dieser Reihenfolge so lange, bis der Auslastungstest abgeschlossen ist. Weitere Informationen finden Sie unter [Sequenzielle Reihenfolge](#SequentialOrder).

### <a name="percentage-based-on-tests-started"></a><a name="BasedOnTestsStarted"></a> Prozentsatz nach gestarteten Tests

Für jeden Test in der Mischung können Sie einen Prozentsatz angeben, durch den bestimmt wird, wie häufig der Test als nächster Test zur Ausführung ausgewählt wird. Beispielsweise können die folgenden Prozentsatzwerte drei Tests zugewiesen werden:

- TestA (50 %)

- TestB (35 %)

- TestC (15 %)

Wenn Sie diese Einstellung verwenden, basiert der nächste zu startende Test auf den zugewiesenen Prozentsätzen. Dabei wird die Anzahl der virtuellen Benutzer, die die einzelnen Tests gerade ausführen, nicht berücksichtigt.

### <a name="percentage-based-on-virtual-users"></a><a name="PercentageBasedonVirtualUsers"></a> Prozentsatz nach virtuellen Benutzern
Dieses Testmischungsmodell bestimmt den Prozentsatz virtueller Benutzer, die einen bestimmten Test ausführen. Wenn Sie dieses Testmischungsmodell verwenden, basiert der nächste zu startende Test nicht nur auf den zugewiesenen Prozentsätzen, sondern auch auf dem Prozentsatz der virtuellen Benutzer, die derzeit einen bestimmten Test ausführen. An jedem Punkt im Auslastungstest stimmt die Anzahl der Benutzer, die einen bestimmten Test ausführen, so genau wie möglich mit der zugewiesenen Verteilung überein.

### <a name="pacing-test-mix"></a><a name="PacingTestMix"></a> Bestimmen der Geschwindigkeit bei der Testmischung

Wenn Sie eine Geschwindigkeit für die Testmischung angeben, legen Sie für jeden Test in der Testmischung und für jeden virtuellen Benutzer eine Testausführungsgeschwindigkeit fest. Diese Geschwindigkeit wird für jeden Test durch die Anzahl von Tests ausgedrückt, die pro Stunde von jedem virtuellen Benutzer ausgeführt werden. Beispielsweise können Sie diesen Tests folgende Geschwindigkeiten bei der Testmischung zuweisen:

- TestA: 4 Tests pro Benutzer pro Stunde

- TestB: 2 Tests pro Benutzer pro Stunde

- TestC: 0,125 Tests pro Benutzer pro Stunde

Wenn Sie das Testmischungsmodell mit Geschwindigkeitsangabe verwenden, wird durch die Auslastungstestruntime-Engine sichergestellt, dass die tatsächliche Geschwindigkeit, mit der Tests gestartet werden, kleiner oder gleich der festgelegten Geschwindigkeit ist. Wenn die Tests angesichts der zugewiesenen Anzahl abzuschließender Tests zu lange dauern, wird ein Fehler zurückgegeben.

Die Einstellung **Reaktionszeit zwischen Testiterationen** gilt nicht, wenn Sie eine Geschwindigkeit für die Testmischung angeben.

#### <a name="apply-distribution-to-pacing-delay"></a>Anwenden der Verteilung auf die Geschwindigkeitsverzögerung
Der Wert für die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** in einem Auslastungstestszenario kann auf TRUE oder FALSE festgelegt werden:

- **TRUE**: Das Szenario wendet typische statistische Verteilungsverzögerungen an, die über den Wert in der Spalte **Tests pro Benutzer und Stunde** im Dialogfeld **Testmischung bearbeiten** angegeben werden. Weitere Informationen finden Sie unter [Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Beispiel: Der Wert für **Tests pro Benutzer und Stunde** im Dialogfeld **Testmischung bearbeiten** für den Test ist auf zwei Benutzer pro Stunde festgelegt. Ist die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** auf **TRUE** festgelegt, wird auf die Wartezeit zwischen den Tests eine typische statistische Verteilung angewendet. Es werden weiterhin zwei Tests pro Stunde ausgeführt, zwischen ihnen vergehen jedoch nicht notwendigerweise 30 Minuten. Der erste Test konnte nach 4 Minuten und der zweite Test nach 45 Minuten ausgeführt werden.

- **FALSE**: Die Tests werden mit der Geschwindigkeit ausgeführt, die Sie für den Wert in der Spalte **Tests pro Benutzer und Stunde** im Dialogfeld **Testmischung bearbeiten** angegeben haben. Weitere Informationen finden Sie unter [Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

   Beispiel: Der Wert für **Tests pro Benutzer und Stunde** im Dialogfeld **Testmischung bearbeiten** für den Test ist auf zwei Benutzer pro Stunde festgelegt. Wenn die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** auf **FALSE** festgelegt ist, ist im Grunde kein Spielraum für die Testausführung vorhanden. Der Test wird alle 30 Minuten ausgeführt. So ist sichergestellt, dass Sie zwei Tests pro Stunde ausführen.

  Weitere Informationen finden Sie unter [Vorgehensweise: Anwenden der Verteilung auf die Geschwindigkeitsverzögerung beim Verwenden eines Testmischungsmodells für die Benutzergeschwindigkeit](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

### <a name="sequential-order"></a><a name="SequentialOrder"></a> Sequenzielle Reihenfolge
Wenn die Option "Basierend auf sequenzieller Testreihenfolge" aktiviert ist, führt jeder virtuelle Benutzer alle Tests in dem Szenario in der Reihenfolge aus, in der die Tests definiert wurden.

## <a name="test-iterations-property"></a>Eigenschaft „Testiterationen“
In den Testlaufeinstellungseigenschaften können Sie einen Wert für die Testiterationen-Eigenschaft angeben. Dieser Wert entspricht der Anzahl von Testiterationen, die in einem Auslastungstest ausgeführt werden sollen. Nachdem die angegebene Anzahl von Testiterationen gestartet wurde, werden unabhängig von den Einstellungen beliebiger Auslastungsprofile keine zusätzlichen Testiterationen gestartet. Nachdem die angegebene Anzahl der Testiterationen abgeschlossen wurde, wird der Auslastungstest beendet. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der Anzahl von Testiterationen in einer Testlaufeinstellung für Auslastungstests](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Initialisierungs- und Beendigungstests
Sie können Tests auswählen, die am Anfang und Ende der Auslastungstestsitzung jedes virtuellen Benutzers ausgeführt werden sollen. Weitere Informationen finden Sie unter [Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

- **Initialisierungstest** Dieser Test wird von jedem virtuellen Benutzer ausgeführt, bevor ein beliebiger Test aus der Testmischung ausgeführt wird.

- **Beendigungstest** Dieser Test wird ausgeführt, nachdem alle Tests für einen bestimmten virtuellen Benutzer ausgeführt wurden.

  Beachten Sie Folgendes im Zusammenhang mit Initialisierungs- und Beendigungstests:

- Sie können die Auslastungstestdauer nach Zeit anstatt der Anzahl der Iterationen angeben. Nach Ablauf der Dauer des Auslastungstests wird der Beendigungstest nicht ausgeführt.

- Wenn der Initialisierungstest ein Komponententest oder Webleistungstest ist, wird der Zustand des TestContext-Objekts oder WebTestContext-Objekts nach Beendigung des Initialisierungstests gespeichert. Er wird daraufhin als Startkontext für Testiterationen in der Testmischung verwendet.

- Neue Benutzer, so wie sie in der Szenarioeigenschaft Prozentsatz neuer Benutzer festgelegt sind, führen immer den Initialisierungstest, eine Testiteration aus der Testmischung und den Beendigungstest aus.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Bearbeiten der Testmischung zur Angabe der Webbrowsertypen in einem Auslastungstestszenario](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
- [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md)
- [Ändern des Testmischungsmodells in einem Szenario](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
