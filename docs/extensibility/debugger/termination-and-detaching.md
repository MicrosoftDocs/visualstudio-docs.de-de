---
title: Beendigung und trennen | Microsoft-Dokumentation
description: Das normale beenden bedeutet, dass ein Programm, das gedebuggt wird, ohne Breakpoints, Ausnahmen, Laufzeitfehler oder Endlosschleifen bis zum Abschluss ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ac3e8517ee99dcd52261eb87b6cee3954793d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895894"
---
# <a name="termination-and-detaching"></a>Beendigung und trennen
Im folgenden Abschnitt wird die normale Beendigung von beschrieben.

## <a name="discussion"></a>Diskussion
 Wenn die [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) -oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) -Schnittstelle fortgesetzt wird und keine Haltepunkte, Ausnahmen, Laufzeitfehler oder Endlosschleifen in der zu debuggenden Anwendung vorhanden sind, wird das Programm, das gedebuggt wird, bis zum Abschluss ausgeführt. Dieser Prozess wird normal beendet.

 Zum Implementieren der normalen Beendigung müssen Sie ein [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) senden. Die normale Beendigung erfordert das Ausführen der [IDebugProgramDestroyEvent2:: getexitcode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) -Methode.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
