---
description: Gibt an, welche Informationen über ein Debug-Eigenschaften Objekt abgerufen werden sollen.
title: DEBUGPROP_INFO_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63467e93b80648e6a00728dc66971b7c9b3c9b24
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170522"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Gibt an, welche Informationen über ein Debug-Eigenschaften Objekt abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Felder
`DEBUGPROP_INFO_FULLNAME`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrFullName` .

`DEBUGPROP_INFO_NAME`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrName` .

`DEBUGPROP_INFO_TYPE`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrType` .

`DEBUGPROP_INFO_VALUE`\
Initialisieren Sie das Feld, und verwenden Sie es `bstrValue` .

`DEBUGPROP_INFO_ATTRIB`\
Initialisieren Sie das Feld, und verwenden Sie es `dwAttrib` .

`DEBUGPROP_INFO_PROP`\
Initialisieren/verwenden Sie das `pProperty` Feld, das eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle enthält.

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Gibt an, dass das Wertfeld für diesen Objekttyp den automatisch erweiterten Wert enthalten soll, falls verfügbar.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Veraltet.

`DEBUGPROP_INFO_VALUE_RAW`\
Geben Sie keine verzierten Werte oder Member zurück (d. h. die Werte nicht formatieren).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Geben Sie keine besonderen Werte mit synthetischer Wert zurück (z. b. nicht für `ToString()` ein Objekt aufzurufen, um einen Wert zu erhalten).

`DEBUGPROP_INFO_NONE`\
Gibt an, dass keine Flags festgelegt wurden.

`DEBUGPROP_INFO_STANDARD`\
Initialisieren/verwenden Sie `dwAttrib` die `bstrName` Felder,, `bstrType` und `bstrValue` .

`DEBUGPROP_INFO_All`\
Gibt eine Maske aller Flags an.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden an die Methoden [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)und [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) übermittelt, um anzugeben, welche Felder [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur initialisiert werden sollen.

Diese Werte werden auch für den `dwFields` -Member der `DEBUG_PROPERTY_INFO` -Struktur verwendet, um anzugeben, welche Felder der Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird.

Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
