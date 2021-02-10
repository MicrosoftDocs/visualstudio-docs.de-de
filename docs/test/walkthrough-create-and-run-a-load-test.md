---
title: Erstellen und Ausführen eines Auslastungstests
description: Lernen Sie, einen Auslastungstest zu erstellen, der Komponententests enthält. Auslastungstests werden mithilfe von Visual Studio Enterprise erstellt und ausgeführt.
ms.custom: SEO-VS-2020
ms.date: 10/01/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, in load tests
- unit tests, load test walkthrough
- load tests, walkthrough
ms.assetid: bbf075a5-96d5-48ed-a03c-330f0fc04748
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 888bf1f699027ab883a01ba74d8efc5703c91c9a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968969"
---
# <a name="walkthrough-create-and-run-a-load-test-that-contains-unit-tests"></a>Exemplarische Vorgehensweise: Erstellen und Ausführen eines Auslastungstests, der Komponententests enthält

In dieser exemplarischen Vorgehensweise erstellen Sie einen Auslastungstest, der Komponententests enthält.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Diese exemplarische Vorgehensweise enthält ausführliche Anweisungen zum Erstellen und Ausführen eines Auslastungstests mithilfe von Visual Studio Enterprise. Ein Auslastungstest ist ein Container für Webleistungs- und Komponententests. Auslastungstests werden mit dem **neuen Auslastungstest-Assistenten** erstellt.

Ein Auslastungstest stellt außerdem eine Vielzahl von Laufzeiteigenschaften zur Verfügung, die angepasst werden können, um die gewünschte Auslastungssimulation herzustellen. In dieser exemplarischen Vorgehensweise verwenden Sie den **neuen Auslastungstest-Assistenten**, um Komponententests zu einem Auslastungstest hinzuzufügen.

Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus:

- Erstellen Sie einen Auslastungstest, in dem Komponententests verwendet werden.

- Ändern einiger Auslastungstesteinstellungen

- Ausführen eines Auslastungstests

- Führen Sie die Schritte unter [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) aus, um eine einfache C#-Klassenbibliothek zu erstellen, die ein Webleistungs- und Auslastungstestprojekt mit einigen Komponententests enthält.

## <a name="create-a-load-test-containing-unit-tests-using-the-new-load-test-wizard"></a>Erstellen eines Auslastungstests mit Komponententests mithilfe des neuen Auslastungstest-Assistenten

### <a name="to-start-the-new-load-test-wizard"></a>So starten Sie den Assistenten für den neuen Auslastungstest

1. Vergewissern Sie sich, dass Sie die Komponente **Tools für Webleistung und Auslastungstests** wie unter [Erstellen eines Auslastungstestprojekts](../test/quickstart-create-a-load-test-project.md) beschrieben installiert haben.

1. Öffnen Sie die Bank-Projektmappe, die Sie in [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) erstellt haben.

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für den Bank-Projektmappenknoten, klicken Sie auf **Hinzufügen** und dann auf **Neues Projekt**.

     Das Dialogfeld **Neues Projekt hinzufügen** wird angezeigt.

1. Erweitern Sie im Dialogfeld **Neues Projekt hinzufügen** die Option **Visual C#** , und wählen Sie **Test** aus. Wählen Sie aus der Liste der Vorlagen **Testprojekt für Webleistung und Auslastung** aus, und geben Sie `BankLoadTest` im Feld **Name** ein. Klicken Sie auf **OK**.

     Das BankLoadTest-Testprojekt für Webleistung und Auslastung wird der Projektmappe hinzugefügt.

1. Öffnen Sie das Kontextmenü für das neue BankLoadTest-Testprojekt für Webleistung und Auslastung, klicken Sie auf **Hinzufügen**, und wählen Sie dann **Auslastungstest** aus.

1. Der **Assistent für neuen Auslastungstest** wird gestartet.

1. Die erste Seite des **Assistenten für neuen Auslastungstest** ist die Seite **Willkommen**.

1. Wählen Sie **Weiter** aus.

### <a name="to-edit-settings-for-load-test-scenario"></a>So bearbeiten Sie die Einstellungen für Auslastungstestszenarien

1. Geben Sie im Textfeld **Namen für das Auslastungstestszenario eingeben****ScenarioSample** ein.

     Ein *Szenario* ist ein Gruppierungsmechanismus. Es besteht aus einem Satz von Tests und den Eigenschaften zum Ausführen dieser Tests unter Last.

2. Legen Sie das **Reaktionszeitprofil** auf `Use normal distribution centered on recorded think times` fest. Die Reaktionszeit stellt die Zeit dar, für die ein Benutzer eine Webseite betrachtet, bevor er zur nächsten Seite wechselt.

1. Klicken Sie auf **Weiter**, wenn Sie fertig sind.

### <a name="to-edit-load-pattern-setting-for-test-scenario"></a>So bearbeiten Sie die Auslastungsmustereinstellung für Testszenarien

1. Klicken Sie auf **Schrittweise Auslastung**.

    > [!NOTE]
    > Sie können unter zwei Typen von Auslastungsmustern wählen: konstant und schrittweise. Jeder Typ hat bei Auslastungstests seine Funktion, für diese exemplarische Vorgehensweise sollten Sie jedoch **Schrittweise Auslastung** auswählen.

2. Legen Sie für **Benutzeranzahl (Anfang)** 10 Benutzer fest.

3. Legen Sie für **Schrittdauer** 10 Sekunden fest.

4. Legen Sie für **Benutzeranzahl pro Schritt** 10 Benutzer/Schritt fest.

5. Legen Sie für **Maximale Benutzeranzahl** 100 Benutzer fest.

6. Wählen Sie **Weiter** aus.

### <a name="to-select-test-mix-model-for-the-scenario"></a>So wählen Sie ein Testmischungsmodell für das Szenario aus

1. Wählen Sie unter **Wie soll die Testmischung modelliert werden?** den Eintrag **Auf Grundlage der Gesamtzahl der Tests** aus.

2. Wählen Sie **Weiter** aus.

### <a name="to-add-unit-tests-to-the-scenario"></a>So fügen Sie dem Szenario Komponententests hinzu

1. Der nächste Schritt lautet **Tests zu einem Auslastungstestszenario hinzufügen und die Testmischung bearbeiten**.

2. Klicken Sie auf **Hinzufügen**, um Tests auszuwählen.

3. Wählen Sie die **CreditTest**-Komponente aus, die im Bereich **Verfügbare Tests** aufgeführt sind, der alle Webleistungstests und Komponententests im Webleistungs- und Auslastungstestprojekt enthält.

4. Klicken Sie auf den Pfeil, um den **CreditTest**-Komponententest zum Bereich **Ausgewählte Tests** hinzuzufügen.

5. Wiederholen Sie die Schritte 3 und 4 für den **DebitTest**- und den **FreezeAccountTest**-Komponententest.

6. Klicken Sie auf **OK**, wenn Sie die drei Komponententests hinzugefügt haben.

     Die Testmischung wird angezeigt.

7. Verschieben Sie den Schieberegler unter **Verteilung** für den **CreditTest** etwas nach rechts, um die Testverteilung anzupassen. Die anderen Schieberegler werden automatisch nach links bewegt, damit die Verteilung weiterhin bei 100 % liegt.

8. Wählen Sie **Weiter** aus.

### <a name="to-select-network-mix-for-test-scenario"></a>So wählen Sie eine Netzwerkmischung für Testszenarien aus

1. Wählen Sie den LAN-Verbindungstyp aus, den Sie der Netzwerkbandbreitenmischung hinzufügen möchten.

     Sie können weitere Netzwerktypen hinzufügen. Verwenden Sie die Schieberegler, um die Testverteilung und die Gewichtung einzustellen.

2. Wählen Sie **Weiter** aus.

### <a name="to-specify-computers-to-monitor-with-counter-sets-during-load-test-run"></a>So geben Sie während Auslastungstestläufen mit Indikatorensätzen zu überwachende Computer an

1. Wählen Sie **Weiter** aus.

     Weitere Informationen zu Indikatorensätzen finden Sie unter [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

### <a name="to-edit-run-setting-for-load-test"></a>So bearbeiten Sie Testlaufeinstellungen für Auslastungstests

1. Klicken Sie auf **Dauer des Testlaufs**, und legen Sie anschließend **Testlaufdauer** auf „2 Minuten“ fest, um für den Auslastungstest eine *Feuerprobe* auszuführen.

     Beim Erstellen von Auslastungstests empfiehlt es sich, zu überprüfen, ob alle Werte ordnungsgemäß konfiguriert wurden und der Test wie erwartet abläuft. Hierzu führen Sie einen kurzen Auslastungstest mit geringer Auslastung durch. Dieser Prozess wird als *Feuerprobe* bezeichnet.

2. Klicken Sie auf **Fertig stellen**. Der Auslastungstest wird im **Auslastungstest-Editor** geöffnet.

## <a name="run-the-load-test"></a>Auslastungstest ausführen
 Nachdem Sie den Auslastungstest erstellt haben, führen Sie ihn aus, um die Reaktion der Bankanwendung auf die Auslastungssimulation zu überprüfen. Während der Ausführung eines Auslastungstests wird das Fenster **Auslastungstest-Analyzer** angezeigt.

### <a name="to-run-the-load-test"></a>So führen Sie den Auslastungstest aus

1. Wenn ein Auslastungstest im **Auslastungstest-Editor** geöffnet ist, klicken Sie auf der Symbolleiste auf die grüne Schaltfläche **Test ausführen**. Der Auslastungstest wird gestartet.

2. Wenn bei der Testsimulation bestimmte Schwellenwerte überschritten werden, weisen Symbole in den Strukturansichtsknoten auf die Schwellenwertverletzung hin. Fehler werden mit einem roten Kreis und Warnungen mit einem gelben Dreieck gekennzeichnet. Sie können einen den Schwellenwert übersteigenden Indikator lokalisieren und anschließend grafisch darstellen, indem Sie das Symbol auf das Diagramm ziehen. Dies kann während der Ausführung des Tests erfolgen.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten der Testmischung zur Angabe der Webbrowsertypen in einem Auslastungstestszenario](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Angeben von virtuellen Netzwerktypen](../test/specify-virtual-network-types-in-a-load-test-scenario.md)
- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
