---
title: Konvertieren von typeof in nameof
description: Hier erfahren Sie, wie Sie mit dem Menü „Schnellaktionen und Refactorings“ in Visual Studio „typeof“ in „nameof“ in C# und GetType in NameOf in Visual Basic konvertieren.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce76b82e2ebc68634be7cf4d463f6b8216d81e06
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761198"
---
# <a name="convert-typeof-to-nameof"></a>Konvertieren von `typeof` in `nameof`

Dieses Refactoring gilt für:

- C#
- Visual Basic

**Beschreibung:** Ermöglicht das Konvertieren einer Instanz von `typeof(<QualifiedType>).Name` in `nameof(<QualifiedType>)` in C# und einer Instanz von `GetType(<QualifiedType>).Name` in `NameOf(<QualifiedType>)` in Visual Basic.

**Hintergrund:**  Alle Instanzen von `typeof(<QualifiedType>).Name`, bei denen `someType` kein generischer Typ ist. Dieser Ausschluss ist erforderlich, da in diesem Fall nicht der gleiche Zeichenfolgenwert als `nameof(<QualifiedType>)`zurückgegeben wird. Gleiches gilt für die Visual Basic-Instanz.

**Vorteile**: Die Verwendung von `nameof` anstelle des Namens des `type` vermeidet die Reflexion, die mit dem Abrufen eines `type`-Objekts verbunden ist, und es ist eine pragmatischere Methode der Programmierung.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor innerhalb der `typeof(<QualifiedType>).Name`-Instanz für C# oder in `GetType(<QualifiedType>).Name` in Visual Basic.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

3. Wählen Sie eine der folgenden Optionen aus:

    - C#
      <br>Wählen Sie **Convert 'typeof' to 'nameof'** („typeof“ in „nameof“ konvertieren) aus: ![Screeenshot des Menüs „Schnellaktionen und Refactorings“ in Visual Studio mit ausgewähltem „‘typeof‘ in ‚nameof‘ konvertieren“ und angezeigten C#-Codeänderungen.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Wählen Sie **Convert 'GetType' to 'NameOf'** („GetType“ in „NameOf“ konvertieren) aus: ![Screeenshot des Menüs „Schnellaktionen und Refactorings“ in Visual Studio mit ausgewähltem „‘GetType‘ in ‚NameOf‘ konvertieren“ und angezeigten Visual Basic-Codeänderungen.](media/convert-get-type.PNG)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
