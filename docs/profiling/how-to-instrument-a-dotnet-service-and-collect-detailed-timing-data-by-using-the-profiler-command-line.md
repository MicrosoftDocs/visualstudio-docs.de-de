---
title: 'Profilerbefehlszeile: Instrumentieren des .NET-Diensts und Abrufen von Details zur Zeitsteuerung'
description: Hier erfahren Sie, wie Sie die Befehlszeilentools für die Profilerstellungstools von Visual Studio verwenden, um detaillierte Zeiterfassungsdaten für einen .NET Framework-Dienst zu sammeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 9f318fc979d4562c355a9613f67a351452b04ddc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942619"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Vorgehensweise: Instrumentieren eines .NET-Diensts und Sammeln ausführlicher Zeitsteuerungsdaten über die Profiler-Befehlszeile

In diesem Artikel wird beschrieben, wie Sie mit den Befehlszeilentools der Visual Studio-Profilerstellungstools einen .NET Framework-Dienst instrumentieren und detaillierte Zeitsteuerungsdaten sammeln.

> [!NOTE]
> Mit der Instrumentationsmethode kann kein Profil für einen Dienst erstellt werden, wenn der Dienst nach dem Start des Computers nicht neu gestartet werden kann, z. B. ein Dienst, der nur gleichzeitig mit dem Betriebssystem gestartet wird.
>
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.
>
> Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools. Siehe [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md).

Um mit der Instrumentierungsmethode detaillierte Zeitsteuerungsdaten aus einem .NET Framework-Dienst zu erfassen, generieren Sie mit dem Tool [VSInstr.exe](../profiling/vsinstr.md) eine instrumentierte Version der Komponente. Sie ersetzen dann die nicht instrumentierte Version des Diensts durch die instrumentierte Version und stellen dabei sicher, dass der Dienst für den manuellen Start konfiguriert ist. Mit [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) können Sie die globalen Umgebungsvariablen für die Profilerstellung initialisieren und den Hostcomputer neu starten. Starten Sie dann den Profiler.

Wenn der Dienst gestartet wird, werden die Zeitsteuerungsdaten automatisch in einer Datendatei erfasst. Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.

Um eine Profilerstellungssitzung zu beenden, deaktivieren Sie den Dienst und fahren danach den Profiler selbst herunter. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.

## <a name="start-the-application-with-the-profiler"></a>Starten der Anwendung mit dem Profiler

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Generieren Sie mit **VSInstr** eine instrumentierte Version der Binärdatei des Diensts.

3. Ersetzen Sie die ursprüngliche Binärdatei durch die instrumentierte Version. Stellen Sie im Windows Dienststeuerungs-Manager sicher, dass der Starttyp auf Manuell eingestellt ist.

4. Initialisieren Sie die .NET Framework-Umgebungsvariablen für die Profilerstellung. Typ:

     **VSPerfClrEnv /globaltraceon**

5. Starten Sie den Computer neu.

6. Öffnen Sie ein Eingabeaufforderungsfenster.

7. Starten Sie den Profiler. Typ:

     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Mit der Option [/start](../profiling/start.md) **:trace** wird der Profiler initialisiert.

   - Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. `OutputFile` gibt den Namen und den Speicherort der Profilerstellungsdaten (*VSP*-Datei) an.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.

     > [!NOTE]
     > Die Optionen **/user** und **/crosssession** sind normalerweise für Profilerstellungsdienste erforderlich.

     | Option | Beschreibung |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte **Prozesse** in der Spalte **Benutzername** des Windows Task-Managers aufgeführt. |
     | [/crosssession](../profiling/crosssession.md) | Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte **Prozesse** in der Spalte **Sitzungs-ID** des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. |
     | [/waitstart](../profiling/waitstart.md)[ **:** `Interval`] | Gibt die Anzahl der Sekunden an, die auf die Initialisierung des Profilers gewartet werden soll, bevor ein Fehler zurückgegeben wird. Wenn `Interval` nicht angegeben wird, wartet der Profiler unendlich lange. Standardmäßig erfolgt die Rückgabe von **/start** sofort. |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | Fügen Sie der Befehlszeile **/start** die Option **globaloff** hinzu, um den Profiler mit angehaltener Datensammlung zu starten. Mit **/globalon** setzen Sie die Profilerstellung fort. |
     | [/counter](../profiling/counter.md) **:** `Config` | Sammelt Informationen aus dem in Config angegebenen Prozessorleistungsindikator. Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden. |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen. |
     | [/automark](../profiling/automark.md) **:** `Interval` | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms. |
     | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt. |

8. Starten Sie den Dienst über den Windows Dienststeuerungs-Manager.

## <a name="control-data-collection"></a>Steuern der Datensammlung

Wenn der Dienst ausgeführt wird, können Sie die *VSPerfCmd.exe*-Optionen verwenden, um das Schreiben der Daten in die Profilerdatendatei zu starten und zu beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen des Diensts.

- Die folgenden Optionenpaare **VSPerfCmd** starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet ( **/threadon**) oder beendet ( **/threadoff**).|

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung

Schließen Sie den Dienst, der die instrumentierte Komponente ausführt, um eine Profilerstellungssitzung zu beenden. Rufen Sie anschließend die **VSPerfCmd**-Option [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /globaloff** werden die Umgebungsvariablen für die Profilerstellung gelöscht.

Sie müssen den Computer neu starten, damit die neuen Umgebungseinstellungen übernommen werden.

1. Beendet den Dienst aus dem Dienststeuerungs-Manager.

2. Schließen Sie den Profiler. Typ:

     **VSPerfCmd /shutdown**

3. Wenn Sie alle Profilerstellungsaufgaben abgeschlossen haben, entfernen Sie die Umgebungsvariablen für die Profilerstellung. Typ:

     **VSPerfClrEnv /globaloff**

4. Ersetzen Sie das instrumentierte Modul durch das Original. Konfigurieren Sie bei Bedarf den Starttyp des Diensts neu.

5. Starten Sie den Computer neu.

## <a name="see-also"></a>Siehe auch

[Profilerstellung für Dienste über die Befehlszeile](../profiling/command-line-profiling-of-services.md)
[Instrumentierungsmethoden-Datenansichten](../profiling/instrumentation-method-data-views.md)
