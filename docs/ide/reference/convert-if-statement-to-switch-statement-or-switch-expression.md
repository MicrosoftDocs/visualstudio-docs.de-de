---
title: Konvertieren einer if-Anweisung in eine switch-Anweisung oder einen switch-Ausdruck
description: Hier erfahren Sie, wie Sie mit dem Menü „Schnellaktionen und Refactorings…“ eine if-Anweisung in eine switch-Anweisung oder einen switch-Ausdruck aus C# 8.0 konvertieren.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0d857338eb1c9b5bb66ccb89e20e6f892944d608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936828"
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
