---
title: 'IDebugProgramNode2:: Attach_V7 | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b143477dc558b20a302a54d5baecc64d02d33ea3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898635"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Veraltet. Verwenden Sie nicht.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>Parameter

`pMDMProgram`\
in Die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle, die das an anzufügende Programm darstellt.

`pCallback`\
in Die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Schnittstelle, die zum Senden von debuggingereignissen an SDM verwendet werden soll.

`dwReason`\
in Ein Wert aus der [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) Enumeration, die den Grund für das Anfügen angibt.

## <a name="return-value"></a>Rückgabewert

Eine-Implementierung sollte immer zurückgeben `E_NOTIMPL` .

## <a name="remarks"></a>Bemerkungen

> [!WARNING]
> Ab Visual Studio 2005 wird diese Methode nicht mehr verwendet und sollte immer zurückgeben `E_NOTIMPL` . Eine alternative Vorgehensweise finden Sie unter der [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) -Schnittstelle, wenn der Programmknoten angeben muss, dass er nicht angefügt werden kann oder wenn der Programmknoten das Programm einfach festlegt `GUID` . Implementieren Sie andernfalls die [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode.

## <a name="prior-to-visual-studio-2005"></a>Vor Visual Studio 2005

Diese Methode muss nur implementiert werden, wenn die de im Adressraum des Programms ausgeführt wird, das gedeppt wird. Andernfalls sollte diese Methode zurückgeben `S_FALSE` .

Wenn diese Methode aufgerufen wird, muss die de das [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Ereignis Objekt senden, wenn es nicht bereits für diese Instanz der [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) -Schnittstelle gesendet wurde, sowie die [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -und [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) -Ereignis Objekte. Das [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) -Ereignis Objekt wird dann gesendet, wenn der- `dwReason` Parameter ist `ATTACH_REASON_LAUNCH` .

Der Dienst muss die [getProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) -Methode für das [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt aufrufen, das vom [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Ereignis Objekt bereitgestellt wird, und muss die GUID des Programms in den Instanzdaten für das Objekt speichern, `IDebugProgram2` das von der de implementiert wird.

## <a name="see-also"></a>Weitere Informationen

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
