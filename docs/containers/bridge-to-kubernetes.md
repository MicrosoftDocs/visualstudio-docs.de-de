---
title: Verwenden von Bridge to Kubernetes mit Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Hier erfahren Sie, wie Sie Bridge to Kubernetes mit Visual Studio verwenden, um Ihren Entwicklungscomputer mit einem Kubernetes-Cluster zu verbinden.
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, Container
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: 7bbeec2baab018ea770dbee60db507399ebeb745
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860442"
---
# <a name="use-bridge-to-kubernetes"></a>Verwenden von Bridge to Kubernetes

Mit Bridge to Kubernetes können Sie Datenverkehr zwischen Ihrem Kubernetes-Cluster und dem auf dem Entwicklungscomputer ausgeführten Code weiterleiten. Darüber hinaus finden Sie in dieser Anleitung ein Skript zur Bereitstellung einer umfangreichen Beispielanwendung mit mehreren Microservices auf einem Kubernetes-Cluster.

## <a name="before-you-begin"></a>Voraussetzungen

In dieser Anleitung wird die [Azure Dev Spaces-Beispielanwendung „Bike Sharing“][bike-sharing-github] verwendet, um zu veranschaulichen, wie Sie Ihren Entwicklungscomputer mit einem Kubernetes-Cluster verbinden. Wenn Sie bereits über eine eigene Anwendung in einem Kubernetes-Cluster verfügen, können Sie die folgenden Schritte dennoch ausführen und dabei die Namen Ihrer eigenen Dienste verwenden.

### <a name="prerequisites"></a>Voraussetzungen

* Ein Azure-Abonnement. Falls Sie über kein Azure-Abonnement verfügen, können Sie ein [kostenloses Konto](https://azure.microsoft.com/free) erstellen.
* Die [Azure CLI][azure-cli] muss installiert sein.
* Mindestens die [Visual Studio 2019][visual-studio]-Version 16.7 Preview 4 muss installiert sein und unter Windows 10 mit der Workload *Azure-Entwicklung* ausgeführt werden.
* [Installierte Erweiterung „Bridge to Kubernetes“][btk-extension]

Installieren Sie für .NET-Konsolenanwendungen außerdem das NuGet-Paket *Microsoft.VisualStudio.Azure.Kubernetes.Tools.Targets*.

## <a name="create-a-kubernetes-cluster"></a>Erstellen eines Kubernetes-Clusters

Erstellen Sie einen AKS-Cluster in einer [unterstützten Region][supported-regions]. Mit den unten angegebenen Befehlen wird eine Ressourcengruppe mit dem Namen *MyResourceGroup* und der AKS-Cluster *MyAKS* erstellt.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Installieren der Beispielanwendung

Installieren Sie die Beispielanwendung mithilfe des bereitgestellten Skripts auf Ihrem Cluster. Sie können das Skript auch mithilfe von [ Azure Cloud Shell][azure-cloud-shell] ausführen.

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

Navigieren Sie zur Beispielanwendung auf Ihrem Cluster, indem Sie die öffentliche URL aufrufen, die in der Ausgabe des Installationsskripts angezeigt wird.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

Im obigen Beispiel lautet die öffentliche URL `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Herstellen einer Clusterverbindung und Debuggen eines Diensts

Laden Sie auf dem Entwicklungscomputer die Kubernetes-CLI herunter, und konfigurieren Sie sie, um unter Verwendung von [az aks get-credentials][az-aks-get-credentials] eine Verbindung mit Ihrem Kubernetes-Cluster herzustellen.

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

Öffnen Sie in GitHub im Repository [Bike Sharing sample application][bike-sharing-github] (Beispielanwendung für das Bikesharing) das Dropdownmenü der grünen Schaltfläche **Code**, und klicken Sie auf **Open in Visual Studio** (In Visual Studio öffnen), um das Repository lokal zu klonen und den Ordner in Visual Studio zu öffnen. Klicken Sie dann auf **Datei** > **Projekt öffnen**, um das Projekt **app.csproj** im Ordner *samples/BikeSharingApp/ReservationEngine* zu öffnen.

Klicken Sie in Ihrem Projekt wie nachfolgend gezeigt im Dropdownmenü mit den Starteinstellungen auf die Option **Bridge to Kubernetes**.

![Klicken auf Bridge to Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Klicken Sie auf die Startschaltfläche neben *Bridge to Kubernetes*. Gehen Sie im Dialogfeld **Profil für Brücke zu Kubernetes erstellen** wie folgt vor:

* Wählen Sie Ihr Abonnement aus.
* Wählen Sie *MyAKS* als Cluster aus.
* Wählen Sie *bikeapp* als Namespace aus.
* Wählen Sie *reservationengine* als Dienst für die Umleitung aus.
* Wählen Sie *app* als Startprofil aus.
* Wählen Sie `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` als URL zum Starten Ihres Browsers aus.

![Auswählen des Bridge to Kubernetes-Clusters](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> Sie können nur Dienste umleiten, die über einen einzelnen Pod verfügen.

Geben Sie an, ob die Ausführung isoliert erfolgen soll. Dies bedeutet, dass andere Benutzer des Clusters, nicht von Ihren Änderungen betroffen sind. Dieser Isolationsmodus wird erreicht, indem Sie Ihre Anforderungen an Ihre Kopie des jeweiligen betroffenen Diensts weiterleiten, während der gesamte andere Datenverkehr normal weiter verläuft. Eine ausführlichere Erläuterung dazu finden Sie unter [Funktionsweise von Bridge to Kubernetes][btk-overview-routing].

Klicken Sie auf **Speichern und Debuggen starten**.

Der gesamte Datenverkehr im Kubernetes-Cluster wird für den Dienst *reservationengine* an die Version der Anwendung umgeleitet, die auf dem Entwicklungscomputer ausgeführt wird. Bridge to Kubernetes leitet zudem den gesamten ausgehenden Datenverkehr der Anwendung zurück an den Kubernetes-Cluster.

> [!NOTE]
> Sie werden aufgefordert, die Ausführung von *EndpointManager* mit erhöhten Rechten zuzulassen und zu erlauben, dass Ihre Hostdatei geändert wird.

Sobald in der Statusleiste angezeigt wird, dass Sie mit dem `reservationengine`-Dienst verbunden sind, ist Ihr Entwicklungscomputer verbunden.

![Verbundener Entwicklungscomputer](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Bei nachfolgenden Starts wird Ihnen das Dialogfeld **Profil für Brücke zu Kubernetes erstellen** nicht mehr angezeigt. Diese Einstellungen werden in den Projekteigenschaften unter **Debuggen** aktualisiert.

Sobald Ihr Entwicklungscomputer verbunden ist, wird Datenverkehr für den Dienst, den Sie ersetzen, an den Entwicklungscomputer umgeleitet.

## <a name="set-a-break-point"></a>Festlegen eines Haltepunkts

Öffnen Sie [BikesHelper.cs][bikeshelper-cs-breakpoint], und klicken Sie auf Zeile 26, um den Cursor dort zu platzieren. Legen Sie durch Drücken von *F9* oder Klicken auf **Debuggen** > **Haltepunkt umschalten** einen Haltepunkt fest.

Rufen Sie die öffentliche URL auf, um zur Beispielanwendung zu navigieren. Wählen Sie **Aurelia Briggs (customer)** als Benutzer und dann ein zu mietendes Fahrrad aus. Klicken Sie auf **Rent Bike** (Fahrrad mieten). Wechseln Sie zurück zu Visual Studio. Sie sehen, dass Zeile 26 hervorgehoben ist. Durch den festgelegten Haltepunkt wurde der Dienst in Zeile 26 angehalten. Drücken Sie zum Fortsetzen des Diensts auf **F5**, oder klicken Sie auf **Debuggen** > **Weiter**. Wechseln Sie erneut in Ihren Browser, und überprüfen Sie, ob auf der Seite angezeigt wird, dass Sie das Fahrrad gemietet haben.

Entfernen Sie den Haltepunkt, indem Sie den Cursor in `BikesHelper.cs` in Zeile 26 platzieren und **F9** drücken.

> [!NOTE]
> Wenn Sie den Debugtask anhalten, wird standardmäßig auch Ihr Entwicklungscomputer vom Kubernetes-Cluster getrennt. Sie können dieses Verhalten ändern, indem Sie im Abschnitt **Kubernetes-Debugtools** in den Debugoptionen die Einstellung **Verbindung nach dem Debuggen trennen** auf `false` festlegen. Wenn Sie diese Einstellung geändert haben, bleibt Ihr Entwicklungscomputer verbunden, wenn Sie das Debuggen beenden und starten. Zum Trennen Ihres Entwicklungscomputers vom Cluster klicken Sie in der Symbolleiste auf die Schaltfläche **Trennen**.

## <a name="additional-configuration"></a>Zusätzliche Konfiguration

Bridge to Kubernetes kann die Weiterleitung des Datenverkehrs und die Replikation von Umgebungsvariablen ohne weitere Konfiguration verarbeiten. Wenn Sie Dateien herunterladen müssen, die in den Container im Kubernetes-Cluster eingebunden sind, z. B. eine ConfigMap-Datei, können Sie eine `KubernetesLocalProcessConfig.yaml`-Datei erstellen, um diese Dateien auf den Entwicklungscomputer herunterzuladen. Weitere Informationen finden Sie unter [Verwenden von KubernetesLocalProcessConfig.yaml zur zusätzlichen Konfiguration für Bridge to Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Verwenden der Protokollierung und Diagnose

Sie finden die Diagnoseprotokolle auf dem Entwicklungscomputer im Verzeichnis `Bridge to Kubernetes` im Unterverzeichnis *TEMP*. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Entfernen der Beispielanwendung aus dem Cluster

Entfernen Sie die Beispielanwendung mithilfe des bereitgestellten Skripts von Ihrem Cluster.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Nächste Schritte

Informieren Sie sich über die Funktionsweise von Bridge to Kubernetes.

> [!div class="nextstepaction"]
> [Funktionsweise von Bridge to Kubernetes](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/overview.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation