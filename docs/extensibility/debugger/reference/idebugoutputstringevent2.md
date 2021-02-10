---
title: IDebugOutputStringEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8fa51311bb7548889cccdd2eb91e70a4679fb5de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953304"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Diese Schnittstelle wird von der Debug-Engine (de) an den Sitzungs-Debug-Manager (SDM) gesendet, um eine Zeichenfolge auszugeben.

## <a name="syntax"></a>Syntax

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle, um eine Zeichenfolge an das **Ausgabe** Fenster der IDE zu senden. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das de-Objekt erstellt und sendet dieses Ereignis Objekt, um eine Zeichenfolge an das **Ausgabe** Fenster zu senden. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von der SDM bereitgestellt wird, wenn Sie an das Programm angefügt wird, das gedeppt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle wird die-Methode von gezeigt `IDebugOutputStringEvent2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Ruft die Meldung ab, die angezeigt werden soll.|

## <a name="remarks"></a>Bemerkungen
 In nicht verwaltetem Code kann z. b. die auszugabeende Zeichenfolge entstehen, wenn das Programm, das debuggt wird, eine Zeichenfolge an die Win32- `OutputDebugString` Funktion sendet. Diese Zeichenfolge wird von der de abgefangen und als Ereignis an die SDM gesendet `IDebugOutputStringEvent2` .

 Verwenden Sie [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) , um eine Nachricht zu senden, die eine Benutzer Antwort erfordert.

 Verwenden Sie [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) , um eine Fehlermeldung zu senden, für die keine Antwort erforderlich ist.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
