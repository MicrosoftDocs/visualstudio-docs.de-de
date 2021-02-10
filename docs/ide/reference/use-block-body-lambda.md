---
title: Verwenden von Lambdaausdrücken oder Blocktext
description: Hier erfahren Sie, wie Sie das Menü „Schnellaktionen und Refactorings...“ verwenden, um Lambdaausdrücke so umzugestalten, dass ein Ausdruckskörper oder ein Blocktextkörper verwendet wird.
ms.custom: SEO-VS-2020
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bc3b80ad625c58fbe9127978ebc23fd8c764f4d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889901"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Verwenden von Ausdruckskörpern oder Blocktext für Lambdaausdrücke

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Lambdaausdrücke können umgestaltet werden, sodass ein Ausdruckskörper oder Blocktext verwendet werden.

**Hintergrund:** Wenn Sie es bevorzugen, dass Lambdaausdrücke entweder ein Ausdruckskörper oder Blocktext verwenden.

**Vorteile**: Lambdaausdrücke können umgestaltet werden, um die Lesbarkeit gemäß der Wünsche Ihrer Benutzer zu verbessern.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refactoring von Lambdaausdruckskörpern oder Ausdruckskörpern

1. Platzieren Sie Ihren Cursor rechts auf einem Lambdaoperator.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

  ![Verwenden von Lambdaausdrücken/Blocktext](media/block-body-lambda.png)

3. Wählen Sie **Use block for lambda expressions** (Block für Lambdaausdrücke verwenden) oder **Use expression body for lambda expressions** (Ausdruckskörper für Lambdaausdrücke verwenden) aus.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipps für .NET-Entwickler](../csharp-developer-productivity.md)