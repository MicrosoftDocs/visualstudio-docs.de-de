---
title: 'Profilerbefehlszeile: Instrumentieren der dynamischen ASP.NET-App und Abrufen von Arbeitsspeicherdaten'
description: Hier erfahren Sie, wie Sie die Befehlszeilentools für die Profilerstellungstools von Visual Studio verwenden, um detaillierte Daten zur Speicheraktivität für eine dynamisch kompilierte ASP.NET-Anwendung zu sammeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: c26342fb956aa5043f316015f05e18ef70d20559
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883591"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Vorgehensweise: Instrumentieren einer dynamisch kompilierten ASP.NET-Webanwendung und Sammeln von Speicherdaten über die Profilerbefehlszeile
In diesem Artikel erfahren Sie, wie Sie die zu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools gehörenden Befehlszeilentools verwenden können, um mithilfe der Instrumentierungsprofilerstellungs-Methode ausführliche Daten zur .NET-Speicherbelegung und Objektlebensdauer für eine dynamisch kompilierte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung zu erfassen.

> [!NOTE]
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

 Wenn Sie Leistungsdaten aus einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung erfassen möchten, müssen Sie die *web.config*-Datei der Zielanwendung bearbeiten, um das [VSInstr.exe](../profiling/vsinstr.md)-Tool zu aktivieren, damit die Dateien der dynamisch kompilierten Anwendung instrumentiert werden können. Verwenden Sie dann das [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md)-Tool, um den Server zu konfigurieren, der die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung hostet, und aktivieren Sie die Profilerstellung für den .NET-Speicher, indem Sie passende Umgebungsvariablen festlegen. Starten Sie anschließend den Computer neu.

 Starten Sie den Profiler, und führen Sie dann die Zielanwendung aus, um Daten zu erfassen. Wenn der Profiler mit der Anwendung verknüpft ist, können Sie die Datensammlung anhalten bzw. fortsetzen. Wenn Sie die entsprechenden Daten erfasst haben, schließen Sie die Anwendung und den IIS-Workerprozess, und fahren Sie den Profiler anschließend herunter.

 Wenn Sie die Profilerstellung abgeschlossen haben, stellen Sie den ursprünglichen Zustand der *web.config*-Datei und des Webservers wieder her.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurieren der ASP.NET-Webanwendung und des Webservers

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurieren der ASP.NET-Webanwendung und des Webservers

1. Bearbeiten Sie die *web.config*-Datei der Zielanwendung. Weitere Informationen finden Sie unter [How to: Modify web.config files to instrument and profile dynamically compiled ASP.NET web applications (Vorgehensweise: Bearbeiten von Web.Config-Dateien zur Instrumentierung und Profilerstellung für dynamisch kompilierte ASP.NET-Webanwendungen)](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Öffnen Sie ein Eingabeaufforderungsfenster auf dem Computer, der die Webanwendung hostet.

3. Initialisieren Sie die Umgebungsvariablen für die Profilerstellung. Typ:

     **VSPerfClrEnv /globaltracegc**

     - oder -

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc** aktiviert die Sammlung von Daten zur Speicherbelegung.

    - **/globaltracegclife** aktiviert die Sammlung von Daten zur Speicherbelegung und zur Objektlebensdauer.

4. Starten Sie den Computer neu.

## <a name="run-the-profiling-session"></a>Ausführen der Profilerstellungssitzung

#### <a name="to-profile-the-aspnet-web-application"></a>Profilerstellung für die ASP.NET-Webanwendung

1. Starten Sie den Profiler. Typ:

    **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Mit der Option **/start:trace** wird der Profiler initialisiert.

   - Die Option **/output:** `OutputFile` ist für **/start** erforderlich. `OutputFile` gibt den Namen und den Speicherort der Profilerstellungsdaten (*VSP*-Datei) an.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.

   > [!NOTE]
   > Die Optionen **/user** und **/crosssession** sind normalerweise für ASP.NET-Anwendungen erforderlich.

   | Option | Beschreibung |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Gibt den optionalen Domänen- und Benutzernamen des Kontos an, das Besitzer des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Workerprozesses ist. Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Name ist auf der Registerkarte **Prozesse** in der Spalte **Benutzername** des Windows Task-Managers aufgeführt. |
   | [/crosssession](../profiling/crosssession.md) | Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte **Prozesse** in der Spalte **Sitzungs-ID** des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Startet den Profiler mit angehaltener Datensammlung. Mit[/globalon](../profiling/globalon-and-globaloff.md) setzen Sie die Profilerstellung fort. |
   | [/counter](../profiling/counter.md) **:** `Config` | Sammelt Informationen aus dem in `Config` angegebenen Prozessorleistungsindikator. Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt. |

2. Starten Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung auf die gewohnte Weise.

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Profiler-Datendatei mit *VSPerfCmd.exe*-Optionen starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet ( **/threadon**) oder beendet ( **/threadoff**).|

- Sie können auch die Option **VSPerfCmd.exe**[/mark](../profiling/mark.md) verwenden, um eine Profilmarkierung in die Datendatei einzufügen. Der Befehl **/mark** fügt einen Bezeichner, einen Zeitstempel und eine optionale benutzerdefinierte Textzeichenfolge hinzu. Mit Markierungen können die Daten in Profilerberichten und Datenansichten gefiltert werden.

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Wenn Sie eine Profilerstellungssitzung beenden möchten, schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung, und halten Sie die IIS an, um den Profilerstellungsprozess abzubrechen. Fahren Sie anschließend den Profiler herunter. Starten Sie dann die IIS neu.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung.

2. Schließen Sie den Workerprozess [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], indem Sie die IIS zurücksetzen. Typ:

    **IISReset /stop**

3. Schließen Sie den Profiler. Typ:

    **VSPerfCmd** [/shutdown](../profiling/shutdown.md)

4. Starten Sie die IIS neu. Typ:

    **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>Wiederherstellen der Anwendungs- und Computerkonfiguration
 Wenn Sie die Profilerstellung abgeschlossen haben, ersetzen Sie die *web.config*-Datei, löschen Sie die Umgebungsvariablen für die Profilerstellung, und starten Sie den Computer neu, um den ursprünglichen Zustand des Servers und der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendung wiederherzustellen.

#### <a name="to-restore-the-application-and-computer-configuration"></a>Wiederherstellen der Anwendungs- und Computerkonfiguration

1. Ersetzen Sie die *web.config*-Datei durch eine Kopie der ursprünglichen Datei.

2. (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:

     **VSPerfCmd /globaloff**

3. Starten Sie den Computer neu.

## <a name="see-also"></a>Siehe auch
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)
