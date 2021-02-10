---
title: Ersetzen einer temporären Variable durch ihren Wert
description: Hier erfahren Sie, wie Sie über das Menü „Schnellaktionen und Refactorings...“ eine temporäre Variable entfernen und durch ihren Wert ersetzen.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ebe062d5dd569ae1d2162ea7334f91d8b82decdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852374"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Inlinesetzen eines temporären Variablenrefactorings

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie eine temporäre Variable entfernen und diese stattdessen durch ihren Wert ersetzen.

**Hintergrund**: Durch die Verwendung der temporären Variable ist der Code schwieriger zu verstehen.

**Vorteile**: Durch das Entfernen einer temporären Variablen kann die Lesbarkeit des Codes verbessert werden.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie die inline zu setzende temporäre Variable, oder platzieren Sie den Textcursor in die Variable:

   - C#:

       ![Hervorgehobener Code – C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code – Visual Basic](media/inline-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus.

3. Wählen Sie im Popupvorschaufenster **Inline temporär variabel** aus.

   Die Variable wird entfernt und sofort durch ihren Wert ersetzt.

   - C#:

      ![Ergebnis des Inlinevorgangs in C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Ergebnis des Inlinevorgangs in Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
