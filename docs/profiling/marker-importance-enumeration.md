---
title: marker_importance Enumeration | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d67a1806034d55147379626b6eb4f868532e4d77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330742"
---
# <a name="marker_importance-enumeration"></a>marker_importance-Enumeration
Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.

## <a name="syntax"></a>Syntax

```cpp
enum marker_importance;
```

## <a name="members"></a>Member

### <a name="values"></a>Werte

|name|Beschreibung|
|----------|-----------------|
|`critical_importance`|Gibt an, dass der Marker kritisch wichtig ist|
|`high_importance`|Gibt an, dass der Marker hoch wichtig ist|
|`low_importance`|Gibt an, dass der Marker weniger wichtig ist|
|`normal_importance`|Gibt an, dass der Marker normal wichtig ist|

## <a name="requirements"></a>Anforderungen
 **Header:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Siehe auch
- [diagnostic-Namespace](../profiling/diagnostic-namespace.md)