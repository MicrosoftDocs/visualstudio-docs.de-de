---
title: Leistungsregeln für Speicher und Auslagerung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bf868164a8768b01793e6c5ec69b90c89cab34bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547965"
---
# <a name="memory-and-paging-performance-rules"></a>Leistungsregeln für Speicher und Auslagerung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Leistungsregeln in der Speicher- und Auslagerungskategorie identifiziert die Auslagerungsaktivität in einer Profilerstellung, die Anwendungsleistung und -reaktionsfähigkeit beeinträchtigen kann.  
  
|Regel|Beschreibung|  
|-|-|  
|[DA0014: Äußerst hohes Maß an Paging von aktivem Speicher auf den Datenträger](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Im Verlauf der Profilerstellung ist ein hohes Maß an Auslagerung von aktivem Speicher auf und vom Datenträger aufgetreten. Solch hohe Auslagerungsraten wirken sich in der Regel negativ auf Leistung und Reaktionszeit der Anwendung aus. Verringern Sie ggf. die Speicherbelegungen, indem Sie die Algorithmen überarbeiten. Sie müssen möglicherweise auch die Speicheranforderungen der Anwendung berücksichtigen. Versuchen Sie, die Profilerstellung erneut auf einem Computer auszuführen, der über mehr Arbeitsspeicher verfügt. Diese Regel wird ausgelöst, wenn die Auslagerungsaktivität den oberen Schwellenwert der Regel DA0017 überschreitet.|  
|[DA0017: Hohes Maß an Paging von aktivem Speicher auf den Datenträger](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Im Verlauf der Profilerstellung ist ein relativ hohes Maß an Auslagerung von aktivem Speicher auf den und von dem Datenträger aufgetreten. Solch hohe Auslagerungsraten wirken sich in der Regel negativ auf Leistung und Reaktionszeit der Anwendung aus. Verringern Sie ggf. die Speicherbelegungen, indem Sie die Algorithmen überarbeiten. Sie müssen möglicherweise auch die Speicheranforderungen der Anwendung berücksichtigen. Versuchen Sie, die Profilerstellung erneut auf einem Computer auszuführen, der über mehr Arbeitsspeicher verfügt.|
