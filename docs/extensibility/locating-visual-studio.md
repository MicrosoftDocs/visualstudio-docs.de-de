---
title: Suchen von Visual Studio | Microsoft-Dokumentation
description: Sie können mehrere Instanzen derselben Version von Visual Studio installieren. Erfahren Sie, wie Sie eine com-Abfrage-API verwenden, um die gewünschte Instanz zu suchen.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 175623723b8f7b59a644a439afd10246eab01c95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893593"
---
# <a name="locate-visual-studio"></a>Suchen nach Visual Studio

Ab Visual Studio 2017 können Sie mehrere Instanzen derselben Version oder sogar der Edition installieren. Dies ist hilfreich, wenn Sie eine Vorschau der neuen Funktionen auf Ihrem primären Entwicklungs Computer anzeigen möchten, während Sie Ihre vorherige Installation beibehalten. Aufgrund dieser Änderungen gibt es keine einzelne Umgebungsvariable oder keinen Registrierungs Wert, den Sie verwenden können, um eine Instanz zu suchen. Stattdessen können Sie eine com- [Abfrage-API](/dotnet/api/microsoft.visualstudio.setup.configuration) verwenden, um nach den für Ihre Erweiterung relevanten Kriterien nach Instanzen zu suchen.

Dies ist eine schnelle, schreibgeschützte API mit nuget-Paketen, die für nativen und verwalteten Code verfügbar sind.

| Code | Paket |
| ---- | --- |
| Systemeigenes Format | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Verwaltet | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Sie können eine einzelne Instanz finden, wenn Sie einen Pfad oder den aktuellen Prozess erhalten, oder alle Instanzen auflisten. In [unseren Beispielen](https://github.com/Microsoft/vs-setup-samples) finden Sie umfassende Beispiele zum Auffinden von Visual Studio.

## <a name="tools"></a>Tools

Um Visual Studio und andere Tools in Buildumgebungen, PowerShell-Skripts, Installer und weiteren Szenarien zu finden, gibt es eine Reihe von Open Source-Tools, die Sie direkt und mit ihren eigenen Skripts weiterverteilen können.

| Projekt | Beschreibung |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Native ausführbare Datei mit einer einzelnen Datei zum Auffinden von Instanzen, die Kriterien erfüllen, z. b. Release oder vorab Release, das installierte Produkt und die installierten Workloads. Unterstützt auch das Auffinden von Visual Studio 2010 und neueren, obwohl weniger Informationen für Visual Studio 2017 und höher zurückgegeben werden. Beispiele finden Sie im [wiki](https://github.com/Microsoft/vswhere/wiki) . |
| [Vssetup-Cmdlets](https://github.com/Microsoft/vssetup.powershell) | PowerShell-Cmdlets unterstützten 2,0 und höher, die umfangreiche Informationen als Objekte zurückgeben, die Sie verwenden können, um nach Instanzen zu suchen, die auf denselben Kriterien wie _vswhere_ basieren, und um noch mehr Eigenschaften zu Instanzen zu ermitteln Beispiele finden Sie im [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) . |
| [Vsixbootstrapper](https://github.com/Microsoft/vsixbootstrapper) | _Vsixinstaller_ wird von automatisch lokalisiert, und die Befehlszeile wird durchlaufen, um eine **. vsix* -Datei zu installieren. Diese Funktion kann in Installationsprogrammen nützlich sein, die keine direkte Unterstützung für die Abfrage-APIs haben. Beispiele finden Sie im [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) . |

## <a name="see-also"></a>Weitere Informationen

* [Änderungen am Setup von Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Starten von Visual Studio mit DTE](launch-visual-studio-dte.md)