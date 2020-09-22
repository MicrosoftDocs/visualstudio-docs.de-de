---
title: 'Vorgehensweise: Konfigurieren der Rauschunterdrückung in Berichtsansichten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5871473eaba749833714d6382beb487702ebe02d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841265"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Gewusst wie: Konfigurieren der Rauschunterdrückung in Berichtsansichten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Berichte können zur Rauschunterdrückung konfiguriert werden, indem die Anzahl von Daten, die in der Aufrufstrukturansicht und der Zuordnungsansicht angezeigt werden, eingeschränkt werden. Leistungsprobleme werden mithilfe der Rauschunterdrückung erkennbarer. Dies ist hilfreich bei der Analyse von Leistungsberichten.  
  
 Konfigurationsoptionen zur Rauschunterdrückung enthalten die folgenden Einstellungen:  
  
- **Trimmen**: Wenn ein Bericht analysiert wird, wird die Ansicht Funktionen weglassen, die in die Werte- und Schwellenwerteinstellungen fallen, die Sie konfiguriert haben, wie es im folgenden Trimmverfahren erklärt wird. Das Trimmen ist standardmäßig aktiviert.  
  
- **Faltung**: Wenn Sie „Faltung“ aktivieren, werden aufeinander folgende Funktionen auf einen Pfad, der den von Ihnen konfigurierten Einstellungen entspricht, zusammengeführt, wie es im folgenden Faltungsverfahren beschrieben wird. Faltung ist standardmäßig aktiviert.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>So konfigurieren Sie Trimmen für einen Leistungsbericht  
  
1. Wenn im Menü **Entwickler** entweder eine Aufrufstrukturansicht oder eine Zuordnungstrukturansicht im erzeugten Bericht angezeigt wird, klicken Sie auf **Profiler** und anschließend auf **Optionen zur Rauschunterdrückung**.  
  
     Es wird das Dialogfeld **Rauschunterdrückung** angezeigt.  
  
2. Um Trimmen zu aktivieren, gehen Sie folgendermaßen vor:  
  
    1. Wählen Sie **Trimmen aktivieren** aus. Dies ist die Standardeinstellung.  
  
        > [!NOTE]
        > Wenn Rauschunterdrückung aktiviert ist, erscheint im Bericht eine Informationsleiste. Weitere Informationen finden Sie unter [Aufrufstrukturansicht](../profiling/call-tree-view.md) und [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md).  
  
    2. Konfigurieren Sie die Werteinstellung mithilfe der Dropdownliste **Wert** und durch das Auswählen der zutreffenden Einstellung.  
  
    3. Konfigurieren Sie die gewünschte Schwellenwerteinstellung durch Eingabe eines Prozentwertes im Textfeld **Schwellenwert**.  
  
    4. Klicken Sie auf **Warnung anzeigen, wenn Rauschunterdrückung aktiviert ist**, um die Rauschunterdrückungswarnung im erzeugten Bericht zu aktivieren. Dies ist die Standardeinstellung.  
  
3. Deaktivieren Sie **Trimmen aktivieren**, um Trimmen zu deaktivieren.  
  
4. Klicken Sie auf **OK**.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>So konfigurieren Sie Faltung für einen Leistungsbericht.  
  
1. Klicken Sie im Menü **Entwickler** auf **Profiler** und anschließend auf **Optionen zur Rauschunterdrückung**.  
  
     Es wird das Dialogfeld **Rauschunterdrückung** angezeigt.  
  
2. Um Faltung zu aktivieren, gehen Sie folgendermaßen vor:  
  
    1. Wählen Sie **Faltung aktivieren** aus. Dies ist die Standardeinstellung.  
  
        > [!NOTE]
        > Wenn Rauschunterdrückung aktiviert ist, erscheint im Bericht eine Informationsleiste. Weitere Informationen finden Sie unter [Aufrufstrukturansicht](../profiling/call-tree-view.md) und [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md).  
  
    2. Konfigurieren Sie die Werteinstellung mithilfe der Dropdownliste **Wert** und durch das Auswählen der zutreffenden Einstellung.  
  
    3. Konfigurieren Sie die gewünschte Schwellenwerteinstellung durch Eingabe eines Prozentwertes im Textfeld **Schwellenwert**.  
  
    4. Klicken Sie auf **Warnung anzeigen, wenn Rauschunterdrückung aktiviert ist**, um die Rauschunterdrückungswarnung im erzeugten Bericht zu aktivieren. Dies ist die Standardeinstellung.  
  
3. Deaktivieren Sie **Faltung aktivieren**, um Faltung zu deaktivieren.  
  
4. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anpassen von Berichts Ansichten von Leistungs Tools](../profiling/customizing-performance-tools-report-views.md)   
 [Gewusst wie: ausschließen oder Einschließen kurzer Funktionen in die Instrumentierung](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Strukturansicht für Aufrufe](../profiling/call-tree-view.md)   
 [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md)
