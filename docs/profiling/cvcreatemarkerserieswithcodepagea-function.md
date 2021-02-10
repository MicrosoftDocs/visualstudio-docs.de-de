---
title: CvCreateMarkerSeriesWithCodePageA-Funktion | Microsoft-Dokumentation
description: Dieser Artikel enthält Referenzinformationen für die Funktion CvCreateMarkerSeriesWithCodePageA des Concurrency Visualizer-SDK (C-Bibliothek).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18e3367199154626703b671820d8d19d303630be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941020"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA-Funktion
Erstellt Markerreihen für einen angegebenen Anbieter und eine angegebene Codepage. Mit dieser Funktion kann die Codepage für den von Marker-API-ANSI-Funktionen ausgeschriebenen Text explizit angegeben werden. Das Festlegen der Codepage kann in Fällen nützlich sein, in denen die Ablaufverfolgung aufgezeichnet und anschließend auf unterschiedlichen Computern mit unterschiedlichen Gebietsschemas/Sprachen analysiert wird. Standardmäßig wird die von der GetACP()-Funktion zurückgegebene Codepage verwendet.

## <a name="syntax"></a>Syntax

```C
HRESULT CvCreateMarkerSeriesWithCodePageA(
   _In_ PCV_PROVIDER pProvider,
   _In_ LPCSTR pSeriesName,
   _In_ UINT nTextCodePage,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>Parameter
 `pProvider`: durch CvInitProvider bereits initialisiertes Anbieterobjekt. Lässt keine NULL-Werte zu.

 `pSeriesName` der Markerreihenname. Darf nicht NULL sein, aber eine leere Zeichenfolge ist zulässig.

 `nTextCodePage`: gültige Codepage.

 `ppMarkerSeries`: die Adresse einer Ausgabevariablen, mit der der Markerreihenkontext gespeichert wird. Lässt keine NULL-Werte zu.

## <a name="return-value"></a>Rückgabewert
 S_OK, wenn Markerreihen erfolgreich erstellt wurden, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkers.h*

## <a name="see-also"></a>Siehe auch
- [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)