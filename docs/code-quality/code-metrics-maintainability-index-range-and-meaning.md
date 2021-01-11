---
title: Codemetrik-Wartbarkeitsindex Bereich und Bedeutung
ms.date: 1/8/2021
description: Erfahren Sie mehr über die Metrik für den verwaltbarkeitsindex für Codemetriken in Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14bee6dcb522b7c1dd0475ca309b829a09c0d4ec
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069533"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Codemetrik-Wartbarkeitsindex Bereich und Bedeutung

Frage: der Wartbarkeitsindex wurde auf einen Wert zwischen 0 und 100 zurückgesetzt. Wie und warum wurde dies erreicht?

Die Metrik wurde ursprünglich wie folgt berechnet: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

Die Verwendung dieser Formel bedeutete, dass Sie von 171 zu einer ungebundenen negativen Zahl reicht.  Als Code in Richtung 0 aufging, war es eindeutig schwierig, Code zu verwalten, und der Unterschied zwischen Code bei 0 und einem negativen Wert war nicht hilfreich.  Aufgrund der absteigenden Nützlichkeit der negativen Zahlen und der Anforderung, die Metrik so klar wie möglich zu halten, haben wir beschlossen, alle 0 oder weniger Indizes als 0 zu behandeln und den Bereich von 171 oder weniger auf den Wert 0 bis 100 zu setzen. Aus diesem Grund lautet die verwendete Formel wie folgt:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Außerdem haben wir uns entschieden, mit den Schwellenwerten konservativ zu sein.  Der Wunsch lautete: Wenn der Index rot angezeigt wird, würden wir mit einem hohen Maß an Vertrauen sagen, dass es ein Problem mit dem Code gab.  Dies hat die folgenden Schwellenwerte zur Folge:

Für die Schwellenwerte haben wir uns entschieden, den 0-100-Bereich 80-20 aufzulösen, um den Rauschpegel niedrig zu halten, und wir haben nur einen verdächtigen Code gekennzeichnet. Wir haben die folgenden Schwellenwerte verwendet:

- 0-9 = rot
- 10-19 = gelb
- 20-100 = grün
