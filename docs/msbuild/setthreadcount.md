---
title: SetThreadCount | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe von „SetThreadCount“ die globale Threadanzahl festlegt und diese Anzahl dem aktuellen Thread zuweist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7282b8c4589007492e48994628910b3a4ef0691
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966161"
---
# <a name="setthreadcount"></a>SetThreadCount

Legt die Anzahl der globalen Threads fest, und weist diese Anzahl für dem aktuellen Thread zu.

## <a name="syntax"></a>Syntax

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parameter

[in] `threadCount`

 Die Anzahl der zu verwendenden Threads.

## <a name="return-value"></a>Rückgabewert

 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn die Anzahl der Threads aktualisiert wurde.

## <a name="requirements"></a>Anforderungen

 **Header:** *FileTracker.h*