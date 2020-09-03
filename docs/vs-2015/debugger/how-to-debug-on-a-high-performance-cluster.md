---
title: 'Vorgehensweise: Debuggen auf einem Hochleistungscluster | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4487b168c3d405b2449bcfb9515e60f0ea67ed1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702688"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Gewusst wie: Debuggen eines Hochleistungsclusters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Debuggen eines Multiprocessing-Programms in einem Hochleistungscluster gleicht dem Debuggen eines gewöhnlichen Programms auf einem Remotecomputer. Es müssen jedoch einige zusätzliche Aspekte berücksichtigt werden. Allgemeine Anforderungen für das Remotesetup finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).  
  
 Beim Debuggen auf einem Hochleistungscluster können alle Debugfenster von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und alle Verfahren für das Remotedebuggen eingesetzt werden. Da Sie jedoch remote debuggen, ist das externe Konsolenfenster nicht verfügbar.  
  
 Das Fenster **Threads** und das Fenster **Prozesse** sind zum Debuggen von parallelen Anwendungen besonders nützlich. Tipps zur Verwendung dieser Fenster finden Sie unter Gewusst [wie: Verwenden des](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) Fensters "Prozesse" und Gewusst [wie: Verwenden des Fensters "Threads](../debugger/how-to-use-the-threads-window.md)".  
  
 In den folgenden Verfahren werden einige Techniken vorgestellt, die beim Debuggen in einem Hochleistungscluster besonders nützlich sind.  
  
 Beim Debuggen einer parallelen Anwendung kann es erforderlich sein, einen Haltepunkt für einen bestimmten Thread, Prozess oder Computer festzulegen. Dies kann durch das Erstellen eines normalen Haltepunkts und das Hinzufügen eines Haltepunktfilters erfolgen.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>So öffnen Sie das Dialogfeld Haltepunktfilter  
  
1. Klicken Sie in einem Quellcodefenster, im Fenster **Disassemblierung**, im Fenster **Aufrufliste** oder im Fenster **Haltepunkte** mit der rechten Maustaste auf ein Haltepunktsymbol.  
  
2. Klicken Sie im Kontextmenü auf **Filter**. Diese Option wird möglicherweise auf oberster Ebene oder im Untermenü unter **Haltepunkte** angezeigt.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>So legen Sie einen Haltepunkt für einen bestimmten Computer fest  
  
1. Entnehmen Sie dem Fenster **Prozesse** den Computernamen.  
  
2. Wählen Sie einen Haltepunkt aus, und öffnen Sie wie in der vorigen Vorgehensweise beschrieben das Dialogfeld **Haltepunktfilter**.  
  
3. Geben Sie im Dialogfeld **Haltepunktfilter** Folgendes ein:  
  
     MachineName =*IhrComputerName*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` (dem Operator UND), `||` (dem Operator ODER) und `!` (dem Operator NICHT) und Klammern kombinieren.  
  
4. Klicken Sie auf **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>So legen Sie einen Haltepunkt für einen bestimmten Prozess fest  
  
1. Entnehmen Sie dem Fenster **Prozesse** den Prozessnamen oder die Prozess-ID.  
  
2. Wählen Sie einen Haltepunkt aus, und öffnen Sie wie in der ersten Vorgehensweise beschrieben das Dialogfeld **Haltepunktfilter**.  
  
3. Geben Sie im Dialogfeld **Haltepunktfilter** Folgendes ein:  
  
     `ProcessName =` *IhrProzessName*  
  
     – oder –  
  
     `ProcessID =` *IhreProzessIDNummer*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` (dem Operator UND), `||` (dem Operator ODER) und `!` (dem Operator NICHT) und Klammern kombinieren.  
  
4. Klicken Sie auf **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>So legen Sie einen Haltepunkt für einen bestimmten Thread fest  
  
1. Entnehmen Sie dem Fenster **Threads** den Threadnamen oder die Thread-ID.  
  
2. Wählen Sie einen Haltepunkt aus, und öffnen Sie wie in der ersten Vorgehensweise beschrieben das Dialogfeld **Haltepunktfilter**.  
  
3. Geben Sie im Dialogfeld **Haltepunktfilter** Folgendes ein:  
  
     `ThreadName =` *IhrThreadName*  
  
     – oder –  
  
     `ThreadID =` *IhreThreadIDNummer*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` (dem Operator UND), `||` (dem Operator ODER) und `!` (dem Operator NICHT) und Klammern kombinieren.  
  
4. Klicken Sie auf **OK**.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Erstellen eines Filters für einen Haltepunkt für einen Computer mit dem Namen `marvin` und einen Thread mit dem Namen `fourier1` beschrieben.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Remote Debuggen](../debugger/remote-debugging.md)   
 [Gewusst wie: Verwenden des Fensters "Prozesse"](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Gewusst wie: Verwenden des Fensters "Threads"](../debugger/how-to-use-the-threads-window.md)   
 [Threads und Prozesse](https://msdn.microsoft.com/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
