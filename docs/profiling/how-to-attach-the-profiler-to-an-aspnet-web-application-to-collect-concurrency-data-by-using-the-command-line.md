---
title: Anfügen eines Profilers an ASP.NET zum Sammeln von Parallelitätsdaten
description: Verwenden Sie Befehlszeilentools der Visual Studio Profilerstellungstools, um den Profiler an eine ASP.NET-Anwendung anzufügen und Parallelitätsdaten für Prozesse und Threads zu erfassen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 4a4f83cbff6e12798649ce34c109786e71a56c28
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801613"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Vorgehensweise: Anfügen des Profilers an eine ASP.NET-Webanwendung zum Sammeln paralleler Daten über die Befehlszeile

In diesem Artikel wird beschrieben, wie der Profiler mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools an eine ASP.NET-Anwendung angefügt wird und Parallelitätsdaten für Prozesse und Threads erfasst werden können.

Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

 Fügen Sie zum Sammeln von Nebenläufigkeitsdaten den Profiler an den ASP.NET-Arbeitsprozess an, der die Website hostet. Während der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen. Der Profiler darf nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden, um eine Profilerstellungssitzung zu beenden. Es empfiehlt sich in den meisten Fällen, am Ende einer Sitzung die Umgebungsvariablen für die Profilerstellung zu löschen.

## <a name="attach-the-profiler"></a>Anfügen des Profilers

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>So fügen Sie den Profiler an eine ASP.NET-Anwendung an

1. Starten Sie den Profiler, indem Sie den folgenden Befehl eingeben:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency /output:** `OutputFile` [`Options`]

   - Mit der Option [/start](../profiling/start.md) wird der Profiler initialisiert, um Ressourcenkonfliktdaten zu sammeln.

   - Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der **/start**-Option verwenden.

   | Option | Beschreibung |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`UserName` | Gibt den optionalen Domänen- und Benutzernamen des Kontos an, dem Zugriff auf den Profiler gewährt werden soll. |
   | [/crosssession](../profiling/crosssession.md) | Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt. |

2. Starten Sie die ASP.NET-Anwendung wie gewohnt.

3. Fügen Sie den Profiler an den ASP.NET-Arbeitsprozess an, indem Sie den folgenden Befehl eingeben:**VSPerfCmd /attach:** `PID` [ **/targetclr:** `Version`]

   - `PID` gibt die ID oder den Namen des ASP.NET-Arbeitsprozesses an. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere Runtimeversionen geladen wurden. Dieser Parameter ist optional.

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Während die Anwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit *VSPerfCmd.exe*-Optionen starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Mit den VSPerfCmd-Optionspaaren in der folgenden Tabelle wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID`  [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess-ID (`PID`) oder des Prozessnamens (*ProcName*) angegeben ist. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein Prozess angegeben ist) beendet.|

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen. Sie können das Sammeln von Daten einer Anwendung, für die mit der Parallelitätsmethode ein Profil erstellt wird, beenden, indem Sie den ASP.NET-Arbeitsprozess neu starten oder die **VSPerfCmd /detach**-Option aufrufen. Rufen Sie anschließend die **VSPerfCmd /shutdown**-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Der **VSPerfClrEnv /globaloff**-Befehl löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Trennen Sie den Profiler von der Zielanwendung, indem Sie die Anwendung schließen oder an einer Eingabeaufforderung Folgendes eingeben:

     **VSPerfCmd /detach**

2. Beenden Sie den Profiler, indem Sie den folgenden Befehl an der Eingabeaufforderung eingeben:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Siehe auch
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
