---
description: Gibt die Informationen an, die zur erfolgreichen Auflösung eines Breakpoints abgerufen werden sollen.
title: BPRESI_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91fa2a8b973149cb9365d817e14ac877bfc9f617
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171030"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Gibt die Informationen an, die zur erfolgreichen Auflösung eines Breakpoints abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Felder
`BPRESI_BPRESLOCATION`\
Initialisieren/verwenden Sie das `bpResLocation` Feld (breakpointlösungsort) der [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) -Struktur.

`BPRESI_PROGRAM`\
Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `pProgram` `BP_RESOLUTION_INFO` .

`BPRESI_THREAD`\
Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `pThread` `BP_RESOLUTION_INFO` .

`BPRESI_ALLFIELDS`\
Gibt alle Felder an.

## <a name="remarks"></a>Bemerkungen
Wird an die [getresolutioninfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) -Methode übermittelt, um anzugeben, welche Felder der [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Struktur initialisiert werden sollen.

Diese Flags werden auch verwendet, um anzugeben, welche Felder der `BP_RESOLUTION_INFO` Struktur verwendet und gültig sind, wenn diese Struktur zurückgegeben wird.

Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
