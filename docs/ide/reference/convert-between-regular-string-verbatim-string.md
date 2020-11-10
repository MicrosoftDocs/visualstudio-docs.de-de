---
title: Konvertierung zwischen regulären und ausführlichen Zeichenfolgenliteralen
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f411c0ac56adeb30370cbfc6f0f908ffd25bed05
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045899"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>Refactoring in Form des Konvertierens zwischen regulären und ausführlichen Zeichenfolgenliteralen

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Ermöglicht das Konvertieren zwischen regulären und ausführlichen Zeichenfolgenliteralen.

**Hintergrund:** Sie möchten entweder Speicherplatz sparen oder für mehr Klarheit im Code sorgen.

**Vorteile** : Durch das Konvertieren eines ausführlichen Zeichenfolgenliterals in ein reguläres können Sie Speicherplatz sparen. Durch das Konvertieren eines regulären Zeichenfolgenliterals in ein ausführliches können Sie für mehr Klarheit sorgen.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie die Einfügemarke entweder im regulären oder ausführlichen Zeichenfolgenliteral:

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

3. Wählen Sie eine der folgenden Optionen aus:

    Klicken Sie auf **In reguläre Zeichenfolge konvertieren**.

    ![In reguläre Zeichenfolge konvertieren](media/convert-to-regular-string.png)

    Klicken Sie auf **In ausführliche Zeichenfolge konvertieren**.

    ![In ausführliche Zeichenfolge konvertieren](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)