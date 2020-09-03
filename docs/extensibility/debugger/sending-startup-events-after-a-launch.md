---
title: Senden von Start Ereignissen nach einem Start | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713014"
---
# <a name="send-startup-events-after-a-launch"></a>Start Ereignisse nach einem Start senden
Nachdem die Debug-Engine (de) an das Programm angefügt wurde, sendet Sie eine Reihe von Start Ereignissen an die Debugsitzung zurück.

 Die an die Debugsitzung zurückgesendeten Start Ereignisse umfassen Folgendes:

- Ein Engine-Erstellungs Ereignis.

- Ein Programm Erstellungs Ereignis.

- Thread Erstellung und Modul Lade Ereignisse.

- Ein Load Complete-Ereignis, das gesendet wird, wenn der Code geladen und bereit ist, aber vor dem Ausführen von Code ausgeführt wird.

  > [!NOTE]
  > Wenn dieses Ereignis fortgesetzt wird, werden globale Variablen initialisiert, und Start Routinen werden ausgeführt.

- Mögliche andere Thread Erstellung und Modul Lade Ereignisse.

- Ein Einstiegspunkt Ereignis, das signalisiert, dass das Programm den Haupteinstiegspunkt erreicht hat, z. b. **Main** oder `WinMain` . Dieses Ereignis wird in der Regel nicht gesendet, wenn die de an ein bereits ausgelaufendes Programm angefügt wird.

  Programm gesteuert Sendet der de zuerst den Session Debug Manager (SDM) an eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Schnittstelle, die ein Engine-Erstellungs Ereignis darstellt, gefolgt von einem [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), das ein Programm Erstellungs Ereignis darstellt.

  Diese Ereignisse folgen in der Regel einem oder mehreren [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) Thread-Erstellungs Ereignissen und [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) -Modul Lade Ereignissen.

  Wenn der Code geladen und zur Ausführung bereit ist, aber bevor Code ausgeführt wird, sendet der de das SDM-Ereignis " [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Load Complete". Wenn das Programm nicht bereits ausgeführt wird, sendet der de ein [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) -Einstiegspunkt Ereignis, das signalisiert, dass das Programm den Haupteinstiegspunkt erreicht hat und zum Debuggen bereit ist.

## <a name="see-also"></a>Weitere Informationen
- [Kontrolle der Ausführung](../../extensibility/debugger/control-of-execution.md)
- [Debugtasks](../../extensibility/debugger/debugging-tasks.md)
