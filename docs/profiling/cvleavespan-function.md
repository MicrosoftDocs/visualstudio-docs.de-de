---
title: CvLeaveSpan-Funktion | Microsoft-Dokumentation
description: Dieser Artikel enthält Referenzinformationen für die Funktion CvLeaveSpan des Concurrency Visualizer-SDK (C-Bibliothek).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1dcd98a8233f8080d03650c3989805ee9ec7289
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686583"
---
# <a name="cvleavespan-function"></a>CvLeaveSpan-Funktion
Markiert das Ende der Spanne.

## <a name="syntax"></a>Syntax

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>Parameter
 `pSpan`: durch vorherigen Aufruf von CvEnterSpan* zurückgegebenes span-Objekt. Lässt keine NULL-Werte zu.

## <a name="return-value"></a>Rückgabewert
 S_OK, wenn die Meldung erfolgreich geschrieben wurde. Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkers.h*

## <a name="see-also"></a>Siehe auch
- [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)