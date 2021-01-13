---
title: 'Visual Studio-Erweiterbarkeit „Ordner öffnen“: Übersicht | Microsoft-Dokumentation'
description: Hier erfahren Sie mehr über die Erweiterbarkeit für das Feature „Ordner öffnen“. Mit diesem Feature können Benutzer eine Codebasis in Visual Studio ohne Projekt- oder Projektmappendateien öffnen.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 81ca62c834e09d542016ffce607abf3c32cf2a61
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863747"
---
# <a name="open-folder-extensibility"></a>Erweiterbarkeit „Ordner öffnen“

Mit dem Feature [Ordner öffnen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) können Benutzer jede beliebige Codebasis in Visual Studio öffnen, ohne dass Projekt- oder Projektmappendateien benötigt werden. „Ordner öffnen“ bietet die Features, die Benutzer von Visual Studio erwarten, beispielsweise:

* Integration von Projektmappen-Explorer und Suche
* Farbliche Kennzeichnung im Editor
* Gehe zu Navigation
* Suchfunktion „In Dateien suchen“

Bei Verwendung mit Workloads z. B. für .NET- und C++-Entwicklung können Benutzer auch die folgenden Funktionen nutzen:

* Umfassende IntelliSense-Funktionen
* Sprachspezifische Funktionen

Mit „Ordner öffnen“ können Erweiterungsautoren umfassende Funktionen für jede beliebige Sprache erstellen. Es sind APIs vorhanden, die das Erstellen, Debuggen und die Symbolsuche für jede Datei in der Codebasis eines Benutzers unterstützen. Aktuelle Extender können vorhandene Visual Studio-Features aktualisieren, um Code zu erfassen, ohne dass Unterstützung durch Projekte oder eine Projektmappe erforderlich ist.

## <a name="an-api-without-project-systems"></a>Eine API ohne Projektsysteme

In der Vergangenheit hat Visual Studio nur Dateien in einer Projektmappe und deren Projekte mithilfe von Projektsystemen verstanden. Ein Projektsystem ist für die Funktionalität und die Benutzerinteraktionen eines geladenen Projekts verantwortlich. Es versteht, welche Dateien das Projekt enthält, und kennt die visuelle Darstellung des Projektinhalts, Abhängigkeiten von anderen Projekten und Änderungen der zugrunde liegenden Projektdatei. Durch diese Hierarchien und Funktionen arbeiten andere Komponenten im Auftrag des Benutzers. Nicht alle Codebasen werden in einer Projekt- und Projektmappenstruktur gut dargestellt. Skriptsprachen und Open-Source-Code, der in C++ für Linux geschrieben wird, sind gute Beispiele. Mit „Ordner öffnen“ bietet Visual Studio Benutzern eine neue Möglichkeit, mit ihrem Quellcode zu interagieren.

Die Ordner öffnen-APIs befinden sich unter dem Namespace `Microsoft.VisualStudio.Workspace.*` und stehen für Extender zum Generieren und Nutzen von Daten oder Aktionen im Zusammenhang mit Dateien in „Ordner öffnen“ zur Verfügung. Erweiterungen können diese APIs verwenden, um Funktionen für viele Bereiche bereitzustellen:

- [Arbeitsbereiche](workspaces.md): Der Ausgangspunkt für die Erweiterbarkeit „Ordner öffnen“ ist der Arbeitsbereich und seine APIs.
- [Dateikontexte und -aktionen](workspace-file-contexts.md): Dateispezifische Codeintelligenz, die über Dateikontexte bereitgestellt wird.
- [Indizierung](workspace-indexing.md): Erfassen und Speichern von Daten zu Arbeitsbereichen des Typs „Ordner öffnen“.
- [Sprachdienste](workspace-language-services.md): Integrieren von Sprachdiensten in Arbeitsbereiche des Typs „Ordner öffnen“.
- [Erstellen](workspace-build.md): Buildunterstützung für Arbeitsbereiche des Typs „Ordner öffnen“.

Funktionen, die die folgenden Typen verwenden, müssen neue APIs einbinden, um „Ordner öffnen“ zu unterstützen:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Feedback, Kommentare, Issues

„Ordner öffnen“ und die `Microsoft.VisualStudio.Workspace.*`-APIs befinden sich in aktiver Entwicklung. Wenn unerwartetes Verhalten auftritt, sehen Sie sich die bekannten Probleme für das betreffende Release an. Die [Entwicklercommunity](https://aka.ms/feedback/suggest?space=8) ist der empfohlene Ort für Abstimmungen und das Erstellen von Issues. Für jegliches Feedback empfehlen wir dringend eine ausführliche Beschreibung Ihres Problems. Geben Sie die Visual Studio-Version an, für die Sie entwickeln, die APIs, die Sie verwenden (sowohl die, die Sie implementiert haben, als auch die, mit dem Sie interagieren), das erwartete Ergebnis und das tatsächliche Ergebnis. Fügen Sie nach Möglichkeit ein Speicherabbild des devenv.exe-Prozesses bei. Verwenden Sie die Problemnachverfolgung von GitHub (Issues), um Feedback dazu sowie zu zugehöriger Dokumentation zu geben.

## <a name="next-steps"></a>Nächste Schritte

* [Arbeitsbereiche](workspaces.md): Erfahren Sie mehr über die Arbeitsbereich-API „Ordner öffnen“.