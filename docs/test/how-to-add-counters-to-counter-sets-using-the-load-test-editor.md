---
title: Hinzufügen von Indikatoren zu Indikatorensätzen für Auslastungstests
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 754c88bd6dbe76736148718d2f1ad32888623c34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288376"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>Vorgehensweise: Hinzufügen von Indikatoren zu Indikatorensätzen mit dem Auslastungstest-Editor

Wenn Sie mithilfe des **Auslastungstest-Assistenten** einen Auslastungstest erstellen, fügen Sie einen Anfangssatz von Indikatoren hinzu. Dadurch erhalten Sie einen Satz vordefinierter Indikatorensätze für den Auslastungstest. Weitere Informationen finden Sie unter [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Bei der Verteilung der Auslastungstests auf mehrere Remotecomputer werden Indikatoren für Controller und Agents den Controller- und Agent-Indikatorensätzen zugeordnet. Weitere Informationen zur Verwendung von Remotecomputern im Auslastungstest finden Sie unter [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

Sie können die Indikatoren mit dem **Auslastungstest-Editor** verwalten. Dem Test bereits hinzugefügte Indikatorensätze werden im Knoten **Indikatorensätze** des Auslastungstests angezeigt. Nachdem Sie einen Auslastungstest erstellt haben, können Sie vorhandenen Indikatorensätzen neue Indikatoren hinzufügen.

## <a name="to-add-counters-to-a-counter-set"></a>So fügen Sie einem Indikatorensatz Indikatoren hinzu

1. Öffnen Sie einen Auslastungstest.

2. Erweitern Sie den Knoten **Indikatorensätze**. Alle dem Auslastungstest hinzugefügten Indikatorensätze werden angezeigt.

    > [!NOTE]
    > In der Hierarchiestruktur des Auslastungstests ist auch der Knoten **Laufzeiteinstellungen** enthalten. Dieser Knoten enthält den Knoten **Indikatorensatzzuordnungen**, von dem alle Computer und die Indikatorensätze angezeigt werden, die diesen Computern zugeordnet sind.

3. Klicken Sie mit der rechten Maustaste auf einen vorhandenen Indikatorensatz, und klicken Sie dann auf **Indikatoren hinzufügen**.

     Das Dialogfeld **Leistungsindikatoren auswählen** wird angezeigt.

4. Geben Sie im Dropdown-Kombinationsfeld **Computer** den Namen des Computers ein, den Sie zuordnen möchten. Sie können auch einen Computer in der Dropdownliste auswählen.

    > [!NOTE]
    > Da Indikatorensätze einem Computer zugeordnet werden müssen, bevor Leistungsdaten erfasst werden, müssen Sie einen Computer festlegen, auf dem die Leistungsdaten erfasst werden sollen.

5. Wählen Sie eine **Leistungskategorie** aus, um die Kategorien von Leistungsdatenindikatoren zu filtern. Es werden zwei Spalten mit Daten angezeigt, aus denen Sie Leistungsindikatoren auswählen können.

    > [!NOTE]
    > Für einige Indikatorenkategorien ist es erforderlich, dass Sie auch eine Instanz auswählen. Wenn Sie beispielsweise einen SQL-Indikator auswählen, müssen Sie außerdem eine SQL-Instanz auswählen, da auf dem Zielcomputer möglicherweise mehrere SQL-Instanzen installiert sind.

6. Wählen Sie einen Indikator und eine Instanz aus, die dem benutzerdefinierten Indikatorensatz hinzugefügt werden sollen.

     \- oder –

     Aktivieren Sie das Optionsfeld **Alle Indikatoren**, um alle verfügbaren Indikatoren auszuwählen.

7. Klicken Sie auf **OK**.

    > [!NOTE]
    > Außerdem ist es möglich, Indikatoren einem Indikatorensatz hinzuzufügen, indem Sie einen vorhandenen Indikator oder eine Indikatorkategorie auswählen, auf „Kopieren“ klicken und den Indikator dann im gewünschten Indikatorensatzknoten einfügen. Wenn zusätzliche Indikatoren kopiert wurden, die nicht benötigt werden, können diese gelöscht werden.

## <a name="see-also"></a>Weitere Informationen

- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
