---
description: Gibt an, wie viel von einem Programmzustand (z. b. das Ausführen von Threads, Stapel Rahmen und aktuelle Anweisungs Adresse) zum Absichern angezeigt werden soll.
title: Dumptype | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cef9f90c1f08dac742a6f01a4dd48f6bff76848b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150977"
---
# <a name="dumptype"></a>DUMPTYPE
Gibt an, wie viel von einem Programmzustand (z. b. das Ausführen von Threads, Stapel Rahmen und aktuelle Anweisungs Adresse) zum Absichern angezeigt werden soll.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="fields"></a>Felder
`DUMP_MINIDUMP`\
Gibt ein kleines, kompaktes Abbild an.

`DUMP_FULLDUMP`\
Gibt ein großes, Abbild Abbild an.

## <a name="remarks"></a>Bemerkungen
Wird als Argument an die " [Write-Dump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) "-Methode übermittelt.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
