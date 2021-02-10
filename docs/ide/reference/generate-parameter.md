---
title: Refactoring der Parametergenerierung
description: Hier erfahren Sie, wie Sie das Menü „Schnellaktionen und Refactorings...“ verwenden, um einen Methodenparameter automatisch zu generieren.
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
ms.openlocfilehash: 33e2be19e3a5a83d89e722aa0c1a1154c8196939
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968033"
---
# <a name="generate-parameter"></a>Parameter generieren

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit wird automatisch ein Methodenparameter generiert.

**Hintergrund:** Sie verweisen auf eine Variable in einer Methode, die im aktuellen Kontext nicht vorhanden ist, und erhalten eine Fehlermeldung. Zur Codefehlerbehebung können Sie einen Parameter generieren. 

**Vorteile**: Sie können eine Methodensignatur schnell und ohne Verlust von Kontext ändern.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in den Variablennamen, und drücken Sie **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
1. Wählen Sie **Parameter generieren** aus.

   ![Parameter generieren](media/generate-parameter.png) 

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
