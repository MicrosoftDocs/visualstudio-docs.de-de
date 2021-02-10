---
title: diagnostic-Namespace | Microsoft-Dokumentation
description: Verwenden Sie den Diagnosenamespace, um Concurrency Visualizer-Marker auszugeben. Der Diagnosenamespace ist Teil des Concurrency-Namespace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22224e375c1d1f463f1c07d41ca5a03efa5cabdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923736"
---
# <a name="diagnostic-namespace"></a>Diagnostic-Namespace
Der `diagnostics`-Namespace stellt Funktionen zum Ausgeben von Markern für Nebenläufigkeitsschnellansichten bereit.

## <a name="syntax"></a>Syntax

```cpp
namespace diagnostic;
```

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|name|Beschreibung|
|----------|-----------------|
|[marker_series-Klasse](../profiling/marker-series-class.md)|Stellt einen seriellen Kanal mit Ereignissen dar, die von einem einzelnen Anbieter generiert werden.|
|[span-Klasse](../profiling/span-class.md)|Definiert eine Phase der Anwendung.|

### <a name="enumerations"></a>Enumerationen

|Name|Beschreibung|
|----------|-----------------|
|[marker_importance-Enumeration](../profiling/marker-importance-enumeration.md)|Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.|

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkersobj.h*

 **Namespace:** Parallelität

## <a name="see-also"></a>Siehe auch
- [Concurrency-Namespace (Parallelitätsschnellansicht)](../profiling/concurrency-namespace-concurrency-visualizer.md)