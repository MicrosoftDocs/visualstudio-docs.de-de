---
title: 'Profiler-Befehlszeile: Instrumentieren einer eigenständigen .NET-Komponente und Abrufen von Arbeitsspeicherdaten'
description: Hier erfahren Sie, wie Sie die Befehlszeilentools für die Profilerstellungstools von Visual Studio verwenden können, um Speicherdaten für eine .NET Framework-Komponente einer eigenständigen Anwendung zu sammeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: c82f6306dbcfd462862c4d68b9a6fa142ff069a0
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883682"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Vorgehensweise: Instrumentieren einer eigenständigen .NET Framework-Komponente und Sammeln von Speicherdaten über die Befehlszeile mit dem Profiler
In diesem Artikel wird beschrieben, wie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools eine .NET Framework-Komponente einer eigenständigen Anwendung wie eine EXE- oder eine DLL-Datei instrumentiert wird und wie Arbeitsspeicherinformationen mit dem Profiler gesammelt werden.

> [!NOTE]
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

 Um Arbeitsspeicherdaten einer .NET Framework-Komponente mit der Instrumentierungsmethode zu erfassen, verwenden Sie das Tool [VSInstr.exe](../profiling/vsinstr.md), um eine instrumentierte Version der Komponente und des Tools [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) zu generieren und Profilerstellungs-Umgebungsvariablen zu initialisieren. Danach starten Sie den Profiler mit dem Tool *VSPerfCmd.exe*.

 Wenn die instrumentierte Komponente ausgeführt wird, werden Speicherdaten automatisch in einer Datendatei erfasst. Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.

 Um eine Profilerstellungssitzung zu beenden, schließen Sie die Zielanwendung, und schließen Sie danach den Profiler. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.

## <a name="start-the-application-with-the-profiler"></a>Starten der Anwendung mit dem Profiler

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>So fügen Sie den Profiler an eine aktive .NET Framework-Anwendung an

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Generieren Sie mit dem Tool **VSInstr** eine instrumentierte Version der Zielanwendung.

3. Initialisieren Sie die .NET Framework-Umgebungsvariablen für die Profilerstellung. Typ:

    **VSPerfClrEnv** { **/tracegc** &#124; **/tracegclife**}

   - Mit den Optionen **/tracegc** und **/tracegclife** werden die Umgebungsvariablen so initialisiert, dass entweder nur Daten zur Speicherbelegung oder Daten zur Speicherbelegung und der Objektlebensdauer gesammelt werden.

       |Option|Beschreibung|
       |------------|-----------------|
       |**/tracegc**|Aktiviert die Sammlung von Daten zur Speicherbelegung.|
       |**/tracegclife**|Aktiviert die Sammlung von Daten zur Speicherbelegung und zur Objektlebensdauer.|

4. Starten Sie den Profiler. Typ:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Mit der Option [/start](../profiling/start.md) **:trace** wird der Profiler initialisiert.

   - Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. `OutputFile` gibt den Namen und den Speicherort der Profilerstellungsdaten (*VSP*-Datei) an.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.

   | Option | Beschreibung |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte **Prozesse** in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt. |
   | [/crosssession](../profiling/crosssession.md) | Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte **Prozesse** in der Spalte **Sitzungs-ID** des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Fügen Sie der Befehlszeile **/start** die Option **globaloff** hinzu, um den Profiler mit angehaltener Datensammlung zu starten. Mit **/globalon** setzen Sie die Profilerstellung fort. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms. |
   | [/counter](../profiling/counter.md) **:** `Config` | Sammelt Informationen aus dem in Config angegebenen Prozessorleistungsindikator. Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden. |
   | [events](../profiling/events-vsperfcmd.md) **:** `Config` | Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt. |

5. Starten Sie die Zielanwendung über das Eingabeaufforderungsfenster.

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit Option *VSPerfCmd.exe* starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Die folgenden Optionenpaare **VSPerfCmd** starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet ( **/threadon**) oder beendet ( **/threadoff**).|

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Schließen Sie die Anwendung, die die instrumentierte Komponente ausführt, um eine Profilerstellungssitzung zu beenden. Rufen Sie anschließend die **VSPerfCmd**-Option [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /off** werden die Umgebungsvariablen für die Profilerstellung gelöscht.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Schließen Sie die Zielanwendung.

2. Schließen Sie den Profiler. Typ:

     **VSPerfCmd /shutdown**

3. (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:

     **VSPerfCmd /off**

## <a name="see-also"></a>Siehe auch
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [.NET-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)
