---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft-Dokumentation
description: Die INTERCEPT_EXCEPTION_ACTION Enumeration gibt an, welche Aktion ausgeführt werden soll, wenn Ausnahmen beim Debuggen von Visual Studio abgefangen werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e80ed1b17f98326701b0ca0aacb8e114c9b49db4
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606442"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
Gibt an, welche Aktionen ausgeführt werden sollen, wenn Ausnahmen abgefangen werden.

## <a name="syntax"></a>Syntax

```cpp
enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
typedef DWORD INTERCEPT_EXCEPTION_ACTION;
```

```csharp
public enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
```

## <a name="parameters"></a>Parameter

`IEA_INTERCEPT`\
Ermöglicht das Abfangen der aktuellen Ausnahme. Dies ist der einzige Wert, der derzeit unterstützt wird und angegeben werden muss.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden an die [interceptaccesstexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) -Methode übergeben.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
