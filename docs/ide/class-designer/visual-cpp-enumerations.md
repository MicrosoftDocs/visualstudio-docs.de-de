---
title: C++-Enumerationen im Klassen-Designer
description: Erfahren Sie, wie der Klassen-Designer C++-Enum- und bereichsbezogene Enum-Klassentypen unterstützt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 88675bb7593a901805cc156bbb36a2f49d69ec29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852556"
---
# <a name="c-enumerations-in-class-designer"></a>C++-Enumerationen im Klassen-Designer

Der **Klassen-Designer** unterstützt `enum`-Typen von C++ und bewertete `enum class`-Typen. Dies ist ein Beispiel:

```cpp
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};
```

Eine C++-Enumerationsform in einem Klassendiagramm gleicht in Struktur und Funktionsweise einer Strukturform, sie trägt allerdings die Bezeichnung **Enum** oder **Enumerationsklasse**, sie ist nicht blau, sondern rosa und wird mit farbigem Rahmen an der linken und oberen Begrenzung angezeigt. Sowohl Enumerationsformen als auch Strukturformen sind eckig.

Weitere Informationen zur Verwendung des `enum`-Typs finden Sie unter [Enumerationen](/cpp/cpp/enumerations-cpp).

## <a name="see-also"></a>Weitere Informationen

- [Arbeiten mit C++-Code](working-with-visual-cpp-code.md)
- [Enumerationen](/cpp/cpp/enumerations-cpp)
