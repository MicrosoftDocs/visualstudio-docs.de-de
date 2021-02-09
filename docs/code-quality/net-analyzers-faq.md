---
title: FxCop-Code Analyse (binäre Analyse) und .net-Analysen (Quell Analyse)
ms.date: 09/06/2018
description: Informieren Sie sich über den Unterschied zwischen der Vorgängerversion FxCop (binäre Analyse) und .net-Analysen (Quell Analyse) in Visual Studio. Hier finden Sie Antworten auf Fragen zur Verwendung dieser Analyzers.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867762"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>Häufig gestellte Fragen zu den Legacy-FxCop-und .net-Analyzern

Es kann etwas verwirrend sein, um die Unterschiede zwischen der Vorgängerversion FxCop (binäre Analyse) und .net-Analysen (Quell Analyse) zu verstehen. Deshalb werden in diesem Artikel einige Fragen behandelt, die Sie möglicherweise haben.

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>Worin besteht der Unterschied zwischen den Legacy-FxCop-und .net-Analyzern?

Legacy-FxCop führt die Analyse einer kompilierten Assembly nach dem Erstellen aus. Eine separate ausführbare Datei namens **FxCopCmd.exe** wird ausgeführt. Die Datei „FxCopCmd.exe“ lädt die kompilierte Assembly, führt die Codeanalyse aus und meldet dann die Ergebnisse (bzw. *Diagnose*).

.Net-Analysen basieren auf dem .NET Compiler Platform ("Roslyn"). Sie [Aktivieren Sie über das .NET SDK oder installieren Sie als nuget-Paket](install-net-analyzers.md) , auf das vom Projekt oder der Projekt Mappe verwiesen wird. Analyzers führen eine Quell Code basierte Analyse während der compilerausführung aus. Analyzers werden innerhalb des Compilerprozesses gehostet, entweder **csc.exe** oder **vbc.exe**, und führen eine Analyse aus, wenn das Projekt erstellt wird. Die Analyseergebnisse werden zusammen mit den Ergebnissen der Kompilierung gemeldet.

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>Worin besteht der Unterschied zwischen FxCop-Analysen und .net-Analysen?

Beide FxCop-Analysen und .net-Analysen beziehen sich auf die .NET Compiler Platform ("Roslyn") Analyzer-Implementierungen von FxCop-Zertifizierungsstellen Regeln. Vor Visual Studio 2019 16,8 und .net 5,0 waren diese Analysen als `Microsoft.CodeAnalysis.FxCopAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)ausgeliefert. Ab Visual Studio 2019 16,8 und .net 5,0 sind diese Analysen im [.NET SDK enthalten](/dotnet/fundamentals/code-analysis/overview). Sie sind auch als `Microsoft.CodeAnalysis.NetAnalyzers` [nuget-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)verfügbar. Sie sollten eine [Migration von FxCop Analyzer zu .NET Analyzer durch](migrate-from-fxcop-analyzers-to-net-analyzers.md)führen.

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>Führt der Befehl zum Ausführen der Code Analyse .net-Analyzers aus?

Vor der Veröffentlichung von Visual Studio 2019 16,5 führt **die Auswahl von Analyse**  >  **Ausführen Code Analyse** aus die Legacy Analyse aus. Starten von Visual Studio 2019 16,5, Menüoption " **Code Analyse ausführen** " führt Roslyn-basierte Analysen für das ausgewählte Projekt oder die ausgewählte Projekt Mappe aus. Wenn Sie .net-Analyzers installiert haben, werden diese ebenfalls ausgeführt. Weitere Informationen finden Sie unter Gewusst [wie: Manuelles Ausführen der Code Analyse für verwalteten Code](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Werden Analysetools von der MSBuild-Projekteigenschaft „RunCodeAnalysis“ ausgeführt?

Nein. Die Eigenschaft **RunCodeAnalysis** in einer Projektdatei (z.B. *.csproj*) wird nur zum Ausführen von Legacy-FxCop verwendet. Sie führt eine MSBuild-Postbuildaufgabe aus, die **FxCopCmd.exe** aufruft.

## <a name="so-how-do-i-run-net-analyzers-then"></a>Wie führe ich also .net-Analysen aus?

Um .net-Analyzers auszuführen, [Aktivieren Sie Sie zuerst über das .NET SDK, oder installieren Sie Sie als nuget-Paket](install-net-analyzers.md). Dann erstellen Sie Ihr Projekt oder Ihre Projektmappe mit Visual Studio oder MSBuild. Die Warnungen und Fehler, die von den Roslyn-Analyzern generiert werden, werden im **Fehlerliste** oder im Befehlsfenster angezeigt.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>Ich erhalte eine Warnung CA0507 auch nachdem ich das .net Analysen-nuget-Paket installiert habe.

Wenn Sie .net-Analysen installiert haben, aber weiterhin eine Warnung erhalten CA0507 **"" Code Analyse ausführen "ist veraltet, da FxCop-Analysen, die während des Builds ausgeführt** werden, veraltet ist. möglicherweise müssen Sie die Eigenschaft" **RunCodeAnalysis** MSBuild "in der [Projektdatei](../ide/solutions-and-projects-in-visual-studio.md#project-file) auf" **false**"festlegen. Andernfalls wird die Legacy Analyse nach jedem Build ausgeführt.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>Welche Regeln wurden in .net-Analyzers portiert?

Informationen dazu, welche Legacy Analyse Regeln an .net-Analyzers portiert wurden, finden Sie unter [Port Status der FxCop-Regel](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Code Analyse Warnungen werden als Fehler behandelt.

Wenn das Projekt die Buildoption verwendet, um Warnungen als Fehler zu behandeln, werden möglicherweise Analyzer-Warnungen als Fehler angezeigt. Um zu verhindern, dass Code Analyse Warnungen als Fehler behandelt werden, führen Sie die Schritte unter Häufig gestellte Fragen zu [Code Analysen](../code-quality/analyzers-faq.md#treat-warnings-as-errors)aus.

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über .NET Compiler Platform-Analysetools](roslyn-analyzers-overview.md)
- [Migrieren zu .NET-Analysetools](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Installieren von .NET-Analysetools](install-net-analyzers.md)
