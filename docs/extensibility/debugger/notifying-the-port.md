---
title: Benachrichtigen des Ports | Microsoft-Dokumentation
description: Erfahren Sie, wie der Port nach dem Starten eines Programms benachrichtigt wird. Dieser Artikel enthält eine ausführliche Beschreibung.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9a838879e7c1eb590bb16cd12a6bf345de8031a
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606618"
---
# <a name="notify-the-port"></a>Benachrichtigen des Ports
Nachdem Sie ein Programm gestartet haben, muss der Port wie folgt benachrichtigt werden:

1. Wenn ein Port einen neuen Programmknoten empfängt, sendet er ein Programm Erstellungs Ereignis an die Debugsitzung zurück. Das Ereignis enthält eine Schnittstelle, die das Programm darstellt.

2. Die Debugsitzung fragt das Programm nach dem Bezeichner einer Debug-Engine (de) ab, die an angefügt werden kann.

3. Die Debugsitzung prüft, ob de in der Liste der zulässigen des für dieses Programm ist. Die Debugsitzung ruft diese Liste aus den aktiven Programmeinstellungen der Projekt Mappe ab, die ursprünglich vom Debugpaket an Sie übermittelt wurden.

    Die "de" muss in der Liste der zulässigen Dateien enthalten sein, andernfalls wird die "de" nicht an das Programm angefügt.

   Programm gesteuert, wenn ein Port zum ersten Mal einen neuen Programmknoten empfängt, erstellt er eine [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle, die das Programm darstellt.

> [!NOTE]
> Dies sollte nicht mit der-Schnittstelle verwechselt werden, die `IDebugProgram2` später von der Debug-Engine (de) erstellt wird.

 Der Port sendet ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Program Creation-Ereignis mithilfe einer COM-Schnittstelle an den Sitzungs-Debug-Manager (SDM) zurück `IConnectionPoint` .

> [!NOTE]
> Dies sollte nicht mit der- `IDebugProgramCreateEvent2` Schnittstelle verwechselt werden, die später von der de gesendet wird.

 Zusammen mit der Ereignis Schnittstelle selbst sendet der Port die [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)-, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)-und [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstellen, die den Port, den Prozess bzw. das Programm darstellen. Der SDM ruft [IDebugProgram2:: getengineingefo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) auf, um die GUID des de-Objekts zu erhalten, das das Programm debuggen kann. Die GUID wurde ursprünglich von der [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle abgerufen.

 Der SDM prüft, ob de in der Liste der zulässigen des ist. Die SDM ruft diese Liste aus den aktiven Programmeinstellungen der Projekt Mappe ab, die ursprünglich vom Debugpaket an Sie übermittelt wurden. Die de muss in der Liste der zulässigen Dateien enthalten sein, oder Sie wird nicht an das Programm angefügt.

 Nachdem die Identität der de bekannt ist, ist die SDM zum Anfügen an das Programm bereit.

## <a name="see-also"></a>Weitere Informationen
- [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)
- [Anfügen nach einem Start](../../extensibility/debugger/attaching-after-a-launch.md)
- [Debugtasks](../../extensibility/debugger/debugging-tasks.md)
