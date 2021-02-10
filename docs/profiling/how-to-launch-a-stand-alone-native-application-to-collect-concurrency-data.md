---
title: 'Profilerbefehlszeile: Öffnen der nativen Client-App und Abrufen von Daten zur Parallelität'
description: Hier erfahren Sie, wie Sie die Befehlszeilentools für die Profilerstellungstools von Visual Studio verwenden, um eine eigenständige native Client-App zu starten und Parallelitätsdaten für Prozesse und Threads zu sammeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: da71c5bb714a50c70cbefcd2a2987a48c14eb4b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928975"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Vorgehensweise: Starten einer nativen, eigenständigen Anwendung mit dem Profiler zum Sammeln von Parallelitätsdaten über die Befehlszeile
In diesem Thema wird beschrieben, wie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools eigenständige native Anwendungen gestartet und Parallelitätsdaten zu Prozessen und Threads erfasst werden.

 Eine Profilerstellungssitzung besteht aus folgenden Teilen:

- Starten der Anwendung mit dem Profiler

- Steuern der Datenauflistung

- Beenden der Profilerstellungssitzung

> [!NOTE]
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

## <a name="start-the-application-with-the-profiler"></a>Starten der Anwendung mit dem Profiler
 Wenn Sie die Zielanwendung mit dem Profiler starten möchten, verwenden Sie die Optionen [VSPerfCmd.exe](../profiling/vsperfcmd.md) **/start** und **/launch**, um den Profiler zu initialisieren und die Anwendung zu starten. Sie können **/start** und **/launch** sowie die zugehörigen Optionen angeben. Sie können auch die Option **/globaloff** hinzufügen, um die Datensammlung beim Starten der Zielanwendung anzuhalten. Zum Starten der Datensammlung verwenden Sie anschließend **/globalon**.

#### <a name="to-start-an-application-with-the-profiler"></a>Starten einer Anwendung mit dem Profiler

1. Geben Sie an einer Eingabeaufforderung folgenden Befehl ein:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]

     Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der Option **/start:concurrency** verwenden.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.|

2. Starten Sie die Zielanwendung, indem Sie folgendes eingeben:

     **VSPerfCmd**  [/launch](../profiling/launch.md) **:** `AppName` [`Options`]

     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der Option **/launch** verwenden.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:** `Arguments`|Gibt eine Zeichenfolge mit den Befehlszeilenargumenten an, die an die Zielanwendung übergeben werden sollen.|
    |[/console](../profiling/console.md)|Startet die Ziel-Befehlszeilenanwendung in einem separaten Fenster.|
    |[/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn die Anwendung mehr als eine Laufzeitversion der CLR lädt.|

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei über *VSPerfCmd.exe*-Optionen starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Mit den Optionspaaren in der folgenden Tabelle wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess-ID (`PID`) oder des Prozessnamens (*ProcName*) angegeben ist. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein Prozess angegeben ist) beendet.|

- Sie können auch die Option **VSPerfCmd.exe**[/mark](../profiling/mark.md) verwenden, um eine Profilmarkierung in die Datendatei einzufügen. Der Befehl **/mark** fügt einen Bezeichner, einen Zeitstempel und eine optionale benutzerdefinierte Textzeichenfolge hinzu. Mit Markierungen können die Daten in Profilerberichten und Datenansichten gefiltert werden.

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen. Sie können die Erfassung von Parallelitätsdaten beenden, indem Sie die profilierte Anwendung schließen oder indem Sie die Option **VSPerfCmd /detach** aufrufen. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Trennen Sie den Profiler von der Zielanwendung, indem Sie die Anwendung schließen oder folgenden Befehl eingeben:

     **VSPerfCmd /detach**

2. Beenden Sie den Profiler, indem Sie den folgenden Befehl an der Eingabeaufforderung eingeben:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)