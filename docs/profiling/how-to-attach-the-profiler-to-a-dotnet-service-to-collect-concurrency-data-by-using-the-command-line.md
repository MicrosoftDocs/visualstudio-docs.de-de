---
title: Anfügen eines Profilers an .NET zum Sammeln von Parallelitätsdaten (Befehlszeile)
titleSuffix: ''
description: Verwenden Sie die Visual Studio Profilerstellungstools, um den Profiler an einen .NET Framework-Dienst anzufügen und Parallelitätsdaten für Prozesse und Threads mithilfe der Samplingmethode abzurufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4c12db2be72e1435c840bf9d85e681536a5e2202
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958842"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Vorgehensweise: Anfügen des Profilers an einen .NET-Dienst zum Sammeln von Parallelitätsdaten über die Befehlszeile
In diesem Artikel wird beschrieben, wie der Profiler mithilfe der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools an einen .NET Framework-Dienst angefügt wird und wie Parallelitätsdaten zu Prozessen und Threads mit der Samplingmethode erfasst werden.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

 Um Nebenläufigkeitsdaten zu sammeln, müssen Sie den Profiler an den Dienstprozess anfügen. Während der Profiler an den Dienst angefügt ist, können Sie die Datensammlung anhalten und fortsetzen. Der Profiler darf nicht mehr an den Dienst angefügt sein und muss explizit beendet werden, um eine Profilerstellungssitzung zu beenden. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.

## <a name="attach-the-profiler"></a>Anfügen des Profilers

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>So fügen Sie den Profiler an einen .NET Framework-Dienst an

1. Installieren Sie den Dienst.

2. Öffnen Sie ein Befehlsfenster.

3. Initialisieren Sie die Umgebungsvariablen für die Profilerstellung. Typ:

     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **/globalsampleon** [ **/samplelineoff**]

    - **/globalsampleon** aktiviert das Sampling.

    - **/samplelineoff** deaktiviert die Zuweisung gesammelter Daten zu bestimmten Quellcodezeilen. Wenn diese Option angegeben wird, werden Daten nur Funktionen zugewiesen.

4. Starten Sie den Computer neu.

5. Starten Sie den Profiler. Typ:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]

     Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start** verwenden.

    > [!NOTE]
    > Die Option **/user** und **/crosssession** sind normalerweise für Dienste erforderlich.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte **Prozesse** in der Spalte **Benutzername** des Windows Task-Managers aufgeführt.|
    |[/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn der Dienst in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte **Prozesse** in der Spalte **Sitzungs-ID** des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt.|

6. Starten Sie den Dienst bei Bedarf.

7. Fügen Sie den Profiler an den Dienst an. Typ:

     **VSPerfCmd /attach:** `PID` [[/targetclr](../profiling/targetclr.md) **:** `Version`]

    - `PID` gibt die ID oder den Namen des Dienstprozesses an. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.

    - **targetclr:** `Version` gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere Runtimeversionen geladen wurden. Dies ist optional.

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Während der Dienst ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit *VSPerfCmd.exe*-Optionen starten und beenden. Durch die Steuerung der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Die folgenden Optionenpaare **VSPerfCmd** starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |**/attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess-ID oder des Prozessnamens angegeben ist. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist) beendet.|

- Sie können auch die Option **VSPerfCmd.exe**[/mark](../profiling/mark.md) verwenden, um eine Profilmarkierung in die Datendatei einzufügen. Der Befehl **/mark** fügt einen Bezeichner, einen Zeitstempel und eine optionale benutzerdefinierte Textzeichenfolge hinzu. Mit Markierungen können die Daten in Profilerberichten und Datenansichten gefiltert werden. Die folgenden Paare von VSPerfCmd-Optionen starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen. Sie können das Sammeln von Daten einer Anwendung, für die mithilfe der Parallelitätsmethode ein Profil erstellt wird, beenden. Beenden Sie hierzu den Dienst, oder rufen Sie die Option **VSPerfCmd /detach** auf. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Der Befehl **VSPerfClrEnv /globaloff** löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:

    - Beenden Sie den Dienst.

         - oder -

    - Geben Sie **VSPerfCmd /detach** ein.

2. Schließen Sie den Profiler. Typ:

     **VSPerfCmd**  [Shutdown](../profiling/shutdown.md)
