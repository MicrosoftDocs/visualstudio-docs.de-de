---
title: Debuggen von Tasks | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die zum Debuggen eines Programms erforderlichen Tasks wie das Anfügen des Programms an eine Debug-Engine, das Generieren von Startereignissen und das Erreichen von Breakpoints.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83d351e2b995922d1a8257f7ea9fc0cdad67ab3e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915569"
---
# <a name="debug-tasks"></a>Debuggen von Tasks
Zum Debuggen eines Programms muss es gestartet werden, und es muss eine Debug-Engine (DE) angefügt werden. Andernfalls muss die DE an ein zuvor gestartetes Programm angefügt werden. Nach dem Anfügen muss die DE bestimmte Startereignisse generieren. Als Antwort versucht das Debugpaket, die Breakpoints zu binden, die in der IDE festgelegt wurden. Wenn das Programm auf einen gebundenen Breakpoint trifft, wird es angehalten und wartet auf eine Benutzereingabe.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Sicherheitsprobleme](../../extensibility/debugger/security-issues.md) erläutert die Sicherheitsschritte, die zum Debuggen eines Programms erforderlich sind.

 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md) enthält schrittweise Anleitungen zum Angeben einer DE, die das Betriebssystem aufruft, um das Programm zu starten.

 [Direktes Anfügen an ein Programm](../../extensibility/debugger/attaching-directly-to-a-program.md) beschreibt den Prozess, der zum Debuggen eines Programms in einem Prozess verwendet wird, der bereits ausgeführt wird.

 [Senden von Startereignissen nach einem Start](../../extensibility/debugger/sending-startup-events-after-a-launch.md) listet die Ereignisse auf, die stattfinden, nachdem die DE an das Programm angefügt wurde, bis sich das Programm an seinem Haupteinstiegspunkt befindet und bereit zum Debuggen ist.

 [Steuerung der Ausführung](../../extensibility/debugger/control-of-execution.md) erläutert, wie die DE normalerweise ein Einstiegspunktereignis, ein Ereignis zum Abschluss eines Ladevorgangs oder ein Anhalteereignis abhängig von den jeweiligen Umständen sendet.

 [Binden von Breakpoints](../../extensibility/debugger/binding-breakpoints.md) beschreibt, wie die IDE die Anforderung formuliert und die Debugsitzung auffordert, den Breakpoint zu erstellen, wenn der Benutzer einen Breakpoint festlegt.

 [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md) erläutert, wie Ausdrücke erstellt werden und was geschieht, wenn ein Ausdruck ausgewertet wird.

 [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md) erläutert, wie Typvisualisierungen und benutzerdefinierte Viewer von der Ausdrucksauswertung (Expression Evaluator, EE) unterstützt werden.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) beschreibt die wichtigsten Architekturkonzepte für das Debuggen.

 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md) bietet einen Überblick über die Debugkomponenten von Visual Studio, zu denen die DE, EE und der Symbolhandler (SH) gehören.

 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) erläutert, wie die DE gleichzeitig innerhalb von Code-, Dokumentations- und Ausdrucksauswertungskontexten funktioniert. Es wird für jeden der drei Kontexte der Speicherort, die Position oder die Auswertung beschrieben, der bzw. die für ihn relevant ist.

## <a name="see-also"></a>Weitere Informationen
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
