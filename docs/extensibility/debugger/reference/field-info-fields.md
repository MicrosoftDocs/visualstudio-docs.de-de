---
description: Gibt an, welche Informationen über ein idebugfield-Objekt abgerufen werden sollen.
title: FIELD_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 024c12d5112398e055141a8db4995f2801ca5401
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170288"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Gibt an, welche Informationen über ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>Felder
`FIF_FULLNAME`\
Initialisieren Sie das `bstrFullName` Feld in der [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur, und verwenden Sie es.

`FIF_NAME`\
Initialisieren/verwenden Sie das- `bstrName` Feld in der- `FIELD_INFO` Struktur.

`FIF_TYPE`\
Initialisieren/verwenden Sie das- `bstrType` Feld in der- `FIELD_INFO` Struktur.

`FIF_MODIFIERS`\
Initialisieren/verwenden Sie das- `bstrModifiers` Feld in der- `FIELD_INFO` Struktur.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden auch als Argument an die [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) -Methode übermittelt, um anzugeben, welche Felder der [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur initialisiert werden sollen.

Diese Werte werden auch im- `dwFields` Member der `FIELD_INFO` -Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.

Diese Flags können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Requirements (Anforderungen)
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
