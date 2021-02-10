---
title: CvReleaseProvider-Funktion | Microsoft-Dokumentation
description: Dieser Artikel enthält Referenzinformationen für die Funktion CvReleaseProvider des Concurrency Visualizer-SDK (C-Bibliothek).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae363f1909f169d2d5dc4004a79cfe3c2919bdf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948230"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider-Funktion
Gibt Markeranbieter frei. Die Freigabe des Markeranbieters hat keine Auswirkungen auf bereits erstellte Markerreihen dieses Anbieters. Markerreihen müssen durch den Aufruf von CvReleaseMarkerSeries getrennt freigegeben werden. Wenn Markeranbieter nicht freigegeben werden, führt dies zu einem Arbeitsspeicherverlust.

## <a name="syntax"></a>Syntax

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parameter
 `pProvider`: der Anbieterkontext. Lässt keine NULL-Werte zu.

## <a name="return-value"></a>Rückgabewert
 S_OK, wenn der Anbieter erfolgreich freigegeben wurde, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkers.h*

## <a name="see-also"></a>Siehe auch
- [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)