---
title: VSPerfMon | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ee2423f552c6931b0c8b62181dc44186053c9460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329974"
---
# <a name="vsperfmon"></a>VSPerfMon
Sie können das VSPerfMon-Tool verwenden, um Leistungsdaten für eine Anwendung zu sammeln. Das Tool wird üblicherweise über *VSPerfCmd.exe* gestartet. VSPerfMon zeigt zusätzliche Informationen zum Anfügen oder Trennen eines Prozesses an, was bei Verwendung des VSPerfCmd-Tools nicht verfügbar ist. Um diese Informationen anzuzeigen, starten Sie VSPerfMon in einem separaten Fenster. Zum Aufrufen von VSPerfMon verwenden Sie die folgende Syntax:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 In der folgenden Tabelle werden die Optionen des VSPerfMon-Tools beschrieben:

|Optionen|Beschreibung|
|-------------|-----------------|
|**U**|Die umgeleitete Konsolenausgabe wird als Unicode geschrieben.  Dabei muss es sich um die erste angegebene Option handeln.|
|**OUTPUT:** `<` *Dateiname* `>`|Leitet die Ausgabe zum angegebenen Dateinamen um.|
|**TRACE**|Startet den Systemmonitor für die instrumentierte Profilerstellung.|
|**SAMPLE**|Startet den Systemmonitor für die Sampling-Profilerstellung.|
|**COVERAGE**|Startet den Systemmonitor für die Code Coverage-Sammlung.|
|**CONCURRENCY**|Startet den Systemmonitor für die Ressourcenkonflikt-Profilerstellung.|
|**USER:** `[` *Domäne* `\]` *Benutzername*|Ermöglicht dem Client Zugriff auf den Systemmonitor vom angegebenen Konto aus.|
|**CROSSSESSION**|Ermöglicht die sitzungsübergreifende Profilerstellung.|
|**COUNTER** `:cfg`|Wenn die Instrumentierungs-Profilerstellungsmethode (TRACE) verwendet wird, wird ein CPU-Indikator angegeben, der an jedem Instrumentierungspunkt gesammelt werden soll. Sie können mehrere Indikatordaten sammeln, indem Sie mehrere Indikatoroptionen angeben.<br /><br /> Verwenden Sie zum Angeben der Indikatordaten (*cfg*) die folgende Syntax:<br /><br /> **CounterName** [ **,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** ist der Name eines Indikators, der durch den VSPerfCmd-Befehl „/QueryCounters“ zurückgegeben wird.<br />-   **Reload** ist das Samplingintervall des Indikatorereignisses. Verwenden Sie *Reload* nicht mit der Instrumentierungsmethode.<br />- Wenn angegeben, ersetzt **FriendlyName** **CounterName** in den Spaltennamen von Berichten der Profilerstellungstools.|
|**WINCOUNTER** `:path`|Gibt einen Windows-Leistungsindikator an, der in Markierungsdaten enthalten sein soll. `path` ist eine Windows-Leistungsindikator-Zeichenfolge im PDH-Indikatorpfadformat. Zum Beispiel:<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|
|**AUTOMARK** `:n`|Gibt das Zeitintervall (in Millisekunden) zwischen automatischen Markierungen an, wenn Sie /WINCOUNTER verwenden. Wird auf die nächsten 500 ms gerundet.<br /><br /> Verwenden Sie 0 zum Deaktivieren von automatischen Markierungen. (Standard = 500 ms, falls nicht angegeben)|

## <a name="see-also"></a>Siehe auch
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Leistungsberichtansichten](../profiling/performance-report-views.md)
