---
title: Refactoring von Code zum Ersetzen von var durch einen expliziten Typ
description: Hier erfahren Sie, wie Sie var mithilfe von Schnellaktionen in einem lokalen variablen Ausdruck durch einen expliziten Typ ersetzen können.
ms.custom: SEO-VS-2020
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d45d4ffcbdedb456bde40b3fd1103fa8b21a8f9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919589"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refactoring zum Ersetzen von var durch einen expliziten Typ

Mithilfe dieses Refactorings können Sie [var](/dotnet/csharp/language-reference/keywords/var) in einer lokalen Variablendeklaration mit einem expliziten Typ ersetzen.

Dieses Refactoring gilt für:

- C#

## <a name="why-to-use-an-explicit-type"></a>Gründe für die Verwendung eines expliziten Typs

Hier finden Sie einige Gründe für das Deklarieren einer Variable mit einem expliziten Typ:

- Bessere Lesbarkeit des Codes

- Wenn die Variable nicht in der Deklaration initialisiert werden soll

[var](/dotnet/csharp/language-reference/keywords/var) muss jedoch verwendet werden, wenn eine Variable mit einem anonymen Typ initialisiert wird und wenn Sie zu einem späteren Zeitpunkt auf die Eigenschaften des Objekts zugreifen möchten. Weitere Informationen finden Sie unter [Implizit typisierte lokale Variablen (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Verwendungsweise

1. Fügen Sie die Einfügemarke in das `var`-Schlüsselwort ein.

1. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , oder klicken Sie auf den Schraubendreher ![Schraubendrehersymbol](../media/screwdriver-icon.png) im Randbereich der Codedatei.

   ![Verwenden des Menüs für schnelle Aktionen für den expliziten Typ](media/use-explicit-type.png)

1. Wählen Sie **Expliziten Typ verwenden** aus. Wählen Sie alternativ **Vorschau der Änderungen anzeigen** aus, um das Dialogfeld [Vorschau der Änderungen](../../ide/preview-changes.md) anzuzeigen. Klicken Sie dann auf **Anwenden**.

## <a name="see-also"></a>Siehe auch

- [Implizit typisierte Variablen (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
