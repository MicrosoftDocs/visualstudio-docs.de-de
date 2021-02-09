---
title: IDebugStopCompleteEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bee46a1f097d1bee98354acb792f75ea9431f301
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897207"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Die Debug-Engine (de) kann dieses optionale Ereignis an den Sitzungs-Debug-Manager (SDM) senden, wenn ein Programm beendet wurde.

## <a name="syntax"></a>Syntax

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer

Diese Schnittstelle wurde mit Visual Studio 2005 eingeführt. Frühere Releases haben das asynchrone beenden nicht unterstützt.

- " [Beendet](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) " wird von SDM in Szenarios mit mehreren Prozessen oder mehreren Programmen aufgerufen. Wenn ein Programm ein anhalteereignis an SDM sendet, fordert der SDM auch andere Programme an, die ebenfalls beendet werden.

"Beenden" wird verwendet, um die SDM asynchron zu benachrichtigen, dass ein Programm beendet wurde. Das übermitteln der SDM ist für eine interpreterdebug-Engine nützlich, bei der manchmal kein Code im debuggten Programm ausgeführt wird. Daher kann " [Beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) " nicht synchron abgeschlossen werden. Wenn eine Debug-Engine diese asynchrone Benachrichtigung verwenden möchte, muss Sie von "Ende" zurückgegeben werden `S_ASYNC_STOP` . [](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)

## <a name="requirements"></a>Anforderungen

Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
