---
title: 'IDebugThread2:: getlogicalthread | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05d788f63d4807ccfd8e99d36cbf858df2be499f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940253"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Diese Methode wird von Debug-engines nicht implementiert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>Parameter
`pStackFrame`\
in Ein [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) -Objekt, das den Stapel Rahmen darstellt.

`ppLogicalThread`\
vorgenommen Gibt eine- `IDebugLogicalThread2` Schnittstelle zurück, die den zugeordneten logischen Thread darstellt. Eine Debug-Engine-Implementierung sollte diese auf einen NULL-Wert festlegen.

## <a name="return-value"></a>Rückgabewert
 Debug-Engine-Implementierungen geben immer zurück `E_NOTIMPL` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
