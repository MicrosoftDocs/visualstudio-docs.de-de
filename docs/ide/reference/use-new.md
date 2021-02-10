---
title: Verwenden von „new()“
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a129e94f6009eec51995b6a4e170f0a804e6407f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889810"
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
