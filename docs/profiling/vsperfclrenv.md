---
title: VSPerfCLREnv | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit dem Tool VSPerfCLREnv Umgebungsvariablen festlegen, die zum Profilen einer .NET Framework-Anwendung erforderlich sind.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 24db8e45efbe732c69dedcce8b3c1b14463a0a0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911488"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

Das VSPerfCLREnv-Tool wird verwendet, um Umgebungsvariablen festzulegen, die für die Profilerstellung einer .NET Framework-Anwendung erforderlich sind. Es verwendet die folgende Syntax:

```cmd
VsPerfCLREnv [/option]
```

Die Option, die Sie auswählen, hängt davon ab, welche der drei Typen der Profilerstellung Sie verwenden: Sampling, Instrumentierung oder die globale Profilerstellung. Eine separate Option ist erforderlich, um Ebeneninteraktionsdaten in die Profilerstellungsdaten einzuschließen. Die Syntax für jede Option wird in den folgenden Tabellen beschrieben.

> [!NOTE]
> Wenn Sie mit der Profilerstellung fertig sind, führen Sie **VSPerfCLREnv** mit der Option **/off** oder **/globaloff** aus, um die für die Profilerstellung erforderlichen Umgebungsvariablen zu löschen. Weitere Informationen finden Sie in den hier dargestellten VSPerfCLREnv-Optionen zum Löschen von Umgebungseinstellungen.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>VSPerfCLREnv-Optionen zum Einschließen von Ebeneninteraktionsdaten

> [!WARNING]
> Profilerstellungsdaten für die Ebeneninteraktion können mit einer beliebigen Visual Studio-Edition erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in Visual Studio Enterprise angezeigt werden.

Die Profilerstellung für die Ebeneninteraktion bietet zusätzliche Informationen zu ADO.NET-Abfragen in mehrstufigen Anwendungen. Es werden nur Daten für synchrone Funktionsaufrufe gesammelt. Interaktionsdaten können zu jeder Profilerstellung hinzugefügt werden, unabhängig von der Profilerstellungsmethode.

Die Optionen **InteractionOn** und **GlobalInteractionOn** aktivieren die Sammlung von Ebeneninteraktionsdaten. Die Interaktionsoption muss festgelegt werden, nachdem die Umgebungsvariable VSPerfCLREnv festgelegt wurde, die für die Profilerstellung einer Anwendung benötigt wird.

Das folgende Beispiel schließt Ebeneninteraktionsdaten in eine Profilerstellung ein, die die Samplingmethode verwendet:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Das folgende Beispiel schließt Ebeneninteraktionsdaten in eine Profilerstellung für einen Windows-Dienst ein:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>VSPerfCLREnv-Optionen zum Verarbeiten der Instrumentierungsprofilerstellung

Die folgende Tabelle beschreibt VSPerfCLREnv-Optionen für die Instrumentierungsprofilerstellung:

|Option|Beschreibung|
|------------|-----------------|
|**TraceOn**|Aktiviert die Profilerstellung mithilfe der Instrumentierungsmethode. Aktiviert nicht die Profilerstellung für die Speicherreservierung oder die Sammlung von Objektlebensdauerdaten.|
|**TraceGC**|Aktiviert die Profilerstellung für die Speicherreservierung mithilfe der Instrumentierungsmethode. Aktiviert nicht die Sammlung von Objektlebensdauerdaten.|
|**TraceGCLife**|Aktiviert die Profilerstellung für die Speicherreservierung und die Sammlung von Objektlebensdauerdaten mithilfe der Instrumentierungsmethode.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>VSPerfCLREnv-Optionen zum Verarbeiten der samplingbasierten Profilerstellung

Die folgende Tabelle beschreibt VSPerfCLREnv-Optionen für die Sampling-Profilerstellung:

|Option|Beschreibung|
|------------|-----------------|
|**SampleOn**|Aktiviert die Profilerstellung mithilfe der Samplingmethode. Aktiviert nicht die Profilerstellung für die Speicherreservierung oder die Sammlung von Objektlebensdauerdaten.|
|**SampleGC**|Aktiviert die Profilerstellung für die Speicherreservierung mithilfe der Samplingmethode. Aktiviert nicht die Sammlung von Objektlebensdauerdaten.|
|**SampleGCLife**|Aktiviert die Profilerstellung für die Speicherreservierung mithilfe der Samplingmethode. Aktiviert zudem die Sammlung von Objektlebensdauerdaten.|
|**SampleLineOff**|Deaktiviert die Sammlung von .NET-Profilerstellungsdaten auf Zeilenebene.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>VSPerfCLREnv-Optionen für die globale Profilerstellung

Um die Profilerstellung für einen verwalteten Dienst wie die ASP.NET-Webanwendung auszuführen, die vom Betriebssystem anstatt vom Benutzer gestartet wird, verwenden Sie Optionen für die globale Profilerstellung der VSPerfCLREnv-Optionen. Die folgende Tabelle beschreibt die globalen Versionen der VSPerfCLREnv-Optionen. Diese Optionen legen die geeigneten Umgebungsvariablen bei der Registrierung fest.

|Option|Beschreibung|
|------------|-----------------|
|**GlobalTraceOn**|Aktiviert die globale Profilerstellung mithilfe der Instrumentierungsmethode. Sammelt keine Speicherreservierungsereignisse oder Objektlebensdauerdaten.|
|**GlobalTraceGC**|Aktiviert die globale Profilerstellung für die Speicherreservierung mithilfe der Instrumentierungsmethode. Aktiviert nicht die Sammlung von Objektlebensdauerdaten.|
|**GlobalTraceGCLife**|Aktiviert die globale Profilerstellung für die Speicherreservierung mithilfe der Instrumentierungsmethode. Aktiviert zudem die Sammlung von Objektlebensdauerdaten.|
|**GlobalSampleOn**|Aktiviert die globale Profilerstellung mithilfe der Samplingmethode. Aktiviert nicht die Sammlung von Speicherreservierungsereignissen oder Objektlebensdauerdaten.|
|**GlobalSampleGC**|Aktiviert die globale Profilerstellung für die Speicherreservierung mithilfe der Samplingmethode. Aktiviert nicht die Sammlung von Objektlebensdauerdaten.|
|**GlobalSampleGCLife**|Aktiviert die globale Profilerstellung für die Speicherreservierung mithilfe der Samplingmethode. Aktiviert zudem die Sammlung von Objektlebensdauerdaten.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>VSPerfCLREnv-Optionen zum Löschen von Umgebungseinstellungen

 Wenn Sie mit der Profilerstellung für die verwaltete Anwendung fertig sind, verwenden Sie eine der folgenden Optionen zum Löschen der Umgebungsvariablen, die von VSPerfCLREnv hinzugefügt wurden. In der folgenden Tabelle wird beschrieben, wie sowohl Standard- als auch globale Umgebungsvariablen gelöscht werden:

|Option|Beschreibung|
|------------|-----------------|
|**Deaktiviert**|Löscht Umgebungsvariablen für die Standard-.NET-Profilerstellung. Verwenden Sie diese Option, wenn die nicht globalen VSPerfClrEnv-Optionen zum Festlegen der Profiler-Umgebungsvariablen verwendet wurden.|
|**GlobalOff**|Löscht Umgebungsvariablen für die globale .NET-Profilerstellung. Verwenden Sie diese Option, wenn die Anwendung vom Betriebssystem anstatt vom Profiler gestartet wurde.|

## <a name="remarks"></a>Bemerkungen

Diese Optionen sind für die Profilerstellung einer verwalteten Anwendung nicht erforderlich, wenn die Anwendung mithilfe des Leistungs-Explorers in der IDE gestartet wurde. Der Leistungs-Explorer legt alle erforderlichen Umgebungseinstellungen für Sie fest.

Wenn während der Profilerstellung nicht die richtige Umgebung festgelegt wurde, wird während der Analyse eine Warnung ausgegeben und die Namen der verwalteten Funktionen werden nicht ordnungsgemäß aufgelöst.

## <a name="see-also"></a>Siehe auch

[Profilerstellung über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)
