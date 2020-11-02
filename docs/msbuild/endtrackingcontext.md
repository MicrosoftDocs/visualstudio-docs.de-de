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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da1ef921106732a7787f68a979bc88f3ac012b6d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436671"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Beenden des aktuellen Nachverfolgungskontexts.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Rückgabewert

Ein **HRESULT** , bei dem **SUCCEEDED** festgelegt ist, wenn der Nachverfolgungskontext beendet wurde.

## <a name="requirements"></a>Anforderungen

**Header:** *FileTracker.h*

## <a name="see-also"></a>Weitere Informationen:

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
