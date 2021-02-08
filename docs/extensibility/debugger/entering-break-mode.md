---
title: Wechseln in den Umbruch Modus | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Prozess, der für einen Haltepunkt in einer Funktion auftritt, in der Zeile des Quellcodes am Cursor ausgeführt wird oder bis zu einem Breakpoint ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3ec09994f6998f87daafc690b1908b31e54706b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840651"
---
# <a name="enter-break-mode"></a>In den Umbruch Modus wechseln
Die folgenden Informationen beschreiben den Prozess, der auftritt, wenn nach dem Durchlaufen einer Funktion ein Haltepunkt erreicht wird, der in der Zeile des Quellcodes ausgeführt wird, in der sich der Cursor befindet, oder bis zu einem Breakpoint ausgeführt wird.

## <a name="break-mode-process"></a>Prozess für den Abbruch Modus

1. Die Debug-Engine (de) sendet [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)oder ein beliebiges anderes anhalteereignis, um zu bewirken, dass die IDE in den Umbruch Modus wechselt.

2. Der SDM Ruft die aufrufstackinformationen aus dem Thread wie folgt ab:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2:: getdocumentcontext zum Abrufen](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) der Quell Code Informationen

    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) , um den Dateinamen zu erhalten

    - [IDebugDocumentContext2:: getstatuementrange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) zum erhalten des Anweisungs Bereichs

    - [IDebugStackFrame2:: getcodecontext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) zum erhalten von Speicherinformationen

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debugger-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
