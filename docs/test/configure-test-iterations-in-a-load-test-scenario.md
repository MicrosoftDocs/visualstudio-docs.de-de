---
title: Konfigurieren von Testiterationen für Auslastungstests
description: Lernen Sie, mit Einstellungen für Testiterationen die maximale Anzahl von Iterationen im Szenario und die Länge der Pause zwischen ihnen zu konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5316b03220a094d3280aba3eb8c46f190a2874f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442559"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Konfigurieren von Testiterationen in einem Auslastungstestszenario

Bearbeiten Sie zum Konfigurieren der Testiterationseinstellungen ein Auslastungstestszenario mithilfe des Auslastungstest-Editors und des Fensters **Eigenschaften**. Standardmäßig wird ein Auslastungstestszenario ohne Angabe einer maximalen Anzahl von Testiterationen eingerichtet. Sie können die maximale Anzahl von Iterationen im Szenario und die Länge der Pause zwischen den Iterationen konfigurieren.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Angeben der maximalen Anzahl von Testiterationen für ein Szenario

Sie können die maximale Anzahl von Testläufen für ein Szenario angeben, indem Sie mithilfe des Auslastungstest-Editors die Eigenschaft **Maximale Anzahl von Testiterationen** im **Eigenschaftenfenster** ändern.

Mit der Eigenschaft **Maximale Anzahl von Testiterationen** wird die maximale Anzahl der Testiterationen gesteuert, die für das Szenario ausgeführt werden sollen. Ebenso wie bei der Eigenschaft **Testiterationen** in den Auslastungslaufzeiteinstellungen handelt es sich dabei um das Maximum für alle Benutzer in allen Agents und nicht um eine Pro-Benutzer-Einstellung.

> [!NOTE]
> Eine vollständige Liste der Eigenschaften von Auslastungstestszenarios und deren Beschreibungen finden Sie unter [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md).

Für eine sequenzielle Testmischung ist eine Iteration ein Durchlauf durch alle Tests in der Mischung. Für alle anderen Testmischungen zählt jede Testausführung als Iteration. Weitere Details finden Sie in den [Informationen zur Mischungssteuerung](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Wenn der Auslastungstest ein dauerbasierter Auslastungstest ist und die Dauer abläuft, bevor sämtliche Iterationen abgeschlossen sind, wird der Test beendet. Wenn der Test iterationsbasiert ist und die Testiterationen vor Szenarioiterationen erreicht werden, wird der Test beendet. Die Dauer wird mit der Eigenschaft **Testlaufdauer** im **Eigenschaftenfenster** konfiguriert, das einer Testlaufeinstellung in einem Auslastungstest zugeordnet ist.

Wenn die Anzahl der Szenarioiterationen erreicht wird, wird die Ausführung des Szenarios beendet, doch alle anderen aktiven Szenarien werden weiterhin ausgeführt.

> [!NOTE]
> Eine verwandte Eigenschaft ist die Eigenschaft **Eindeutig** für eine Webtest-Datenquelle, mit der Zeile für Zeile sequenziell durch die Daten navigiert wird. Dabei wird jedoch jeder Datensatz nur einmal angesteuert. Weitere Informationen finden Sie unter [Hinzufügen einer Datenquelle für einen Webleistungstests](../test/add-a-data-source-to-a-web-performance-test.md).

Die Eigenschaft **Maximale Anzahl von Testiterationen** ist für eine Vielzahl von Situationen nützlich. Einige Auslastungstester bevorzugen iterationsbasierte Tests, andere hingegen auf der Dauer basierende Tests.

![Angeben von Testiterationen in einem Szenario](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>So geben Sie die maximale Anzahl von Testiterationen an

1. Öffnen Sie einen Auslastungstest.

2. Der Auslastungstest-Editor wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

3. Klicken Sie im Ordner **Szenarios** der Auslastungsteststruktur auf den Szenarioknoten, für den Sie die maximale Anzahl von Testiterationen angeben möchten.

4. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden im Fenster **Eigenschaften** angezeigt.

5. Geben Sie im Textfeld für die Eigenschaft **Maximale Anzahl von Testiterationen** einen Wert an, der die maximale Anzahl von Tests angibt, die bei Ausführung des Auslastungstests für das Szenario ausgeführt werden sollen.

    > [!NOTE]
    > Wenn Sie für die Eigenschaft **Maximale Anzahl von Testiterationen** den Wert 0 verwenden, wird keine maximale Anzahl von Iterationen angegeben.

6. Nachdem die Änderungen der Eigenschaft abgeschlossen sind, wählen Sie im Menü **Datei** die Option **Speichern** aus. Anschließend können Sie den Auslastungstest mit dem neuen Wert für **Maximale Anzahl von Testiterationen** ausführen.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Angeben von Reaktionszeiten zwischen Testiterationen in einem Szenario

Die Eigenschaft **Reaktionszeit zwischen Testiterationen** wird im **Eigenschaftenfenster** festgelegt, während die Eigenschaften von Auslastungstestszenarios im Auslastungstest-Editor angegeben werden.

Mit der Eigenschaft **Reaktionszeit zwischen Testiterationen** wird die Wartezeit vor dem Starten einer Testiteration angegeben (als Anzahl von Sekunden).

> [!NOTE]
> Eine vollständige Liste der Auslastungstest-Szenarioeigenschaften finden Sie unter [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>So geben Sie die Reaktionszeiten zwischen Testiterationen an

1. Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2. Klicken Sie im Ordner **Szenarios** der Auslastungsteststruktur auf den Szenarioknoten, für den die Reaktionszeit angegeben werden soll.

3. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden im **Eigenschaftenfenster** angezeigt.

4. Geben Sie im Wert für die Eigenschaft **Reaktionszeit zwischen Testiterationen** eine Zahl ein, die die Anzahl von Sekunden vor dem Starten der nächsten Testiteration darstellt.

5. Nachdem die Änderungen der Eigenschaft abgeschlossen sind, wählen Sie im Menü **Datei** die Option **Speichern** aus. Sie können den Auslastungstest anschließend mit dem neuen Wert für **Reaktionszeit zwischen Testiterationen** ausführen.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Configure test agents and test controllers for load tests (Konfigurieren von Test-Agents und Testcontrollern für Auslastungstests)](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md)
- [Bearbeiten der Reaktionszeit zum Simulieren menschlicher Interaktionsverzögerungen in Auslastungstestszenarios für Websites](../test/edit-think-times-in-load-test-scenarios.md)
