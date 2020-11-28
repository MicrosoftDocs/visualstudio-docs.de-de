---
title: Auslastungsmuster für Auslastungstests
description: Erfahren Sie mehr über die integrierten Auslastungsmuster, die Visual Studio bereitstellt. Wählen Sie das Auslastungsmuster aus, und passen Sie die Werte der Eigenschaften Ihrem Auslastungstest an.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c46c353b09df792b2e204ce90a04b372e23ebd8b
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440258"
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten

Die Auslastungsmustereigenschaften geben an, wie die simulierte Benutzerauslastung während eines Auslastungstests angepasst wird. Visual Studio stellt drei integrierte Auslastungsmuster bereit: „konstant“, „schrittweise“ und „zielbasiert“. Sie wählen das Auslastungsmuster aus und passen die Werte der Eigenschaften entsprechend Ihren Anforderungen an den Auslastungstest an.

Bei dem Auslastungsmuster handelt es sich um die Komponente eines Szenarios. Die Szenarien umfassen zusammen mit ihren definierten Auslastungsmustern einen Auslastungstest.

> [!NOTE]
> In allen Auslastungsmustern ist die von Visual Studio generierte Last eine simulierte Auslastung der virtuellen Benutzer.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-patterns"></a>Auslastungsmuster

### <a name="constant"></a>Konstante

Mit dem Muster für konstante Auslastung wird eine Benutzerauslastung angegeben, die sich während des Auslastungstests nicht ändert. Beispielsweise können Sie bei einer Feuerprobe für eine Webanwendung eine kleine und konstante Auslastung mit 10 Benutzern festlegen.

#### <a name="constant-load-pattern-considerations"></a>Überlegungen zu konstanten Auslastungsmustern

Ein konstantes Auslastungsmuster wird verwendet, um bei der Ausführung eines Auslastungstests die gleiche Benutzerauslastung auszuführen. Achten Sie darauf, ein konstantes Auslastungsmuster nicht mit einer hohen Benutzeranzahl zu verwenden. Dadurch werden am Anfang des Auslastungstests die Server möglicherweise unangemessen und unrealistisch stark belastet. Wenn der Auslastungstest z.B. einen Webtest enthält, der mit einer Anforderung an eine Homepage beginnt und Sie den Auslastungstest mit einer konstanten Auslastung von 1.000 Benutzern einrichten, sendet der Auslastungstest die ersten 1.000 Anforderungen möglichst schnell an die Homepage. Dies ist möglicherweise keine realistische Simulation von realem Zugriff auf die Website. Um das zu verhindern, können Sie ein schrittweises Auslastungsmuster verwenden, das allmählich auf 1.000 Benutzer ansteigt, oder geben Sie in den Testlaufeinstellungen für Auslastungstests eine Aufwärmphase an. Wenn eine Aufwärmphase angegeben wird, erhöht der Auslastungstest automatisch allmählich die Auslastung während der Aufwärmphase. Weitere Informationen finden Sie unter [Konfigurieren von Szenariostartverzögerungen](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Schritt

Mit dem Muster für schrittweise Auslastung wird eine Benutzerauslastung angegeben, die mit der Zeit gesteigert wird, bis eine maximale Benutzerauslastung erreicht wird. Für eine schrittweise Auslastung geben Sie die folgenden Informationen an: **Benutzeranzahl (ursprünglich)**, **Maximale Benutzeranzahl**, **Schrittdauer (Sekunden)** und **Benutzeranzahl pro Schritt**.

Sie können beispielsweise die folgenden Informationen angeben: **Benutzeranzahl (ursprünglich)** =1, **Maximale Benutzeranzahl**=100, **Schrittdauer (Sekunden)** =10 und **Benutzeranzahl pro Schritt**=1. In diesem Fall wird ein Auslastungsmuster erstellt, bei dem die Anzahl der Benutzer mit 1 beginnt und alle 10 Sekunden um 1 erhöht wird, bis schließlich eine Auslastung durch 100 Benutzer erreicht wird.

> [!NOTE]
> Wenn die gesamte Testdauer kürzer ist als die Zeit, die zum Erreichen der maximalen Benutzerauslastung erforderlich ist, wird der Test nach Ablauf der Testdauer beendet, und das Ziel **Maximale Benutzeranzahl** wird nicht erreicht.

Sie können die Auslastung schrittweise erhöhen, bis die Leistung des Servers wesentlich beeinträchtigt ist. Wenn die Auslastung zunimmt, stehen dem Server schließlich keine ausreichenden Ressourcen mehr zur Verfügung. Die schrittweise Auslastung bietet eine effektive Möglichkeit, die Anzahl der Benutzer festzustellen, bei der der Server überlastet sein könnte. Des Weiteren müssen Sie bei der schrittweisen Auslastung die Ressourcen der Agents genau überwachen, um sicher zu stellen, dass diese in der Lage sind, die gewünschte Auslastung zu generieren.

Normalerweise sollten mehrere Testläufe mit verschiedenen Schrittdauern und Benutzeranzahlen pro Schritt ausgeführt werden, um aussagekräftige Messergebnisse für eine gegebene Auslastung zu erzielen. In vielen Fällen wird bei jedem Schritt, mit dem die Benutzeranzahl erhöht wird, anfänglich eine Auslastungsspitze angezeigt. Ein Beibehalten der Auslastung mit dieser Rate ermöglicht die Messung der Systemleistung, nachdem das System die anfängliche Auslastungsspitze überwunden hat.

#### <a name="step-load-pattern-considerations"></a>Überlegungen zu schrittweisen Auslastungsmustern

Ein schrittweises Auslastungsmuster kann zum Erhöhen der Auslastung auf den Servern während der Ausführung des Auslastungstests verwendet werden, um zu verdeutlichen, wie sich die Leistung bei Erhöhen der Benutzerauslastung ändert. Um beispielsweise die Leistung der Server beim Erhöhen der Benutzerauslastung auf 2.000 Benutzer anzuzeigen, könnten Sie einen 10-Stunden-Auslastungstest mit einem schrittweisen Auslastungsmuster mit den folgenden Eigenschaften ausführen:

- **Benutzeranzahl (ursprünglich)** : 100

- **Maximale Benutzeranzahl**: 2.000

- **Schrittdauer (Sekunden)** : 1.800

- **Schrittverlaufszeit (Sekunden)** : 20

- **Benutzeranzahl pro Schritt**: 100

  Mit diesen Einstellungen wird der Auslastungstest 30 Minuten (1.800 Sekunden) bei Benutzerlasten von 100, 200, 300 und bis zu 2.000 Benutzern ausgeführt. Vor allem die Eigenschaft **Schrittverlaufszeit** muss erwähnt werden, da es sich dabei um die einzige Eigenschaft handelt, die im **Assistenten für neue Auslastungstests** nicht zur Auswahl zur Verfügung steht. Diese Eigenschaft ermöglicht es, dass die Steigerung von einer Stufe zur nächsten (z. B. von 100 auf 200 Benutzer) schrittweise und nicht plötzlich vonstatten geht. In dem Beispiel würde die Benutzerauslastung von 100 auf 200 Benutzer in einem Zeitraum von 20 Sekunden (Zunahme von fünf Benutzern pro Sekunde) gesteigert werden. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der Schrittverlaufszeiteigenschaft für ein detailliertes Auslastungsmuster](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>Zielbasiert

Ein Muster für zielbasierte Auslastung ähnelt dem schrittweisen Muster, passt jedoch die Benutzerauslastung auf Grundlage eines Vergleichs von Schwellenwerten für Leistungsindikatoren und den regelmäßigen Anpassungen der Benutzerauslastung an. Zielbasierte Auslastungen sind nützlich für eine Reihe von Aufgaben:

- Maximieren der Ausgabe der Agents: Messen Sie die Eckdaten der Agents, um die Ausgabe zu maximieren. In der Regel handelt es sich hierbei um die Prozessorleistung, aber auch eine Messung des Arbeitsspeichers kann von Nutzen sein.

- Erreichen eines bestimmten Ressourcenwerts auf dem Zielserver (in der Regel Prozessorauslastung) und anschließende Messung des Durchsatzes bei diesem Wert. Auf diese Weise können Sie Run-To-Run-Vergleiche des Durchsatzes bei vorgegebener, gleichbleibender Verwendung der Serverressourcen durchführen.

- Erreichen eines bestimmten Durchsatzwerts auf dem Server

  Das Beispiel in der folgenden Tabelle veranschaulicht ein zielbasiertes Muster mit den folgenden Eigenschafteneinstellungen:

|Eigenschaftengruppe|Eigenschaft|Wert|
|-|--------------|-|
|Leistungsindikator|Kategorie|Prozessor|
|Leistungsindikator|Computer|ContosoServer1|
|Leistungsindikator|Leistungsindikator|% Prozessorzeit|
|Leistungsindikator|Instanz|_Total|
|Zielbereich für Leistungsindikator|Höchste Werte|90|
|Zielbereich für Leistungsindikator|Niedrigste Werte|70|
|Einschränkungen der Benutzeranzahl|Benutzeranzahl (ursprünglich)|1|
|Einschränkungen der Benutzeranzahl|Maximale Benutzeranzahl|100|
|Einschränkungen der Benutzeranzahl|Maximale Abnahme der Benutzeranzahl|5|
|Einschränkungen der Benutzeranzahl|Maximale Zunahme der Benutzeranzahl|5|
|Einschränkungen der Benutzeranzahl|Minimale Benutzeranzahl|1|

Durch diese Einstellungen wird während eines Testlaufs die Benutzerauslastung zwischen 1 und 100 vom **Auslastungstest-Analyzer** so angepasst, dass sich der **Zähler** für `% Processor Time` von WebServer01 zwischen `70%` und `90%.` bewegt.

Der Umfang jeder Anpassung der Benutzerauslastung wird durch die Einstellungen **Maximale Zunahme der Benutzeranzahl** und **Maximale Abnahme der Benutzeranzahl** festgelegt. Die Einschränkungen der Benutzeranzahl werden durch die Eigenschaften **Maximale Benutzeranzahl** und **Minimale Benutzeranzahl** festgelegt.

#### <a name="goal-based-load-pattern-considerations"></a>Überlegungen zu zielbasierten Auslastungsmustern

Ein zielbasiertes Auslastungsmuster ist nützlich, wenn Sie die Anzahl der Benutzer bestimmen möchten, die vom System unterstützt wird, bevor es eine bestimmte Ebene der Ressourcennutzung erreicht. Diese Option funktioniert am besten, wenn Sie bereits die beschränkende Ressource, also den Engpass, im System identifiziert haben.

Sie wissen beispielsweise, dass es sich bei der beschränkenden Ressource im System um die CPU auf dem Datenbankserver handelt, und Sie möchten anzeigen, wie viele Benutzer unterstützt werden können, wenn die CPU auf dem Datenbankserver zu ungefähr 75 Prozent ausgelastet ist. Sie könnten ein zielbasiertes Auslastungsmuster mit dem Ziel verwenden, den Wert des Leistungsindikators "% Prozessorzeit" zwischen 70 und 80 Prozent zu halten.

Sie müssen jedoch aufpassen, ob eine andere Ressource den Durchsatz des Systems beschränkt. Solche Ressourcen können bewirken, dass das vom zielbasierten Auslastungsmuster angegebene Ziel nie erreicht wird. Außerdem steigt die Benutzerauslastung weiterhin, bis der für **Maximale Benutzeranzahl** angegebene Wert erreicht ist. Dabei handelt es sich normalerweise nicht um die gewünschte Auslastung. Seien Sie daher bei der Auswahl des Leistungsindikators im zielbasierten Auslastungsmuster vorsichtig.

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-|-----------------------|
|**Angeben des anfänglichen Auslastungsmusters für den Auslastungstest**: Wenn Sie mit dem **Assistenten für neue Auslastungstests** einen Auslastungstest erstellen, wählen Sie ein Auslastungsmuster aus.|-   [Ändern des Auslastungsmusters](../test/edit-load-patterns-to-model-virtual-user-activities.md#change-the-load-pattern)|
|**Bearbeiten des Auslastungsmusters für den Auslastungstest**: Nachdem Sie den Auslastungstest erstellt haben, können Sie das Auslastungsmuster im **Auslastungstest-Editor** bearbeiten.|-   [Vorgehensweise: Angeben der Schrittverlaufszeiteigenschaft für ein detailliertes Auslastungsmuster](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Angeben, ob die virtuellen Benutzer im Auslastungstestszenario Webcachedaten einschließen sollten**: Sie können die Eigenschaft **Prozentsatz neuer Benutzer** ändern, um die Methode zu beeinflussen, mit der der Auslastungstest die Webzwischenspeicherung simuliert, die von einem Webbrowser für die virtuellen Benutzer ausgeführt werden würde.|-   [Vorgehensweise: Angeben des Prozentsatzes virtueller Benutzer, die auf Webcachedaten zugreifen](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Angeben der Schrittverlaufszeit für ein schrittweises Auslastungsmuster**: Die Eigenschaft **Schrittverlaufszeit** ermöglicht es, dass die Steigerung von einer Stufe zur nächsten (z.B. von 100 auf 200 Benutzer) schrittweise und nicht plötzlich vonstatten geht.|-   [Vorgehensweise: Angeben der Schrittverlaufszeiteigenschaft für ein detailliertes Auslastungsmuster](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="change-the-load-pattern"></a>Ändern des Auslastungsmusters

Nachdem Sie den Auslastungstest mit dem **Assistenten für neuen Auslastungstest** erstellt haben, können Sie mithilfe des **Auslastungstest-Editors** die Eigenschaften des Auslastungsmusters für ein Szenario Ihren Anforderungen an den Test entsprechend anpassen.

> [!NOTE]
> Eine vollständige Liste der Eigenschaften von Auslastungstestszenarios und deren Beschreibungen finden Sie unter [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md).

Das Auslastungsmuster gibt die Anzahl der während eines Auslastungstests aktiven virtuellen Benutzer und die Frequenz an, mit der neue Benutzer hinzugefügt werden. Ihnen stehen drei Muster für die Auswahl zur Verfügung: Schrittweise, konstant und zielbasiert. Weitere Informationen finden Sie unter [Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
> Sie können die Auslastungseigenschaften auch programmgesteuert mit einem Auslastungstest-Plug-In ändern. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines Auslastungstest-Plug-Ins](../test/how-to-create-a-load-test-plug-in.md).

### <a name="to-change-the-load-pattern"></a>So ändern Sie das Auslastungsmuster

1. Öffnen Sie einen Auslastungstest.

2. Erweitern Sie im **Auslastungstest-Editor** im Ordner *Szenarios* das Szenario, dessen Auslastungsmuster Sie bearbeiten möchten, und wählen Sie das Auslastungsmuster für das Szenario aus.

    > [!NOTE]
    > Der in der Szenariostruktur Ihres Auslastungstests angezeigte Text für den Auslastungsmuster-Knoten gibt das beim Erstellen des Auslastungstests ausgewählte Auslastungsprofil wieder. Hierbei handelt es sich entweder um ein **Constant Load Profile** (Profil für konstante Auslastung) oder ein **Step Load Profile** (Schrittweises Auslastungsprofil).

3. Drücken Sie **F4**, um das **Eigenschaftenfenster** anzuzeigen.

     Das **Auslastungsmuster** und die Kategorien **Parameter** werden im **Eigenschaftenfenster** angezeigt.

4. (Optional) Ändern Sie in der Kategorie **Auslastungsmuster** die Eigenschaft **Muster**.

     Sie können der Eigenschaft **Muster** die Werte **Schritt**, **Konstante** oder **Zielbasiert** zuordnen. Weitere Informationen über Auslastungsmustertypen finden Sie unter [Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5. (Optional) Ändern Sie die Werte in der Kategorie **Parameter**.

    > [!NOTE]
    > Die für **Parameter** verfügbaren Werte hängen vom ausgewählten Wert der Eigenschaft **Muster** ab.

6. Nachdem die Änderungen der Eigenschaften abgeschlossen sind, klicken Sie im Menü **Datei** auf **Speichern**. Anschließend können Sie den Auslastungstest mit dem neuen Auslastungsmuster ausführen.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Vorgehensweise: Angeben des Prozentsatzes virtueller Benutzer, die auf Webcachedaten zugreifen](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Vorgehensweise: Angeben der Schrittverlaufszeiteigenschaft für ein detailliertes Auslastungsmuster](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)
