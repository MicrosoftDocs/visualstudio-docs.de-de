---
title: MSBuild-API | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e87ee95c4027d0513c78d3ce0386cf31d47baf94
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862678"
---
# <a name="use-the-msbuild-api"></a>Verwenden der MSBuild-API

MSBuild bietet eine öffentliche API-Oberfläche, mit der Ihr Programm Builds ausführen und Projekte überprüfen kann. Aktuelle Versionen der MSBuild-APIs finden Sie in den folgenden NuGet-Paketen:

| Paketname | Beschreibung |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | Dieses Paket enthält die Microsoft.Build-Assembly, die zum Erstellen, Bearbeiten und Auswerten von MSBuild-Projekten verwendet wird.|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Dieses Paket enthält die Assembly für das allgemeine MSBuild-Framework, das von anderen MSBuild-Assemblys verwendet wird. |
| [Microsoft.Build.Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | Dieses Paket stellt eine vollständige, ausführbare Kopie von MSBuild bereit. Verweisen Sie nur auf dieses Paket, wenn Ihre Anwendung Projekte laden oder prozessinterne Builds ausführen muss, ohne eine Installation von MSBuild zu erfordern. Für die erfolgreiche Auswertung von Projekten mithilfe dieses Pakets müssen zusätzliche Komponenten (z. B. die Compiler) in ein Anwendungsverzeichnis aggregieren. |
| [Microsoft.Build.Tasks.Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | Dieses Paket enthält die Microsoft.Build.Tasks-Assembly, die die häufig verwendeten Tasks von MSBuild implementiert. |
| [Microsoft.Build.Utilities.Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Dieses Paket enthält die Microsoft.Build.Utilities-Assembly, die zum Implementieren benutzerdefinierter MSBuild-Tasks verwendet wird. |

Darüber hinaus hostet NuGet die Legacy-Assembly [Microsoft.Build.Engine](https://www.nuget.org/packages/Microsoft.Build.Engine), die veraltet ist.

Es gibt verschiedene Versionen der MSBuild-API, und für die Versionen 15 und 16 gibt es zwei unterschiedliche Arten von Assemblys in den NuGet-Paketen. Eine von diesem wurde mit .NET Framework und die andere mit .NET Core (eine Teilmenge der .NET Framework-API) kompiliert.  Die .NET Core-Version von MSBuild wird verwendet, wenn Sie den `dotnet`-Befehl aufrufen und wenn MSBuild auf Mac- und Linux-Systemen verwendet wird.

Die Dokumentation zur MSBuild-API finden Sie mithilfe des [.NET-API-Browsers](/dotnet/api), oder indem Sie die Namespaces in der folgenden Liste durchsuchen.

::: moniker range="vs-2017"
| Namespace | Gilt für | Beschreibung |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | Alle |  Dieser Namespace enthält Typen, die das MSBuild-Objektmodell verwendet, um Projektverzeichnisse mit nicht ausgewerteten Werten zu erstellen. Alle Projektverzeichnisse entsprechen einem Projekt oder einer Zieledatei. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält die `ProjectOptions`-Klasse, die die Projektkonstruktion unterstützt. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die das MSBuild-Objektmodell zum Auswerten von Projekten verwendet. Alle Projekte sind mindestens einem Projektverzeichnis zugeordnet. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält die `EvaluationContext`-Klasse, die zum Speichern des Auswertungsstatus zwischen Aufrufen verwendet wird. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Ausnahmetypen, die während des Buildprozesses ausgelöst werden können. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die das MSBuild-Objektmodell zum Erstellen von Projekten verwendet. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält die Typen, die die Interaktion von Tasks und Protokollierungen mit der MSBuild-Engine definieren.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält die Typen, die die Leistungsprofilerstellung unterstützen. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | Nur für .NET Framework | Dieser Namespace enthält die Klassen, die zum Darstellen der XAML-Typen verwendet werden, die aus Dateien, Regeln und anderen Quellen gelesen werden. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Klassen, die die Verarbeitung von Platzhaltern unterstützen. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die Erweiterungen für die Verarbeitung von Platzhaltern unterstützen. |
| [Microsoft.Build.Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die die MSBuild-Option `-graph` unterstützen. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die für die Protokollierung des Fortschritts eines Buildprozesses verwendet werden. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die das Remoting in MSBuild unterstützen. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält die Implementierung aller Tasks, die mit MSBuild bereitgestellt werden. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | Nur für .NET Framework | Dieser Namespace enthält Klassen, die intern von MSBuild verwendet werden. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | Nur für .NET Framework | Dieser Namespace enthält Klassen, die von MSBuild verwendet werden.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Klassen, die intern von MSBuild verwendet werden. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | Nur für .NET Framework | Dieser Namespace enthält Klassen, die sich auf XAML-Buildtasks beziehen. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | Alle | Dieser Namespace enthält Hilfsklassen, die Sie verwenden können, um Ihre eigenen MSBuild-Protokollierungen und -Tasks zu erstellen.|
:::moniker-end
:::moniker range=">=vs-2019"
| Namespace | Gilt für | Beschreibung |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | Alle |  Dieser Namespace enthält Typen, die das MSBuild-Objektmodell verwendet, um Projektverzeichnisse mit nicht ausgewerteten Werten zu erstellen. Alle Projektverzeichnisse entsprechen einem Projekt oder einer Zieledatei. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält die `ProjectOptions`-Klasse, die die Projektkonstruktion unterstützt. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die das MSBuild-Objektmodell zum Auswerten von Projekten verwendet. Alle Projekte sind mindestens einem Projektverzeichnis zugeordnet. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält die `EvaluationContext`-Klasse, die zum Speichern des Auswertungsstatus zwischen Aufrufen verwendet wird. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Ausnahmetypen, die während des Buildprozesses ausgelöst werden können. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die das MSBuild-Objektmodell zum Erstellen von Projekten verwendet. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält die Typen, die die Interaktion von Tasks und Protokollierungen mit der MSBuild-Engine definieren.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält die Typen, die die Leistungsprofilerstellung unterstützen. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | Nur für .NET Framework | Dieser Namespace enthält die Klassen, die zum Darstellen der XAML-Typen verwendet werden, die aus Dateien, Regeln und anderen Quellen gelesen werden. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Klassen, die die Verarbeitung von Platzhaltern unterstützen. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die Erweiterungen für die Verarbeitung von Platzhaltern unterstützen. |
| [Microsoft.Build.Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die die MSBuild-Option `-graph` unterstützen. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die für die Protokollierung des Fortschritts eines Buildprozesses verwendet werden. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Typen, die das Remoting in MSBuild unterstützen. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält die Implementierung aller Tasks, die mit MSBuild bereitgestellt werden. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | Nur für .NET Framework | Dieser Namespace enthält Klassen, die intern von MSBuild verwendet werden. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | Nur für .NET Framework | Dieser Namespace enthält Klassen, die von MSBuild verwendet werden.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Klassen, die intern von MSBuild verwendet werden. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | Nur für .NET Framework | Dieser Namespace enthält Klassen, die sich auf XAML-Buildtasks beziehen. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | Alle | Dieser Namespace enthält Hilfsklassen, die Sie verwenden können, um Ihre eigenen MSBuild-Protokollierungen und -Tasks zu erstellen.|
:::moniker-end

In der obigen Tabelle bedeutet „Alle“ in der Spalte „Gilt für“, dass die Typen im Namespace sowohl in der .NET Framework-Version als auch in der .NET Core-Version der MSBuild-API verfügbar sind.
