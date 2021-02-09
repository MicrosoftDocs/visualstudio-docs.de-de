---
title: BP_REQUEST_INFO2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ad3c5492143f97559770c57d528971ac84f22fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903275"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
Enthält die Informationen, die zum Implementieren eines Breakpoints erforderlich sind, einschließlich der Hersteller-GUID, der Einschränkung und des Ablauf Verfolgungs Punkts.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_REQUEST_INFO2 {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
    GUID            guidVendor;
    BSTR            bstrConstraint;
    BSTR            bstrTracepoint;
} BP_REQUEST_INFO2;
```

```csharp
public struct BP_REQUEST_INFO2 {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
    public Guid           guidVendor;
    public string         bstrConstraint;
    public string         bstrTracepoint;
};
```

## <a name="members"></a>Member
`dwFields`\
Eine Kombination von Flags aus der [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Enumeration, die angibt, welche Felder ausgefüllt werden.

`guidLanguage`\
Die Sprach-GUID.

`bpLocation`\
Die [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) -Struktur, die den Typ der Haltepunkt Position angibt.

`pProgram`\
Das [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das die Anwendung darstellt, in der der Breakpoint auftritt.

`bstrProgramName`\
Der Name der Anwendung, in der der Breakpoint auftritt.

`pThread`\
Das [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, in dem der Breakpoint auftritt.

`bstrThreadName`\
Der Name des Threads, in dem der Breakpoint auftritt.

`bpCondition`\
Die [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) -Struktur, die die Bedingungen beschreibt, unter denen der Breakpoint ausgelöst wird.

`bpPassCount`\
Die [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) -Struktur, die die Informationen zur Durchlauf Anzahl des Breakpoints enthält.

`dwFlags`\
Eine Kombination von Flags aus der [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Enumeration, die die Flags für den angeforderten Haltepunkt angibt.

`guidVendor`\
GUID des Anbieters. Kann ein NULL-Wert sein.

`bstrConstraint`\
Der Name der breakpointeinschränkung. Kann ein NULL-Wert sein.

`bstrTracepoint`\
Der Name des Ablauf Verfolgungs Punkts. Kann ein NULL-Wert sein.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von der [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
