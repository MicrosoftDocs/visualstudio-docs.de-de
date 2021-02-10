---
title: Erweitertes Beispiel für Container
description: Hier erfahren Sie mehr über ein erweitertes Beispiel für Docker-Container. Die Docker-Beispieldatei verwendet ein spezifisches Versionstag des microsoft/dotnet-framework-Images.
ms.custom: SEO-VS-2020
ms.date: 03/25/2020
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d8b2148dced2d08d04c73091375f91ab37732274
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868730"
---
# <a name="advanced-example-for-containers"></a>Erweitertes Beispiel für Container

::: moniker range="vs-2017"

Das Beispiel-Dockerfile unter [Installieren von Build Tools in einem Container](build-tools-container.md) verwendet immer das [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework)-Image, das auf dem aktuellen microsoft/windowsservercore-Image und dem aktuellen Visual Studio Build Tools-Installer basiert. Wenn Sie dieses Image in einer [Docker-Registrierung](https://azure.microsoft.com/services/container-registry) veröffentlichen, sodass andere dieses herunterladen können, kann das Image für viele Szenarios geeignet sein. In der Praxis ist es allerdings üblich, ein spezifisches Basisimage zu verwenden, spezifische Binärdateien herunterzuladen und spezifische Tools zu installieren.

::: moniker-end

::: moniker range="vs-2019"

Das Beispiel-Dockerfile unter [Installieren von Build Tools in einem Container](build-tools-container.md) verwendet immer das [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework)-Image, das auf dem aktuellen microsoft/windowsservercore-Image und dem aktuellen Visual Studio Build Tools-Installer basiert. Wenn Sie dieses Image in einer [Docker-Registrierung](https://azure.microsoft.com/services/container-registry) veröffentlichen, sodass andere dieses herunterladen können, kann das Image für viele Szenarios geeignet sein. In der Praxis ist es allerdings üblich, ein spezifisches Basisimage zu verwenden, spezifische Binärdateien herunterzuladen und spezifische Tools zu installieren.

::: moniker-end

Die folgende Docker-Beispieldatei verwendet ein spezifisches Versionstag des microsoft/dotnet-framework-Images. Das Verwenden eines spezifischen Tags für ein Basisimage ist üblich und erleichtert es, daran zu denken, dass das Erstellen und Neuerstellen von Images immer die gleiche Grundlage hat.

> [!NOTE]
> Sie können Visual Studio nicht in microsoft/windowsservercore:10.0.14393.1593 oder in einem auf microsoft/windowsservercore:10.0.14393.1593 basierenden Image installieren, da dort bekannte Probleme beim Starten des Installers in einem Container entstehen können. Weitere Informationen finden Sie unter [Bekannte Probleme bei Containern](build-tools-container-issues.md).

Über das folgende Beispiel wird das neueste Build Tools-Release heruntergeladen. Wenn Sie eine ältere Build Tools-Version verwenden möchten, die Sie zu einem späteren Zeitpunkt in einem Container installieren können, müssen Sie zuerst ein Layout [erstellen](create-an-offline-installation-of-visual-studio.md) und [verwalten](update-a-network-installation-of-visual-studio.md).

## <a name="install-script"></a>Installieren eines Skripts

Um beim Auftreten von Installationsfehlern Protokolle zu erfassen, erstellen Sie ein Batchskript mit dem Namen „Install.cmd“ im Arbeitsverzeichnis mit folgendem Inhalt:

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Docker-Datei

Erstellen Sie im Arbeitsverzeichnis die Docker-Datei mit dem folgenden Inhalt:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image.
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/runtime:4.8
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Visual Studio 2017 Version 15.8 und früher (alle Produkte) werden unter mcr\.microsoft\.com\/windows\/servercore:1809 oder höher nicht ordnungsgemäß installiert. Es wird keine Fehlermeldung angezeigt.
   >
   > Weitere Informationen finden Sie unten unter [Bekannte Probleme bei Containern](build-tools-container-issues.md).

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

Führen Sie den folgenden Befehl aus, um das Image im aktuellen Arbeitsverzeichnis zu erstellen:

::: moniker range="vs-2017"

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

::: moniker-end

::: moniker range="vs-2019"

```shell
docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
```

::: moniker-end

Sie können entweder eins der Argumente `FROM_IMAGE` und `CHANNEL_URL` oder beide Argumente gleichzeitig übergeben, indem Sie die Befehlszeilenoption `--build-arg` verwenden, um ein anderes Basisimage oder den Speicherort des internen Layouts anzugeben, wenn Sie ein bestimmtes Image verwalten möchten.

   > [!TIP]
   > Eine Liste der Workloads und Komponenten finden Sie unter [Visual Studio Build Tools: Komponentenverzeichnis](workload-component-id-vs-build-tools.md).
   >

## <a name="diagnosing-install-failures"></a>Analysieren von Fehlern bei der Installation

Dieses Beispiel lädt spezifische Tools herunter und überprüft, dass die Hashwerte übereinstimmen. Es lädt ebenfalls die aktuellen Visual Studio- und .NET-Hilfsprogramme für die Protokollsammlung herunter, sodass Sie diese im Fall einer fehlgeschlagenen Installation auf Ihren Hostcomputer kopieren können, um den Fehler zu analysieren.

::: moniker range="vs-2017"

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range="vs-2019"

```shell
> docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

Nachdem die Ausführung der letzten Zeile abgeschlossen ist, öffnen Sie „%TEMP%\vslogs.zip“ auf Ihrem Computer, oder melden Sie ein Problem auf der Website der [Entwicklercommunity](https://aka.ms/feedback/suggest?space=8).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Build Tools in einem Container](build-tools-container.md)
* [Bekannte Probleme für Container](build-tools-container-issues.md)
* [Workload- und Komponenten-IDs in Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
