---
title: Konvertieren einer LINQ-Abfrage in eine foreach-Anweisung
ms.custom: SEO-VS-2020
description: Führen Sie ein Refactoring für Ihren Code aus, um eine beliebige, in der Abfragesyntax geschriebene LINQ-Abfrage in eine foreach-Anweisung zu konvertieren.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 832c4160d743ca35dbe41eb0f0cbafd81d60dd26
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102545"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refactoring zum Konvertieren von LINQ in eine foreach-Anweisung

Verwenden Sie dieses Refactoring, um die [LINQ-Abfragesyntax](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) in eine [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)-Anweisung zu konvertieren.

Dieses Refactoring gilt für:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Verwendungsweise

1. Wählen Sie die gesamte LINQ-Abfrage aus, die mit `from` beginnt.

   > [!NOTE]
   > Dieses Refactoring kann nur verwendet werden, um LINQ-Abfragen zu konvertieren, die mit der Abfragesyntax ausgedrückt werden, nicht mit der Methodensyntax.

1. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , oder klicken Sie auf den Schraubendreher ![Schraubendrehersymbol](../media/screwdriver-icon.png) im Randbereich der Codedatei.

   ![Menü für schnelle Aktionen zum Konvertieren von LINQ in „foreach“](media/convert-linq-to-foreach.png)

1. Wählen Sie **In "foreach" konvertieren** aus. Wählen Sie alternativ **Vorschau der Änderungen anzeigen** aus, um das Dialogfeld [Vorschau der Änderungen](../../ide/preview-changes.md) anzuzeigen. Klicken Sie dann auf **Anwenden**.

> [!NOTE]
> In C# verwendet der durch diese Refactorings generierte Code entweder einen expliziten Typ oder [var](/dotnet/csharp/language-reference/keywords/var) für die Iterationsvariable der `foreach`-Schleife. Der Typ im generierten Code, unabhängig ob explizit oder implizit, hängt von den Einstellungen des Codeformats für diesen Bereich ab. Diese bestimmten Einstellungen des Codeformats werden auf Computerebene unter **Extras** > **Optionen** > **Text-Editor** > **C#**  > **Codeformat** > **Allgemein** >  **\'var-Einstellungen** oder auf Projektmappenebene in einer [EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types)-Datei konfiguriert. Wenn Sie die Einstellungen des Codeformats in den **Optionen** ändern, müssen Sie die Codedatei erneut öffnen, damit die Änderungen wirksam werden.

## <a name="see-also"></a>Weitere Informationen

- [LINQ](/dotnet/standard/using-linq)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
