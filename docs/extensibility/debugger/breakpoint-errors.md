---
title: Breakpoint-Fehler | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Prozess, wenn ein Breakpoint versucht, eine Bindung an den Code herzustellen, aber fehlschlägt und wie Fehler bei Haltepunkten behoben werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 840fde5943cb2249bdf73cc92ca15878ae4e3890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943453"
---
# <a name="breakpoint-errors"></a>Haltepunkt Fehler
Im folgenden wird der Prozess beschrieben, wenn ein Breakpoint versucht, eine Bindung an Code herzustellen, aber fehlschlägt.

## <a name="troubleshoot-a-breakpoint-error"></a>Beheben von Haltepunkt Fehlern

1. Die Debug-Engine (de) sendet ein [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) an den Sitzungs-Debug-Manager (SDM).

2. Der SDM ruft [IDebugBreakpointErrorEvent2:: geterrorbreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) auf, um den Fehler Haltepunkt zu erhalten.

3. Der SDM ruft [IDebugErrorBreakpoint2:: getpdingbreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) auf, um den ausstehenden Haltepunkt zu erhalten, von dem der Fehler-Breakpoint stammt.

4. Der SDM ruft [IDebugErrorBreakpoint2:: getbreakpointresolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) auf, um den Grund zu erhalten, warum der Fehler Haltepunkt nicht gebunden werden konnte.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debugger-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
