---
title: Debuggen auf einem Hochleistungscluster | Microsoft-Dokumentation
description: Hier erfahren Sie, welche Aspekte beim Debuggen eines Multiprocessing-Programms in einem Hochleistungscluster von besonderer Bedeutung sind. Zwei Fenster sind besonders nützlich. Außerdem gibt es spezielle Techniken.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b19f1d919095f30e4408056e49847c3c9ba5671
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903107"
---
# <a name="how-to-debug-on-a-high-performance-cluster-c-visual-basic-c"></a>Vorgehensweise: Debuggen auf einem Hochleistungscluster (C#, Visual Basic, C++)

Das Debuggen eines Multiprocessing-Programms in einem Hochleistungscluster gleicht dem Debuggen eines gewöhnlichen Programms auf einem Remotecomputer. Es müssen jedoch einige zusätzliche Aspekte berücksichtigt werden. Allgemeine Anforderungen für das Remotesetup finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

 Beim Debuggen auf einem Hochleistungscluster können alle Debugfenster von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und alle Verfahren für das Remotedebuggen eingesetzt werden. Da Sie jedoch remote debuggen, ist das externe Konsolenfenster nicht verfügbar.

 Das Fenster **Threads** und das Fenster **Prozesse** sind zum Debuggen von parallelen Anwendungen besonders nützlich. Tipps zur Verwendung dieser Fenster finden Sie unter [Vorgehensweise: Verwenden des Prozessfensters](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) und [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters „Threads“](../debugger/how-to-use-the-threads-window.md).

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

`(MachineName = marvin) & (ThreadName = fourier1)`

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Remote Debugging](../debugger/remote-debugging.md)
- [How to: Verwenden des Fensters „Prozesse“](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))
- [Debuggen von Multithread-Apps](../debugger/get-started-debugging-multithreaded-apps.md)
- [Threads und Prozesse](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))
- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)