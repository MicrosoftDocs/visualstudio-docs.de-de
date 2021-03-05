---
description: Gibt die einem Programmanbieter zugeordneten Eigenschaften an.
title: PROVIDER_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: daf2ca4aa53c2800685f8fdbde26c402f217b811
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225304"
---
# <a name="provider_fields"></a>PROVIDER_FIELDS
Gibt die einem Programmanbieter zugeordneten Eigenschaften an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
typedef DWORD PROVIDER_FIELDS;
```

```csharp
public enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
```

## <a name="fields"></a>Felder
 `PFIELD_PROGRAM_NODES`\
 Das `ProgramNodes` Feld ist gültig.

 `PFIELD_IS_DEBUGGER_PRESENT`\
 Das `fIsDebuggerPresent` Feld ist gültig.

## <a name="remarks"></a>Bemerkungen
 Diese Werte werden im- `Fields` Member der [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Struktur zurückgegeben, um anzugeben, welche Felder der Struktur explizit ausgefüllt wurden.

 Diese Werte können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
