---
title: Erstellen von Assert-Klassen und -Methoden für MSTest
description: Erfahren Sie, wie Sie Assert-Anweisungen verwenden, um die Richtigkeit des Verhaltens Ihres Codes bei einem Komponententest des Anwendungscodes zu testen.
ms.custom: SEO-VS-2020
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c5401fb15a19d069c0bf454661d6d9283abb2585
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598197"
---
# <a name="use-assert-classes-for-unit-testing"></a>Verwenden von Assert-Klassen für Komponententests

Verwenden Sie die Assert-Klassen des <xref:Microsoft.VisualStudio.TestTools.UnitTesting>-Namespace, um bestimmte Funktionen zu überprüfen. Eine Komponententestmethode führt den Code einer Methode im Code Ihrer Anwendung aus. Ob sich der Code ordnungsgemäß verhält, wird jedoch nur angegeben, wenn Sie Assert-Anweisungen einbinden.

## <a name="kinds-of-asserts"></a>Arten von Assert-Vorgängen

Der <xref:Microsoft.VisualStudio.TestTools.UnitTesting>-Namespace stellt mehrere Arten von Assert-Klassen bereit.

In Ihrer Testmethode können Sie sämtliche Methoden der Klasse <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> aufrufen, wie z.B. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. Die Klasse <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> stellt eine Vielzahl von Methoden bereit, für die in vielen Fällen mehrere Überladungen vorhanden sind.

### <a name="compare-strings-and-collections"></a>Vergleichen von Zeichenfolgen und Sammlungen

Verwenden Sie die Klasse <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>, um Objektsammlungen zu vergleichen und den Zustand einer Sammlung zu überprüfen.

Verwenden Sie die Klasse <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>, um Zeichenfolgen zu vergleichen und zu überprüfen. Diese Klasse enthält eine Vielzahl von nützlichen Methoden, wie z.B. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> und <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Ausnahmen

Die Ausnahme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> wird immer dann ausgelöst, wenn ein Test fehlschlägt. Ein Test schlägt fehl, wenn eine Zeitüberschreitung auftritt, eine unerwartete Ausnahme ausgelöst wird oder der Test eine Assert-Anweisung enthält, die zum Ergebnis **Fehler** führt.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> wird immer dann ausgelöst, wenn ein Test das Ergebnis **Nicht eindeutig** erzeugt. In der Regel fügen Sie eine <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType>-Anweisung zu einem Test hinzu, an dem Sie noch arbeiten, um anzuzeigen, dass der Test noch nicht zur Ausführung bereit ist.

> [!NOTE]
> Eine andere Möglichkeit besteht darin, einen noch nicht zur Ausführung geeigneten Test mit dem Attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> zu kennzeichnen. Dies hat jedoch den Nachteil, dass Berichte über die Anzahl der noch zu implementierenden Tests nur noch mit einigem Aufwand generiert werden können.

Wenn Sie eine neue Assert-Ausnahmeklasse schreiben, kann die Ausnahme leichter als Assert-Fehler erkannt werden, wenn die Klasse von der Basisklasse <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> erbt. Andernfalls lassen sich Assert-Ausnahmen nicht eindeutig von unerwarteten Ausnahmen unterscheiden, die ggf. durch den Test- oder Produktionscode ausgelöst werden.

Um zu überprüfen, ob eine Ausnahme tatsächlich wie erwartet durch eine Methode in Ihrem Anwendungscode ausgelöst wird, verwenden Sie die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>-Methode.

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
