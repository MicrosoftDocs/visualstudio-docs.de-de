---
title: Generieren einer Methodenüberschreibung
description: Hier erfahren Sie, wie Sie sofort den Code für eine Methode generieren, die von einer Basisklasse überschrieben werden kann.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f27adacc39c53bf46b3a2ee09c71ae27b47f928
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617486"
---
# <a name="generate-an-override-in-visual-studio"></a>Generieren einer Überschreibung in Visual Studio

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung**: Sie können sofort Code für eine Methode generieren, die von einer Basisklasse überschrieben werden kann.

**Hintergrund**: Sie möchten eine Basisklassenmethode überschreiben und die Signatur automatisch generieren.

**Vorteile**: Sie könnten die Methodensignatur selbst schreiben – dieses Feature generiert die Signatur jedoch automatisch.

## <a name="how-to"></a>Vorgehensweise

1. Schreiben Sie `override` in C# oder `Overrides` in Visual Basic, gefolgt von einem Leerzeichen, an der Stelle, an der Sie eine Überschreibungsmethode einfügen möchten.

   - C#:

      ![Überschreiben mit IntelliSense in C#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Überschreiben mit IntelliSense in Visual Basic](media/override-intellisense-vb.png)

2. Wählen Sie die zu überschreibende Methode aus der Basisklasse.

   > [!TIP]
   > - Verwenden Sie das Eigenschaftssymbol, ![Eigenschaftssymbol](media/override-property-cs.png) um Eigenschaften in der Liste anzuzeigen oder auszublenden.
   > - Verwenden Sie das Methodensymbol, ![Methodensymbol](media/override-method-cs.png) um Methoden in der Liste anzuzeigen oder auszublenden.

   Die ausgewählte Methode oder Eigenschaft wird der Klasse als Überschreibung hinzugefügt und steht für die Implementierung zur Verfügung.

   - C#:

       ![Ergebnis der Überschreibung in C#](media/override-result-cs.png)

   - Visual Basic:

       ![Ergebnis der Überschreibung in Visual Basic](media/override-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
