---
title: Timer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e5f6c6db903b3ecced2ac3ebc4aaa0a3e60910c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145497"
---
# <a name="timer"></a>Zeitgeber
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die „VSPerfCmd.exe“ **Timer**-Option legt das Profilerstellungsereignis fest, das für Prozessortaktzyklen gesampelt wird, und optional wird die Anzahl der Zyklen in einem Sample vom Standard 10.000.000 auf einen anderen Wert geändert. Auf einen 1-GHz-Prozessor (ein Gigahertz) entsprechen 10.000.000 Prozessortaktzyklen ungefähr 100 Samples pro Sekunde. Die Mindestanzahl an Zyklen, die sich festlegen lässt, ist 50.000.  
  
 **Timer** kann nur verwendet werden, wenn man die Sampling-Profilerstellungsmethode verwendet, und die Befehlszeile zusätzlich die **Launch** oder **Attach**-Option enthält.  
  
 Standardmäßig ist das Profiler-Samplingereignis auf Prozessortaktzyklen eingestellt und das Samplingintervall beträgt 10.000.000. Die Optionen **Timer**, **PF**, **Sys** und **Counter** ermöglichen es Ihnen, das Samplingereignis und das Samplingintervall festzulegen. Die Option **GC** sammelt die .NET-Speicherdaten bei jedem Zuordnungs- und Garbage Collection-Ereignis. In einer Befehlszeile kann nur eine dieser Optionen angegeben werden.  
  
 Das Samplingereignis und -intervall können nur in der ersten Befehlszeile festgelegt werden, die die Option **Launch** (Starten) oder **Attach** (Anfügen) enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Cycles`  
 Ein Ganzzahlwert, der die Anzahl der Prozessortaktzyklen in einem Samplingintervall festlegt. Wenn `Cycles` nicht festgelegt wurde, wird das Intervall auf 10.000.000 gesetzt. Geben Sie den Wert ohne Kommas an.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 **Timer** lassen sich nur in einer Befehlszeile festlegen, die eine der folgenden Optionen enthält.  
  
 **Starten** Sie Folgendes: `AppName`  
 Startet den Profiler und die von `AppName` festgelegten Anwendungen.  
  
 **Anfügen:**`PID`  
 Fügt den Profiler dem von der Prozess-ID (`PID`) festgelegten Prozess an.  
  
## <a name="invalid-options"></a>Ungültige Optionen  
 Die folgenden Optionen können nicht auf der selben Befehlszeile wie **Timer** festgelegt werden.  
  
 **PF**[**:** `Events` ]  
 Legt die Seitenstandards für das Samplingereignis fest und optional das Samplingintervall auf `Events`. Das standardmäßige PF-Intervall beträgt 10.  
  
 **Sys**[**:** `Events` ]  
 Legt die Betriebssystemaufrufe für das Samplingereignis fest und optional das Samplingintervall auf `Events`. Das standardmäßige Sys-Intervall beträgt 10.  
  
 **Counter**[**:** `Name,Reload,FriendlyName` ]  
 Legt das Samplingereignis auf den von `Name` festgelegten CPU-Leistungsindikator fest und das Samplingintervall auf `Reload`.  
  
 **GC**[**:**{**Allocation**|**Lifetime**}]  
 Sammelt .NET-Speicherdaten. Standardmäßig (**Zuordnung**) werden Daten bei jedem Speicher Belegungs Ereignis gesammelt. Wenn der **Lifetime** -Parameter angegeben wird, werden die Daten auch bei jedem Garbage Collection Ereignis gesammelt.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie das Profiler-Samplingintervall auf 1.000.000 Prozessortaktzyklen festgelegt wird.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)
