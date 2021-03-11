---
description: Bestimmt, ob eine Sitzung den Anbieter aktiviert hat
title: marker_series::is_enabled-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ce01d71b3fac63062a3f823f1862fd199fa39be
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223575"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series:: is_enabled-Methode
Bestimmt, ob eine Sitzung den Anbieter aktiviert hat

## <a name="syntax"></a>Syntax

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>Parameter
 `_Importance`: die Wichtigkeitsstufe.

 `_Category`: die Kategorie.

## <a name="return-value"></a>Rückgabewert

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Siehe auch
- [marker_series-Klasse](../profiling/marker-series-class.md)
