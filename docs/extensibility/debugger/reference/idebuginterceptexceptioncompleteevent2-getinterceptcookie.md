---
description: Wird aufgerufen, wenn die Verarbeitung einer abgefangenen Ausnahme abgeschlossen wurde.
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70fb92c20eab3700043a11f8544896bbbce3b7c6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172531"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Wird aufgerufen, wenn die Verarbeitung einer abgefangenen Ausnahme abgeschlossen wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetInterceptCookie(
   UINT64* pqwCookie
);
```

```csharp
int GetInterceptCookie(
   out ulong pqwCookie
);
```

## <a name="parameters"></a>Parameter
`pqwCookie`\
vorgenommen Eindeutiger Wert, der der abgefangenen Ausnahme zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nachdem die [interceptaccesstexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) -Methode die Verarbeitung einer abgefangenen Ausnahme abgeschlossen hat, sendet Sie das [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) -Ereignis. Der-Handler kann die- `GetInterceptCookie` Methode verwenden, um den eindeutigen Wert abzurufen, der der Ausnahme zugeordnet ist (derselbe Wert, der an die-Methode übertragen wird `InterceptCurrentException` ).

## <a name="see-also"></a>Weitere Informationen
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
