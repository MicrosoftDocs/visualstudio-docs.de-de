---
title: 'IDebugEngine2:: kreateperdingbreakpoint | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93534a40d523c7b67a769ebea319463cf59e4b7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879019"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Erstellt einen ausstehenden Haltepunkt in der Debug-Engine (de).

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Parameter
`pBPRequest`\
in Ein [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) -Objekt, das den zu erstellenden ausstehenden Breakpoint beschreibt.

`ppPendingBP`\
vorgenommen Gibt ein [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Objekt zurück, das den ausstehenden Haltepunkt darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt in der Regel zurück, `E_FAIL` Wenn der- `pBPRequest` Parameter keiner Sprache entspricht, die von der de von unterstützt wird, wenn der- `pBPRequest` Parameter ungültig oder unvollständig ist.

## <a name="remarks"></a>Bemerkungen
Ein ausstehender Haltepunkt ist im Wesentlichen eine Sammlung aller Informationen, die erforderlich sind, um einen Breakpoint an Code zu binden. Der von dieser Methode zurückgegebene ausstehende Haltepunkt ist erst an den Code gebunden, wenn die [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) -Methode aufgerufen wird.

Für jeden ausstehenden Haltepunkt, den der Benutzer festlegt, ruft der Sitzungs-Debug-Manager (SDM) diese Methode in jeder angefügten de auf. Es liegt an der de, zu überprüfen, ob der Breakpoint für Programme gültig ist, die in dieser de ausgeführt werden.

Wenn der Benutzer einen Haltepunkt in einer Codezeile festlegt, kann de den Haltepunkt an die nächstgelegene Zeile im Dokument binden, die diesem Code entspricht. Dies ermöglicht es dem Benutzer, einen Haltepunkt in der ersten Zeile einer mehrzeiligen Anweisung festzulegen, ihn aber an die letzte Zeile zu binden (wobei der gesamte Code in den Debuginformationen attributiert ist).

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches-Objekt implementiert wird `CProgram` . Die de-Implementierung von `IDebugEngine2::CreatePendingBreakpoint` kann dann alle Aufrufe an diese Implementierung der-Methode in jedem Programm weiterleiten.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Zwick](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
