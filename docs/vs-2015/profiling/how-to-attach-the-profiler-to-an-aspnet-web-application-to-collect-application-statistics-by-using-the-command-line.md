---
title: 'Vorgehensweise: Anfügen des Profilers an eine ASP.NET-Webanwendung zum Sammeln von Anwendungsstatistiken über die Befehlszeile | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c60e63384ab6f391cee1151c8ee20d39ae2e1b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841223"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Gewusst wie: Anfügen des Profilers an eine ASP.NET-Webanwendung zum Sammeln von Anwendungsstatistiken über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie der Profiler mit den Befehlszeilentools der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools an eine ASP.NET-Webanwendung angefügt wird und wie Sie mit der Samplingmethode Leistungsstatistiken sammeln können.  

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
> Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools. Informationen hierzu finden Sie unter [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
>   
> Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Zum Erfassen von Leistungsdaten in einer ASP.NET-Webanwendung müssen die entsprechenden Umgebungsvariablen initialisiert sein, und der Computer, auf dem die ASP.NET-Webanwendung gehostet wird, muss neu neu gestartet werden, um den Webserver zur Profilerstellung konfigurieren zu können.  

 Anschließend fügen Sie den Profiler an den ASP.NET-Arbeitsprozess an, der die Website hostet. Wenn der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  

 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von allen profilierten Anwendungen getrennt und explizit beendet werden. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  

## <a name="starting-the-profiler-and-attaching-to-an-aspnet-web-application"></a>Starten des Profilers und Anfügen an eine ASP.NET-Webanwendung  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>So fügen Sie den Profiler an eine ASP.NET-Webanwendung an  

1. Öffnen Sie ein Eingabeaufforderungsfenster.  

2. Initialisieren Sie die Umgebungsvariablen für die Profilerstellung. Typ:  

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]  

   - **/globalsampleon** aktiviert das Sampling.  

   - **/samplelineoff** deaktiviert die Zuweisung gesammelter Daten zu bestimmten Quellcodezeilen. Wenn diese Option angegeben wird, werden Daten nur Funktionen zugewiesen.  

3. Starten Sie den Computer neu.  

4. Starten Sie den Profiler. Typ:**VSPerfCmd** [/Start](../profiling/start.md)**: Sample** [/Output](../profiling/output.md)**:** `OutputFile` [ `Options` ]  

   - Mit der Option **/start:sample** wird der Profiler initialisiert.  

   - Die Option **/output:** `OutputFile` ist für **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:sample** verwenden.  

   > [!NOTE]
   > Die Optionen **/user** und **/crosssession** sind normalerweise für ASP.NET-Anwendungen erforderlich.  

   |                                 Option                                  |                                                                                                                                                        Beschreibung                                                                                                                                                        |
   |-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` |                   Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des ASP.NET-Arbeitsprozesses ist. Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.                    |
   |              [/crosssession](../profiling/crosssession.md)              | Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen. Diese Option ist erforderlich, wenn die ASP.NET-Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs-ID des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                         Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.                                                                                                                         |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                       Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.                                                                                       |
   |       [/events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                         Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.                                                                                          |

5. Starten Sie die ASP.NET-Webanwendung wie gewohnt.  

6. Fügen Sie den Profiler an den ASP.NET-Arbeitsprozess an. Typ:**VSPerfCmd** [/Attach](../profiling/attach.md)**:**{ `PID`&#124;`ProcName` } [ `Sample Event` ] [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - `PID` gibt die Prozess-ID des ASP.NET-Arbeitsprozesses an; `ProcName` gibt den Namen des Arbeitsprozesses an. Die Prozess-IDs und die Namen aller aktiven Prozesse werden im Windows Task-Manager angezeigt.  

   - Standardmäßig wird alle 10.000.000 nicht angehaltene Prozessortaktzyklen ein Sampling der Leistungsdaten durchgeführt. Bei einem 1-GHz-Prozessor entspricht dies etwa 100 Mal pro Sekunde. Sie können eine der folgenden **VSPerfCmd**-Optionen angeben, um das Taktzyklusintervall zu ändern oder ein anderes Samplingereignis anzugeben.  

   |Samplingereignis|Beschreibung|  
   |------------------|-----------------|  
   |[/timer](../profiling/timer.md) **:** `Interval`|Ändert das Samplingintervall auf die Anzahl der mit `Interval` angegebenen nicht angehaltenen Taktzyklen.|  
   |[/pf](../profiling/pf.md)[ **:** `Interval`]|Ändert das Samplingereignis in Seitenfehler. Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Seitenfehler zwischen den Samplings angegeben. Der Standardwert ist 10.|  
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Ändert das Samplingereignis in Systemaufrufe des Prozesses an den Betriebssystem-Kernel (syscalls). Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Aufrufe zwischen den Samplings angegeben. Der Standardwert ist 10.|  
   |[/counter](../profiling/counter.md) **:** `Config`|Ändert das Samplingereignis auf den Prozessorleistungsindikator und das Samplingintervall in das in `Config` angegebene Intervall.|  
   |[/targetclr](../profiling/targetclr.md) **:** `Version`|Gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn mehr als eine Laufzeitversion in eine Anwendung geladen wird.|  

   - **/targetclr:** `Version` gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere CLR-Versionen geladen wurden. (Optional)  

## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Wenn die Anwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit **VSPerfCmd.exe**-Optionen starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  

- Die folgenden Optionenpaare **VSPerfCmd** starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  

    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` **/PROCESSOFF:**`PID`|Die Datensammlung wird für den Prozess, der von `PID` angegeben wird, gestartet (**/processon**) oder beendet (**/processoff**).|  
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der `PID` oder des Prozessnamens (ProcName) angegeben wurde. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist) beendet.|  

## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Schließen Sie die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung, um eine Profilerstellungssitzung zu beenden, und verwenden Sie den **IISReset**-Befehl der Internetinformationsdienste (IIS), um den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Workerprozess zu schließen. Rufen Sie die **VSPerfCmd**-Option [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen.  

 Mit dem Befehl **VSPerfClrEnv /globaloff** werden die Umgebungsvariablen für die Profilerstellung gelöscht. Sie müssen den Computer neu starten, damit die neuen Umgebungseinstellungen übernommen werden.  

 Der **VSPerfClrEnv /globaloff**-Befehl löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.  

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  

1. Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  

    - Geben Sie **VSPerfCmd /detach** ein.  

         - oder -  

    - Schließen Sie den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess.  

2. Schließen Sie den Profiler. Type:**VSPerfCmd** [/shutdown](../profiling/shutdown.md)  

3. (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:  

     **VSPerfCmd /globaloff**  

4. Starten Sie den Computer neu.  

## <a name="see-also"></a>Weitere Informationen  
 [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)
