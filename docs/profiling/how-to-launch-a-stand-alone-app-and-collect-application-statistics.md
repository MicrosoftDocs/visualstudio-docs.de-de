---
title: 'Profilerbefehlszeile: Starten einer eigenständigen App und Abrufen von App-Statistiken'
description: Hier erfahren Sie, wie Sie die Befehlszeilentools für die Profilerstellungstools von Visual Studio verwenden, um eine eigenständige App zu starten und Leistungsdaten über die Samplingmethode zu sammeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 575601f2676a8081422b029d0d7da94b6a4836ca
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883517"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Vorgehensweise: Starten einer eigenständigen Anwendung mit dem Profiler und Sammeln von Anwendungsstatistiken über die Befehlszeile
In diesem Thema wird beschrieben, wie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools eine eigenständige (Client-)Anwendung gestartet wird und wie mit der Samplingmethode Leistungsstatistiken gesammelt werden können.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools. Siehe [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Sie können die Profilerstellungstools auf einem Computer, auf dem Visual Studio installiert ist, aus einem Visual Studio-Befehlsfenster öffnen.

1. Wenn Sie die Profilerstellungstools auf einem Computer ausführen, auf dem Visual Studio installiert ist, werden die richtigen Pfade über ein Visual Studio-Befehlsfenster festgelegt. Wählen Sie im Menü **Tools** die **VS-Eingabeaufforderung** aus.

> [!NOTE]
> Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.

## <a name="start-the-application-with-the-profiler"></a>Starten der Anwendung mit dem Profiler
 Wenn Sie die Zielanwendung mit dem Profiler starten möchten, verwenden Sie die VSPerfCmd-Optionen **/start** und **/launch**, um den Profiler zu initialisieren und die Anwendung zu starten. Sie können **/start** und **/launch** sowie die zugehörigen Optionen in einer einzigen Befehlszeile angeben.

 Sie können auch die Option **/globaloff** hinzufügen, um die Datensammlung beim Starten der Zielanwendung anzuhalten. Zum Starten der Datensammlung verwenden Sie anschließend **/globalon**.

#### <a name="to-start-an-application-by-using-the-profiler"></a>So starten Sie eine Anwendung mit dem Profiler

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Starten Sie den Profiler. Typ:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - Mit der Option [/start](../profiling/start.md) **:sample** wird der Profiler initialisiert.

   - Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:sample** verwenden.

   | Option | Beschreibung |
   | - | - |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (*ETL*) gesammelt. |

3. Starten Sie die Zielanwendung. Type:**VSPerfCmd /launch:** `appName` [`Options`] [`Sample Event`]

    Die folgenden Optionen können mit der Option **/launch** kombiniert werden.

   |Option|Beschreibung|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:** `Arguments`|Gibt eine Zeichenfolge mit den Befehlszeilenargumenten an, die an die Zielanwendung übergeben werden sollen.|
   |[/console](../profiling/console.md)|Startet die Ziel-Befehlszeilenanwendung in einem separaten Fenster.|

    Standardmäßig wird alle 10.000.000 nicht angehaltene Prozessortaktzyklen ein Sampling der Leistungsdaten durchgeführt. Dies entspricht ca. 10 Sekunden auf einem 1-GHz-Prozessor. Sie können eine der folgenden Optionen angeben, um das Taktzyklusintervall zu ändern oder ein anderes Samplingereignis anzugeben.

   |Samplingereignis|Beschreibung|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:** `Interval`|Ändert das Samplingintervall auf die Anzahl der mit `Interval` angegebenen nicht angehaltenen Taktzyklen.|
   |[/pf](../profiling/pf.md)[ **:** `Interval`]|Ändert das Samplingereignis in Seitenfehler. Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Seitenfehler zwischen den Samplings angegeben. Der Standardwert ist 10.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ **:** `Interval`]|Ändert das Samplingereignis in Systemaufrufe des Prozesses an den Betriebssystem-Kernel (syscalls). Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Aufrufe zwischen den Samplings angegeben. Der Standardwert ist 10.|
   |[/counter](../profiling/counter.md) **:** `Config`|Ändert das Samplingereignis auf den Prozessorleistungsindikator und das Samplingintervall in das in `Config` angegebene Intervall.|

## <a name="control-data-collection"></a>Steuern der Datensammlung
 Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Profiler-Datendatei mit Optionen *VSPerfCmd.exe* starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung

- Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|Beschreibung|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID`  [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der `PID` oder des Prozessnamens (ProcName) angegeben wurde. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist) beendet.|

## <a name="end-the-profiling-session"></a>Beenden der Profilerstellungssitzung
 Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an eine profilierte Anwendung angefügt sein und muss explizit beendet werden. Den Profiler können Sie von einer Anwendung trennen, für die ein Profil mit der Samplingmethode erstellt wurde, indem Sie die Anwendung schließen oder die Option **VSPerfCmd /detach** aufrufen. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /off** werden die Umgebungsvariablen für die Profilerstellung gelöscht.

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung

1. Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:

    - Schließen Sie die Zielanwendung.

         - oder -

    - Geben Sie **VSPerfCmd /detach** ein.

2. Schließen Sie den Profiler. Typ:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Siehe auch
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)
