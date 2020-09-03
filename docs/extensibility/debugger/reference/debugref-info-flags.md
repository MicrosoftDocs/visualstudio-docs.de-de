---
title: DEBUGREF_INFO_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737392"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Gibt an, welche Informationen über ein debugverweisobjekt abgerufen werden.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Felder
`DEBUGREF_INFO_NAME`\
Initialisieren/verwenden Sie das- `bstrName` Feld in der-Struktur.

`DEBUGREF_INFO_TYPE`\
Initialisieren/verwenden Sie das- `bstrType` Feld in der-Struktur.

`DEBUGREF_INFO_VALUE`\
Initialisieren/verwenden Sie das- `bstrValue` Feld in der-Struktur.

`DEBUGREF_INFO_ATTRIB`\
Initialisieren/verwenden Sie das- `dwAttrib` Feld in der-Struktur.

`DEBUGREF_INFO_REFTYPE`\
Initialisieren/verwenden Sie das- `dwRefType` Feld in der-Struktur.

`DEBUGREF_INFO_REF`\
Initialisieren/verwenden Sie das- `pReference` Feld in der-Struktur.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
Das Wertfeld muss den automatisch erweiterten Wert für diesen Objekttyp enthalten, falls verfügbar.

`DEBUGREF_INFO_NONE`\
Gibt an, dass keine Flags festgelegt sind.

`DEBUGREF_INFO_ALL`\
Gibt eine Maske der Flags an.

## <a name="remarks"></a>Bemerkungen
Diese Flags werden an die [enumchildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) -Methode und die [getreferencanfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) -Methode übergeben, um anzugeben, welche Felder der [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur initialisiert werden sollen.

Wird für den- `dwFields` Member der `DEBUG_REFERENCE_INFO` -Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind, wenn die-Struktur zurückgegeben wird.

Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
