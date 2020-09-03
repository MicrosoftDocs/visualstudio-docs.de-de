---
title: ProcessOn und ProcessOff | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 77e21a280700520b6861dd42e01a4aefa4faa704
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180202"
---
# <a name="processon-and-processoff"></a>ProcessOn und ProcessOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Unterbefehle **ProcessOff** und **ProcessOn** von „VSPerfCmd.exe“ halten die Profilerstellung für den angegebenen Prozess in einer Befehlszeilen-Profilerstellungssitzung an bzw. setzen sie fort. **ProcessOff** stoppt die Profilerstellung des Prozesses, und **ProcessOn** startet sie.  
  
 In den meisten Fällen geben Sie **ProcessOn** oder **ProcessOff** als einzige Option in einer VSPerfCmd.exe-Befehlszeile an. Sie können aber auch mit den Unterbefehlen **GlobalOn**, **GlobalOff**, **ThreadOn** und **ThreadOff** kombiniert werden.  
  
 Die Unterbefehle **ProcessOn** und **ProcessOff** interagieren mit den Unterbefehlen **GlobalOn** und **GlobalOff**, die die Datensammlung für alle Prozesse in einer Befehlszeilen-Profilerstellungssitzung steuern. Sie interagieren außerdem mit den Unterbefehlen **ThreadOn** und **ThreadOff**, die die Datensammlung für einen angegebenen Thread steuern.  
  
 Die Unterbefehle **ProcessOff** und **ProcessOn** haben außerdem Auswirkungen auf die Start/Stop-Zähler von Prozessen, der von den Profiler-API-Funktionen bearbeitet wird.  
  
- **ProcessOff** legt die Start/Stop-Zähler sofort auf 0 (null) fest und hält die Profilerstellung daher an.  
  
- **ProcessOff** legt die Start/Stop-Zähler sofort auf 1 fest und setzt die Profilerstellung daher fort.  
  
  Weitere Informationen finden Sie unter [APIs für Profilerstellungstools](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `PID`  
 Der ganzzahlige Bezeichner des Prozesses zum Starten oder Beenden. Prozess-IDs werden auf der Registerkarte „Prozesse“ des Windows Task-Managers aufgeführt.  
  
## <a name="required-subcommands"></a>Erforderliche Unterbefehle  
 Keine  
  
## <a name="valid-subcommands"></a>Gültige Unterbefehle  
 **ProcessOn** und **ProcessOff** können in Befehlszeilen angegeben werden, die auch die folgenden Unterbefehle enthalten:  
  
 **Start:**`Method`  
 Initialisiert die Profilerstellungssitzung in der Befehlszeile und legt die angegebene Profilerstellungsmethode fest  
  
 **Starten** Sie Folgendes: `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
 **Anfügen:**`PID`  
 Startet die Profilerstellung für den angegebenen Prozess  
  
 **GlobalOff**|**GlobalOn**  
 Beendet oder startet die Profilerstellung für alle Prozesse in einer Befehlszeilen-Profilerstellungssitzung  
  
 {**ThreadOff**&#124;**THREADON**} **:**`TID`  
 Beendet oder beginnt die Profilerstellung für den angegebenen Thread (nur Instrumentierungsmethode)  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden mit dem Unterbefehl **ProcessOff** Profilerstellungsdaten für den Start der Anwendung gesammelt.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)
