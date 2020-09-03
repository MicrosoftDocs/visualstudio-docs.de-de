---
title: Starten des Debuggers | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738458"
---
# <a name="launch-the-debugger"></a>Starten Sie den Debugger.
Zum Starten des Debuggers muss die richtige Sequenz von Methoden und Ereignissen mit ihren richtigen Attributen gesendet werden.

## <a name="sequences-of-methods-and-events"></a>Sequenzen von Methoden und Ereignissen

1. Der sitzungsdebug-Manager (SDM) wird aufgerufen, indem Sie das Menü **Debuggen** auswählen und dann **starten**auswählen. Weitere Informationen finden Sie unter [Starten eines Programms](../../extensibility/debugger/launching-a-program.md).

2. Die SDM Ruft die [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode auf.

3. Basierend auf dem Prozessmodell der Debug-Engine (de) `IDebugProgramNodeAttach2::OnAttach` gibt die Methode eine der folgenden Methoden zurück, die bestimmt, was als nächstes geschieht.

     Wenn `S_FALSE` zurückgibt, muss die Debug-Engine (de) im Prozess der virtuellen Maschine geladen werden.

     - oder -

     Wenn `S_OK` zurückgibt, muss de in-Process des SDM geladen werden. Der SDM führt dann die folgenden Aufgaben aus:

    1. Ruft [getengineinfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) auf, um die Engine-Informationen von de zu erhalten.

    2. Erstellt die de.

    3. Aufrufe [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Der de sendet ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC` .

5. Der de sendet ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC` .

6. Der de sendet ein [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC` .

7. Der de sendet ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC` .

8. Der de sendet ein [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC` .

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debugger-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
- [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)
