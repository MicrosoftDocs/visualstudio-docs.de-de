---
title: Visual Studio-Containertools mit ASP.NET Core und React.js
author: ghogen
description: Erfahren Sie mehr über die Verwendung von Visual Studio-Containertools und Docker für Windows
ms.author: ghogen
ms.date: 05/14/2020
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: 321d85537f210d17414be115b8f6b3f8b8d5b3c9
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249205"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>Schnellstart: Verwenden von Docker mit einer React-App mit einer einzigen Seite in Visual Studio

Mit Visual Studio können Sie ASP.NET Core-Container-Apps mühelos erstellen, debuggen und ausführen (einschließlich Apps mit clientseitigem JavaScript, z.B. React.js-Apps mit einer einzigen Seite). Anschließend können Sie sie in Azure Container Registry (ACR), Docker Hub, Azure App Service oder Ihrer eigenen Containerregistrierung veröffentlichen. In diesem Artikel wird die Veröffentlichung in ACR veranschaulicht.

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) mit den Workloads für **Webentwicklung**, **Azure-Tools** und bzw. oder **plattformübergreifende .NET Core-Entwicklung**
* Zum Veröffentlichen in Azure Container Registry ist ein Azure-Abonnement erforderlich. [Registrieren Sie sich für eine kostenlose Testversion.](https://azure.microsoft.com/offers/ms-azr-0044p/)
* [Node.js](https://nodejs.org/en/download/)
* Für Windows-Container, Windows 10, Version 1903 oder höher, um die Docker-Images zu verwenden, auf die in diesem Artikel verwiesen wird.
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) mit installierten Workloads für **Webentwicklung**, **Azure-Tools** und/oder **plattformübergreifende .NET Core-Entwicklung**
* [.NET Core 2.2-Entwicklungstools](https://dotnet.microsoft.com/download/dotnet-core/2.2) zur Entwicklung mit .NET Core 2.2
* Zum Veröffentlichen in Azure Container Registry ist ein Azure-Abonnement erforderlich. [Registrieren Sie sich für eine kostenlose Testversion.](https://azure.microsoft.com/offers/ms-azr-0044p/)
* [Node.js](https://nodejs.org/en/download/)
* Für Windows-Container, Windows 10, Version 1903 oder höher, um die Docker-Images zu verwenden, auf die in diesem Artikel verwiesen wird.
::: moniker-end

## <a name="installation-and-setup"></a>Installation und Einrichtung

Lesen Sie vor der Installation von Docker zunächst [Docker Desktop for Windows: What to know before you install (Docker Desktop für Windows: Was vor der Installation zu beachten ist)](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install). Installieren Sie anschließend [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows).

## <a name="create-a-project-and-add-docker-support"></a>Erstellen eines Projekts und Hinzufügen der Docker-Unterstützung

::: moniker range="vs-2017"
1. Erstellen Sie ein neues Projekt über die Vorlage **ASP.NET Core-Webanwendung**.
1. Wählen Sie **React.js** aus. **Docker-Unterstützung aktivieren** kann nicht ausgewählt werden, aber Sie können diese Unterstützung nach dem Erstellen des Projekts hinzufügen.

   ![Screenshot des neuen React.js-Projekts](media/container-tools-react/vs2017/new-react-project.png)

1. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen** > **Docker-Unterstützung** aus, um Ihrem Projekt ein Dockerfile hinzufügen.

   ![Hinzufügen von Docker-Unterstützung](media/container-tools-react/vs2017/add-docker-support.png)

1. Wählen Sie den Containertyp aus, und klicken Sie auf **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
1. Erstellen Sie ein neues Projekt über die Vorlage **ASP.NET Core-Webanwendung**.
1. Wählen Sie **React.js** aus, und klicken Sie auf **Erstellen**. **Docker-Unterstützung aktivieren** kann nicht ausgewählt werden, aber Sie können diese Unterstützung später hinzufügen.

   ![Screenshot des neuen React.js-Projekts](media/container-tools-react/vs2019/new-react-project.png)

1. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen** > **Docker-Unterstützung** aus, um Ihrem Projekt ein Dockerfile hinzufügen.

   ![Hinzufügen von Docker-Unterstützung](media/container-tools-react/vs2017/add-docker-support.png)

1. Wählen Sie den Containertyp aus.
::: moniker-end

Der nächste Schritt ist je nachdem, ob Sie Linux-oder Windows-Container verwenden, unterschiedlich.

## <a name="modify-the-dockerfile-linux-containers"></a>Ändern der Dockerfile (Linux-Container)

Eine *Dockerfile*-Datei, der wichtigste Bestandteil beim Erstellen eines endgültigen Docker-Images, wird im Projekt erstellt. Verweisen Sie auf einen [Dockerfile-Verweis](https://docs.docker.com/engine/reference/builder/), damit Sie einen Überblick über die darin enthaltenen Befehle erlangen.

Öffnen Sie das *Dockerfile* im Projekt, und fügen Sie die folgenden Zeilen hinzu, um Node.js 10.x im Container zu installieren. Achten Sie darauf, dass diese Zeilen beide im ersten Abschnitt eingefügt werden, um die Installation von Node Package Manager (*npm.exe*) dem Basisimage sowie im Abschnitt `build` hinzuzufügen.

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

Das *Dockerfile* sollte in etwa wie folgt aussehen:

```Dockerfile
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication37/WebApplication37.csproj", "WebApplication37/"]
RUN dotnet restore "WebApplication37/WebApplication37.csproj"
COPY . .
WORKDIR "/src/WebApplication37"
RUN dotnet build "WebApplication37.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication37.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication37.dll"]
```

Das obige *Dockerfile* basiert auf dem Image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) und enthält Anweisungen zum Anpassen des Basisimages durch Erstellen Ihres Projekts und anschließendem Hinzufügen zum Container.

Wenn im neuen Projektdialogfeld das Kontrollkästchen **Configure for HTTPS** (Für HTTPS konfigurieren) aktiviert ist, werden durch die *Dockerfile*-Datei zwei Ports verfügbar gemacht. Ein Port wird für den HTTP-Datenverkehr, der andere für HTTPS verwendet. Wenn dieses Kontrollkästchen nicht aktiviert ist, wird nur der Port 80 für den HTTP-Datenverkehr verfügbar gemacht.

## <a name="modify-the-dockerfile-windows-containers"></a>Ändern der Dockerfile (Windows-Container)

Öffnen Sie die Projektdatei durch Doppelklicken auf den Projektknoten. Aktualisieren Sie die Projektdatei (*.csproj), indem Sie die folgende Eigenschaft als untergeordnetes Element des Elements `<PropertyGroup>` hinzufügen:

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

Aktualisieren Sie die Dockerfile durch Hinzufügen der folgenden Zeilen. Hierdurch werden „node“ und „npm“ in den Container kopiert.

   1. Fügen Sie der ersten Zeile der Dockerfile ``# escape=` `` hinzu.
   1. Fügen Sie vor `FROM … base` die folgenden Zeilen hinzu.

      ```Dockerfile
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. Fügen Sie vor und hinter `FROM … build` die folgenden Zeilen hinzu.

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. Die vollständige Dockerfile sollte in etwa wie folgt aussehen:

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-1903 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplication7/WebApplication37.csproj", "WebApplication37/"]
      RUN dotnet restore "WebApplication7/WebApplication7.csproj"
      COPY . .
      WORKDIR "/src/WebApplication37"
      RUN dotnet build "WebApplication37.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplication37.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplication37.dll"]
      ```

   1. Aktualisieren Sie die. DOCKERIGNORE-Datei, indem Sie `**/bin`entfernen.

## <a name="debug"></a>Debug

Wählen Sie in der Symbolleiste im Dropdownmenü „Debuggen“ die Option **Docker** aus, und starten Sie das Debuggen der Anwendung. Möglicherweise wird eine Meldung mit einer Eingabeaufforderung zum Vertrauen eines Zertifikats angezeigt. Vertrauen Sie dem Zertifikat, um fortzufahren.  Beim ersten Build lädt Docker die Basisimages herunter, weshalb der Vorgang etwas länger dauern kann.

Die Option **Containertools** im Fenster **Ausgabe** zeigt, welche Aktionen ausgeführt werden. Die mit *npm.exe* verknüpften Installationsschritte werden angezeigt.

Der Browser zeigt die Startseite der App.

::: moniker range="vs-2017"
   ![Screenshot der ausgeführten App](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Screenshot der ausgeführten App](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

Navigieren Sie zur Seite *Indikator*, und testen Sie den clientseitigen Code für den Indikator, indem Sie auf die Schaltfläche **Inkrement** klicken.

Öffnen Sie die **Paket-Manager-Konsole** über das Menü **Extras**> NuGet-Paket-Manager > **Paket-Manager-Konsole**.

Das resultierende Docker-Image der App wird mit dem Tag *dev* versehen. Das Image basiert auf dem Tag *2.2-aspnetcore-runtime* des Basisimages *microsoft/dotnet*. Führen Sie im Fenster **Paket-Manager-Konsole** den Befehl `docker images` aus. Die Images auf dem Computer werden angezeigt:

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> Das **dev**-Image enthält weder die Binärdateien der App noch andere Inhalte, da die **Debugkonfigurationen** die Volumebereitstellung nutzen, um die iterativen Bearbeitungs- und Debugfunktionen bereitzustellen. Verwenden Sie die **Releasekonfiguration**, um ein Produktionsimage zu erstellen, das alle Inhalte enthält.

Führen Sie in der Paket-Manager-Konsole den Befehl `docker ps` aus. Beachten Sie, dass die App mithilfe des Containers ausgeführt wird:

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="publish-docker-images"></a>Veröffentlichen von Docker-Images

Sobald der Entwicklungs- und Debugzyklus der App abgeschlossen ist, können Sie ein Produktionsimage der App erstellen.

1. Wählen Sie im Dropdownmenü „Konfiguration“ die Option **Release** aus, und erstellen Sie die App.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen**.
1. Wählen Sie im Dialogfeld „Ziel veröffentlichen“ die Registerkarte **Container Registry**.
1. Klicken Sie auf **Neue Azure Container Registry-Instanz erstellen**, und klicken Sie dann auf **Veröffentlichen**.
1. Geben Sie die gewünschten Werte im Feld **Neue Azure-Containerregistrierung erstellen** ein.

    | Einstellung      | Empfohlener Wert  | Beschreibung                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS-Präfix** | Global eindeutiger Name | Name, der Ihre Containerregistrierung eindeutig identifiziert. |
    | **Abonnement** | Auswählen Ihres Abonnements | Das zu verwendende Azure-Abonnement. |
    | **[Ressourcengruppe](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Name der Ressourcengruppe, in der die Containerregistrierung erstellt werden soll. Wählen Sie **Neu** aus, um eine neue Ressourcengruppe zu erstellen.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Standard | Dienstebene der Containerregistrierung  |
    | **Registrierungsstandort** | Ein Standort in Ihrer Nähe | Wählen Sie einen Standort in einer [Region](https://azure.microsoft.com/regions/) in Ihrer Nähe oder in der Nähe anderer Dienste aus, die Ihre Containerregistrierung verwenden werden. |

    ![Visual Studio-Dialogfeld zum Erstellen einer Azure-Containerregistrierung][0]

1. Klicken Sie auf **Erstellen**.

   ![Screenshot mit erfolgreicher Veröffentlichung](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>Nächste Schritte

Sie können jetzt den Container aus der Registrierung auf einen beliebigen Host ziehen, auf dem Docker-Images ausgeführt werden können. Beispiel: [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="additional-resources"></a>Zusätzliche Ressourcen

* [Containerentwicklung mit Visual Studio](/visualstudio/containers)
* [Problembehandlung bei der Visual Studio-Entwicklung mit Docker](troubleshooting-docker-errors.md)
* [GitHub-Repository mit Visual Studio-Containertools](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end
