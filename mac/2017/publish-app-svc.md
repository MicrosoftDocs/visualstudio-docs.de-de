---
title: Veröffentlichen in Azure App Service
ms.date: 01/17/2019
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.custom: video
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 49a8dfb3625ebda01caf0d0fa806b197c1bdaefb
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722996"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Veröffentlichen einer Web-App in Azure App Service mit Visual Studio für Mac

Sie können das Tool zum Veröffentlichen verwenden, um ASP.NET Core-Apps in Azure App Service zu veröffentlichen.

## <a name="prerequisites"></a>Voraussetzungen

- [Visual Studio 2017 für Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) installiert mit aktiviertem ASP.NET Core.
- Ein Azure-Abonnement. [Registrieren Sie sich kostenlos](https://azure.microsoft.com/free/dotnet/), wenn Sie noch nicht über ein Abonnement verfügen. Dabei werden Ihnen für 30 Tage und 12 Monate für beliebte kostenlose Dienste 200 USD gutgeschrieben.
- Ein ASP.NET Core-Projekt. Wenn Sie noch kein Projekt haben, können Sie [ein neues Projekt erstellen](./create-new-projects.md?view=vsmac-2017&preserve-view=true).

## <a name="publish-to-azure-app-service"></a>Veröffentlichen in Azure App Service

 1. Klicken Sie im Lösungspad mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**.

    ![Kontextmenü „Veröffentlichen“](media/publish-context-menu.png)

 2. Wenn Sie dieses Projekt bereits in Azure App Service veröffentlicht haben, sehen Sie im Menü das Veröffentlichungsprofil. Wählen Sie das Veröffentlichungsprofil aus, um den Veröffentlichungsprozess zu starten.

 3. Wenn Sie das Projekt zum ersten Mal in App Service veröffentlichen möchten, klicken Sie auf **In Azure veröffentlichen**.

    ![Kontextmenü „In App Service veröffentlichen“](media/publish-to-azure-context-menu.png)

 4. Das Dialogfeld **In Azure App Service veröffentlichen** mit allen vorhandenen App Services wird angezeigt. Wählen Sie einen App Service aus der Liste aus, und klicken Sie dann auf **Veröffentlichen**, um einen vorhandenen App Service zu veröffentlichen.

    ![Dialogfeld „In Azure App Service veröffentlichen“](media/publish-to-app-service-dialog.png)

 5. Klicken Sie auf **Neu**, um einen neuen App Service zu erstellen.

    ![Dialogfeld „In App Service veröffentlichen“](media/publish-to-app-service-dialog-new-selected.png)

 6. Das Dialogfeld **Neuer App Service** wird angezeigt. In diesem Dialogfeld können Sie die Einstellungen Ihres neuen App Service konfigurieren.

    ![Dialogfeld „Neuer App Service“](media/publish-new-app-service.png)

    Hier sollten Sie einige Optionen anpassen. Der Standardname des App Service entspricht dem Projektnamen. Wenn der Name nicht verfügbar ist, wird auf der rechten Seite des Eingabefelds eine Warnung angezeigt. Der Name des App Service wird in der URL Ihrer Website verwendet, er muss also für die Verwendung in einer URL gültig sein.

    Sie können das Abonnement, das dem App Service zugeordnet wird, über das Dropdownfeld **Abonnement** ändern.

    Sie können eine vorhandene **Ressourcengruppe** über das Dropdownfeld auswählen, oder Sie erstellen ein neues über die **+** -Schaltfläche.

    Wählen Sie einen vorhandenen App Service-Plan aus, oder erstellen Sie einen neuen, indem Sie auf das Optionsfeld **Benutzerdefiniert** klicken.

    Klicken Sie auf **Erstellen**, um Ihren neuen App Service zu erstellen und Ihr Projekt darin zu veröffentlichen.

    Das Dialogfeld **Neuer App Service** wird geschlossen, nachdem Sie auf **Erstellen** geklickt haben, und die folgende Meldung sollte angeben, dass der App Service gestartet wurde.

      ![Meldung zur Erstellung des App Service](media/publish-create-app-service-message.png)

    Klicken Sie auf **OK**, um die Nachricht zu schließen. Anschließend können Sie mit der Arbeit an Ihrem Projekt fortfahren. Sie können den Status des Veröffentlichungsprozesses anhand der Statusleiste am oberen Rand der IDE verfolgen. Sobald Ihre Web-App erfolgreich veröffentlicht wurde, wird die Website in Ihrem Standardbrowser geöffnet.

## <a name="related-video"></a>Zugehörige Videos

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]