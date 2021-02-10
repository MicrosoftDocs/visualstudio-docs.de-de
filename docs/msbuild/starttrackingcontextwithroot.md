---
title: StartTrackingContextWithRoot | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe von „StartTrackingContextWithRoot“ einen Nachverfolgungskontext unter Verwendung einer Antwortdatei startet, die einen Stammmarker angibt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b52541c99fa81f31eddde8e6c12ad2eee04f3c20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967045"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Startet einen Nachverfolgungskontext mithilfe einer Antwortdatei, die einen Stammmarker angibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parameter

[in] `intermediateDirectory`

 Das Verzeichnis, in dem das Nachverfolgungsprotokoll gespeichert werden soll

[in] `taskName`

 Identifiziert den Nachverfolgungskontext. Dieser Name wird verwendet, um den Protokolldateinamen zu erstellen.

[in] `rootMarkerResponseFile`

 Der Pfadname einer Antwortdatei mit einem Stammmarker. Der Stammname wird verwendet, um alle Nachverfolgungen für einen Kontext zusammen zu gruppieren.

## <a name="return-value"></a>Rückgabewert

 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn der Nachverfolgungskontext erstellt wurde

## <a name="requirements"></a>Anforderungen

 **Header:** *FileTracker.h*

## <a name="see-also"></a>Weitere Informationen:

- [StartTrackingContext](../msbuild/starttrackingcontext.md)