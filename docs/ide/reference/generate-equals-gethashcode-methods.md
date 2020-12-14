---
title: Generieren der Equals- und GetHashCode-Methodenüberschreibungen in C#
description: Hier erfahren Sie mehr über die Verwendung des Menüs „Schnellaktionen und Refactorings...“ zum Generieren von Equals- und GetHashCode-Methoden.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f6f7ec74af21ef62079a3fef18dd39544e7b42aa
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617512"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generieren der Überschreibungsmethoden „Equals“ und „GetHashCode“ in Visual Studio

Diese Codegenerierung gilt für:

- C#

**Beschreibung**: Ermöglicht das Generieren von **Equals**- und **GetHashCode**-Methoden.

**Hintergrund**: Generieren Sie diese Überschreibungsmethoden, wenn Sie einen Typ haben, der durch ein Feld oder mehrere Felder verglichen werden soll, anstelle des Objektspeicherorts im Arbeitsspeicher.

**Vorteile**:

- Wenn Sie einen Werttyp implementieren, sollten Sie erwägen, die **Equals**-Methode zu überschreiben, um eine bessere Leistung als mit der Standardimplementierung der Equals-Methode in ValueType zu erzielen.

- Wenn Sie einen Verweistyp implementieren, sollten Sie erwägen, die **Equals**-Methode zu überschreiben, wenn der Typ wie ein Basistyp aussieht, z.B. Point, String, BigNumber usw.

- Überschreiben Sie die **GetHashCode**-Methode, damit ein Typ in einer Hashtabelle ordnungsgemäß funktioniert. Informieren Sie sich weiter über [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in der Zeile Ihrer Typdeklaration an einer beliebigen Stelle.

   ![Markierter Code](media/overrides-highlight-cs.png)

   > [!TIP]
   > Doppelklicken Sie nicht auf den Typnamen. Andernfalls ist die Menüoption nicht verfügbar. Platzieren Sie den Cursor einfach an einer beliebigen Stelle in der Zeile.

1. Führen Sie dann eine der folgenden Aktionen aus:

   - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.

   - Klicken Sie auf die Schaltfläche ![Schraubendrehersymbol](../media/screwdriver-icon.png) am linken Rand

   ![Generieren von Überschreibungen – Vorschau](media/overrides-preview-cs.png)

1. Klicken Sie im Dropdownmenü auf **„Equals(object)“ generieren** oder **„Equals“ und „GetHashCode“ generieren**.

1. Wählen Sie die Mitglieder, für die Sie die Methoden generieren wollen, im Dialogfeld **Member auswählen** aus:

    ![Generieren von Überschreibungen – Dialogfeld](media/overrides-dialog-cs.png)

    > [!TIP]
    > In diesem Dialogfeld können Sie auch über das entsprechende Kontrollkästchen unten im Dialogfeld die Generierung von Operatoren auswählen.

   Die Methoden `Equals` und `GetHashCode` werden mit Standardimplementierungen generiert.

   ![Ergebnis der Aktion zum Generieren einer Methode](media/overrides-result-cs.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
