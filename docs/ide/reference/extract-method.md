---
title: Extrahieren einer Methode
description: Wandeln Sie ein Codefragment in eine eigene Methode um, indem Sie den Code auswählen und STRG+R, STRG+M drücken.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 21f6ac868268c40ea6df837596546f86fd9a3a44
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129470"
---
# <a name="extract-a-method-refactoring"></a>Refactoring des Extrahierens einer Methode

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie ein Codefragment in eine eigene Methode umwandeln.

**Hintergrund**: Sie verwenden ein Fragment von vorhandenem Code in einer Methode, die von einer anderen Methode aufgerufen werden muss.

**Vorteile**: Sie könnten diesen Code kopieren und einfügen, dies würde jedoch zu einer Duplizierung führen. Eine bessere Lösung wäre es, dieses Fragment in eine eigene Methode umzugestalten, die von anderen Methoden beliebig aufgerufen werden kann.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den zu extrahierenden Code:

   - C#:

       !Screenshot: C#-Code für die Program-Klasse mit einer hervorgehobenen Codezeile in der Main-Funktion](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Screenshot: Visual Basic-Code für Main Sub mit einer hervorgehobenen Codezeile](media/extractmethod-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie **STRG+R** und dann **STRG+M**. (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Methode extrahieren** aus.
   - **Maus**
      - Wählen Sie **Bearbeiten > Umgestalten > Methode extrahieren** aus.
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie **Umgestalten > Extrahieren > Methode extrahieren**.
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Methode extrahieren** aus.

   Die Methode wird sofort erstellt. In dieser Ansicht können Sie nun die Methode umbenennen, indem Sie einfach den neuen Namen eingeben.

   > [!TIP]
   > Sie können auch Kommentare und andere Zeichenfolgen vor dem Speichern mit diesem neuen Namen aktualisieren sowie eine [Vorschau der Änderungen](../../ide/preview-changes.md) anzeigen, indem Sie oben rechts in der IDE die jeweiligen Kontrollkästchen im Feld **Umbenennen** aktivieren.

   - C#:

      ![!Screenshot: C#-Code für die Program-Klasse mit einem hervorgehobenen Methodennamen und dem Popupfenster „Umbenennen“ geöffnet](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Screenshot: Visual Basic-Code für Main Sub mit einem hervorgehobenen Methodennamen und dem Popupfenster „Umbenennen“ geöffnet](media/extractmethod-rename-vb.png)

3. Wenn Sie mit der Änderung zufrieden sind, klicken Sie auf die Schaltfläche **Übernehmen**, oder drücken Sie die **EINGABETASTE**. Die Änderungen werden angewendet.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
