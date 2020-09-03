---
title: CANSTOP_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7be361d4468584c109db52f487b3de3c1fdff0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737684"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Wird verwendet, um zu bestimmen, ob ein Programm die Ausführung nach Erreichen eines bestimmten Punkts in der Ausführung abbrechen kann.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Felder
`CANSTOP_ENTRYPOINT`\
Gibt den Einstiegspunkt des angegebenen Programms an.

`CANSTOP_STEPIN`\
Gibt den Schritt in einer Funktion an.

## <a name="remarks"></a>Bemerkungen
Wird als Argument an die [geverrat](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) -Methode übermittelt, um den Sitzungs-Debug-Manager (SDM) zu bestätigen, wenn es in Ordnung ist, nach Erreichen des Einstiegs Punkts des Programms oder nach dem Durchlaufen einer Funktion oder Methode zu beenden.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
