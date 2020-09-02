---
title: Zusammenfassungsansicht – Ansicht für Ressourcenkonflikte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65f659b64b6a1e29e1e25ae344dd8033e631de09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157767"
---
# <a name="summary-view---resource-contention-view"></a>Zusammenfassungsansicht – Ansicht für Ressourcenkonflikte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Zusammenfassung zeigt Informationen zu den Ereignissen in der Anwendung an, in der ein Thread oder Prozess angehalten wurde, während er auf den Zugriff auf eine Ressource gewartet hat.  
  
 Weitere Informationen, einschließlich einer Beschreibung der Benachrichtigungslinks und Berichtslisten, finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Zeitachsendiagramm  
 Die Zeitachsendiagramm in der Zusammenfassungsansicht zeigt die Auslastung des Prozessors (CPU) durch die profilierte Anwendung während des Zeitraums an, in dem die Profilerstellung stattgefunden sind. Sie können das Zeitachsendiagramm zum Filtern der Ansicht in einem ausgewählten Zeitraum verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Filtern von Berichtsansichten aus der Zeitachsenübersicht](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="most-contended-resources"></a>Ressourcen mit den meisten Konflikten  
 **Ressourcen mit den meisten Konflikten** listet die Ressourcen in der Anwendung auf, die die meisten Konfliktereignisse verursacht haben. Sie können auf einen Ressourcennamen klicken, um die Ansicht „Konflikte“ anzuzeigen. Die Ansicht „Konflikte“ bietet eine detaillierte Zeitachse der Ressourcenkonflikte nach Thread.  
  
 **Ressourcen mit den meisten Konflikten** umfasst die folgenden Daten für jede Ressource.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Name**|Der Name der Ressource.|  
|**Konflikte %**|Der Prozentsatz aller Konfliktereignisse in den Profilerstellungsdaten, die Konflikte für die Ressource waren.|  
  
## <a name="most-contended-thread"></a>Threads mit den meisten Konflikten  
 **Threads mit den meisten Konflikten** listet die Threads in der Anwendung, die die größte Anzahl von Konfliktereignissen aufgewiesen hat. Sie können auf einen Threadnamen klicken, um die Ansicht „Konflikte“ anzuzeigen, die eine detaillierte Zeitachse der Ressourcenkonflikte nach Thread bereitstellt.  
  
 **Ressourcen mit den meisten Konflikten** umfasst die folgenden Daten für jeden Thread.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**ID**|Der Threadbezeichner.|  
|**Name**|Der Name des Prozesses, der den Thread besitzt.|  
|**Konflikte %**|Der Prozentsatz aller Konfliktereignisse in den Profilerstellungsdaten, die Konflikte für die Ressource waren.|
