---
title: Schrittverlaufszeit für Auslastungstests
description: Hier erfahren Sie, wie Sie die Eigenschaft „Schrittverlaufszeit“ im Eigenschaftenfenster festlegen. Die Eigenschaft Schrittverlaufszeit wird nur mit einem schrittweisen Auslastungsmuster verwendet.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 9d630d84124bb132c82389ecf73af24aac7e1a49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915793"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Vorgehensweise: Angeben der Schrittverlaufszeiteigenschaft für ein detailliertes Auslastungsmuster

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Szenarioeigenschaften mit dem **Auslastungstest-Editor** entsprechend Ihren Testanforderungen und -zielen ändern. Weitere Informationen finden Sie unter [ Vorgehensweise: Erstellen und Ausführen eines Auslastungstests](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Eine vollständige Liste der Eigenschaften von Auslastungstestszenarios und deren Beschreibungen finden Sie unter [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md).

Die Eigenschaft **Schrittverlaufszeit** wird im **Eigenschaftenfenster** festgelegt. Sie bearbeiten Eigenschaften von Auslastungstestszenarios im **Auslastungstest-Editor**.

Die Eigenschaft **Schrittverlaufszeit** wird nur mit einem Schrittauslastungsmuster verwendet. Weitere Informationen finden Sie unter [Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Ein schrittweises Auslastungsmuster wird zum Erhöhen der Auslastung auf den Servern während der Ausführung des Auslastungstests verwendet, um zu verdeutlichen, wie sich die Leistung bei Erhöhen der Benutzerauslastung ändert. Wenn Sie z. B. die Leistung der Server beim Erhöhen der Benutzerauslastung auf 2.000 Benutzer anzeigen möchten, können Sie einen 10-stündigen Auslastungstest mit einem schrittweisen Auslastungsmuster mit den folgenden Eigenschaften ausführen:

- Benutzeranzahl (ursprünglich): 100

- Maximale Benutzeranzahl: 2.000

- Schrittdauer (Sekunden): 1.800

- Schrittverlaufszeit (Sekunden): 20

- Benutzeranzahl pro Schritt: 100

Mit diesen Einstellungen wird der Auslastungstest 30 Minuten (1.800 Sekunden) mit einer Benutzerauslastung von 100, 200, 300 und bis zu 2.000 Benutzern ausgeführt.

> [!NOTE]
> Die Eigenschaft **Schrittverlaufszeit** ist die einzige dieser Eigenschaften, die im **Assistenten für neuen Auslastungstest** nicht ausgewählt werden kann.

Die Eigenschaft **Schrittverlaufszeit** ermöglicht es, dass die Steigerung von einer Stufe zur nächsten (z.B. von 100 auf 200 Benutzer) schrittweise statt plötzlich vonstatten geht. In dem Beispiel würde die Benutzerauslastung von 100 auf 200 Benutzer in einem Zeitraum von 20 Sekunden (Zunahme von fünf Benutzern pro Sekunde) gesteigert werden.

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>So bearbeiten Sie die Eigenschaft „Schrittverlaufszeit“ für ein detailliertes Auslastungsmuster

1. Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2. Öffnen Sie im Ordner **Szenarios** der Auslastungsteststruktur den Szenarioknoten, für den die Schrittverlaufszeit angegeben werden soll.

3. Klicken Sie auf den Knoten **Schrittweises Auslastungsmuster**.

    > [!NOTE]
    > Das Auslastungsmuster für das Szenario muss ein schrittweises Auslastungsmuster sein. Falls dies nicht der Fall ist, zeigt das Auslastungsmuster den Auslastungsmustertyp an, der dem Szenario derzeit zugeordnet ist. Weitere Informationen finden Sie unter [Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden im **Eigenschaftenfenster** angezeigt.

5. Legen Sie den Wert für die Eigenschaft **Schrittverlaufszeit** fest, indem Sie eine Zahl für die Sekunden der einzelnen Schritte eingeben, um die von der Eigenschaft **Benutzeranzahl pro Schritt** angegebenen Benutzer allmählich hinzuzufügen.

6. Nachdem die Änderungen der Eigenschaft abgeschlossen sind, wählen Sie im Menü **Datei** die Option **Speichern** aus. Sie können anschließend den Auslastungstest mit dem neuen Wert für die **Schrittverlaufszeit** ausführen.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
- [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md)
- [Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten](../test/edit-load-patterns-to-model-virtual-user-activities.md)
