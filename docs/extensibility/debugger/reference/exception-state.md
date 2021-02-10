---
title: EXCEPTION_STATE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f804f9a47314bfd239e6904286122776977e92e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936924"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Gibt den Ausnahmezustand an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Felder
`EXCEPTION_NONE`\
Nehmen Sie keine Beendigung an der Ausnahme vor.

`EXCEPTION_STOP_FIRST_CHANCE`\
Beendigung beim ersten Auslösen der Ausnahme. Wenn ein Ausnahme Ereignis beschrieben wird, gibt dieses Flag an, dass es sich bei dem Ausnahme Ereignis um ein Ausnahme Ereignis der ersten Chance handelt.

`EXCEPTION_STOP_SECOND_CHANCE`\
Beim zweiten Auslösen einer Ausnahme angehalten. Gibt beim Beschreiben eines Ausnahme Ereignisses an, dass es sich bei dem Ausnahme Ereignis um ein Ausnahme Ereignis der zweiten Chance handelt.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Wird beim ersten Auslösen einer benutzermodusausnahme beendet. Gibt beim Beschreiben eines Ausnahme Ereignisses an, dass es sich bei dem Ausnahme Ereignis um ein Benutzer Ausnahme Ereignis der ersten Chance handelt.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Beenden, wenn eine benutzermodusausnahme nicht abgefangen wird. Gibt beim Beschreiben eines Ausnahme Ereignisses an, dass es sich bei dem Ausnahme Ereignis um ein nicht abgefangener Ausnahme Ereignis im Benutzermodus handelt.

`EXCEPTION_STOP_ALL`\
Wird bei jeder Ausnahme beendet. Wird nicht verwendet, wenn ein Ausnahme Ereignis beschrieben wird.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Gibt beim Beschreiben eines Ausnahme Ereignisses an, dass die Ausnahme nicht fortgesetzt werden kann.

`EXCEPTION_CODE_SUPPORTED`\
Gibt an, dass die Ausnahme Code unterstützt. Wird verwendet, um eine Ausnahme anzuzeigen.

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Gibt an, dass der Ausnahme Code in hexadezimal angezeigt werden soll. Wird verwendet, um eine Ausnahme anzuzeigen.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Gibt an, dass der Ausnahme Code JustMyCode unterstützt. Wird verwendet, um eine Ausnahme anzuzeigen.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Gibt an, dass der Debugger für verwalteten Code Ausnahmen behandeln soll. Wenn nicht festgelegt, verarbeitet der Standard Debugger die Ausnahmen. Diese wird an die [setallexceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) -Methode und nicht in der [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur verwendet.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
veraltet, nicht verwenden.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
veraltet, nicht verwenden.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
veraltet, nicht verwenden.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
veraltet, nicht verwenden.

## <a name="remarks"></a>Bemerkungen
Wird als `dwState` Member der [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur verwendet, um den Zustand der Ausnahme anzugeben, und was damit erreicht werden kann.

Diese Werte werden auch an die [setallexceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) -Methode übermittelt, um den Status aller Ausnahmen festzulegen.

Diese Flags können mit einem bitweisen OR kombiniert werden.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
