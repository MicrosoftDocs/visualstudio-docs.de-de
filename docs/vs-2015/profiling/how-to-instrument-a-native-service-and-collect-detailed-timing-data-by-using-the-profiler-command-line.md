---
title: 'Vorgehensweise: Instrumentieren eines nativen Diensts und Sammeln ausführlicher Zeitsteuerungsdaten über die Profiler-Befehlszeile | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ac986eb03d038121c043250d3001d9c5b6c6b54
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841107"
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Gewusst wie: Instrumentieren eines systemeigenen Diensts und Sammeln ausführlicher Zeitsteuerungsdaten über die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools einen systemeigenen Dienst (C/C++) instrumentieren und ausführliche Zeitsteuerungsdaten sammeln können.  

> [!NOTE]
> Mit der Instrumentationsmethode kann kein Profil für einen Dienst erstellt werden, wenn der Dienst nach dem Start des Computers nicht neu gestartet werden kann, z. B. ein Dienst, der nur gleichzeitig mit dem Betriebssystem gestartet wird.  
>   
> Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind 64-Bit- und 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Um ausführliche Zeitsteuerungsdaten mit der Instrumentierungsmethode aus einem nativen Dienst zu erfassen, generieren Sie mit dem Tool [VSInstr.exe](../profiling/vsinstr.md) eine instrumentierte Version der Komponente. Sie ersetzen dann die nicht instrumentierte Version des Diensts durch die instrumentierte Version und stellen dabei sicher, dass der Dienst für den manuellen Start konfiguriert ist. Starten Sie dann den Profiler.  

 Wenn der Dienst gestartet wird, werden die Zeitsteuerungsdaten automatisch in einer Datendatei erfasst. Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  

 Um eine Profilerstellungssitzung zu beenden, deaktivieren Sie den Dienst und fahren danach den Profiler selbst herunter.  

## <a name="starting-the-application-with-the-profiler"></a>Starten der Anwendung mit dem Profiler  

#### <a name="to-start-profiling-a-native-service"></a>So starten Sie die Profilerstellung für einen systemeigenen Dienst  

1. Öffnen Sie ein Eingabeaufforderungsfenster.  

2. Generieren Sie mit **VSInstr** eine instrumentierte Version der Binärdatei des Diensts.  

3. Ersetzen Sie die ursprüngliche Binärdatei durch die instrumentierte Version. Stellen Sie im Windows Dienststeuerungs-Manager sicher, dass der Starttyp auf Manuell eingestellt ist.  

4. Starten Sie den Profiler. Typ:  

    **VSPerfCmd** [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - Mit der Option **/start:trace** wird der Profiler initialisiert.  

   - Die Option **/output:** `OutputFile` ist für **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.  

   > [!NOTE]
   > Die Optionen **/user** und **/crosssession** sind normalerweise für ASP.NET-Anwendungen erforderlich.  

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

5. Startet den Dienst aus dem Dienststeuerungs-Manager.  

## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Wenn der Dienst ausgeführt wird, können Sie die **VSPerfCmd.exe**-Optionen verwenden, um das Schreiben der Daten in die Profilerdatendatei zu starten und zu beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen des Diensts.  

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  

- Die folgenden Optionenpaare **VSPerfCmd** starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  

    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet ( **/threadon**) oder beendet ( **/threadoff**).|  

## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, beenden Sie den Dienst, der die instrumentierte Komponente ausführt, und rufen Sie dann die **VSPerfCmd**-Option [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen.  

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  

1. Beendet den Dienst aus dem Dienststeuerungs-Manager.  

2. Schließen Sie den Profiler. Typ:  

     **VSPerfCmd /shutdown**  

3. Ersetzen Sie das instrumentierte Modul durch das Original. Konfigurieren Sie bei Bedarf den Starttyp des Diensts neu.  

## <a name="see-also"></a>Weitere Informationen  
 [Profil Erstellungs Dienste](../profiling/command-line-profiling-of-services.md)   
 [Instrumentierungs Methoden-Datenansichten](../profiling/instrumentation-method-data-views.md)
