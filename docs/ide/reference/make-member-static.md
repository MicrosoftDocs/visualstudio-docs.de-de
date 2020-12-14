---
title: Festlegen eines Members als statisch
description: Hier erfahren Sie, wie Sie das Menü „Schnellaktionen und Refactorings...“ verwenden, um einen Member als statisch zu kennzeichnen.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e663d59f47728bc4a7c84290ee0e89ae453f23ae
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561018"
---
# <a name="make-member-static"></a>Festlegen eines Members als statisch

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Festlegen eines Members als statisch

**Hintergrund:** Wenn Sie einen nicht statischen Member als statisch festlegen möchten

**Vorteile**: Statische Member verbessern die Lesbarkeit: Wenn bekannt ist, dass spezifischer Code isoliert ist, ist dieser einfacher zu verstehen, wieder zu lesen und wiederzuverwenden. 

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie das Caretzeichen im Membernamen.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Festlegen eines Members als statisch](media/make-member-static.png)

3. Klicken Sie auf **Als statisch festlegen**.

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
