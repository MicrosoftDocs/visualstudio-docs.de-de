---
description: Listet die gültigen Werte auf, die die Informationen angeben, die über eine breakpointanforderung abgerufen werden sollen.
title: BPREQI_FIELDS90 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5405f728cf979738de5a830421c4306c5e398bb2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151083"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Listet die gültigen Werte auf, die die Informationen angeben, die über eine breakpointanforderung abgerufen werden sollen. Diese Enumeration erweitert die [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Enumeration.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Felder
`BPREQI90_BPLOCATION`\
Initialisieren Sie das `bpLocation` Feld (Haltepunkt Position) der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) -oder [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur, oder verwenden Sie es.

`BPREQI90_LANGUAGE`\
Initialisieren oder verwenden Sie das- `guidLanguage` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.

`BPREQI90_PROGRAM`\
Initialisieren oder verwenden Sie das- `pProgram` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.

`BPREQI90_PROGRAMNAME`\
Initialisieren oder verwenden Sie das- `bstrProgramName` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.

`BPREQI90_THREAD`\
Initialisieren oder verwenden Sie das- `pThread` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.

`BPREQI90_THREADNAME`\
Initialisieren oder verwenden Sie das- `bstrThreadName` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.

`BPREQI90_PASSCOUNT`\
Initialisieren oder verwenden Sie das- `bpPassCount` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.

`BPREQI90_CONDITION`\
Initialisieren oder verwenden Sie das `bpCondition` Feld (breakpointbedingung) der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.

`BPREQI90_FLAGS`\
Initialisieren oder verwenden Sie das- `dwFlags` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.

`BPREQI90_ALLOLDFIELDS`\
Initialisieren oder verwenden Sie alle Felder für den der- `BP_REQUEST_INFO` Struktur.

`BPREQI90_VENDOR`\
Initialisieren Sie das Feld der-Struktur, oder verwenden Sie es `guidVendor` `BP_REQUEST_INFO2` .

`BPREQI90_CONSTRAINT`\
Initialisieren Sie das Feld der-Struktur, oder verwenden Sie es `bstrConstraint` `BP_REQUEST_INFO2` .

`BPREQI90_TRACEPOINT`\
Initialisieren Sie das Feld der-Struktur, oder verwenden Sie es `bstrTracepoint` `BP_REQUEST_INFO2` .

`BPREQI90_MACROTRACEPOINT`\
Initialisieren Sie das Feld der-Struktur, oder verwenden Sie es `bstrMacroTracepoint` `BP_REQUEST_INFO2` . BPREQI_ALLFIELDS enthält dieses Feld nicht.

`BPREQI90_ALLFIELDS`\
Gibt alle Felder für die `BP_REQUEST_INFO2` Struktur an.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: Msdbg90. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
