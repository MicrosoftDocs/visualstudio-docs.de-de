---
title: 'Vorgehensweise: Auswählen eines Repositorys für Auslastungstestergebnisse'
description: Lernen Sie, einen lokalen oder Remote-SQL Server zum Speichern der Testergebnisse zu identifizieren. Der Server muss über einen Auslastungstest-Ergebnisspeicher verfügen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ada73cc1f907a298a2cc1efcf3281fb8a219ef32
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439939"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Vorgehensweise: Auswählen eines Repositorys für Auslastungstestergebnisse

Sie sind nicht auf einen lokalen Ergebnisspeicher beschränkt. Häufig werden Auslastungstests auf einem Remotesatz von Agent-Computern ausgeführt. Agents können zusammen mit einem Controller eine größere simulierte Last generieren als jeder einzelne Computer. Weitere Informationen finden Sie im Artikel zu [Testcontrollern und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

Testergebnisse von den Agents oder den lokalen Computern können auf einem beliebigen SQL-Server gespeichert werden, auf dem Sie einen Auslastungstest-Ergebnisspeicher erstellt haben. In jedem Fall müssen Sie im Fenster **Testcontroller verwalten** angeben, wo die Ergebnisse des Auslastungstests gespeichert werden sollen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Angeben eines Ergebnisspeichers für Auslastungstestdaten

1. Öffnen Sie im **Projektmappen-Explorer** die Auslastungstestdatei.

2. Klicken Sie auf der Symbolleiste **Auslastungstest** auf **Testcontroller verwalten**. Das Dialogfeld **Testcontroller verwalten** wird angezeigt. Wenn Sie einen Agent remote verwenden, müssen Sie einen Controller auswählen.

     ![Verbindungseigenschaften des Ergebnisspeichers für Auslastungstests](../test/media/loadtestconnectionproperties.png) Verbindungseigenschaften des Ergebnisspeichers für Auslastungstests

3. Klicken Sie unter **Auslastungstest-Ergebnisspeicher** auf **(…)** , um das Dialogfeld **Verbindungseigenschaften** anzuzeigen.

4. Geben Sie in **Servername** den Namen des Servers ein, auf dem Sie die `LoadTest`-Skripts ausgeführt haben.

    > [!TIP]
    > Wenn Sie SQL Express auf dem lokalen Computer für den Auslastungstestspeicher verwenden, geben Sie „\<computername>\sqlexpress“ ein (z. B. **MyComputer\sqlexpress**).

5. Unter **Beim Server anmelden** können Sie **Windows-Authentifizierung verwenden** auswählen. Sie können einen Benutzernamen und das Kennwort angeben. In diesem Fall müssen Sie jedoch auch die Option **Kennwort speichern** auswählen.

6. Klicken Sie unter **Mit Datenbank verbinden** auf **Select or enter a database name** (Datenbankname auswählen oder eingeben). Wählen Sie im Dropdown-Listenfeld **LoadTest** aus.

7. Klicken Sie auf **OK**. Sie können die Verbindung testen, indem Sie auf **Verbindung testen** klicken.

8. Klicken Sie im Dialogfeld **Testcontroller verwalten** auf **Schließen** aus.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
