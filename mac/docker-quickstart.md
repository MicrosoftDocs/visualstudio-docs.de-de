---
title: Erste Schritte mit Docker
description: Informationen zum Hinzufügen von Docker zu Ihren Projekten in Visual Studio für Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: e2bfb78369ae5da389820a318196dd7e9e13e897
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493074"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Erste Schritte mit Docker in Visual Studio für Mac

Mit Visual Studio für Mac können Sie ganz einfach containerisierte ASP.NET Core-Anwendungen erstellen, debuggen und ausführen und in Azure veröffentlichen.

## <a name="prerequisites"></a>Voraussetzungen

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio für Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Installation und Einrichtung

Lesen Sie für die Installation von Docker zunächst [Installieren von Docker Desktop für Mac](https://docs.docker.com/docker-for-mac/install/).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Erstellen einer ASP.NET Core-Webanwendung und Hinzufügen von Docker-Unterstützung

1. Erstellen Sie eine neue Projektmappe, indem Sie zu **Datei > Neue Projektmappe** wechseln.
1. Wählen Sie unter **.NET Core > App** die Vorlage **Webanwendung** aus: ![Erstellen einer neuen ASP.NET-Anwendung](media/docker-quickstart-1.png)
1. Wählen Sie das Zielframework aus. Bei diesem Beispiel verwenden wir .NET Core 2.2: ![Festlegen des Zielframeworks](media/docker-quickstart-2.png)
1. Geben Sie die Projektdetails ein, z.B. den Namen (_DockerDemo_ in diesem Beispiel). Das erstellte Projekt enthält alle Grundinformationen, die Sie für Aufbau und Betrieb einer ASP.NET Core-Website benötigen.
1. Klicken Sie im Projektmappenfenster mit der rechten Maustaste auf das Projekt „DockerDemo“ und dann mit der linken auf **Hinzufügen > Docker-Unterstützung hinzufügen**: ![Hinzufügen von Docker-Unterstützung](media/docker-quickstart-3.png)

Visual Studio für Mac fügt Ihrer Projektmappe automatisch ein neues Projekt namens **docker-compose** und dem bestehenden Projekt eine **Dockerfile** hinzu.

![Generierte Docker-Unterstützungsdateien](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Übersicht über die Dockerfile

Eine Dockerfile ist der wichtigste Bestandteil beim Erstellen eines endgültigen Docker-Images. Verweisen Sie auf einen [Dockerfile-Verweis](https://docs.docker.com/engine/reference/builder/), damit Sie einen Überblick über die darin enthaltenen Befehle erlangen.

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore DockerDemo/DockerDemo.csproj
COPY . .
WORKDIR /src/DockerDemo
RUN dotnet build DockerDemo.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish DockerDemo.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

Das obige *Dockerfile* basiert auf dem Image [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) und enthält Anweisungen zum Anpassen des Basisimages durch Erstellen Ihres Projekts und anschließendem Hinzufügen zum Container.

> [!NOTE]
> Die von Visual Studio für Mac erstellte standardmäßige Dockerfile macht Port 80 für HTTP-Datenverkehr verfügbar. Fügen Sie zum Ermöglichen von HTTPS-Datenverkehr `Expose 443` zur Dockerfile hinzu.

## <a name="debugging"></a>Debuggen

Legen Sie das Projekt `docker-compose` als Startprojekt fest, und starten Sie das Debuggen (**Ausführen > Debuggen starten**). Dadurch wird das ASP.NET-Projekt in einem Container erstellt, bereitgestellt und gestartet.

> [!TIP]
> Bei der ersten Ausführung nach der Installation von Docker Desktop erhalten Sie möglicherweise die folgende Fehlermeldung, wenn Sie das Debuggen versuchen: `Cannot start service dockerdemo: Mounts denied`
>
> Fügen Sie in Docker Desktop `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` der Registerkarte für die Dateifreigabe hinzu:
>
> ![Hinzufügen des Ordners „NuGetFallbackFolder“ zur Dateifreigabe](media/docker-quickstart-5.png)

Wenn der Build abgeschlossen ist, wird die Anwendung in Safari gestartet:

![In Safari ausgeführtes Docker-Standardprojekt](media/docker-quickstart-6.png)

Beachten Sie, dass der Container an einem Port lauscht, z.B. `http://localhost:32768`, der variieren kann.

Um die Liste der ausgeführten Container anzuzeigen, verwenden Sie im Terminal den Befehl `docker ps`.

Beachten Sie das Portrelay im folgenden Screenshot (unter **PORTS**). Dieser zeigt, dass der Container an dem Port lauscht, den wir in Safari oben kennengelernt haben, und Anforderungen an den internen Webserver an Port 80 (wie in der Dockerfile definiert) weiterleitet. Aus Sicht der Anwendung wird an Port 80 gelauscht:

![Liste der Docker-Container](media/docker-quickstart-7.png)
