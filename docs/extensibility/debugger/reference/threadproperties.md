---
title: Thread Properties | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2eb7abf897cf4891f08228dd5f0c918f580a1ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850660"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Beschreibt die Eigenschaften eines Threads.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>Member
 `dwFields`\
 Eine Kombination von Flags aus der [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Enumeration, die beschreibt, welche Felder in dieser Struktur gültig sind.

 `dwThreadId`\
 Die Thread-ID.

 `dwSuspendCount`\
 Die Thread Anzahl für den Thread.

 `dwThreadState`\
 Ein Wert aus der [ThreadState](../../../extensibility/debugger/reference/threadstate.md) -Enumeration, der den Status des Betriebs Threads angibt.

 `bstrPriority`\
 Eine Zeichenfolge, die die Thread Priorität angibt. Beispiel: "oberhalb normal", "Normal" oder "Zeit kritisch".

 `bstName`\
 Der Thread Name.

 `bstrLocation`\
 Der Thread Speicherort (in der Regel der oberste Stapel Rahmen), der in der Regel als Name der Methode ausgedrückt wird, in der die Ausführung zurzeit angehalten wird.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird durch einen Aufrufen der [getthreadproperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) -Methode ausgefüllt. Die Informationen, die zurückgegeben werden, werden in der Regel zum Auffüllen des **Thread** Fensters verwendet.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [ThreadState](../../../extensibility/debugger/reference/threadstate.md)
