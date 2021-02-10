---
title: switch-Anweisung in switch-Ausdruck konvertieren
description: Hier erfahren Sie, wie Sie mit dem Menü „Schnellaktionen und Refactorings…“ eine switch-Anweisung in einen switch-Ausdruck aus C# 8.0 konvertieren.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 56a1b20854cdd2c1821490bb4972d67bbe912056
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919665"
---
# <a name="convert-switch-statement-to-switch-expression"></a>switch-Anweisung in switch-Ausdruck konvertieren

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Hiermit wird eine [switch-Anweisung](/dotnet/csharp/language-reference/keywords/switch) in einen [switch-Ausdruck](/dotnet/csharp/whats-new/csharp-8#switch-expressions) von C# 8.0 konvertiert.

**Hintergrund:** Sie möchten eine `switch`-Anweisung in einen `switch`-Ausdruck und umgekehrt konvertieren. 

**Vorteile**: Wenn Sie nur Ausdrücke verwenden, ermöglicht dieses Refactoring einen einfachen Wechsel von herkömmlichen `switch`-Anweisungen.

## <a name="how-to"></a>Vorgehensweise

1. Legen Sie in der Projektdatei die [Sprachversion auf „Vorschau“ fest](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file), da `switch`-Ausdrücke ein neues C# 8.0-Feature sind.
2. Platzieren Sie den Cursor im Schlüsselwort `switch`, und drücken Sie **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **switch-Anweisung in switch-Ausdruck konvertieren** aus.

   ![switch-Anweisung in switch-Ausdruck konvertieren](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
