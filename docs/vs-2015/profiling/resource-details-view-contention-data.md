---
title: Ressourcendetailansicht – Konfliktdaten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 922edcd45dd42c8da5a9ec4dc8d3e8f450ceea09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823600"
---
# <a name="resource-details-view---contention-data"></a>Ressourcendetailansicht – Konfliktdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Ansicht Ressourcendetails enthält ein Zeitachsendiagramm der blockierenden Ereignisse, die von Konflikten ausgewählter Ressourcen ausgelöst wurden. Ein blockierendes Ereignis tritt auf, wenn der Thread gezwungen wird, die Ausführung anzuhalten, da ein anderer Thread den Zugriff auf die Ressource gesperrt hat.  
  
 Diese Ansicht stellt die Ausführungszeitachse jedes Threads als horizontalen Balken und die blockierenden Ereignisse als senkrechten Balken für den Thread dar. Bei Bedarf können Sie einen Teil eines Zeitachsenbereichs vergrößern, um die einzelnen Ereignisse anzuzeigen. Um den Ausführungspfad (Aufrufliste) der Funktionen anzuzeigen, die zum Ereignis geführt haben, klicken Sie auf die Ereignisleiste. Die Funktionen werden im Fenster **Aufrufliste** angezeigt. Wenn der Quellcode für eine Funktion verfügbar ist, können Sie auf den Funktionsnamen klicken, um die Quelldatei in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Oberfläche zu bearbeiten.  
  
## <a name="procedures"></a>Verfahren  
  
#### <a name="to-magnify-a-timeline-segment"></a>So vergrößern Sie ein Zeitachsensegment  
  
- Wählen Sie mit gedrückter Maustaste einen Bereich auf der Zeitachse aus.  
  
     Wenn Sie die Maustaste loslassen, wird die Ansicht des ausgewählten Zeitsegments vergrößert. Sie können den Prozess wiederholen, um das Segment weiter zu vergrößern. Das Bildlauffeld auf der Zeitbildlaufleiste stellt die relative Größe des Zeitsegments dar, das in der Ansicht angezeigt wird.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>So verkleinern Sie die Ansicht einer Zeitachse  
  
- Führen Sie einen der folgenden Schritte aus:  
  
  - Klicken Sie auf **Verkleinern**, um zur vorherigen Zoomstufe zurückzukehren.  

  - Klicken Sie auf **Zurücksetzen des Zooms**, um die ganze Zeitachse in der Ansicht anzuzeigen.  

#### <a name="to-view-the-call-stack-of-an-event"></a>So zeigen Sie die Aufrufliste eines Ereignisses an  
  
- Klicken Sie im Zeitachsendiagramm auf die Ereignisleiste.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>So zeigen Sie den Quellcode für eine Funktion in der Aufrufliste an oder bearbeiten diesen  
  
- Klicken Sie im Fenster **Aufrufliste** auf den Funktionsnamen.  
  
  Der Funktionsquellcode muss Teil des aktuellen Projekts sein.  
  
#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>So zeigen Sie die Aufrufstruktur von Konfliktereignissen für die Ressource an  
  
- Klicken Sie im Zeitachsendiagramm auf **Gesamt**.  
  
     Die Konflikte für die Ressource werden angezeigt. Weitere Informationen finden Sie unter [Ressourcenkonfliktansicht](../profiling/resource-contentions-view-contention-data.md).  
  
#### <a name="to-view-all-the-contention-events-of-a-thread"></a>So zeigen Sie alle Konfliktereignisse eines Threads an  
  
- Klicken Sie im Zeitachsendiagramm auf den Namen oder die ID des Threads.  
  
     Die Detailansicht des Threads wird für den ausgewählten Thread angezeigt. Weitere Informationen finden Sie unter [Threaddetailansicht](../profiling/thread-details-view-contention-data.md).
