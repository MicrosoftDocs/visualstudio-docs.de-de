---
description: Gibt an, welche Art von Informationen für einen bestimmten Computer abgerufen werden sollen.
title: MACHINE_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb07f679027c37ebc74343ba17051a7e7980c1c7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222561"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Gibt an, welche Art von Informationen für einen bestimmten Computer abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Felder
 `MCIF_NAME`\
 Initialisieren/verwenden Sie das- `bstrName` Feld in der-Struktur.

 `MCIF_FLAGS`\
 Initialisieren/verwenden Sie das- `Flags` Feld in der-Struktur.

 `MIF_ALL`\
 Initialisieren/verwenden Sie alle Felder in der Struktur.

## <a name="remarks"></a>Bemerkungen
 Diese Werte werden an die [getmachineingefo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) -Methode übermittelt, um anzugeben, welche Member der [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Struktur initialisiert werden sollen.

 Wird auch im- `Fields` Member der `MACHINE_INFO` -Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.

 Diese Flags können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
