---
title: Vereinfachen von LINQ-Ausdrücken
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 006fc0fe84b11573ece98019a4446d83de52d62c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957555"
---
# <a name="simplify-linq-expression"></a>Vereinfachen von LINQ-Ausdrücken

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Führt Refactoring von Instanzen von `SomeEnumerableType.Where(<LambdaExpression>).Single()` in `SomeEnumerable.Single(<LambdaExpression>)` für `Enumerable.Single()` sowie die folgenden Enumerable-Methoden aus: `SingleOrDefault()`, `Last()`, `LastOrDefault()`, `Any()`, `Count()`, `First()` und `FirstOrDefault()`.

**Hintergrund:**  Alle Instanzen, in denen die Methode `Single()`, `SingleOrDefault()` usw. aufruft, besitzen keine Argumente, und ihnen wird ein `Where()`-Ausdruck vorangestellt. Die Eingabe für den `Where()`-Ausdruck kann nicht als Ausdrucksbaumstruktur erstellt werden.

**Vorteile**: Wenn Sie den nicht erforderlichen Aufruf von Enumerable für die `.Where()`-Methode entfernen, werden Leistung und Lesbarkeit verbessert.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor innerhalb der `SomeEnumerableType.Where(<LambdaExpression>).Single()`-Instanz in Visual Studio.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **LINQ-Ausdruck vereinfachen** aus.

   ![Konvertieren von typeof in nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
