---
title: Anfügen des Profilers an eine native App und Sammeln von App-Statistiken
description: Verwenden Sie die Visual Studio Profilerstellungstools, um den Profiler an eine native eigenständige Anwendung anzufügen, die gerade ausgeführt wird, und mit der Samplingmethode Leistungsstatistiken abzurufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 37914559f71748865e25b5512264f6597ae4ef42
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801646"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Vorgehensweise: Anfügen des Profilers an eine native, eigenständige Anwendung und Sammeln von Anwendungsdaten über die Befehlszeile
In diesem Artikel wird beschrieben, wie die Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools verwendet werden, um den Profiler an eine ausgeführte eigenständige und native .NET Framework-(Client-)Anwendung anzufügen und Leistungsstatistik mithilfe der Samplingmethode zu sammeln.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

 Wenn der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen. Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden.

## <a name="attach-the-profiler"></a>Anfügen des Profilers
 Verwenden Sie zum Anfügen des Profilers an eine Zielanwendung mit dem Profiler die Optionen **VSPerfCmd/start** und **/attach**, um den Profiler zu initialisieren und an die Zielanwendung anzufügen. Sie können **/start** und **/attach** sowie die zugehörigen Optionen in einer einzigen Befehlszeile angeben. Sie können auch die Option **/globaloff** hinzufügen, um die Datensammlung beim Starten der Zielanwendung anzuhalten. Zum Starten der Datensammlung verwenden Sie anschließend **/globalon**.

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>So fügen Sie den Profiler an eine aktive .NET Framework-Anwendung an

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Starten Sie den Profiler. Typ:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - Der Profiler wird mit der Option [/start](../profiling/start.md) **:sample** initialisiert.

   - Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:sample** verwenden.

   | Option | Beschreibung |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt. |
   | [/crosssession](../profiling/crosssession.md) | Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn die ASP.NET-Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs-ID des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt. |

3. Fügen Sie den Profiler an die Zielanwendung an. Typ:

    **VSPerfCmd**  [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [`Sample Event`]

    `PID` gibt die Prozess-ID der Zielanwendung an. `ProcessName` gibt den Namen des Prozesses an. Beachten Sie, dass unvorhersehbare Ergebnissen ausgegeben werden können, wenn Sie `ProcessName` angeben und mehrere Prozesse mit dem gleichen Namen ausgeführt werden. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.

    Standardmäßig wird alle 10.000.000 nicht angehaltene Prozessortaktzyklen ein Sampling der Leistungsdaten durchgeführt. Bei einem 1-GHz-Prozessor entspricht dies etwa 100 Mal pro Sekunde. Sie können eine der folgenden Optionen angeben, um das Taktzyklusintervall zu ändern oder ein anderes Samplingereignis anzugeben.

   |Samplingereignis|Beschreibung|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:** `Interval`|Ändert das Samplingintervall auf die Anzahl der mit `Interval` angegebenen nicht angehaltenen Taktzyklen.|
   |[/pf](../profiling/pf.md)[ **:** `Interval`]|Ändert das Samplingereignis in Seitenfehler. Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Seitenfehler zwischen den Samplings angegeben. Der Standardwert ist 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [ **:** `Interval`]|Ändert das Samplingereignis in Systemaufrufe des Prozesses an den Betriebssystem-Kernel (syscalls). Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Aufrufe zwischen den Samplings angegeben. Der Standardwert ist 10.|
   |[/counter](../profiling/counter.md) **:** `Config`|Ändert das Samplingereignis auf den Prozessorleistungsindikator und das Samplingintervall in das in `Config` angegebene Intervall.|

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Wenn die Zielanwendung ausgeführt wird, können Sie mit *VSPerfCmd.exe*-Optionen das Schreiben der Daten in die Profilerdatendatei starten und beenden. Durch die Steuerung der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Die folgenden Optionenpaare **VSPerfCmd** starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den Prozess, der von `PID` angegeben wird, gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/attach](../profiling/attach.md) **:** `PID` [/detach](../profiling/detach.md)|Mit **/attach** wird die Datensammlung für den über die `PID` angegebenen Prozess gestartet. Mit **/detach** wird die Datensammlung für alle Prozesse beendet.|

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von allen profilierten Prozessen getrennt und explizit beendet werden. Den Profiler können Sie von einer Anwendung trennen, für die ein Profil mit der Samplingmethode erstellt wurde, indem Sie die Anwendung schließen oder die Option **VSPerfCmd /detach** aufrufen. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /off** werden die Umgebungsvariablen für die Profilerstellung gelöscht.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen.

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
