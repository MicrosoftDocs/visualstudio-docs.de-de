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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dcd81b79fa43d86036a7fd1ac0ad813e6e2ebb78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894971"
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
