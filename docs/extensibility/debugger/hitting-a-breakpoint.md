---
title: Erreichen eines halte Punkts | Microsoft-Dokumentation
description: In diesem Artikel wird der Prozess beschrieben, der ausgeführt wird, wenn die Debug-Engine während der Ausführung oder Ausführung einen Haltepunkt erreicht.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 808bf95631bb4106d071c29d7af233d071ef5229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947722"
---
# <a name="hit-a-breakpoint"></a>Treffen eines Haltepunkts
Der folgende Abschnitt beschreibt den Prozess, in dem die Debug-Engine (de) während der Ausführung oder beim Ausführen des Vorgangs einen Haltepunkt erreicht:

## <a name="troubleshoot-a-hit-breakpoint"></a>Behandeln von Problemen mit einem Treffer Haltepunkt

1. Der de sendet eine [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) -Schnittstelle als **EVENT_SYNC_STOP**.

2. Der Session Debug Manager (SDM) ruft [IDebugBreakpointEvent2::: enumbreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) auf, um den Treffer Haltepunkt zu erhalten.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Ereignisse aufzurufen](../../extensibility/debugger/calling-debugger-events.md)
