---
title: Verwenden von „new()“
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b2091c046efac9f5676e5d2d99ef798283b95f6e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403527"
---
# <a name="use-new"></a>Verwenden Sie `new()`

Dies gilt für:

- C#

**Beschreibung:** Verwenden Sie `new()`.

**Hintergrund:** Sie verfügen über ein Feld, das `var` nicht verwenden kann, oder bevorzugen das Codeformat ohne `var`.

**Vorteile**: Mithilfe dieses Refactorings müssen Sie keinen sich wiederholenden Code mit doppelter Eingabe schreiben.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie das Caretzeichen in der Felddeklaration.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

3. Wählen Sie die Option **Use 'new(…)'** aus.

    ![Option „Use 'new(...)'“](media/use-new.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
