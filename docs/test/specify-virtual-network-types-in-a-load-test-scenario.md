---
title: Angeben der Typen von virtuellen Netzwerken (Auslastungstest)
description: Hier erfahren Sie, wie Sie eine Netzwerkmischung einsetzen, um eine genauere Annäherung an die Interaktion zwischen Endbenutzern und Anwendungen zu erzielen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, adding networks
- load tests, removing networks
- load tests, virtual networks
- network mix
ms.assetid: 3c4f7874-081a-4ec4-9510-4d6d7d863a11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94973f8f791158f408b841442478dcfa6aeeff58
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330211"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Angeben von virtuellen Netzwerktypen in einem Auslastungstestszenario

Mithilfe der *Netzwerkmischung* kann die Auslastung in einem Auslastungstestszenario realistischer simuliert werden. Die Auslastung wird durch Verwendung einer heterogenen Mischung von Netzwerktypen anstelle eines einzigen generiert. Sie erreichen so eine bessere Annäherung an die Interaktion zwischen Endbenutzern und Anwendungen.

Die Netzwerkmischung gibt die Wahrscheinlichkeit an, mit der ein virtueller Benutzer ein bestimmtes *Netzwerkprofil* ausführt. Ein Netzwerkprofil ist eine Simulation der Netzwerkbandbreite auf Anwendungsebene. Netzwerklatenz wird nicht simuliert.

Beim Erstellen eines Auslastungstests sollten Sie die Auslastung mit mehr als einem Typ von Netzwerkverbindung simulieren. Die Netzwerkmischung umfasst mehrere Netzwerktypen. Die verschiedenen Netzwerkverbindungen werden simuliert. Wenn Sie eine Option wie `Cable-DSL 1.5Mbps` auswählen, werden Wartezeiten in den Test eingefügt, um die ausgewählte Bandbreite zu simulieren.

Die Netzwerkmischung arbeitet nach dem gleichen Prinzip wie die anderen Mischungsoptionen. Ein ausgewählter Netzwerktyp wird auf Grundlage der Netzwerkmischung nach dem Zufallsprinzip einem virtuellen Benutzer zugeordnet. Die Tests für den Benutzer werden mit einem Netzwerktyp ausgeführt, der entsprechend der in der Mischung angegebenen Wahrscheinlichkeit ausgewählt wird.

Nachdem Sie eine Netzwerkmischung angegeben haben, können Sie Netzwerktypen hinzufügen oder entfernen. Sie können auch die Verteilung der Netzwerkmischung über die Mischungssteuerung ändern.

Mit der Mischungssteuerung können Sie die Verteilung der Netzwerke in einem Szenario auf einfache Weise anpassen.

Weitere Details finden Sie in den [Informationen zur Mischungssteuerung](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Wahre Netzwerkemulation

Visual Studio verwendet eine softwarebasierte echte Netzwerkemulation für alle Testtypen, einschließlich Auslastungstests. Wahre Netzwerkemulation simuliert Netzwerkbedingungen durch direkte Bearbeitung der Netzwerkpakete. Der wahre Netzwerkemulator kann das Verhalten von Kabel- und Funknetzwerken mit einem zuverlässigen physischen Kanal (z. B. einem Ethernet) emulieren. Die folgenden Netzwerkattribute werden in wahre Netzwerkemulation integriert:

- Round-Trip-Zeit für das Netzwerk (Wartezeit)

- Die Menge an verfügbarer Bandbreite

- Warteschlangenverhalten

- Paketverlust

- Neuanordnung von Paketen

- Fehlerweitergabe

Wahre Netzwerkemulation bietet auch Flexibilität beim Filtern von Netzwerkpaketen auf Grundlage von IP-Adressen oder Protokollen, z. B. TCP, UDP und ICMP.

Wahre Netzwerkemulation kann von netzwerkbasierten Anwendungsentwicklern und Testern dazu verwendet werden, eine gewünschte Testumgebung zu emulieren, die Leistung zu bewerten, die Auswirkungen auf Änderung zu prognostizieren oder Entscheidungen zu Technologieoptimierung zu treffen. Im Vergleich zu Hardwareprüfständen ist wahre Netzwerkemulation eine weitaus günstigere und flexiblere Lösung.

## <a name="to-add-new-networks-to-a-scenario"></a>So fügen Sie einem Szenario neue Netzwerke hinzu

1. Klicken Sie während des Angebens der Netzwerkmischung für ein Szenario auf **Hinzufügen**.

     Dem Raster wird ein neuer Netzwerkeintrag hinzugefügt.

    > [!NOTE]
    > Klicken Sie mit der rechten Maustaste auf ein bereits vorhandenes Szenario, und klicken Sie anschließend auf **Netzwerkmischung bearbeiten**, um das Dialogfeld **Netzwerkmischung bearbeiten** anzuzeigen.

2. Wählen Sie in der Spalte **Netzwerktyp** den Pfeil für den neuen Eintrag aus. Wählen Sie den gewünschten Netzwerktyp aus.

3. (Optional) Passen Sie die Mischungssteuerung an, um die Testverteilung anzugeben. Weitere Details finden Sie in den [Informationen zur Mischungssteuerung](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Wenn Sie keine weiteren Netzwerke hinzufügen möchten, klicken Sie auf **OK**.

## <a name="to-remove-networks-from-a-scenario"></a>So entfernen Sie Netzwerke aus einem Szenario

1. Öffnen Sie einen Auslastungstest.

2. Klicken Sie mit der rechten Maustaste auf das Szenario, aus dem ein Netzwerk entfernt werden soll, und klicken Sie auf **Netzwerkmischung bearbeiten**. Das Dialogfeld **Netzwerkmischung bearbeiten** wird angezeigt.

3. Wählen Sie das Netzwerk im Raster aus, und klicken Sie dann auf **Entfernen**.

4. (Optional) Passen Sie die Mischungssteuerung an, um die Testverteilung anzugeben. Weitere Details finden Sie in den [Informationen zur Mischungssteuerung](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Wenn Sie keine weiteren Netzwerke entfernen möchten, klicken Sie auf **OK**.

## <a name="about-the-mix-control"></a>Informationen zur Mischungssteuerung

Mithilfe der Mischungssteuerung können Sie die Lastprozentsätze anpassen, die in einem Auslastungstestszenario auf die Tests, Browsertypen bzw. Netzwerktypen verteilt werden. Um die Prozentwerte anzupassen, verschieben Sie die Schieberegler. Die Mischung für die Netzwerktypen gibt die Wahrscheinlichkeit an, mit der ein virtueller Benutzer ein bestimmtes Netzwerkprofil in einem Auslastungstestszenario ausführt.

Wenn Sie einen Schieberegler bewegen, werden die Prozentwerte aller verfügbaren Elemente geändert. Wenn mehr als zwei Elemente vorhanden sind, wird der hinzugefügte bzw. entfernte Betrag gleichmäßig auf die anderen Elemente verteilt. Dieses Verhalten kann geändert werden. Wenn Sie für ein bestimmtes Element das Kontrollkästchen in der Sperrspalte aktivieren, wird der für dieses Element festgelegte Prozentsatz gesperrt. Wenn Sie anschließend einen Schieberegler bewegen, wird der hinzugefügte bzw. entfernte Betrag nur auf die verbleibenden, nicht gesperrten Elemente verteilt.

Mit der Schaltfläche **Verteilen** werden die Prozentsätze gleichmäßig auf alle Elemente verteilt. Wenn beispielsweise drei Elemente vorhanden sind und Sie auf die Schaltfläche **Verteilen** klicken, werden die Prozentsätze auf 34, 33 und 33 festgelegt.

> [!WARNING]
> Gesperrte Elemente werden durch Klicken auf die Schaltfläche **Verteilen** überschrieben.

Statt die Schieberegler zu verwenden, können Sie die Prozentsätze auch direkt in die Spalte **%** eintragen. Wenn Sie einen Prozentsatz direkt eingeben, werden die anderen Elemente nicht automatisch angepasst.

> [!NOTE]
> Die Schieberegler werden deaktiviert, wenn die Gesamtsumme nicht 100 % ergibt oder Dezimalwerte in die Spalte **%** eingetragen werden.

Wenn Sie Prozentsätze manuell eingeben, sollten Sie sich vergewissern, dass die Summe aller Elemente 100 % ergibt. Wenn Sie eine Mischung speichern, deren Summe nicht 100 % beträgt, werden Sie aufgefordert, die vorhandenen Prozentsätze zu bestätigen oder anzupassen. Wenn Sie die Prozentsätze bestätigen, werden diese anteilsmäßig auf 100 % umgerechnet.  Wenn beispielsweise zwei Elemente vorhanden sind und Sie diese auf 80 % und 40 % festgelegt haben, wird das erste Element auf 66,67 % (80 geteilt durch 120) und das zweite Element auf 33,33 % (40 geteilt durch 120) festgelegt.
