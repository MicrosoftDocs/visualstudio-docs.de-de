---
title: Notifydebuggerofwaitcompletion-Methode | Microsoft-Dokumentation
description: Erfahren Sie mehr über die notifydebuggerofwaitcompletion-Methode, bei der es sich um einen Platzhalter handelt, der vom Debugger als Haltepunkt Ziel verwendet wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35571b28287ecdea48a2ff089cb25cf3ed742d60
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606631"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Notifydebuggerofwaitcompletion-Methode
Die Platzhalter Methode, die vom Debugger als Haltepunkt Ziel verwendet wird. Diese Methode darf nicht Inline oder optimiert sein.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Syntax

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Bemerkungen
 Alle joinvorgänge mit einer Aufgabe sollten diese Methode abrufen, wenn Ihr Debugger-Benachrichtigungs Bit festgelegt ist.

## <a name="requirements"></a>Anforderungen

## <a name="see-also"></a>Weitere Informationen
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)
