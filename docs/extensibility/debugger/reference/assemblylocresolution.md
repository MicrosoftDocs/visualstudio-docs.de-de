---
title: Assemblylokresolution | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e2611828f1e9bb2aec740e392db18ce60839d19a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952394"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
Gibt an, wo sich eine Assembly befindet.

## <a name="syntax"></a>Syntax

```cpp
enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
typedef DWORD ASSEMBLYLOCRESOLUTION;
```

```csharp
public enum enum_ASSEMBLYLOCRESOLUTION {
    ALR_NAME      = 0x0,
    ALR_USERDIR   = 0x1,
    ALR_SHAREDDIR = 0x2,
    ALR_REMOTEDIR = 0x4,
};
```

## <a name="fields"></a>Felder
`ALR_NAME`\
Die Assembly befindet sich im aktuellen Namespace.

`ALR_USERDIR`\
Die Assembly befindet sich in einem Benutzerverzeichnis.

`ALR_SHAREDDIR`\
Die Assembly befindet sich im freigegebenen Verzeichnis.

`ALR_REMOTEDIR`\
Die Assembly befindet sich in einem Remote Verzeichnis.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden von der [resolveassemblyref](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) -Methode und der [getmanagedviewerkreationdata](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md) -Methode zurückgegeben.

Diese Werte können mit dem-Vorgang kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)
- [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)
