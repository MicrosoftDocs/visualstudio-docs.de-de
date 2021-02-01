---
title: CvInitProvider-Funktion | Microsoft-Dokumentation
description: Dieser Artikel enthält Referenzinformationen für die Funktion CvInitProvider des Concurrency Visualizer-SDK (C-Bibliothek).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d1b41d9d62bbf5a159ec3a9d60f4e2edf5cc115
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686505"
---
# <a name="cvinitprovider-function"></a>CvInitProvider-Funktion
Initialisiert Markeranbieter. Muss vor anderen Funktionen des SDK für die Nebenläufigkeitsschnellansicht aufgerufen werden.

## <a name="syntax"></a>Syntax

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parameter
 `pGuid`: die Anbieter-GUID. Lässt keine NULL-Werte zu.

 `ppProvider`: die Adresse einer Ausgabevariablen, mit der der Anbieterkontext gespeichert wird. Lässt keine NULL-Werte zu.

## <a name="return-value"></a>Rückgabewert
 S_OK, wenn der Anbieter erfolgreich initialisiert wurde, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkers.h*

## <a name="see-also"></a>Siehe auch
- [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)