---
description: Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c2e7560c91882afe1ee2608bb2ae2fc105738dc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223939"
---
# <a name="marker_importance-enumeration"></a>marker_importance-Enumeration
Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.

## <a name="syntax"></a>Syntax

```cpp
enum marker_importance;
```

## <a name="members"></a>Member

### <a name="values"></a>Werte

|Name|Beschreibung|
|----------|-----------------|
|`critical_importance`|Gibt an, dass der Marker kritisch wichtig ist|
|`high_importance`|Gibt an, dass der Marker hoch wichtig ist|
|`low_importance`|Gibt an, dass der Marker weniger wichtig ist|
|`normal_importance`|Gibt an, dass der Marker normal wichtig ist|

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Siehe auch
- [diagnostic-Namespace](../profiling/diagnostic-namespace.md)
