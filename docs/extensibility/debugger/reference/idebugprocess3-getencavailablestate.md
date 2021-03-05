---
description: Diese Methode ruft den aktuellen Zustand "Bearbeiten und Fortfahren" des Prozesses ab.
title: 'IDebugProcess3:: getencavailablestate | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13ad3bc88ab1e9f10dc87db7d7124adc993b168c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149774"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Diese Methode ruft den aktuellen Zustand "Bearbeiten und Fortfahren" des Prozesses ab. Ein benutzerdefinierter Port Lieferant sollte immer zurückgeben `E_NOTIMPL` .

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>Parameter
`pReason`\
vorgenommen Ein Wert [aus der](../../../extensibility/debugger/reference/encunavailablereason.md) Enumeration "Enumeration" in "Enumeration".

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

> [!NOTE]
> Ein benutzerdefinierter Port Lieferant sollte immer zurückgeben `E_NOTIMPL` .

## <a name="remarks"></a>Bemerkungen
 Dieser Status kann von [disableumc](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)beeinflusst werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
