---
title: Editor config und Analysen
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b060ae550fd0188728c827cac01c12d51930b57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "88711546"
---
# <a name="code-analysis-faq"></a>FAQ zur Code Analyse

Diese Seite enthält Antworten auf einige häufig gestellte Fragen zur .NET Compiler Platform basierten Code Analyse in Visual Studio.

## <a name="code-analysis-versus-editorconfig"></a>Code Analyse im Vergleich zu Editor config

**F**: sollte ich die Code Analyse oder editorconfig zum Überprüfen des Code Formats verwenden?

**A**: Code Analyse-und Editor config-Dateien arbeiten Hand in Hand. Wenn Sie Code Stile [in einer editorconfig-Datei](../ide/editorconfig-code-style-settings-reference.md) oder auf der [Options Seite Text-Editor](../ide/code-styles-and-code-cleanup.md) definieren, konfigurieren Sie tatsächlich die in Visual Studio integrierten Code-Analysen. Editor config-Dateien können verwendet werden, um Analyzer-Regeln zu aktivieren oder zu deaktivieren sowie um nuget Analyzer-Pakete zu konfigurieren.

## <a name="editorconfig-versus-rule-sets"></a>Editor config im Vergleich zu Regelsätzen

**F**: sollte ich meine Analysen mithilfe eines Regelsatzes oder einer Editor config-Datei konfigurieren?

**A**: Regelsätze und Editor config-Dateien können gleichzeitig vorhanden sein und können zum Konfigurieren von Analysemodulen verwendet werden. Sowohl Editor config-Dateien als auch Regelsätze ermöglichen das Aktivieren und Deaktivieren von Regeln und das Festlegen Ihres schwere Grads.

Editor config-Dateien bieten jedoch weitere Möglichkeiten zum Konfigurieren von Regeln:

- Mit Editor config-Dateien können Sie für die .NET-Code Qualitätsanalysen [definieren, welche Arten von Code analysiert](fxcop-analyzer-options.md)werden.
- Bei den in Visual Studio integrierten .net-codeformatierungsanalyzern können Sie mit Editor config-Dateien [die bevorzugten Code Stile für eine Codebasis definieren](../ide/editorconfig-code-style-settings-reference.md) .

Zusätzlich zu den Regelsätzen und Editor config-Dateien werden einige Analysen durch die Verwendung von Textdateien konfiguriert, die als [zusätzliche Dateien](../ide/build-actions.md#build-action-values) für die c#-und VB-Compiler gekennzeichnet sind.

> [!NOTE]
> - Editor config-Dateien können nur zum Aktivieren von Regeln und Festlegen Ihres schwere Grads in Visual Studio 2019, Version 16,3 und höher, verwendet werden.
> - Editor config-Dateien können nicht zum Konfigurieren der Legacy Analyse verwendet werden, wohingegen Regelsätze dies möglich macht.

## <a name="code-analysis-in-ci-builds"></a>Code Analyse in CI-Builds

**F**: funktioniert die .NET Compiler Platform basierte Code Analyse in Continuous Integration (CI)-Builds?

**A:** Ja. Bei Analysemodulen, die von einem nuget-Paket installiert werden, werden diese Regeln [zur Buildzeit erzwungen](roslyn-analyzers-overview.md#build-errors), einschließlich während eines CI-Builds. Die in CI verwendeten Analyzers erstellen die Regel Konfiguration für Regelsätze und Editor config-Dateien. Derzeit sind die in Visual Studio integrierten Code Analysen nicht als nuget-Paket verfügbar, sodass diese Regeln in einem CI-Build nicht durchsetzbar sind.

## <a name="ide-analyzers-versus-stylecop"></a>IDE-Analysen im Vergleich zu StyleCop

**F**: Worin besteht der Unterschied zwischen den Visual Studio-IDE-Code-Analyzern und StyleCop-Analyzern?

**A**: die Visual Studio-IDE enthält integrierte Analysen, die sowohl Code-als auch Qualitätsprobleme suchen. Diese Regeln helfen Ihnen, neue sprach Features zu verwenden, wenn Sie eingeführt werden, und die Wartbarkeit Ihres Codes zu verbessern. IDE-Analysen werden ständig mit jeder Visual Studio-Version aktualisiert.

[StyleCop-Analysen](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) sind Analysen von Drittanbietern, die als nuget-Paket installiert werden und die Stilkonsistenz in Ihrem Code überprüfen. Im Allgemeinen können Sie mit StyleCop-Regeln persönliche Einstellungen für eine Codebasis festlegen, ohne einen Stil über einen anderen zu empfehlen.

## <a name="code-analyzers-versus-legacy-analysis"></a>Code Analysetools und Legacy Analyse

**F**: Worin besteht der Unterschied zwischen der Legacy Analyse und der .NET Compiler Platform basierten Code Analyse?

**A**: die .NET Compiler Platform basierte Code Analyse analysiert den Quellcode in Echtzeit und während der Kompilierung, während die Legacy Analyse Binärdateien analysiert, nachdem der Build abgeschlossen wurde. Weitere Informationen finden Sie unter [.NET Compiler Platform-basierte Analyse](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) und häufig gestellte Fragen zu den [FxCop-Analysen](fxcop-analyzers-faq.md).

## <a name="treat-warnings-as-errors"></a>Warnungen als Fehler behandeln

**F**: mein Projekt verwendet die Option "Build", um Warnungen als Fehler zu behandeln. Nach der Migration von der Legacy Analyse zur Quell Code Analyse werden alle Code Analyse Warnungen nun als Fehler angezeigt. Wie kann ich dies verhindern?

**A**: um zu verhindern, dass Code Analyse Warnungen als Fehler behandelt werden, führen Sie die folgenden Schritte aus:

  1. Erstellen Sie eine.-Eigenschaften Datei mit folgendem Inhalt:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. Fügen Sie der CSPROJ-oder VBPROJ-Projektdatei eine Zeile hinzu, um die im vorherigen Schritt erstellte Eigenschaften Datei zu importieren. Diese Zeile muss vor allen Zeilen platziert werden, in denen die FxCop Analyzer.-Eigenschaften Dateien importiert werden. Beispiel: Wenn die Datei ".-Eigenschaften" den Namen "CodeAnalysis.-Eigenschaften" hat:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>Eigenschaften Seite für die Code Analyselösung

**F**: wo befindet sich die Eigenschaften Seite "Code Analyse" für die Lösung?

**A**: die Code Analyse-Eigenschaften Seite auf Projektmappenebene wurde zugunsten der zuverlässigeren freigegebenen Eigenschaften Gruppe entfernt. Zum Verwalten der Code Analyse auf Projektebene ist die Eigenschaften Seite für die Code Analyse weiterhin verfügbar. (Bei verwalteten Projekten wird auch empfohlen, von RuleSets zu Editor config für die Regel Konfiguration zu migrieren.)  Zum Freigeben von RuleSets für mehrere/alle Projekte in einer Projekt Mappe oder einem Repository empfiehlt es sich, eine Eigenschaften Gruppe mit der codeanalysisruleset-Eigenschaft in einer freigegebenen Datei mit den Eigenschaften/Zielen oder der Datei "Directory.-Eigenschaften/Verzeichnis. targets" zu definieren. Wenn Sie keine gemeinsamen Eigenschaften oder Ziele haben, die von all ihren Projekten importiert werden, sollten Sie [eine solche Eigenschaften Gruppe zu einem Verzeichnis.-Eigenschaften oder zu einem Verzeichnis. targets in einem Projektmappenverzeichnis der obersten Ebene hinzufügen, das automatisch in alle Projektdateien importiert wird, die im Verzeichnis oder seinen Unterverzeichnissen definiert](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build?directorybuildprops-and-directorybuildtargets)sind.

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über Analyzers](roslyn-analyzers-overview.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
