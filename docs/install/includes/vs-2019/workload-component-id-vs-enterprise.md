---
title: Workload- und Komponenten-IDs in Visual Studio Enterprise 2019
titleSuffix: ''
description: Verwenden Sie Arbeitsauslastungs- und Komponenten-IDs, um Visual Studio über die Befehlszeile zu installieren oder um sie als Abhängigkeit in einem VSIX-Manifest anzugeben
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 11/10/2020
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: cecadf43e7f54f5ad0954acfc725f5e48a2a69cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881839"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Visual Studio-Kern-Editor (in Visual Studio Enterprise 2019 enthalten)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Beschreibung:** Die Shell-Kernbenutzeroberfläche von Visual Studio, die syntaxfähige Codebearbeitung, Quellcodeverwaltung und Arbeitselementverwaltung bereitstellt.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio-Kern-Editor | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Visual Studio-Startseite für C++-Benutzer | 16.0.28315.86 | Optional

## <a name="azure-development"></a>Azure-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Azure

**Beschreibung:** Azure-Tools und -Projekte sowie zugehörige SDKs zur Entwicklung von Cloud-Apps und zur Erstellung von Ressourcen mithilfe von .NET Core und .NET Framework. Enthalten sind auch Tools zur Erstellung von Containeranwendungen und zur Unterstützung von Docker.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Erforderlich
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs-Tools | 16.0.28714.129 | Erforderlich
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Erforderlich
Microsoft.ComponentGroup.ClickOnce.Publish | ClickOnce-Veröffentlichung für .NET Core | 16.8.30622.256 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Erforderlich
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Erforderlich
Microsoft.NetCore.Component.DevelopmentTools | .NET Core-Entwicklungstools | 16.8.30607.99 | Erforderlich
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1-Runtime (LTS) | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0-Runtime | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.SDK | .NET SDK | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Web | .NET Core-Entwicklungstools | 16.5.29721.120 | Erforderlich
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.4.29313.120 | Erforderlich
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#-Sprachunterstützung für Webprojekte | 16.3.29207.166 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.3.29207.166 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.4.0 | TypeScript 4.0 SDK | 16.0.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Erforderliche Komponenten für die Azure-Entwicklung | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs-Tools | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Erforderlich
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake und Stream Analytics-Tools | 16.8.30509.167 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Empfohlen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Runtime (LTS) | 16.8.30703.189 | Empfohlen
Microsoft.VisualStudio.Component.AspNet45 | Erweiterte ASP.NET-Features | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio-Tools für Kubernetes | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Powershell | Azure PowerShell | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager-Kerntools | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric-Tools | 16.4.29313.120 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services-Buildtools | 16.3.29207.166 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Momentaufnahmedebugger | 16.5.29813.82 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Time Travel Debugger | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services-Tools | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager-Tools | 16.0.28528.71 | Empfohlen
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.8.TargetingPack | Paket zur Festlegung von Zielversionen für .NET Framework 4.8 | 16.4.29313.120 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8-Entwicklungstools | 16.4.29318.151 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional

## <a name="data-storage-and-processing"></a>Datenspeicherung und -verarbeitung

**ID:** Microsoft.VisualStudio.Workload.Data

**Beschreibung:** Hiermit werden Datenlösungen mit SQL Server, Azure Data Lake oder Hadoop verbunden, entwickelt und getestet.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Empfohlen
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Empfohlen
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake und Stream Analytics-Tools | 16.8.30509.167 | Empfohlen
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Empfohlen
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Empfohlen
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Empfohlen
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1-Runtime (LTS) | 16.8.30703.189 | Empfohlen
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0-Runtime | 16.8.30703.189 | Empfohlen
Microsoft.NetCore.Component.SDK | .NET SDK | 16.8.30703.189 | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.4.29313.120 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services-Buildtools | 16.3.29207.166 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.4.29318.151 | Empfohlen
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.3.29207.166 | Empfohlen
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.4.0 | TypeScript 4.0 SDK | 16.0.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.4.29318.151 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Empfohlen
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#-Desktopsprachunterstützung | 16.0.28315.86 | Optional

## <a name="data-science-and-analytical-applications"></a>Data Science und analytische Anwendungen

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Beschreibung:** Sprachen und Tools zum Erstellen von Data Science-Anwendungen (einschließlich Python und F#).

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.PythonTools | Unterstützung der Sprache Python | 16.5.29515.121 | Empfohlen
Microsoft.Component.PythonTools.Minicondax64 | Python-Miniconda | 16.2.29003.222 | Empfohlen
Microsoft.Component.PythonTools.Web | Webunterstützung für Python | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.Component.FSharp.Desktop | F#-Desktopsprachunterstützung | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Empfohlen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.4.0 | TypeScript 4.0 SDK | 16.0.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Empfohlen
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Native Python-Entwicklungstools | 16.8.30607.99 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 16.5.29515.121 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.28) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Optional

## <a name="net-desktop-development"></a>.NET-Desktopentwicklung

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Beschreibung:** Hiermit werden WPF-, Windows Forms- und Konsolenanwendungen mithilfe von C#, Visual Basic und F# mit .NET Core und .NET Framework erstellt.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Erforderlich
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Erforderlich
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1-Runtime (LTS) | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0-Runtime | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.SDK | .NET SDK | 16.8.30703.189 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET-Desktopentwicklungstools | 16.8.30607.99 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.2876 | Empfohlen
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Empfohlen
Microsoft.ComponentGroup.ClickOnce.Publish | ClickOnce-Veröffentlichung für .NET Core | 16.8.30622.256 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Empfohlen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Runtime (LTS) | 16.8.30703.189 | Empfohlen
Microsoft.NetCore.Component.DevelopmentTools | .NET Core-Entwicklungstools | 16.8.30607.99 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time-Debugger | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.DotNetModelBuilder | ML.NET-Modell-Generator (Vorschau) | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6-Tools | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Empfohlen
Component.Dotfuscator | PreEmptive Protection – Dotfuscator | 16.0.28528.71 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.8.TargetingPack | Paket zur Festlegung von Zielversionen für .NET Framework 4.8 | 16.4.29313.120 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8-Entwicklungstools | 16.4.29318.151 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 16.0.28528.71 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 16.4.29409.204 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.4.29409.204 | Optional
Microsoft.VisualStudio.Component.FSharp.Desktop | F#-Desktopsprachunterstützung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.PortableLibrary | Paket zur Festlegung von Zielversionen für die portable .NET-Bibliothek | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.TypeScript.4.0 | TypeScript 4.0 SDK | 16.0.30509.167 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 16.5.29514.35 | Optional
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | MSIX Packaging Tools | 16.8.30607.99 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.4.29318.151 | Optional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Optional

## <a name="game-development-with-unity"></a>Spieleentwicklung mit Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Beschreibung:** Erstellen Sie 2D- und 3D-Spiele mit Unity, einer leistungsfähigen plattformübergreifenden Entwicklungsumgebung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5-Entwicklungstools | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools für Unity | 16.0.28315.86 | Erforderlich
Component.UnityEngine.x64 | Unity Hub | 16.8.30509.167 | Empfohlen
Component.UnityEngine.x86 | Unity 5.6-Editor (32 Bit) | 16.1.28811.260 | Empfohlen

## <a name="linux-development-with-c"></a>Linux-Entwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Beschreibung:** Erstellen und debuggen Sie Anwendungen, die in einer Linux-Umgebung ausgeführt werden.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.MDD.Linux | C++ für die Linux-Entwicklung | 16.5.29515.121 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.8.30509.167 | Erforderlich
Component.Linux.CMake | C++-CMake-Tools für Linux | 16.2.29003.222 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Empfohlen
Component.MDD.Linux.GCC.arm | Embedded-Tools und Tools für die IoT-Entwicklung | 16.5.29515.121 | Optional

## <a name="desktop-development-with-c"></a>Desktopentwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Beschreibung:** Hiermit können Sie moderne C++-Apps für Windows mithilfe Ihrer bevorzugten Tools erstellen, darunter MSVC, Clang, CMake und MSBuild.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Erforderlich
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 16.0.28528.71 | Erforderlich
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 Redistributable-Update | 16.5.29515.121 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Architekturtools für C++ | 16.0.28621.142 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Wichtige C++-Desktopfeatures | 16.2.29012.281 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.2876 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time-Debugger | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer (experimentell) | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.VC.ATL | C++-ATL für die neuesten v142-Buildtools (x86 und x64) | 16.4.29313.120 | Empfohlen
Microsoft.VisualStudio.Component.VC.CMake.Project | C++-CMake-Tools für Windows | 16.3.29103.31 | Empfohlen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Testadapter für Boost.Test | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Testadapter für Google Test | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.28) | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.CMake | JSON-Editor | 16.3.29207.166 | Empfohlen
Component.Incredibuild | IncrediBuild – Buildbeschleunigung | 16.5.29721.120 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 – VS 2015: C++-Buildtools (v14.00) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | C++-MFC für die neusten v142-Buildtools (x86 und x64) | 16.4.29313.120 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.28) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.Llvm.Clang | C++-Clang-Compiler für Windows (10.0.0) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | C++-Clang-cl für v142-Buildtools (x64/x86) | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | C++-Module für v142-Buildtools (x64/x86 – experimentell) | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86-Buildtools (v14.16) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | C++-Clang-Tools für Windows (10.0.0 – x64/x86) | 16.8.30509.167 | Optional

## <a name="game-development-with-c"></a>Spieleentwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Beschreibung:** Verwenden Sie die volle Leistung von C++, um professionelle Spiele zu erstellen, die von DirectX, Unreal oder Cocos2D unterstützt werden.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 Redistributable-Update | 16.5.29515.121 | Erforderlich
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.28) | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer (experimentell) | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Empfohlen
Component.Android.NDK.R16B | Android NDK (R16B) | 16.8.30629.96 | Optional
Component.Android.SDK25.Private | Android SDK-Setup (API-Ebene 25, lokale Installation für die Mobile-Entwicklung mit C++) | 16.0.28625.61 | Optional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Optional
Component.Cocos | Cocos | 16.0.28315.86 | Optional
Component.Incredibuild | IncrediBuild – Buildbeschleunigung | 16.5.29721.120 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Optional
Component.MDD.Android | C++ Android-Entwicklungstools | 16.0.28517.75 | Optional
Component.OpenJDK | OpenJDK (Microsoft-Distribution) | 16.1.28811.260 | Optional
Component.Unreal | Unreal Engine-Installer | 16.1.28810.153 | Optional
Component.Unreal.Android | Unterstützung der Android-IDE für die Unreal-Engine | 16.1.28810.153 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Optional
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Optional
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet-Ziele und Buildtasks | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional

## <a name="mobile-development-with-c"></a>Mobile Entwicklung mit C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Beschreibung:** Erstellen Sie mit C++ plattformübergreifende Anwendungen für iOS, Android oder Windows.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Android.SDK25.Private | Android SDK-Setup (API-Ebene 25, lokale Installation für die Mobile-Entwicklung mit C++) | 16.0.28625.61 | Erforderlich
Component.OpenJDK | OpenJDK (Microsoft-Distribution) | 16.1.28811.260 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.8.30509.167 | Erforderlich
Component.Android.NDK.R16B | Android NDK (R16B) | 16.8.30629.96 | Empfohlen
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Empfohlen
Component.MDD.Android | C++ Android-Entwicklungstools | 16.0.28517.75 | Empfohlen
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32 Bit) | 16.8.30629.96 | Optional
Component.Google.Android.Emulator.API25.Private | Google Android-Emulator (API-Ebene 25) (lokale Installation) | 16.1.28810.153 | Optional
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM), lokale Installation | 16.0.28528.71 | Optional
Component.Incredibuild | IncrediBuild – Buildbeschleunigung | 16.5.29721.120 | Optional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Optional
Component.MDD.IOS | C++ iOS-Entwicklungstools | 16.0.28517.75 | Optional

## <a name="net-core-cross-platform-development"></a>Plattformübergreifende .NET Core-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Beschreibung:** Hiermit erstellen Sie plattformübergreifende Anwendungen mit .NET Core, ASP.NET Core, HTML, JavaScript und Containern mit Docker-Unterstützung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Erforderlich
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Erforderlich
Microsoft.ComponentGroup.ClickOnce.Publish | ClickOnce-Veröffentlichung für .NET Core | 16.8.30622.256 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Erforderlich
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Erforderlich
Microsoft.NetCore.Component.DevelopmentTools | .NET Core-Entwicklungstools | 16.8.30607.99 | Erforderlich
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1-Runtime (LTS) | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0-Runtime | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.SDK | .NET SDK | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Web | .NET Core-Entwicklungstools | 16.5.29721.120 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#-Sprachunterstützung für Webprojekte | 16.3.29207.166 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.3.29207.166 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.4.0 | TypeScript 4.0 SDK | 16.0.30509.167 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.2876 | Empfohlen
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs-Tools | 16.0.28714.129 | Empfohlen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Runtime (LTS) | 16.8.30703.189 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.4.29313.120 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Momentaufnahmedebugger | 16.5.29813.82 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Time Travel Debugger | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.DotNetModelBuilder | ML.NET-Modell-Generator (Vorschau) | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs-Tools | 16.0.28621.142 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudtools für die Webentwicklung | 16.2.29003.222 | Empfohlen
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Entwicklungszeit-IIS-Unterstützung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | MSIX Packaging Tools | 16.8.30607.99 | Optional

## <a name="mobile-development-with-net"></a>Mobile Entwicklung mit .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Beschreibung:** Erstellen Sie mit Xamarin plattformübergreifende Anwendungen für iOS, Android oder Windows.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (Microsoft-Distribution) | 16.1.28811.260 | Erforderlich
Component.Xamarin | Xamarin | 16.8.30509.167 | Erforderlich
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.8.30509.167 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Erforderlich
Microsoft.ComponentGroup.ClickOnce.Publish | ClickOnce-Veröffentlichung für .NET Core | 16.8.30622.256 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Erforderlich
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Erforderlich
Microsoft.NetCore.Component.DevelopmentTools | .NET Core-Entwicklungstools | 16.8.30607.99 | Erforderlich
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1-Runtime (LTS) | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0-Runtime | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.SDK | .NET SDK | 16.8.30703.189 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.Merq | Häufig verwendete interne Xamarin-Tools | 16.2.29012.281 | Erforderlich
Microsoft.VisualStudio.Component.MonoDebugger | Mono-Debugger | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET-Vorlagen-Engine | 16.0.28315.86 | Erforderlich
Component.Android.SDK28 | Android SDK-Setup (API-Ebene 28) | 16.2.29003.222 | Empfohlen

## <a name="aspnet-and-web-development"></a>ASP.NET und Webentwicklung

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Beschreibung:** Hiermit erstellen Sie Webanwendungen mit ASP.NET Core, ASP.NET, HTML und JavaScript sowie Container mit Docker-Unterstützung.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Erforderlich
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Erforderlich
Microsoft.ComponentGroup.ClickOnce.Publish | ClickOnce-Veröffentlichung für .NET Core | 16.8.30622.256 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Erforderlich
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Erforderlich
Microsoft.NetCore.Component.DevelopmentTools | .NET Core-Entwicklungstools | 16.8.30607.99 | Erforderlich
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1-Runtime (LTS) | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0-Runtime | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.SDK | .NET SDK | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Web | .NET Core-Entwicklungstools | 16.5.29721.120 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.FSharp | F#-Sprachunterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.FSharp.WebTemplates | F#-Sprachunterstützung für Webprojekte | 16.3.29207.166 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.3.29207.166 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.4.0 | TypeScript 4.0 SDK | 16.0.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.Web.Client | ASP.NET und Webentwicklungstools | 16.8.30607.99 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.2876 | Empfohlen
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure WebJobs-Tools | 16.0.28714.129 | Empfohlen
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Empfohlen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 16.0.28516.191 | Empfohlen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1-Runtime (LTS) | 16.8.30703.189 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.AspNet45 | Erweiterte ASP.NET-Features | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.4.29313.120 | Empfohlen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud-Explorer | 16.0.28625.61 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Momentaufnahmedebugger | 16.5.29813.82 | Empfohlen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Time Travel Debugger | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6-Tools | 16.0.28315.86 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure WebJobs-Tools | 16.0.28621.142 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Cloudtools für die Webentwicklung | 16.2.29003.222 | Empfohlen
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.8.TargetingPack | Paket zur Festlegung von Zielversionen für .NET Framework 4.8 | 16.4.29313.120 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8-Entwicklungstools | 16.4.29318.151 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 16.0.28528.71 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 16.4.29409.204 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Tools für Webleistung und Auslastungstests | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Zusätzliche Projektvorlagen (frühere Versionen) | 16.0.28621.142 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 16.5.29514.35 | Optional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Entwicklungszeit-IIS-Unterstützung | 16.0.28315.86 | Optional

## <a name="nodejs-development"></a>Node.js-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Node

**Beschreibung:** Erstellen Sie skalierbare Netzwerkanwendungen mithilfe von Node.js, einer asynchronen, ereignisgesteuerten JavaScript-Runtime. 

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.Node.Tools | Node.js-Entwicklungstools | 16.5.29515.121 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.4.0 | TypeScript 4.0 SDK | 16.0.30509.167 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Erforderlich
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.2876 | Empfohlen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Optional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.4.29409.204 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.28) | 16.8.30509.167 | Optional

## <a name="officesharepoint-development"></a>Office/SharePoint-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Office

**Beschreibung:** Erstellen Sie Office- und SharePoint-Add-Ins, SharePoint-Lösungen und VSTO-Add-Ins mithilfe von C#, VB und JavaScript.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Erforderlich
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Erforderlich
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Erforderlich
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 16.0.28517.75 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Erforderlich
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1-Runtime (LTS) | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0-Runtime | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.SDK | .NET SDK | 16.8.30703.189 | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET-Desktopentwicklungstools | 16.8.30607.99 | Erforderlich
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools für Visual Studio | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.3.29207.166 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.TypeScript.4.0 | TypeScript 4.0 SDK | 16.0.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Erforderlich
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools für Office (VSTO) | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.Net.Component.4.6.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.1 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.7.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.8.TargetingPack | Paket zur Festlegung von Zielversionen für .NET Framework 4.8 | 16.4.29313.120 | Optional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8-Entwicklungstools | 16.4.29318.151 | Optional
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Optional
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Optional

## <a name="python-development"></a>Python-Entwicklung

**ID:** Microsoft.VisualStudio.Workload.Python

**Beschreibung:** Bearbeiten, Debuggen, interaktive Entwicklung und Quellcodeverwaltung für Python.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.PythonTools | Unterstützung der Sprache Python | 16.5.29515.121 | Erforderlich
Component.CPython3.x64 | Python 3, 64 Bit (3.7.8) | 3.7.8 | Empfohlen
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.2876 | Empfohlen
Microsoft.Component.PythonTools.Minicondax64 | Python-Miniconda | 16.2.29003.222 | Empfohlen
Microsoft.Component.PythonTools.Web | Webunterstützung für Python | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 16.4.29409.204 | Empfohlen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript- und TypeScript-Sprachunterstützung | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.TypeScript.4.0 | TypeScript 4.0 SDK | 16.0.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.WebDeploy | Web Deploy | 16.0.28517.75 | Empfohlen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET und Webentwicklung | 16.8.30509.167 | Empfohlen
Component.CPython2.x64 | Python 2, 64 Bit (2.7.18) | 2.7.18 | Optional
Component.CPython2.x86 | Python 2, 32 Bit (2.7.18) | 2.7.18 | Optional
Component.CPython3.x86 | Python 3, 32 Bit (3.7.8) | 3.7.8 | Optional
Component.Microsoft.VisualStudio.RazorExtension | Razor-Sprachdienste | 16.0.28714.129 | Optional
Component.Microsoft.Web.LibraryManager | Bibliotheks-Manager | 16.0.28315.86 | Optional
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Optional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Native Python-Entwicklungstools | 16.8.30607.99 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Optional
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Optional
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Optional
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1-Runtime (LTS) | 16.8.30703.189 | Optional
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0-Runtime | 16.8.30703.189 | Optional
Microsoft.NetCore.Component.SDK | .NET SDK | 16.8.30703.189 | Optional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure-Dokumenterstellungstools | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Azure-Bibliotheken für .NET | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure-Serveremulator | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure-Speicheremulator | 16.4.29313.120 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services-Kerntools | 16.4.29409.204 | Optional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services-Buildtools | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.DockerTools | Containerentwicklungstools | 16.4.29409.204 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript-Diagnose | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Core für Arbeitsauslastung verwalteter Desktops | 16.4.29318.151 | Optional
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server-ODBC-Treiber | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server-Befehlszeilenprogramme | 16.0.28707.177 | Optional
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 16.0.28315.86 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++-Profilerstellungstools | 16.5.29515.121 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.28) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Web | ASP.NET und Webentwicklungstools | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Optional
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Voraussetzungen: ASP.NET- und Webentwicklungstools | 16.4.29318.151 | Optional

## <a name="universal-windows-platform-development"></a>Entwicklung für die universelle Windows-Plattform

**ID:** Microsoft.VisualStudio.Workload.Universal

**Beschreibung:** Hiermit erstellen Sie Anwendungen für die Universelle Windows-Plattform mit C#, VB oder optional C++.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET systemeigen | 16.5.29515.121 | Erforderlich
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 16.0.28517.75 | Erforderlich
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1-Runtime (LTS) | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0-Runtime | 16.8.30703.189 | Erforderlich
Microsoft.NetCore.Component.SDK | .NET SDK | 16.8.30703.189 | Erforderlich
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Erforderlich
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.Graphics | Bild- und 3D-Modell-Editoren | 16.0.28517.75 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | MSIX Packaging Tools | 16.8.30607.99 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native und .NET Standard | 16.3.29102.218 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.Support | UWP-Tools (Universelle Windows-Plattform) | 16.4.29409.204 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | UWP-Tools für Xamarin | 16.8.30607.99 | Erforderlich
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Empfohlen
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | Klassen-Designer | 16.0.28528.71 | Optional
Microsoft.VisualStudio.Component.CodeClone | Codeklon | 16.4.29409.204 | Optional
Microsoft.VisualStudio.Component.CodeMap | Code Map | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Live-Abhängigkeitsüberprüfung | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML-Editor | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | Grafikdebugger und GPU-Profiler für DirectX | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Optional
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | C++-Unterstützung für die Universelle Windows-Plattform für v142-Buildtools (ARM64) | 16.3.29207.166 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | C++-Kernfeatures | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 – VS 2019 C++ ARM-Buildtools (v14.28) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 – VS 2019 C++-ARM64-Buildtools (v14.28) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.28) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ ARM-Buildtools (v14.16) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ ARM64-Buildtools (v14.16) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86-Buildtools (v14.16) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.8.30509.167 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | USB-Gerätekonnektivität | 16.8.30607.99 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Architektur- und Analysetools | 16.5.29514.35 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | UWP-Tools (Universelle Windows-Plattform) für C++ (v142) | 16.8.30607.99 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | UWP-Tools (Universelle Windows-Plattform) für C++ (v141) | 16.1.28810.153 | Optional

## <a name="visual-studio-extension-development"></a>Entwicklung von Visual Studio-Erweiterungen

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Beschreibung:** Erstellen Sie Add-Ons und Erweiterungen für Visual Studio, z. B. neue Befehle, Codeanalysetools und Toolfenster.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Erforderlich
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 16.0.28517.75 | Erforderlich
Microsoft.Net.Component.4.7.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.7.2 | 16.8.30509.167 | Erforderlich
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2-Entwicklungstools | 16.3.29207.166 | Erforderlich
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,3 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 16.1.28829.92 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 16.0.28714.129 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 16.8.30509.167 | Erforderlich
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Erforderlich
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Erforderliche Komponenten für die Visual Studio-Extensionentwicklung | 16.4.29318.151 | Erforderlich
Microsoft.VisualStudio.Component.DiagnosticTools | .NET-Profilerstellungstools | 16.8.30509.167 | Empfohlen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Empfohlen
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 16.0.28625.61 | Empfohlen
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 16.2.29003.222 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Optional
Microsoft.VisualStudio.Component.DslTools | SDK für Modellierung | 16.0.28315.86 | Optional

## <a name="unaffiliated-components"></a>Nicht zugeordnete Komponenten

Dies sind Komponenten, die in keiner Arbeitsauslastung enthalten sind, jedoch als einzelne Komponenten ausgewählt werden können.

Komponenten-ID | name | Version
--- | --- | ---
Component.GitHub.VisualStudio | GitHub-Erweiterung für Visual Studio | 2.5.9.5485
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 16.4.29409.204
Microsoft.Component.HelpViewer | Help Viewer | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2-Runtime (nicht mehr unterstützt) | 16.8.30509.167
Microsoft.Net.Core.Component.SDK.3.0 | .NET Core 3.0-Runtime (nicht mehr unterstützt) | 16.8.30703.189
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Entwicklungstools mit .NET Core 2.1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Webentwicklungstools mit .NET Core 2.1 | 16.3.29207.166
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Azure DevOps-Integration in Office | 16.0.28625.61
Microsoft.VisualStudio.Component.Debugger.VSOnline | Debugger für Visual Studio Codespaces | 16.8.30509.167
Microsoft.VisualStudio.Component.Git | Git für Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL-Tools | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Test der codierten UI | 16.0.28327.66
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ ARM-Buildtools (v14.20) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - VS 2019: C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ ARM64-Buildtools (v14.20) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - VS 2019: C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | C++ v14.20 ATL für v142-Buildtools (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | C++ v14.20 ATL für v142-Buildtools (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | C++ v14.20 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | C++ v14.20 ATL für v142-Buildtools (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | C++ v14.20 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | C++ v14.20 ATL für v142-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.20) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.20.MFC | C++ v14.20 MFC für v142-Buildtools (x86 & x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | C++ v14.20 MFC für v142-Buildtools (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | C++ v14.20 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | C++ v14.20 MFC für v142-Buildtools (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | C++ v14.20 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | C++ v14.20 MFC für v142-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.20) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 - VS 2019: C++-ARM-Buildtools (v14.21) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 - VS 2019: C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 - VS 2019 C++ ARM64-Buildtools (v14.21) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 - VS 2019: C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | C++ v14.21 ATL für v142-Buildtools (x86/x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | C++ v14.21 ATL für v142-Buildtools (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | C++ v14.21 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | C++ v14.21 ATL für v142-Buildtools (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | C++ v14.21 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | C++ v14.21 ATL für v142-Buildtools mit Spectre-Entschärfungen (x86/x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | C++ v14.21 MFC für v142-Buildtools (x86/x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | C++ v14.21 MFC für v142-Buildtools (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | C++ v14.21 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | C++ v14.21 MFC für v142-Buildtools (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | C++ v14.21 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | C++ v14.21 MFC für v142-Buildtools mit Spectre-Entschärfungen (x86/x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 - VS 2019: C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC v142 – VS 2019 C++: ARM-Buildtools (v14.22) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | MSVC v142 – VS 2019: C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 – VS 2019 C++ ARM64-Buildtools (v14.22) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC v142 – VS 2019: C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | C++ v14.22: ATL für v142-Buildtools (x86 und x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | C++ v14.22: ATL für v142-Buildtools (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | C++ v14.22: ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | C++ v14.22: ATL für v142-Buildtools (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | C++ v14.22: ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | C++ v14.22: ATL für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.22) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.22.MFC | C++ v14.22: MFC für v142-Buildtools (x86 und x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | C++ v14.22: MFC für v142-Buildtools (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | C++ v14.22: MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | C++ v14.22: MFC für v142-Buildtools (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | C++ v14.22: MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | C++ v14.22: MFC für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 – VS 2019 C++: x64/x86-Buildtools (v14.22) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC v142 – VS 2019: C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 – VS 2019 C++-ARM-Buildtools (v14.23) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 – VS 2019 C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC v142 – VS 2019 C++-ARM64-Buildtools (v14.23) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | MSVC v142 – VS 2019 C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | C++ v14.23 ATL für v142-Buildtools (x86 und x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | C++ v14.23 ATL für v142-Buildtools (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | C++ v14.23 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | C++ v14.23 ATL für v142-Buildtools (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | C++ v14.23 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | C++ v14.23 ATL für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.23) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.23.MFC | C++ v14.23 MFC für v142-Buildtools (x86 und x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | C++ v14.23 MFC für v142-Buildtools (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | C++ v14.23 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | C++ v14.23 MFC für v142-Buildtools (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | C++ v14.23 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | C++ v14.23 MFC für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.23) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | MSVC v142 – VS 2019 C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC v142 – VS 2019 C++-ARM-Buildtools (v14.24) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | MSVC v142 – VS 2019 C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64 | MSVC v142 – VS 2019 C++-ARM64-Buildtools (v14.24) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | MSVC v142 – VS 2019 C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | C++ v14.24 ATL für v142-Buildtools (x86 und x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | C++ v14.24 ATL für v142-Buildtools (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | C++ v14.24 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | C++ v14.24 ATL für v142-Buildtools (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | C++ v14.24 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | C++ v14.24 ATL für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.24) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.24.MFC | C++ v14.24 MFC für v142-Buildtools (x86 und x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM | C++ v14.24 MFC für v142-Buildtools (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM.Spectre | C++ v14.24 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64 | C++ v14.24 MFC für v142-Buildtools (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64.Spectre | C++ v14.24 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.24.MFC.Spectre | C++ v14.24 MFC für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.24) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC v142 – VS 2019 C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.25.ARM | MSVC v142 – VS 2019 C++-ARM-Buildtools (v14.25) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.ARM.Spectre | MSVC v142 – VS 2019 C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.25) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.ARM64 | MSVC v142 – VS 2019 C++-ARM64-Buildtools (v14.25) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.ARM64.Spectre | MSVC v142 – VS 2019 C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.25) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.ATL | C++ v14.25 ATL für v142-Buildtools (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM | C++ v14.25 ATL für v142-Buildtools (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM.Spectre | C++ v14.25 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM64 | C++ v14.25 ATL für v142-Buildtools (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM64.Spectre | C++ v14.25 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.ATL.Spectre | C++ v14.25 ATL für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.25) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.MFC | C++ v14.25 MFC für v142-Buildtools (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM | C++ v14.25 MFC für v142-Buildtools (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM.Spectre | C++ v14.25 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64 | C++ v14.25 MFC für v142-Buildtools (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64.Spectre | C++ v14.25 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.MFC.Spectre | C++ v14.25 MFC für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.25) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.25.x86.x64.Spectre | MSVC v142 – VS 2019 C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.25) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ARM | MSVC v142 – VS 2019 C++ ARM-Buildtools (v14.26) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ARM.Spectre | MSVC v142 – VS 2019 C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.26) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ARM64 | MSVC v142 – VS 2019 C++-ARM64-Buildtools (v14.26) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ARM64.Spectre | MSVC v142 – VS 2019 C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.26) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ATL | C++ v14.26 ATL für v142-Buildtools (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM | C++ v14.26 ATL für v142-Buildtools (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM.Spectre | C++ v14.26 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64 | C++ v14.26 ATL für v142-Buildtools (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64.Spectre | C++ v14.26 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.ATL.Spectre | C++ v14.26 ATL für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.26) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.MFC | C++ v14.26 MFC für v142-Buildtools (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM | C++ v14.26 MFC für v142-Buildtools (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM.Spectre | C++ v14.26 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64 | C++ v14.26 MFC für v142-Buildtools (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64.Spectre | C++ v14.26 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.MFC.Spectre | C++ v14.26 MFC für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.26) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.26.x86.x64.Spectre | MSVC v142 – VS 2019 C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.26) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ARM | MSVC v142 – VS 2019 C++ ARM-Buildtools (v14.27) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ARM.Spectre | MSVC v142 – VS 2019 C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.27) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ARM64 | MSVC v142 – VS 2019 C++-ARM64-Buildtools (v14.27) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ARM64.Spectre | MSVC v142 – VS 2019 C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.27) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ATL | C++ v14.27 ATL für v142-Buildtools (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM | C++ v14.27 ATL für v142-Buildtools (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM.Spectre | C++ v14.27 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM64 | C++ v14.27 ATL für v142-Buildtools (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM64.Spectre | C++ v14.27 ATL für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.ATL.Spectre | C++ v14.27 ATL für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.CLI.Support | C++-/CLI-Unterstützung für v142-Buildtools (14.27) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.MFC | C++ v14.27 MFC für v142-Buildtools (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM | C++ v14.27 MFC für v142-Buildtools (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM.Spectre | C++ v14.27 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64 | C++ v14.27 MFC für v142-Buildtools (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64.Spectre | C++ v14.27 MFC für v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.MFC.Spectre | C++ v14.27 MFC für v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.x86.x64 | MSVC v142 – VS 2019 C++-x64/x86-Buildtools (v14.27) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.14.27.x86.x64.Spectre | MSVC v142 – VS 2019 C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.27) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.ATL.ARM | C++-ATL für die neuesten v142-Buildtools (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++-ATL für die neuesten v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++-ATL für die neuesten v142-Buildtools (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++-ATL für die neuesten v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++-ATL für die neuesten v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++-MFC für die neuesten v142-Buildtools mit Spectre-Entschärfungen (x86 und x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++-MFC für die neuesten v142-Buildtools (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++-MFC für die neuesten v142-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++-MFC für die neuesten v142-Buildtools (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++-MFC für die neuesten v142-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++ 2019 Redistributable-MSMs | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 – VS 2019 C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.28) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 – VS 2019 C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.28) | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 – VS 2019 C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.28)  | 16.8.30509.167
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 - VS 2017: C++-ARM-Bibliotheken mit Spectre-Entschärfungen (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 - VS 2017: C++-ARM64-Bibliotheken mit Spectre-Entschärfungen (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | C++-ATL für v141-Buildtools (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | C++-ATL für v141-Buildtools (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | C++-ATL für v141-Buildtools mit Spectre-Entschärfungen (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | C++-ATL für v141-Buildtools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | C++-ATL für v141-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | C++-ATL für v141-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | C++-/CLI-Unterstützung für v141-Buildtools (14.16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | C++ MFC für v141-Buildtools (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | C++ MFC für v141-Buildtools (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | C++ MFC für v141-Buildtools mit Spectre-Entschärfungen (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | C++ MFC für v141-Buildtools (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | C++ MFC für v141-Buildtools mit Spectre-Entschärfungen (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | C++ MFC für v141-Buildtools mit Spectre-Entschärfungen (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 - VS 2017: C++-x64/x86-Bibliotheken mit Spectre-Entschärfungen (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | C++-Windows XP-Unterstützung für Tools in VS 2017 (v141) [veraltet] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
