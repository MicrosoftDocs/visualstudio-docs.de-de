---
title: VSPerfReport | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über das Befehlszeilentool VSPerfReport, das zum Erstellen von Berichten mithilfe von Profilerstellungs-Datendateien aus den Visual Studio Profilerstellungstools verwendet wird.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ed3ba5453976e3f3976aba43bc296c040a86b7a5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719772"
---
# <a name="vsperfreport"></a>VSPerfReport
Das VSPerfReport-Befehlszeilentool wird zum Erstellen von Berichten mithilfe von Profilerstellungs-Datendateien aus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools verwendet. Das Standardberichtsformat ist eine *CSV-Datei*.

 VSPerfReport verwendet die folgende Syntax:

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 Bitte beachten Sie, dass es sich bei `filename` um eine gültige *VSP-* oder *VSPS-Datei* handeln muss.

 Das VSPerfReport-Befehlszeilentool wird ebenfalls verwendet, um *VSP-* oder *VSPS-Dateien* miteinander zu vergleichen. Verwenden Sie die folgende Syntax, um einen Unterschiedebericht („Diff“) zu generieren:

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 Es muss sich bei `vspfilename1 and vspfilename2` um gültige *VSP-* oder *VSPS-Dateien* handeln.

## <a name="symbol-files"></a>Symboldateien
 Das VSPerfReport-Befehlszeilentool benötigt Zugriff auf die Symboldateien (.pdb) der profilierten Komponenten und die Windows-Systemdateien, um Symbolinformationen wie Funktionsnamen und Zeilennummern anzuzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).

## <a name="general-report-options"></a>Allgemeine Berichtsoptionen
 In der folgenden Tabelle werden die allgemeinen Optionen zur Berichtsformatierung beschrieben sowie die Optionen, die die Daten auswählen, die gemeldet werden sollen.

|Optionen|Beschreibung|
|-------------|-----------------|
|**U**|Die Berichtsausgabe und die umgeleitete Konsolenausgabe werden als Unicode geschrieben. Es muss sich um die erste angegebene Option handeln.|
|**Summary:**[*types*]|Erstellt mindestens einen Berichtstyp<br /><br /> -   `All` – alle Berichtstypen werden generiert<br />-   `CallerCallee` – über- und untergeordnete Beziehungen zwischen Funktionen<br />-   `Function` – aufgerufene Funktionen<br />-   `CallTree` – Hierarchien der aufgerufenen Funktionen<br />-   `Counter` – alle Markierungen und Windows-Leistungsindikatorwerte<br />-   `Ip` – Anweisungen mit Profilen<br />-   `Life` – Lebensdauer von zugeordneten Objekten (verfügbar, wenn Speicherbelegungsdaten erfasst wurden)<br />-   `Line` – Profildaten von Quellcodezeilen<br />-   `Header` – der Bericht enthält Dateiheaderinformationen<br />-   `Mark` – alle Markierungen<br />-   `Module` – Module mit Profilen<br />-   `Process` – Prozesse mit Profilen<br />-   `Thread` – Threads mit Profilen<br />-   `Type` – zugeordnete Typen<br />-   `Contention` – Ressourcenkonflikte<br />-   `RuleWarnings` – Probleme mit Leistungsregeln<br />-   `ETW` – alle während der Profilerstellungsausführung erfassten Ereignisse der Ereignisablaufverfolgung für Windows (ETW). Die ETL-Datendatei muss sich am ursprünglichen Standort oder in dem Verzeichnis mit der VSP- oder VSPS-Datei befinden.|
|**Xml**|Ausgabebericht im XML-Format|
|**CallTrace**|Erstellt eine Liste mit Funktionseinträgen und beendet ETW-Ereignisse und Markierungen|
|**ClearPackedSymbols**|Entfernt zuvor eingebettete Symbole aus einer Profilerdatendatei. Führen Sie diesen Befehl aus, bevor Sie PackSymbols ein zweites Mal ausführen.|
|**SymbolPath:** `path`|Gibt mindestens einen Suchpfad oder Symbolserver an, die Symbole für die Profilerdatendatei enthalten.|
|**DebugSymPath**|Listet die Speicherorte auf, die nach den Symbolen durchsucht werden, und gibt an, ob diese gefunden werden. Diese Option ist nützlich für das Beheben von Problemen mit der Symbolauflösung.|
|**PackSymbols**|Speichert Symbole in der Profilerdatendatei (VSP), damit keine Symboldateien (*PDB*) für die Analyse benötigt werden.|
|**Ausgabe:** *Pfad*|*Dateiname*|Gibt einen alternativen Speicherort für die generierten Berichtsdateien an. Standardmäßig werden Berichte im aktuellen Verzeichnis erstellt.|
|**SummaryFile**|Analysieren und speichern Sie die analysierten Informationen in einer VSPS-Zusammenfassungsdatei|
|**PrintMarks**|Zeigt die Namen und Zeitstempel sämtlicher Markierungen in einer Berichtsdatei an.|
|**?**|Zeigt Nutzungsinformationen an.|
|**NoLogo**|Blendet die Versionsinformationen aus, während der Bericht ausgeführt wird.|
|**UserRulesDirectory**|Gibt ein Verzeichnis an, das benutzerdefinierte Leistungsregeln enthält (noch nicht implementiert).|

## <a name="filter-options"></a>Filteroptionen
 In der folgenden Tabelle werden Optionen beschrieben, über die Sie verfügbare Daten filtern können.

|Optionen|Beschreibung|
|-------------|-----------------|
|**JustMyCode**[ **:** [`caller`][,`callee`]]|Zeigt nur Funktionsaufrufe der Benutzeranwendung an und blendet Systemaufrufe aus<br /><br /> – Keine Parameter: blendet alle Systemfunktionen aus<br />-   `caller` – zeigt eine Ebene von Systemfunktionen an, die Anwendungsfunktionen aufrufen<br />-   `callee` – zeigt eine Ebene von Systemfunktionen an, die von Benutzeranwendungsfunktionen aufgerufen werden|
|**StartTime:** [*Wert*]|Zeigt nur Daten an, die nach dem Wert erfasst werden (in Millisekunden)|
|**EndTime:** [*Wert*]|Zeigt nur Daten an, die vor dem Wert erfasst werden (in Millisekunden)|
|**FilterFile:** `VSPFFile`|Gibt den Speicherort einer Filterdatei an, die aus dem Visual Studio-Fenster „Leistungsbericht“ generiert wurde|
|**MsFilter:** [*Startzeit,Dauer*]|Zeigt nur Daten ab `starttime` bis zur Länge von `duration` (in Millisekunden) an|
|**Process:** [*PID*]|Zeigt nur Daten aus dem angegebenen Prozess an|
|**Thread:** [*Thread-ID*]|Zeigt nur Daten aus dem angegebenen Thread an|
|**Thread:** [*Thread-ID,Prozess-ID*]|Zeigt nur Daten aus dem angegebenen Thread an, der dem angegebenen Prozess zugeordnet ist|

## <a name="difference-report-options"></a>Optionen für Unterschiedeberichte
 In der folgenden Tabelle werden die Optionen zum Vergleichen von Berichtsdateien beschrieben.

|Optionen|Beschreibung|
|-------------|-----------------|
|**Diff**  `vspfile1 vspfile2`|Vergleicht zwei Berichtsdateien (*VSP-* oder *VSPS-Dateien*). Optionen zur Zusammenfassung werden bei der Verwendung der „Diff“-Option ignoriert.|
|**Diff:**[*Wert*]|Bei Werten, die unter diesem Schwellenwert liegen, wird der Unterschied zwischen zwei Werten ignoriert. Außerdem werden keine neuen Daten mit Werten angezeigt, die unter diesem Schwellenwert legen.|
|**DiffTable:** [*Tabellenname*]|Verwendet die angegebene Tabelle zum Vergleichen von Dateien. Standardmäßig wird die Funktionstabelle verwendet.|
|**DiffColumn:** [*Spaltenname*]|Verwendet diese angegebene Spalte zum Vergleichen von Werten. Standardmäßig handelt es sich dabei um die Spalte mit dem prozentualen Anteil exklusiver Stichproben.|
|**QueryDiffTables**|Listet die gültigen Tabellen und Spalten für die beiden bereitgestellten Berichtsdateien auf.|

## <a name="see-also"></a>Siehe auch
- [Leistungsberichtansichten](../profiling/performance-report-views.md)
