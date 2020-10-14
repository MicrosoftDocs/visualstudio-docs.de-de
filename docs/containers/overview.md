---
title: Visual Studio-Containertools unter Windows
description: Lernen Sie die in Visual Studio verfügbaren Tools zum Arbeiten mit Docker kennen.
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: f1473c731dbf9413cf695e1b2331039c3880b8d7
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2020
ms.locfileid: "91829868"
---
# <a name="container-tools-in-visual-studio"></a>Containertools in Visual Studio

Die in Visual Studio enthaltenen Tools für die Entwicklung mit Containern sind einfach zu verwenden und können das Erstellen, Debuggen und Bereitstellen von Containeranwendungen erheblich vereinfachen. Sie können mit einem Container für ein einzelnes Projekt arbeiten oder die Containerorchestrierung mit Docker Compose, Service Fabric oder Kubernetes zum Arbeiten mit mehreren Diensten in Containern verwenden.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Voraussetzungen

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) mit den Workloads für **Webentwicklung**, **Azure-Tools** und bzw. oder **plattformübergreifende .NET Core-Entwicklung**
* Zum Veröffentlichen in Azure Container Registry ist ein Azure-Abonnement erforderlich. [Registrieren Sie sich für eine kostenlose Testversion.](https://azure.microsoft.com/offers/ms-azr-0044p/)

## <a name="docker-support-in-visual-studio"></a>Docker-Unterstützung in Visual Studio

Docker-Unterstützung ist für ASP.NET-Projekte, ASP.NET Core-Projekte sowie .NET Core- und .NET Framework-Konsolenprojekte verfügbar.

Die Unterstützung für Docker in Visual Studio hat sich im Verlauf einer Reihe von Versionen aufgrund von Kundenanforderungen geändert. Es gibt zwei Stufen der Docker-Unterstützung, die Sie einem Projekt hinzufügen können, und die unterstützten Optionen unterscheiden sich je nach Projekttyp und Visual Studio-Version. Bei einigen unterstützten Projekttypen können Sie in dem Fall, dass Sie nur einen Container für ein einzelnes Projekt ohne Verwendung der Orchestrierung wünschen, die Docker-Unterstützung hinzufügen.  Die nächste Stufe ist die Unterstützung der Containerorchestrierung, bei der entsprechende Unterstützungsdateien für den jeweils ausgewählten Orchestrator hinzugefügt werden.

Bei Visual Studio 2017 können Sie Docker Compose und Service Fabric als Containerorchestrierungsdienste verwenden.  Sie können auch Kubernetes verwenden, wenn Sie die [Visual Studio-Tools für Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes) installieren.

> [!NOTE]
> Wenn Sie eine Version von Visual Studio 2017 vor 15.8 verwenden, oder wenn Sie die .NET Framework-Projektvorlage (nicht .NET Core) verwenden, wird beim Hinzufügen der Docker-Unterstützung die Orchestrierungsunterstützung mithilfe von Docker Compose automatisch hinzugefügt. Die Unterstützung der Containerorchestrierung über Docker Compose wird in Visual Studio 2017, Version 15.0 bis 15.7, und für .NET Framework-Projekte automatisch hinzugefügt.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Voraussetzungen

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit installierten Workloads für **Webentwicklung**, **Azure-Tools** und/oder **plattformübergreifende .NET Core-Entwicklung**
* [.NET Core-Entwicklungstools](https://dotnet.microsoft.com/download/dotnet-core/) für die Entwicklung mit .NET Core.
* Zum Veröffentlichen in Azure Container Registry ist ein Azure-Abonnement erforderlich. [Registrieren Sie sich für eine kostenlose Testversion.](https://azure.microsoft.com/offers/ms-azr-0044p/)

## <a name="docker-support-in-visual-studio"></a>Docker-Unterstützung in Visual Studio

Docker-Unterstützung ist für ASP.NET-Projekte, ASP.NET Core-Projekte sowie .NET Core- und .NET Framework-Konsolenprojekte verfügbar.

Die Unterstützung für Docker in Visual Studio hat sich im Verlauf einer Reihe von Versionen aufgrund von Kundenanforderungen geändert. Es gibt zwei Stufen der Docker-Unterstützung, die Sie einem Projekt hinzufügen können, und die unterstützten Optionen unterscheiden sich je nach Projekttyp und Visual Studio-Version. Bei einigen unterstützten Projekttypen können Sie in dem Fall, dass Sie nur einen Container für ein einzelnes Projekt ohne Verwendung der Orchestrierung wünschen, die Docker-Unterstützung hinzufügen.  Die nächste Stufe ist die Unterstützung der Containerorchestrierung, bei der entsprechende Unterstützungsdateien für den jeweils ausgewählten Orchestrator hinzugefügt werden.

Bei Visual Studio 2019 können Sie Docker Compose, Kubernetes und Service Fabric als Containerorchestrierungsdienste verwenden.

> [!NOTE]
> Wenn Sie die vollständige Projektvorlage der .NET Framework-Konsole verwenden, steht Ihnen nach dem Erstellen eines Projekts die Option **Unterstützung für Containerorchestrator hinzufügen** zur Verfügung. Zusätzlich haben Sie die Wahl, ob Sie Service Fabric oder Docker Compose verwenden möchten. Sie haben bei Einzelprojekten ohne Orchestrierung nicht die Möglichkeit, bereits während der Projekterstellung Unterstützung hinzuzufügen. Auch die Option **Add Docker Support** (Docker-Support hinzufügen) steht Ihnen nicht zur Verfügung.

In Visual Studio 2019 Version 16.4 und höher ist das Fenster **Container** verfügbar, über das Sie ausgeführte Container, Umgebungsvariablen, Protokolle und Portzuordnungen anzeigen, verfügbare Images durchsuchen, das Dateisystem untersuchen, einen Debugger anfügen oder ein Terminalfenster in der Containerumgebung öffnen können. Weitere Informationen finden Sie unter [Anzeigen und Diagnostizieren von Containern und Images in Visual Studio](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Hinzufügen der Docker-Unterstützung

Sie können die Docker-Unterstützung während der Projekterstellung aktivieren, indem Sie beim Erstellen eines neuen Projekts die Option **Docker-Unterstützung aktivieren** auswählen, wie im folgenden Screenshot gezeigt:

::: moniker range="vs-2017"
![Aktivieren der Docker-Unterstützung für neue ASP.NET Core-Web-App in Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Aktivieren der Docker-Unterstützung für neue ASP.NET Core-Web-App in Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> Für .NET Framework-Projekte (nicht .NET Core) sind nur Windows-Container verfügbar.

Sie können die Docker-Unterstützung einem vorhandenen Projekt hinzufügen, indem Sie im **Projektmappen-Explorer** die Option **Hinzufügen** > **Docker-Unterstützung** auswählen. Die Befehle **Hinzufügen > Docker-Unterstützung** und **Hinzufügen > Unterstützung für Containerorchestrator** befinden sich im ** Projektmappen-Explorer** im Kontextmenü des Projektknotens für ein ASP.NET Core-Projekt wie im folgenden Screenshot gezeigt:

![Menüoption „Hinzufügen > Docker-Unterstützung“ in Visual Studio](./media/overview/add-docker-support-menu.png)

Wenn Sie die Docker-Unterstützung hinzufügen oder aktivieren, fügt Visual Studio dem Projekt Folgendes hinzu:

- eine *Dockerfile*-Datei
- eine DOCKERIGNORE-Datei
- einen NuGet-Paketverweis auf „Microsoft.VisualStudio.Azure.Containers.Tools.Targets“

::: moniker range=">=vs-2019"
Nachdem Sie die Docker-Unterstützung hinzugefügt haben, sieht die Projektmappe wie folgt aus:

![Screenshot des Projektmappen-Explorers mit Dockerfile- und DOCKERIGNORE-Datei](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Wenn Sie die Docker-Unterstützung während der Projekterstellung für ein ASP.NET-Projekt (.NET Framework, kein .NET Core-Projekt) aktivieren, wie es im folgenden Screenshot gezeigt ist, wird auch die Unterstützung der Containerorchestrierung hinzugefügt.

![Aktivieren der Docker Compose-Unterstützung für ein ASP.NET-Projekt](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Docker Compose-Unterstützung

Wenn Sie eine Projektmappe mit mehreren Containern mithilfe von Docker Compose erstellen möchten, fügen Sie Ihren Projekten die Unterstützung der Containerorchestrierung hinzu. Dadurch können Sie eine Gruppe von Containern (eine gesamte Projektmappe oder eine Gruppe von Projekten) gleichzeitig ausführen und debuggen, wenn diese in derselben *docker-compose.yml*-Datei definiert sind.

Um die Unterstützung der Containerorchestrierung mithilfe von Docker Compose hinzuzufügen, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe oder den Projektknoten, und wählen Sie **Hinzufügen > Unterstützung für Containerorchestrator** aus. Wählen Sie dann **Docker Compose** aus, um die Container zu verwalten.

Nachdem Sie Ihrem Projekt die Unterstützung der Containerorchestrierung hinzugefügt haben, können Sie im **Projektmappen-Explorer** sehen, dass dem Projekt eine *Dockerfile*-Datei (falls bisher noch keine vorhanden war) und der Projektmappe ein Ordner **docker-compose** hinzugefügt wurde, wie es hier gezeigt ist:

![Docker-Dateien im Projektmappen-Explorer in Visual Studio](media/overview/docker-support-solution-explorer.png)

Wenn *docker-compose.yml* bereits vorhanden ist, fügt Visual Studio nur die erforderlichen Zeilen zum Konfigurationscode hinzu.

Wiederholen Sie den Vorgang für die anderen Projekte, die Sie mithilfe von Docker Compose steuern möchten.

## <a name="kubernetes-support"></a>Kubernetes-Unterstützung

::: moniker range="vs-2017"
Zum Hinzufügen der Kubernetes-Unterstützung installieren Sie die [Visual Studio-Tools für Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).
::: moniker-end

Mit der Kubernetes-Unterstützung können Sie eine Verbindung zwischen Ihrem lokalen Projekt und einem Kubernetes-Cluster unter [Azure Kubernetes Service (AKS)](/azure/aks) aktivieren und dadurch Ihre Dienste unter AKS mithilfe von Visual Studio ändern und debuggen.  Dieser Dienst wird von [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio) bereitgestellt. Azure Dev Spaces ermöglicht Ihnen auch das Einrichten separater Verzweigungen Ihrer Kubernetes-Dienste, sogenannter *Dev Spaces*, für Entwicklungszwecke, sodass Sie Produktionsdienste effizient von Arbeitsversionen in der Entwicklung isolieren und unterschiedliche Änderungen sauber voneinander getrennt halten können.

Wenn Sie Ihren Projekten Kubernetes-Unterstützung hinzufügen möchten, wählen Sie beim Hinzufügen der Unterstützung für die Containerorchestrierung die Option **Kubernetes/Helm** aus. Ihrem Projekt werden mehrere Dateien hinzugefügt, einschließlich *azds.yaml*, die Azure Dev Spaces konfiguriert, und Helm-Diagramme, die die Struktur Ihrer Kubernetes-Dienste beschreiben.

## <a name="service-fabric-support"></a>Service Fabric-Unterstützung

Mit Service Fabric-Tools in Visual Studio können Sie für Azure Service Fabric entwickeln und debuggen, lokal ausführen und debuggen sowie in Azure bereitstellen.

::: moniker range="vs-2017"
Visual Studio 2017 Version 15.9 und höher mit installierter Workload für die Azure-Entwicklung unterstützt die Entwicklung von Containermicroservices mithilfe von Windows-Containern und Service Fabric-Orchestrierung.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 unterstützt die Entwicklung von Containermicroservices mithilfe von Windows-Containern und Service Fabric-Orchestrierung.
::: moniker-end

Ein ausführliches Tutorial finden Sie unter [Tutorial: Bereitstellen einer .NET-Anwendung in einem Windows-Container in Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Weitere Informationen zu Azure Service Fabric finden Sie unter [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Continuous Delivery und Continuous Integration (CI/CD)

Visual Studio lässt sich problemlos in Azure Pipelines integrieren, um eine automatisierte und kontinuierliche Integration und Bereitstellung von Änderungen an Ihrem Servicecode und Ihrer Konfiguration zu ermöglichen. Informationen zu den ersten Schritten finden Sie unter [Erstellen Ihrer ersten Pipeline](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2&preserve-view=true).

Informationen zu Service Fabric finden Sie unter [Tutorial: Bereitstellen einer ASP.NET Core-App in Azure Service Fabric mithilfe von Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric).

Informationen zu Kubernetes finden Sie unter [Bereitstellen einer Docker-Container-App in Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops&preserve-view=true).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Implementierung der Dienste und Verwendung von Visual Studio-Tools für das Arbeiten mit Containern finden Sie in den folgenden Artikeln:

[Debuggen von Apps in einem lokalen Docker-Container](edit-and-refresh.md)

[Bereitstellen eines ASP.NET-Containers an eine Containerregistrierung mithilfe von Visual Studio](hosting-web-apps-in-docker.md)
