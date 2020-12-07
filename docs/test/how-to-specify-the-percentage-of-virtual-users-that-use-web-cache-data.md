---
title: 'Auslastungstest: Festlegen eines Prozentsatzes virtueller Benutzer, die Webcachedaten verwenden'
description: Lernen Sie, wie Sie die Eigenschaft „Prozentsatz neuer Benutzer“ im Eigenschaftenfenster festgelegt wird. Sie bearbeiten Eigenschaften von Auslastungstestszenarien im Auslastungstest-Editor.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19568cce3fbd7abd4a74922d2a726ff7c92dd09a
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329054"
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Vorgehensweise: Angeben des Prozentsatzes virtueller Benutzer, die auf Webcachedaten zugreifen

Nachdem Sie den Auslastungstest mithilfe des **Assistenten für neuen Auslastungstest** erstellt haben, können Sie die Szenarioeigenschaften ändern, um Ihre Testanforderungen und -ziele mithilfe des **Auslastungstest-Editors** zu erfüllen. Eine vollständige Liste der Eigenschaften von Auslastungstestszenarios und deren Beschreibungen finden Sie unter [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Die Eigenschaft **Prozentsatz neuer Benutzer** wird im Fenster **Eigenschaften** festgelegt. Sie bearbeiten Eigenschaften von Auslastungstestszenarios im **Auslastungstest-Editor**.

Die Eigenschaft **Prozentsatz neuer Benutzer** wirkt sich auf die Simulation der Webbrowser-Zwischenspeicherung im Auslastungstest aus. In der Standardeinstellung ist die Eigenschaft **Prozentsatz neuer Benutzer** auf „0%“ festgelegt. Wenn der Wert für die Eigenschaft **Prozentsatz neuer Benutzer** auf „100%“ festgelegt ist, wird jeder Webleistungstestlauf in einem Auslastungstest wie ein erstmaliger Zugriff eines Benutzers auf eine Website behandelt, wobei der Browsercache des Benutzers keine Daten aus vorherigen Websiteaufrufen enthält. Daher werden alle Anforderungen im Webtest, einschließlich aller abhängigen Anforderungen, wie z.B. Bilder, heruntergeladen.

> [!NOTE]
> Wird die gleiche zwischenspeicherbare Ressource mehrmals in einem Webtest angefordert, werden die Anforderungen nicht heruntergeladen.

Wenn Sie einen Auslastungstest für eine Website ausführen, die eine erhebliche Anzahl von regelmäßigen Besuchern aufweist, bei denen der lokale Browsercache wahrscheinlich Bilder und andere zwischenspeicherbare Inhalte enthält, erfolgen durch die Verwendung der Einstellung „100%“ für die Eigenschaft **Prozentsatz neuer Benutzer** mehr Downloadanforderungen als in einer realistischen Umgebung. In diesem Fall sollten Sie einen prozentualen Schätzwert für die erstmaligen Websiteaufrufe festlegen und die Eigenschaft **Prozentsatz neuer Benutzer** entsprechend festlegen.

## <a name="to-specify-the-percentage-of-new-users-for-a-scenario"></a>So geben Sie den Prozentsatz neuer Benutzer für ein Szenario an

1. Öffnen Sie einen Auslastungstest.

     Der **Auslastungstest-Editor** wird angezeigt. Die Auslastungsteststruktur wird angezeigt.

2. Klicken Sie im Ordner **Szenarios** der Auslastungsteststruktur auf den Szenarioknoten, für den Sie den Prozentsatzwert neuer Benutzer ändern möchten.

3. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Die Szenariokategorien und -eigenschaften werden im **Eigenschaftenfenster** angezeigt.

4. Legen Sie den Wert für die Eigenschaft **Prozentsatz neuer Benutzer** fest, indem Sie eine Zahl für den prozentualen Anteil neuer Benutzer eingeben.

5. Nachdem die Änderungen der Eigenschaft abgeschlossen sind, wählen Sie im Menü **Datei** die Option **Speichern** aus. Sie können anschließend den Auslastungstest mit dem neuen Wert für **Prozentsatz neuer Benutzer** ausführen.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
- [Exemplarische Vorgehensweise: Erstellen und Ausführen eines Auslastungstests](../test/walkthrough-create-and-run-a-load-test.md)
- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
- [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md)
- [Bearbeiten von Auslastungsmustern zur Modellierung virtueller Benutzeraktivitäten](../test/edit-load-patterns-to-model-virtual-user-activities.md)
