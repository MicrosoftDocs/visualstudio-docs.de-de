---
title: Manuelles Ausführen der Code Analyse für .net
ms.date: 09/02/2020
description: Erfahren Sie, wie Sie die Code Analyse in Visual Studio 2019 Version 16,5 oder höheren Versionen manuell ausführen. Weitere Informationen finden Sie unter Ausführen von Roslyn-Analyzern in c# oder Visual Basic-Code.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 997fc6f6ecb8ffbd8c48e2352dcc9ae2f6092211
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860021"
---
# <a name="run-code-analysis-manually-for-net"></a>Manuelles Ausführen der Code Analyse für .net
Standardmäßig analysieren .NET Compiler Platform ("Roslyn")-Analysen ihren c#-oder Visual Basic Code bei der Typisierungs Erstellung, indem Sie Live Analysen und während des Builds ausführen. Daher ist es normalerweise nicht erforderlich, die Code Analyse manuell zu initiieren. Es gibt jedoch einige Szenarien, in denen Sie ggf. die Code Analyse manuell auslassen möchten:

> [!NOTE]
> Zum manuellen Ausführen der Code Analyse ist Visual Studio 2019 Version 16,5 oder höher erforderlich.

- Standardmäßig führt die Live Code Analyse Analysetools nur für geöffnete Dateien in Visual Studio aus. Möglicherweise interessieren Sie sich jedoch für die Anzeige von Code Analyse Warnungen für alle Dateien in einem bestimmten Projekt oder einer bestimmten Projekt Mappe. Wenn dies der Fall ist, empfiehlt es sich, die Code Analyse für ein Projekt oder eine Projekt Mappe einmal zu initiieren. Alternativ können Sie die kontinuierliche Live Code Analyse für die gesamte Projekt Mappe aktivieren. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren des Bereichs für die Liveanalyse für verwalteten Code](./configure-live-code-analysis-scope-managed-code.md).
- Möglicherweise bevorzugen Sie den bedarfsgesteuerten Workflow für die Ausführung der Code Analyse für fortlaufende Live Analysen oder die Analyse der Buildzeit. Wenn dies der Fall ist, können Sie die Analyseprogramm Ausführung während der Live Analyse und/oder der Erstellung deaktivieren. Weitere Informationen zum Deaktivieren der Analyse finden [Sie unter Deaktivieren der Quell Code Analyse](disable-code-analysis.md). Anschließend sollten Sie die Code Analyse in einem Projekt oder einer Projekt Mappe einmal manuell Auslösers.

### <a name="run-code-analysis-manually"></a>Manuelles Ausführen der Codeanalyse

1. Wählen Sie in **Projektmappen-Explorer** das Projekt aus.

2. Klicken Sie im Menü **analysieren** **auf Code Analyse für** *Projekt Name* ausführen.

Die Code Analyse wird im Hintergrund gestartet. In der Visual Studio-Statusleiste in der linken unteren Ecke wird die Meldung angezeigt, **dass die Code Analyse für \<project> ... ausgeführt** wird. Wenn die Code Analyse abgeschlossen ist, wird die Statusmeldung in die **Code Analyse \<project> abgeschlossen für** geändert. Die Fehlerliste wird in Kürze mit der gesamten Code Analyse Diagnose aktualisiert.
