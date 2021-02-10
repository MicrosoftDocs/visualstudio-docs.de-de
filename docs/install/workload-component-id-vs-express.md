---
title: Workload- und Komponenten-IDs in Visual Studio Desktop Express
titleSuffix: ''
description: Verwenden Sie Arbeitsauslastungs- und Komponenten-IDs, um Visual Studio über die Befehlszeile zu installieren oder um sie als Abhängigkeit in einem VSIX-Manifest anzugeben
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: 21735c82a318623758f1980a1865a543adde121e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881801"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Visual Studio Desktop Express-Komponentenverzeichnis

In den Tabellen auf dieser Seite sind die IDs aufgeführt, die Sie verwenden können, um Visual Studio über die Befehlszeile zu installieren, oder die Sie als Abhängigkeit in einem VSIX-Manifest angeben können. Beachten Sie, dass weitere Komponenten hinzugefügt werden, wenn wir Updates für Visual Studio veröffentlichen.

Beachten Sie zudem Folgendes im Hinblick auf die Seite:

* Für jede Arbeitsauslastung gibt es einen eigenen Abschnitt, gefolgt von der Arbeitsauslastungs-ID und einer Tabelle der Komponenten, die für die Arbeitsauslastung zur Verfügung stehen.
* Die **erforderlichen** Komponenten werden standardmäßig bei der Installation der Arbeitsauslastung installiert.
* Bei Bedarf können Sie auch die **empfohlenen** und **optionalen** Komponenten installieren.
* Wir haben auch einen Abschnitt hinzugefügt, in dem die zusätzlichen Komponenten aufgeführt sind, die keiner Arbeitsauslastung zugeordnet sind.

Wenn Sie Abhängigkeiten im VSIX-Manifest festlegen, müssen Sie nur Komponenten-IDs angeben. Verwenden Sie die Tabellen auf dieser Seite, um die minimalen Komponentenabhängigkeiten zu bestimmen. In einigen Fällen könnte dies bedeuten, dass Sie nur eine Komponente einer Arbeitsauslastung angeben. In anderen Fällen könnte dies bedeuten, dass Sie mehrere Komponenten einer einzelnen Arbeitsauslastung oder mehrere Komponenten von mehreren Arbeitsauslastungen angeben. Weitere Informationen finden Sie auf der Seite [Gewusst wie: Migrieren von Erweiterungsprojekten zu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Weitere Informationen zur Verwendung dieser IDs finden Sie auf der Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Eine Liste der Arbeitsauslastungs- und Komponenten-IDs für andere Produkte finden Sie auf der Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017](workload-and-component-ids.md).

## <a name="express-for-windows-desktop"></a>Express für Windows Desktop

**ID:** Microsoft.VisualStudio.Workload.WDExpress

**Beschreibung:** Erstellen Sie native und verwaltete Anwendungen wie WPF, WinForms und Win32 mit syntaxfähiger Codebearbeitung, Quellcodeverwaltung und Arbeitselementverwaltung. Bietet Unterstützung für C#, Visual Basic und Visual C++.

### <a name="components-included-by-this-workload"></a>Komponenten in dieser Arbeitsauslastung

Komponenten-ID | Name | Version | Abhängigkeitstyp
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce-Veröffentlichung | 15.8.27825.0 | Erforderlich
Microsoft.Component.HelpViewer | Help Viewer | 15.6.27323.2 | Erforderlich
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Erforderlich
Microsoft.Component.VC.Runtime.OSSupport | Visual C++ Runtime für UWP | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.5.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.1 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.5.2.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5.2 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.5.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.5 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.1.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6.1 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.6.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4.6 | 15.6.27406.0 | Erforderlich
Microsoft.Net.Component.4.TargetingPack | Paket zur Festlegung von Zielversionen von .NET Framework 4 | 15.6.27406.0 | Erforderlich
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1-Entwicklungstools | 15.8.27825.0 | Erforderlich
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Entwicklungstools für .NET Framework 4 – 4.6 | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Common.Azure.Tools | Tools für Konnektivität und Veröffentlichung | 15.9.28107.0 | Erforderlich
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio-Kern-Editor | 15.8.27729.1 | Erforderlich
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6-Tools | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.NuGet | NuGet-Paket-Manager | 15.9.28016.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.Compiler | C#- und Visual Basic-Roslyn-Compiler | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# und Visual Basic | 15.8.27729.1 | Erforderlich
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL-Runtime | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CLR | CLR-Datentypen für SQL Server | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server-Befehlszeilenprogramme | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.DataSources | Datenquellen für SQL Server-Unterstützung | 15.0.26621.2 | Erforderlich
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Erforderlich
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server-Datentools | 15.9.28107.0 | Erforderlich
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statische Analysetools | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.TextTemplating | Textvorlagentransformation | 15.0.26208.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.CLI.Support | C++-/CLI-Unterstützung | 15.6.27309.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.Tools.ARM | Visual Studio C++-Compiler und -Bibliotheken für ARM | 15.8.27825.0 | Erforderlich
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Visual C++-Compiler und -Bibliotheken für ARM64 | 15.9.28230.55 | Erforderlich
Microsoft.VisualStudio.Component.VisualStudioData | Datenquellen und Dienstverweise | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Erforderlich
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Erforderlich

## <a name="unaffiliated-components"></a>Nicht zugeordnete Komponenten

Dies sind Komponenten, die in keiner Arbeitsauslastung enthalten sind, jedoch als einzelne Komponenten ausgewählt werden können.

Komponenten-ID | Name | Version
--- | --- | ---
n/v | n/v | n/v

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Weitere Informationen

* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Beispiele für Befehlszeilenparameter](command-line-parameter-examples.md)
* [Erstellen einer Offlineinstallation von Visual Studio](create-an-offline-installation-of-visual-studio.md)
