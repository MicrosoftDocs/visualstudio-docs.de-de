---
title: SEEK_START | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca1c38027123ca5147a6a7ab1fa6a3f92966409a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713592"
---
# <a name="seek_start"></a>SEEK_START
Gibt die Position an, ab der in einem disassemblystream gesucht werden soll.

## <a name="syntax"></a>Syntax

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Felder
 `SEEK_START_BEGIN`\
 Beginnt die Suche am Anfang des aktuellen Dokuments.

 `SEEK_START_END`\
 Beginnt die Suche am Ende des aktuellen Dokuments.

 `SEEK_START_CURRENT`\
 Startet die Suche an der aktuellen Position des aktuellen Dokuments.

 `SEEK_START_CODECONTEXT`\
 Startet die Suche im angegebenen Code Kontext des aktuellen Dokuments.

 `SEEK_START_CODELOCID`\
 Beginnt mit der Suche nach dem angegebenen Code Speicherort Bezeichner. Bezeichner für den Code Speicherort werden abgerufen, indem [getcurrentlocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)aufgerufen wird.

## <a name="remarks"></a>Bemerkungen
 Wird als Argument an die [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) -Methode übermittelt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
