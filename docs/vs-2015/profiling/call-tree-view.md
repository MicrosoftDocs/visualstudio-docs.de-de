---
title: Aufrufstrukturansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 105f16c0d9deb8d94a102818c5335af18685c675
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840832"
---
# <a name="call-tree-view"></a>Aufrufstrukturansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Aufrufstrukturansicht werden die Funktionsausführungspfade angezeigt, die in der mit einem Profil versehenen Anwendung durchlaufen wurden. Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente. Unter den einzelnen Funktionsknoten werden alle Funktionen aufgeführt, die von ihnen aufgerufen wurden. Zudem werden Leistungsdaten über diese Funktionsaufrufe angezeigt.  
  
 Die Aufrufstrukturansicht kann erweitert werden und den Ausführungspfad einer Funktion hervorheben, für die die meisten Samplings durchgeführt oder die meiste Zeit verwendet wurde. Um den leistungsintensivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  
  
 Jeder Prozess in der Profilerstellung wird als Stammknoten angezeigt. Sie können den Startknoten der Aufrufstrukturansicht festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.  
  
 Durch das Festlegen eines Stammknotens wird sichergestellt, dass in der Ansicht lediglich die Teilstruktur des ausgewählten Knotens angezeigt wird. Sie können den Stammknoten wieder auf den angezeigten Knoten festlegen. Klicken Sie dazu mit der rechten Maustaste in das Fenster der Aufrufstrukturansicht, und wählen Sie **Stamm zurücksetzen** aus.  
  
 Sie können die Aufrufstrukturansicht an Ihre Bedürfnisse anpassen, indem Sie Spalten hinzufügen oder entfernen. Klicken Sie mit der rechten Maustaste auf die **Titelleiste des Spaltennamens**, und klicken Sie anschließen auf **Spalten hinzufügen/entfernen**.  
  
 Für die Aufrufstrukturansicht kann die Rauschunterdrückung konfiguriert werden, indem Sie festlegen, das weniger Daten angezeigt werden. Leistungsprobleme werden mithilfe der Rauschunterdrückung in der Ansicht erkennbarer. Leichter zu identifizierende Leistungsprobleme können auch leichter analysiert werden. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren der Rauschunterdrückung in Berichtsansichten](../profiling/how-to-configure-noise-reduction-in-report-views.md).  
  
> [!NOTE]
> Wenn die Rauschunterdrückung so konfiguriert ist, dass sie eine Warnung anzeigt, wenn Sie aktiviert ist, wird eine Informationsleiste im Bericht angezeigt.  
  
 Weitere Informationen zu Definitionen von Spalten in der Aufrufstrukturansicht finden Sie in den folgenden Artikeln:  
  
 [Aufrufstrukturansicht](../profiling/call-tree-view-sampling-data.md)  
  
 [Aufrufstrukturansicht](../profiling/call-tree-view-instrumentation-data.md)  
  
 [Aufrufstrukturansicht - Sampling](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [Aufrufstrukturansicht](../profiling/call-tree-view-contention-data.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Leistungs Berichts Ansichten](../profiling/performance-report-views.md)   
 [Grundlegendes zu Instrumentations Datenwerten](../profiling/understanding-instrumentation-data-values.md)   
 [Grundlegendes zu Stichprobendaten Werten](../profiling/understanding-sampling-data-values.md)
