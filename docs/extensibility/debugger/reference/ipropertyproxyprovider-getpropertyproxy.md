---
title: 'Ipropertyproxyprovider:: getpropertyproxy | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7efff35e46ed0849045cf6c743a5a26c3d86bcd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962144"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
Ruft die eigenschaftenproxyschnittstelle für die angegebene Proxy-ID ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPropertyProxy(
   DWORD                  dwID,
   IPropertyProxyEESide** proxy
);
```

```csharp
int GetPropertyProxy(
   uint                     dwID,
   out IPropertyProxyEESide proxy
);
```

## <a name="parameters"></a>Parameter
`dwID`\
in ID des gewünschten Eigenschafts Proxys.

`proxy`\
vorgenommen Gibt ein [ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) -Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Zur Unterstützung externer typvisualisierungen leitet diese Methode den-Befehl in der Regel an die [getpropertyproxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) -Methode weiter. Ausführliche Informationen zur Art und Weise, wie ieevisualizerservice abgerufen wird, finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
