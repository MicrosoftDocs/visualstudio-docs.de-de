---
title: Aktivieren oder Installieren von .net-Analyzern
ms.date: 08/03/2018
description: Erfahren Sie, wie Sie .net-Analysen aus dem .NET SDK aktivieren oder diese Analysen als nuget-Paket installieren.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a14d89caba498a07c2447f9df1109e4da9f6a466
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112163"
---
# <a name="enable-or-install-net-analyzers"></a>Aktivieren oder Installieren von .net-Analyzern

## <a name="overview"></a>Übersicht

Die Analysetools für die .NET-Compilerplattform (Roslyn) untersuchen Ihren C#- oder Visual Basic-Code auf Probleme hinsichtlich Codequalität und Codeformat. Sie können diese Analysen auf eine der folgenden Arten aktivieren oder installieren:

- **Aktivieren über das .NET SDK**: ab Visual Studio 2019 16,8 und .net 5,0 sind diese Analysen im [.NET SDK enthalten](/dotnet/fundamentals/code-analysis/overview). Die Analyse ist standardmäßig für Projekte aktiviert, die auf .net 5,0 oder höher ausgerichtet sind. Sie können die Code Analyse für Projekte aktivieren, die auf frühere .NET-Versionen abzielen, indem Sie die- `EnableNETAnalyzers` Eigenschaft auf festlegen `true` . Sie können die Code Analyse für Ihr Projekt auch deaktivieren, indem Sie `EnableNETAnalyzers` auf festlegen `false` .

- **Installieren Sie als nuget-Paket**: Alternativ können Sie diese Analysen installieren, indem Sie das `Microsoft.CodeAnalysis.NetAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) in Visual Studio 2019 installieren. Wenn Sie Visual Studio 2017 haben, installieren Sie die neueste `2.9.x` Version des `Microsoft.CodeAnalysis.FxCopAnalyzers` [nuget-Pakets](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> Es wird empfohlen, dass Sie die Analysetools aus dem .NET SDK aktivieren, anstatt das `Microsoft.CodeAnalysis.NetAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)zu installieren, wenn dies möglich ist. Durch das Aktivieren der Analysen aus dem .NET SDK wird sichergestellt, dass Sie die Analyzer-Fehlerbehebungen und neuen Analysen automatisch erhalten, sobald Sie das SDK aktualisieren.

## <a name="see-also"></a>Siehe auch

- [Übersicht über Code Analysen in Visual Studio](roslyn-analyzers-overview.md)
- [Verwenden von Codeanalysetools in Visual Studio](use-roslyn-analyzers.md)
- [Migrieren von Legacy Analysen zu .net-Analyzern](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migrieren von FxCop-Analysen zu .net-Analysemodulen](migrate-from-fxcop-analyzers-to-net-analyzers.md)
