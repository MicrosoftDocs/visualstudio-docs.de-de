---
title: Bereitstellen von ASP.NET-Docker-Containern in einer Azure Container Registry-Instanz
description: Erfahren Sie, wie Sie Visual Studio-Containertools zum Bereitstellen einer ASP.NET- oder ASP.NET Core-Web-App in einer Containerregistrierung verwenden.
author: ghogen
manager: jmartens
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: 74a74e17dcc909b529a0afad1d66959000c80455
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859540"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Bereitstellen eines ASP.NET-Containers an eine Containerregistrierung mithilfe von Visual Studio

## <a name="overview"></a>Übersicht

Docker ist eine einfache Container-Engine, in gewisser Weise mit einem virtuellen Computer vergleichbar, die Sie zum Hosten von Anwendungen und Diensten verwenden können.
Dieses Tutorial führt Sie durch die Verwendung von Visual Studio zum Veröffentlichen Ihrer Containeranwendung für eine [Azure-Containerregistrierung](https://azure.microsoft.com/services/container-registry).

Wenn Sie kein Azure-Abonnement besitzen, können Sie ein [kostenloses Konto](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) erstellen, bevor Sie beginnen.

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieses Tutorials benötigen Sie Folgendes:

::: moniker range="vs-2017"
* Installation der neuesten Version von [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) mit der Workload „ASP.NET und Webentwicklung“
::: moniker-end
::: moniker range=">=vs-2019"
* Installation der neuesten Version von [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit der Workload „ASP.NET und Webentwicklung“
::: moniker-end
* Installieren von [Docker für Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Erstellen einer ASP.NET Core-Web-App

Die folgenden Schritte führen Sie durch die Erstellung einer einfachen ASP.NET Core-App, die in diesem Tutorial verwendet wird. Wenn Sie bereits über ein Projekt verfügen, können Sie diesen Abschnitt überspringen.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

::: moniker range="vs-2017"

## <a name="publish-your-container-to-azure-container-registry"></a>Veröffentlichen Ihres Containers in Azure Container Registry

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen**.
2. Wählen Sie im Dialogfeld **Ziel veröffentlichen** die Registerkarte **Container Registry** aus.
3. Wählen Sie **Neue Azure-Containerregistrierung**, und klicken Sie auf **Veröffentlichen**.
4. Geben Sie die gewünschten Werte im Feld **Neue Azure-Containerregistrierung erstellen** ein.

    | Einstellung      | Empfohlener Wert  | Beschreibung                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-Präfix** | Global eindeutiger Name | Name, der Ihre Containerregistrierung eindeutig identifiziert. |
    | **Abonnement** | Auswählen Ihres Abonnements | Das zu verwendende Azure-Abonnement. |
    | **[Ressourcengruppe](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Name der Ressourcengruppe, in der die Containerregistrierung erstellt werden soll. Wählen Sie **Neu** aus, um eine neue Ressourcengruppe zu erstellen.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Dienstebene der Containerregistrierung  |
    | **Registrierungsstandort** | Ein Standort in Ihrer Nähe | Wählen Sie einen Standort in einer [Region](https://azure.microsoft.com/regions/) in Ihrer Nähe oder in der Nähe anderer Dienste aus, die Ihre Containerregistrierung verwenden werden. |

    ![Visual Studio-Dialogfeld zum Erstellen einer Azure-Containerregistrierung](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Klicken Sie auf **Erstellen**
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Veröffentlichen Ihres Containers in Azure Container Registry
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen**.
2. Wählen Sie im Dialogfeld **Veröffentlichen** die Option **Docker-Containerregistrierung** aus.

   ![Screenshot des Dialogfelds „Veröffentlichen“: Auswählen von „Docker-Containerregistrierung“](media/container-tools/vs-2019/docker-container-registry.png)

3. Wählen Sie **Neue Azure Container Registry-Instanz erstellen**.
 
   ![Screenshot des Dialogfelds „Veröffentlichen“: Auswählen von „Neue Azure Container Registry erstellen“](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. Geben Sie die gewünschten Werte auf dem Bildschirm **Azure Container Registry** ein.

    | Einstellung      | Vorgeschlagener Wert  | Beschreibung                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-Präfix** | Global eindeutiger Name | Name, der Ihre Containerregistrierung eindeutig identifiziert. |
    | **Abonnement** | Auswählen Ihres Abonnements | Das zu verwendende Azure-Abonnement. |
    | **[Ressourcengruppe](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Name der Ressourcengruppe, in der die Containerregistrierung erstellt werden soll. Wählen Sie **Neu** aus, um eine neue Ressourcengruppe zu erstellen.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Dienstebene der Containerregistrierung  |
    | **Registrierungsstandort** | Ein Standort in Ihrer Nähe | Wählen Sie einen Standort in einer [Region](https://azure.microsoft.com/regions/) in Ihrer Nähe oder in der Nähe anderer Dienste aus, die Ihre Containerregistrierung verwenden werden. |

    ![Visual Studio-Dialogfeld zum Erstellen einer Azure-Containerregistrierung](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png)

5. Klicken Sie auf **Erstellen**.

6. Wählen Sie **Fertig stellen** aus, um den Vorgang abzuschließen.
::: moniker-end

Sie können jetzt den Container aus der Registrierung auf einen beliebigen Host ziehen, auf dem Docker-Images ausgeführt werden können. Beispiel: [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Weitere Informationen

[Schnellstart: Bereitstellen einer Containerinstanz in Azure mithilfe der Azure CLI](/azure/container-instances/container-instances-quickstart)
