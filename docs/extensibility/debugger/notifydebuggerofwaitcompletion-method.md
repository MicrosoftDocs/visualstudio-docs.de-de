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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b62b613950f9fd6c8ce18969c126a6e74a154b58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851295"
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
