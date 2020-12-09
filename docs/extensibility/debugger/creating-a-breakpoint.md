---
title: Erstellen eines Breakpoints | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Methodenaufrufe, die der Sitzungs-Debug-Manager ausführt, wenn das zum Binden eines Breakpoints benötigte Modul geladen wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba192a0cda2e63453984d3de7d6007744cc401b7
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914227"
---
# <a name="create-a-breakpoint"></a>Erstellen eines Breakpoints
Im folgenden wird der Prozess zum Erstellen eines Breakpoints beschrieben.

## <a name="methods-in-breakpoint-creation"></a>Methoden bei der Breakpoint-Erstellung
 Wenn das Modul, das zum Binden eines Breakpoints benötigt wird, geladen ist, ruft der Sitzungs-Debug-Manager (SDM) die folgenden Methoden auf:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > " **Canbind** " wird nur aufgerufen, wenn ein Benutzer einen Haltepunkt im Fenster " **Breakpoints** " erstellt.

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Ereignisse aufzurufen](../../extensibility/debugger/calling-debugger-events.md)
