---
title: Bekannte Probleme bei Containern
description: Informationen zu bekannten Problemen, die bei der Installation von Visual Studio Build Tools in einem Windows-Container auftreten können.
ms.date: 02/18/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 338d7a19bf613ee2b2432fba6b635cf0c46eb008
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868646"
---
# <a name="known-issues-for-containers"></a>Bekannte Probleme bei Containern

Es gibt einige Probleme bei der Installation von Visual Studio in einem Docker-Container.

## <a name="windows-container"></a>Windows-Container

Die folgenden bekannten Probleme treten auf, wenn Sie Visual Studio Build Tools in einem Windows-Container installieren.

::: moniker range="vs-2017"

* Sie können Visual Studio nicht in einem Container basierend auf dem Image microsoft/windowsservercore:10.0.14393.1593 installieren. Images mit Windows-Versionen vor oder nach Version 10.0.14393 sollten funktionieren.

* Sie können Version 10.0.14393 des Windows SDK sowie frühere Versionen nicht installieren. Einige Pakete können nicht installiert werden, und Workloads, die von diesen Paketen abhängig sind, funktionieren nicht.

::: moniker-end

* Übergeben Sie `-m 2GB` (oder mehr), wenn Sie das Image erstellen. Einige Workloads erfordern bei der Installation mehr Arbeitsspeicher als die standardmäßigen 1 GB.
* Sie müssen Docker konfigurieren, damit Sie Datenträger verwenden können, die größer als die standardmäßig festgelegten 20 GB sind.
* Übergeben Sie `--norestart` auf der Befehlszeile. Beim Versuch, einen Windows-Container von innerhalb des Container neu zu starten, wird `ERROR_TOO_MANY_OPEN_FILES` an den Host zurückgegeben (Stand: Veröffentlichung dieses Artikels).
* Wenn Sie Ihr Image direkt auf der Grundlage von microsoft/windowsservercore erstellen, wird .NET Framework möglicherweise nicht ordnungsgemäß installiert, ohne dass ein Installationsfehler ausgegeben wird. Es kann sein, dass verwalteter Code nach Abschluss der Installation nicht ausgeführt wird. Erstellen Sie Ihr Image stattdessen auf der Grundlage von [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) oder höher. Beispielsweise kann beim Erstellen mit MSBuild ein Fehler angezeigt werden, der dem folgenden ähnelt:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): error MSB6003: The specified task executable "csc.exe" could not be run. Could not load file or assembly 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies. (Fehler MSB6003: Die angegebene ausführbare Datei des Tasks (csc.exe) konnte nicht ausgeführt werden. Die Datei oder Assembly 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a', oder eine Abhängigkeit davon, wurde nicht gefunden.) Die angegebene Datei wurde nicht gefunden.“

::: moniker range="vs-2017"

* Sie können Version 15.8 und frühere Versionen von Visual Studio 2017 (alle Produkte) auf mcr.microsoft.com/windows/servercore:1809 und höher nicht installieren. Weitere Informationen finden Sie unter https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Build Tools-Container

Die folgenden bekannten Probleme treten möglicherweise auf, wenn Sie einen Build Tools-Container verwenden. Um festzustellen, ob Probleme behoben wurden oder ob es andere bekannte Probleme gibt, besuchen Sie die [Entwicklercommunity](https://aka.ms/feedback/suggest?space=8).

* IntelliTrace funktioniert [in einigen Szenarios](https://github.com/Microsoft/vstest/issues/940) innerhalb eines Containers möglicherweise nicht.
* In älteren Versionen von Docker für Windows beträgt die Standardgröße für Containerimages nur 20 GB und bietet nicht genügend Platz für Build Tools. [Hier finden Sie Anweisungen zum Ändern der Imagegröße](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) auf 127 GB oder mehr.
Sehen Sie sich die Protokolldateien an, um bestätigen zu können, ob ein Speicherplatzproblem vorliegt. Wenn der Speicherplatz ausgeht, enthält Ihre `vslogs\dd_setup_<timestamp>_errors.log`-Datei Folgendes: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Weitere Informationen

* [Installieren von Build-Tools in einen Container](build-tools-container.md)
* [Erweitertes Beispiel für Container](advanced-build-tools-container.md)
* [Workload- und Komponenten-IDs in Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
