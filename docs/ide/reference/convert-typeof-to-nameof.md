---
title: Konvertieren von typeof in nameof
description: Hier erfahren Sie, wie Sie mit dem Menü „Schnellaktionen und Refactorings“ in Visual Studio „typeof“ in „nameof“ in C# und GetType in NameOf in Visual Basic konvertieren.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f93c5232f852e1390eac9e2ebb57235abc5e1f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919695"
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
