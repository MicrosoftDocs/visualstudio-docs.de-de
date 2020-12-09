---
title: Aufrufen von Debugger-Ereignissen | Microsoft-Dokumentation
description: Ereignisse in Debugsitzungen treten in einer bestimmten Reihenfolge auf. Dieser Artikel listet die Aufruf Reihenfolge der Ereignisse auf, die in einer typischen Debugsitzung auftreten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 832b42e62731a087048b4aa50e19b74c408343c5
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914387"
---
# <a name="call-debugger-events"></a>Debugger-Ereignisse aufzurufen
Ereignisse in Debugsitzungen treten in einer bestimmten Reihenfolge auf.

## <a name="discussion"></a>Diskussion
 Um das Muster von Aufrufen zwischen Debug Engine (de) und Session Debug Manager (SDM) zu verstehen, stellt Folgendes die Aufruf Reihenfolge der Ereignisse dar, die in einer typischen Debugsitzung auftreten:

1. [Anfügen und trennen an ein Programm](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Starten des Debuggers](../../extensibility/debugger/launching-the-debugger.md)

3. [Beenden eines Programms](../../extensibility/debugger/terminating-a-program.md)

4. [Erstellen eines Breakpoints](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Wenn ein Breakpoint gebunden wird oder die Bindung aufgehoben wird](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Haltepunkt Fehler](../../extensibility/debugger/breakpoint-errors.md)

7. [Treffen eines Haltepunkts](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Löschen eines Breakpoints](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Wechseln in den Umbruch Modus](../../extensibility/debugger/entering-break-mode.md)

10. [Schrittweise im Break-Modus](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Ausdrucks Auswertung im Break-Modus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Ausnahmebehandlung](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Weitere Informationen
- [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
