---
description: Wird vom Debugger auf dem aktuellen Stapel Rahmen aufgerufen, wenn die aktuelle Ausnahme abgefangen werden soll.
title: 'IDebugStackFrame3:: intercepteption TException | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93fa7f73b3e13c655716ecbb16ff420605f76c90
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145780"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Wird vom Debugger auf dem aktuellen Stapel Rahmen aufgerufen, wenn die aktuelle Ausnahme abgefangen werden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Parameter
`dwFlags`\
in Gibt verschiedene Aktionen an. Derzeit wird nur der [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) Wert `IEA_INTERCEPT` unterstützt und muss angegeben werden.

`pqwCookie`\
vorgenommen Eindeutiger Wert, der eine bestimmte Ausnahme identifiziert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

 Im folgenden finden Sie die häufigsten Fehler, die zurückgegeben werden.

|Fehler|BESCHREIBUNG|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Die aktuelle Ausnahme kann nicht abgefangen werden.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Der aktuelle Ausführungs Rahmen wurde noch nicht nach einem Handler durchsucht.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Diese Methode wird für diesen Frame nicht unterstützt.|

## <a name="remarks"></a>Bemerkungen
 Wenn eine Ausnahme ausgelöst wird, erhält der Debugger die Steuerung der Laufzeit an wichtigen Punkten während der Ausnahmebehandlung. In diesen Zeitpunkten kann der Debugger den aktuellen Stapel Rahmen Abfragen, wenn der Frame die Ausnahme abfangen möchte. Auf diese Weise handelt es sich bei einer abgefangenen Ausnahme im Wesentlichen um einen direkt unter Laufwerks Ausnahmehandler für einen Stapel Rahmen, auch wenn dieser Stapel Rahmen keinen Ausnahmehandler hat (z. b. ein try/catch-Block im Programmcode).

 Wenn der Debugger wissen möchte, ob die Ausnahme abgefangen werden soll, wird diese Methode für das aktuelle Stapel Rahmen Objekt aufgerufen. Diese Methode ist für die Verarbeitung aller Details der Ausnahme verantwortlich. Wenn die [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) -Schnittstelle nicht implementiert ist oder die `InterceptStackException` Methode einen Fehler zurückgibt, setzt der Debugger die Verarbeitung der Ausnahme in der Regel fort.

> [!NOTE]
> Ausnahmen können nur in verwaltetem Code abgefangen werden, d. h., wenn das decodierende Programm unter der .NET-Laufzeit ausgeführt wird. Selbstverständlich können sprach Implementierungen von Drittanbietern `InterceptStackException` in ihren eigenen Debug-engines implementieren, wenn Sie dies auswählen.

 Nach Abschluss der Abfang Funktion wird ein [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) signalisiert.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
