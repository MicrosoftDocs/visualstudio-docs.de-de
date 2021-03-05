---
description: Ruft eine Liste der untergeordneten Elemente der-Eigenschaft ab.
title: 'IDebugProperty2:: enumchildren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c9cade8cb0468c78ba03e2beec682d7c2284be0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166956"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Ruft eine Liste der untergeordneten Elemente der-Eigenschaft ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
in Eine Kombination von Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, die angibt, welche Felder in den aufgelisteten [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen ausgefüllt werden sollen.

`dwRadix`\
in Gibt das Basis an, das beim Formatieren numerischer Informationen verwendet werden soll.

`guidFilter`\
in GUID des Filters, der mit dem `dwAttribFilter` -Parameter und dem-Parameter verwendet wird `pszNameFilter` , um auszuwählen, welche untergeordneten Elemente `DEBUG_PROPERTY_INFO` aufgelistet werden sollen. Beispielsweise `guidFilterLocals` Filter für lokale Variablen.

`dwAttribFilter`\
in Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Enumeration, die angibt, welcher Typ von Objekten aufgelistet werden soll, z `DBG_ATTRIB_METHOD` . b. für alle Methoden, die möglicherweise untergeordnete Elemente dieser Eigenschaft sind. Wird in Kombination mit `guidFilter` den `pszNameFilter` Parametern und verwendet.

`pszNameFilter`\
in Der Name des Filters, der mit dem `guidFilter` -Parameter und dem-Parameter verwendet wird `dwAttribFilter` , um auszuwählen, welche untergeordneten Elemente `DEBUG_PROPERTY_INFO` aufgelistet werden sollen. Wenn Sie diesen Parameter beispielsweise auf "MYX"-Filter für alle untergeordneten Elemente mit dem Namen "MYX" festlegen.

`dwTimeout`\
in Gibt die maximale Zeit in Millisekunden an, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden `INFINITE` Sie, um unbegrenzt zu warten.

`ppEnum`\
vorgenommen Gibt ein [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt zurück, das eine Liste der untergeordneten Eigenschaften enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
