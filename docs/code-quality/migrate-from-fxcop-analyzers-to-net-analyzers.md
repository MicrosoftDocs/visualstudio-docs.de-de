---
title: Migrieren von FxCop-Analysen zu .net-Analysemodulen
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
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112167"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migrieren von FxCop-Analysen zu .net-Analysemodulen

Die Quell Analyse durch .NET Compiler Platform ("Roslyn")-Analysen ersetzt die [Legacy Analyse](code-analysis-for-managed-code-overview.md) für verwalteten Code. Viele der Regeln für die Legacy Analyse (FxCop) wurden bereits als Quell Analytiker umgeschrieben.

Vor Visual Studio 2019 16,8 und .net 5,0 waren diese Analysen als `Microsoft.CodeAnalysis.FxCopAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)ausgeliefert.

Ab Visual Studio 2019 16,8 und .net 5,0 sind diese Analysen im [.NET SDK enthalten](/dotnet/fundamentals/code-analysis/overview). Sie sind auch als `Microsoft.CodeAnalysis.NetAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)verfügbar. `Microsoft.CodeAnalysis.FxCopAnalyzers` Das nuget-Paket wird bald als veraltet markiert.

## <a name="migration-steps"></a>Schritte bei der Migration

Führen Sie die folgenden Schritte aus, um das Projekt oder die Projekt Mappe von `Microsoft.CodeAnalysis.FxCopAnalyzers` zu den .net-Analyzern zu migrieren:

1. Deinstallieren des `Microsoft.CodeAnalysis.FxCopAnalyzers` nuget-Pakets

2. [Aktivieren oder Installieren von .net-Analyzern](install-net-analyzers.md)

3. Zusätzliche Regeln aktivieren: `Microsoft.CodeAnalysis.NetAnalyzers` ist im Vergleich zu weitaus konservativer `Microsoft.CodeAnalysis.FxCopAnalyzers` . Im Gegensatz zum fxcopanalyzers-Paket sind nur einige Richtigkeit-Regeln verfügbar, die [standardmäßig als Buildwarnungen aktiviert](/dotnet/fundamentals/code-analysis/overview#enabled-rules)sind. Sie können [zusätzliche Regeln aktivieren](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) , indem Sie die MSBuild-Eigenschaft [analysismode](/dotnet/core/project-sdk/msbuild-props#analysismode) anpassen. Wenn Sie z. b. die-Eigenschaft auf festlegen, `AllEnabledByDefault` werden alle anwendbaren Zertifizierungsstellen Regeln standardmäßig als Buildwarnungen aktiviert.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Siehe auch

- [Quellcodeanalyse im Vergleich zur Legacyanalyse](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Migrieren von Legacy Analysen zu .net-Analyzern](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Aktivieren oder Installieren von .net-Analyzern](install-net-analyzers.md)
- [Häufig gestellte Fragen zu .net-Analyzern](net-analyzers-faq.md)
- [Konfigurieren von .net-Analyzern](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
