---
title: Konvertieren von typeof in nameof
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
ms.openlocfilehash: 96bd4d67302fb09e5c1cb7837ad73b345ad88c81
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400323"
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
      <br>Wählen Sie **Convert 'typeof' to 'nameof'** („typeof“ in „nameof“ konvertieren) aus: ![„typeof“ in „nameof“ konvertieren](media/convert-type-of.PNG)

    - Visual Basic
      <br>Wählen Sie **Convert 'GetType' to 'NameOf'** („GetType“ in „NameOf“ konvertieren) aus: ![„typeof“ in „nameof“ konvertieren](media/convert-get-type.PNG)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
