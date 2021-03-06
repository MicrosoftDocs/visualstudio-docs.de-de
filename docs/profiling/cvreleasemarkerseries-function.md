---
title: CvReleaseMarkerSeries-Funktion | Microsoft-Dokumentation
description: Dieser Artikel enthält Referenzinformationen für die Funktion CvReleaseMarkerSeries des Concurrency Visualizer-SDK (C-Bibliothek).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 60a216c99e21d76efd4d348fea0d06d4f016db5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948243"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries-Funktion
Gibt Markerreihen frei. Verwenden Sie keine freigegebenen Markerreihenobjekte, da die Anwendung andernfalls möglicherweise abstürzt. Wenn Markerreihen nicht freigegeben werden, führt dies zu einem Arbeitsspeicherverlust.

## <a name="syntax"></a>Syntax

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>Parameter
 `pMarkerSeries`: die Adresse der Anbieterobjektvariable. Die Adresse darf nicht NULL sein. Die Variable kann einen beliebigen Wert aufweisen.

## <a name="return-value"></a>Rückgabewert
 S_OK, wenn Markerreihen erfolgreich freigegeben wurden, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkers.h*

## <a name="see-also"></a>Siehe auch
- [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)