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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc796689b56518948c62196407ddeaefe3ea822f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560849"
---
# <a name="hit-a-breakpoint"></a>Treffen eines Haltepunkts
Der folgende Abschnitt beschreibt den Prozess, in dem die Debug-Engine (de) während der Ausführung oder beim Ausführen des Vorgangs einen Haltepunkt erreicht:

## <a name="troubleshoot-a-hit-breakpoint"></a>Behandeln von Problemen mit einem Treffer Haltepunkt

1. Der de sendet eine [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) -Schnittstelle als **EVENT_SYNC_STOP**.

2. Der Session Debug Manager (SDM) ruft [IDebugBreakpointEvent2::: enumbreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) auf, um den Treffer Haltepunkt zu erhalten.

## <a name="see-also"></a>Siehe auch
- [Debugger-Ereignisse aufzurufen](../../extensibility/debugger/calling-debugger-events.md)
