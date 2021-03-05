---
description: Fügt den Sitzungs-Debug-Manager (SDM) an den Prozess an.
title: 'IDebugProcess2:: Attach | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73dbe76a32e67794736fd26595378485879b00b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161443"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Fügt den Sitzungs-Debug-Manager (SDM) an den Prozess an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parameter
`pCallback`\
in Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das für die debugereignisbenachrichtigung verwendet wird.

`rgguidSpecificEngines`\
in Ein Array von GUIDs von Debug-engines, das zum Debuggen von Programmen verwendet werden soll, die im Prozess ausgeführt werden. Dieser Parameter kann ein NULL-Wert sein. Einzelheiten finden Sie in den Hinweisen.

`celtSpecificEngines`\
in Die Anzahl der Debug-engines im `rgguidSpecificEngines` Array und die Größe des `rghrEngineAttach` Arrays.

`rghrEngineAttach`\
[in, out] Ein Array von HRESULT-Codes, die von den Debug-engines zurückgegeben werden. Die Größe dieses Arrays wird im-Parameter angegeben `celtSpecificEngines` . Jeder Code ist in der Regel entweder `S_OK` oder `S_ATTACH_DEFERRED` . Letztere gibt an, dass die de zurzeit an keine Programme angefügt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. In der folgenden Tabelle werden andere mögliche Werte angezeigt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Der angegebene Prozess ist bereits an den Debugger angefügt.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Während der Anfüge Prozedur ist ein Sicherheits Verstoß aufgetreten.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Ein Desktop Prozess kann nicht an den Debugger angefügt werden.|

## <a name="remarks"></a>Bemerkungen
 Beim Anfügen an einen Prozess wird die SDM an alle Programme angehängt, die in diesem Prozess ausgeführt werden und von den im Array angegebenen Debug-engines (de) debuggt werden können `rgguidSpecificEngines` . Legen Sie den- `rgguidSpecificEngines` Parameter auf einen Nullwert fest, oder fügen Sie ihn `GUID_NULL` in das Array ein, um ihn an alle Programme im Prozess anzufügen

 Alle Debugereignisse, die im Prozess auftreten, werden an das angegebene [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt gesendet. Dieses `IDebugEventCallback2` Objekt wird bereitgestellt, wenn die SDM diese Methode aufruft.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
