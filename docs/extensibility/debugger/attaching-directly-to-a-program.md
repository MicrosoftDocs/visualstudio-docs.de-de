---
title: Direktes Anfügen an ein Programm | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio das Anfügen einer Debug-Engine an einen Prozess implementiert, der bereits ausgeführt wird, indem Sie dieses Verfahren in der Visual Studio-IDE verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f1b23cd7c09f3eeac2bfe85de882ff42affaa652
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920081"
---
# <a name="attach-directly-to-a-program"></a>Direkt an ein Programm anfügen
Benutzer, die Programme in einem Prozess debuggen möchten, der bereits ausgeführt wird, führen in der Regel folgenden Vorgang aus:

1. Wählen Sie **in der IDE im Menü Extras** den Befehl **Debuggen** aus.

    Das Dialogfeld **Prozesse** wird angezeigt.

2. Wählen Sie einen Prozess aus, und klicken Sie auf die Schaltfläche **Anhängen**

    Das Dialogfeld **an den Prozess anhängen** wird angezeigt, in dem alle auf dem Computer installierten Debugmodule (debugengines) aufgelistet sind.

3. Geben Sie den zum Debuggen des ausgewählten Prozesses zu verwendenden des an, und klicken Sie dann auf **OK**.

   Das Debugpaket startet eine Debugsitzung und übergibt die Liste von des an Sie. Die Debugsitzung wiederum übergibt diese Liste zusammen mit einer Rückruffunktion an den ausgewählten Prozess und fordert den Prozess auf, die ausgelaufenden Programme aufzulisten.

   Programm gesteuert instanziiert das Debugpaket als Reaktion auf die Benutzer Anforderung den Sitzungs-Debug-Manager (SDM) und übergibt die Liste der ausgewählten des an ihn. Zusammen mit der Liste übergibt das Debug-Paket die SDM an eine [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) -Schnittstelle. Das Debugpaket übergibt die Liste von des an den ausgewählten Prozess, indem [IDebugProcess2:: Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)aufgerufen wird. Der SDM ruft dann [IDebugProcess2:: enumprograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) auf dem Port auf, um die im Prozess ausgezählten Programme aufzulisten.

   Ab diesem Zeitpunkt wird jedes Debug-Modul genau wie beim Anfügen [nach einem Start](../../extensibility/debugger/attaching-after-a-launch.md)mit zwei Ausnahmen an ein Programm angefügt.

   Aus Effizienzgründen werden des, das für die gemeinsame Nutzung eines Adressraums mit dem SDM implementiert ist, so gruppiert, dass jede de über eine Reihe von Programmen verfügt, an die Sie angefügt wird. In diesem Fall ruft [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) [IDebugEngine2:: Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) auf und übergibt ihm ein Array von Programmen, an die angehängt werden soll.

   Die zweite Ausnahme besteht darin, dass die Start Ereignisse, die von einem Anfügen an ein bereits ausgelaufendes Programm gesendet werden, in der Regel nicht das Einstiegspunkt Ereignis enthalten.

## <a name="see-also"></a>Weitere Informationen
- [Senden von Start Ereignissen nach einem Start](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Debugtasks](../../extensibility/debugger/debugging-tasks.md)
