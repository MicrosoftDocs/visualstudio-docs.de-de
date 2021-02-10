---
title: VSInstr | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zum VSInstr-Tool. Dieses wird verwendet, um Binärdateien zu instrumentieren. Außerdem erhalten Sie Informationen zu weiteren verfügbaren VSInstr-Tooloptionen.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 476822abe665bee18d082b7187bfa657cc360d3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911649"
---
# <a name="vsinstr"></a>VSInstr
Das VSInstr-Tool wird zum Instrumentieren von Binärdateien verwendet. Es wird mithilfe der folgenden Syntax aufgerufen:

```cmd
VSInstr [/U] filename [/options]
```

 In der folgenden Tabelle werden die Optionen des VSInstr-Tools beschrieben:

|Optionen|Beschreibung|
|-------------|-----------------|
|**Help** oder **?**|Zeigt die Hilfe an.|
|**U**|Schreibt die umgeleitete Konsolenausgabe als Unicode. Dabei muss es sich um die erste angegebene Option handeln.|
|`@filename`|Gibt den Namen einer Antwortdatei an, die eine Befehlsoption pro Zeile enthält.  Verwenden Sie keine Anführungszeichen.|
|**OutputPath** `:path`|Gibt ein Zielverzeichnis für das instrumentierte Image an. Wenn kein Ausgabepfad angegeben wird, wird die ursprüngliche Binärdatei umbenannt, indem „Orig“ an den Dateinamen im gleichen Verzeichnis angefügt wird, und es wird eine Kopie der Binärdatei instrumentiert.|
|**Exclude:** `funcspec`|Gibt eine Funktionsspezifikation zum Ausschließen von der Instrumentierung durch Überprüfungen an. Dies ist hilfreich, wenn die Profilerstellung zum Einfügen der Überprüfung in einer Funktion unvorhersehbare oder unerwünschte Ergebnisse verursacht.<br /><br /> Verwenden Sie keine **Exclude**- und **Include**-Optionen, die sich auf Funktionen in der gleichen Binärdatei beziehen.<br /><br /> Sie können mehrere Funktionsspezifikationen mit separaten **Exclude**-Optionen angeben.<br /><br /> `funcspec` wird folgendermaßen definiert:<br /><br /> [namespace\<separator1>] [class\<separator2>]function<br /><br /> \<separator1> entspricht bei nativem Code `::` und bei verwaltetem Code `.`.<br /><br /> \<separator2> entspricht immer `::`.<br /><br /> **Exclude** wird mit Code Coverage unterstützt.<br /><br /> Das Platzhalterzeichen \* wird unterstützt. Verwenden Sie beispielsweise Folgendes, um alle Funktionen in einem Namespace auszuschließen:<br /><br /> MyNamespace::\*<br /><br /> Sie können **VSInstr /DumpFuncs** verwenden, um die vollständigen Namen von Funktionen in der angegebenen Binärdatei aufzulisten.|
|**Include:** `funcspec`|Gibt eine Funktionsspezifikation in einer Binärdatei an, um mit Überprüfungen zu instrumentieren. Alle anderen Funktionen in den Binärdateien werden nicht instrumentiert.<br /><br /> Sie können mehrere Funktionsspezifikationen mit separaten **Include**-Optionen angeben.<br /><br /> Verwenden Sie keine **Include**- und **Exclude**-Optionen, die sich auf Funktionen in der gleichen Binärdatei beziehen.<br /><br /> **Include** wird mit Code Coverage nicht unterstützt.<br /><br /> `funcspec` wird folgendermaßen definiert:<br /><br /> [namespace\<separator1>] [class\<separator2>]function<br /><br /> \<separator1> entspricht bei nativem Code `::` und bei verwaltetem Code `.`.<br /><br /> \<separator2> entspricht immer `::`.<br /><br /> Das Platzhalterzeichen \* wird unterstützt. Verwenden Sie beispielsweise Folgendes, um alle Funktionen in einem Namespace einzuschließen:<br /><br /> MyNamespace::\*<br /><br /> Sie können **VSInstr /DumpFuncs** verwenden, um die vollständigen Namen von Funktionen in der angegebenen Binärdatei aufzulisten.|
|**DumpFuncs**|Listet die Funktionen innerhalb des angegebenen Images auf. Es wird keine Instrumentierung durchgeführt.|
|**ExcludeSmallFuncs**|Schließt kleine Funktionen, also kurze Funktionen, die keine Funktionsaufrufe ausführen, aus der Instrumentierung aus. Die Option **ExcludeSmallFuncs** bietet bei weniger Instrumentierungsoverhead eine daher verbesserte Instrumentierungsgeschwindigkeit.<br /><br /> Der Ausschluss kleiner Funktionen reduziert auch die Größe der *VSP-Datei* und den Zeitaufwand für die Analyse.|
|**Mark:** {**Before**\|**After**\|**Top**\|**Bottom**}`,funcname,markid`|Fügt eine Profilmarkierung (ein Bezeichner, der zum Einschränken der Daten in Berichten verwendet wird) ein, die Sie zum Identifizieren des Beginns oder des Endes eines Datenbereichs in der VSP-Berichtsdatei verwenden können.<br /><br /> **Before**: Unmittelbar vor dem Zielfunktionseintrag.<br /><br /> **After**: Unmittelbar nach dem Zielfunktionsausgang.<br /><br /> **Top**: Unmittelbar nach dem Zielfunktionseintrag.<br /><br /> **Bottom**: Unmittelbar vor jeder Rückgabe in der Zielfunktion.<br /><br /> `funcname`: Name der Zielfunktion<br /><br /> `Markid`: Eine positive ganze Zahl (lang), die als Bezeichner der Profilmarkierung verwendet werden soll.|
|**Coverage**|Führt die Coverage-Instrumentierung durch. Sie kann nur mit den folgenden Optionen verwendet werden: **Verbose**, **OutputPath**, **Exclude** und **Logfile**.|
|**Verbose**|Die **Verbose**-Option wird verwendet, um detaillierte Informationen zum Instrumentierungsprozess anzuzeigen.|
|**NoWarn** `[:[Message Number[;Message Number]]]`|Alle oder bestimmte Warnungen unterdrücken.<br /><br /> `Message Number`: Warnnummer. Wenn `Message Number` ausgelassen wird, werden alle Warnungen unterdrückt.<br /><br /> Weitere Informationen finden Sie unter [VSInstr-Warnungen](../profiling/vsinstr-warnings.md).|
|**Control:** `{` **Thread** \| **Process** \| **Global** `}`|Gibt die Profilerstellungsebene der folgenden VSInstr-Steuerungsoptionen für die Datensammlung an:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread**: Gibt die Steuerungsfunktionen für die Datensammlung auf Thread-Ebene an. Die Profilerstellung wird nur für den aktuellen Thread gestartet oder angehalten. Der Profilerstellungsstatus anderer Threads ist nicht betroffen. Der Standardwert ist Thread.<br /><br /> **Process**: Gibt die Steuerungsfunktionen für die Profildatensammlung auf Prozessebene an. Die Profilerstellung wird für alle Threads im aktuellen Prozess gestartet oder angehalten. Der Profilerstellungsstatus anderer Prozesse ist nicht betroffen.<br /><br /> **Global**: Gibt die Steuerungsfunktionen für die Datensammlung auf globaler Ebene (prozessübergreifend) an.<br /><br /> Wenn Sie die Profilerstellungsebene nicht angeben, tritt ein Fehler auf.|
|**Start:** `{` **Inside** \| **Outside** `},funcname`|Beschränkt die Datensammlung auf die Zielfunktion und die untergeordneten Funktionen, die von dieser Funktion aufgerufen werden.<br /><br /> **Inside**: Fügt die Funktion „StartProfile“ direkt nach dem Eintrag zur Zielfunktion ein. Fügt die Funktion „StopProfile“ direkt vor jeder Rückgabe in der Zielfunktion ein.<br /><br /> **Outside**: Fügt die Funktion „StartProfile“ direkt vor jedem Aufruf zur Zielfunktion ein. Fügt die Funktion „StopProfile“ direkt vor nach jedem Aufruf zur Zielfunktion ein.<br /><br /> `funcname`: Der Name der Zielfunktion.|
|**Suspend:** `{` **Inside** \| **Outside** `},funcname`|Beschränkt die Datensammlung für die Zielfunktion und die untergeordneten Funktionen, die von der Funktion aufgerufen werden.<br /><br /> **Inside**: Fügt die Funktion „SuspendProfile“ direkt nach dem Eintrag zur Zielfunktion ein. Fügt die Funktion „ResumeProfile“ direkt vor jeder Rückgabe in der Zielfunktion ein.<br /><br /> **Outside**: Fügt die Funktion „SuspendProfile“ direkt vor dem Eintrag zur Zielfunktion ein. Fügt die Funktion „ResumeProfile“ direkt nach dem Ausgang der Zielfunktion ein.<br /><br /> `funcname`: Name der Zielfunktion.<br /><br /> Wenn die Zielfunktion eine „StartProfile“-Funktion enthält, wird die Funktion „SuspendProfile“ vor dieser eingefügt. Wenn die Zielfunktion eine „StopProfile“-Funktion enthält, wird die Funktion „ResumeProfile“ nach dieser eingefügt.|
|**StartOnly:** `{` **Before** \| **After** \| **Top** \| **Bottom** `},funcname`|Startet die Datensammlung während einer Profilerstellung. Fügt die StartProfile-API-Funktion an der angegebenen Position ein.<br /><br /> **Before**: Unmittelbar vor dem Zielfunktionseintrag.<br /><br /> **After**: Unmittelbar nach dem Zielfunktionsausgang.<br /><br /> **Top**: Unmittelbar nach dem Zielfunktionseintrag.<br /><br /> **Bottom**: Unmittelbar vor jeder Rückgabe in der Zielfunktion.<br /><br /> `funcname`: Name der Zielfunktion.|
|**StopOnly:** {**Before**\|**After**\|**Top**\|**Bottom**}`,funcname`|Stoppt die Datensammlung während einer Profilerstellung. Fügt die „StopProfile“-Funktion an der angegebenen Position ein.<br /><br /> **Before**: Unmittelbar vor dem Zielfunktionseintrag.<br /><br /> **After**: Unmittelbar nach dem Zielfunktionsausgang.<br /><br /> **Top**: Unmittelbar nach dem Zielfunktionseintrag.<br /><br /> **Bottom**: Unmittelbar vor jeder Rückgabe in der Zielfunktion.<br /><br /> `funcname`: Name der Zielfunktion.|
|**SuspendOnly:** {**Before**\|**After**\|**Top**\|**Bottom**}`,funcname`|Stoppt die Datensammlung während einer Profilerstellung. Fügt die „SuspendProfile“-API an der angegebenen Position ein.<br /><br /> **Before**: Unmittelbar vor dem Zielfunktionseintrag.<br /><br /> **After**: Unmittelbar nach dem Zielfunktionsausgang.<br /><br /> **Top**: Unmittelbar nach dem Zielfunktionseintrag.<br /><br /> **Bottom**: Unmittelbar vor jeder Rückgabe in der Zielfunktion.<br /><br /> `funcname`: Name der Zielfunktion.<br /><br /> Wenn die Zielfunktion eine „StartProfile“-Funktion enthält, wird die Funktion „SuspendProfile“ vor dieser eingefügt.|
|**ResumeOnly:** {**Before**\|**After**\|**Top**\|**Bottom**}`,funcname`|Startet die Datensammlung während einer Profilerstellung oder setzt sie fort.<br /><br /> Wird normalerweise dazu verwendet, die Profilerstellung zu starten, nachdem die Option **SuspendOnly** die Profilerstellung beendet hat. Fügt eine ResumeProfile-API an der angegebenen Position ein.<br /><br /> **Before**: Unmittelbar vor dem Zielfunktionseintrag.<br /><br /> **After**: Unmittelbar nach dem Zielfunktionsausgang.<br /><br /> **Top**: Unmittelbar nach dem Zielfunktionseintrag.<br /><br /> **Bottom**: Unmittelbar vor jeder Rückgabe in der Zielfunktion.<br /><br /> `funcname`: Name der Zielfunktion.<br /><br /> Wenn die Zielfunktion eine „StopProfile“-Funktion enthält, wird die Funktion „ResumeProfile“ nach dieser eingefügt.|

## <a name="see-also"></a>Siehe auch
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [VSInstr-Warnungen](../profiling/vsinstr-warnings.md)
- [Leistungsberichtansichten](../profiling/performance-report-views.md)
