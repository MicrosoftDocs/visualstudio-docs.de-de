---
title: Löschen eines Breakpoints | Microsoft-Dokumentation
description: Erfahren Sie, wie der sitzungsdebug-Manager einen ausstehenden Haltepunkt und alle gebundenen Haltepunkte entfernt, die beim Löschen eines ausstehenden halte Punkts gebunden sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ebd2922f48a53c371f4930e5de1fd86ed6852a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862174"
---
# <a name="deleting-a-breakpoint"></a>Löschen eines Breakpoints
Im folgenden wird der Prozess zum Löschen eines ausstehenden Breakpoints beschrieben:

## <a name="deletion-process"></a>Löschvorgang
 Der Session Debug Manager (SDM) Ruft die [IDebugPendingBreakpoint2::D Elete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) -Methode auf, um den ausstehenden Haltepunkt und alle von ihm gebundenen gebundenen Haltepunkte zu entfernen.

> [!NOTE]
> Ein einzelner gebundener Haltepunkt kann auch durch einen [IDebugBoundBreakpoint2::D Elete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)-aufrufungspunkt gelöscht werden.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Ereignisse aufzurufen](../../extensibility/debugger/calling-debugger-events.md)
