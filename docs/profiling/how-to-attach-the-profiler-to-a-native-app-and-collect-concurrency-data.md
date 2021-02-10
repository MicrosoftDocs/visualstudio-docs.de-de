---
title: Anfügen des Profilers an eine native App und Sammeln von Parallelitätsdaten
description: Verwenden Sie Befehlszeilentools der Visual Studio Profilerstellungstools, um den Profiler an eine native eigenständige (C-/C++-)Anwendung anzufügen, die gerade ausgeführt wird, und Daten zu Threadkonflikten abzurufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: e1104f17e1932dcdd7c1071d14cb57a01aad8522
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969346"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Vorgehensweise: Anfügen des Profilers an eine native, eigenständige Anwendung und Sammeln von Parallelitätsdaten über die Befehlszeile
In diesem Artikel wird beschrieben, wie der Profiler mithilfe der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools an eine aktive, native und eigenständige Anwendung (C/C++) angefügt wird und Daten zu Threadkonflikten erfasst werden.

> [!NOTE]
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

 Während der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen. Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden.

## <a name="attach-the-profiler-to-a-running-native-application"></a>Anfügen des Profilers an eine aktive native Anwendung

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>So fügen Sie den Profiler an eine aktive native Anwendung an

1. Geben Sie an einer Eingabeaufforderung folgenden Befehl ein:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**

     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der Option **/start:concurrency** verwenden.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`Username`|Gibt den optionalen Domänen- und Benutzernamen des Kontos an, dem Zugriff auf den Profiler gewährt werden soll.|
    |[/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.|

2. Fügen Sie den Profiler an die Zielanwendung an, indem Sie den folgenden Befehl eingeben:

     **VSPerfCmd**  [/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`}

     `PID` gibt die Prozess-ID der Zielanwendung an. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit Option *VSPerfCmd.exe* starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Mit den Optionspaaren in der folgenden Tabelle wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess-ID (`PID`) oder des Prozessnamens (*ProcName*) angegeben ist. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein Prozess angegeben ist) beendet.|

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen. Sie können das Sammeln von Daten einer Anwendung, für die mithilfe der Samplingmethode ein Profil erstellt wird, beenden. Schließen Sie dazu die Anwendung, oder rufen Sie die Option **VSPerfCmd /detach** auf. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Trennen Sie den Profiler von der Zielanwendung, indem Sie die Anwendung schließen oder den folgenden Befehl eingeben:

     **VSPerfCmd /detach**

2. Beenden Sie den Profiler, indem Sie den folgenden Befehl eingeben:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)
