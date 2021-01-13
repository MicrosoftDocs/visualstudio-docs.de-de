---
title: Debuggen von F# | Microsoft-Dokumentation
description: Hier finden Sie eine Liste der Unterschiede zwischen dem Debuggen von F# und dem Debuggen anderer verwalteter Sprachen in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2dcacff924386cc279708c34d2232e50aa92c55
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728420"
---
# <a name="debugging-f"></a>Debuggen von F\#
Das Debuggen von F# entspricht mit wenigen Ausnahmen dem Debuggen einer verwalteten Sprache:

- Das Fenster **Auto** zeigt keine F#-Variablen an.

- Bearbeiten und Fortfahren wird für F# nicht unterstützt. Das Bearbeiten von F#-Code während einer Debugsitzung ist möglich, sollte aber vermieden werden. Da Codeänderungen während der Debugsitzung nicht übernommen werden, verursacht das Bearbeiten von F#-Code während des Debuggens einen Konflikt zwischen dem Quellcode und dem gedebuggten Code.

- Der Debugger erkennt keine F#-Ausdrücke. Übersetzen Sie den Ausdruck in C#-Syntax, um während des F#-Debuggings einen Ausdruck in ein Debuggerfenster oder Dialogfeld einzugeben. Beachten Sie beim Übersetzen eines F#-Ausdrucks in C#, dass C# == als Vergleichsoperator für Gleichheit und F# ein einzelnes = verwendet.

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
