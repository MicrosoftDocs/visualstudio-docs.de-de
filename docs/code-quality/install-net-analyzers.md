---
title: Aktivieren oder Installieren von .net-Analysen von erst Anbietern
ms.date: 08/03/2018
description: Erfahren Sie, wie Sie .net-Analysen von erst Anbietern aus dem .NET SDK aktivieren oder diese Analysen als nuget-Paket installieren.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 60eb4828d4c8450376178c2fdccf7d4c0f63d989
ms.sourcegitcommit: 208bd1edebfe6dec5d3bb92c63b5c1e093677e35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440378"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Aktivieren oder Installieren von .net-Analysen von erst Anbietern

## <a name="overview"></a>Übersicht

Die Analysetools für die .NET-Compilerplattform (Roslyn) untersuchen Ihren C#- oder Visual Basic-Code auf Probleme hinsichtlich Codequalität und Codeformat. Sie können die .net-Analysen von erst Anbietern auf eine der folgenden Arten aktivieren oder installieren:

- **Aktivieren über das .NET SDK**: ab Visual Studio 2019 16,8 und .net 5,0 sind diese Analysen im [.NET SDK enthalten](/dotnet/fundamentals/code-analysis/overview). Die Analyse ist standardmäßig für Projekte aktiviert, die auf .net 5,0 oder höher ausgerichtet sind. Sie können die Code Analyse für Projekte aktivieren, die auf frühere .NET-Versionen abzielen, indem Sie die- `EnableNETAnalyzers` Eigenschaft auf festlegen `true` . Sie können die Code Analyse für Ihr Projekt auch deaktivieren, indem Sie `EnableNETAnalyzers` auf festlegen `false` .

- **Installieren Sie als nuget-Paket**: Alternativ können Sie diese Analysen installieren, indem Sie das `Microsoft.CodeAnalysis.NetAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) in Visual Studio 2019 installieren. Wenn Sie Visual Studio 2017 haben, installieren Sie die neueste `2.9.x` Version des `Microsoft.CodeAnalysis.FxCopAnalyzers` [nuget-Pakets](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> Es wird empfohlen, dass Sie die Analysetools aus dem .NET SDK aktivieren, anstatt das `Microsoft.CodeAnalysis.NetAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)zu installieren, wenn dies möglich ist. Durch das Aktivieren der Analysen aus dem .NET SDK wird sichergestellt, dass Sie die Analyzer-Fehlerbehebungen und neuen Analysen automatisch erhalten, sobald Sie das SDK aktualisieren.

## <a name="see-also"></a>Siehe auch

- [Übersicht über Code Analysen in Visual Studio](roslyn-analyzers-overview.md)
- [Verwenden von Codeanalysetools in Visual Studio](use-roslyn-analyzers.md)
- [Migrieren von der Legacyanalyse zu .NET-Analysetools](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migrieren von FxCop-Analysetools zu .NET-Analysetools](migrate-from-fxcop-analyzers-to-net-analyzers.md)
