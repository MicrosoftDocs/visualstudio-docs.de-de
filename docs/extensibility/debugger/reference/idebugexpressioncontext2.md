---
title: IDebugExpressionContext2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92e2561d28c3d4c7133208c78b9a492bc2614fd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901656"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Diese Schnittstelle stellt einen Kontext für die Ausdrucks Auswertung dar.

## <a name="syntax"></a>Syntax

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um einen Kontext darzustellen, in dem ein Ausdruck ausgewertet werden kann.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufrufen von [getexpressioncontext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) gibt die dieser Schnittstelle zurück. Auf diese Schnittstelle kann nur zugegriffen werden, wenn das Programm, das gedeppt wird, angehalten wurde und ein Stapel Rahmen verfügbar ist.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugExpressionContext2` .

|Methode|Beschreibung|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Ruft den Namen des Auswertungs Kontexts ab.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analysiert einen textbasierten Ausdruck für die Auswertung.|

## <a name="remarks"></a>Bemerkungen
 Ein Auswertungs Kontext kann als Bereich zum Durchführen der Ausdrucks Auswertung betrachtet werden.

 Wenn ein Programm angehalten wurde, erhält der Sitzungs-Debug-Manager (SDM) einen Stapel Rahmen von der de mit einem aufzurufenden [enumframeinfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)-Aufrufs. Der SDM ruft dann [getexpressioncontext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um die `IDebugExpressionContext2` Schnittstelle zu erhalten. Darauf folgt ein aufruftertext [](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , um eine [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle zu erstellen, die den analysierten Ausdruck darstellt, der für die Auswertung bereit ist.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
