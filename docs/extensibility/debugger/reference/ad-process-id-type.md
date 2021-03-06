---
description: Gibt an, wie eine Prozess-ID in der AD_PROCESS_ID Struktur interpretiert werden soll.
title: AD_PROCESS_ID_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f56ca1db0462a85bd68b193147f5dd3a46c6bee9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164343"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Gibt an, wie eine Prozess-ID in der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur interpretiert werden soll.

## <a name="syntax"></a>Syntax

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Felder
`AD_PROCESS_ID_SYSTEM`\
Die Prozess-ID ist ein System Bezeichner. Verwenden Sie das- `ProcessId.dwProcessId` Feld der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur.

`AD_PROCESS_ID_GUID`\
Die Prozess-ID ist eine GUID. Verwenden Sie das- `ProcessId.guidProcessId` Feld der- `AD_PROCESS_ID` Struktur.

## <a name="remarks"></a>Bemerkungen
Wird für den `ProcessIdType` Member der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur verwendet, um den Typ der Prozess-ID zu identifizieren, der in der Struktur enthalten ist. Bestimmt, wie die `ProcessId` Union in der-Struktur interpretiert wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
