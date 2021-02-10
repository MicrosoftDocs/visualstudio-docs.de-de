---
title: Anfügen eines Profilers an eine eigenständige .NET-App, Abrufen der App-Statistiken
description: Hier erfahren Sie, wie Sie mit Befehlszeilentools der Visual Studio Profilerstellungstools den Profiler an eine aktuell ausgeführte eigenständige .NET Framework-(Client-)Anwendung anfügen und Statistiken abrufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 52a1e52590073c48f0386c5d174eec8193f1518d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958920"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Vorgehensweise: Anfügen des Profilers an eine eigenständige .NET Framework-Anwendung und Sammeln von Anwendungsdaten über die Befehlszeile
In diesem Artikel wird beschrieben, wie Sie die Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools verwenden, um den Profiler an eine aktive eigenständige .NET Framework-(Client-)Anwendung anzufügen und mithilfe der Samplingmethode Leistungsstatistiken zu sammeln.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.
>
> Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools. Siehe [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Um Leistungsdaten von einer .NET Framework-Anwendung zu erfassen, müssen Sie vor dem Starten der Zielanwendung die entsprechenden Umgebungsvariablen initialisieren. Wenn der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.

 Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Profilerstellungssitzung zu entfernen.

## <a name="attach-the-profiler"></a>Anfügen des Profilers

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>So fügen Sie den Profiler an eine aktive .NET Framework-Anwendung an

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Initialisieren Sie die Umgebungsvariablen für die Profilerstellung. Typ:

    **VSPerfClrEnv /sampleon** [ **/samplelineoff**]

   - Die Option **/samplelineoff** deaktiviert die Erfassung der Quellcode-Zeilennummerdaten.

3. Starten Sie den Profiler. Typ:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - Mit der Option [/start](../profiling/start.md) **:sample** wird der Profiler initialisiert.

   - Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:sample** verwenden.

   | Option | Beschreibung |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Gibt die optionale Domäne und den Benutzernamen des Kontos an, das den profilierten Prozess besitzt. Diese Option ist nur erforderlich, wenn die profilierte Anwendung mit einem anderen Benutzer als dem angemeldeten Benutzer gestartet wurde. |
   | [/crosssession](../profiling/crosssession.md) | Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt. |

4. Starten Sie die Zielanwendung ggf. in der üblichen Weise.

5. Fügen Sie den Profiler an die Zielanwendung an. Typ:

    **VSPerfCmd /attach:** {`PID`&#124;`ProcessName`} [`Sample Event`] [ **/targetclr:** `Version`]

   - `PID` gibt die Prozess-ID der Zielanwendung an. `ProcessName` gibt den Namen des Prozesses an. Beachten Sie, dass unvorhersehbare Ergebnissen ausgegeben werden können, wenn Sie `ProcessName` angeben und mehrere Prozesse mit dem gleichen Namen ausgeführt werden. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere Runtimeversionen geladen wurden. Dies ist optional.

   - Standardmäßig wird alle 10.000.000 nicht angehaltene Prozessortaktzyklen ein Sampling der Leistungsdaten durchgeführt. Dies entspricht bei einem 1-GHz-Prozessor etwa einem Mal alle 10 Sekunden. Sie können eine der folgenden Optionen angeben, um das Taktzyklusintervall zu ändern oder um ein anderes Samplingereignis anzugeben. [/targetclr](../profiling/targetclr.md) **:** `Version` gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere Laufzeitversionen geladen wurden. Dies ist optional.

   |Samplingereignis|Beschreibung|
   |-|-|
   |[/timer](../profiling/timer.md) **:** `Interval`|Ändert das Samplingintervall auf die Anzahl der mit `Interval` angegebenen nicht angehaltenen Taktzyklen.|
   |[/pf](../profiling/pf.md) [ **:** `Interval`]|Ändert das Samplingereignis in Seitenfehler. Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Seitenfehler zwischen den Samplings angegeben. Der Standardwert ist 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [ **:** `Interval`]|Ändert das Samplingereignis in Systemaufrufe des Prozesses an den Betriebssystem-Kernel (syscalls). Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Aufrufe zwischen den Samplings angegeben. Der Standardwert ist 10.|
   |[/counter](../profiling/counter.md) **:** `Config`|Ändert das Samplingereignis auf den Prozessorleistungsindikator und das Samplingintervall in das in `Config` angegebene Intervall.|

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Profiler-Datendatei mit Optionen *VSPerfCmd.exe* starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den Prozess, der von `PID` angegeben wird, gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der `PID` oder des Prozessnamens (ProcName) angegeben wurde. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist) beendet.|

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von allen profilierten Prozessen getrennt und explizit beendet werden. Den Profiler können Sie von einer Anwendung trennen, für die ein Profil mit der Samplingmethode erstellt wurde, indem Sie die Anwendung schließen oder die Option **VSPerfCmd /detach** aufrufen. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /off** werden die Umgebungsvariablen für die Profilerstellung gelöscht.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:

    - Geben Sie **VSPerfCmd /detach** ein.

         - oder -

    - Schließen Sie die Zielanwendung.

2. Schließen Sie den Profiler. Typ:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

3. (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:

     **VSPerfClrEnv /off**

## <a name="see-also"></a>Siehe auch
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)
