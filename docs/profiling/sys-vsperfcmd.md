---
title: Sys (VSPerfCmd) | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur VSPerfCmd.exe-Option. Diese legt das Profilerstellungsereignis, für das ein Sampling durchgeführt wird, auf Systemaufrufereignisse fest.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 66815265544afdee263490ed5eec92301911e3cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868165"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
Die *VSPerfCmd.exe-Option* **Sys** legt das Profilerstellungsereignis fest, für das ein Sampling für Aufrufereignisse (Funktionsaufrufe des Betriebssystems der Anwendung mit einem Profil) durchgeführt werden soll, und ändert optional die Anzahl der Systemaufrufe (standardmäßig 10) in einem Samplingintervall.

 **Sys** kann nur in einer Befehlszeile verwendet werden, die auch die Optionen **Launch** (Starten) und **Attach** (Anfügen) enthält.

 Standardmäßig ist das Profiler-Samplingereignis auf Prozessortaktzyklen eingestellt und das Samplingintervall beträgt 10.000.000. Die Optionen **Timer**, **PF**, **Sys** und **Counter** ermöglichen es Ihnen, das Samplingereignis und das Samplingintervall festzulegen. Die Option **GC** sammelt die .NET-Speicherdaten bei jedem Zuordnungs- und Garbage Collection-Ereignis. In einer Befehlszeile kann nur eine dieser Optionen angegeben werden.

 Das Samplingereignis und -intervall können nur in der ersten Befehlszeile festgelegt werden, die die Option **Launch** (Starten) oder **Attach** (Anfügen) enthält.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Parameter
 `Events`: ist ein ganzzahliger Wert, der die Anzahl der Systemaufrufe in einem Samplingintervall angibt. Wenn `Events` nicht festgelegt wurde, wird das Intervall auf 10 festgelegt.

## <a name="required-options"></a>Erforderliche Optionen
 Für **Sys** ist eine der folgenden Optionen erforderlich.

 **Launch:** `AppName` startet den Profiler und die von `AppName` festgelegte Anwendung.

 **Attach:** `PID` fügt den Profiler an den von `PID` angegebenen Prozess an.

## <a name="invalid-options"></a>Ungültige Optionen
 Die folgenden Optionen können nicht in derselben Befehlszeile wie **Sys** festgelegt werden.

 **PF**[ **:** `Events`]: legt die Seitenstandards für das Samplingereignis und optional das Samplingintervall auf `Events` fest. Das standardmäßige PF-Intervall beträgt 10.

 **Timer**[ **:** `Cycles`]: legt das Samplingereignis auf die Prozessortaktzyklen und das Samplingintervall optional auf `Cycles` fest. Das Timer-Standardintervall beträgt 10.000.000.

 **Counter:** `Name`[`,Reload`[`,FriendlyName`]] legt das Samplingereignis auf den von `Name` festgelegten CPU-Leistungsindikator und das Samplingintervall auf `Reload` fest.

 **GC**[**:**{**Allocation**&#124;**Lifetime**}]: erfasst .NET-Arbeitsspeicherdaten. Wenn der Parameter **Allocation** angegeben wird (Standard), werden Daten bei jedem Speicherbelegungsereignis gesammelt. Wenn jedoch der **Lifetime**-Parameter angegeben wird, werden die Daten auch bei jedem Garbage Collection-Ereignis gesammelt.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird dargestellt, wie das Profilersamplingereignis auf Symstemaufrufe und das Samplingintervall auf 20 Aufrufe pro Beispiel festgelegt wird.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
