---
title: Unterstützte Ereignis Typen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Ereignis Typen, die von Visual Studio-Debugging unterstützt werden, einschließlich asynchroner Ereignisse, synchroner Ereignisse und Beenden von Ereignissen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9bf2e154d5803324161e073edbd74e049c0897ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960688"
---
# <a name="supported-event-types"></a>Unterstützte Ereignis Typen
Das Debuggen von Visual Studio unterstützt derzeit die folgenden Ereignis Typen:

- Asynchrone Ereignisse

   Benachrichtigen Sie den Sitzungs-Debug-Manager (SDM) und die IDE, dass sich der Status der zu debuggenden Anwendung ändert. Diese Ereignisse werden in der Freizeit von SDM und der IDE verarbeitet. Es wird keine Antwort an die Debug-Engine (de) gesendet, sobald das Ereignis verarbeitet wurde. Die [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) -und [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) -Schnittstellen sind Beispiele für asynchrone Ereignisse.

- Synchrone Ereignisse

   Benachrichtigen Sie die SDM und die IDE, dass sich der Status der zu deschenden Anwendung ändert. Der einzige Unterschied zwischen diesen Ereignissen und asynchronen Ereignissen besteht darin, dass eine Antwort mithilfe der [continuefromsynchronoutsvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) -Methode gesendet wird.

   Das Senden eines synchronen Ereignisses ist nützlich, wenn Sie möchten, dass ihre Verarbeitung fortgesetzt wird, nachdem die IDE das Ereignis empfangen und verarbeitet hat.

- Synchrone Stopp Ereignisse oder Beenden von Ereignissen

   Benachrichtigen von SDM und der IDE, dass die Anwendung, für die das Debugging ausgeführt wird, nicht mehr ausgeführt wird. Wenn Sie ein anhalteereignis mithilfe des Methoden [Ereignisses](../../extensibility/debugger/reference/idebugeventcallback2-event.md)senden, ist der [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) -Parameter erforderlich. Das Beenden von Ereignissen wird durch einen Rückruf der folgenden Methoden fortgesetzt:

  - [Ausführen](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Schritt](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Fortsetzen](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Die Schnittstellen [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sind Beispiele für das Beenden von Ereignissen.

  > [!NOTE]
  > Asynchrone anhalteereignisse werden nicht unterstützt. Es ist ein Fehler, ein asynchrones anhalteereignis zu senden.

## <a name="discussion"></a>Diskussion
 Die tatsächliche Implementierung von Ereignissen hängt vom Entwurf Ihrer de ab. Der Typ jedes gesendeten Ereignisses wird durch seine Attribute bestimmt, die beim Entwerfen von de festgelegt werden. Beispielsweise kann eine de ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Ereignis als asynchrones Ereignis senden, während ein anderes es als anhalteereignis senden kann.

 In der folgenden Tabelle wird angegeben, welche Programm-und Thread Parameter für welche Ereignisse und Ereignis Typen erforderlich sind. Beliebige Ereignisse können synchron sein. Es muss kein Ereignis synchron sein.

> [!NOTE]
> Die [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) -Schnittstelle ist für alle Ereignisse erforderlich.

|event|IDebugProgram2|IDebugThread2|Beenden von Ereignissen|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Erforderlich|Erforderlich|Nein|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nicht zulässig|Nicht zulässig|Nein|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nicht zulässig|Nicht zulässig|Nein|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Wird bei Bedarf|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Wird bei Bedarf|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Wird bei Bedarf|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Nein|
|IDebugStopCompleteEvent2|Erforderlich|Erforderlich|Ja|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Nein|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Erforderlich|Erforderlich|Nein|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Erforderlich|Erforderlich|Nein|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Zulässig, aber nicht erforderlich|Zulässig, aber nicht erforderlich|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)
