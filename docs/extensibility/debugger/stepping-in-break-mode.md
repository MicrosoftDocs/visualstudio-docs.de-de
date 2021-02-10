---
title: Schrittweise im Break-Modus | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Prozess, der auftritt, wenn sich der Debugger im unterbrechen Modus befindet. Der Debugger muss dann den Code schrittweise durchlaufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f284fecf32a94f7187ecd34798f9ac21f476804
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960675"
---
# <a name="stepping-in-break-mode"></a>Schrittweise im Break-Modus
Im folgenden Abschnitt wird der Prozess beschrieben, der auftritt, wenn sich der Debugger im Break-Modus befindet und den Code schrittweise durchlaufen muss:

## <a name="stepping-process"></a>Schritt Prozess

1. Ruft [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) mit den Argumenten [stepkind](../../extensibility/debugger/reference/stepkind.md) und [stepunit](../../extensibility/debugger/reference/stepunit.md) auf, um einen Schritt auszuführen.

2. Wenn der Schritt abgeschlossen ist, senden Sie ein [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als anhalteereignis.

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debugger-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
