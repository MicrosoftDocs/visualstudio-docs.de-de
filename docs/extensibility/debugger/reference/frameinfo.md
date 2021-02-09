---
title: FrameInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1d52989d5687e922e0cb0ab306efc5321ffecef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904754"
---
# <a name="frameinfo"></a>FRAMEINFO
Beschreibt einen Stapel Rahmen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagFRAMEINFO {
    FRAMEINFO_FLAGS    m_dwValidFields;
    BSTR               m_bstrFuncName;
    BSTR               m_bstrReturnType;
    BSTR               m_bstrArgs;
    BSTR               m_bstrLanguage;
    BSTR               m_bstrModule;
    UINT64             m_addrMin;
    UINT64             m_addrMax;
    IDebugStackFrame2* m_pFrame;
    IDebugModule2*     m_pModule;
    BOOL               m_fHasDebugInfo;
    BOOL               m_fStaleCode;
    BOOL               m_fAnnotatedFrame;
} FRAMEINFO;
```

```csharp
public struct FRAMEINFO {
    public uint              m_dwValidFields;
    public string            m_bstrFuncName;
    public string            m_bstrReturnType;
    public string            m_bstrArgs;
    public string            m_bstrLanguage;
    public string            m_bstrModule;
    public ulong             m_addrMin;
    public ulong             m_addrMax;
    public IDebugStackFrame2 m_pFrame;
    public IDebugModule2     m_pModule;
    public int               m_fHasDebugInfo;
    public int               m_fStaleCode;
    public int               m_fAnnotatedFrame;
} FRAMEINFO;
```

## <a name="members"></a>Member
`m_dwValidFields`\
Eine Kombination von Flags aus der [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Enumeration, die angibt, welche Felder ausgefüllt werden.

`m_bstrFuncName`\
Der dem Stapel Rahmen zugeordnete Funktionsname.

`m_bstrReturnType`\
Der Rückgabetyp, der dem Stapel Rahmen zugeordnet ist.

`m_bstrArgs`\
Die Argumente für die Funktion, die dem Stapel Rahmen zugeordnet ist.

`m_bstrLanguage`\
Die Sprache, in der die Funktion implementiert wird.

`m_bstrModule`\
Der Modulname, der dem Stapel Rahmen zugeordnet ist.

`m_addrMin`\
Die minimale physische Stapel Adresse.

`m_addrMAX`\
Die maximale physische Stapel Adresse.

`m_pFrame`\
Das [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) -Objekt, das diesen Stapel Rahmen darstellt.

`m_pModule`\
Das [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) -Objekt, das das Modul darstellt, das diesen Stapel Rahmen enthält.

`m_fHasDebugInfo`\
Ungleich NULL ( `TRUE` ), wenn im angegebenen Frame Debuginformationen vorhanden sind.

`m_fStaleCode`\
Ungleich NULL ( `TRUE` ), wenn der Stapel Rahmen Code zugeordnet ist, der nicht mehr gültig ist.

`m_fAnnotatedFrame`\
Ungleich NULL ( `TRUE` ), wenn der Stapel Rahmen vom Sitzungs-Debug-Manager (SDM) kommentiert wird.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird an die [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) -Methode, die ausgefüllt werden soll, übermittelt. Diese Struktur ist auch in einer Liste enthalten, die in der [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) -Schnittstelle enthalten ist, die wiederum von einem Rückruf der [enumframeinfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) -Methode zurückgegeben wird.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
