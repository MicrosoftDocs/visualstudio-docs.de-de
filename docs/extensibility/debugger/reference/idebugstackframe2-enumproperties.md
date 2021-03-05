---
description: Erstellt einen Enumerator für Eigenschaften, die dem Stapel Rahmen zugeordnet sind, z. b. lokale Variablen.
title: 'IDebugStackFrame2:: EnumProperties | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 40298e505f0d3ccbba200c5487a1bf1d6723f5b2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145962"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Erstellt einen Enumerator für Eigenschaften, die dem Stapel Rahmen zugeordnet sind, z. b. lokale Variablen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`dwFieldSpec`\
in Eine Kombination von Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, die angibt, welche Felder in den aufgelisteten [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen ausgefüllt werden sollen.

`nRadix`\
in Der zum Formatieren numerischer Informationen zu verwendende Basis.

`refiid`\
in Eine GUID eines Filters, der verwendet wird, um auszuwählen, welche [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen aufgelistet werden sollen, z `guidFilterLocals` . b..

`dwTimeout`\
in Maximale Zeit in Millisekunden, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden `INFINITE` Sie, um unbegrenzt zu warten.

`pcelt`\
vorgenommen Gibt die Anzahl der aufgelisteten Eigenschaften zurück. Dies entspricht dem Aufrufen der [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) -Methode.

`ppEnum`\
vorgenommen Gibt ein [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt zurück, das eine Liste der gewünschten Eigenschaften enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Da diese Methode zulässt, dass alle ausgewählten Eigenschaften mit einem einzigen Aufruf abgerufen werden, ist Sie schneller als das sequenzielle Aufrufen der [getdebugproperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) -Methode und der [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) -Methode.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
