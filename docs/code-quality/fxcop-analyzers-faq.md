---
title: FxCop-Codeanalyse und FxCop-Analysetools
ms.date: 09/06/2018
description: Informieren Sie sich über den Unterschied zwischen den veralteten FxCop-und FxCop-Analyzern in Visual Studio. Hier finden Sie Antworten auf Fragen zur Verwendung dieser Analyzers.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e6768ad7f1ee87f75592c736b03bf6fd64e28c2
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348957"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Häufig gestellte Fragen zu FxCop und FxCop-Analysetools

Die Unterschiede zwischen Legacy-FxCop und FxCop-Analysetools können verwirrend sein. Deshalb werden in diesem Artikel einige Fragen behandelt, die Sie möglicherweise haben.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Was ist der Unterschied zwischen Legacy-FxCop und FxCop-Analysetools?

Legacy-FxCop führt die Analyse einer kompilierten Assembly nach dem Erstellen aus. Eine separate ausführbare Datei namens **FxCopCmd.exe** wird ausgeführt. Die Datei „FxCopCmd.exe“ lädt die kompilierte Assembly, führt die Codeanalyse aus und meldet dann die Ergebnisse (bzw. *Diagnose* ).

FxCop-Analysetools basieren auf der .NET Compiler Platform („Roslyn“). Sie [installieren sie als NuGet-Pakete](install-fxcop-analyzers.md#nuget-package), auf die von dem Projekt oder der Projektmappe verwiesen wird. FxCop-Analysetools führen während der Ausführung des Compilers Analysen aus, die auf dem Quellcode basieren. FxCop-Analysetools werden im Compilerprozess gehostet, entweder **csc.exe** oder **vbc.exe** , und führen die Analyse bei der Erstellung des Projekts aus. Die Analyseergebnisse werden zusammen mit den Ergebnissen der Kompilierung gemeldet.

> [!NOTE]
> Sie können [FxCop-Analysetools auch als Visual Studio-Erweiterung installieren](install-fxcop-analyzers.md#vsix). In diesem Fall werden die Analysetools ausgeführt, während Sie in den Code-Editor schreiben. Allerdings werden Sie nicht zum Zeitpunkt der Erstellung ausgeführt. Wenn Sie FxCop-Analysetools als Teil der CI (Continuous Integration) ausführen möchten, installieren Sie sie stattdessen als NuGet-Pakete.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Werden FxCop-Analysetools mit dem Befehl „Codeanalyse ausführen“ ausgeführt?

Vor der Veröffentlichung von Visual Studio 2019 16,5 führt **die Auswahl von Analyse**  >  **Ausführen Code Analyse** aus die Legacy Analyse aus. Starten von Visual Studio 2019 16,5, Menüoption " **Code Analyse ausführen** " führt Roslyn-basierte Analysen für das ausgewählte Projekt oder die ausgewählte Projekt Mappe aus. Wenn Sie Roslyn-basierte FxCop-Analyzers installiert haben, werden diese ebenfalls ausgeführt. Weitere Informationen finden Sie unter Gewusst [wie: Manuelles Ausführen der Code Analyse für verwalteten Code](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Werden Analysetools von der MSBuild-Projekteigenschaft „RunCodeAnalysis“ ausgeführt?

Nein. Die Eigenschaft **RunCodeAnalysis** in einer Projektdatei (z.B. *.csproj* ) wird nur zum Ausführen von Legacy-FxCop verwendet. Sie führt eine MSBuild-Postbuildaufgabe aus, die **FxCopCmd.exe** aufruft.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Wie kann ich FxCop-Analysetools ausführen?

Zum Ausführen von FxCop-Analysetools müssen Sie zunächst die entsprechenden [NuGet-Pakete installieren](install-fxcop-analyzers.md). Dann erstellen Sie Ihr Projekt oder Ihre Projektmappe mit Visual Studio oder MSBuild. Die Warnungen und Fehlermeldungen von FxCop-Analysetools werden in der **Fehlerliste** oder im Befehlsfenster angezeigt.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Nach der Installation des NuGet-Pakets für das FxCop-Analysetool erhalte ich die Warnung „CA0507“.

Wenn Sie FxCop-Analysen installiert haben, aber weiterhin eine Warnung erhalten CA0507 **"" Code Analyse ausführen "wurde als veraltet markiert, um FxCop-Analysen zu bevorzugen, die während des Builds ausgeführt** werden. möglicherweise müssen Sie die Eigenschaft" **RunCodeAnalysis** MSBuild "in der [Projektdatei](../ide/solutions-and-projects-in-visual-studio.md#project-file) auf" **false** "festlegen. Andernfalls wird die Legacy Analyse nach jedem Build ausgeführt.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Welche Regeln wurden in FxCop-Analyzers portiert?

Informationen dazu, welche Legacy Analyse Regeln in [FxCop-Analysen](install-fxcop-analyzers.md)portiert wurden, finden Sie unter [Port Status der FxCop-Regel](fxcop-rule-port-status.md).

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Code Analyse Warnungen werden als Fehler behandelt.

Wenn das Projekt die Buildoption verwendet, um Warnungen als Fehler zu behandeln, werden möglicherweise FxCop Analyzer-Warnungen als Fehler angezeigt. Um zu verhindern, dass Code Analyse Warnungen als Fehler behandelt werden, führen Sie die Schritte unter Häufig gestellte Fragen zu [Code Analysen](../code-quality/analyzers-faq.md#treat-warnings-as-errors)aus.

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über .NET Compiler Platform-Analysetools](roslyn-analyzers-overview.md)
- [Migration zu FxCop-Analysetools](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Installieren von FxCop-Analysetools](install-fxcop-analyzers.md)
