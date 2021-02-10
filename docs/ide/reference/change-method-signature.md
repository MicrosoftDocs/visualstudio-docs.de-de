---
title: Ändern der Methodensignatur
description: Informationen zum Hinzufügen und Entfernen von Parametern einer Methode oder Ändern ihrer Reihenfolge. Klicken Sie mit der rechten Maustaste auf eine Methode, wählen Sie „Schnelle Aktionen“ und anschließend „Refactorings“ aus, und klicken Sie auf „Signatur ändern“.
ms.date: 07/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 01acbab7725effff5b2edbf8a80ab4f115fd2eff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935845"
---
# <a name="change-a-method-signature-refactoring"></a>Ändern einer Methodensignatur durch Refactoring

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit können Sie Parameter einer Methode entfernen oder deren Reihenfolge ändern.

**Hintergrund:** Sie möchten einen Methodenparameter verschieben oder entfernen, der gegenwärtig an vielen Stellen verwendet wird.

**Vorteile**: Sie könnten die Parameter manuell entfernen und neu anordnen und anschließend alle Aufrufe dieser Methode suchen und nacheinander ändern, was jedoch Fehler verursachen könnte.  Bei diesem Refactoringtool wird der Task automatisch ausgeführt.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den Namen der zu ändernden Methode oder eines ihrer Vorkommen, oder platzieren Sie den Textcursor in den Namen:

   - C#:

       ![Hervorgehobener Code – C#](media/changesignature-highlight-cs.png)

   - VB:

       ![Hervorgehobener Code in Visual Basic](media/changesignature-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie **STRG+R** und dann **STRG+V**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Signatur ändern** aus.
   - **Maus**
      - Wählen Sie **Bearbeiten > Umgestalten > Parameter entfernen** aus.
      - Wählen Sie **Bearbeiten > Umgestalten > Parameter neu anordnen** aus.
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Signatur ändern** aus.

3. Mit den Schaltflächen auf der rechten Seite im angezeigten Dialogfeld **Signatur ändern** können Sie die Methodensignatur ändern:

   ![Dialogfeld „Signatur ändern“](media/change-signature.png)

   | Schaltfläche | Beschreibung
   | ------ | ---
   | **Nach oben/unten** | Den ausgewählten Parameter in der Liste nach oben oder nach unten verschieben
   | **Add** | Einen neuen Parameter zur Liste hinzufügen
   | **Entfernen** | Den ausgewählten Parameter aus der Liste entfernen
   | **Wiederherstellen** | Den ausgewählten, durchgestrichenen Parameter in der Liste wiederherstellen

   > [!TIP]
   > Aktivieren Sie das Kontrollkästchen **Vorschau der Verweisänderungen**, um vor einer endgültigen Änderung das [Ergebnis zu sehen](../../ide/preview-changes.md).

4. Durch Auswählen von **Hinzufügen** im Dialogfeld **Signatur ändern** wird das Dialogfeld **Parameter hinzufügen** geöffnet. Mit dem Dialogfeld **Parameter hinzufügen** können Sie einen Typnamen und einen Parameternamen hinzufügen. Sie können mit einem Standardwert festlegen, ob der Parameter erforderlich oder optional ist. Sie können dann auf der Aufrufsite einen Wert hinzufügen und ein benanntes Argument für diesen Wert auswählen, oder Sie können eine TODO-Variable einführen. Die TODO-Variable fügt ein TODO in Ihren Code ein, sodass Sie jeden Fehler untersuchen und jede Aufrufsite unabhängig durchlaufen und entscheiden können, was übergeben werden soll. Für optionale Parameter besteht die Möglichkeit, die Aufrufsite vollständig auszulassen.

    ![Dialogfeld „Parameter hinzufügen“: C#](media/add-parameter-dialog.png)

5. Wenn Sie mit dem Hinzufügen eines Parameters fertig sind, klicken Sie auf die Schaltfläche **OK**, um eine Vorschau der Änderungen anzuzeigen.

    ![Dialogfeld „Signatur ändern“](media/change-signature.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)