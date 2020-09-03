---
title: Auslastungstest-Indikatorensätze
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.dialog.countersetmapping
helpviewer_keywords:
- counters, counter sets
- performance counters
- counter sets
- load tests, counter sets
ms.assetid: 64315c2f-a0b2-4378-be16-0774b99beef5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eeb99d58a9fc0547d118c529878d8b02cc83dda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287687"
---
# <a name="how-to-manage-counter-sets-using-the-load-test-editor"></a>Vorgehensweise: Verwalten von Indikatorensätzen mithilfe des Auslastungstest-Editors

Wenn Sie mithilfe des **Assistenten für neuen Auslastungstest** einen Auslastungstest erstellen, fügen Sie einen anfänglichen Indikatorensatz hinzu. Dadurch erhalten Sie einen Satz vordefinierter Indikatorensätze für den Auslastungstest.

> [!NOTE]
> Bei der Verteilung der Auslastungstests auf mehrere Remotecomputer werden Indikatoren für Controller und Agents den Controller- und Agent-Indikatorensätzen zugeordnet. Weitere Informationen zur Verwendung von Remotecomputern im Auslastungstest finden Sie unter [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

Das Verwalten von Indikatorensätzen umfasst die Auswahl der Computer, für die Leistungsdaten erfasst werden sollen, und das Zuweisen von Indikatorensätzen, die auf jedem der Computer erfasst werden sollen. Sie können die Indikatoren mit dem **Auslastungstest-Editor** verwalten.

![Verwalten von Indikatorensätzen](../test/media/loadtestmanagecountersets.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-manage-counter-sets"></a>So verwalten Sie Indikatorensätze

1. Öffnen Sie einen Auslastungstest.

2. Klicken Sie auf die Schaltfläche **Indikatorensätze verwalten**.

     – oder –

     Klicken Sie in der Auslastungsteststruktur mit der rechten Maustaste auf den Ordner **Indikatorensätze**, und wählen Sie **Indikatorensätze verwalten** aus.

     Das Dialogfeld **Indikatorensätze verwalten** wird angezeigt.

3. (Optional) Wählen Sie im Listenfeld **Die ausgewählten Computer und Indikatorensätze werden den folgenden standardmäßigen Laufzeiteinstellungen hinzugefügt** eine andere Laufzeiteinstellung aus.

    > [!NOTE]
    > Dies gilt nur, wenn der Auslastungstest mehrere Testlaufeinstellungen enthält.

4. (Optional) Klicken Sie auf **Hinzufügen**, um einen neuen zu überwachenden Computer hinzuzufügen. Sie werden aufgefordert, einen Namen einzugeben. Geben Sie den Namen eines Computers ein. Unter dem neuen Eintrag werden Knoten angezeigt. Zum Beispiel **ASP.NET**, **IIS**, **SQL** und andere. Aktivieren Sie die Kontrollkästchen vor den Knoten, die Sie auswählen möchten. Die neuen Indikatoren werden im Bereich **Vorschau für Auswahl** angezeigt.

5. (Optional) Geben Sie im Textfeld **Computertags** ein Tag ein, das dem Computer zugeordnet werden soll, z. B. "TestMachine12 in lab3".

     Computertags ermöglichen es Ihnen, einen Computer anhand eines einfachen Namens zu identifizieren.

     Die Tags werden im Knoten **Indikatorensatzzuordnungen** in der Struktur im Auslastungstest-Editor angezeigt. Wichtiger ist jedoch, dass die Tags in Excel-Berichten angezeigt werden, sodass die Projektbeteiligten die Rolle des Computers im Auslastungstest erkennen können. Beispiel: "Webserver1 in Lab2" oder "SQL Server2 im Phoenix-Büro". Weitere Informationen finden Sie unter [Erstellen von Berichten zu Auslastungstestergebnissen für Testvergleiche oder die Trendanalyse](../test/compare-load-test-results.md).

6. Klicken Sie auf **OK**.

## <a name="see-also"></a>Weitere Informationen

- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
