---
description: Gibt die Flags für die Debug-Modul Informationen an.
title: MODULE_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc27420fc598d174b8e71c5ed3edd879a4a30d9d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222366"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Gibt die Flags für die Debug-Modul Informationen an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Felder
 `MIF_NONE`\
 Initialisieren/verwenden Sie keines der Felder in der Struktur.

 `MIF_NAME`\
 Initialisieren Sie das `m_bstrName` Feld in der [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur, und verwenden Sie es.

 `MIF_URL`\
 Initialisieren/verwenden Sie das- `m_bstrUrl` Feld in der- `MODULE_INFO` Struktur.

 `MIF_VERSION`\
 Initialisieren/verwenden Sie das- `m_bstrVersion` Feld in der- `MODULE_INFO` Struktur.

 `MIF_DEBUGMESSAGE`\
 Initialisieren/verwenden Sie das- `m_bstrDebugMessage` Feld in der- `MODULE_INFO` Struktur.

 `MIF_LOADADDRESS`\
 Initialisieren/verwenden Sie das- `m_addrLoadAddress` Feld in der- `MODULE_INFO` Struktur.

 `MIF_PREFFEREDADDRESS`\
 Initialisieren/verwenden Sie das- `m_addrPreferredLoadAddress` Feld in der- `MODULE_INFO` Struktur.

 `MIF_SIZE`\
 Initialisieren/verwenden Sie das- `m_dwSize` Feld in der- `MODULE_INFO` Struktur.

 `MIF_LOADORDER`\
 Initialisieren/verwenden Sie das- `m_dwLoadOrder` Feld in der- `MODULE_INFO` Struktur.

 `MIF_TIMESTAMP`\
 Initialisieren/verwenden Sie das- `m_TimeStamp` Feld in der- `MODULE_INFO` Struktur.

 `MIF_URLSYMBOLLOCATION`\
 Initialisieren/verwenden Sie das- `m_bstrUrlSymbolLocation` Feld in der- `MODULE_INFO` Struktur.

 `MIF_FLAGS`\
 Initialisieren/verwenden Sie das- `m_dwModuleFlags` Feld in der- `MODULE_INFO` Struktur.

 `MIF_ALLFIELDS`\
 Initialisieren/verwenden Sie alle Felder in der `MODULE_INFO` Struktur.

## <a name="remarks"></a>Bemerkungen
 Diese Werte werden als Argument an die [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) -Methode übermittelt, um anzugeben, welche Felder der [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur initialisiert werden sollen.

 Diese Werte werden auch in der- `MODULE_INFO` Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.

 Diese Flags können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
