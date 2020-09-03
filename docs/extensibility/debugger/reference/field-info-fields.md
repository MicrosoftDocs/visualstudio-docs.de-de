---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736910"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Gibt an, welche Informationen über ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_INFO_FIELDS { 
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

## <a name="requirements"></a>Anforderungen
Header: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
