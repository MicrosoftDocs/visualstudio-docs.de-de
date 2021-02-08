---
title: Anfügen und trennen an ein Programm | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die richtige Sequenz von Methoden und Ereignissen mit den richtigen Attributen zum Anfügen eines Debuggers senden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d41f9e3f88f28dbbb83e9c7e00fe8b8afd434c26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837748"
---
# <a name="attaching-and-detaching-to-a-program"></a>Anfügen und trennen an ein Programm
Das Anfügen des Debuggers erfordert, dass die richtige Sequenz von Methoden und Ereignissen mit den richtigen Attributen gesendet wird.

## <a name="sequence-of-methods-and-events"></a>Abfolge von Methoden und Ereignissen

1. Der Sitzungs-Debug-Manager (SDM) Ruft die [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode auf.

    Basierend auf dem Prozessmodell der Debug-Engine (de) `IDebugProgramNodeAttach2::OnAttach` gibt die Methode eine der folgenden Methoden zurück, die bestimmt, was als nächstes geschieht.

    Wenn `S_FALSE` zurückgegeben wird, wurde die Debug-Engine erfolgreich an das Programm angefügt. Andernfalls wird die [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode aufgerufen, um den Anfüge Vorgang abzuschließen.

    Wenn `S_OK` zurückgegeben wird, muss de in demselben Prozess wie das SDM geladen werden. Der SDM führt die folgenden Aufgaben aus:

   1. Ruft [getengineinfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) auf, um die Engine-Informationen von de zu erhalten.

   2. Erstellt die de.

   3. Aufrufe [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. Der de sendet ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC` .

3. Der de sendet ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC` .

4. Der de sendet ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC_STOP` .

   Das Trennen von einem Programm ist ein einfacher, zweistufiger Prozess:

5. Die SDM-Aufrufe [trennen](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. Der de sendet eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debugger-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
