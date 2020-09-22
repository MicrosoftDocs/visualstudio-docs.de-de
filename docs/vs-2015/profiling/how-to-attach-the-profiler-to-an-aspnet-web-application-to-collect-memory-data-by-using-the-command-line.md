---
title: 'Vorgehensweise: Hinzufügen des Profilers zu einer ASP.NET-Webanwendung zum Erfassen von Speicherdaten über die Befehlszeile | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 454bcc4fe8e17530d71927d373a05f5f12beae61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841182"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Gewusst wie: Anfügen des Profilers an eine ASP.NET-Webanwendung zum Sammeln von Speicherdaten über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools den Profiler an eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung anfügen und Daten zur Anzahl und Größe der .NET Framework-Speicherbelegungen sammeln können. Sie können außerdem Daten zur Lebensdauer von .NET Framework-Arbeitsspeicherobjekten erfassen.  

> [!NOTE]
> Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Um Leistungsdaten von einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung zu erfassen, müssen Sie das Tool [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) verwenden, um die entsprechenden Umgebungsvariablen auf dem Computer zu initialisieren, der die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung hostet. Sie müssen dann den Computer neu starten, um den Webserver für die Profilerstellung zu konfigurieren.  

 Verwenden Sie dann das Tool [VSPerfCmd.exe](../profiling/vsperfcmd.md), um den Profiler dem [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess hinzuzufügen, der die Website hostet. Wenn der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  

 Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  

## <a name="attaching-the-profiler"></a>Anfügen des Profilers  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>So fügen Sie den Profiler an eine ASP.NET-Webanwendung an  

1. Öffnen Sie ein Eingabeaufforderungsfenster.  

2. Initialisieren Sie die Umgebungsvariablen für die Profilerstellung. Typ:  

    **VSPerfClrEnv** {**/globalsamplegc**|**/globalsamplegclife**} [**/samplelineoff**]  

   - Die Optionen **/globalsamplegc** und **/globalsamplegclife** geben den Typ der Speicherdaten an, die erfasst werden sollen.  

        Geben Sie eine der folgenden Optionen.  

       |Option|BESCHREIBUNG|  
       |------------|-----------------|  
       |**/globalsamplegc**|Aktiviert die Sammlung von Daten zur Speicherbelegung.|  
       |**/globalsamplegclife**|Aktiviert die Sammlung von Daten zur Speicherbelegung und zur Objektlebensdauer.|  

   - Die Option **/samplelineoff** deaktiviert die Zuweisung gesammelter Daten zu bestimmten Quellcodezeilen. Wenn diese Option angegeben ist, werden Daten auf Funktionsebene zugewiesen.  

3. Starten Sie den Computer neu, um die neue Umgebungskonfiguration festzulegen.  

4. Öffnen Sie ein Eingabeaufforderungsfenster. Legen Sie ggf. die Umgebungsvariable des Profilerpfads fest.  

5. Starten Sie den Profiler. Typ:  

    **VSPerfCmd**  [/Start](../profiling/start.md) **: Sample**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]  

   - Mit der Option **/start:sample** wird der Profiler initialisiert.  

   - Die Option **/output:** `OutputFile` ist für **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:sample** verwenden.  

   > [!NOTE]
   > Die Optionen **/user** und **/crosssession** sind normalerweise für ASP.NET-Anwendungen erforderlich.  

   |                                 Option                                  |                                                                                                                                                        Beschreibung                                                                                                                                                        |
   |-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` |                   Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des ASP.NET-Arbeitsprozesses ist. Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.                    |
   |              [/crosssession](../profiling/crosssession.md)              | Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen. Diese Option ist erforderlich, wenn die ASP.NET-Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs-ID des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. |
   |        [/WaitStart](../profiling/waitstart.md) [**:** `Interval` ]        |                                                      Gibt die Anzahl der Sekunden an, die auf die Initialisierung des Profilers gewartet werden soll, bevor ein Fehler zurückgegeben wird. Wenn `Interval` nicht angegeben wird, wartet der Profiler unendlich lange. Standardmäßig erfolgt die Rückgabe von **/start** sofort.                                                      |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                         Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.                                                                                                                         |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                       Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.                                                                                       |
   |       [/events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                         Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.                                                                                          |

6. Starten Sie die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung auf die gewohnte Weise.  

7. Fügen Sie den Profiler an den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess an. Typ:  

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**:** `Version` ]    

   - Die Prozess-ID `(PID)` gibt die Prozess-ID oder den Prozessnamen des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozesses an. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.  

   - **/targetclr:** `Version` Gibt die Version des Common Language Runtime (CLR) für die Profilerstellung an, wenn mehr als eine Laufzeitversion in eine Anwendung geladen wird.  

## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Während die Anwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Profilerdatendatei mit Optionen für **VSPerfCmd.exe** starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  

- Die folgenden Optionenpaare **VSPerfCmd** starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  

    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der `PID` angegebenen Prozess gestartet (**/processon**) oder beendet (**/processoff**).|  
    |**/Attach:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;: `ProcName` }]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der durch die Prozess-ID oder den Prozessnamen festgelegt ist. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist) beendet.|  

## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von der Webanwendung getrennt werden. Sie können das Sammeln von Daten für eine Anwendung anhalten, für die ein Profil mit der Samplingmethode erstellt wurde, indem Sie den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess erneut starten oder die Option **VSPerfCmd /detach** aufrufen. Rufen Sie anschließend die Option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Der **VSPerfClrEnv /globaloff**-Befehl löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.  

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  

1. Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  

   - Geben Sie **VSPerfCmd** [/detach](../profiling/detach.md) ein.  

      - oder -  

   - Schließen Sie den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess. Typ:  

     **IISReset /stop**  

2. Schließen Sie den Profiler. Typ:  

    **VSPerfCmd /shutdown**  

3. (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:  

    **VSPerfCmd /globaloff**  

4. Starten Sie den Computer neu. Starten Sie bei Bedarf Internetinformationsdienste (Internet Information Services, IIS) erneut. Typ:  

    **IISReset /start**  

## <a name="see-also"></a>Weitere Informationen  
 [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET-Arbeitsspeicher Datenansichten](../profiling/dotnet-memory-data-views.md)
