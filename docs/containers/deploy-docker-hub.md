---
title: Bereitstellen eines ASP.NET Core-Docker-Containers in Docker Hub | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Visual Studio-Containertools zum Bereitstellen einer ASP.NET Core-Web-App in Docker Hub verwenden.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e51088d135d0d2cdcc5d1bcca71f72fed8b73fd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867658"
---
# <a name="deploy-to-docker-hub"></a>Bereitstellen in Docker Hub

Docker Hub bietet einen praktischen Hostingdienst für Ihre Imagerepositorys. Sie können Bereitstellungen in Docker Hub mühelos über Visual Studio manuell durchführen.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Erstellen eines Docker-Kontos und eines Docker Hub-Repositorys

[Registrieren Sie sich](https://hub.docker.com/signup) für ein Docker-Konto, wenn Sie noch nicht über ein Konto verfügen.

Wenn Sie über kein Docker Hub-Repository verfügen, erstellen Sie ein Konto in [Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Veröffentlichen des Images für ein einzelnes Projekt in Docker Hub

1. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Veröffentlichen...** aus. Daraufhin wird eine Anzeige mit Bereitstellungsoptionen angezeigt.

   ![Screenshot: Bereitstellungsoptionen](media/container-tools/vs-2019/docker-container-registry.png)

1. Wählen Sie **Docker-Containerregistrierung** und dann **Docker Hub** aus.

   ![Screenshot des Dialogfelds „Veröffentlichen“: Auswählen von „Docker Hub“](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Geben Sie Ihre Docker-Anmeldeinformationen ein.

   ![Screenshot: Docker Hub-Dialogfeld](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Wenn Sie eine Verbindung zu Ihrem eigenen Repository herstellen (das nicht zu einer Organisation gehört), lassen Sie das Kontrollkästchen **Publish to a personal repository** (In einem persönlichen Repository veröffentlichen) aktiviert. Wenn sich das Repository im Besitz einer Organisation befindet, deaktivieren Sie das Kontrollkästchen, und geben Sie den Namen der Organisation ein. Geben Sie Ihren Benutzernamen und Ihr Kennwort für Ihr Docker-Konto ein, das über die Berechtigungen für den Zugriff auf das Repository verfügt, zu dem Sie eine Verbindung herstellen, und klicken Sie dann auf **Speichern**.

   Visual Studio versucht, Ihr Image in Docker Hub bereitzustellen.  Bei erfolgreicher Ausführung wird die Anzeige **Veröffentlichen** mit der URL für das Repositoryimage, dem Imagetag, dem Repository und der Buildkonfiguration (z. B. **Release**) angezeigt.

   ![Screenshot: Anzeige „Veröffentlichen“](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Sie können das Image jederzeit aktualisieren, indem Sie auf dieser Seite auf **Veröffentlichen** klicken.  Alternativ können Sie das Profil mithilfe der Links unter der URL anpassen oder entfernen.

## <a name="next-steps"></a>Nächste Schritte

Führen Sie für die Veröffentlichung in [Azure Container Registry](/azure/container-registry/) die Schritte unter [Bereitstellen in Azure Container Registry](hosting-web-apps-in-docker.md) aus.

Richten Sie Continuous Integration und Continuous Delivery (CI/CD) mit [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true) ein.

## <a name="see-also"></a>Siehe auch

[Bereitstellen in Azure App Service](deploy-app-service.md)
[Containertools in Visual Studio](./index.yml)