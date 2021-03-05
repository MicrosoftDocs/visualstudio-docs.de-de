---
description: Beschreibt den Computer, auf dem der Debugger ausgeführt wird.
title: COMPUTER_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81dee41b0ffc45ae6e0403e732c27d030026fb07
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170906"
---
# <a name="computer_info"></a>COMPUTER_INFO
Beschreibt den Computer, auf dem der Debugger ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="members"></a>Members
`wProcessorArchitecture`\
Gibt die Architektur des Mikroprozessors an.

`wSuiteMask`\
Gibt die Sammlungs Maske an.

`dwOperatingSystemVersion`\
Die Versionsnummer des Betriebssystems.

## <a name="remarks"></a>Bemerkungen
Diese Struktur wird von der [getcomputerinfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) -Methode zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Getcomputerinfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
