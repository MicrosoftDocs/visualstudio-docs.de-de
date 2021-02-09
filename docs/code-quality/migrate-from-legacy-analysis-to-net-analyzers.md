---
title: Migrieren von FxCop zur Quell Analyse (.net-Analyzers)
ms.custom: SEO-VS-2020
description: Erfahren Sie, wie Sie Code zum ersten Mal analysieren oder von FxCop (Binary Analysis) zur neuen Methode der Analyse von verwaltetem Code mithilfe der Quell Analyse (.net-Analyzers) migrieren.
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
manager: jmartens
ms.openlocfilehash: 96a0c0b7fa1f2c703cefde31070ed98c5edddcb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859761"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Migration von der Legacy Analyse (FxCop) zur Quell Analyse (.net-Analyzers)

Die Quell Analyse durch .NET Compiler Platform ("Roslyn")-Analysen ersetzt die [Legacy Analyse](../code-quality/code-analysis-for-managed-code-overview.md) für verwalteten Code. Bei neueren Projektvorlagen wie .net Core und .NET Standard Projekten ist die Legacy Analyse nicht verfügbar.

Viele der Regeln für die Legacy Analyse (FxCop) wurden bereits für .net-Analyzers umgeschrieben, eine Reihe von Roslyn-Code Analysen. Roslyn-Analysen führen bei der compilerausführung Quell Code basierte Analysen aus. Die Analyseergebnisse werden zusammen mit den Ergebnissen der Kompilierung gemeldet.

Weitere Informationen zu den Unterschieden zwischen der Legacy-und der Quell Analyse finden Sie in den folgenden Quellen:

- [Quellcodeanalyse im Vergleich zur Legacyanalyse](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)

- [Häufig gestellte Fragen zu .net-Analyzern](../code-quality/net-analyzers-faq.md)

## <a name="migration"></a>Migration

Um zur Quell Analyse zu migrieren, [Aktivieren oder installieren Sie die .net-Analysen](install-net-analyzers.md). Wenn Verstöße bei der Quellcodeanalyse gefunden werden, werden diese ähnlich wie bei der Legacyanalyse im Fenster „Fehlerliste“ in Visual Studio angezeigt. Außerdem erscheinen Verstöße bei der Quellcodeanalyse auch im Code-Editor als *Wellenlinie* unter dem fehlerhaften Code. Die Farbe der Wellenlinie hängt von den [Schweregradeinstellungen](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) der Regel ab. Informationen zum Anzeigen des Status von Regeln, die an die neuen .net-Analyzers portiert werden, finden Sie unter [portierte und nicht portierte Regeln](../code-quality/fxcop-rule-port-status.md)

> [!NOTE]
> Vor Visual Studio 2019 16,8 und .net 5,0 waren diese Analysen als `Microsoft.CodeAnalysis.FxCopAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)ausgeliefert. Ab Visual Studio 2019 16,8 und .net 5,0 sind diese Analysen im [.NET SDK enthalten](/dotnet/fundamentals/code-analysis/overview). Sie sind auch als `Microsoft.CodeAnalysis.NetAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)verfügbar. Weitere Informationen finden Sie unter [Migrieren von FxCop-Analysen zu .net-Analysen](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="configuration"></a>Konfiguration

Weitere Informationen zum Konfigurieren der .net-Analyzers finden Sie unter:

- Informationen zum Konfigurieren von .net-Analyzern finden Sie unter [Konfigurieren von .net-Analysen](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Weitere Informationen zum Konfigurieren von Analysemodulen mithilfe von vordefinierten Regeln mit Editor config oder einer Regel Satz Datei finden Sie unter [Aktivieren einer Kategorie von Regeln](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

## <a name="see-also"></a>Weitere Informationen

- [Migrieren von FxCop-Analysetools zu .NET-Analysetools](migrate-from-fxcop-analyzers-to-net-analyzers.md)
