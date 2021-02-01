---
title: Timer | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur VSperfCmd.exe-Option „Timer“. Diese legt das Profilerstellungsereignis, für das ein Sampling durchgeführt wurde, auf Prozessortaktzyklen fest.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 908685b49a08b3084c31e768675e64bc087bc727
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722437"
---
# <a name="timer"></a>Timer
Die *VSPerfCmd.exe* **Timer**-Option legt das Profilerstellungsereignis fest, das für Prozessortaktzyklen gesampelt wird, und optional wird die Anzahl der Zyklen in einem Sample vom Standard 10.000.000 auf einen anderen Wert geändert. Auf einen 1-GHz-Prozessor (ein Gigahertz) entsprechen 10.000.000 Prozessortaktzyklen ungefähr 100 Samples pro Sekunde. Die Mindestanzahl an Zyklen, die sich festlegen lässt, ist 50.000.

 **Timer** kann nur verwendet werden, wenn man die Sampling-Profilerstellungsmethode verwendet, und die Befehlszeile zusätzlich die **Launch** oder **Attach**-Option enthält.

 Standardmäßig ist das Profiler-Samplingereignis auf Prozessortaktzyklen eingestellt und das Samplingintervall beträgt 10.000.000. Die Optionen **Timer**, **PF**, **Sys** und **Counter** ermöglichen es Ihnen, das Samplingereignis und das Samplingintervall festzulegen. Die Option **GC** sammelt die .NET-Speicherdaten bei jedem Zuordnungs- und Garbage Collection-Ereignis. In einer Befehlszeile kann nur eine dieser Optionen angegeben werden.

 Das Samplingereignis und -intervall können nur in der ersten Befehlszeile festgelegt werden, die die Option **Launch** (Starten) oder **Attach** (Anfügen) enthält.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>Parameter
 `Cycles`: ist ein ganzzahliger Wert, der die Anzahl der Prozessortaktzyklen in einem Samplingintervall angibt. Wenn `Cycles` nicht festgelegt wurde, wird das Intervall auf 10.000.000 gesetzt. Geben Sie den Wert ohne Kommas an.

## <a name="required-options"></a>Erforderliche Optionen
 **Timer** lassen sich nur in einer Befehlszeile festlegen, die eine der folgenden Optionen enthält.

 **Launch:** `AppName` startet den Profiler und die von `AppName` festgelegte Anwendung.

 **Attach:** `PID` fügt den Profiler dem von der Prozess-ID (`PID`) festgelegten Prozess an.

## <a name="invalid-options"></a>Ungültige Optionen
 Die folgenden Optionen können nicht auf der selben Befehlszeile wie **Timer** festgelegt werden.

 **PF**[ **:** `Events`]: legt die Seitenstandards für das Samplingereignis und optional das Samplingintervall auf `Events` fest. Das standardmäßige PF-Intervall beträgt 10.

 **Sys**[ **:** `Events`]: legt die Betriebssystemaufrufe für das Samplingereignis und optional das Samplingintervall auf `Events` fest. Das standardmäßige Sys-Intervall beträgt 10.

 **Counter**[ **:** `Name,Reload,FriendlyName`]: legt das Samplingereignis auf den von `Name` festgelegten CPU-Leistungsindikator und das Samplingintervall auf `Reload` fest.

 **GC**[**:**{**Allocation**&#124;**Lifetime**}]: erfasst .NET-Arbeitsspeicherdaten. Wenn der Parameter **Allocation** angegeben wird (Standard), werden Daten bei jedem Speicherbelegungsereignis gesammelt. Wenn jedoch der **Lifetime**-Parameter angegeben wird, werden die Daten auch bei jedem Garbage Collection-Ereignis gesammelt.

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt, wie das Profiler-Samplingintervall auf 1.000.000 Prozessortaktzyklen festgelegt wird.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
