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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f898bcb040b5b46144fd7c4f3fc2260b480872d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945941"
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
