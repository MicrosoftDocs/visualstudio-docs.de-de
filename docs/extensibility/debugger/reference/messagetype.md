---
title: MessageType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9735c394e0b88dbe7ea3a5113026d4012839b8fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961988"
---
# <a name="messagetype"></a>MESSAGETYPE
Gibt den Nachrichtentyp und den Grund an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Felder
 `MT_OUTPUTSTRING`\
 Gibt an, dass die Nachricht an das Ausgabefenster gesendet werden soll. Dies schließt sich gegenseitig aus `MT_MESSAGEBOX` .

 `MT_MESSAGEBOX`\
 Gibt an, dass die Meldung in einem Meldungs Feld angezeigt werden soll. Dies schließt sich gegenseitig aus `MT_OUTPUTSTRING` .

 `MT_TYPE_MASK`\
 Ein Maskenwert, um das Ziel für die Nachricht zu isolieren.

 `MT_REASON_EXCEPTION`\
 Gibt an, dass ein Meldungs Feld als Ergebnis einer Ausnahme angezeigt wird. Dies schließt sich gegenseitig aus `MT_REASON_TRACEPOINT` .

 `MT_REASON_TRACEPOINT`\
 Gibt an, dass ein Meldungs Feld durch das Erreichen eines Ablauf Verfolgungs Punkts angezeigt wird. Dies schließt sich gegenseitig aus `MT_REASON_EXCEPTION` .

 `MT_REASON_MASK`\
 Ein Maskenwert, um den Grund für die angezeigte Meldung zu isolieren.

## <a name="remarks"></a>Bemerkungen
 Diese Werte werden von der [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) -Methode und der [getErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) -Methode zurückgegeben.

 Einer der Grundwerte kann mit einem der Ausgabeziel Werte mithilfe eines bitweisen kombiniert werden `OR` .

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
