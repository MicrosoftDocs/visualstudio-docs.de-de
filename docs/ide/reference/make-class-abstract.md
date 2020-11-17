---
title: Festlegen einer Klasse als abstrakt
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8bfcaa7117249ceffbaed706ac420c5250c02089
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403522"
---
# <a name="make-class-abstract"></a>Festlegen einer Klasse als abstrakt

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hierbei handelt es sich um ein Refactoring zum Festlegen einer Klasse als abstrakt.

**Hintergrund:** Sie schreiben eine abstrakte Methode in einer Klasse, die nicht abstrakt ist.

**Vorteile**:  Mit einer Codekorrektur zum Festlegen einer Klasse als abstrakt, nachdem Sie eine abstrakte Methode geschrieben haben, sparen Sie Zeit.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie das Caretzeichen in der abstrakten Methode.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

3. Klicken Sie auf **Make class 'abstract'** (Klasse als abstrakt festlegen).

    ![Festlegen einer Klasse als abstrakt](media/make-class-abstract.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
