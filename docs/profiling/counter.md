---
title: Counter | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Option „Counter“ von VSPerfCmd.exe. Diese Option gibt entweder ein Samplingintervall an oder misst bei der Profilerstellung durch Instrumentierung Ereignisintervalle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 85ed799cac54d630dfff1b285d3f2257e5eb99b5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720695"
---
# <a name="counter"></a>Leistungsindikator
Die Option **Counter** sammelt Daten von Leistungsindikatoren für Prozessoren (Hardware).

- Wenn Sie die Sampling-Profilerstellung (Methode) verwenden, gibt **Counter** den Chipleistungsindikator und die Anzahl der Zählerereignisse an, die als Samplingintervall verwendet werden sollen. Sie können nur einen Zähler angeben, wenn Sie Sampling verwenden.

- Bei der Profilerstellung für die Instrumentierung (Methode) wird die Anzahl der Zählerereignisse, die im Intervall zwischen den vorherigen und den aktuellen Auflistungsereignissen aufgetreten sind, als separate Felder in Profiler-Berichten aufgeführt. Mehrere **Counter**-Optionen können angegeben werden, wenn Sie die Instrumentierung verwenden.

  Jeder Prozessortyp hat eigene Hardware-Leistungsindikatoren. Der Profiler definiert mehrere generische Leistungsindikatoren, die für fast alle Prozessoren verwendet werden. Um die generischen und prozessorspezifischen Leistungsindikatoren auf dem Computer aufzulisten, verwenden Sie den VSPerfCmd-Befehl **QueryCounters**.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parameter
 `Name`: der Name des Indikators. Mit dem VSPerfCmd.exe-Befehl **QueryCounters** können Sie den Namen der verfügbaren Leistungsindikatoren auf dem Computer auflisten.

 `Reload`: die Anzahl der Indikatorereignisse im Samplingintervall. Verwenden Sie sie nicht mit der Instrumentierungsmethode.

 `FriendlyName` (Optional): Dies ist die Zeichenfolge, die Sie anstelle von `Name` in den Spaltenüberschriften von Profilerberichten und Ansichten verwenden sollten.

## <a name="required-options"></a>Erforderliche Optionen
 Die „Counter“-Option kann nur mit einer der folgenden Optionen verwendet werden:

 **Start:** `Trace` initialisiert den Profiler für die Verwendung der Instrumentierungsmethode.

 **Launch:** `AppName` startet die angegebene Anwendung und den Profiler. Der Profiler muss für die Verwendung der Samplingmethode initialisiert werden.

 **Attach:** `PID` startet den Profiler und fügt ihn dem von der Prozess-ID angegebenen Prozess an. Der Profiler muss für die Verwendung der Samplingmethode initialisiert werden.

## <a name="example"></a>Beispiel
 Das Beispiel mit der Samplingmethode veranschaulicht, wie eine Anwendung bei jedem tausendsten Vorkommen des generischen Profilerzählers „NonHaltedCycles“ überprüft wird.

 Die Instrumentierungsmethode veranschaulicht, wie der Profiler für das Sammeln von L2InstructionFetches-Leistungsindikatorereignissen initialisiert wird. Der Name des L2InstructionFetches-Zählers ist für jeden Prozessor eindeutig.

```cmd
; Sample Method Example
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"

;INSTRUMENTATION METHOD EXAMPLE
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
