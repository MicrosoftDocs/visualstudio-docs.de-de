---
title: Unterstützte Visual Studio-Features (Vorschau)
description: Hier erfahren Sie mehr über die bei der Arbeit mit GitHub Codespaces verfügbaren Visual Studio-IDE-Features.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 1a94915748f6c7cedb19a0b27c67eb67d6086963
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971140"
---
# <a name="supported-visual-studio-features-preview"></a>Unterstützte Visual Studio-Features (Vorschau)

Visual Studio stellt eine umfangreiche Entwicklungsumgebung bereit, wenn eine Verbindung mit einem Codespace hergestellt wird. Sie können die bereits bekannten internen Visual Studio-Tools zum Bearbeiten, Debuggen, Testen und Versionieren Ihres Quellcodes nutzen sowie Produktivitätsfeatures wie Projektvorlagen, umfangreiche Codenavigation und IntelliSense.

In der aktuellen [öffentlichen Betaversion](https://github.com/features/codespaces) von GitHub Codespaces werden einige Visual Studio-Features möglicherweise nicht vollständig unterstützt oder fehlen zu Beginn noch. In den folgenden Abschnitten wird erläutert, was Sie von Visual Studio und der Betaversion von GitHub Codespaces erwarten können und worauf Sie sich in Zukunft freuen können. 

Dies ist **nicht als vollständige Liste gedacht**, sondern zur Erläuterung der allgemeinen Funktionen von Visual Studio bei einer Verbindung mit einem Codespace.

> [!NOTE]
> Wenn Ihnen bei der Verwendung von Codespaces mit Visual Studio ein bestimmtes Feature fehlt, raten wir Ihnen, in der [Visual Studio-Entwicklercommunity](https://aka.ms/feedback/suggest?space=8) ein Issue zu erstellen und uns dies mitzuteilen. Dies hilft uns dabei, die meistgewünschten Features als vorrangig zu behandeln.

> [!NOTE]
> Die folgende Beschreibung von Features bezieht sich nur auf Visual Studio und nicht auf die beiden anderen GitHub Codespaces-Clients (Visual Studio Code und der Editor im Browser).

## <a name="edit-and-navigation"></a>Bearbeitung und Navigation

Bei der Bearbeitung von Quellcode in einem Codespace sollten Sie kaum Unterschiede erkennen, da Ihnen intelligente Sprachfeatures wie IntelliSense, Codenavigation, Diagnose und Vorschläge zur Verfügung stehen.

* IntelliSense*
* Codenavigation*
* Codeformatierung über „Dokument formatieren“
* Syntaxhervorhebung
* QuickInfo*
* HTML-, CSS- und Razor-Editoren*: teilweise unterstützt
* JavaScript- und TypeScript-Editor*: teilweise unterstützt

Noch nicht verfügbar:

* IntelliSense*: Einige der Filter für die automatische Vervollständigung/Memberliste sind nicht verfügbar. Vervollständigung für nicht importierte Typen und IntelliSense im Überwachungsfenster sind noch nicht verfügbar.
* Codenavigation*: Die meisten Befehle werden unterstützt. „Zu Basis wechseln“ und „In Dateien suchen“ mit Pfadspezifikation werden noch nicht unterstützt.
* QuickInfo*: Farbgebung in der QuickInfo wird nicht unterstützt.
* HTML-, CSS- und Razor-Editoren*: Diagnose, IntelliSense-Vervollständigung, QuickInfo, intelligenter Einzug; semantische Farbgebung, Navigationsbefehle etc. derzeit nicht unterstützt
* JavaScript- und TypeScript-Editor*: Skriptblöcke (z. B. JavaScript-Inhalte in HTML- und CSHTML-Dateien) sowie semantische Hervorhebung werden noch nicht unterstützt. Es liegen bekannte Probleme mit Glühbirnenfeatures und dem Linten vor.
* CMake-Zielansicht
* Editor für CMake-Projekteinstellungen
* STRG+F7 (Datei kompilieren)
* CodeLens
* Codeausschnitte
* IntelliCode

## <a name="application-types-and-configuration"></a>Anwendungstypen und Konfigurationen

Die meisten Anwendungstypen und Projektkonfigurationen werden unterstützt. Sie müssen den Projektcode jedoch ohne Hilfe von visuellen Designern direkt bearbeiten. Weitere Informationen zur Konfiguration finden Sie unter [Anpassen eines Codespace](customize-codespaces.md).

* Projekt- und Elementvorlagen
* .NET Core- und ASP.NET Core-Projekte
* C++-Konsolen-Apps: CMake und VCXPROJ unterstützt
* C++-Apps für Linux: weitgehend unterstützt für Nutzung ohne grafische Benutzeroberfläche (GUI), Möglichkeit zum Installieren und Bereitstellen des WSL sowie einer plattformspezifischen Version von IntelliSense und zum Kompilieren
* Bearbeitung von Projektdateien: weitgehend unterstützt, einige Vervollständigungs-, Syntaxhervorhebungs- und erweiterte Bearbeitungsfeatures fehlen
* GitHub-Konten: können verwendet werden, um Codespaces zu erstellen und eine Verbindung damit herzustellen sowie um auf Ressourcen zuzugreifen, die für das Konto auf GitHub zur Verfügung stehen
* Azure CLI: Die Schnittstelle verwendet die angemeldete Visual Studio-Identität bzw. die angemeldeten Keychainkonten nicht. Die browserbasierte Anmeldung wird nicht unterstützt, Sie können sich jedoch im integrierten Terminal mit `az login --use-device-code` authentifizieren.

Noch nicht verfügbar:

* Benutzeroberflächen-Designer: WinForms-, WPF-, und Ressourcen-Designer
* Die App-Umwandlung für WinForms- und WPF-Projekte ist nur unter einem Featureflag verfügbar.
* Visual Basic- und F#-Projekte
* Projekte für das .NET Framework
* Docker Compose-Projekte
* Seiten mit Projekteigenschaften
* Authentifizierungsoptionen in ASP.NET Core-Vorlagen
* Apps, die für die Installation eine grafische Benutzeroberfläche benötigen: Alles, was über das Terminal installiert werden kann, wird unterstützt (einschließlich des Installationsprogramms für Chocolatey), die tatsächliche GUI ist allerdings nicht sofort verfügbar. Dieses Problem können Sie derzeit umgehen, indem Sie den Zugriff auf die GUIs für den Vollbildmodus von Live Share aktivieren. Auf Verwaltungskonsolen kann nicht zugegriffen werden. Apps, für deren Installation ein Neustart erforderlich ist, werden nicht unterstützt.
* Verwaltete Identitäten für Azure-Ressourcen in Visual Studio
* Intranetressourcen (privates Netzwerk): Codespaces können derzeit keine Verbindung mit einer Ressource herzustellen, für die ein VPN erforderlich ist.
* Erweiterungen: Bei der Verwendung von Codespaces mit Visual Studio werden keine Erweiterungen unterstützt.

## <a name="debugging"></a>Debuggen

Grundlegendes Debuggen von inneren Schleifen wird unterstützt. Hierzu gehören das Festlegen von Haltepunkten, die grundlegende Einzelschrittausführung von Code, das Überprüfen von Variablen und die Fenster „Lokal“ und „Auto“ sowie das Überwachungsfenster. Einige weitere Fenster, Anpassungen und Schnellansichten werden nicht unterstützt.

* Haltepunkte*
* Grundlegende Einzelschrittausführung
* Fenster „Lokal“ und „Auto“ und Überwachungsfenster*: teilweise unterstützt
* Symbolserver, Quellserver und das Importieren/Exportieren von Datentipps werden teilweise unterstützt.

Noch nicht verfügbar:

* Haltepunkte*: An Haltepunktbezeichnungen, Datenhaltepunkten und „Haltepunkt festlegen“ im Fenster „Disassemblierung“ wird derzeit noch gearbeitet. Das Importieren und Exportieren von Haltepunkten wird teilweise unterstützt.
* Fenster „Lokal“ und „Auto“ und Überwachungsfenster*: einige Funktionen wie die Anweisungsvervollständigung im Suchfeld und die Suchfeldnavigation
* Anpassungsmöglichkeiten für die Benutzeroberfläche: Anheftbare Eigenschaften und das Ausblenden von Vorlagenparametern werden nicht unterstützt.
* Schnellansichten: Natvis für C++ wird teilweise unterstützt. Das Fenster „Disassemblierung“, XAML Visual Diagnostics, benutzerdefinierte .NET-Schnellansichten und Datasetschnellansichten werden nicht unterstützt.
* Weitere Debuggerfenster: Prozessfenster werden teilweise unterstützt. Fenster „Parallele Stapel“: Aufgabenansicht, Diagnosehub und die Dialogfelder „Quellcode suchen“ und „Symbol suchen“ werden nicht unterstützt.
* Einige Debuggerworkflows: „An Prozess anhängen“, Just-in-Time-Debugger (JIT), das Debuggen von Speicherabbildern, Profilerstellung und IntelliTrace werden nicht unterstützt. Die Einzelschrittausführung von C++-Code mit dem Feature „Nur eigenen Code“ wird teilweise unterstützt.
* Bearbeiten und fortfahren: wird weder für verwalteten noch für nativen Code unterstützt
* Threadingfeatures: „Threads einfrieren“/„Threads reaktivieren“, „Thread umbenennen“ und „Threads in Quelle anzeigen“ werden nicht unterstützt.
* Weitere Einzelschrittausführungsfeatures: Das automatische Überspringen von Eigenschaften und Operatoren (.NET Core) und „Einzelschritt in Angabe“ werden nicht unterstützt. 

## <a name="features"></a>Features

Beim Arbeiten mit Visual Studio mit einem verbundenen Codespace stehen Ihnen die gleichen Barrierefreiheitsfunktionen zur Verfügung wie beim lokalen Arbeiten.

* Quellcodeverwaltung: Umfassende Git-Unterstützung über die neue [integrierte Git-Benutzeroberfläche](../git-with-visual-studio.md). Damit Git-Submodule in einem Codespace geklont werden, müssen Sie möglicherweise `git submodule update` über das Terminal ausführen.
* Barrierefreiheit: Es liegt ein bekanntes Problem vor, bei dem Hilfstechnologien nicht auf das Appcasting einer debuggten App zugreifen können. Abgesehen von dieser Einschränkung wird nicht davon ausgegangen, dass Kompatibilitätsprobleme vorliegen, die nicht bereits in der lokalen Version von Visual Studio bestehen. Informieren Sie uns, wenn Sie Fehler finden, indem Sie auf der [Entwicklercommunity-Website](https://aka.ms/feedback/report?space=8) ein Issue erstellen.
* Veröffentlichung: Das Veröffentlichen in Azure über GitHub Actions wird unterstützt.
* Verbundene Dienste: AppInsights, Key Vault, Storage, SQL, Redis, Cosmos, OpenAPI und gRPC werden teilweise unterstützt.
* Test-Explorer*: weitgehend unterstützt

Noch nicht verfügbar:

* Test-Explorer*: Einige Features, z. B. Standardarchitekturauswahl, das parallele Ausführen von Tests sowie Wiedergabelisten, werden nicht unterstützt. Es liegen bekannte Probleme beim Debuggen von Komponententests, Laufzeiteinstellungen und einigen weiteren Enterprise-Features vor. Die Profilerstellung für Komponententests wird nicht unterstützt.
* Benutzeroberfläche des NuGet-Paket-Managers: Die NuGet-Befehlszeile wird unterstützt.
* Enterprise-Testfeatures: Live Unit Testing, Microsoft Fakes, Code Coverage und IntelliTest werden nicht unterstützt.
* Erweiterte Veröffentlichungsszenarios: selektive Veröffentlichung, FTP-Veröffentlichung, Vorschau von Änderungen, Symbolleiste für schnelles Veröffentlichen etc.

## <a name="see-also"></a>Weitere Informationen

* [Was ist GitHub Codespaces?](codespaces-overview.md)
* [Verwenden von Visual Studio mit einem Codespace](use-visual-studio-with-codespaces.md)
* [Anpassen eines Codespace](customize-codespaces.md)
