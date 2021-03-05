---
description: Gibt an, welche Informationen über einen Thread abgerufen werden sollen.
title: THREADPROPERTY_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 698c803304cf5efd3375b6d49e4dedbc4622f4c1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221833"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Gibt an, welche Informationen über einen Thread abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Felder
 `TPF_ID`\
 Initialisieren/verwenden Sie das- `dwThreadId` Feld der [Thread Properties](../../../extensibility/debugger/reference/threadproperties.md) -Struktur.

 `TPF_SUSPENDCOUNT`\
 Initialisieren/verwenden Sie das- `dwSuspendCount` Feld der `THREADPROPERTIE` S-Struktur.

 `TPF_STATE`\
 Initialisieren/verwenden Sie das- `dwThreadState` Feld der `THREADPROPERTIE` S-Struktur.

 `TPF_PRIORITY`\
 Initialisieren/verwenden Sie das- `bstrPriority` Feld der `THREADPROPERTIE` S-Struktur.

 `TPF_NAME`\
 Initialisieren/verwenden Sie das- `bstrName` Feld der `THREADPROPERTIE` S-Struktur.

 `TPF_LOCATION`\
 Initialisieren/verwenden Sie das- `bstrLocation` Feld der `THREADPROPERTIE` S-Struktur.

 `TPF_ALLFIELDS`\
 Gibt alle Felder an.

## <a name="remarks"></a>Bemerkungen
 Diese Werte werden als Argument an die [getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) -Methode übermittelt, um anzugeben, welche Felder der [Thread Properties](../../../extensibility/debugger/reference/threadproperties.md) -Struktur initialisiert werden sollen.

 Diese Werte werden auch im- `dwFields` Member der `THREADPROPERTIES` -Struktur verwendet, um anzugeben, welche Felder verwendet und gültig sind.

 Diese Flags können mit einem bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
