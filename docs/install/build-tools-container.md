---
title: Installieren von Visual Studio Build Tools in einem Container
titleSuffix: ''
description: Erfahren Sie, wie Sie Visual Studio Build Tools in einem Windows-Container installieren können, um CI/CD-Workflows (Continuous Integration und Continuous Delivery) zu unterstützen.
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fd584a977900de83af454f26722d3e4ba2bd8ac8
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847662"
---
# <a name="install-build-tools-into-a-container"></a>Installieren von Build Tools in einem Container

Sie können Visual Studio Build Tools in einem Windows-Container installieren, um CI/CD-Workflows (Continuous Integration und Continuous Delivery) zu unterstützen. In diesem Artikel erfahren Sie, welche Docker-Konfigurationsänderungen erforderlich sind, sowie welche [Workloads und Komponenten](workload-component-id-vs-build-tools.md) Sie in einem Container installieren können.

[Container](https://www.docker.com/what-container) stellen eine hervorragende Möglichkeit dar, aus einem konsistenten Buildsystem ein Paket zu erstellen, welches Sie nicht nur in einer CI/CD-Serverumgebung, sondern auch in Entwicklungsumgebungen nutzen können. Sie können z.B. Ihren Quellcode in einen Container einbinden, der von einer benutzerdefinierten Umgebung erstellt werden soll, und parallel Visual Studio oder andere Tools verwenden, um Code zu schreiben. Wenn Ihr CI/CD-Workflow das gleiche Containerimage verwendet, können Sie sicher sein, dass Ihr Code konsistent erstellt wird. Sie können Container auch zum Erreichen von Runtime-Konsistenz verwenden, was bei Microservices üblich ist, die mithilfe eines Orchestrierungssystems mehrere Container nutzen. Dieser Aspekt wird in diesem Artikel jedoch nicht behandelt.

Wenn Sie Ihren Quellcode mithilfe von Visual Studio Build Tools nicht erstellen können, können Sie die gleichen Schritte auch auf andere Visual Studio-Produkte anwenden. Beachten Sie allerdings, dass Windows-Container keine interaktiven Benutzeroberflächen unterstützen und daher alle Befehle automatisiert werden müssen.

## <a name="before-you-begin"></a>Vorbereitungen

Für dieses Thema wird davon ausgegangen, dass Sie zu einem gewissen Grad mit [Docker](https://www.docker.com/what-docker) vertraut sind. Wenn Sie noch nicht mit der Ausführung von Docker unter Windows vertraut sind, informieren Sie sich über das [Installieren und Konfigurieren der Docker-Engine unter Windows](/virtualization/windowscontainers/manage-docker/configure-docker-daemon).

Das folgende Basisimage ist ein Beispiel und funktioniert für Ihr System möglicherweise nicht. Lesen Sie den Artikel [Kompatibilität von Windows-Containerversionen](/virtualization/windowscontainers/deploy-containers/version-compatibility), um zu ermitteln, welches Basisimage Sie für Ihre Umgebung verwenden sollten.

## <a name="create-and-build-the-dockerfile"></a>Erstellen und Kompilieren der Dockerfile-Datei

Speichern Sie die folgende Dockerfile-Beispieldatei in einer neuen Datei auf Ihrem Datenträger. Wenn Sie die Datei einfach „Dockerfile“ nennen, wird sie standardmäßig erkannt.

> [!WARNING]
> Diese Dockerfile-Beispieldatei kann lediglich bei älteren Windows SDKs nicht verwendet werden, die nicht in Containern installiert werden können. Bei älteren Releases schlägt der Buildbefehl fehl.

1. Öffnen Sie eine Eingabeaufforderung.

1. Erstellen Sie ein neues Verzeichnis (empfohlen):

   ```shell
   mkdir C:\BuildTools
   ```

1. Ändern Sie die Verzeichnisse auf dieses neue Verzeichnis:

   ```shell
   cd C:\BuildTools
   ```

1. Speichern Sie den folgenden Inhalt unter C:\BuildTools\Dockerfile.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN start /wait C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Eine Liste der Workloads und Komponenten finden Sie unter [Visual Studio Build Tools: Komponentenverzeichnis](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Wenn Sie Ihr Image direkt auf der Grundlage von microsoft/windowsservercore oder mcr.microsoft.com/windows/servercore – siehe [Microsoft syndicates container catalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/) (Microsoft veröffentlicht Containerkatalog) – erstellen, wird .NET Framework möglicherweise nicht ordnungsgemäß installiert, ohne dass ein Installationsfehler ausgegeben wird. Es kann sein, dass verwalteter Code nach Abschluss der Installation nicht ausgeführt wird. Erstellen Sie Ihr Image stattdessen auf der Grundlage von [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) oder höher. Beachten Sie außerdem, dass Images der Version 4.7.2 oder höher möglicherweise PowerShell als Standard-`SHELL` verwenden, wodurch die Anweisungen `RUN` und `ENTRYPOINT` nicht ausgeführt werden können.
   >
   > Visual Studio 2017 Version 15.8 und früher (alle Produkte) werden unter „mcr.microsoft.com/windows/servercore:1809“ oder höher nicht ordnungsgemäß installiert. Es wird keine Fehlermeldung angezeigt.
   >
   > Informationen dazu,welche Containerbetriebssystemversionen auf welchen Hostbetriebssystemversionen unterstützt werden, finden Sie unter [Kompatibilität der Windows-Containerversionen](/virtualization/windowscontainers/deploy-containers/version-compatibility). Informationen zu bekannten Problemen finden Sie unter [Bekannte Probleme bei Containern](build-tools-container-issues.md).
   
   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Eine Liste der Workloads und Komponenten finden Sie unter [Visual Studio Build Tools: Komponentenverzeichnis](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Wenn Sie Ihr Image direkt auf der Grundlage von microsoft/windowsservercore erstellen, wird .NET Framework möglicherweise nicht ordnungsgemäß installiert, ohne dass ein Installationsfehler ausgegeben wird. Es kann sein, dass verwalteter Code nach Abschluss der Installation nicht ausgeführt wird. Erstellen Sie Ihr Image stattdessen auf der Grundlage von [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) oder höher. Beachten Sie außerdem, dass Images der Version 4.8 oder höher möglicherweise PowerShell als Standard-`SHELL` verwenden, wodurch die Anweisungen `RUN` und `ENTRYPOINT` nicht ausgeführt werden können.
   >
   > Informationen dazu,welche Containerbetriebssystemversionen auf welchen Hostbetriebssystemversionen unterstützt werden, finden Sie unter [Kompatibilität der Windows-Containerversionen](/virtualization/windowscontainers/deploy-containers/version-compatibility). Informationen zu bekannten Problemen finden Sie unter [Bekannte Probleme bei Containern](build-tools-container-issues.md).

   ::: moniker-end
   
   > [!NOTE]
   > Der Fehlercode `3010` wird verwendet, um den Erfolg eines erforderlichen Neustarts anzuzeigen. Weitere Informationen finden Sie unter [MsiExec.exe-Fehlermeldungen](/windows/win32/msi/error-codes).

1. Führen Sie den folgenden Befehl innerhalb jenes Verzeichnisses aus.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Dieser Befehl erstellt die Dockerfile-Datei im aktuellen Verzeichnis. Dies erfordert 2 GB an Arbeitsspeicher. Standardmäßig steht dafür 1 GB zur Verfügung. Dies ist jedoch zum Installieren einiger Workloads nicht ausreichend. Abhängig von Ihren Buildanforderungen reicht dies möglicherweise dennoch aus.

   Das endgültige Image trägt die Markierung „buildtools2017:latest“, sodass Sie es problemlos als „buildtools2017“ in einem Container ausführen können, da das Tag „latest“ standardmäßig verwendet wird, wenn kein Tag angegeben wurde. Wenn Sie eine bestimmte Version von Visual Studio Build Tools 2017 in einem [komplexeren Szenario](advanced-build-tools-container.md) verwenden möchten, können Sie den Container stattdessen mit einer bestimmten Visual Studio-Buildnummer sowie dem Tag „latest“ markieren, damit die Container eine bestimmte Version konsistent verwenden.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Dieser Befehl erstellt die Dockerfile-Datei im aktuellen Verzeichnis. Dies erfordert 2 GB an Arbeitsspeicher. Standardmäßig steht dafür 1 GB zur Verfügung. Dies ist jedoch zum Installieren einiger Workloads nicht ausreichend. Abhängig von Ihren Buildanforderungen reicht dies möglicherweise dennoch aus.

   Das endgültige Image trägt die Markierung „buildtools2019:latest“, sodass Sie es problemlos als „buildtools2019“ in einem Container ausführen können, da das Tag „latest“ standardmäßig verwendet wird, wenn kein Tag angegeben wurde. Wenn Sie eine bestimmte Version von Visual Studio Build Tools 2019 in einem [komplexeren Szenario](advanced-build-tools-container.md) verwenden möchten, können Sie den Container stattdessen mit einer bestimmten Visual Studio-Buildnummer sowie dem Tag „latest“ markieren, damit die Container eine bestimmte Version konsistent verwenden.

   ::: moniker-end

## <a name="using-the-built-image"></a>Verwenden des erstellten Images

Da Sie bereits ein Image erstellt haben, können Sie dieses nun in einem Container ausführen, um sowohl interaktive, als auch automatisierte Builds abzudecken. Im Beispiel wird die Developer-Eingabeaufforderung verwendet, damit Ihre PATH-Variable und andere Umgebungsvariablen bereits konfiguriert sind.

1. Öffnen Sie eine Eingabeaufforderung.

1. Führen Sie den Container aus, um eine PowerShell-Umgebung zu starten, in der alle Entwicklerumgebungsvariablen festgelegt sind:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Wenn Sie dieses Image für Ihren CI/CD-Workflow verwenden möchten, können Sie es in Ihrer eigenen [Azure Container Registry](https://azure.microsoft.com/services/container-registry) oder in einer anderen internen [Docker-Registrierung](https://docs.docker.com/registry/deploying) veröffentlichen, damit die Server es nur abrufen müssen.

   > [!NOTE]
   > Wenn der Docker-Container nicht gestartet werden kann, liegt vermutlich ein Visual Studio-Installationsproblem vor. Sie können das Dockerfile aktualisieren, um den Schritt zu entfernen, der den Visual Studio-Batchbefehl aufruft. Dadurch können Sie den Docker-Container starten und die Installationsfehlerprotokolle lesen.
   >
   > Entfernen Sie die Parameter `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` und `&&` aus dem Befehl `ENTRYPOINT` in Ihrer Dockerfile-Datei. Der Befehl sollte nun wie folgt lauten: `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]`. Erstellen Sie das Dockerfile dann neu, und führen Sie den Befehl `run` aus, um auf die Containerdateien zuzugreifen. Navigieren Sie zum Verzeichnis `$env:TEMP`, und suchen Sie die Datei `dd_setup_<timestamp>_errors.log`, um die Installationsfehlerprotokolle zu finden.
   >
   > Nachdem Sie das Installationsproblem identifiziert und behoben haben, können Sie die Parameter `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` und `&&` wieder zum Befehl `ENTRYPOINT` hinzufügen und Ihr Dockerfile neu erstellen.
   >
   > Weitere Informationen finden Sie unter [Bekannte Probleme bei Containern](build-tools-container-issues.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Erweitertes Beispiel für Container](advanced-build-tools-container.md)
* [Bekannte Probleme für Container](build-tools-container-issues.md)
* [Workload- und Komponenten-IDs in Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
