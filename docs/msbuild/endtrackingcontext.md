---
title: EndTrackingContext | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Syntax, den Rückgabewert und die Anforderungen für die Verwendung der MSBuild-Aufgabe „EndTrackingContext“ zum Beenden des aktuellen Nachverfolgungskontexts.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90f4c8c4a83a496dba537e74dddfde4ae3f2f21a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877225"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Beenden des aktuellen Nachverfolgungskontexts.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Rückgabewert

Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn der Nachverfolgungskontext beendet wurde.

## <a name="requirements"></a>Anforderungen

**Header:** *FileTracker.h*

## <a name="see-also"></a>Weitere Informationen:

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
