---
title: Sys (VSPerfCmd) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 981b37fe1ebaad5e45f0308143ab0384ef1d559b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145603"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die „VSPerfCmd.exe“-Option **Sys** legt das Profilerstellungereignis fest, für das ein Sampling für Aufrufereignisse (Funktionsaufrufe des Betriebssystems der Anwendung mit einem Profil) durchgeführt werden soll, und ändert optional die Anzahl der Systemaufrufe (standardmäßig 10) in einem Samplingintervall.  
  
 **Sys** kann nur in einer Befehlszeile verwendet werden, die auch die Optionen **Launch** (Starten) und **Attach** (Anfügen) enthält.  
  
 Standardmäßig ist das Profiler-Samplingereignis auf Prozessortaktzyklen eingestellt und das Samplingintervall beträgt 10.000.000. Die Optionen **Timer**, **PF**, **Sys** und **Counter** ermöglichen es Ihnen, das Samplingereignis und das Samplingintervall festzulegen. Die Option **GC** sammelt die .NET-Speicherdaten bei jedem Zuordnungs- und Garbage Collection-Ereignis. In einer Befehlszeile kann nur eine dieser Optionen angegeben werden.  
  
 Das Samplingereignis und -intervall können nur in der ersten Befehlszeile festgelegt werden, die die Option **Launch** (Starten) oder **Attach** (Anfügen) enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Events`  
 Ein ganzzahliger Wert, der die Anzahl der Systemaufrufe in einem Samplingintervall angibt. Wenn `Events` nicht festgelegt wurde, wird das Intervall auf 10 festgelegt.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 Für **Sys** ist eine der folgenden Optionen erforderlich.  
  
 **Starten** Sie Folgendes: `AppName`  
 Startet den Profiler und die von `AppName` festgelegten Anwendungen.  
  
 **Anfügen:**`PID`  
 Fügt den Profiler an den von `PID` angegebenen Prozess an.  
  
## <a name="invalid-options"></a>Ungültige Optionen  
 Die folgenden Optionen können nicht in derselben Befehlszeile wie **Sys** festgelegt werden.  
  
 **PF**[**:** `Events` ]  
 Legt die Seitenstandards für das Samplingereignis fest und optional das Samplingintervall auf `Events`. Das standardmäßige PF-Intervall beträgt 10.  
  
 **Timer**[**:** `Cycles` ]  
 Legt das Samplingereignis auf die Prozessortaktzyklen und das Samplingintervall optional auf `Cycles` fest. Das Timer-Standardintervall beträgt 10.000.000.  
  
 **Counter:** `Name` [`,Reload`[`,FriendlyName`]]  
 Legt das Samplingereignis auf den von `Name` festgelegten CPU-Leistungsindikator fest und das Samplingintervall auf `Reload`.  
  
 **GC**[**:**{**Allocation**|**Lifetime**}]  
 Sammelt .NET-Speicherdaten. Standardmäßig (**Zuordnung**) werden Daten bei jedem Speicher Belegungs Ereignis gesammelt. Wenn der **Lifetime** -Parameter angegeben wird, werden die Daten auch bei jedem Garbage Collection Ereignis gesammelt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird dargestellt, wie das Profilersamplingereignis auf Symstemaufrufe und das Samplingintervall auf 20 Aufrufe pro Beispiel festgelegt wird.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)
