---
title: diagnostic-Namespace | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d412cfa5a9b5e7e90aeac3ac6bbb530b0ef48ad0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157578"
---
# <a name="diagnostic-namespace"></a>diagnostic-Namespace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der `diagnostics`-Namespace stellt Funktionen zum Ausgeben von Markern für Nebenläufigkeitsschnellansichten bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>Member  
  
### <a name="classes"></a>Klassen  
  
|name|Beschreibung|  
|----------|-----------------|  
|[marker_series-Klasse](../profiling/marker-series-class.md)|Stellt einen seriellen Kanal mit Ereignissen dar, die von einem einzelnen Anbieter generiert werden.|  
|[span-Klasse](../profiling/span-class.md)|Definiert eine Phase der Anwendung.|  
  
### <a name="enumerations"></a>Enumerationen  
  
|name|Beschreibung|  
|----------|-----------------|  
|[marker_importance-Enumeration](../profiling/marker-importance-enumeration.md)|Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkersobj.h  
  
 **Namespace:** Parallelität  
  
## <a name="see-also"></a>Weitere Informationen  
 [Concurrency-Namespace (Parallelitätsschnellansicht)](../profiling/concurrency-namespace-concurrency-visualizer.md)
