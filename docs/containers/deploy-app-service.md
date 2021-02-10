---
title: Bereitstellen eines ASP.NET Core-Containers in Azure App Service
description: Erfahren Sie, wie Sie Visual Studio-Containertools zum Bereitstellen einer ASP.NET Core-Web-App in einem Docker-Container in Azure App Service verwenden.
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 2e23658cfde1154f5b4df7ae7dade71b1569e35c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859644"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Bereitstellen eines ASP.NET Core-Containers in Azure App Service mit Visual Studio

Dieses Tutorial führt Sie durch die Verwendung von Visual Studio zum Veröffentlichen Ihrer ASP.NET Core-Containerwebanwendung in einer [Azure App Service-Instanz](/azure/app-service). Azure App Service ist ein geeigneter Dienst für Web-Apps mit einem Container, die in Azure gehostet werden.

Wenn Sie kein Azure-Abonnement besitzen, können Sie ein [kostenloses Konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) erstellen, bevor Sie beginnen.

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieses Tutorials benötigen Sie Folgendes:

::: moniker range="vs-2017"
- Installieren der neuesten Version von [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) mit der Workload „ASP.NET und Webentwicklung“
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit der Workload *ASP.NET- und Webentwicklung*
::: moniker-end
- Installation von [Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Erstellen einer ASP.NET Core-Web-App

Die folgenden Schritte führen Sie durch die Erstellung einer einfachen ASP.NET Core-App, die in diesem Tutorial verwendet wird.

::: moniker range="vs-2017"
1. Wählen Sie im Menü von Visual Studio **Datei > Neu > Projekt** aus.
2. Wählen Sie im Abschnitt **Vorlagen** des Dialogfelds **Neues Projekt** die Option **Visual C# > Web** aus.
3. Wählen Sie **ASP.NET Core-Webanwendung** aus.
4. Weisen Sie Ihrer neuen Anwendung einen Namen zu (oder übernehmen Sie den Standardnamen), und wählen Sie **OK** aus.
5. Wählen Sie **Webanwendung** aus.
6. Aktivieren Sie das Kontrollkästchen **Docker-Unterstützung aktivieren**.
7. Wählen Sie den Containertyp **Linux** aus, und klicken Sie auf **OK**. Windows-Container werden nicht für die Bereitstellung in Azure App Service unterstützt.
::: moniker-end
::: moniker range=">= vs-2019"
1. Wählen Sie im Startfenster von Visual Studio die Option **Neues Projekt erstellen**.
1. Wählen Sie **ASP.NET Core-Webanwendung** und dann **Weiter** aus.
1. Weisen Sie Ihrer neuen Anwendung einen Namen zu (oder übernehmen Sie den Standardnamen), und wählen Sie **Erstellen** aus.
1. Wählen Sie eine **Webanwendung** aus.
1. Wählen Sie im Kontrollkästchen **Für HTTPS konfigurieren** aus, ob Sie SSL unterstützen möchten.
1. Aktivieren Sie das Kontrollkästchen **Docker-Unterstützung aktivieren**.
1. Wählen Sie den Containertyp aus, und klicken Sie auf **Erstellen**.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Bereitstellen des Containers in Azure

::: moniker range="vs-2017"

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen**.
1. Wählen Sie im Dialogfeld „Veröffentlichungsziel“ eine der Option **App Service Linux** oder **App Service** aus. Dabei handelt es sich um das Betriebssystem, das den Webserver hostet.
1. Sie können nur in App Service veröffentlichen oder sowohl in App Service als auch in Azure Container Registry (ACR) veröffentlichen. Wählen Sie **Create new App Service for containers** (Neue App Service-Instanz für Container erstellen) aus, und klicken Sie auf **Veröffentlichen**, um den Container in einer ACR-Instanz zu veröffentlichen.

   ![Screenshot: Dialogfeld „Veröffentlichen“](media/deploy-app-service/publish-app-service-linux.PNG)

   Klicken Sie auf **Neu erstellen** und dann auf **Veröffentlichen**, um nur in einer Azure App Service-Instanz ohne Azure Container Registry zu veröffentlichen.

1. Stellen Sie sicher, dass Sie mit dem Konto angemeldet sind, das Ihrem Azure-Abonnement zugeordnet ist, und wählen Sie einen eindeutigen Namen, ein Abonnement, eine Ressourcengruppe, einen Hostingplan und eine Containerregistrierung (falls zutreffend) aus, oder verwenden Sie die Standardwerte.

   ![Screenshot: Veröffentlichungseinstellungen](media/deploy-app-service/publish-app-service-linux2.png)

1. Wählen Sie **Erstellen**. Ihr Container wird in der ausgewählten Ressourcengruppe und Containerregistrierung in Azure bereitgestellt. Dieser Prozess kann ein wenig Zeit beanspruchen. Wenn er abgeschlossen ist, werden auf der Registerkarte **Veröffentlichen** Informationen zur Veröffentlichung, einschließlich der Website-URL, angezeigt.

   ![Screenshot: Registerkarte „Veröffentlichen“](media/deploy-app-service/publish-succeeded.PNG)

1. Klicken Sie auf den Websitelink, um zu überprüfen, ob Ihre App erwartungsgemäß in Azure funktioniert.

   ![Screenshot: Webanwendung](media/deploy-app-service/web-application-running.png)

1. Das Veröffentlichungsprofil wird mit allen ausgewählten Details gespeichert, z. B. die Ressourcengruppe und Containerregistrierung.

1. Sie können erneut eine Bereitstellung mit demselben Veröffentlichungsprofil durchführen, indem Sie auf **Veröffentlichen** oder im Fenster **Webveröffentlichungsaktivität** auf **Veröffentlichen** klicken oder indem Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** klicken und im Kontextmenü die Option **Veröffentlichen** auswählen.
:::moniker-end
:::moniker range=">=vs-2019"
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen**.
1. Wählen Sie im Dialogfeld **Veröffentlichen** das Ziel **Azure** aus.

   ![Screenshot des Veröffentlichungs-Assistenten](media/deploy-app-service/publish-choices.png)

1. Wählen Sie auf der Registerkarte **Bestimmtes Ziel** abhängig von Ihrem Containertyp das entsprechende Bereitstellungsziel, z. B. **App Service (Windows)** oder **App Service (Linux)** .

   ![Screenshot der Registerkarte „Bestimmtes Ziel“ des Veröffentlichungs-Assistenten](media/deploy-app-service/publish-app-service-windows.png)

1. Wenn Sie mit dem gewünschten Abonnement nicht beim richtigen Azure-Konto angemeldet sind, melden Sie sich im Fenster **Veröffentlichen** über die Schaltfläche links oben an.

1. Sie können eine vorhandene App Service-Instanz verwenden oder eine neue erstellen, indem Sie auf den Link **Neue Azure App Service-Instanz erstellen** klicken. Suchen Sie in der Strukturansicht Ihre vorhandene App Service-Instanz, indem Sie deren Ressourcengruppe aufklappen, oder ändern Sie die Einstellung **Ansicht** in **Ressourcentyp**, um nach Typ zu sortieren.

   ![Screenshot der Wahl einer App Service-Instanz](media/deploy-app-service/publish-app-service-windows2.png)

1. Wenn Sie eine neue erstellen, werden eine Ressourcengruppe und eine App Service-Instanz in Azure generiert. Sie können die Namen nach Wunsch ändern, solange sie eindeutig sind.

   ![Screenshot der Erstellung einer App Service-Instanz](media/deploy-app-service/publish-app-service-windows3.png)

1. Sie können den standardmäßigen Hostingplan übernehmen oder den Hostingplan jetzt oder später im Azure-Portal ändern. Die Standardeinstellung ist `S1` (klein) in einer der unterstützten Regionen. Um einen Hostingplan zu erstellen, wählen Sie **Neu** neben der Dropdownliste **Hostingplan**. Das Fenster **Hostingplan** wird eingeblendet.

   ![Screenshot der Optionen für den Hostingplan](media/deploy-app-service/hosting-plan.png)

   Die Details zu diesen Optionen können Sie in der Übersicht [App Service-Pläne](/azure/app-service/overview-hosting-plans) einsehen.

1. Sobald Sie mit dem Auswählen oder Erstellen dieser Ressourcen fertig sind, wählen Sie **Fertig stellen**. Ihr Container wird in der ausgewählten Ressourcengruppe und App Service-Instanz in Azure bereitgestellt. Dieser Prozess kann ein wenig Zeit beanspruchen. Wenn er abgeschlossen ist, werden auf der Registerkarte **Veröffentlichen** Informationen zur Veröffentlichung, einschließlich der Website-URL, angezeigt.

   ![Screenshot: Registerkarte „Veröffentlichen“](media/deploy-app-service/publish-succeeded-windows.png)

1. Klicken Sie auf den Websitelink, um zu überprüfen, ob Ihre App erwartungsgemäß in Azure funktioniert.

   ![Screenshot: Webanwendung](media/deploy-app-service/web-application-running2.png)

1. Das Veröffentlichungsprofil wird mit allen ausgewählten Details gespeichert, z. B. Ressourcengruppe und App Service-Instanz.

1. Sie können erneut eine Bereitstellung mit demselben Veröffentlichungsprofil durchführen, indem Sie auf **Veröffentlichen** oder im Fenster **Webveröffentlichungsaktivität** auf **Veröffentlichen** klicken oder indem Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** klicken und im Kontextmenü die Option **Veröffentlichen** auswählen.
:::moniker-end

## <a name="view-container-settings"></a>Anzeigen von Containereinstellungen

Im [Azure-Portal](https://portal.azure.com) können Sie Ihre App Service-Bereitstellung öffnen.

Sie können Einstellungen Ihrer App Service-Bereitstellung einsehen, indem Sie das Menü **Containereinstellungen** öffnen (in Visual Studio 2019 ab Version 16.4).

![Screenshot des Menüs „Containereinstellungen“ im Azure-Portal](media/deploy-app-service/container-settings-menu.png)

In diesem Menü können Sie sich Containerinformationen ansehen, Protokolle anzeigen oder herunterladen, oder Continuous Deployment einrichten. Weitere Informationen erhalten Sie im Artikel [Continuous Deployment mit Web-App für Container](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Löschen Sie die Ressourcengruppe über das [Azure-Portal](https://portal.azure.com), um alle Azure-Ressourcen für dieses Tutorial zu löschen. Klicken Sie auf **Ansicht** > **Weitere Fenster** > **Webveröffentlichungsaktivität**, und klicken Sie dann auf das Zahnradsymbol, um die Ressourcengruppe zu finden, die einer veröffentlichten Webanwendung zugeordnet ist. Daraufhin wird die Registerkarte **Veröffentlichen** geöffnet, die die Ressourcengruppe enthält.

Klicken Sie im Azure-Portal auf **Ressourcengruppen**, und wählen Sie dann die Ressourcengruppe aus, um ihre zugehörige Detailseite zu öffnen. Überprüfen Sie, ob es sich um die richtige Ressourcengruppe handelt, und klicken Sie dann auf **Ressourcengruppe entfernen**. Geben Sie anschließend den Namen der Ressourcengruppe ein, und klicken Sie auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr zu [Azure App Service](/azure/app-service/overview).

## <a name="see-also"></a>Siehe auch

[Bereitstellen in Azure Container Registry](hosting-web-apps-in-docker.md)