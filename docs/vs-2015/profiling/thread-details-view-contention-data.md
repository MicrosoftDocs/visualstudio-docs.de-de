---
title: Ansicht „Threaddetails – Konfliktdaten < Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16ee86e69cb3a150a98de5077aa0c545545833e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145593"
---
# <a name="thread-details-view---contention-data"></a>Ansicht „Threaddetails“ – Konfliktdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Ansicht "Threaddetails" enthält ein Zeitachsendiagramm der blockierenden Ereignisse im ausgewählten Thread einer Profilerstellung, die von Ressourcenkonflikten ausgelöst wurden. Ein blockierendes Ereignis tritt auf, wenn der Thread gezwungen wird, die Ausführung anzuhalten, da ein anderer Thread den Zugriff auf eine Ressource gesperrt hat.  
  
 Diese Ansicht stellt die Ausführungszeitachse des Threads als horizontalen Balken und die blockierenden Ereignisse als senkrechten Balken auf einer horizontalen Zeitachse für den Thread dar. Bei Bedarf können Sie die Ansicht eines Zeitachsenbereichs vergrößern, um die einzelnen Ereignisse anzuzeigen. Um den Ausführungspfad der Funktionen anzuzeigen, die zum Ereignis geführt haben, klicken Sie auf die Ereignisleiste. Die Funktionen werden im Fenster "Aufrufliste" angezeigt. Wenn der Quellcode für eine Funktion verfügbar ist, können Sie auf den Funktionsnamen klicken, um die Quelldatei in der Visual Studio IDE zu bearbeiten.  
  
## <a name="navigating-the-timeline"></a>Navigieren in der Zeitachse  
  
#### <a name="to-zoom-in-on-a-timeline-segment"></a>So vergrößern Sie die Ansicht eines Zeitachsensegments  
  
- Wählen Sie mit gedrückter Maustaste einen Bereich auf der Zeitachse aus.  
  
     Wenn Sie die Maustaste loslassen, wird die Ansicht des ausgewählten Zeitsegments vergrößert. Sie können den Vorgang wiederholen, um größeres Detail zu vergrößern. Das Bildlauffeld auf der Zeitbildlaufleiste stellt die relative Größe des Zeitsegments dar, das in der Ansicht angezeigt wird.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>So verkleinern Sie die Ansicht einer Zeitachse  
  
- Klicken Sie auf **Verkleinern**, um zur vorherigen Zoomstufe zurückzukehren.  
  
- Klicken Sie auf **Zurücksetzen des Zooms**, um die ganze Zeitachse in der Ansicht anzuzeigen.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>So zeigen Sie die Aufrufliste eines Ereignisses an  
  
- Klicken Sie im Zeitachsendiagramm auf den senkrechten Balken, der das Ereignis darstellt.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>So zeigen Sie den Quellcode für eine Funktion in der Aufrufliste an oder bearbeiten diesen  
  
- Klicken Sie im Fenster "Aufrufliste" auf den Funktionsnamen.  
  
  Der Funktionsquellcode muss Teil des aktuellen Projekts sein.  
  
#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>So zeigen Sie die Konfliktereignisse einer Ressource in allen Threads bei der Profilerstellung an  
  
- Klicken Sie im Zeitachsendiagramm auf den Namen oder die ID der Ressource.  
  
     Die Ansicht [Ressourcendetails](../profiling/resource-details-view-contention-data.md) wird für die ausgewählte Resource angezeigt.  
  
#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>So zeigen Sie die Threadkonfliktdaten im Fenster "Prozesse" an  
  
- Klicken Sie im Zeitachsendiagramm auf **Gesamt**.  
  
     Die [Prozessansicht](../profiling/process-view-contention-data.md) wird mit ausgewähltem Thread angezeigt.
