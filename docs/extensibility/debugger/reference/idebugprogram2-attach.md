---
title: 'IDebugProgram2:: Attach | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f42aa8ff646a62f7314887df4b38c648e2d84b31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931447"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Wird an das Programm angefügt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>Parameter
`pCallback`\
in Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das für die Debug-Ereignis Benachrichtigung verwendet werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. In der folgenden Tabelle sind einige mögliche Fehlercodes aufgeführt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Das angegebene Programm ist bereits an den Debugger angefügt.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Während der Anfüge Prozedur ist ein Sicherheits Verstoß aufgetreten.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Ein Desktop Programm kann nicht an den Debugger angefügt werden.|

## <a name="remarks"></a>Bemerkungen
 Eine Debug-Engine (de) ruft diese Methode niemals auf, um Sie an ein Programm anzufügen. Wenn die de im Adressraum des Programms ausgeführt wird, wird die [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode aufgerufen. Wenn die de im Adressraum des Sitzungs-Debug-Managers (SDM) ausgeführt wird, wird die [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode aufgerufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
