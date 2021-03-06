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
ms.openlocfilehash: f214ac47ad3d831432b91652c5bbe3249ce5f1c5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223484"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Gewusst wie: Manuelles Ausführen der Legacy Code Analyse für verwalteten Code

Das Code Analysetool enthält Informationen zu möglichen Fehlern im Quellcode. Sie können die Code Analyse automatisch mit jedem Build eines Code Projekts ausführen, und Sie können die Code Analyse auch manuell ausführen. Die Regeln, die beim Ausführen der Code Analyse geprüft werden, werden auf der Seite Code Analyse der Eigenschaften Seiten des Projekts angegeben. Weitere Informationen finden Sie unter Gewusst [wie: Konfigurieren der Code Analyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>So führen Sie die Code Analyse manuell aus

1. Wenn Sie Visual Studio 2019 Version 16,5 oder höher ausführen, führen Sie vor dem Starten von Visual Studio den folgenden Befehl an der Eingabeaufforderung aus:

```
setx EnableLegacyCodeAnalysis true
```

2. Klicken Sie in **Projektmappen-Explorer** auf das Projekt.

3. Klicken Sie im Menü **analysieren** auf **Code Analyse für** *Projekt Name* ausführen.
