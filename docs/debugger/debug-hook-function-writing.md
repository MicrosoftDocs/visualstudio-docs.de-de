---
title: Schreiben von Hookfunktionen zum Debuggen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 038c976380ff1e1f0a1a7c4c150fc462f6b1d1db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350718"
---
# <a name="debug-hook-function-writing"></a>Schreiben von Hookfunktionen zum Debuggen
In diesem Abschnitt wird eine Reihe von benutzerdefinierten Hookfunktionen zum Debuggen beschrieben, mit denen Code an vordefinierten Punkten in die normalen Verarbeitungsschritte des Debuggers eingefügt werden kann.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Hookfunktionen für Clientblöcke](../debugger/client-block-hook-functions.md): Enthält Anweisungen sowie einen Prototyp für das Schreiben von Funktionen, mit denen der Inhalt der Daten, die in _CLIENT_BLOCK-Blöcken gespeichert werden, überprüft oder dokumentiert wird.

 [Hookfunktionen für Reservierungen](../debugger/allocation-hook-functions.md): Enthält eine Beschreibung einer Hookfunktion für Reservierungen und der unterschiedlichen Verwendung, Hinweise auf Beschränkungen sowie einen Prototyp.

 [Reservierungshooks und CRT-Speicherbelegungen](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md): In diesem Abschnitt wird die für Reservierungshookfunktionen anwendbare Beschränkung beschrieben, nach der `_CRT_BLOCK`-Blöcke explizit ignoriert werden, wenn sie C-Laufzeitbibliotheksfunktionen aufrufen, durch die interner Speicher belegt wird. Hier wird außerdem beschrieben, welche Konsequenzen es hat, wenn der Zuweisungshook `_CRT_BLOCK`-Blöcke nicht ignoriert (einschließlich Beispielen), und wie Sie die standardmäßige Zuweisungshookfunktion **CrtDefaultAllocHook** ändern.

 [Hookfunktionen für Berichte](../debugger/report-hook-functions.md): Hier wird die `_CrtSetReportHook`-Funktion beschrieben, mit der Sie Berichte nach bestimmten Reservierungstypen filtern können. In diesem Thema finden Sie außerdem einen Prototyp.

## <a name="related-sections"></a>Verwandte Abschnitte

- [CRT-Debugtechniken](../debugger/crt-debugging-techniques.md): Enthält Links zu Debugtechniken für die C-Laufzeitbibliothek, darunter Verwenden der CRT-Debugbibliothek, Makros für die Berichterstellung, Unterschiede zwischen `malloc` und `_malloc_dbg`, Schreiben von Hookfunktionen für das Debuggen und CRT-Debugheap.