---
description: Enthält Informationen zu einem Prozess.
title: PROCESS_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5557e4171bdeb51ae1ac954870a85227a8c4c92
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222093"
---
# <a name="process_info"></a>PROCESS_INFO
Enthält Informationen zu einem Prozess.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Members
 `Fields`\
 Eine Kombination von Flags aus der [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) Enumeration, die angeben, welche Felder ausgefüllt werden.

 `bstrFileName`\
 Der vollständige Pfadname des Prozesses. Äquivalent zum Aufrufen der [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) -Methode mit dem-Parameter `GN_FILENAME` .

 `bstrBaseName`\
 Der Dateiname und die Erweiterung des Prozesses. Äquivalent zum Aufrufen der- `IDebugProcess2::Getname` Methode mit dem-Parameter `GN_BASENAME` .

 `bstrTitle`\
 Der Titel des Prozesses, wenn ein solcher vorhanden ist. Äquivalent zum Aufrufen der- `IDebugProcess2::Getname` Methode mit dem-Parameter `GN_TITLE` .

 `ProcessId`\
 Die [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) -Struktur, die den Prozess identifiziert. Äquivalent zum Aufrufen der [getphysicalprocessid-](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) Methode.

 `dwSessionId`\
 Der Bezeichner der Debugsitzung, in der dieser Prozess ausgeführt wird.

 `bstrAttachedSessionName`\
 Der Name der angefügten Sitzung. Äquivalent zum Aufrufen der [getattachedsessionname](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) -Methode.

 `CreationTime`\
 Der Zeitpunkt, zu dem der Prozess erstellt wurde.

 `Flags`\
 Eine Kombination von Flags aus der [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) Enumeration, die Eigenschaften des Prozesses angeben.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird an die [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) -Methode, in der Sie ausgefüllt ist, übermittelt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
