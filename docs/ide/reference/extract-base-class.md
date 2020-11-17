---
title: Extrahieren einer Basisklasse
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
ms.openlocfilehash: 8eb87ff8e3acc141c49a495b155fb769e03fb89b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403515"
---
# <a name="extract-base-class"></a>Extrahieren einer Basisklasse

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hierbei handelt es sich um ein Refactoring für das Extrahieren der Basisklasse.

**Hintergrund:** Sie möchten Member aus einer ausgewählten Klasse in eine neue Basisklasse extrahieren.

**Vorteile**: Das manuelle Abrufen von Membern kann zeitaufwändig sein und Ihren Workflow unterbrechen. 

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihr Caretzeichen entweder im Klassennamen oder in einem hervorgehobenen Member.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

3. Wählen Sie **Member auf neue Basisklasse ziehen** aus.

    ![Dialogfeld „Basisklasse extrahieren“](media/extract-base-class.png)

Das neue Dialogfeld **Extract Base Class** (Basisklasse extrahieren) wird geöffnet, in dem Sie den Namen und die gewünschte Position für die Basisklasse angeben können. Sie können die Member auswählen, die in die neue Basisklasse übertragen werden sollen. Wenn Sie das Kontrollkästchen in der Spalte „Als abstrakt festlegen“ aktivieren, werden die Member als abstrakt definiert.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
