---
description: Ruft eine Beschreibung des Stapel Rahmens ab.
title: 'IDebugStackFrame2:: GetInfo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3af7aafe43c0d7916a3fc11b855d5512f50a1d5f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168620"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Ruft eine Beschreibung des Stapel Rahmens ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

## <a name="parameters"></a>Parameter
`dwFieldSpec`\
in Eine Kombination von Flags aus der [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Enumeration, die angibt, welche Felder des `pFrameInfo` Parameters ausgefüllt werden sollen.

`nRadix`\
in Der zum Formatieren numerischer Informationen zu verwendende Basis.

`pFrameInfo`\
vorgenommen Eine [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Struktur, die mit der Beschreibung des Stapel Rahmens ausgefüllt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
