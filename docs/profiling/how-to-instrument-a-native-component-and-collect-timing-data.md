---
title: 'Profilerbefehlszeile: Instrumentieren einer nativen Komponente und Abrufen von Zeitsteuerungsdaten'
description: Hier erfahren Sie, wie Sie die Befehlszeilentools für die Profilerstellungstools von Visual Studio verwenden, um detaillierte Zeiterfassungsdaten für eine native Komponente wie eine EXE- oder DLL-Datei für C++ zu sammeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 7d63ec7bded9cc19e31ee0d6f8ce7346990bf7aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929133"
---
# <a name="how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Vorgehensweise: Instrumentieren einer nativen, eigenständigen Komponente und Sammeln von Zeitsteuerungsdaten über die Befehlszeile mit dem Profiler
In diesem Artikel wird beschrieben, wie eine native Komponente (beispielsweise eine *EXE*- oder *DLL*-Datei in C++) mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools instrumentiert wird und wie ausführliche Zeitsteuerungsdaten gesammelt werden.

> [!NOTE]
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

Um ausführliche Zeitsteuerungsdaten aus einer Komponente mithilfe der Instrumentierungsmethode zu sammeln, generieren Sie mit dem Tool [VSInstr.exe](../profiling/vsinstr.md) eine instrumentierte Version der Komponente. Starten Sie dann den Profiler. Wenn die instrumentierte Komponente ausgeführt wird, werden Zeitsteuerungsdaten automatisch in einer Datendatei erfasst. Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.

 Um eine Profilerstellungssitzung zu beenden, schließen Sie die Zielanwendung, und schließen Sie danach den Profiler.

## <a name="start-the-profiling-session"></a>Starten der Profilerstellungssitzung

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>So starten Sie die Profilerstellung mit der Instrumentationsmethode

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Generieren Sie mit dem Tool **VSInstr** eine instrumentierte Version der Zielanwendung.

3. Starten Sie den Profiler. Typ:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Mit der Option [/start](../profiling/start.md) **:trace** wird der Profiler initialisiert.

   - Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können mindestens eine der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.

   | Option | Beschreibung |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte **Prozesse** in der Spalte **Benutzername** des Windows Task-Managers aufgeführt. |
   | [/crosssession](../profiling/crosssession.md) | Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte Prozesse in der Spalte **Sitzungs-ID** des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Startet den Profiler mit angehaltener Datensammlung. Mit[/globalon](../profiling/globalon-and-globaloff.md) setzen Sie die Profilerstellung fort. |
   | [/counter](../profiling/counter.md) **:** `Config` | Sammelt Informationen aus dem in `Config` angegebenen Prozessorleistungsindikator. Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt. |

4. Starten Sie die Zielanwendung auf die gewohnte Weise.

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit Optionen *VSPerfCmd.exe* starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet ( **/threadon**) oder beendet ( **/threadoff**).|

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Schließen Sie die Anwendung, die die instrumentierte Komponente ausführt, um eine Profilerstellungssitzung zu beenden. Rufen Sie anschließend die **VSPerfCmd**-Option [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Schließen Sie die Zielanwendung.

2. Schließen Sie den Profiler. Typ:

     **VSPerfCmd /shutdown**

## <a name="see-also"></a>Siehe auch
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Datenansichten der Instrumentierungsmethode](../profiling/instrumentation-method-data-views.md)
