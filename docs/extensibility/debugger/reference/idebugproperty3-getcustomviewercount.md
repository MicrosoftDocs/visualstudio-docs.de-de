---
title: 'IDebugProperty3:: getcustomviewercount | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffdca7e4a556a72c8fb7f3f533e69d47fa289732
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896089"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Ruft die Anzahl der benutzerdefinierten Viewer ab, die möglicherweise für diese Eigenschaft verfügbar sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>Parameter
`pcelt`\
vorgenommen Die Anzahl der für diese Eigenschaft verfügbaren benutzerdefinierten Viewer.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Zur Unterstützung von typvisualisierungen leitet diese Methode den-Befehl an die [getcustomviewercount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) -Methode weiter. Wenn die Ausdrucks Auswertung auch benutzerdefinierte Viewer für diesen Eigenschaftentyp unterstützt, fügt diese Methode die Anzahl der benutzerdefinierten Viewer dem zurückgegebenen Wert hinzu.

Ausführliche Informationen zu den Unterschieden zwischen typvisualisierungen und benutzerdefinierten Viewern finden Sie unter [typvisualizer und Custom Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cproperty** -Objekt implementiert wird, das die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle verfügbar macht.

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
