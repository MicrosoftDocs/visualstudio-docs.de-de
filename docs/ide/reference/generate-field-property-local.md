---
title: Generieren eines Felds, einer Eigenschaft oder einer lokalen Variablen
description: Hier erfahren Sie, wie Sie über das Menü „Schnellaktionen und Refactorings...“ den Code für ein zuvor nicht deklariertes Feld oder eine zuvor nicht deklarierte Eigenschaft oder lokale Variable generieren.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ebce688317a04bdc223659fb0c085b2f0223119d
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617499"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Generieren eines Felds, einer Eigenschaft oder einer lokalen Variablen in Visual Studio

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung**: Sie können sofort Code für ein Feld, eine Eigenschaft oder ein lokales Element generieren, das bzw. die zuvor nicht deklariert war.

**Hintergrund**: Sie führen während der Eingabe ein neues Feld, eine neue Eigenschaft oder ein neues lokales Element ein und möchten dieses bzw. diese automatisch deklarieren.

**Vorteile**: Sie könnten das Feld, die Eigenschaft oder das lokale Element zwar vor der Verwendung deklarieren, dieses Feature generiert Deklaration und Typ jedoch automatisch.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf der Zeile, in der eine rote Wellenlinie angezeigt wird. Die rote Wellenlinie weist auf ein Feld, ein lokales Element oder eine Eigenschaft hin, die noch nicht vorhanden sind.

   - C#:

       ![Hervorgehobener Code – C#](media/field-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code in Visual Basic](media/field-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
      - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
      - Zeigen Sie auf die rote Wellenlinie, und klicken Sie auf das ![Fehlerglühbirnensymbol](media/error-bulb.png) das angezeigt wird.
      - Klicken Sie auf die Schaltfläche ![Fehlerglühbirnensymbol](media/error-bulb.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der roten Wellenlinie platziert wurde.

      ![Feld/Eigenschaft/Lokales Element generieren – Vorschau](media/field-preview-cs.png)

3. Klicken Sie im Dropdownmenü auf eine der folgenden Generierungsoptionen.

   > [!TIP]
   > Klicken Sie im unteren Bereich des Vorschaufensters auf den Link **Vorschau der Änderungen**, um vor einer Auswahl [alle Änderungen anzuzeigen](../../ide/preview-changes.md), die vorgenommen werden.

   Das Feld, die Eigenschaft bzw. das lokale Element wird mit dem aus der Verwendung abgeleiteten Typ erstellt.

   - C#:

       ![Ergebnis der Methodengenerierung in C#](media/field-result-cs.png)

   - Visual Basic:

       ![Ergebnis der Methodengenerierung in Visual Basic](media/field-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
