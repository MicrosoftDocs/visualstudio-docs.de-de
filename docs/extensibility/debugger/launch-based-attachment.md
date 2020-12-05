---
title: Start basierte Anlage | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Start basierte Anlage zu einem Programm, das automatisch erfolgt und einem Pfad wie dem der manuellen Anlage folgt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e041c692a833b7d0a1891c078388a3f5b2d11e4
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606670"
---
# <a name="launch-based-attachment"></a>Start basierte Anlage
Die Start basierte Anlage zu einem Programm erfolgt automatisch. Wenn der Prozess, in dem das Programm gehostet wird, von der SDM gestartet wird, folgt die Start basierte Anlage einem Pfad, der dem der manuellen Anlage-Methode ähnelt. Weitere Informationen finden [Sie unter Anfügen an das Programm](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>Der Anfüge Vorgang
 Der Hauptunterschied ist die Abfolge der Ereignisse nach dem **Anfüge** Befehl, wie folgt:

1. Senden Sie ein **IDebugEngineCreateEvent2** -Ereignis Objekt an SDM. Weitere Informationen finden [Sie unter Senden von Ereignissen](../../extensibility/debugger/sending-events.md).

2. Ruft die- `IDebugProgram2::GetProgramId` Methode für die an die **Attach** -Methode weiter gegebene **IDebugProgram2** -Schnittstelle auf.

3. Senden Sie ein **IDebugProgramCreateEvent2** -Ereignis Objekt, um die SDM zu benachrichtigen, dass das lokale **IDebugProgram2** -Objekt erstellt wurde, um das Programm für die de darzustellen.

4. Senden Sie ein [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) -Ereignis Objekt, um die SDM zu benachrichtigen, dass ein neuer Thread für den gestarteten Prozess erstellt wird.

## <a name="see-also"></a>Weitere Informationen
- [Erforderliche Ereignisse senden](../../extensibility/debugger/sending-the-required-events.md)
- [Aktivieren eines zu deaktivier enden Programms](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
