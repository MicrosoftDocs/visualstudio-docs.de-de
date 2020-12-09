---
title: Kontrolle der Ausführung | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Beenden von Ereignissen, d. h., der Benutzer wartet auf eine Antwort vom Benutzer über die IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88adaad3092e084841c40b5e04d45f94985a2ee8
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913879"
---
# <a name="control-of-execution"></a>Kontrolle der Ausführung
Die Debug-Engine (de) sendet in der Regel eines der folgenden Ereignisse als letztes Start Ereignis:

- Das Einstiegspunkt Ereignis, wenn es an ein neu gestartetes Programm angefügt wird.

- Das Lade Abschluss Ereignis, wenn es an ein Programm angefügt wird, das bereits ausgeführt wird.

  Beide Ereignisse sind das Beenden von Ereignissen, d. h., das Ende wartet auf eine Antwort vom Benutzer über die IDE. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Beenden des Ereignisses
 Wenn ein anhalteereignis an die Debugsitzung gesendet wird:

1. Das Programm und der Thread, die den aktuellen Anweisungs Zeiger enthalten, können von der Ereignis Schnittstelle abgerufen werden.

2. Die IDE bestimmt die aktuelle Quell Code Datei und-Position, die im Editor als hervorgehoben angezeigt wird.

3. Die Debugsitzung antwortet in der Regel auf dieses erste anhalteereignis, indem die **Continue** -Methode des Programms aufgerufen wird.

4. Das Programm wird dann ausgeführt, bis eine Anhaltebedingung feststellt, z. b. das Erreichen eines Breakpoints. In diesem Fall sendet der de ein breakpointereignis an die Debugsitzung. Bei dem breakpointereignis handelt es sich um ein anhalteereignis, das wiederum auf eine Benutzer Antwort wartet.

5. Wenn der Benutzer eine Funktion in Einzelschritten, überspringen oder aus einer Funktion auswählt, wird die Debugsitzung von der IDE aufgefordert, die-Methode des Programms aufzurufen `Step` . Die IDE übergibt dann die Schritt Einheit (Anweisung, Anweisung oder Zeile) und den Typ des Schritts (ob Einzel-, über-oder Ausgabe der Funktion). Nachdem der Schritt ausgeführt wurde, sendet der de ein Step Complete-Ereignis an die Debugsitzung, bei der es sich um ein anhalteereignis handelt.

    - oder -

    Wenn der Benutzer die Ausführung über den aktuellen Anweisungs Zeiger fortsetzt, wird die Debugsitzung von der IDE aufgefordert, die **Execute** -Methode des Programms aufzurufen. Das Programm setzt die Ausführung fort, bis die nächste Anhaltebedingung auftritt.

    - oder -

    Wenn die Debugsitzung ein bestimmtes anhalteereignis ignorieren soll, ruft die Debugsitzung die **Continue** -Methode des Programms auf. Wenn das Programm eine Funktion in Einzelschritten, ein-oder Auschecken, wenn die Anhaltebedingung aufgetreten ist, wird der Schritt fortgesetzt.

   Programm gesteuert, wenn die de auf eine Anhaltebedingung stößt, sendet Sie derartige anhalteereignisse als [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) über eine [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) -Schnittstelle an den Sitzungs-Debug-Manager (SDM). Der de übergibt die [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -und [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) -Schnittstellen, die das Programm darstellen, und den Thread, der den aktuellen Anweisungs Zeiger enthält. Der SDM ruft [IDebugThread2:: enumframeinfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) auf, um den obersten Stapel Rahmen zu erhalten, und ruft [IDebugStackFrame2:: getdocumentcontext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) auf, um den Dokument Kontext zu erhalten, der dem aktuellen Anweisungs Zeiger zugeordnet ist. Dieser Dokument Kontext ist in der Regel ein Quell Code Dateiname, eine Zeile und eine Spaltennummer. Diese werden von der IDE zum Hervorheben des Quellcodes verwendet, der den aktuellen Anweisungs Zeiger enthält.

   Der SDM antwortet in der Regel auf dieses erste anhalteereignis, indem [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)aufgerufen wird. Das Programm wird dann ausgeführt, bis eine Anhaltebedingung (z. b. das Erreichen eines Breakpoints) erkannt wird. in diesem Fall sendet der de eine [IDebugBreakpointEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugbreakpointevent2.md) an die SDM. Bei dem breakpointereignis handelt es sich um ein anhalteereignis, das wiederum auf eine Benutzer Antwort wartet.

   Wenn der Benutzer eine Funktion in Einzelschritten, überspringen oder aus einer Funktion auswählt, fordert die IDE den SDM auf, [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md)aufzurufen. Die IDE übergibt dann die [stepunit](../../extensibility/debugger/reference/stepunit.md) (-Anweisung,-Anweisung oder-Zeile) und den [stepkind](../../extensibility/debugger/reference/stepkind.md), d. h. ob die Funktion in Einzelschritten, überspringen oder aus der Funktion ausgeführt werden soll. Nach Abschluss des Schritts sendet der de eine [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) -Schnittstelle an die SDM, bei der es sich um ein anhalteereignis handelt.

   Wenn der Benutzer die Ausführung über den aktuellen Anweisungs Zeiger fortsetzt, fordert die IDE die SDM auf, [IDebugProgram2:: Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)aufzurufen. Das Programm setzt die Ausführung fort, bis die nächste Anhaltebedingung auftritt.

   Wenn das Debugpaket ein bestimmtes anhalteereignis ignorieren soll, ruft das Debugpaket den SDM auf, der [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)aufruft. Wenn das Programm eine Funktion in Einzelschritten, ein-oder Auschecken, wenn die Anhaltebedingung aufgetreten ist, wird der Schritt fortgesetzt. Dies bedeutet, dass das Programm einen Schritt-für-Schritt beibehält, sodass er weiß, wie er fortfahren kann.

   Die Aufrufe, die SDM `Step` ausführt, **Ausführen** und **fortsetzen** , sind asynchron. Dies bedeutet, dass die SDM erwartet, dass der Aufruf schnell zurückgegeben wird. Wenn von de der SDM ein anhalteereignis im gleichen Thread `Step` ausgeführt wird, bevor, **Execute** oder **Continue** zurückgegeben wird, reagiert der SDM nicht mehr.

## <a name="see-also"></a>Weitere Informationen
- [Debuggen von Tasks](../../extensibility/debugger/debugging-tasks.md)
