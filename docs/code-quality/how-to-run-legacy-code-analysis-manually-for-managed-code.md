---
title: Manuelles Ausführen der Legacy Code Analyse (.net)
description: Erfahren Sie, wie Sie mögliche Fehler im Quellcode erkennen. Weitere Informationen finden Sie unter Manuelles Ausführen von Legacy Code Analysen für verwalteten Code in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 45f201e2c647a1b1074585d59c7618e1ddeb9084
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859995"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Gewusst wie: Manuelles Ausführen der Legacy Code Analyse für verwalteten Code

Das Code Analysetool enthält Informationen zu möglichen Fehlern im Quellcode. Sie können die Code Analyse automatisch mit jedem Build eines Code Projekts ausführen, und Sie können die Code Analyse auch manuell ausführen. Die Regeln, die beim Ausführen der Code Analyse geprüft werden, werden auf der Seite Code Analyse der Eigenschaften Seiten des Projekts angegeben. Weitere Informationen finden Sie unter Gewusst [wie: Konfigurieren der Code Analyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>So führen Sie die Code Analyse manuell aus

1. Wenn Sie Visual Studio 2019 Version 16,5 oder höher ausführen, führen Sie vor dem Starten von Visual Studio den folgenden Befehl an der Eingabeaufforderung aus:

```
set EnableLegacyCodeAnalysis = true
```

2. Klicken Sie in **Projektmappen-Explorer** auf das Projekt.

3. Klicken Sie im Menü **analysieren** auf **Code Analyse für** *Projekt Name* ausführen.
