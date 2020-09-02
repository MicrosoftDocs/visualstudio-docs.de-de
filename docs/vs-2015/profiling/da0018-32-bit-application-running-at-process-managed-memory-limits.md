---
title: 'DA0018: 32-Bit-Anwendung wird an den vom Prozess verwalteten Speicherlimits ausgeführt | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d3247fb421800f87740a911563880b70abf3eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844733"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: 32-Bit-Anwendung wird an den vom Prozess verwalteten Speicherlimits ausgeführt.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-ID | DA0018 |  
| Kategorie | Profilerstellungstools Verwendung |  
| Profil Erstellungs Methode | Stichprobenentnahme |  
| Meldung | Verwaltete Speicher Belegungen nähern sich dem Standard Limit für einen 32-Bit-Prozess an. Die Anwendung ist möglicherweise speichergebunden.|  
| Regeltyp | Warnung |  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="cause"></a>Ursache  
 Die bei der Profilerstellung erfassten Systemdaten deuten darauf hin, dass sich die .NET Framework-Arbeitsspeicherheaps der maximalen Größe angenähert haben, die verwaltete Heaps in einem 32-Bit-Prozess erreichen können. Diese maximale Größe ist ein Standardwert. Er basiert auf der Gesamtmenge des Prozessadressbereichs, der für private Bytes belegt werden kann. Der gemeldete Wert ist der Maximalwert der Heaps, der ermittelt wurde, während der Prozess aktiv war, dessen Profil erstellt wurde. Wiederholen Sie die Profilerstellung mit der Methode zur .NET-Speicherprofilerstellung, und optimieren Sie die Verwendung verwalteter Ressourcen durch die Anwendung.  
  
 Wenn sich die Größe der verwalteten Heaps dem Standardlimit nähert, muss unter Umständen die automatische Garbage Collection häufiger aufgerufen werden. Dadurch vergrößert sich der Mehraufwand für die Speicherverwaltung.  
  
 Die Regel wird nur für 32-Bit-Anwendungen ausgelöst, die auf 32-Bit-Computern ausgeführt werden.  
  
## <a name="rule-description"></a>Beschreibung der Regel  
 Die Microsoft .NET-CLR (Common Language Runtime) verfügt über einen automatischen Speicherverwaltungsmechanismus, durch den der Speicher von Objekten, die von der Anwendung nicht mehr verwendet werden, mithilfe eines Garbage Collectors freigegeben wird. Der Garbage Collector ist generationsorientiert, da angenommen wird, dass viele Speicherbelegungen kurzlebig sind. Lokale Variablen müssen beispielsweise kurzlebig sein. Neu erstellte Objekte beginnen in Generation 0 (gen 0) und werden zu Generation 1, wenn sie nach einer Ausführung der Garbage Collection noch vorhanden sind, und schließlich zu Generation 2, wenn sie von der Anwendung auch weiterhin verwendet werden.  
  
 Verwaltete Objekte, die größer als 85 KB sind, werden dem Heap für große Objekte zugewiesen. Dort werden Garbage Collections und Komprimierungen seltener ausgeführt als bei kleineren Objekten. Große Objekte werden separat verwaltet, da angenommen wird, dass sie beständiger sind, und da das Mischen von beständigen und großen Objekten mit häufig zugewiesenen kleineren Objekten zu einer starken Fragmentierung des Heaps führen kann.  
  
 Wenn sich die Gesamtgröße der verwalteten Heaps dem Standardlimit nähert, nimmt der Mehraufwand für die Speicherverwaltung häufig so weit zu, dass sich dies negativ auf die Reaktionszeit und die Skalierbarkeit der Anwendung auswirkt.  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur Ansicht [Markierungen](../profiling/marks-view.md) zu navigieren. Suchen Sie die Spalten **.NET CLR-Speicher\\Anzahl der Bytes in den Heaps** und **Festgelegte Bytes insgesamt**. Überprüfen Sie, ob die Zuordnung von verwaltetem Speicher in bestimmten Phasen der Programmausführung besonders häufig auftritt. Vergleichen Sie die Werte der Spalte **Anzahl der Bytes in den Heaps**  der Garbage Collection-Rate aus den Spalten **.NET CLR-Speicher\\Auflistungsanzahl der Generation 0**, **.NET CLR-Speicher\\der Generation 1** und **.NET CLR-Speicher\\der Generation 2**, um zu ermitteln, ob sich das Muster der verwalteten Speicherbelegung auf die Garbage Collection-Rate auswirkt.  
  
 In einer .NET Framework-Anwendung wird die Gesamtgröße der verwalteten Heaps durch die Common Language Runtime auf einen Wert beschränkt, der knapp der halben Maximalgröße des privaten Teils eines Prozessadressbereichs entspricht. Bei einem 32-Bit-Prozess, die auf einem 32-Bit-Computer ausgeführt werden, beträgt die Obergrenze des privaten Teils des Prozessadressbereichs 2 GB. Wenn sich die Gesamtgröße der verwalteten Heaps dem Standardlimit nähert, nimmt unter Umständen der Mehraufwand für die Verwaltung des Arbeitsspeichers zu, während die Leistung der Anwendung abnimmt.  
  
 Wenn ein hoher Speicherverwaltungsaufwand ein Problem ist, ziehen Sie eine der folgenden Optionen in Betracht:  
  
- Optimieren Sie die Verwendung verwalteter Speicherressourcen durch die Anwendung.  
  
   - oder -  
  
- Umgehen Sie die architektonischen Einschränkungen für die maximale Größe von virtuellem Arbeitsspeicher für 32-Bit-Prozesse.  
  
  Wenn Sie die Verwendung von verwalteten Speicherressourcen optimieren möchten, sammeln Sie im Rahmen einer .NET-Speicherbelegungsprofilerstellung Daten zur verwalteten Speicherbelegung. Überprüfen Sie die Berichte der .net-Arbeits [Speicherdaten Sichten](../profiling/dotnet-memory-data-views.md) , um das Muster der Speicher Belegung der Anwendung zu verstehen.  
  
  Verwenden Sie die [Objekt Lebensdauer-Ansicht](../profiling/object-lifetime-view.md) , um zu bestimmen, welche der Datenobjekte des Programms in Generierung verbleiben und dann von dort aus freigegeben werden.  
  
  Ermitteln Sie mithilfe der [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md) den Ausführungspfad, der zu diesen Speicherbelegungen geführt hat.  
  
  Weitere Informationen zur Verbesserung der Garbage Collection-Leistung finden Sie im technischen Artikel [Garbage Collector-Grundlagen und Tipps zur Leistung](https://msdn.microsoft.com/library/ms973837.aspx) zu .NET Framework auf der MSDN-Website.  
  
  Wenn Sie den architektonischen Einschränkungen für virtuellen Arbeitsspeicher hinsichtlich der Größe des privaten Teils eines Prozessadressbereichs entgehen möchten, führen Sie diesen 32-Bit-Prozess auf einem 64-Bit-Computer aus.  Einem 32-Bit-Prozess stehen auf einem 64-Bit-Computer bis zu 4 GB an privatem, virtuellem Arbeitsspeicher zur Verfügung.  
  
  Einem 64-Bit-Prozess stehen auf einem 64-Bit-Computer bis zu 8 TB an virtuellem Arbeitsspeicher zur Verfügung. Kompilieren Sie die Anwendung neu, um sie als native 64-Bit-Anwendung auszuführen. Diese Regel dient nur als Information. Möglicherweise sind keine Korrekturmaßnahmen erforderlich.
