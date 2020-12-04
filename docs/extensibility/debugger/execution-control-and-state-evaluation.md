---
title: Ausführungs Steuerung und Zustands Auswertung | Microsoft-Dokumentation
description: Erfahren Sie, wie das Visual Studio-debuggen seine Ausführungs Steuerung auf von Debuggerkomponenten gesendeten Ereignissen stützt
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021fab07cfaf1ec17821a8ef9a33a03f2d6ec714
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560901"
---
# <a name="execution-control-and-state-evaluation"></a>Ausführungs Steuerung und Zustands Auswertung
Das Debuggen einer Anwendung erfordert die Implementierung solcher Ausführungs Steuerungsfunktionen als schrittweise Ausführung von Funktionen, Anhalten an Haltepunkten und Fortsetzen der Ausführung. Das Visual Studio-debuggen basiert auf den Ereignissen, die zwischen Debugger-Komponenten gesendet werden

## <a name="in-this-section"></a>In diesem Abschnitt
 [Programmsteuerung](../../extensibility/debugger/program-control.md) Listet die folgenden Routinen auf, die auf der Programmebene auftreten: Festlegen der nächsten Anweisung, ausführen, Schritt-und fortsetzen, anhalten und fortsetzen.

 [Methoden im Zusammenhang mit Breakpoints](../../extensibility/debugger/breakpoint-related-methods.md) Definiert die gebundenen und ausstehenden Typen von Breakpoints, die von Visual Studio unterstützt werden.

 [Auswertung von aufrufstapeln](../../extensibility/debugger/call-stack-evaluation.md) Erläutert die Implementierung der Methoden, die das Anzeigen der Stapel Rahmen der aufzurufenden Stapel Rahmen im Break-Modus ermöglichen.

 [Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Erläutert, wie die Debug-Engine (de), Ausdrucks Auswertung (EE) und Session Debug Manager an der Analyse und Auswertung eines Ausdrucks beteiligt sind, der in eines der Fenster der IDE eingegeben wurde.

 [Steuerelement Ereignisse](../../extensibility/debugger/control-events.md) Erläutert die Schnittstelle, die zum Senden von Ereignissen während der kontrollierten Ausführung des Programms verwendet wird.
