---
title: Hochstufen von Membern in der Hierarchie
description: Hier erfahren Sie, wie Sie über das Menü „Schnellaktionen und Refactorings...“ Member auf den Basistyp hochstufen.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 159608644cb641aa2c84e4d55e92156215069030
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616875"
---
# <a name="pull-members-up"></a>Hochstufen von Membern in der Hierarchie

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Member sollen in den Basistyp hochgestuft werden.

**Hintergrund:** Sie haben eine Schnittstelle implementiert und möchten einen Member in den Basistyp verschieben.

**Vorteile**: Wenn Sie Member in der Hierarchie hochstufen, können andere Implementierungen Ihrer Schnittstelle diese Member ebenfalls erben.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf einem beliebigen Member einer implementierten Schnittstelle.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Hochstufen von Membern in der Hierarchie](media/pull-members-up.png)

2. Klicken Sie auf **Pull Members up to base type** (Member in den Basistyp hochstufen).

3. Wählen Sie im Dialogfeld aus, welche Member der ausgewählten Schnittstelle hinzugefügt werden sollen.

   ![Hochstufen eines Members in der Hierarchie](media/pull-members-up-dialog.png)

4. Klicken Sie auf **OK**. Die ausgewählten Member werden auf die Schnittstelle hochgestuft.

   ![Vollständiges Hochstufen von Membern in der Hierarchie](media/pull-members-up-completed.png)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
