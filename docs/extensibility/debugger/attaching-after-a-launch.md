---
title: Anfügen nach einem Start | Microsoft-Dokumentation
description: Wenn ein Programm gestartet wird, kann die Debuggingsitzung an das Programm angefügt werden. Wählen Sie einen Entwurfs Ansatz für die Kommunikation mit der Debug-Engine aus.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e19d9090126a13b657f53c20d7ec44a793d5376
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913892"
---
# <a name="attach-after-a-launch"></a>Nach einem Start anfügen
Nachdem ein Programm gestartet wurde, ist die Debugsitzung bereit, das Debugmodul (de) an das angefügte Programm anzufügen.

## <a name="design-decisions"></a>Entwurfsentscheidungen
 Da die Kommunikation innerhalb eines freigegebenen Adressraums einfacher ist, müssen Sie zwischen zwei Entwurfs Ansätzen wählen: Festlegen der Kommunikation zwischen der Debugsitzung und der de. Oder legen Sie die Kommunikation zwischen dem Programm de und dem Programm fest. Wählen Sie eine der folgenden Optionen aus:

- Wenn es sinnvoller ist, die Kommunikation zwischen der Debugsitzung und der de einzurichten, erstellt die Debugsitzung die de und fordert die de auf, das Programm anzufügen. Dieser Entwurf verlässt die Debuggingsitzung und de in einem Adressraum und die Laufzeitumgebung und das Programm in einem anderen.

- Wenn es sinnvoller ist, die Kommunikation zwischen dem Programm de und dem Programm einzurichten, erstellt die Laufzeitumgebung die de. Dieser Entwurf verlässt die SDM in einem Adressraum und der de-, Laufzeitumgebung und dem Programm in einem anderen. Dieser Entwurf ist typisch für eine de, die mit einem Interpreter zum Ausführen von Skriptsprachen implementiert wird.

    > [!NOTE]
    > Wie der de an das Programm angefügt wird, hängt von der Implementierung ab. Die Kommunikation zwischen der de und dem Programm ist ebenfalls implementierungsabhängig.

## <a name="implementation"></a>Implementierung
 Programm gesteuert, wenn der Sitzungs-Debug-Manager (SDM) zuerst das [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -Objekt empfängt, das das zu startende Programm darstellt, ruft es die [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) -Methode auf und übergibt ihm ein [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das später verwendet wird, um Debugereignisse an die SDM zurückzuleiten. Die `IDebugProgram2::Attach` Methode ruft dann die [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode auf. Weitere Informationen zur Art und Weise, in der die SDM die `IDebugProgram2` Schnittstelle empfängt, finden Sie unter [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md).

 Wenn Ihre de in demselben Adressraum wie das Programm ausgeführt werden muss, das Sie Debuggen: da die de in der Regel Teil eines interpreters ist, der ein Skript ausgeführt, `IDebugProgramNodeAttach2::OnAttach` gibt die Methode zurück `S_FALSE` . Der `S_FALSE` Rückgabewert gibt an, dass der Anfüge Vorgang abgeschlossen wurde.

 Wenn die-Methode jedoch im Adressraum des SDM ausgeführt wird, `IDebugProgramNodeAttach2::OnAttach` gibt die Methode zurück `S_OK` , oder die [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) -Schnittstelle ist nicht für das [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekt implementiert, das dem Programm zugeordnet ist, das Sie Debuggen. In diesem Fall wird die [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode schließlich aufgerufen, um den Anfüge Vorgang abzuschließen.

 Im letzteren Fall müssen Sie die [getProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) -Methode für das- `IDebugProgram2` Objekt aufrufen, das an die-Methode weitergegeben wurde `IDebugEngine2::Attach` , die `GUID` im lokalen Programmobjekt speichern und diese zurückgeben, `GUID` Wenn die- `IDebugProgram2::GetProgramId` Methode anschließend für dieses Objekt aufgerufen wird. `GUID`Wird verwendet, um das Programm in den verschiedenen Debugkomponenten eindeutig zu identifizieren.

 Im Fall der Rückgabe der- `IDebugProgramNodeAttach2::OnAttach` Methode `S_FALSE` wird die `GUID` , die für das Programm verwendet werden soll, an diese Methode weitergegeben, und es handelt sich um die `IDebugProgramNodeAttach2::OnAttach` Methode, die für `GUID` das lokale Programmobjekt festlegt.

 DE ist nun an das Programm angefügt und kann alle Start Ereignisse senden.

## <a name="see-also"></a>Weitere Informationen
- [Direktes Anfügen an ein Programm](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md)
- [Debugtasks](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)
