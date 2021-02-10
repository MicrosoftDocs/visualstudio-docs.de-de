---
title: Hochstufen von Membern in der Hierarchie
description: Hier erfahren Sie, wie Sie über das Menü „Schnellaktionen und Refactorings...“ Member auf den Basistyp hochstufen.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ee5776e9fc39b77f8059146848d847e0976a5664
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958283"
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
