---
title: Verwenden von Visual Studio mit einem Codespace (Vorschauversion)
description: In diesem Artikel erfahren Sie mehr über die Verwendung der Visual Studio-IDE mit GitHub Codespaces für die Entwicklung unter Windows.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: c3a2e14236c2d24bc9650fab81150cc295826844
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189926"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>Verwenden von Visual Studio mit einem Codespace (Vorschauversion)

Visual Studio bietet hervorragende Unterstützung für die Entwicklung in GitHub Codespaces. Erstellen Sie einfach einen Codespace, und stellen Sie eine Verbindung damit her. So können Sie den vollen Funktionsumfang von Visual Studio in einer remote gehosteten Umgebung für Ihre Entwicklungsprojekte verwenden. Obwohl sich der Quellcode und die Tools in einem Codespace befinden und die Kompilierung sowie das Debuggen in der Cloud erfolgen, verläuft die Entwicklung so schnell und reibungslos, als würden Sie lokal arbeiten. Sie können in der Vorschauversion für Visual Studio 2019 mit Codespaces arbeiten ([für die eingeschränkte öffentliche Betaversion registrieren](https://github.com/features/codespaces/signup-vs)).

> [!NOTE]
> In diesem Artikel wird die Verwendung von Visual Studio für das Herstellen einer Verbindung mit GitHub Codespaces erläutert. Informationen zum Herstellen einer Verbindung mit einem Codespace von anderen Clients aus finden Sie in der Dokumentation für [Visual Studio Code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) oder [GitHub](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace).

> [!NOTE]
> Wenn Sie die [Vorschauversion für Visual Studio 2019](https://aka.ms/vspreview) noch nicht installiert haben, können Sie diese auf [visualstudio.microsoft.com](https://aka.ms/vspreview) herunterladen.

## <a name="enable-connect-to-github-codespaces"></a>Aktivieren von „Verbindung mit GitHub Codespaces herstellen“

Das Herstellen einer Verbindung mit GitHub Codespaces über die Vorschauversion für Visual Studio 2019 ist standardmäßig deaktiviert. Daher müssen Sie die Option zuerst unter „Vorschaufunktionen“ aktivieren.

1. Klicken Sie in der Vorschauversion für Visual Studio 2019 auf die Menüelemente **Extras** > **Optionen**, um das Dialogfeld „Optionen“ zu öffnen.

2. Klicken Sie unter **Umgebung** auf **Vorschaufunktionen**, und aktivieren Sie die Previewfunktion **Verbindung mit GitHub Codespaces herstellen**.

   ![Aktivieren der Previewfunktion „Verbindung mit GitHub Codespaces herstellen“](media/connect-to-github-codespaces-preview-feature.png)

3. Damit das Feature verfügbar wird, müssen Sie Visual Studio neu starten.

## <a name="create-a-codespace"></a>Erstellen eines Codespace

Wenn Sie noch keinen Codespace haben, können Sie einen in Visual Studio erstellen.

1. Beim Start von Visual Studio wird im Startfenster unter „Erste Schritte“ die Schaltfläche **Verbindung mit einem Codespace herstellen** angezeigt.

   ![Startfenster in Visual Studio mit „Verbindung mit einem Codespace herstellen“](media/visual-studio-start-window.png)

2. Klicken Sie auf **Verbindung mit einem Codespace herstellen**. Sie werden daraufhin aufgefordert, sich bei GitHub anzumelden. Sie können auch ein kostenloses GitHub-Konto erstellen, falls Sie noch keines besitzen.

   ![Visual Studio-Anmeldung bei GitHub](media/visual-studio-sign-in-to-github.png)

   Führen Sie den Onlineanmeldeworkflow von GitHub aus, nachdem Sie auf **Bei GitHub anmelden** geklickt haben.

3. Wenn Sie noch nie einen Codespace erstellt haben, werden Sie aufgefordert, einen zu erstellen.

   Unter „Details zum Codespace“ müssen Sie eine **Repository-URL** bereitstellen. GitHub Codespaces klont das angegebene Repository in Ihrem Codespace, wenn dieser erstellt wird.

   Sie können auch den **Instanztyp** ändern und über die Dropdownmenüs unter **Anhalten nach** einen Timeoutzeitraum festlegen. Nachdem Sie die Details des Codespace festgelegt haben, klicken Sie auf **Erstellen und Verbindung herstellen**.

   ![Details zum Visual Studio-Codespace](media/visual-studio-codespace-details.png)

   Der Codespace wird in GitHub Codespaces vorbereitet und in Visual Studio geöffnet, sobald er bereit ist.

   Der Name des Codespace wird in der Remoteanzeige in der Menüleiste angezeigt.

   ![Visual Studio-Verbindung mit dem Repositorycodespace „eShopOnWeb“](media/visual-studio-eshoponweb-codespace.png)

4. Verwenden Sie Visual Studio genauso, wie Sie auch lokal damit arbeiten würden. Versuchen Sie Folgendes:

   * Durchsuchen von Quellcode
   * Auswählen einer Projektmappendatei und Erstellen der Projektmappe (**STRG+UMSCHALT+B**)
   * Festlegen eines Haltepunkts in einer Quelldatei und Drücken von **F5**, um die Anwendung im Debugger zu starten
   * Vornehmen von Änderungen und Committen der Änderungen in Ihrem Repository   

> [!NOTE]
> Aktuell können keine GitHub Codespaces-Instanzen für Visual Studio über das [GitHub Codespaces-Portal](https://github.com/codespaces) erstellt werden. Codespaces können nur mithilfe von Visual Studio erstellt werden.

## <a name="connect-to-a-codespace"></a>Herstellen einer Verbindung mit einem Codespace

Nachdem Sie Ihren Codespace erstellt haben, können Sie ihn direkt in Visual Studio öffnen.

1. Beim Start von Visual Studio wird im Startfenster unter „Erste Schritte“ die Schaltfläche **Verbindung mit einem Codespace herstellen** angezeigt.

   ![Startfenster in Visual Studio mit „Verbindung mit einem Codespace herstellen“](media/visual-studio-start-window.png)

   Wenn Sie sich bereits in Visual Studio befinden, können Sie auf die Menüelemente **Datei** > **Verbindung mit einem Codespace herstellen** klicken.

   ![Visual Studio-Menüelemente „Datei“ > „Verbindung mit einem Codespace herstellen“](media/visual-studio-file-connect-to-codespace.png)

2. Klicken Sie auf **Verbindung mit einem Codespace herstellen**. Wenn Sie nicht bereits bei GitHub angemeldet sind, werden Sie aufgefordert, sich anzumelden.

3. Anschließend werden Ihnen alle Ihre GitHub Codespaces zusammen mit den dazugehörigen Details (rechts) angezeigt.

   ![In Visual Studio werden verfügbare GitHub-Codespaces und die dazugehörigen Details angezeigt.](media/visual-studio-connect-codespace.png)

   Alle Codespaces, in denen ein Azure DevOps-Repository geklont wurde, sind nur hier in Visual Studio und nicht auf der Codespaces-Seite von GitHub sichtbar.

4. Wählen Sie einen Codespace aus, und klicken Sie auf **Verbinden**. Wenn der Codespace angehalten wurde, wird er neu gestartet, und Visual Studio wird mit einer bestehenden Verbindung mit dem Codespace geöffnet.

   Der Name des Codespace wird in der Remoteanzeige in der Menüleiste angezeigt.

   ![Visual Studio-Verbindung mit dem Repositorycodespace „eShopOnWeb“](media/visual-studio-eshoponweb-codespace.png)

5. Verwenden Sie Visual Studio genauso, wie Sie auch lokal damit arbeiten würden. Versuchen Sie Folgendes:

   * Durchsuchen von Quellcode
   * Auswählen einer Projektmappendatei und Erstellen der Projektmappe (**STRG+UMSCHALT+B**)
   * Festlegen eines Haltepunkts in einer Quelldatei und Drücken von **F5**, um die Anwendung im Debugger zu starten
   * Vornehmen von Änderungen und Committen der Änderungen in Ihrem Repository

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>Weitere Informationen

* [Was ist GitHub Codespaces?](codespaces-overview.md)
* [Anpassen eines Codespace](customize-codespaces.md)
* [Unterstützte Visual Studio-Features](supported-features-codespaces.md)
