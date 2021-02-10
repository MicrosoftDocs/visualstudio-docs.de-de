---
title: Hinzufügen von benutzerdefinierten Indikatorensätzen für Auslastungstests
description: Wenn Sie mithilfe des Auslastungstest-Assistenten einen Auslastungstest erstellen, fügen Sie einen Anfangssatz von Indikatoren hinzu. Lernen Sie, benutzerdefinierte Indikatorensätzen mithilfe des Auslastungstest-Editors hinzuzufügen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ce34a4e30c9d612bd37afb61c354b7a4b5df7aed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966928"
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Vorgehensweise: Hinzufügen von benutzerdefinierten Indikatorensätzen mithilfe des Auslastungstest-Editors

Wenn Sie mithilfe des **Assistenten für neuen Auslastungstest** einen Auslastungstest erstellen, fügen Sie einen anfänglichen Satz von Indikatoren hinzu. Dadurch erhalten Sie einen Satz vordefinierter Indikatorensätze für den Auslastungstest.

> [!NOTE]
> Bei der Verteilung der Auslastungstests auf mehrere Remotecomputer werden Indikatoren für Controller und Agents den Controller- und Agent-Indikatorensätzen zugeordnet. Weitere Informationen zur Verwendung von Remotecomputern im Auslastungstest finden Sie unter [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

Sie können die Indikatoren mit dem **Auslastungstest-Editor** verwalten. Dem Test bereits hinzugefügte Indikatorensätze werden im Knoten **Indikatorensätze** des Auslastungstests angezeigt. Nach dem Erstellen eines Auslastungstests können Sie neue, benutzerdefinierte Indikatorensätze hinzufügen.

![Benutzerdefinierter Indikatorensatz](../test/media/loadtestcustomcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>So fügen Sie einen benutzerdefinierten Indikatorensatz zu einem Auslastungstest hinzu

1. Öffnen Sie einen Auslastungstest.

2. Erweitern Sie den Knoten **Indikatorensätze**. Alle dem Auslastungstest hinzugefügten Indikatorensätze werden angezeigt.

3. Klicken Sie mit der rechten Maustaste auf den Knoten **Indikatorensätze**, und wählen Sie **Benutzerdefinierten Indikatorensatz hinzufügen** aus.

    > [!NOTE]
    > Der Indikatorensatz wird mit einen Standardnamen bezeichnet, z.B. **Custom1**. Sie können diesen Namen im Fenster **Eigenschaften** ändern. Drücken Sie **F4**, um das **Eigenschaftenfenster** anzuzeigen.

4. Um dem benutzerdefinierten Indikatorensatz Indikatoren hinzuzufügen, klicken Sie mit der rechten Maustaste auf den neuen Indikatorensatz und dann auf **Indikatoren hinzufügen**. Weitere Informationen zum Hinzufügen von Indikatoren finden Sie unter [Vorgehensweise: Hinzufügen von Indikatoren zu Indikatorensätzen](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Sie können auch einen benutzerdefinierten Indikator hinzufügen, indem Sie mit der rechten Maustaste auf einen vorhandenen Indikatorensatz klicken, auf "Kopieren" klicken und den Indikator dann im Indikatorensatzknoten einfügen. Zusätzliche Indikatoren, die kopiert wurden, aber nicht benötigt werden, können gelöscht werden. Sie können den Namen des neuen Indikatorensatzes im Fenster **Eigenschaften** ändern.

## <a name="see-also"></a>Weitere Informationen

- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
