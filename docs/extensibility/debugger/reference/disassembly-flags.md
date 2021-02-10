---
title: DISASSEMBLY_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fe1515616d6781613961fa11d87005a479c70fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939018"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Gibt die Flags für die Disassembly an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Felder
`DF_DOCUMENTCHANGE`\
Gibt an, dass sich diese Anweisung in einem anderen Dokument als die vorherige Anweisung befindet.

`DF_DISABLED`\
Gibt an, dass diese Anweisung nicht ausgeführt wird.

`DF_INSTRUCTION_ACTIVE`\
Gibt an, dass es sich bei dieser Anweisung um eine der nächsten auszuführenden Anweisungen handelt (möglicherweise gibt es mehr als eine).

`DF_DATA`\
Gibt an, dass diese Anweisung wirklich Daten (nicht Code) ist.

`DF_HASSOURCE`\
Gibt an, dass diese Anweisung über eine Quelle verfügt. Einige Anweisungen, wie z. b. Profilerstellung oder Garbage Collection Code, verfügen nicht über die entsprechende Quelle.

`DF_DOCUMENT_CHECKSUM`\
Gibt an, dass das `bstrDocumentUrl` Feld Prüfsummen Daten nach der Dokument-URL enthält. Weitere Informationen zur Speicherung der Prüfsummen Daten finden Sie im Abschnitt "Hinweise" für die [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) -Struktur.

## <a name="remarks"></a>Bemerkungen
Wird als `dwFlags` Member der [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) -Struktur verwendet.

Diese Flags können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
