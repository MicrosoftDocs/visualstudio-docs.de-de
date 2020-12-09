---
title: Anhängen an das Programm | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio den Debugger implementiert, der an ein Programm angehängt wird, nachdem das Programm mit dem entsprechenden Port registriert wurde.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 030ee19e7e9e9e52140fb41da78f766978e18d3f
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913762"
---
# <a name="attach-to-the-program"></a>An das Programm anfügen
Nachdem Sie Ihre Programme mit dem entsprechenden Port registriert haben, müssen Sie den Debugger an das Programm anfügen, das Sie debuggen möchten.

## <a name="choose-how-to-attach"></a>Auswählen, wie angefügt werden soll
 Es gibt drei Möglichkeiten, wie der Sitzungs-Debug-Manager (SDM) versucht, an das zu debuggende Programm anzufügen.

1. Für Programme, die von der Debug-Engine über die [launchangeh](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) Ende-Methode gestartet werden (z. b. typisch für interpretierte Sprachen), ruft die SDM die [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) -Schnittstelle aus dem [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekt ab, das mit dem angefügten Programm verknüpft ist. Wenn die SDM die `IDebugProgramNodeAttach2` Schnittstelle abrufen kann, ruft der SDM die [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode auf. Die- `IDebugProgramNodeAttach2::OnAttach` Methode gibt zurück, `S_OK` um anzugeben, dass Sie nicht an das Programm angefügt wurde und dass andere Versuche zum Anfügen an das Programm vorgenommen werden können.

2. Wenn die SDM die [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) -Schnittstelle von dem angefügten Programm abrufen kann, ruft die SDM die [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) -Methode auf. Diese Vorgehensweise ist typisch für Programme, die vom Anschluss Lieferanten Remote gestartet wurden.

3. Wenn das Programm nicht über die-Methode oder die-Methode angefügt werden kann `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` , lädt SDM die Debug-Engine (sofern nicht bereits geladen) durch Aufrufen der `CoCreateInstance` -Funktion und ruft dann die [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode auf. Diese Vorgehensweise ist typisch für Programme, die lokal von einem Port Lieferanten gestartet werden.

    Es ist auch möglich, dass ein benutzerdefinierter Port Lieferant die `IDebugEngine2::Attach` -Methode in der Implementierung der-Methode des benutzerdefinierten Port Anbieters aufruft `IDebugProgramEx2::Attach` . In diesem Fall wird der benutzerdefinierte Port Lieferant in der Regel die Debug-Engine auf dem Remote Computer starten.

   Die Anlage wird erreicht, wenn der Sitzungs-Debug-Manager (SDM) die [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode aufruft.

   Wenn Sie die de in demselben Prozess wie die zu debuggende Anwendung ausführen, müssen Sie die folgenden Methoden von [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)implementieren:

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Nachdem die- `IDebugEngine2::Attach` Methode aufgerufen wurde, führen Sie die folgenden Schritte in der Implementierung der- `IDebugEngine2::Attach` Methode aus:

1. Senden Sie ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Ereignis Objekt an SDM. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).

2. Aufrufen der [getProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) -Methode für das [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das an die-Methode weitergegeben wurde `IDebugEngine2::Attach` .

     Gibt einen zurück `GUID` , der zum Identifizieren des Programms verwendet wird. `GUID`Muss in dem-Objekt gespeichert werden, das das lokale Programm in der de darstellt, und es muss zurückgegeben werden, wenn die- `IDebugProgram2::GetProgramId` Methode für die- `IDebugProgram2` Schnittstelle aufgerufen wird.

    > [!NOTE]
    > Wenn Sie die `IDebugProgramNodeAttach2` -Schnittstelle implementieren, wird das Programm `GUID` an die-Methode übermittelt `IDebugProgramNodeAttach2::OnAttach` . Diese `GUID` wird für das `GUID` von der-Methode zurückgegebene Programm verwendet `IDebugProgram2::GetProgramId` .

3. Senden Sie ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Ereignis Objekt, um die SDM zu benachrichtigen, dass das lokale `IDebugProgram2` Objekt erstellt wurde, um das Programm für die de darzustellen. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Dabei handelt es sich nicht um dasselbe `IDebugProgram2` Objekt, das an die-Methode übermittelt wurde `IDebugEngine2::Attach` . Das zuvor bestandene `IDebugProgram2` Objekt wird nur vom Port erkannt und ist ein separates Objekt.

## <a name="see-also"></a>Weitere Informationen
- [Start basierte Anlage](../../extensibility/debugger/launch-based-attachment.md)
- [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Anfügen](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)
