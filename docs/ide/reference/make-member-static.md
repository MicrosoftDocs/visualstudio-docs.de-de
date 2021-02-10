---
title: Festlegen eines Members als statisch
description: Hier erfahren Sie, wie Sie das Menü „Schnellaktionen und Refactorings...“ verwenden, um einen Member als statisch zu kennzeichnen.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5478e85d89d4ea44d34e0a5ae9170aaffb3836f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919443"
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
