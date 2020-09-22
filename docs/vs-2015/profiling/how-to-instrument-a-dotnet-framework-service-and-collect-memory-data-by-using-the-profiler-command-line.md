---
title: 'Vorgehensweise: Instrumentieren eines .NET Framework-Diensts und Sammeln von Speicherdaten über die Profiler-Befehlszeile | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d76eb9882eaf51de031d886c15954df8d5180e25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841011"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Gewusst wie: Instrumentieren eines .NET Framework-Diensts und Sammeln von Speicherdaten über die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools einen [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Dienst instrumentieren und Daten zur Speicherauslastung sammeln können. Sie können nur Daten zur Speicherbelegung oder Daten zur Speicherbelegung und zur Lebensdauer von Objekten sammeln.  

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Mit der Instrumentationsmethode kann kein Profil für einen Dienst erstellt werden, wenn der Dienst nach dem Start des Computers nicht neu gestartet werden kann, z. B. ein Dienst, der gleichzeitig mit dem Betriebssystem gestartet wird.  
>   
> Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind 64-Bit- und 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="starting-the-profiling-session"></a>Starten der Profilerstellungssitzung  
 Verwenden Sie [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) zum Sammeln von Leistungsdaten von einem [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Dienst, um die entsprechenden Umgebungsvariablen zu initialisieren, und [VSInstr.exe](../profiling/vsinstr.md), um eine instrumentierte Kopie der Binärdatei des Diensts zu erstellen.  

 Der Computer, auf dem der Dienst gehostet wird, muss neu gestartet werden, um ihn für die Profilerstellung zu konfigurieren. Außerdem müssen Sie den Dienst manuell über den Dienststeuerungs-Manager starten. Starten Sie dann den Profiler und anschließend den [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Dienst.  

 Wenn die instrumentierte Komponente ausgeführt wird, werden Speicherdaten automatisch in einer Datendatei erfasst. Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  

 Um eine Profilerstellungssitzung zu beenden, schließen Sie den Dienst und fahren danach den Profiler selbst herunter. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  

#### <a name="to-begin-profiling-a-net-framework-service"></a>So starten Sie die Profilerstellung für einen .NET Framework-Dienst  

1. Öffnen Sie ein Eingabeaufforderungsfenster.  

2. Generieren Sie mit **VSInstr** eine instrumentierte Version der Binärdatei des Diensts.  

3. Ersetzen Sie mit dem Dienststeuerungs-Manager die ursprüngliche Binärdatei durch die instrumentierte Version. Stellen Sie sicher, dass der Starttyp des Diensts auf Manuell festgelegt ist.  

4. Initialisieren Sie die Umgebungsvariablen für die Profilerstellung. Typ:  

    **VSPerfClrEnv** { **/globaltracegc** | **/globaltracegclife**}  

   - **/globaltracegc** und **/globaltracegclife** aktivieren die Erfassung von Daten zur Speicherbelegung und zur Objektlebensdauer.  

       |Option|Beschreibung|  
       |------------|-----------------|  
       |**/globaltracegc**|Sammelt nur Daten zur Speicherbelegung.|  
       |**/globaltracegclife**|Sammelt Daten zur Speicherbelegung und zur Objektlebensdauer.|  

5. Starten Sie den Computer neu.  

6. Öffnen Sie ein Eingabeaufforderungsfenster.  

7. Starten Sie den Profiler. Typ:  

    **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - Mit der Option **/start:contention** wird der Profiler initialisiert.  

   - Die Option **/output:** `OutputFile` ist für **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:sample** verwenden.  

   > [!NOTE]
   > Die Option **/user** und **/crosssession** sind normalerweise für Dienste erforderlich.  

   |                                 Option                                  |                                                                                                                                                   Beschreibung                                                                                                                                                    |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` |               Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des ASP.NET-Arbeitsprozesses ist. Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.               |
   |              [/crosssession](../profiling/crosssession.md)              | Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen. Diese Option ist erforderlich, wenn die ASP.NET-Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte „Prozesse“ in der Spalte „Sitzungs-ID“ des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. |
   |        [/waitstart](../profiling/waitstart.md)[ **:** `Interval`]         |                                                 Gibt die Anzahl der Sekunden an, die auf die Initialisierung des Profilers gewartet werden soll, bevor ein Fehler zurückgegeben wird. Wenn `Interval` nicht angegeben wird, wartet der Profiler unendlich lange. Standardmäßig erfolgt die Rückgabe von **/start** sofort.                                                  |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                             Fügen Sie der Befehlszeile **/start** die Option **globaloff** hinzu, um den Profiler mit angehaltener Datensammlung zu starten. Mit **/globalon** setzen Sie die Profilerstellung fort.                                                                              |
   |           [/counter](../profiling/counter.md) **:** `Config`            |                                                                           Sammelt Informationen aus dem in Config angegebenen Prozessorleistungsindikator. Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden.                                                                           |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                    Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.                                                                                                                     |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                  Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.                                                                                   |
   |       [/events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                     Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.                                                                                     |

8. Starten Sie den Dienst bei Bedarf.  

9. Fügen Sie den Profiler an den Dienst an. Typ:  

     **VSPerfCmd /attach:** `PID`&#124;`ProcessName`  

    - Geben Sie die Prozess-ID oder den Prozessnamen des Diensts an. Die Prozess-IDs und die Namen aller aktiven Prozesse werden im Windows Task-Manager angezeigt.  

## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Während der Dienst ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit **VSPerfCmd.exe**-Optionen starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  

- Die folgenden Optionenpaare **VSPerfCmd** starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  

    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet ( **/threadon**) oder beendet ( **/threadoff**).|  

## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Schließen Sie die Anwendung, die die instrumentierte Komponente ausführt, um eine Profilerstellungssitzung zu beenden. Starten Sie anschließend die **VSPerfCmd**-Option [/shutdown](../profiling/shutdown.md), um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /globaloff** werden die Umgebungsvariablen für die Profilerstellung gelöscht.  

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  

1. Beendet den Dienst aus dem Dienststeuerungs-Manager.  

2. Schließen Sie den Profiler. Typ:  

     **VSPerfCmd /shutdown**  

3. Wenn Sie alle Profilerstellungsaufgaben abgeschlossen haben, entfernen Sie die Umgebungsvariablen für die Profilerstellung. Typ:  

     **VSPerfClrEnv /globaloff**  

     Ersetzen Sie das instrumentierte Modul durch das Original. Konfigurieren Sie bei Bedarf den Starttyp des Diensts neu.  

4. Starten Sie den Computer neu.  

## <a name="see-also"></a>Weitere Informationen  
 [Profil Erstellungs Dienste](../profiling/command-line-profiling-of-services.md)   
 [.NET-Arbeitsspeicher Datenansichten](../profiling/dotnet-memory-data-views.md)
