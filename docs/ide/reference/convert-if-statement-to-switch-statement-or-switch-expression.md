---
title: Konvertieren einer if-Anweisung in eine switch-Anweisung oder einen switch-Ausdruck
description: Hier erfahren Sie, wie Sie mit dem Menü „Schnellaktionen und Refactorings…“ eine if-Anweisung in eine switch-Anweisung oder einen switch-Ausdruck aus C# 8.0 konvertieren.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e19314b8bf73f5859fdf2cef7d281f142c643b68
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305553"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Konvertieren der if-Anweisung in eine switch-Anweisung

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Konvertieren einer if-Anweisung in eine [switch-Anweisung](/dotnet/csharp/language-reference/keywords/switch) oder in einen C#-8.0-[switch-Ausdruck](/dotnet/csharp/whats-new/csharp-8#switch-expressions)

**Hintergrund:** Sie möchten eine `if`-Anweisung in einen `switch`-Ausdruck oder einen `switch`-Ausdruck und umgekehrt konvertieren.

**Vorteile**: Wenn Sie nur `if`-Ausdrücke verwenden, ermöglicht dieses Refactoring einen einfachen Übergang zu `switch`-Anweisungen oder `switch`-Ausdrücken.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor im Schlüsselwort `if`.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie eine der folgenden beiden Optionen aus:

    Klicken Sie auf **In switch-Anweisung konvertieren**.

   ![Konvertieren von if-Anweisung in switch-Anweisung](media/convert-if-to-switch-statement.png)

    Klicken Sie auf **In switch-Ausdruck konvertieren**.

    ![Konvertieren von if-Anweisung in switch-Ausdruck](media/convert-if-to-switch-expression.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
