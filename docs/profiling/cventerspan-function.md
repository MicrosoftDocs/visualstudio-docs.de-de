---
title: CvEnterSpan-Funktion | Microsoft-Dokumentation
description: Dieser Artikel enthält Referenzinformationen für die Funktion CvEnterSpan des Concurrency Visualizer-SDK (C-Bibliothek).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvEnterSpanVA
- cvmarkers/CvEnterSpanW
- cvmarkers/CvEnterSpanExW
- cvmarkers/CvEnterSpanA
- cvmarkers/CvEnterSpanExVW
- cvmarkers/CvEnterSpanExA
- cvmarkers/CvEnterSpanVW
helpviewer_keywords:
- CvEnterSpanVW method
- CvEnterSpanVA method
- CvEnterSpanExA method
- CvEnterSpanW method
- CvEnterSpanA method
- CvEnterSpanExVW method
- CvEnterSpanExW method
ms.assetid: 91689e9c-6733-44b9-b36a-8b9b2eef7d1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50a68d58d6a9b2564c732605075811e8bc99721f
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686518"
---
# <a name="cventerspan-function"></a>CvEnterSpan-Funktion
Kennzeichnet den Anfang einer neuen Spanne.

## <a name="syntax"></a>Syntax

```C
HRESULT CvEnterSpanW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvEnterSpanA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvEnterSpanVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    _In_ va_list argList
    );

HRESULT CvEnterSpanVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    _In_ va_list argList
    );

HRESULT CvEnterSpanExW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvEnterSpanExA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvEnterSpanExVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvEnterSpanExVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ CV_IMPORTANCE level,
    _In_ int category,
    _Out_ PCV_SPAN* ppSpan,
    _In_ PCSTR pMessage,
    _In_ va_list argList);

```

#### <a name="parameters"></a>Parameter
 `argList`: eine Liste von Argumenten.

 `category`: die Kategorie der Spanne.

 `level`: die Wichtigkeitsstufe der Spanne.

 `pMarkerSeries`: gültiger Markerreihenkontext. Lässt keine NULL-Werte zu.

 `pMessage`: die Nachrichtenformatzeichenfolge. Lässt keine NULL-Werte zu.

 `ppSpan`: die Adresse der Variablen, in der das resultierende span-Objekt gespeichert wird. Die Adresse darf nicht NULL sein. Die Variable kann einen beliebigen Wert aufweisen.

## <a name="return-value"></a>Rückgabewert
 S_OK, wenn die Meldung erfolgreich geschrieben wurde. Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkers.h*

 **Unicode:** CvEnterSpanW, CvEnterSpanVW, CvEnterSpanExW, CvEnterSpanExVW

 **ANSI:** CvEnterSpanA, CvEnterSpanVA, CvEnterSpanExA, CvEnterSpanExVW

## <a name="see-also"></a>Siehe auch
- [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)