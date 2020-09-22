---
title: PF | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 243d5fada7342bc05d8768a7e33cca6f55e309ef
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2020
ms.locfileid: "90841101"
---
# <a name="pf"></a>PF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die VSPerfCmd.exe-Option **PF** legt das Profilerstellungsereignis fest, das auf Seitenfehler gesampelt wird, und optional wird die Anzahl der Zyklen in einem Samplingintervall vom Standard „10“ auf einen anderen Wert geändert.  
  
> [!NOTE]
> PF kann nicht in 64-Bit-Systemen verwendet werden.  
  
 **Hinweis:****PF** wird auf 64-Bit-Computern nicht unterstützt und kann nur in einer Befehlszeile verwendet werden, die auch die Optionen **Launch** oder **Attach** enthält.  
  
 Standardmäßig ist das Samplingereignis auf angehaltene Prozessortaktzyklen festgelegt und das Samplingintervall auf 10.000.000. Die Optionen **Timer**, **PF**, **Sys** und **Counter** ermöglichen es Ihnen, das Samplingereignis und das Samplingintervall festzulegen. Die Option **GC** sammelt die .NET-Speicherdaten bei jedem Zuordnungs- und Garbage Collection-Ereignis. In einer Befehlszeile kann nur eine dieser Optionen angegeben werden.  
  
 Das Samplingereignis und -intervall können nur in der ersten Befehlszeile festgelegt werden, die die Option **Launch** oder **Attach** enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Parameter  
 `Events`  
 Ein ganzzahliger Wert, der die Anzahl der Seitenfehlerereignisse in einem Samplingintervall angibt. Wenn `Events` nicht festgelegt wurde, wird das Intervall auf 10 festgelegt.  
  
## <a name="required-options"></a>Erforderliche Optionen  
 **PF** kann nur in einer Befehlszeile festgelegt werden, die eine der folgenden Optionen enthält.  
  
 **Starten** Sie Folgendes: `AppName`  
 Startet den Profiler und die von AppName festgelegten Anwendungen  
  
 **Anfügen:**`PID`  
 Fügt den Profiler an den von AppName angegebenen Prozess an  
  
## <a name="invalid-options"></a>Ungültige Optionen  
 Die folgenden Optionen können nicht in derselben Befehlszeile wie **PF** angegeben werden.  
  
 **Timer**[**:** `Cycles` ]  
 Legt das Samplingereignis auf die Prozessortaktzyklen und das Samplingintervall optional auf `Cycles` fest. Das Timer-Standardintervall beträgt 10.000.000.  
  
 **Sys**[**:** `Events` ]  
 Legt das Samplingereignis auf Aufrufe von der Anwendung mit Profil auf den Betriebssystemkernel (syscalls) und das Samplingintervall optional auf `Events` fest. Das standardmäßige Sys-Intervall beträgt 10.  
  
 **Counter:** `Name` [`,Reload`[`,FriendlyName`]]  
 Legt das Samplingereignis auf den von `Name` festgelegten CPU-Leistungsindikator fest und das Samplingintervall auf `Reload`.  
  
 **GC**[**:**{**Allocation**|**Lifetime**}]  
 Sammelt .NET-Speicherdaten. Standardmäßig (**Zuordnung**) werden Daten bei jedem Speicher Belegungs Ereignis gesammelt. Wenn der **Lifetime** -Parameter angegeben wird, werden die Daten auch bei jedem Garbage Collection Ereignis gesammelt.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird veranschaulicht, wie das Profilerstellungs-Samplingereignis auf Seitenfehler festgelegt und das Samplingintervall auf 20 Seitenfehler festgelegt wird.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)
