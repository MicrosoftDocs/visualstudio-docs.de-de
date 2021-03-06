---
description: Ruft eine ausführliche Beschreibung der Ausnahme ab, die dieses Ereignis ausgelöst hat.
title: 'IDebugExceptionEvent2:: GetException | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6505cd2309323d7fe91f2c807af33555c3575fd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152896"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Ruft eine ausführliche Beschreibung der Ausnahme ab, die dieses Ereignis ausgelöst hat.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>Parameter
`pExceptionInfo`\
[in, out] Eine [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur, die mit der Beschreibung der Ausnahme ausgefüllt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen

 [Nur C++] Der Aufrufer ist für das Freigeben von Zeichen folgen in der [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur und das Freigeben des [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekts in der Struktur verantwortlich.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
