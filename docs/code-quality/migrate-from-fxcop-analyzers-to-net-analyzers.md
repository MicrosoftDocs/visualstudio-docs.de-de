---
title: Migrieren von FxCop-Analysetools zu .NET-Analysetools
ms.custom: SEO-VS-2020
description: Erfahren Sie, wie Sie von FxCop-Analysen zu .net-Analysen migrieren.
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f9794c825012d682ca40dfdc5ebbfa03f0614ee
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398376"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migrieren von FxCop-Analysetools zu .NET-Analysetools

Die Quell Analyse durch .NET Compiler Platform ("Roslyn")-Analysen ersetzt die [Legacy Analyse](code-analysis-for-managed-code-overview.md) für verwalteten Code. Viele der Regeln für die Legacy Analyse (FxCop) wurden bereits als Quell Analytiker umgeschrieben.

Vor Visual Studio 2019 16,8 und .net 5,0 waren diese Analysen als `Microsoft.CodeAnalysis.FxCopAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)ausgeliefert.

Ab Visual Studio 2019 16,8 und .net 5,0 sind diese Analysen im [.NET SDK enthalten](/dotnet/fundamentals/code-analysis/overview). Wenn Sie nicht zum .net 5 + SDK wechseln möchten oder wenn Sie ein auf einem nuget-Paket basierendes Modell bevorzugen, sind die Analysetools auch im `Microsoft.CodeAnalysis.NetAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)verfügbar. Möglicherweise bevorzugen Sie ein Paket basiertes Modell für Bedarfs gesteuerte Versions Aktualisierungen.

> [!NOTE]
> Die .net-Analysen von ersten Anbietern sind Ziel Platt Form agnostisch. Das heißt, das Projekt muss keine bestimmte .NET-Plattform als Ziel haben. Die Analyzer funktionieren für Projekte, die auf `net5.0` und frühere Versionen von .net abzielen, z `netcoreapp` . b `netstandard` ., und `net472` .

## <a name="migration-steps"></a>Schritte bei der Migration

Ab Version ist `3.3.2` das `Microsoft.CodeAnalysis.FxCopAnalyzers` nuget-Paket veraltet. Führen Sie die folgenden Schritte aus, um das Projekt oder die Projekt Mappe von `Microsoft.CodeAnalysis.FxCopAnalyzers` zu den .net-Analyzern zu migrieren:

1. Deinstallieren des `Microsoft.CodeAnalysis.FxCopAnalyzers` nuget-Pakets

2. [Aktivieren oder installieren Sie .net-Analysen](install-net-analyzers.md). Beachten Sie, dass Sie die Zielplattform des Projekts nicht ändern müssen.

3. Zusätzliche Regeln aktivieren: `Microsoft.CodeAnalysis.NetAnalyzers` ist im Vergleich zu weitaus konservativer `Microsoft.CodeAnalysis.FxCopAnalyzers` . Im Gegensatz zum fxcopanalyzers-Paket sind nur einige Richtigkeit-Regeln verfügbar, die [standardmäßig als Buildwarnungen aktiviert](/dotnet/fundamentals/code-analysis/overview#enabled-rules)sind. Sie können [zusätzliche Regeln aktivieren](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) , indem Sie die MSBuild-Eigenschaft [analysismode](/dotnet/core/project-sdk/msbuild-props#analysismode) anpassen. Wenn Sie z. b. die-Eigenschaft auf festlegen, `AllEnabledByDefault` werden alle anwendbaren Zertifizierungsstellen Regeln standardmäßig als Buildwarnungen aktiviert.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Weitere Informationen

- [Quellcodeanalyse im Vergleich zur Legacyanalyse](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Migrieren von der Legacyanalyse zu .NET-Analysetools](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Aktivieren oder Installieren von .net-Analyzern](install-net-analyzers.md)
- [Häufig gestellte Fragen zu .net-Analyzern](net-analyzers-faq.md)
- [Konfigurieren von .net-Analyzern](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
