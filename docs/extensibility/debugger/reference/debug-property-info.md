---
description: Enthält Informationen über eine Debug-Eigenschaft.
title: DEBUG_PROPERTY_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0b02ca1f8c85f81096954fb416cc73ee400b9ba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170587"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
Enthält Informationen über eine Debug-Eigenschaft.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>Members
`dwValidFields`\
Eine Kombination von Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, die angibt, welche Felder ausgefüllt werden.

`bstrFullName`\
Der vollständige Name der Eigenschaft.

`bstrName`\
Der Eigenschaftsname innerhalb eines Kontexts.

`bstrType`\
Der Eigenschaftentyp als formatierte Zeichenfolge.

`bstrValue`\
Der Eigenschafts Wert als formatierte Zeichenfolge.

`pProperty`\
Das von dieser-Struktur beschriebene [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt.

`dwAttrib`\
Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) -Enumeration, die die Attribute dieser Eigenschaft beschreibt.

## <a name="remarks"></a>Bemerkungen
Eine Eigenschaft ist ein Objekt einer hierarchischen Natur, das einen Namen, einen Typ und einen Wert hat. Eine Eigenschaft kann z. b. lokale Variablen, Parameter, Überwachungs Variablen und Ausdrücke beschreiben und registriert werden.

Diese Struktur wird an die [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) -Methode übermittelt, wo Sie ausgefüllt ist. Diese Struktur wird auch als Teil einer Liste dieser Struktur von der [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Schnittstelle zurückgegeben, die wiederum von einem Rückruf der [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) -Methode und der [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) -Methode zurückgegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
