---
title: 'Profilerbefehlszeile: Instrumentieren der statischen ASP.NET-App und Abrufen von Daten zur Zeitsteuerung'
description: Hier erfahren Sie, wie Sie die Befehlszeilentools für die Profilerstellungstools von Visual Studio verwenden, um detaillierte Zeiterfassungsdaten für eine vorkompilierte ASP.NET-Webkomponente oder Website zu sammeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 65db2ebe3b79fbe1391e59c9e948dc8cb034a57c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929003"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Vorgehensweise: Instrumentieren einer statisch kompilierten ASP.NET-Webanwendung und Sammeln ausführlicher Zeitsteuerungsdaten über die Profiler-Befehlszeile
In diesem Artikel wird beschrieben, wie die Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools verwendet werden, um eine vorkompilierte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webkomponente oder -Website zu instrumentieren und ausführliche Zeitsteuerungsdaten zu erfassen.

> [!NOTE]
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.
>
> Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools. Informationen hierzu finden Sie unter [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 Um ausführliche Zeitsteuerungsdaten aus einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webkomponente mithilfe der Instrumentierungsmethode zu erfassen, können Sie mit dem Tool [VSInstr.exe](../profiling/vsinstr.md) eine instrumentierte Version der Komponente generieren. Auf dem Computer, der die Komponente hostet, müssen Sie die nicht instrumentierte Version der Komponente durch die instrumentierte Version ersetzen. Mit [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) können Sie die globalen Umgebungsvariablen für die Profilerstellung initialisieren und den Hostcomputer neu starten. Starten Sie dann den Profiler.

 Wenn die instrumentierte Komponente ausgeführt wird, werden Zeitsteuerungsdaten automatisch in einer Datendatei erfasst. Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.

 Wenn Sie eine Profilerstellungssitzung beenden möchten, schließen Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Workerprozess, der die Komponente hostet, und anschließend explizit den Profiler. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.

## <a name="start-to-profile"></a>Erste Schritte der Profilerstellung

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>So instrumentieren Sie eine ASP.NET-Webkomponente und starten die Profilerstellung

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Generieren Sie mit dem Tool **VSInstr** eine instrumentierte Version der Zielanwendung. Ersetzen Sie die Anwendungsbinärdateien auf dem ASP.NET-Hostcomputer falls notwendig durch die instrumentierten Binärdateien.

3. Initialisieren Sie die .NET-Umgebungsvariablen für die Profilerstellung. Geben Sie im Fenster Eingabeaufforderung Folgendes ein:

    **VSPerfClrEnv /globaltraceon**

4. Starten Sie den Computer neu.

5. Öffnen Sie ein Eingabeaufforderungsfenster. Legen Sie den Toolpfad für den Profiler fest, falls notwendig.

6. Starten Sie den Profiler. Typ:

    **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]

   - Mit der Option [/start](../profiling/start.md) **:trace** wird der Profiler initialisiert.

   - Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.

   > [!NOTE]
   > Die Optionen **/user** und **/crosssession** sind normalerweise für ASP.NET-Anwendungen erforderlich.

   | Option | Beschreibung |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des ASP.NET-Arbeitsprozesses ist. Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte **Prozesse** in der Spalte **Benutzername** des Windows Task-Managers aufgeführt. |
   | [/crosssession](../profiling/crosssession.md) | Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen. Diese Option ist erforderlich, wenn die ASP.NET-Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte Prozesse in der Spalte **Sitzungs-ID** des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt. |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | Fügen Sie der Befehlszeile **/start** die Option **globaloff** hinzu, um den Profiler mit angehaltener Datensammlung zu starten. Mit **/globalon** setzen Sie die Profilerstellung fort. |

7. Öffnen Sie die Website, die die instrumentierte Komponente enthält.

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
 Schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung, um eine Profilerstellungssitzung zu beenden, und verwenden Sie den **IISReset**-Befehl der Internetinformationsdienste (IIS), um den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Workerprozess zu schließen. Rufen Sie die **VSPerfCmd**-Option [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen.

 Mit dem Befehl **VSPerfClrEnv /globaloff** werden die Umgebungsvariablen für die Profilerstellung gelöscht. Sie müssen den Computer neu starten, damit die neuen Umgebungseinstellungen übernommen werden.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung.

2. Schließen Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Arbeitsprozess. Typ:

    **IISReset /stop**

3. Schließen Sie den Profiler. Typ:

    **VSPerfCmd /shutdown**

4. (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:

    **VSPerfCmd /globaloff**

5. Starten Sie den Computer neu.

## <a name="see-also"></a>Siehe auch
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Datenansichten der Instrumentierungsmethode](../profiling/instrumentation-method-data-views.md)
