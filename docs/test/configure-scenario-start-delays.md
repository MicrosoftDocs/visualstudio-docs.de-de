---
title: Konfigurieren des Szenarios „Startverzögerungen für Auslastungstests“
description: Lernen Sie, mit dem Auslastungstest-Editor und dem Fenster „Eigenschaften“ eine Verzögerung vor dem Beginn eines Szenarios in einem Auslastungstest anzugeben.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: bc7a57e759cbeb6fcb5fd9c96dd4c68aa0637afa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868035"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Konfigurieren des Szenarios „Startverzögerungen in Auslastungstests“

Mit dem Auslastungstest-Editor und dem Fenster **Eigenschaften** können Sie eine Verzögerung angeben, mit der ein Szenario in einem Auslastungstest beginnt.

Die Eigenschaft **Startzeit verzögern** kann beispielsweise verwendet werden, wenn Sie in einem Szenario mit der Erstellung von Elementen beginnen müssen, die in einem anderen Szenario benötigt werden. Sie können das Szenario, in dem die Elemente verwendet werden sollen, verzögern, damit in dem Szenario, in dem die Elemente erstellt werden, einige Daten ausgefüllt werden.

Ein anderes Beispiel ist, dass ein Szenario nur zu einer bestimmten Tageszeit ausgeführt wird. Sie möchten daher den Start des Szenarios verzögern, um dies zu simulieren.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Angeben einer verzögerten Startzeit für ein Szenario

Sie können mit dem Auslastungstest-Editor eine Verzögerung vor dem Beginn eines Szenarios in einem Auslastungstest angeben, um die Eigenschaft **Startzeit verzögern** im **Eigenschaftenfenster** zu ändern.

> [!NOTE]
> Eine vollständige Liste der Eigenschaften von Auslastungstestszenarios und deren Beschreibungen finden Sie unter [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md).

Die Eigenschaft **Startzeit verzögern** kann z.B. verwendet werden, wenn Sie in einem Szenario mit der Erstellung von Elementen beginnen müssen, die in einem anderen Szenario benötigt werden. Sie können das Szenario, in dem die Elemente verwendet werden sollen, verzögern, damit in dem Szenario, in dem die Elemente erstellt werden, einige Daten ausgefüllt werden.

Ein anderes Beispiel ist, dass ein Szenario nur zu einer bestimmten Tageszeit ausgeführt wird. Sie möchten daher den Start des Szenarios verzögern, um dies zu simulieren.

> [!NOTE]
> Eine vollständige Liste der Eigenschaften von Laufzeiteinstellungen und deren Beschreibungen finden Sie unter [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>So geben Sie die Verzögerungsstartzeit für ein Szenario an

1. Öffnen Sie einen Auslastungstest.

     Der Auslastungstest-Editor wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2. Klicken Sie im Ordner **Szenarios** der Auslastungsteststrukturen auf den Szenarioknoten, für den Sie die Verzögerungsstartzeit angeben möchten.

3. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden im Fenster **Eigenschaften** angezeigt.

4. Geben Sie im Textfeld für die Eigenschaft **Startzeit verzögern** einen Zeitwert ein, der die Dauer der Wartezeit nach dem Start des Auslastungstests angibt, bevor das Szenario bei Ausführung des Auslastungstests gestartet wird.

    > [!NOTE]
    > Wenn der Wert für die Eigenschaft **Während Aufwärmdauer deaktivieren** für das Szenario auf **TRUE** festgelegt wird, wird der Zeitwert der Eigenschaft **Startzeit verzögern** nach der Aufwärmphase übernommen. Sie können mithilfe der Szenarioeigenschaft **Während Aufwärmdauer deaktivieren** festlegen, welche Szenarios in die Aufwärmphase einbezogen werden.

5. Klicken Sie nach dem Ändern der Eigenschaft im Menü **Datei** auf **Speichern**. Sie können anschließend den Auslastungstest mithilfe des neuen Werts für **Startzeit verzögern** ausführen.

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Aktivieren und Deaktivieren, ob ein Szenario während der Aufwärmphase ausgeführt wird

Die Eigenschaft **Während Aufwärmdauer deaktivieren** wird über das **Eigenschaftenfenster** festgelegt. Die Bearbeitung der Eigenschaften von Auslastungstestszenarien wird durch den Auslastungstest-Editor festgelegt.

Mit der Eigenschaft **Während Aufwärmdauer deaktivieren** wird angegeben, ob das Szenario während der Aufwärmphase, die in der Eigenschaft **Startzeit verzögern** angegeben ist, ausgeführt werden soll oder nicht. Weitere Informationen finden Sie in der vorherigen Prozedur [Angeben einer verzögerten Startzeit für ein Szenario](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>So aktivieren oder deaktivieren Sie die Aufwärmphase für ein Szenario

1. Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2. Wählen Sie im Ordner **Szenarios** den Szenarioknoten aus, für den Sie das Aufwärmverhalten ändern möchten.

3. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden im **Eigenschaftenfenster** angezeigt.

     Wählen Sie in der Eigenschaft **Während Aufwärmdauer deaktivieren** entweder die Option **TRUE** oder **FALSE** aus.

4. Nachdem die Änderungen der Eigenschaft abgeschlossen sind, wählen Sie im Menü **Datei** die Option **Speichern** aus. Sie können anschließend den Auslastungstest mit dem neuen Wert für **Während Aufwärmdauer deaktivieren** ausführen.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Configure test agents and test controllers for load tests (Konfigurieren von Test-Agents und Testcontrollern für Auslastungstests)](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md)
