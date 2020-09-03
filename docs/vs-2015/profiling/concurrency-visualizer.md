---
title: Nebenläufigkeitsschnellansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7061acabbe5ce18ff6e1f210fe0003bdaf88980
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586812"
---
# <a name="concurrency-visualizer"></a>Concurrency Visualizer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Concurrency Visualizer ist eine optionale Erweiterung für Visual Studio. Laden Sie Concurrency Visualizer und die Concurrency Visualizer Collection Tools unter folgenden Links herunter:  
> 
> - Laden Sie die Erweiterung              [Concurrency Visualizer](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) herunter.  
>   - Laden Sie die Tools für die Parallelitäts Schnellansicht              [für Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103)herunter.  
> 
>   Mit dem [Befehlszeilenprogramm für die Nebenläufigkeitsschnellansicht (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) können Sie die Ablaufverfolgung aus der Befehlszeile sammeln und diese in Concurrency Visualizer für Visual Studio 2015 anzeigen. Das Tool kann auf Computern verwendet werden, auf denen Visual Studio nicht installiert ist.  
  
 Mit der Nebenläufigkeitsschnellansicht können Sie die Leistung einer Multithread-App überprüfen. Die Ansichten der Parallelitätsschnellansicht stellen Daten zu den temporären Beziehungen zwischen den Threads im Programm und dem System als Ganzem in grafischer, tabellarischer und textlicher Form bereit. Sie können die Parallelitätsschnellansicht verwenden, um Leistungsengpässe, CPU-Unterauslastungen, Threadkonflikte, kernübergreifende Threadmigration, Synchronisierungsverzögerungen, DirectX-Aktivitäten, Bereiche überlappender E/A und andere Informationen zu suchen. Die Ansichten stellen aktionsfähige Daten bereit, indem die grafische Ausgabe nach Möglichkeit mit Aufruflisten und Quellcode verknüpft wird.  
  
 Die Nebenläufigkeitsschnellansicht beruht auf den Funktionen der [Ereignisablaufverfolgung für Windows](https://msdn.microsoft.com/library/bb968803(VS.85).aspx) .  
  
> [!NOTE]
> Die Nebenläufigkeitsschnellansicht unterstützt keine Webprojekte.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|BESCHREIBUNG|  
|-----------|-----------------|  
|[Auslastungsansicht](../profiling/utilization-view.md)|Beschreibt, wie Systemaktivitäten über alle Prozessoren hinweg angezeigt und analysiert werden.|  
|[Thread Ansicht](../profiling/threads-view-parallel-performance.md)|Beschreibt, wie die Interaktionen zwischen Threads in Ihrem Programm analysiert werden.|  
|[Kernansicht](../profiling/cores-view.md)|Beschreibt, wie die Threadmigration über Kerne hinweg analysiert wird.|  
|[Allgemeine Muster für nicht verhaltene Multithreadanwendungen](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Beschreibt einige allgemeine Muster und zeigt, wie diese in der Nebenläufigkeitsschnellansicht angezeigt werden.|  
|[Parallele Entwicklung in Visual Studio (Blog)](https://docs.microsoft.com/archive/blogs/visualizeparallel/)|Bietet Tipps und empfohlene Vorgehensweisen für die Nebenläufigkeitsschnellansicht.|  
|[Leistungs Berichts Ansichten](../profiling/performance-report-views.md)|Enthält Referenzinformationen zu den Berichten und Ansichten der Visual Studio-Profilerstellungstools.|  
|[SDK der Nebenläufigkeitsschnellansicht](../profiling/concurrency-visualizer-sdk.md)|Beschreibt, wie Sie Ihren Quellcode instrumentieren, um zusätzliche Informationen in der Nebenläufigkeitsschnellansicht anzuzeigen.|  
|[Befehlszeilenhilfsprogramm für die Parallelitätsschnellansicht (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Beschreibt, wie das Befehlszeilenprogramm der Nebenläufigkeitsschnellansicht (CVCollectionCmd.exe) verwendet wird, um Ablaufverfolgungen auf Computern zu erfassen und zu verarbeiten, auf denen kein Visual Studio installiert ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Profilerstellungstools](../profiling/profiling-tools.md)
