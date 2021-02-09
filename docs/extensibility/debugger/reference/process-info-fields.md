---
title: PROCESS_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 451a6ea5334006bb23e8961595f4de85c985b8ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895946"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Gibt an, welche Art von Informationen für einen Prozess abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Felder
 `PIF_FILE_NAME`\
 Initialisieren Sie das- `bstrFileName` Feld der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur, und verwenden Sie es.

 `PIF_BASE_NAME`\
 Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `bstrBaseName` `PROCESS_INFO` .

 `PIF_TITLE`\
 Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `bstrTitle` `PROCESS_INFO` .

 `PIF_PROCESS_ID`\
 Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `ProcessId` `PROCESS_INFO` .

 `PIF_SESSION_ID`\
 Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `dwSessionId` `PROCESS_INFO` .

 `PIF_ATTACHED_SESSION_NAME`\
 Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `bstrAttachedSessionName` `PROCESS_INFO` .

 `PIF_CREATION_TIME`\
 Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `CreationTime` `PROCESS_INFO` .

 `PIF_FLAGS`\
 Initialisieren Sie das-Feld der-Struktur, und verwenden Sie es `Flags` `PROCESS_INFO` .

 `PIF_ALL`\
 Füllt alle Felder aus.

## <a name="remarks"></a>Bemerkungen
 Wird an die [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) -Methode übermittelt, um anzugeben, welche Felder der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur initialisiert werden sollen.

 Wird auch im `Fields` Feld der `PROCESS_INFO` -Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.

 Diese Flags können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
