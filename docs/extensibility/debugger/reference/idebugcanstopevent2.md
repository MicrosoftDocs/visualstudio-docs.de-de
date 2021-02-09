---
title: IDebugCanStopEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 87306e1373d746479ce59c96b6625fa41ef119fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903240"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Diese Schnittstelle wird verwendet, um den Sitzungs-Debug-Manager (SDM) zu Fragen, ob er am aktuellen Code Speicherort angehalten werden soll.

## <a name="syntax"></a>Syntax

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um das Durchlaufen des Quellcodes zu unterstützen. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden (SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle).

 Die Implementierung dieser Schnittstelle muss den SDM-Befehl [canstoppt](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) an die Debug-Engine übermitteln. Dies kann z. b. mit einer Nachricht erfolgen, die an den Meldungs Behandlungs Thread der Debug-Engine gesendet wurde, oder das Objekt, das diese Schnittstelle implementiert, kann einen Verweis auf die Debug-Engine enthalten und einen Rückruf in die Debug-Engine mit dem an übergeben `IDebugCanStopEvent2::CanStop` .

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die de kann diese Methode jedes Mal senden, wenn die de aufgefordert wird, die Ausführung fortzusetzen, und die de den Code schrittweise durchläuft. Dieses Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von SDM beim Anfügen an das gedestete Programm bereitgestellt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugCanStopEvent2` .

|Methode|Beschreibung|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ruft den Grund für dieses Ereignis ab.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Gibt an, ob das Programm, das gedebuggt wird, an der Position dieses Ereignisses angehalten werden soll (und ein Ereignis senden soll, das den Grund für das Beenden beschreibt), oder die Ausführung einfach|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ruft den Dokument Kontext ab, der den Speicherort dieses Ereignisses beschreibt.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ruft den Code Kontext ab, der den Speicherort dieses Ereignisses beschreibt.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird von der de gesendet, wenn der Benutzer eine Funktion durchführt und die Datei keine Debuginformationen findet oder wenn die Debuginformationen vorhanden sind, aber der de-Code nicht weiß, ob der Quellcode für diese Position angezeigt werden kann.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
