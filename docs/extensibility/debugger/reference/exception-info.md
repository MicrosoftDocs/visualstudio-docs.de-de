---
title: EXCEPTION_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f6ecbd791297f4c186d22d9ed14c627cf7be43f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941852"
---
# <a name="exception_info"></a>EXCEPTION_INFO
Beschreibt eine Ausnahme oder einen Laufzeitfehler, der von dem Programm ausgelöst wird, das deentschlgt wird.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>Member
`pProgram`\
Das [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das das Programm darstellt, in dem die Ausnahme aufgetreten ist.

`bstrProgramName`\
Der Name des Programms, in dem die Ausnahme aufgetreten ist.

`bstrExceptionName`\
Der Name der Ausnahme.

`dwCode`\
Der Identifikationscode für die Ausnahme oder den Laufzeitfehler.

`dwState`\
Ein Wert aus der [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Enumeration, die den Zustand der Ausnahme definiert.

`guidType`\
Der GUID-Sprachen Bezeichner, entweder `guidLang` oder `guidEng` .

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird als Parameter an die Methoden " [abtexception](../../../extensibility/debugger/reference/idebugengine2-setexception.md) " und " [removesetexception](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) " übergeben. Diese Struktur wird auch an die [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) -Methode übergeben, die ausgefüllt werden soll.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
