---
title: Optionen für C++-Projekteinstellungen
description: Hier erfahren Sie, wie Sie die Seite „VC++-Projekteinstellungen“ im Abschnitt „Projekte und Projektmappen“ verwenden, um Build- und Projekteinstellungen für C++ zu definieren, die für die Protokollierung, Leistung sowie unterstützende Dateitypen relevant sind.
ms.custom: SEO-VS-2020
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 16226cd66c2cf46d1dc46f1cb3f90dc3bad9658c
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616277"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++-Projekteinstellungen, Projekte und Projektmappen, Dialogfeld "Optionen"

In diesem Dialogfeld können Sie Build- und Projekteinstellungen für C++ definieren, die für die Protokollierung, die Leistung sowie unterstützende Dateitypen relevant sind.

## <a name="to-access-this-dialog-box"></a>So öffnen Sie das Dialogfeld

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Wählen Sie **Projekte und Projektmappen** aus, und wählen Sie dann **VC++-Projekteinstellungen** aus.

## <a name="build-logging"></a>Buildprotokollierung

 **Ja**

  Aktiviert die Generierung der Buildprotokolldatei. Durch diese Option wird die Datei "BuildLog.htm" generiert, die sich im Zwischendateiverzeichnis des Projekts befindet. Durch jedes neue Build wird die vorherige Datei "BuildLog.htm" überschrieben.

 **Nein**

  Deaktiviert die Generierung der Buildprotokolldatei.

## <a name="show-environment-in-log"></a>Umgebung in Protokoll anzeigen

 **Ja**

Listet Umgebungsvariablen in der Buildprotokolldatei auf. Diese Option gibt an, dass während der Erstellung von C++-Projekten alle Umgebungsvariablen als Echo in die Buildprotokolldatei aufgenommen werden.

 **Nein**

Schließt Umgebungsvariablen aus der Buildprotokolldatei aus.

## <a name="build-timing"></a>Buildzeitgeber

 **Ja**

  Aktiviert die Zeitnahme für das Build. Wenn diese Option ausgewählt ist, wird die Dauer der Builderstellung im Ausgabefenster ausgegeben. Weitere Informationen finden Sie unter [Ausgabefenster](../../ide/reference/output-window.md).

 **Nein**

Deaktiviert die Zeitnahme für das Build.

## <a name="maximum-concurrent-c-compilations"></a>Maximale Anzahl gleichzeitiger C++-Kompilierungen

Gibt die maximale Anzahl von CPU-Kernen an, die für parallele C++-Kompilierungen verwendet werden können.

## <a name="extensions-to-include"></a>Einzuschließende Erweiterungen

Gibt die Dateinamenerweiterungen der Dateien an, die in das Projekt portiert werden können.

## <a name="extensions-to-hide"></a>Auszublendende Erweiterungen

Gibt die Dateierweiterungen der Dateien an, die nicht im **Projektmappen-Explorer** angezeigt werden, wenn die Option **Alle Dateien anzeigen** aktiviert ist.

## <a name="build-customization-search-path"></a>Suchpfad für die Buildanpassung

Gibt die Liste der Verzeichnisse mit RULES-Dateien an, die Sie bei der Definition von Buildregeln für Projekte unterstützen.

## <a name="solution-explorer-mode"></a>Projektmappen-Explorer-Modus

**Nur Dateien im Projekt anzeigen**

Konfiguriert den **Projektmappen-Explorer** so, dass nur Dateien im Projekt angezeigt werden.

**Alle Dateien anzeigen**

Konfiguriert den **Projektmappen-Explorer** so, dass Dateien im Projekt und Dateien auf dem Datenträger im Projektordner angezeigt werden.

## <a name="enable-project-caching"></a>Aktivieren der Projektzwischenspeicherung

**Ja**

Ermöglicht das Zwischenspeichern von Projektdaten in Visual Studio, damit die zwischengespeicherten Daten beim nächsten Öffnen des Projekts abrufen werden können und Sie sie nicht erneut aus den Projektdateien berechnen müssen. Durch zwischengespeicherte Daten kann die Projektladezeit deutlich verringert werden.

**Nein**

Kein Verwenden von zwischengespeicherten Projektdaten. Analysieren Sie die Projektdateien jedes Mal, wenn das Projekt geladen wird.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen von C/C++-Programmen](/cpp/build/projects-and-build-systems-cpp)
- [Referenz zur C/C++-Erstellung](/cpp/build/reference/c-cpp-building-reference)