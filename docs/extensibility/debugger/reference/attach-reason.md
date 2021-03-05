---
description: Gibt den Grund für das Anfügen der Debug-Engine (de) an einen Programmknoten an.
title: ATTACH_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6fa83fb537f05a2c073e3693dab964fa58af464
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144610"
---
# <a name="attach_reason"></a>ATTACH_REASON
Gibt den Grund für das Anfügen der Debug-Engine (de) an einen Programmknoten an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="fields"></a>Felder
`ATTACH_REASON_AUTO`\
Anfügen, da sich der Prozess derzeit im Debugmodus befindet.

`ATTACH_REASON_LAUNCH`\
Anfügen, da der Prozess gestartet wurde.

`ATTACH_REASON_USER`\
Anfügen aufgrund einer Benutzer Anforderung.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden als Parameter für die [Anfüge](../../../extensibility/debugger/reference/idebugengine2-attach.md) -und [Anfüge](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) Methoden verwendet.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
