---
title: Erstellen eines Projekts für einen Webleistungs- und Auslastungstest
description: In diesem Schnellstart wird veranschaulicht, wie Sie ein Testprojekt für Webleistung und Auslastung in Visual Studio erstellen und ausführen.
ms.custom: SEO-VS-2020
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3833542dc00f347014dabf96f836fbd4fa810862
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329132"
---
# <a name="quickstart-create-a-load-test-project"></a>Schnellstart: Erstellen eines Auslastungstestprojekts

In diesem Schnellstart, der etwa zehn Minuten Ihrer Zeit in Anspruch nimmt, wird veranschaulicht, wie Sie ein Testprojekt für Webleistung und Auslastung in Visual Studio erstellen und ausführen. Auslastungstests führen Webleistungstests oder Komponententests aus, um den gleichzeitigen Zugriff vieler Benutzer auf einen Server zu simulieren.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Softwareanforderungen

Testprojekte für Webleistung und Auslastung sind nur in der **Enterprise Edition** von Visual Studio verfügbar.

## <a name="install-the-load-testing-component"></a>Installieren der Auslastungstestkomponente

Wenn Sie noch keine Komponente für Tools für Webleistung und Auslastungstests installiert haben, müssen Sie diese über den Visual Studio-Installer installieren.

1. Öffnen Sie den **Visual Studio-Installer** über das Windows-**Startmenü**. Sie können auch in Visual Studio über das Dialogfeld „Neues Projekt“ oder durch Klicken auf **Extras** > **Tools und Features abrufen** in der Menüleiste auf den Installer zugreifen.

1. Klicken Sie im **Visual Studio-Installer** auf die Registerkarte **Einzelne Komponenten**, und scrollen Sie nach unten zum Abschnitt **Debuggen und Testen**. Wählen Sie **Tools für Webleistung und Auslastungstests** aus.

   ![Die Komponente „Tools für Webleistung und Auslastungstests“](media/web-perf-load-testing-tools-component.png)

1. Klicken Sie auf die Schaltfläche **Ändern**.

   Die Komponente „Tools für Webleistung und Auslastungstests“ wird installiert.

## <a name="create-a-load-test-project"></a>Erstellen eines Auslastungstestprojekts

In diesem Abschnitt wird das Erstellen eines Auslastungstestprojekts in C# erläutert. Wenn Ihnen das lieber ist, können Sie Ihr Auslastungstestprojekt auch in Visual Basic erstellen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio.

2. Wählen Sie auf der Menüleiste **Datei** > **Neu** > **Projekt** aus.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Erweitern Sie im Dialogfeld **Neues Projekt** die Option **Installiert** und dann die Option **Visual C#** , wählen Sie dann die Kategorie **Test** aus. Wählen Sie die Vorlage **Testprojekt für Webleistung und Auslastung** aus.

   ![Vorlage „Testprojekt für Webleistung und Auslastung“](media/web-perf-load-test-project-template.png)

4. Benennen Sie das Projekt, wenn Sie den Standardnamen nicht verwenden möchten, und klicken Sie dann auf **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio.

2. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

3. Geben Sie auf der Seite **Neues Projekts erstellen** in das Suchfeld **Webtest** ein, und wählen Sie dann die Vorlage **Testprojekt für Webleistung und Auslastung \[veraltet]** für C#. Wählen Sie **Weiter** aus.

4. Benennen Sie das Projekt, wenn Sie den Standardnamen nicht verwenden möchten, und wählen Sie **OK**.

::: moniker-end

   Visual Studio erstellt das Projekt und zeigt die Dateien im **Projektmappen-Explorer** an. Das Projekt enthält zu Beginn nur eine Webtestdatei namens *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Hinzufügen eines Auslastungstests zum Projekt

1. Öffnen Sie durch einen Rechtsklick das Kontextmenü des Projektknotens im **Projektmappen-Explorer**, und klicken Sie dann auf **Hinzufügen** > **Auslastungstest**.

   Der **Assistent für neuen Auslastungstest** wird geöffnet.

1. Wählen Sie die Option **Lokaler Auslastungstest** aus, und klicken Sie dann auf **Weiter**. Weitere Informationen über cloudbasierte Auslastungstests finden Sie [hier](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true).

   ![Erste Seite des Assistenten für neuen Auslastungstest](media/load-test-wizard-page-1.png)

1. Klicken Sie im Assistent auf **Weiter**, bis Sie die Seite **Tests zu einem Auslastungstestszenario hinzufügen und die Testmischung bearbeiten** erreichen. Wählen Sie die Schaltfläche **Hinzufügen** aus.

   Das Dialogfeld **Tests hinzufügen** wird geöffnet.

1. Wählen Sie unter **Verfügbare Tests** den Test **WebTest1** aus, und klicken Sie dann auf den Pfeil nach rechts, um ihn in das Feld **Ausgewählte Tests** zu verschieben. Klicken Sie auf die Schaltfläche **OK** .

   ![Dialogfeld „Tests hinzufügen“](media/add-tests-dialog-box.png)

1. Klicken Sie im **Assistent für neuen Auslastungstest** auf die Schaltfläche **Fertigstellen**.

   Der Auslastungstest wird dem Projekt hinzugefügt und die Auslastungstestdatei wird im Editor-Fenster geöffnet.

## <a name="run-the-load-test"></a>Auslastungstest ausführen

Damit haben Sie einen Auslastungstest erstellt, der nicht viel tut, führen Sie ihn dennoch aus.

Öffnen Sie hierzu durch einen Rechtsklick das Kontextmenü des Auslastungstests, der im Editor geöffnet ist, und klicken Sie dann auf **Auslastungstest ausführen**.

![Menü „Auslastungstest ausführen“](media/run-load-test.png)

Der Auslastungstest wird ausgeführt. Das Fenster **Testergebnisse** zeigt an, dass der Test ausgeführt wird, und der Auslastungstest-Analyzer wird im Editor-Fenster angezeigt. Nach Abschluss des Tests, der innerhalb von fünf Minuten durchgeführt werden sollte, wenn Sie die Standardeinstellungen verwendet haben, wird eine Zusammenfassung im Editor angezeigt. Klicken Sie auf **Diagramme**, **Tabellen** oder **Detail**, um verschiedene Informationen über die Ergebnisse des Auslastungstests abzurufen.

![Auslastungstest-Analyzer-Fenster](media/load-test-analyzer.png)

## <a name="next-steps"></a>Nächste Schritte

Da Sie nun ein einfaches Auslastungstestprojekt erstellt haben, ist der nächste Schritt das Konfigurieren von Szenarios, Indikatorensätzen und Laufzeiteinstellungen.

> [!div class="nextstepaction"]
> [Edit test settings (Bearbeiten von Testeinstellungen)](edit-load-tests.md)
