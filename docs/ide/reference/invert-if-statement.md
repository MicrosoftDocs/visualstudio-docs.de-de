---
title: Umkehren von if-Anweisungen
description: Hier erfahren Sie, wie Sie über das Menü „Schnellaktionen und Refactorings...“ eine if- oder if-else-Anweisung umkehren, ohne die Bedeutung des Codes zu ändern.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 71b3a11e053b6a600d0b33db7c52a91c4950bf5b
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616979"
---
# <a name="invert-if-statement"></a>Umkehren von if-Anweisungen

Dieses Refactoring gilt für:

- C#
- Visual Basic

**Beschreibung:** Ermöglicht Ihnen das Umkehren einer `if`- oder `if else`-Anweisung, ohne die Bedeutung des Codes zu ändern.

**Hintergrund:** Wenn Sie über eine `if`- oder `if else`-Anweisung verfügen, die verständlicher wäre, wenn sie umgekehrt wäre.

**Vorteile**: Das manuelle Umkehren einer `if`- oder `if else`-Anweisung kann sehr viel länger dauernd und Fehler verursachen. Dieser Codefix unterstützt Sie dabei, dieses Refactoring automatisch durchzuführen.

## <a name="invert-if-statement-refactoring"></a>Refactoring: Invertieren von if-Anweisungen

1. Platzieren Sie den Cursor in einer `if`- oder `if else`-Anweisung.

    ![if else-Anweisung umkehren](media/invert-if.png)

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

    ![Codefix zum Umkehren einer if else-Anweisung](media/invert-if-codefix.png)

3. Wählen Sie **if umkehren** aus.

    ![Ergebnis des Umkehrens einer if else-Anweisung](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../csharp-developer-productivity.md)
