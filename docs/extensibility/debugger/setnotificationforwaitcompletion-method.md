---
title: Setnotificationforwaitcompletion-Methode | Microsoft-Dokumentation
description: Erfahren Sie, wie der Debugger ein State-Bit verwendet, um den asynchronen Methoden Text für Promise-Aufgaben zu unterstützen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80904e95c1561dd20ed2a6cc9ad561e6c18ee93a
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845218"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion-Methode
Legt das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustands Bit fest oder löscht dieses.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Syntax

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parameter
 `enabled`

 `true` So legen Sie das Bit fest `false` , wenn das Bit nicht festgelegt werden soll.

## <a name="exceptions"></a>Ausnahmen

## <a name="remarks"></a>Bemerkungen
 Der Debugger legt dieses Bit fest, um den asynchronen Methoden Text auszulagern. Wenn `enabled` ist `true` , muss diese Methode nur für eine Aufgabe aufgerufen werden, die noch nicht abgeschlossen wurde. Wenn `enabled` `false` den Wert hat, kann diese Methode für abgeschlossene Aufgaben aufgerufen werden. In beiden Ereignissen sollte Sie nur für Aufgaben im Promise-Stil verwendet werden.

## <a name="requirements"></a>Requirements (Anforderungen)

## <a name="see-also"></a>Weitere Informationen
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)
