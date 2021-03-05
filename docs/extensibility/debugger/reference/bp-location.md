---
description: Gibt den Strukturtyp an, der verwendet wird, um den Speicherort des Breakpoints zu beschreiben.
title: BP_LOCATION | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 472dc7b2e642608691ea2adb2ad1a7dce170729f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144181"
---
# <a name="bp_location"></a>BP_LOCATION
Gibt den Strukturtyp an, der verwendet wird, um den Speicherort des Breakpoints zu beschreiben.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Members
`bpLocationType`\
Ein Wert aus der [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) Enumeration, mit der die `bpLocation` Union oder die Member interpretiert werden `unionmemberX` .

`bpLocation`.`bplocCodeFileLine`\
[Nur C++] Enthält die [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_FILE_LINE` .

`bpLocation.bplocCodeFuncOffset`\
[Nur C++] Enthält die [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET` .

`bpLocation.bplocCodeContext`\
[Nur C++] Enthält die [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_CONTEXT` .

`bpLocation.bplocCodeString`\
[Nur C++] Enthält die [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_STRING` .

`bpLocation.bplocCodeAddress`\
[Nur C++] Enthält die [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Struktur, wenn `bpLocationType`  =  `BPLT_CODE_ADDRESS` .

`bpLocation.bplocDataString`\
[Nur C++] Enthält die [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Struktur, wenn `bpLocationType`  =  `BPLT_DATA_STRING` .

`bpLocation.bplocResolution`\
[Nur C++] Enthält die [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Struktur, wenn `bpLocationType`  =  `BPLT_RESOLUTION` .

`unionmember1`\
[Nur c#] Weitere Informationen finden Sie unter Hinweise zur Interpretation von.

`unionmember2`\
[Nur c#] Weitere Informationen finden Sie unter Hinweise zur Interpretation von.

`unionmember3`\
[Nur c#] Weitere Informationen finden Sie unter Hinweise zur Interpretation von.

`unionmember4`\
[Nur c#] Weitere Informationen finden Sie unter Hinweise zur Interpretation von.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Member der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) -und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) -Strukturen.

 [Nur c#] Die Elemente `unionmemberX` werden entsprechend der folgenden Tabelle interpretiert. Suchen Sie in der linken Spalte nach dem `bpLocationType` Wert, und überprüfen Sie dann die anderen Spalten, um zu bestimmen, was die einzelnen Elemente `unionmemberX` darstellen und wie Sie das Mars Hallen `unionmemberX` Ein Beispiel für eine Möglichkeit, einen Teil dieser Struktur in c# zu interpretieren, finden Sie im Beispiel.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (ein Kontext)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (ein Kontext)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (ein Kontext)|`string` (bedingter Ausdruck)|-|-|
|`BPLT_CODE_ADDRESS`|`string` (ein Kontext)|`string` (Modul-URL)|`string` (Funktionsname)|`string` Adresse|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (ein Kontext)|`string` (Daten Ausdruck)|`uint` (Anzahl von Elementen)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Beispiel
In diesem Beispiel wird gezeigt, wie die- `BP_LOCATION` Struktur in c# für den-Typ interpretiert wird `BPLT_DATA_STRING` . Dieser spezielle Typ zeigt, wie alle vier Member `unionmemberX` in allen möglichen Formaten (Objekt, Zeichenfolge und Zahl) interpretiert werden.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
            }
        }
    }
}
```

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
