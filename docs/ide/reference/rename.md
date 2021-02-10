---
title: Refactoring des Umbenennens
description: 'Hier erfahren Sie, wie Sie mit dem Feature „Refactoring: Umbenennen“ Bezeichner für Codesymbole (z. B. Felder, lokale Variablen, Methoden, Namespaces, Eigenschaften und Typen) umbenennen.'
ms.custom: SEO-VS-2020
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2e3d4d5d0abc335cfb857e5a4de9c5189a1ca5cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958101"
---
# <a name="rename-a-code-symbol-refactoring"></a>Refactoring des Umbenennens eines Codesymbols

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit können Sie Bezeichner für Codesymbole (z. B. Felder, lokale Variablen, Methoden, Namespaces, Eigenschaften und Typen) umbenennen.

**Hintergrund:** Sie möchten ein Element sicher umbenennen, ohne alle Instanzen suchen und den neuen Namen kopieren und einfügen zu müssen.

**Vorteile**: Das Kopieren und Einfügen des neuen Namens in ein ganzes Projekt würde wahrscheinlich zu Fehlern führen. Dieses Refactoringtool führt die Umbenennungsaktion ordnungsgemäß durch.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den Namen des umzubenennenden Elements, oder platzieren Sie den Textcursor in das Element:

   - C#:

       ![Hervorgehobener Code – C#](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code – Visual Basic](media/rename-highlight-vb.png)

2. Verwenden Sie nun die Tastatur oder Maus wie folgt:

   - **Tastatur**
      - Drücken Sie **STRG+R** und dann **STRG+R**. (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
   - **Maus**
      - Wählen Sie **Bearbeiten > Umgestalten > Umbenennen** aus.
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie **Umbenennen** aus.

3. Benennen Sie das Element einfach um, indem Sie den neuen Namen eingeben.

   - C#:

      ![Animation des Umbenennungsvorgangs – C#](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Umbenennung – Visual Basic](media/rename-rename-vb.png)

   > [!TIP]
   > Sie können auch Kommentare und andere Zeichenfolgen vor dem Speichern mit diesem neuen Namen aktualisieren sowie eine [Vorschau der Änderungen](../../ide/preview-changes.md) anzeigen, indem Sie oben rechts im Editor die jeweiligen Kontrollkästchen im Feld **Umbenennen** aktivieren.

4. Wenn Sie mit der Änderung zufrieden sind, klicken Sie auf die Schaltfläche **Übernehmen**, oder drücken Sie die **EINGABETASTE**. Die Änderungen werden angewendet.

## <a name="remarks"></a>Hinweise

- Wenn Sie ab Visual Studio 2019 Version 16.3 einen Typ umbenennen, der mit dem Namen der Datei übereinstimmt, in der er sich befindet, wird ein Kontrollkästchen angezeigt, mit dem Sie die Datei zur gleichen Zeit umbenennen können. Diese Option wird angezeigt, wenn Sie eine Klasse, eine Schnittstelle oder eine Enumeration umbenennen. Diese Option wird für partielle Typen mit mehreren Definitionen nicht unterstützt.

   ![Umbenennen einer Animation mit Datei: C#](media/rename-with-file-animated-cs.gif)

- Wenn Sie einen bereits vorhandenen Namen verwenden, der zu einem Konflikt führen würde, werden Sie durch das Feld **Umbenennen** darüber informiert.

   ![Umbenennungskonflikt](media/rename-conflict-cs.png)

- Eine andere Möglichkeit zum Umbenennen eines Symbols besteht darin, den Namen des Symbols im Editor zu ändern. Wenn sich der Cursor auf dem Symbolnamen befindet, drücken Sie **STRG**+ **.** Alternativ dazu können Sie auch einfach das Menü mit dem Glühbirnensymbol erweitern und **Umbenennen von \<old name> in \<new name>** auswählen.

   ![Umbenennen im Editor](media/rename-with-editor-cs.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
