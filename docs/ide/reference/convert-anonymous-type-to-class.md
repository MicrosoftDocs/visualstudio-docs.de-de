---
title: Konvertieren eines anonymen Typs in eine Klasse
description: Hier erfahren Sie, wie Sie mit dem Menü „Schnellaktionen und Refactorings…“ einen anonymen Typ in eine Klasse in Visual Studio konvertieren.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: 19e755e4b56675265d85a416684f2b42bd7ccd13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907660"
---
# <a name="convert-anonymous-type-to-class"></a>Konvertieren eines anonymen Typs in eine Klasse

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Konvertieren eines anonymen Typs in eine Klasse

**Hintergrund:** Sie verfügen über einen anonymen Typ, den Sie in einer Klasse weiterentwickeln möchten.

**Vorteile**: Anonyme Typen sind nützlich, wenn Sie sie nur lokal verwenden. Sobald Ihr Code komplexer wird, ist es von Vorteil, Typen einfach zu Klassen heraufzustufen.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in einem anonymen Typ.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Konvertieren eines anonymen Typs in eine Klasse](media/convert-anon-to-class.png)

2. Drücken Sie die **EINGABETASTE**, um das Refactoring zu akzeptieren.

   ![Die Konvertierung eines anonymen Typs in eine Klasse wurde akzeptiert](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
