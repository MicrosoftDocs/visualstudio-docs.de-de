---
title: Breakpoints (Visual Studio SDK) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739193"
---
# <a name="breakpoints-visual-studio-sdk"></a>Haltepunkte (Visual Studio SDK)
Es gibt drei Arten von Haltepunkten: Ausstehend, gebunden und Fehler.

 **Ein ausstehender Haltepunkt:**

- Eine Abstraktion, die alle Informationen enthält, die erforderlich sind, um einen Breakpoint an einen oder mehrere Code Kontexte in einem oder mehreren Programmen zu binden. Jedes Mal, wenn ein Programm, das debuggt wird, Code geladen wird, überprüft die Debug-Engine alle ausstehenden Haltepunkte, um festzustellen, ob Sie gebunden werden können.

   Ein ausstehender Haltepunkt selbst wird nie an den Code gebunden, sondern sammelt und enthält alle gebundenen Haltepunkte, die er generiert.

- Wird durch eine [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Schnittstelle dargestellt.

  **Ein gebundener Haltepunkt:**

- Eine Abstraktion für einen Haltepunkt, der einem einzelnen Code Kontext zugeordnet ist oder an diesen gebunden ist. Jeder gebundene Haltepunkt wird als Reaktion auf einen ausstehenden Haltepunkt generiert. Ein ausstehender Haltepunkt kann jedoch mehr als einen gebundenen Haltepunkt generieren.

   Beim Entladen von Code kann ein gebundener Haltepunkt ungebunden und verworfen werden.

- Wird durch eine [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) -Schnittstelle dargestellt.

  **Fehler-Haltepunkt:**

- Eine Abstraktion zum Beschreiben eines Fehlers beim Versuch, einen ausstehenden Breakpoint an einen Code Kontext zu binden. Ein Fehler Haltepunkt beschreibt entweder einen Fehler im Speicherort oder im Breakpoint-Ausdruck selbst. Weitere Informationen finden Sie unter [Binden von Breakpoints](../../extensibility/debugger/binding-breakpoints.md).

   Der Breakpoint-Fehler kann entweder ein Fehler oder eine Warnung sein.

- Wird durch eine [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) -Schnittstelle dargestellt.

## <a name="see-also"></a>Weitere Informationen
- [Programs](../../extensibility/debugger/programs.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [Code Kontext](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
