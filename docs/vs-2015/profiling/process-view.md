---
title: Prozessansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0436401c458a7d6771a2785028a8b5fe0ef57546
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180211"
---
# <a name="process-view"></a>Prozessansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Prozessansicht zeigt Profilerstellungsdaten für die Prozesse und Threads, die während der Profilerstellung ausgeführt wurden.  
  
 Prozesse werden nach Namen aufgelistet. Threads werden als untergeordnete Knoten des Prozesses aufgeführt, in dem sie erstellt wurden. Threads werden von der Funktion benannt, die den Thread gestartet hat, oder von der Bezeichnung **[ntdll.dll]** , falls keine Symbole verfügbar sind.  
  
 Klicken Sie zum Hinzufügen oder Entfernen von Spalten mit der rechten Maustaste in die Ansicht, und wählen Sie anschließend **Spalten hinzufügen/entfernen** aus. Zusätzlich können Sie die Daten durch Klicken auf einen Spaltennamen sortieren. Weitere Informationen finden Sie unter Gewusst [wie: Anpassen von Spalten in der Berichtsansicht](../profiling/how-to-customize-report-view-columns.md).  
  
 Die Spalten der Prozessansicht sind die gleichen Spalten wie für die Daten, die mithilfe der Sampling- und Instrumentierungsmethoden generiert wurden, sowie für Daten, die .NET-Speicherdaten enthalten. In der folgenden Tabelle sind die Spaltenwerte beschrieben.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Eindeutige ID**|Ein durch die Profilerstellung generierter Bezeichner, der für den Prozess oder Thread eindeutig ist.|  
|**ID**|Der von einem System generierte Bezeichner für den Prozess oder Thread.|  
|**Name**|Der Name des Prozesses oder Threads.|  
|**Anfangszeit**|Die Anzahl von Millisekunden oder Prozessorzyklen vom Anfang der Profilerstellung zum Anfang des Prozesses oder Threads.|  
|**Beendigungszeit**|Die Anzahl von Millisekunden oder Prozessorzyklen vom Anfang der Profilerstellung bis zum Anfang des Prozesses oder Threads.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)   
 [Instrumentierungs Methoden-Datenansichten](../profiling/instrumentation-method-data-views.md)   
 [.NET-Arbeitsspeicher Datenansichten](../profiling/dotnet-memory-data-views.md)
