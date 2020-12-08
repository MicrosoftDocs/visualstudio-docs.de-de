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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80273bf470a3ed0c342e781085de6e991508451c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845192"
---
# <a name="stepping-in-break-mode"></a>Schrittweise im Break-Modus
Im folgenden Abschnitt wird der Prozess beschrieben, der auftritt, wenn sich der Debugger im Break-Modus befindet und den Code schrittweise durchlaufen muss:

## <a name="stepping-process"></a>Schritt Prozess

1. Ruft [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) mit den Argumenten [stepkind](../../extensibility/debugger/reference/stepkind.md) und [stepunit](../../extensibility/debugger/reference/stepunit.md) auf, um einen Schritt auszuführen.

2. Wenn der Schritt abgeschlossen ist, senden Sie ein [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als anhalteereignis.

## <a name="see-also"></a>Siehe auch
- [Aufrufen von Debugger-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
