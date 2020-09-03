---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737768"
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

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
