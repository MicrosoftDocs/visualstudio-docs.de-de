---
title: 'IDebugProperty3:: getcustomviewerlist | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdabe777bf2147dee2b98ca552183ae0e14d16f1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888211"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Ruft eine Liste von benutzerdefinierten Viewern ab, die dieser Eigenschaft zugeordnet sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCustomViewerList(
    ULONG                celtSkip,
    ULONG                celtRequested,
    DEBUG_CUSTOM_VIEWER* rgViewers,
    ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
    uint                  celtSkip,
    uint                  celtRequested,
    DEBUG_CUSTOM_VIEWER[] rgViewers,
    out uint              pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celtSkip`\
in Die Anzahl der zu über springenden Viewer.

`celtRequested`\
in Die Anzahl der abzurufenden Viewer (gibt auch die Größe des `rgViewers` Arrays an).

`rgViewers`\
[in, out] Array von [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen, die ausgefüllt werden sollen.

`pceltFetched`\
vorgenommen Die tatsächliche Anzahl der zurückgegebenen Viewer.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Zur Unterstützung von typvisualisierungen leitet diese Methode den Aufrufen an die [getcustomviewerlist](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) -Methode weiter. Wenn die Ausdrucks Auswertung auch benutzerdefinierte Viewer für diesen Eigenschaftentyp unterstützt, kann diese Methode die entsprechenden benutzerdefinierten Viewer an die Liste anfügen.

Ausführliche Informationen zu den Unterschieden zwischen typvisualisierungen und benutzerdefinierten Viewern finden Sie unter [typschnell Ansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cproperty** -Objekt implementiert wird, das die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle verfügbar macht.

```cpp
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)
{
    if (NULL == prgViewers)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
