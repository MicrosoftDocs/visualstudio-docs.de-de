---
title: SuspendTracking| Microsoft-Dokumentation
description: Erfahren Sie mehr über Syntax, Anforderungen und Rückgabewert für die MSBuild-Funktion „SuspendTracking“ zum Anhalten der Nachverfolgung im aktuellen Kontext.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e8be768bc48c1815fc00069640e5bf3f4370f434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945278"
---
# <a name="suspendtracking"></a>SuspendTracking

Hält die Nachverfolgung des aktuellen Kontexts an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Rückgabewert

 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn die Nachverfolgung angehalten wurde.

## <a name="requirements"></a>Anforderungen

 **Header:** *FileTracker.h*

## <a name="see-also"></a>Weitere Informationen:

- [ResumeTracking](../msbuild/resumetracking.md)