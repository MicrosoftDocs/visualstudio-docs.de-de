---
title: Beenden eines Programms | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie die IDE mithilfe der Debug-Engine ein einzelnes Programm mit einem einzigen Thread beendet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0f44cb287945576d361d0318eaeafa42de99871d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895907"
---
# <a name="terminating-a-program"></a>Beenden eines Programms
Im folgenden Abschnitt wird die Beendigung eines einzelnen Programms mit einem Thread beschrieben.

## <a name="termination-process"></a>Beendigungs Prozess

1. Der de sendet eine [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) mit einem gültigen [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. Der de sendet eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) mit einem gültigen [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   Die IDE wechselt in den Entwurfs Modus. Mit der Debug-Engine oder der Laufzeitumgebung wird [IDebugPortNotify2:: removeprogramnode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) aufgerufen, um das Programm aus dem Port zu entfernen.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debugger-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
