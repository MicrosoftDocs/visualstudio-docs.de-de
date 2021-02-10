---
title: Testmischung für ein Auslastungstestszenario
description: Lernen Sie, die Testmischung eines Szenarios zu bearbeiten, die eine Kombination der Auswahl von Webleistungs- und Komponententests und der Verteilung dieser Tests ist.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 99cc7f629fe28bb241033113bdecca043d67f032
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926793"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Bearbeiten der Testmischung zum Angeben, welche Webleistungstests, Komponententests und Tests der programmierten UI in ein Auslastungstestszenario einbezogen werden sollen

Die *Testmischung* eines Szenarios ergibt sich aus einer Kombination verschiedener Faktoren, beispielsweise der Auswahl von Webleistungs- und Komponententests, die im Szenario enthalten sind, und der Verteilung dieser Tests im Szenario. Bei der Verteilung handelt es sich um eine Einstellung, die Sie für die Wahrscheinlichkeit angeben können, dass ein bestimmter Test während eines Auslastungstestlaufs von einem virtuellen Benutzer ausgewählt wird.

Nachdem Sie einem Auslastungstest eine Reihe von Tests hinzugefügt haben, funktioniert die *Testmischung* wie andere Mischungsoptionen. Ein virtueller Benutzer wählt zufallsgesteuert auf Grundlage der in der Mischung angegebenen Wahrscheinlichkeit einen Test aus. Wenn beispielsweise zwei Tests vorhanden sind, deren Wahrscheinlichkeit in der Mischung jeweils 50 Prozent beträgt, wird der erste Test von einem virtuellen Benutzer während ungefähr der Hälfte der Zeit ausgeführt. Wenn in einer 50/50-Mischung ein langer und ein kurzer Test vorhanden sind, wird durch den langen Test eine höhere Auslastung hervorgerufen.

Wenn Sie einer Mischung Tests hinzugefügt haben, können Sie diese wieder entfernen. Über die Mischungssteuerung können Sie auch die Verteilung der Testmischung ändern. Mit der Mischungssteuerung können Sie die Verteilung der Tests in einem Szenario auf einfache Weise anpassen.

> [!NOTE]
> Die Verteilung ist ein Maßstab für die Wahrscheinlichkeit, dass ein bestimmter Test während eines Auslastungstestlaufs von einem virtuellen Benutzer ausgewählt wird. Die Verteilung wird in Prozent angegeben. Daher lautet die Summe der Verteilungen für alle in einem Szenario enthaltenen Tests 100. Wenn ein Szenario z. B. nur einen Test enthält, beträgt die Verteilung für diesen Test 100 Prozent.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Hinzufügen neuer Tests zu einer Testmischung in einem vorhandenen Szenario

Sie können beim Erstellen eines neuen Szenarios mithilfe des **Assistenten für neuen Auslastungstest** die Webleistungs- und Komponententests angeben, die der Testmischung des neuen Szenarios hinzugefügt werden sollen.

Sie können der Testmischung des Szenarios mithilfe des **Auslastungstest-Editors** weitere Webleistungs- und Komponententests hinzufügen.

![Hinzufügen eines Tests zu einem bestehenden Auslastungstest](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>So fügen Sie einem vorhandenen Szenario weitere Tests hinzu

1. Öffnen Sie einen Auslastungstest.

2. Klicken Sie im **Auslastungstest-Editor** mit der rechten Maustaste auf ein vorhandenes Szenario, und wählen Sie anschließend **Tests hinzufügen** aus.

     Das Dialogfeld **Tests hinzufügen** wird angezeigt. Alle Webleistungs- und Komponententests sowie Tests der programmierten UI in Ihrer Lösung, die noch nicht zum Szenario gehören, können zum Szenario hinzugefügt werden.

3. Wählen Sie im Bereich **Verfügbare Tests** die Webleistungs- oder Komponententests sowie die Tests der programmierten UI aus, die hinzugefügt werden sollen. Klicken Sie auf den Pfeil nach rechts, um die Tests zum Bereich **Ausgewählte Tests** hinzuzufügen.

4. Wenn Sie keine weiteren Tests hinzufügen möchten, klicken Sie auf **OK**.

     Die Tests werden zur Testmischung hinzugefügt. Den Tests in der Testmischung wird automatisch eine neue Verteilung zugewiesen.

5. (Optional) Passen Sie die Mischungssteuerung an, um die Testverteilung anzugeben. Weitere Details finden Sie in den [Informationen zur Mischungssteuerung](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Entfernen von Tests aus einem Szenario
![Entfernen eines Tests aus einem bestehenden Auslastungstest](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>So entfernen Sie Tests aus einem Szenario

1. Öffnen Sie einen Auslastungstest.

2. Klicken Sie im **Auslastungstest-Editor** in der Auslastungsteststruktur mit der rechten Maustaste auf das Szenario, aus dem Sie einen Test entfernen möchten, und wählen Sie **Testmischung bearbeiten** aus. Das Dialogfeld **Testmischung bearbeiten** wird angezeigt.

3. Wählen Sie den Webleistungs- oder Komponententest oder Test der programmierten UI im Raster aus, und klicken Sie dann auf **Entfernen**.

    > [!NOTE]
    > Passen Sie die Testmischung nach dem Entfernen des Tests an die gewünschte Verteilung an.

4. Wenn Sie keine weiteren Tests entfernen möchten, klicken Sie auf **OK**.

## <a name="about-the-mix-control"></a><a name="EditingTestMixAboutMixControl"></a> Informationen zur Mischungssteuerung
Mithilfe der Mischungssteuerung können Sie die Lastprozentsätze anpassen, die in einem Auslastungstestszenario auf die Tests, Browsertypen bzw. Netzwerktypen verteilt werden. Die Prozentsätze werden mit Schiebereglern angepasst. Die Testmischung gibt die Wahrscheinlichkeit an, mit der ein virtueller Benutzer einen bestimmten Test in einem Auslastungstestszenario ausführt.

Wenn Sie einen Schieberegler bewegen, werden die Prozentwerte aller verfügbaren Elemente geändert. Wenn mehr als zwei Elemente vorhanden sind, wird der hinzugefügte bzw. entfernte Betrag gleichmäßig auf die anderen Elemente verteilt. Dieses Verhalten kann geändert werden. Wenn Sie für ein bestimmtes Element das Kontrollkästchen in der Sperrspalte aktivieren, wird der für dieses Element festgelegte Prozentsatz gesperrt. Wenn Sie anschließend einen Schieberegler bewegen, wird der hinzugefügte bzw. entfernte Betrag nur auf die verbleibenden, nicht gesperrten Elemente verteilt.

Mit der Schaltfläche **Verteilen** werden die Prozentsätze gleichmäßig auf alle Elemente verteilt. Wenn beispielsweise drei Elemente vorhanden sind und Sie auf die Schaltfläche **Verteilen** klicken, werden die Prozentsätze auf 34, 33 und 33 festgelegt.

> [!WARNING]
> Gesperrte Elemente werden durch Klicken auf die Schaltfläche **Verteilen** überschrieben.

Statt die Schieberegler zu verwenden, können Sie die Prozentsätze auch direkt in die Spalte **%** eintragen. Wenn Sie einen Prozentsatz direkt eingeben, werden die anderen Elemente nicht automatisch angepasst.

> [!NOTE]
> Die Schieberegler werden deaktiviert, wenn die Gesamtsumme nicht 100 % ergibt oder Dezimalwerte in die Spalte **%** eingetragen werden.

Wenn Sie Prozentsätze manuell eingeben, sollten Sie sich vergewissern, dass die Summe aller Elemente 100 % ergibt. Wenn Sie eine Mischung speichern, deren Summe nicht 100 % beträgt, werden Sie aufgefordert, die vorhandenen Prozentsätze zu bestätigen oder anzupassen. Wenn Sie die Prozentsätze bestätigen, werden diese anteilsmäßig auf 100 % umgerechnet.  Wenn beispielsweise zwei Elemente vorhanden sind und Sie diese auf 80 % und 40 % festgelegt haben, wird das erste Element auf 66,67 % (80 geteilt durch 120) und das zweite Element auf 33,33 % (40 geteilt durch 120) festgelegt.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
