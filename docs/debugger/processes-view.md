---
title: Prozessansicht | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ba60021410f1965e05f7c5479231013d53cb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62904227"
---
# <a name="processes-view"></a>Prozessansicht
In der Prozessansicht wird eine Struktur aller aktiven Prozesse Ihres Systems angezeigt. Die Prozess-ID und der Modulname werden angezeigt. Verwenden Sie die Prozessansicht, wenn Sie einen bestimmten Systemprozess untersuchen möchten, der in der Regel einem laufenden Programm entspricht. Prozesse werden durch Modulnamen identifiziert oder werden als „Systemprozesse“ bezeichnet.

 Microsoft Windows unterstützt mehrere Prozesse. Jeder Prozess kann über einen oder mehrere Threads verfügen, wobei jeder Thread über mindestens ein zugeordnetes Fenster auf oberster Ebene verfügen kann. Jedes Fenster der obersten Ebene kann eine Reihe von Fenstern besitzen. Das Plussymbol (+) gibt an, dass eine Ebene reduziert wird. Die reduzierte Ansicht besteht aus einer Zeile pro Prozess. Klicken Sie auf das „+“-Symbol, um die Ebene zu erweitern.

 Verwenden Sie die Prozessansicht, wenn Sie einen bestimmten Systemprozess untersuchen möchten, der in der Regel einem laufenden Programm entspricht. Prozesse werden durch Modulnamen identifiziert oder werden als „Systemprozesse“ bezeichnet. Wenn Sie nach einem Prozess suchen möchten, klappen Sie die Struktur zu, und durchsuchen Sie die Liste.

## <a name="procedures"></a>Verfahren

#### <a name="to-open-the-processes-view"></a>Öffnen der Prozessansicht

1. Wählen Sie im Menü **Spy** die Option **Prozesse** aus.

   ![Spy&#43;&#43;-Prozessansicht](../debugger/media/spy--_processes.png "Spy++_Processes") Spy++-Prozessansicht

   Die obige Abbildung zeigt die Prozessansicht mit den erweiterten Prozess- und Threadknoten.

### <a name="in-this-section"></a>In diesem Abschnitt
 [Suchen eines Prozesses in der Prozessansicht](../debugger/how-to-search-for-a-process-in-processes-view.md) erläutert, wie Sie in der Prozessansicht nach einem bestimmten Prozess suchen.

 [Anzeigen von Prozesseigenschaften](../debugger/how-to-display-process-properties.md) erläutert, wie Sie weitere Informationen zu einer Meldung anzeigen.

### <a name="related-sections"></a>Verwandte Abschnitte
 [Spy++-Ansichten](../debugger/spy-increment-views.md) erläutert die Spy++-Strukturansichten von Fenstern, Meldungen, Prozessen und Threads.

 [Verwenden von Spy++](../debugger/using-spy-increment.md) bietet eine Einführung in das Tool Spy++ und dessen Verwendung.

 [Dialogfeld „Prozesssuche“](../debugger/process-search-dialog-box.md) wird verwendet, um den Knoten für einen bestimmten Prozess in der Prozessansicht zu suchen.

 [Dialogfeld „Prozesseigenschaften“](../debugger/process-properties-dialog-box.md) zeigt die Eigenschaften eines Prozesses an, der in der Prozessansicht ausgewählt wurde.

 [Spy++-Referenz](../debugger/spy-increment-reference.md) enthält Abschnitte mit Beschreibungen der einzelnen Menüs und Dialogfelder von Spy++.