---
title: Generieren von IEquatable-Operatoren für Strukturen
description: Hier erfahren Sie mehr über die Verwendung des Menüs „Schnellaktionen und Refactorings...“ zum Generieren der Operatoren Equals und IEquatable für Strukturen.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28d70c0ea95c9373eb87e6199d53f1b43fadd508
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617200"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Sie können IEquatable-Operatoren generieren, wenn Sie „Equals“ für Strukturen generieren.

Diese Codegenerierung gilt für:

- C#

**Beschreibung:** Ermöglicht das Generieren der Operatoren **Equals** und **IEquatable** für [Strukturen](/dotnet/csharp/language-reference/builtin-types/struct).

**Hintergrund:** Sie verfügen über eine Struktur, der wir automatisch die Operatoren IEquatable, „Equals“ und „Not equals“ hinzufügen.

**Vorteile**:

- Wenn Sie einen Werttyp implementieren, sollten Sie erwägen, die **Equals**-Methode zu überschreiben, um eine bessere Leistung als mit der Standardimplementierung der Equals-Methode in ValueType zu erzielen.

- Durch die Implementierung der IEquatable-Schnittstelle wird eine typspezifische Equals()-Methode implementiert.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor an einer beliebigen Stelle in der Zeile Ihrer Strukturdeklaration.

2. Führen Sie dann eine der folgenden Aktionen aus:

   - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.

   - Klicken Sie auf die Schaltfläche ![Schraubendrehersymbol](../media/screwdriver-icon.png) am linken Rand

   ![Generieren von IEquatable und Equals für Strukturen](media/generate-equals-structs.png)

3. Wählen Sie im Dropdownmenü **Equals(object) generieren** aus.

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)