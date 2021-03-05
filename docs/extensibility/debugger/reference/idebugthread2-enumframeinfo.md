---
description: Ruft eine Liste der Stapel Rahmen für diesen Thread ab.
title: 'IDebugThread2:: enumframeinfo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9ad740de00338596de622cbce1028768ddda638
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149339"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Ruft eine Liste der Stapel Rahmen für diesen Thread ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`dwFieldSpec`\
in Eine Kombination von Flags aus der [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Enumeration, die angibt, welche Felder der [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen ausgefüllt werden sollen. Geben `FIF_FUNCNAME_FORMAT` Sie das Flag an, um den Funktionsnamen in einer einzelnen Zeichenfolge zu formatieren.

`nRadix`\
in Der zum Formatieren von numerischen Informationen im Enumerator verwendete Radix.

`ppEnum`\
vorgenommen Gibt ein [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) -Objekt zurück, das eine Liste der [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen enthält, die den Stapel Rahmen beschreiben.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Rahmen des Threads werden in der Reihenfolge aufgelistet, wobei der aktuelle Frame zuerst aufgezählt und der älteste enumerationsframe zuletzt aufgeführt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
