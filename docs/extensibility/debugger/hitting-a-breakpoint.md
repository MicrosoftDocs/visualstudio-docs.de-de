---
title: Erreichen eines halte Punkts | Microsoft-Dokumentation
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
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738570"
---
# <a name="hit-a-breakpoint"></a>Treffen eines Haltepunkts
Der folgende Abschnitt beschreibt den Prozess, in dem die Debug-Engine (de) während der Ausführung oder beim Ausführen des Vorgangs einen Haltepunkt erreicht:

## <a name="troubleshoot-a-hit-breakpoint"></a>Behandeln von Problemen mit einem Treffer Haltepunkt

1. Der de sendet eine [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) -Schnittstelle als **EVENT_SYNC_STOP**.

2. Der Session Debug Manager (SDM) ruft [IDebugBreakpointEvent2::: enumbreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) auf, um den Treffer Haltepunkt zu erhalten.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Ereignisse aufzurufen](../../extensibility/debugger/calling-debugger-events.md)
