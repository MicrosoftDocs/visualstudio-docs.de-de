---
title: Befehlszeilenprogramm für die Parallelitätsschnellansicht
description: Verwenden Sie das Befehlszeilenhilfsprogramm CVCollectionCmd.exe, um Überwachungsdaten zu erfassen, die Sie in Concurrency Visualizer anzeigen können. Visual Studio muss nicht installiert sein.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 47da8ae405dc24cad5bab4c98384ad5db5a97ef2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941176"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Befehlszeilenprogramm für die Parallelitätsschnellansicht (CVCollectionCmd)
Sie können das Befehlszeilenprogramm für die Parallelitätsschnellansicht (*CVCollectionCmd.exe*) verwenden, um die Ablaufverfolgung aus der Befehlszeile zu sammeln und diese in der Parallelitätsschnellansicht für Visual Studio anzuzeigen. Die Tools können auf Computern verwendet werden, auf denen Visual Studio nicht installiert ist.

> [!NOTE]
> Seit Visual Studio 2013 ist Concurrency Visualizer eine optionale Erweiterung. (Zuvor war das Programm Bestandteil von Visual Studio.) Sie können die [Concurrency Visualizer Collection Tools für Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) aus dem Download Center herunterladen.

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Herunterladen des Befehlszeilenprogramms für die Parallelitätsschnellansicht
 Zum Herunterladen und Installieren des Befehlszeilenprogramms rufen Sie [Concurrency Visualizer Collection Tools für Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) auf, und folgen Sie den Anweisungen. Standardmäßig wird *CVCollectionCmd.exe* in %ProgramFiles%\Microsoft Concurrency Visualizer Collection Tools\ (%ProgramFiles(x86)%\Microsoft Concurrency Visualizer Collection Tools\ auf 64-Bit-Computern) installiert.

## <a name="collect-a-trace-with-cvcollectioncmd"></a>Eine Ablaufverfolgung mit CVCollectionCmd sammeln
 Sie können eine Ablaufverfolgung sammeln, indem Sie die App mit CVCollectionCmd starten oder es dieser anhängen. Siehe die Befehlszeilenreferenz unten hinsichtlich Ihrer Optionen. Beispiel:

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>Befehle und Parameter
 Wenn Sie Hilfe zu den Befehlen und Parametern im Befehlszeilenprogramm benötigen, geben Sie Folgendes in der Eingabeaufforderung ein:

 **CVCollectionCmd**

|Option|Beschreibung|Parameter|Rückgabewerte|
|------------|-----------------|----------------|-------------------|
|Abfrage|Gibt zurück, ob sich die Auflistung starten lässt.|Keine|0, wenn die Auflistung startbereit ist.<br /><br /> 1, wenn die Auflistung bereits läuft.<br /><br /> 2, wenn die Auflistung nicht läuft, aber eine oder mehr der erforderlichen [ETW](/dotnet/framework/wcf/samples/etw-tracing)-Sitzungen bereit aktiviert ist.|
|Starten|Führt den festgelegten Prozess unter Concurrency Visualizer aus.|Der Pfad der ausführbaren Datei.|0, wenn das Ausführen erfolgreich war.<br /><br /> 1, wenn das Ausführen fehlgeschlagen ist, weil die Zielanwendung nicht gestartet werden konnte.<br /><br /> 13, wenn das Ausführen fehlgeschlagen ist, weil CVCollectionCmd keine ausreichenden Berechtigungen für das Schreiben in die festgelegte Ausgabeverzeichnis besitzt.|
|Anfügen|Beginnt mit dem Erfassen einer systemweiten Ablaufverfolgung; wird ansonsten an einen Prozess angefügt, sofern ein solcher festgelegt wurde.|Keine|0, wenn Anfügen erfolgreich war.<br /><br /> 1, wenn das Anfügen fehlgeschlagen ist, weil der festgelegte Prozess ungültig oder mehrdeutig ist.<br /><br /> 13, wenn das Anfügen fehlgeschlagen ist, weil CVCollectionCmd nicht ausreichende Berechtigungen für das Schreiben in das festgelegte Ausgabeverzeichnis besitzt.|
|Trennen|Auflistung wird angehalten.|Keine|0, wenn Trennen erfolgreich war.<br /><br /> 1, wenn das Trennen fehlgeschlagen ist, weil die Auflistung aktuell nicht ausgeführt wird.<br /><br /> 2, wenn das Trennen fehlgeschlagen ist, weil die Auflistung nicht angehalten werden konnte.|
|Analysieren|Analysiert die festgelegte Ablaufverfolgung.|Der vollständige Pfad der Datei DVTrace.|0, wenn die Analyse erfolgreich war.<br /><br /> 1, wenn die Analyse nicht gestartet werden kann, da die festgelegte Ablaufverfolgung systemweit war, aber kein Zielprozess festgelegt worden ist.<br /><br /> 2, wenn die Analyse nicht gestartet werden kann, da die Ablaufverfolgung nicht systemweit war und ein Zielprozess festgelegt worden ist.<br /><br /> 3, wenn die Analyse fehlgeschlagen ist, weil der festgelegte Prozess ungültig ist.<br /><br /> 4, wenn die Analyse fehlgeschlagen ist, weil die festgelegte Datei CVTrace ungültig ist.|
|LaunchArgs|Legt die ausführbaren Argumente des Ziels fest. Diese Option gilt nur für den Befehl "Launch".|Die Befehlszeilenargumente für die Anwendung.|Keine|
|Outdir|Legt das Verzeichnis fest, in dem die Ablaufverfolgungsdateien gespeichert werden sollen. Gilt für die Befehle "Starten" und "Anfügen".|Ein Verzeichnispfad oder ein relativer Pfad.|Keine|
|Prozess|Legt den anfügenden Prozess fest, wenn der Befehl "Anfügen" ausgeführt wird oder den zu analysierenden Prozesses in einer Ablaufverfolgung, wenn der Befehl "Analysieren" ausgeführt wird. Gilt für die Befehle "Anfügen" und "Analysieren".|PID oder Name des Prozesses.|Keine|
|Konfigurationen|Legt den Pfad der Konfigurationsdatei fest, wenn Sie andere Auflistungeinstellungen als die standardmäßigen möchten.   Gilt für die Befehle "Starten", "Anfügen" und "Analysieren".|Der Verzeichnispfad oder relative Pfad der XML-Konfigurationsdatei.|Keine|

## <a name="customize-configuration-settings"></a>Anpassen von Konfigurationseinstellungen
 Wenn Sie CVCollectionCmd für die Auflistung der Ablaufverfolgung verwenden und die Einstellungen anpassen möchten, dann verwenden Sie eine Konfigurationsdatei, um diese festzulegen.

> [!NOTE]
> Wenn Sie Visual Studio für die Auflistung der Ablaufverfolgung verwenden, dann verändern Sie die Konfigurationsdatei nicht direkt.  Nutzen Sie stattdessen das Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) dafür.

 Erstellen Sie für Änderungen an den Auflistungseinstellung eine Konfigurationsdatei auf dem Rechner, auf dem das Dienstprogramm CVCollectionCmd ausgeführt wird. Sie können die Konfigurationsdatei neu erstellen oder auf den Computer kopieren, auf dem Visual Studio installiert ist und sie anschließend anpassen. Die Datei heißt *UserConfig.xml* und befindet sich im Ordner *Local AppData*. Wenn Sie das Dienstprogramm ausführen, verwenden Sie die Option "Config" zusammen mit dem Befehl "Starten", "Anfügen" oder "Analysieren".  Geben Sie in dem der Option "Config" zugeordneten Parameter den Pfad zur Konfigurationsdatei an.

### <a name="configuration-file-tags"></a>Tags der Konfigurationsdatei
 Die Konfigurationsdatei ist XML-basiert. Hier sind die gültigen Tags und Werte:

| Tag | Beschreibung | Werte |
|-------------------------| - | - |
| Konfigurationen | Grenzt die gesamte Config-Datei ab. | Muss folgende Elemente enthalten:<br /><br /> - MinorVersion<br />- MajorVersion |
| MajorVersion | Gibt die Hauptversion der Konfigurationsdatei an. | Muss 1 sein für [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] -Projekte. Wenn nicht 1, dann funktioniert das Dienstprogramm nicht. |
| MinorVersion | Legt die Nebenversion der Konfigurationsdatei fest. | Muss 0 sein für [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] -Projekte. Wenn nicht 0, dann funktioniert das Dienstprogramm nicht. |
| IncludeEnvSymbolPath | Legt einen Wert fest, der bestimmt, ob der Umgebungssymbolpfad (_NT_SYMBOL_PATH) verwendet wird. | - TRUE<br />- FALSE |
| DeleteEtlsAfterAnalysis | Gibt einen Wert an, der festlegt, ob die ETL-Dateien nach Abschluss der Analyse gelöscht werden. | - TRUE<br />- FALSE |
| SymbolPath | Gibt den Pfad des Symbolservers an. Weitere Informationen finden Sie unter [Beziehen von Debugsymboldateien über den Microsoft-Symbolserver](/windows/win32/dxtecharts/debugging-with-symbols). | Ein Verzeichnisname oder eine URL. |
| Marker | Enthält die Liste der Markeranbieter. | Kann null oder mehr MarkerProvider-Elemente enthalten. |
| MarkerProvider | Gibt einen einzelnen Markeranbieter an. | Muss folgende Elemente enthalten:<br /><br /> - Ebene<br />- GUID<br />- Name<br /><br /> Kann folgende Elemente enthalten:<br /><br /> - Kategorien<br />- IsEnabled |
| Ebene | Legt den Wert für die Bedeutung eines MarkerProviders fest. | - Niedrig<br />- Normal<br />- Hoch<br />- Kritisch<br />- Alles |
| GUID | Der Globally Unique Identifier des ETW-Markeranbieters. | Ein GUID. |
| name | Gibt die Beschreibung des Markeranbieters an. | Eine Zeichenfolge. |
| Kategorien | Gibt die für den Markeranbieter erfassten Kategorien an. | Eine durch Kommas getrennte Zeichenfolge oder eine Reihe von Zahlen. |
| IsEnabled | Gibt einen Wert an der festlegt, ob der Markeranbieter für die Auflistung aktiviert ist. | - TRUE<br />- FALSE |
| FilterConfig | Gibt die Liste der Konfigurationsoptionen der ETW-Ereignisse an, die aus der Auflistung gefiltert werden. | Kann folgende Elemente enthalten:<br /><br /> - CollectClrEvents<br />- ClrCollectionOptions<br />- CollectSampleEvents<br />- CollectGpuEvents<br />- CollectFileIO |
| CollectClrEvents | Geben Sie einen Wert an, der festlegt, ob CLR-Ereignisse gesammelt werden. | - TRUE<br />- FALSE |
| ClrCollectionOptions | Gibt an, ob CLR-Ereignisse für systemeigene Apps gesammelt werden und ob NGEN-Rundownereignisse erfasst werden sollen. | Kann einen, beide oder keinen der folgenden Werte enthalten:<br /><br /> - CollectForNative<br />- DisableNGenRundown |
| CollectSampleEvents | Gibt einen Wert an, der festlegt, ob Samplingereignisse gesammelt werden. | - TRUE<br />- FALSE |
| CollectGpuEvents | Gibt einen Wert an, der festlegt, ob die von DX erstellten Ereignisse gesammelt werden. | - TRUE<br />- FALSE |
| CollectFileIO | Gibt einen Wert an, der festlegt, ob I/O-Ereignisse gesammelt werden. | - TRUE<br />- FALSE |
| UserBufferSettings | Gibt die Parameterliste für die Benutzerpuffereinstellungen an. | Muss folgende Elemente enthalten:<br /><br /> - BufferFlushTimer<br />- BufferSize<br />- MinimumBuffers<br />- MaximumBuffers |
| KernelBufferSettings | Gibt die Parameterliste für die Kernelpuffereinstellungen an. | Muss folgende Elemente enthalten:<br /><br /> - BufferFlushTimer<br />- BufferSize<br />- MinimumBuffers<br />- MaximumBuffers |
| BufferFlushTimer | Gibt den Leerungszeitgeber der ETW-Puffer an. | Eine positive ganze Zahl. |
| BufferSize | Die jedem Sitzungspuffer für die Ereignisablaufverfolgung zugewiesene Menge an Speicher in Kilobyte. | Eine Zahl von 0 bis 1024. |
| MinimumBuffers | Die Mindestanzahl an Puffern, die für den Pufferpool der Ereignisablaufverfolgungssitzung zugeordnet sind. | Eine positive ganze Zahl größer oder gleich der doppelten Anzahl logischer Kerne. |
| MaximumBuffers | Die maximale Anzahl an Puffern, die für den Pufferpool der Ereignisablaufverfolgungssitzung zugeordnet sind. | Ein Zahl größer oder gleich der MinimumBuffers. |
| JustMyCode | Gibt die Liste der Verzeichnisse "Nur mein Code" an. | Eine Liste von null oder mehr MyCodeDirectory-Elementen. |
| MyCodeDirectory | Gibt ein Verzeichnis an, das Ihren Code enthält. | Ein absoluter Pfad. |

### <a name="example"></a>Beispiel
 Statt eine Konfigurationsdatei von vorn zu beginnen, können Sie das folgende Beispiel kopieren und es dann an Ihren Bedarf anpassen.

```xml
<?xml version="1.0"?>
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">

  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>

  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>

  <TraceLocation>C:\traces</TraceLocation>

  <SymbolPath>http://symweb</SymbolPath>

  <Markers>
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />

    <!-- The IsEnabled and Categories elements are optional -->
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />
  </Markers>

  <FilterConfig>
    <CollectClrEvents>true</CollectClrEvents>
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>
    <CollectSampleEvents>true</CollectSampleEvents>
    <CollectGpuEvents>true</CollectGpuEvents>
    <CollectFileIO>true</CollectFileIO>
  </FilterConfig>

  <UserBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </UserBufferSettings>

  <KernelBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </KernelBufferSettings>

  <!-- List of MyCodeDirectory directories -->
  <JustMyCode>
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>
  </JustMyCode>
</LocalConfig>

```
