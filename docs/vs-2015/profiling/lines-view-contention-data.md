---
title: Zeilenansicht - Konfliktdaten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cb6b8191b39bfc79615bf0bbcd4fb469395f8d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62583157"
---
# <a name="lines-view---contention-data"></a>Zeilenansicht - Konfliktdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Zeilenansicht der Konfliktdaten werden die Leistungsdaten für die Anweisungen aufgeführt, die ausgeführt wurden, als die Samplings bei der Profilerstellung erfasst wurden. In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.  
  
 Eine Anweisung wird mit den folgenden Daten identifiziert:  
  
- Die Quelldatei, die die Funktionsanweisung enthält.  
  
- Die Funktion, die die Anweisung enthält.  
  
- Die Quellzeile, an der die Anweisung beginnt.  
  
- Das Zeichen in der Quellzeile, an dem die Anweisung beginnt.  
  
- Die Quellzeile, an der die Anweisung endet.  
  
- Das Zeichen in der Quellzeile, an dem die Anweisung endet.  
  
  Die Zeilennamensspalte, die eine sortierbare Verkettung der Bezeichnerdaten bereitstellt.  
  
  In der folgenden Tabelle werden die Spalten des Zeilenansichtsberichts beschrieben.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Exklusive blockierte Zeit**|Die Zeitspanne, während der diese Anweisung bei der Ausführung eines Codes in der Anweisung aufgrund eines Konfliktereignisses blockiert wurde. Blockierte Zeit in Funktionen, die von der Anweisung aufgerufen wurden, ist nicht enthalten.|  
|**Exklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit im Prozess, die exklusive blockierte Zeit der Anweisung war.|  
|**Exklusive Konflikte**|Die Anzahl des Vorkommens, während der diese Anweisung bei der Ausführung eines Codes in der Anweisung aufgrund eines Konfliktereignisses blockiert wurde. Konfliktereignisse in Funktionen, die von der Anweisung aufgerufen wurden, sind nicht enthalten.|  
|**Exklusive Konflikte %**|Der Prozentsatz aller Konfliktereignisse im Prozess, die exklusive Konflikte dieser Anweisung waren.|  
|**Funktionsadresse**|Die Adresse der Funktion, die diese Anweisung enthält.|  
|**Funktionsname**|Der vollqualifizierte Name der Funktion, die diese Anweisung enthält.|  
|**Inklusive blockierte Zeit**|Die blockierte Zeit in dieser Anweisung und Funktionen, die in der Anweisung aufgerufen wurden.|  
|**Inklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit im Prozess, die inklusive blockierte Zeit der Anweisung war.|  
|**Inklusive Konflikte**|Die Anzahl des Vorkommens, dass diese Anweisung und Funktionen, die in der Anweisung aufgerufen wurden, bei der Ausführung blockiert wurden.|  
|**Inklusive Konflikte %**|Der Prozentsatz aller Konfliktereignisse im Prozess, die inklusive Konflikte dieser Anweisung waren.|  
|**Zeilenname**|Ein vom Profiler generierter Bezeichner der Zeile. Der Bezeichner verwendet folgende Syntax:`SourceFile` **;[** `LineNumberStart` **,** `CharacterStart` **]->;[** `LineNumberEnd` **,** `CharacterEnd` **]**|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Anweisung enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält.|  
|**Prozess-ID**|Die Prozess-ID (PID) des Profilerstellungsprozesses.|  
|**Prozessname**|Der Prozessname.|  
|**Quellanfangszeichen**|Der Offset des Startzeichens in der Quelldateizeile, an dem diese Anweisung beginnt.|  
|**Quellendzeichen**|Der Offset des Startzeichens in der Quelldateizeile, an dem diese Anweisung endet.|  
|**Quelldatei**|Der Name der Quelldatei, die die Funktionsanweisung enthält.|  
|**Quellanfangszeile**|Die Zeilennummer in der Quelldatei, bei der die Anweisung beginnt.|  
|**Quellendzeile**|Die Zeilennummer in der Quelldatei, bei der die Anweisung endet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Anpassen von Spalten in der Berichtsansicht](../profiling/how-to-customize-report-view-columns.md)   
 [Zeilen Ansicht](../profiling/lines-view.md)   
 [Zeilen Ansicht-Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Zeilenansicht](../profiling/lines-view-sampling-data.md)
