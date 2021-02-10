---
title: Anfügen eines Profilers an .NET zum Sammeln von Parallelitätsdaten
description: Hier erfahren Sie, wie Sie Befehlszeilentools der Visual Studio Profilerstellungstools zum Anfügen des Profilers an eine aktuell ausgeführte .NET Framework-App verwenden, um Parallelitätsdaten für Prozesse und Threads abzurufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: f3eb5fbed055ef79595947954f86159b9cb2efc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958907"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>Vorgehensweise: Anfügen des Profilers an eine eigenständige .NET Framework-Anwendung zum Sammeln von Parallelitätsdaten über die Befehlszeile
In diesem Artikel wird beschrieben, wie der Profiler mithilfe der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools an eine ausgeführte eigenständige .NET Framework-(Client-)Anwendung angefügt wird und wie Parallelitätsdaten zu Prozessen und Threads gesammelt werden.

> [!NOTE]
> Informationen zum Pfad zu den Profilerstellungstools finden Sie unter [Exemplarische Vorgehensweise: Verwenden von Profiler-APIs](../profiling/walkthrough-using-profiler-apis.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads für Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

 Während der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen. Der Profiler darf nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden, um eine Profilerstellungssitzung zu beenden.

## <a name="attach-the-profiler"></a>Anfügen des Profilers

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>So fügen Sie den Profiler an eine aktive .NET Framework-Anwendung an

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Starten Sie den Profiler. Typ:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]

     Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:concurrency** verwenden.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.|

3. Starten Sie die Zielanwendung auf die gewohnte Weise.

4. Fügen Sie den Profiler an die Zielanwendung an. Typ:

     **VSPerfCmd /attach:** `PID` [ **/lineoff**] [ **/targetclr:** `Version`]

    - `PID` gibt die Prozess-ID der Zielanwendung an. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.

    - [/lineoff](../profiling/lineoff.md) deaktiviert die Erfassung der Zeilennummerndaten.

    - [/targetclr](../profiling/targetclr.md) **:** `Version` gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere Runtimeversionen geladen wurden. Dies ist optional.

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit Option *VSPerfCmd.exe* starten und beenden. Durch die Steuerung der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Mit den folgenden *VSPerfCmd.exe*-Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess-ID (`PID`) oder des Prozessnamens („ProcName“) angegeben ist. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist) beendet.|

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen. Sie können das Sammeln von Daten einer Anwendung, für die mithilfe der Parallelitätsmethode ein Profil erstellt wird, beenden. Schließen Sie dazu die Anwendung, oder rufen Sie die Option **VSPerfCmd /detach** auf. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /off** werden die Umgebungsvariablen für die Profilerstellung gelöscht.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:

    - Geben Sie **VSPerfCmd /detach** ein.

         - oder -

    - Schließen Sie die Zielanwendung.

2. Schließen Sie den Profiler. Typ:

     VSPerfCmd[/shutdown](../profiling/shutdown.md)
