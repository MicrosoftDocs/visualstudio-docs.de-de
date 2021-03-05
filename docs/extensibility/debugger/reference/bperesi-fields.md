---
description: Gibt die Informationen an, die bei einer fehlgeschlagenen Auflösung eines Breakpoints abgerufen werden sollen.
title: BPERESI_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e26b5a7285c2e5c9135429777b4b58f35252e550
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162523"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Gibt die Informationen an, die bei einer fehlgeschlagenen Auflösung eines Breakpoints abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Felder
`PERESI_BPRESLOCATION`\
Initialisieren/verwenden Sie das `bpResLocation` Feld (breakpointlösungsort) der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) -Struktur.

`BPERESI_PROGRAM`\
Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `pProgram` `BP_ERROR_RESOLUTION_INFO` .

`BPERESI_THREAD`\
Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `pThread` `BP_ERROR_RESOLUTION_INFO` .

`BPERESI_MESSAGE`\
Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `bstrMessage` `BP_ERROR_RESOLUTION_INFO` .

`BPERESI_TYPE`\
Initialisieren/verwenden Sie das `dwType` Feld (breakpointtyp) der- `BP_ERROR_RESOLUTION_INFO` Struktur.

`BPERESI_ALLFIELDS`\
Initialisieren/verwenden Sie alle Felder der- `BP_ERROR_RESOLUTION_INFO` Struktur.

## <a name="remarks"></a>Bemerkungen
Wird als Parameter an die [getresolutioninfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) -Methode übergeben, um anzugeben, welche Felder der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur initialisiert werden sollen.

Diese Werte werden auch verwendet, um anzugeben, welche Felder in der `BP_ERROR_RESOLUTION_INFO` Struktur verwendet und gültig sind, wenn diese Struktur zurückgegeben wird.

Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
