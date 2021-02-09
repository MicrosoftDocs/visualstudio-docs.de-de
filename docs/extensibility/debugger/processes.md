---
title: Prozesse | Microsoft-Dokumentation
description: In diesem Artikel werden die Definition und die Rolle eines Prozesses in der Debugger-Architektur in Visual Studio beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2fe8d170f6e7b4dcd774773109c4880d4898e0b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884831"
---
# <a name="processes"></a>Prozesse
In der Debugger-Architektur ist ein *Prozess*:

- Ist ein Container für einen Satz von Programmen. Sie ähnelt einem Windows-Prozess, bei dem es sich um einen Container für eine Gruppe von Threads handelt.

- Kann sich selbst anhand des Namens, Bezeichners oder physischen Bezeichners identifizieren.

- Kann alle ausgelaufenden Programme (und deren Threads) auflisten.

- Kann sich selbst, den Port, in dem er ausgeführt wird, und den Computer, der ihn enthält, beschreiben.

- Kann ein oder mehrere Programme erstellen, alle erstellten Programme beenden oder ein Programm beenden.

- Wird durch eine [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) -Schnittstelle dargestellt, die beim Starten des Prozesses erstellt wird. Ein Prozess wird entweder vom Sitzungs-Debug-Manager (SDM) oder vom [launchangeh](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)alten gestartet.

  Das Debugpaket kann eine Debug-Engine (de) an einen Prozess anfügen, indem Sie [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md)aufrufen. Dies bedeutet, dass die de an alle möglichen Programme angefügt wird, die im Prozess ausgeführt werden, den Sie verarbeiten kann. Wenn z. b. der Common Language Runtime de an einen Prozess angefügt wird, wird er nur an Programme angefügt, die verwalteten Code ausführen.

## <a name="see-also"></a>Weitere Informationen
- [Programs](../../extensibility/debugger/programs.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [Paket Debuggen](../../extensibility/debugger/debug-package.md)
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md)
