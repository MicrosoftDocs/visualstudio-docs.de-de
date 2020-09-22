---
title: Zusammenfassungsbericht – Samplingdaten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c759922fcd28ce0b686745fc917c02f41762cae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841159"
---
# <a name="summary-view---sampling-data"></a>Zusammenfassungsansicht – Samplingdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Zusammenfassungsansicht zeigt Informationen über die leistungsintensivsten Funktionen in einem Profilerstellungslauf. Weitere Informationen, einschließlich einer Beschreibung der Benachrichtigungslinks und Berichtslisten, finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).  
  
> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="timeline-graph"></a>Zeitachsendiagramm  
 Das Zeitachsendiagramm in der Zusammenfassungsansicht zeigt den Prozentsatz der Auslastung des Prozessors (CPU) durch die profilierte Anwendung während des Zeitraums an, in dem die Profilerstellung stattgefunden sind. Sie können das Zeitachsendiagramm zum Filtern der Ansicht in einem ausgewählten Zeitraum verwenden. Weitere Informationen finden Sie unter Gewusst [wie: Filtern von Berichts Ansichten aus der Zusammenfassungs Zeitachse](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Langsamster Pfad  
 **Langsamster Pfad** zeigt den Ausführungspfad, in dem die meisten Samples erfasst wurden. Sie können auf eine Funktion klicken, um die Ansicht „Funktionsdetails“ für die Funktion anzuzeigen. Zum Anzeigen anderer Ansichten für die Funktion klicken Sie mit rechten Maustaste auf die Funktion, und klicken Sie dann auf eine Ansicht in der Liste.  
  
 **Langsamster Pfad** umfasst die folgenden Daten für jede Funktion:  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Name**|Der Name der Funktion.|  
|**Inklusive Samplings in %**|Der Prozentsatz aller Samplings, die stattgefunden haben, wenn die Funktion oder eine von ihr aufgerufene Funktion ausgeführt wurde.|  
|**Exklusive Samplings %**|Der Prozentsatz aller Samplings, die stattgefunden haben, wenn die Funktion Code im Funktionsrumpf ausgeführt hat. In Funktionen, die von dieser Funktion aufgerufen wurden, erfasste Samplings sind nicht enthalten.|  
  
## <a name="functions-doing-most-individual-work"></a>Funktionen, die die meisten Einzelaufgaben durchführen  
 Die Liste **Funktionen mit den meisten einzelnen Aufgaben** enthält die Funktionen, die die größte Anzahl von exklusiven Samplings beim Profilerstellungslauf aufweisen. Ein exklusives Sampling wird einer Funktion zugewiesen, wenn die Funktion eigenen Code ausführt, wenn das Sampling erfasst wurde. Ein exklusives Sampling wird einer Funktion nicht zugewiesen, wenn die Funktion bei der Erfassung des Samplings eine andere Funktion aufruft. Eine große Anzahl von exklusiven Samplings gibt an, dass viel Zeit in der Funktion aufgewendet wurde.  
  
 Sie können auf eine Funktion klicken, um die Ansicht „Funktionsdetails“ für die Funktion anzuzeigen. Zum Anzeigen anderer Ansichten für die Funktion klicken Sie mit rechten Maustaste auf die Funktion, und klicken Sie dann auf eine Ansicht in der Liste.  
  
 **Funktionen mit den meisten einzelnen Aufgaben** umfasst die folgenden Daten für jede Funktion:  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Name**|Der Name der Funktion.|  
|**Exklusive Samplings %**|Der Prozentsatz aller Samplings bei der Profilerstellung, die gesammelt wurden, als die Funktion Code in ihrem Funktionsrumpf ausgeführt hat. Der Prozentsatz schließt Samplings aus, die während der Ausführung von Funktionen erfasst wurden, die von dieser Funktion aufgerufen wurden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zusammenfassungs Ansicht](../profiling/summary-view-dotnet-memory-data.md)   
 [Zusammenfassungsansicht](../profiling/summary-view-instrumentation-data.md)
