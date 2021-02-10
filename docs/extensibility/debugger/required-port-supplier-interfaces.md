---
title: Erforderliche Port Lieferanten Schnittstellen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Schnittstellen, die ein Port Lieferant ausführen muss. Ein Port Lieferant liefert Ports und implementiert diese.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 930166d84e6203b0d1d62ef661e768f0f14e60f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961052"
---
# <a name="required-port-supplier-interfaces"></a>Erforderliche Port Lieferanten Schnittstellen
Ein Port Lieferant muss die [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle implementieren. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Ein Port Lieferant liefert Ports und implementiert diese. Daher müssen die folgenden Schnittstellen ausgeführt werden:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Beschreibt den Port und listet alle Prozesse auf, die auf dem Port ausgeführt werden.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Ermöglicht das Starten und Beenden von Prozessen auf dem Port.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Bietet einen Mechanismus für Programme, die innerhalb des Kontexts dieses Ports ausgeführt werden, um Sie über die Erstellung und Zerstörung von Programmknoten zu benachrichtigen. Weitere Informationen finden Sie unter [Programmknoten](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Stellt einen Verbindungspunkt für [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)bereit.

## <a name="port-supplier-operation"></a>Port Lieferanten Vorgang
 Die [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) -Senke empfängt Benachrichtigungen, wenn Prozess und Programme auf einem Port erstellt und zerstört werden. Ein Port ist erforderlich, um [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) zu senden, wenn ein Prozess erstellt wird, und [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) , wenn ein Prozess auf dem Port zerstört wird. Ein Port ist auch erforderlich, um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zu senden, wenn ein Programm erstellt wird, und [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) , wenn ein Programm in einem Prozess zerstört wird, der auf dem Port ausgeführt wird.

 Ein Port sendet in der Regel Programm Erstellungs-und Lösch Ereignisse als Reaktion auf die Methoden " [addprogramnode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) " und " [removeprogramnode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) ".

 Da ein Port sowohl physische als auch logische Programme starten und beenden kann, müssen die folgenden Schnittstellen auch von der Debug-Engine implementiert werden:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Beschreibt den physischen Prozess. Mindestens die folgenden Methoden müssen implementiert werden:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Bietet eine Möglichkeit für das Anfügen und trennen von SDM von einem Prozess.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Beschreibt das logische Programm. Mindestens die folgenden Methoden müssen implementiert werden:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Bietet eine Möglichkeit, das SDM an dieses Programm anzufügen.

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Port Anbieters](../../extensibility/debugger/implementing-a-port-supplier.md)
