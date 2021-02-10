---
title: StopTrackingAndCleanup | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe von „StopTrackingAndCleanup“ die Nachverfolgung vollständig beendet und Speicherplatz freigibt, der von der Nachverfolgungssitzung belegt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e74e44289e4fd04acf82170584af8645767b63e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905235"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Beendet die Nachverfolgung vollständig und macht Speicherplatz frei, der von der Nachverfolgungssitzung verwendet wird

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Rückgabewert

 Gibt ein **HRESULT** zurück, bei dem **SUCCEEDED** festgelegt ist, wenn die Nachverfolgung beendet wurde

## <a name="requirements"></a>Anforderungen

 **Header:** *FileTracker.h*

## <a name="see-also"></a>Weitere Informationen:

- [StartTrackingContext](../msbuild/starttrackingcontext.md)