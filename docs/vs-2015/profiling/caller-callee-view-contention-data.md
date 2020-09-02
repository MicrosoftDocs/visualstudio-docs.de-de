---
title: 'Ansicht der Aufrufer/Aufgerufenen: Konfliktdaten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f60e8eedeeb7106a7a95a33a4a5cc794194861c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164566"
---
# <a name="caller--callee-view----contention-data"></a>Ansicht der Aufrufer/Aufgerufenen – Konfliktdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Ansicht der Aufrufer/Aufgerufenen werden Konfliktinformationen für eine ausgewählte Funktion und deren übergeordnete und untergeordnete Funktionen angezeigt. Die Aufrufer-/Aufgerufener-Ansicht enthält drei Raster.  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt, und zeigt Konfliktinformationen für die ausgewählte Funktion an. Die Werte umfassen alle blockierenden Konflikte der Funktion.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und gibt die einzelnen Beiträge der (übergeordneten) Aufruferfunktion zu den Werten der ausgewählten (aktuellen) Funktion an.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im unteren Raster angezeigt, und gibt Konfliktinformationen für die aufgerufene Funktion (untergeordnete Funktion) der ausgewählten Funktion an, als die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Type**|Der Kontext der Funktion:<br /><br /> -   **0** – die aktuelle Funktion<br />-   **1** – eine Funktion, die die aktuelle Funktion aufruft<br />-   **2** – eine Funktionen, die von der aktuellen Funktion aufgerufen wird<br /><br /> Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|  
|**Exklusive blockierte Zeit %**|– Bei einer aktuellen Funktion die Zeit, für die die Funktion vom Ausführen von Code im Funktionsrumpf abgehalten wurde. Dies umfasst nicht die blockierte Zeit für Funktionen, die von dieser Funktion aufgerufen wurden.<br />– Bei einer aufrufenden Funktion der Anteil der exklusiven blockierten Zeit der aktuellen Funktion, als diese Funktion die aktuelle Funktion aufgerufen hat.<br />– Bei einer aufgerufenen Funktion die Zeit, während der diese Funktion ihren eigenen Code nicht ausführen konnte, als diese Funktion von der aktuellen Funktion aufgerufen wurde. Dies umfasst nicht die blockierte Zeit für untergeordnete Funktionen, die von dieser aufgerufenen Funktion aufgerufen wurden.|  
|**Exklusive blockierte Zeit %**|Der Anteil der gesamten blockierten Zeit bei der Profilerstellung, die der exklusiven blockierten Zeit für diese Funktion in diesem Kontext entspricht.|  
|**Exklusive Konflikte**|– Bei einer aktuellen Funktion die Anzahl der Blockierungen der Ausführung von Code im Funktionsrumpf durch diese Funktion. Dies umfasst nicht die Konflikte, die in Funktionen aufgetreten sind, die von dieser Funktion aufgerufen wurden.<br />– Bei einer aufrufenden Funktion die Anzahl von exklusiven Konflikten der aktuellen Funktion, die aufgetreten sind, als diese Funktion die aktuelle Funktion aufgerufen hat.<br />– Bei einer aufgerufenen Funktion die Anzahl der Blockierungen der Ausführung des Codes dieser Funktion, als diese Funktion von der aktuellen Funktion aufgerufen wurde. Dies umfasst nicht die Konflikte, die in Funktionen auftraten, die von der aufgerufenen Funktion aufgerufen wurden.|  
|**Exklusive Konflikte %**|Der Anteil aller Konflikte bei der Profilerstellung, die als exklusive Ausnahmen dieser Funktion in diesem Kontext aufgetreten sind.|  
|**Funktionsadresse**|Die Funktionsadresse oder das Token.|  
|**Funktionsname**|Der vollqualifizierte Name der Funktion.|  
|**Inklusive blockierte Zeit**|– Bei einer aktuellen Funktion die Zeit, als diese Funktion oder eine von ihr aufgerufene andere Funktion nicht ausgeführt werden konnte. Dies umfasst die blockierte Zeit für Funktionen, die von der aktuellen Funktion aufgerufen wurden.<br />– Für eine aufrufende Funktion der Anteil der inklusiven blockierten Zeit für die aktuelle Funktion, die aufgetreten ist, als diese Funktion die aktuelle Funktion aufgerufen hat.<br />– Bei einer aufgerufenen Funktion die Zeit, als diese Funktion oder eine der Funktionen, die von dieser Funktion aufgerufen wurden, nicht ausgeführt werden konnte, als diese Funktion von der aktuellen Funktion aufgerufen wurde. Diese umfasst die blockierte Zeit für Funktionen, die von dieser aufgerufenen Funktion aufgerufen wurden.|  
|**Inklusive blockierte Zeit %**|Der Anteil der gesamten blockierten Zeit bei der Profilerstellung, die der inklusiven blockierten Zeit für diese Funktion in diesem Kontext entspricht.|  
|**Inklusive Konflikte %**|– Bei einer aktuellen Funktion die Anzahl wie oft diese Funktion oder eine der von ihr aufgerufenen Funktionen nicht ausgeführt werden konnten. Umfasst die Konflikte in Funktionen, die von dieser Funktion aufgerufen wurden.<br />– Bei einer aufrufenden Funktion die Anzahl von vollständigen Konflikten der aktuellen Funktion, die aufgetreten sind, als diese Funktion die aktuelle Funktion aufgerufen hat.<br />– Bei einer aufgerufenen Funktion die Anzahl wie oft diese Funktion oder eine der Funktionen, die von dieser Funktion aufgerufen wurden, nicht ausgeführt werden konnten, als diese Funktion von der aktuellen Funktion aufgerufen wurde. Konflikte, die in Funktionen auftraten, die von der aufgerufenen Funktion aufgerufen wurden, werden einbezogen.|  
|**Inklusive Konflikte %**|Der Anteil aller Konflikte bei der Profilerstellung, die als exklusive Ausnahmen dieser Funktion in diesem Kontext aufgetreten sind.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess-ID**|Die Prozess-ID (PID) des Prozesses, in dem die Konflikte aufgetreten sind.|  
|**Prozessname**|Der Prozessname.|  
|**Name der Stammfunktion**|Der Name der aktuellen Funktion. Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Anpassen von Spalten in der Berichtsansicht](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufer/aufgerufene Ansicht](../profiling/caller-callee-view.md)   
 [Aufrufer-/aufgerufeneransicht-Samplings](../profiling/caller-callee-view-sampling-data.md)   
 [Aufrufer-/Aufgerufener-Ansicht-Speicher Instrumentations Daten](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Aufrufer-/Aufgerufener-Ansicht-.NET-Arbeitsspeicher](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Aufrufer-/Aufgerufener-Ansicht](../profiling/caller-callee-view-instrumentation-data.md)
