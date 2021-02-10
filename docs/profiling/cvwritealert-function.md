---
title: CvWriteAlert-Funktion | Microsoft-Dokumentation
description: Dieser Artikel enthält Referenzinformationen für die Funktion CvWriteAlert des Concurrency Visualizer-SDK (C-Bibliothek).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteAlertVA
- cvmarkers/CvWriteAlertVW
- cvmarkers/CvWriteAlertA
- cvmarkers/CvWriteAlertW
helpviewer_keywords:
- CvWriteAlertVW method
- CvWriteAlertA method
- CvWriteAlertVA method
- CvWriteAlertW method
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 015a25e57e042c86bee28c42489ce3d4f63e8553
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948178"
---
# <a name="cvwritealert-function"></a>CvWriteAlert-Funktion
Schreibt eine Warnung in die Ablaufverfolgungsdatei der Nebenläufigkeitsschnellansicht

## <a name="syntax"></a>Syntax

```C
HRESULT CvWriteAlertW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteAlertA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteAlertVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteAlertVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    _In_ va_list argList);
```

#### <a name="parameters"></a>Parameter
 `argList`: eine Liste von Argumenten.

 `pMarkerSeries`: gültiger Markerreihenkontext. Lässt keine NULL-Werte zu.

 `pMessage`: die Formatzeichenfolge für die Meldung. Lässt keine NULL-Werte zu.

## <a name="return-value"></a>Rückgabewert
 S_OK, wenn die Meldung erfolgreich geschrieben wurde. Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkers.h*

 **Unicode:** CvWriteAlertW, CvWriteAlertVW

 **ANSI:** CvWriteAlertA, CvWriteAlertVA

## <a name="see-also"></a>Siehe auch
- [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)