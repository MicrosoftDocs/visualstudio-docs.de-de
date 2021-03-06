---
title: Invertieren von bedingten Ausdrücken und logischen Operationen
description: Hier erfahren Sie mehr über die Verwendung des Menüs „Schnellaktionen und Refactorings...“ zum Umkehren eines bedingten Ausdrucks oder eines bedingten AND-/OR-Operators.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0bd75a40f52a6148a6c50b212183bb8dc7a52d56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852244"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Invertieren von bedingten Ausdrücken und bedingten UND/ODER-Operatoren

Dieses Refactoring gilt für:

- C#
- Visual Basic

**Beschreibung:** Ermöglicht das Invertieren von bedingten Ausdrücken oder bedingten UND/ODER-Operatoren.

**Hintergrund:** Sie haben einen bedingten Ausdruck oder einen bedingten UND/ODER-Operator, der in invertierter Form besser verstanden würde.

**Vorteile**: Einen Ausdruck oder einen bedingten UND/ODER-Operator manuell zu invertieren ist zeitaufwändiger. Außerdem könnten dabei Fehler eingeführt werden. Dieser Codefix unterstützt Sie dabei, dieses Refactoring automatisch durchzuführen.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Umkehren von bedingten Ausdrücken und Refactoring von bedingten UND/ODER-Operatoren

1. Platzieren Sie Ihren Cursor in einen bedingten Ausdruck oder einen bedingten UND/ODER-Operator.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **Invert conditional** (Bedingung invertieren) aus oder **ersetzen Sie '&&' mit '||'**.

    ![Screenshot: Option „Bedingten Operator umkehren“](media/invert-conditional.png)

    ![Screenshot: Option „Replace && with ||“ (Ersetzen von && durch ||)](media/invert-logical-operator.png)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../csharp-developer-productivity.md)
