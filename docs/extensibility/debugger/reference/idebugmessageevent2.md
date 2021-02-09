---
title: IDebugMessageEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6796e2d4f3a7fa20e4bcab4088b6687866edf570
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928262"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Diese Schnittstelle wird von der Debug-Engine (de) verwendet, um eine Nachricht an Visual Studio zu senden, die eine Antwort vom Benutzer erfordert.

## <a name="syntax"></a>Syntax

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle, um eine Nachricht an Visual Studio zu senden, die eine Benutzer Antwort erfordert. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle.

 Die Implementierung dieser Schnittstelle muss den Visual Studio-Befehl [setresponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) mit der de kommunizieren. Dies kann z. b. mit einer Nachricht erfolgen, die an den Nachrichten Behandlungs Thread von de gesendet wurde, oder das Objekt, das diese Schnittstelle implementiert, kann einen Verweis auf die de enthalten und mit der Antwort an die de zurückgeben `IDebugMessageEvent2::SetResponse` .

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das de-Objekt erstellt und sendet dieses Ereignis Objekt, um dem Benutzer eine Meldung anzuzeigen, die eine Antwort erfordert. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von der SDM bereitgestellt wird, wenn Sie an das Programm angefügt wird, das gedeppt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugMessageEvent2` .

|Methode|Beschreibung|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ruft die Meldung ab, die angezeigt werden soll.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Legt die Antwort, sofern vorhanden, aus dem Meldungs Feld fest.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird von de verwendet, wenn für eine bestimmte Nachricht eine bestimmte Antwort vom Benutzer erforderlich ist. Wenn z. b. "de" nach einem Remote Anfügen an ein Programm eine Meldung "Zugriff verweigert" erhält, sendet der de diese Nachricht in einem Ereignis mit dem Format "MessageBox" an Visual Studio `IDebugMessageEvent2` `MB_RETRYCANCEL` . Dadurch kann der Benutzer den Anfüge Vorgang wiederholen oder Abbrechen.

 Der Dienst gibt an, wie diese Nachricht behandelt werden soll, indem Sie den Konventionen der Win32-Funktion folgt `MessageBox` (Weitere Informationen finden Sie unter [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) ).

 Verwenden Sie die [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) -Schnittstelle zum Senden von Nachrichten an Visual Studio, für die keine Antwort vom Benutzer erforderlich ist.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
