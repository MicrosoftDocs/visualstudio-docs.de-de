---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54773ee6f770855122992f49bebad44fa1f6129a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870297"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Gibt den Gültigkeitsbereich des disassemblystreams an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Felder
`DSS_HUGE`\
Gibt an, dass die Disassemblierung des Code Kontexts eine größere Ausgabe generieren würde, als ein Client in der Regel in einem einzigen-Befehl abrufen soll.

`DSS_FUNCTION`\
Gibt an, dass die im Code Kontext enthaltene Funktion disassembliert werden soll. Gibt an, dass der disassemblystream eine Funktion darstellt, wenn Sie von der [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) -Methode zurückgegeben wird

`DSS_MODULE`\
Gibt bei Rückgabe durch die-Methode an, `IDebugDisassemblyStream2::GetScope` dass der disassemblystream ein Modul darstellt.

`DSS_ALL`\
Gibt die Disassembly für den gesamten Adressraum an.

## <a name="remarks"></a>Bemerkungen
Wird als Argument an die [getdisassemblystream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) -Methode übergeben und von der [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) -Methode zurückgegeben.

Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
