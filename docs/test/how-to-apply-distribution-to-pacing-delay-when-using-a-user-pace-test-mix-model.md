---
title: Anwenden der Verteilung auf Geschwindigkeitsverzögerung für Auslastungstests
description: Lernen Sie, die Eigenschaft „Verteilung auf Geschwindigkeitsverzögerung anwenden“ für einen Auslastungstest im Eigenschaftenfenster festzulegen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2c966eb9b4ad0bbf8e00c8a27fd69fef0c59cbc1
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440121"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Vorgehensweise: Anwenden der Verteilung auf die Geschwindigkeitsverzögerung beim Verwenden eines Testmischungsmodells für die Benutzergeschwindigkeit

Nachdem Sie den Auslastungstest mithilfe des **Auslastungstest-Assistenten** erstellt haben, können Sie die Szenarioeigenschaften mit dem Auslastungstest-Editor entsprechend Ihren Testanforderungen und -zielen ändern.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** wird mit dem **Eigenschaftenfenster** festgelegt. Eigenschaften für Auslastungstestszenarien werden mit dem Auslastungstest-Editor geändert.

> [!NOTE]
> Die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** gilt nur, wenn die *Auslastungstestmischung* auf Grundlage der Benutzergeschwindigkeit konfiguriert ist. Weitere Informationen finden Sie unter [Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Der Wert für **Verteilung auf Geschwindigkeitsverzögerung anwenden** kann auf TRUE oder FALSE festgelegt werden:

- **True**: Das Szenario wendet herkömmliche statistische Verteilungsverzögerungen an, die über den Wert in der Spalte **Tests pro Benutzer und Stunde** im Dialogfeld **Testmischung bearbeiten** angegeben werden. Weitere Informationen finden Sie unter [Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Beispiel: Der Wert für **Tests pro Benutzer und Stunde** im Dialogfeld **Testmischung bearbeiten** ist für den Test auf zwei Benutzer pro Stunde festgelegt. Ist die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** auf **TRUE** festgelegt, wird auf die Wartezeit zwischen den Tests eine herkömmliche statistische Verteilung angewendet. Es werden weiterhin zwei Tests pro Stunde ausgeführt, zwischen ihnen ist jedoch nicht notwendigerweise eine Verzögerung von 30 Minuten. Der erste Test konnte nach 4 Minuten und der zweite Test nach 45 Minuten ausgeführt werden.

- **FALSE**: Die Tests werden mit der Geschwindigkeit ausgeführt, die Sie für den Wert in der Spalte **Tests pro Benutzer und Stunde** im Dialogfeld **Testmischung bearbeiten** angegeben haben. Weitere Informationen finden Sie unter [Bearbeiten von Textmischungsmodellen zum Angeben der Wahrscheinlichkeit, mit der ein virtueller Benutzer einen Test ausführt](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Beispiel: Der Wert für **Tests pro Benutzer und Stunde** im Dialogfeld **Testmischung bearbeiten** ist für den Test auf zwei Benutzer pro Stunde festgelegt. Wenn die Eigenschaft **Verteilung auf Geschwindigkeitsverzögerung anwenden** auf **FALSE** festgelegt ist, ist kein Spielraum für die Testausführung vorhanden. Der Test wird alle 30 Minuten ausgeführt. So ist sichergestellt, dass Sie zwei Tests pro Stunde ausführen.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>So geben Sie die Eigenschafteneinstellung "Verteilung auf Geschwindigkeitsverzögerung anwenden" für ein Szenario an

1. Öffnen Sie einen Auslastungstest.

   Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2. Wählen Sie im Ordner **Szenarios** der Auslastungsteststruktur den Szenarioknoten aus, auf den Sie die Verteilung der Geschwindigkeitsverzögerung anwenden möchten.

3. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

   Die Szenariokategorien und -eigenschaften werden im Fenster **Eigenschaften** angezeigt.

4. Wählen Sie im Eigenschaftswert für **Verteilung auf Geschwindigkeitsverzögerung anwenden** entweder **TRUE** oder **FALSE** aus.

5. Wählen Sie **Datei** > **Speichern** aus. Sie können nun den Auslastungstest mit dem neuen Wert von **Verteilung auf Geschwindigkeitsverzögerung anwenden** ausführen.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Exemplarische Vorgehensweise: Erstellen und Ausführen eines Auslastungstests](../test/walkthrough-create-and-run-a-load-test.md)
- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
- [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md)
