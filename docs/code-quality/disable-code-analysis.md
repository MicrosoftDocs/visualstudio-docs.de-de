---
title: Code Analyse deaktivieren
ms.date: 09/01/2020
description: Erfahren Sie, wie Sie die Visual Studio-Quell Code Analyse in .net Core-, .NET Standard-und .NET Framework-Projekten deaktivieren.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.openlocfilehash: e808cb623fa47c9971e1cdceb15a02b5bf46e901
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348553"
---
# <a name="disable-source-code-analysis-for-net"></a>Quell Code Analyse für .net deaktivieren

::: moniker range=">=vs-2019"

Auf dieser Seite können Sie die Code Analyse in Visual Studio deaktivieren. Es gelten Einschränkungen für das, was Sie deaktivieren können, und die Vorgehensweise zum Ausschalten der Code Analyse variiert je nach den folgenden Faktoren:

- Projekttyp (.net Core/Standard im Vergleich zu .NET Framework)

  .Net Core-und .NET Standard-Projekte verfügen über Optionen auf der Seite mit den Code Analyse Eigenschaften, mit denen Sie die Code Analyse von Analyzern deaktivieren können, die als nuget-Paket installiert wurden. Weitere Informationen finden Sie unter [.net Core-und .NET Standard-Projekte](#net-core-and-net-standard-projects). Informationen zum Deaktivieren der Quell Code Analyse für .NET Framework Projekte finden Sie unter [.NET Framework Projekte](#net-framework-projects).

- Quell Analyse und Legacy Analyse

  Dieses Thema bezieht sich auf die Quell Code Analyse und nicht auf die Legacy-(binäre) Analyse. Weitere Informationen zum Deaktivieren der Legacy Analyse finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der Legacy Code Analyse](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>.Net Core-und .NET Standard-Projekte

Ab Visual Studio 2019, Version 16,3, stehen auf der Seite mit den Code Analyse Eigenschaften zwei Kontrollkästchen zur Verfügung, mit denen Sie steuern können, ob Analysen zum Zeitpunkt der Erstellung und zur Entwurfszeit ausgeführt werden. Diese Optionen sind projektspezifisch.

![Aktivieren oder Deaktivieren der Live Code Analyse oder bei der Erstellung in Visual Studio](media/run-on-build-run-live-analysis.png)

Klicken Sie zum Öffnen dieser Seite in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Eigenschaften** aus. Wählen Sie die Registerkarte **Code Analyse** aus.

- Zum Deaktivieren der Quell Analyse während der Buildzeit deaktivieren Sie die Option **bei Build ausführen** .
- Um die Live Quell Analyse zu deaktivieren, deaktivieren Sie die Option **bei Live Analyse ausführen** .

> [!NOTE]
> Wenn Sie ab Visual Studio 2019 Version 16,5 den Workflow für die Bedarfs gesteuerte Ausführung der Code Analyse bevorzugen, können Sie die Analyseprogramm Ausführung während der Live Analyse deaktivieren und/oder die Code Analyse einmal in einem Projekt oder einer Projekt Mappe bei Bedarf erstellen und manuell auslöst. Weitere Informationen zum manuellen Ausführen der Code Analyse finden [Sie unter Gewusst wie: Manuelles Ausführen der Code Analyse für verwalteten Code](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>.NET Framework Projekte

Fügen Sie der [Projektdatei](../ide/solutions-and-projects-in-visual-studio.md#project-file)mindestens eine der folgenden MSBuild-Eigenschaften hinzu, um die Quell Code Analyse für Analyzers zu deaktivieren.

| MSBuild-Eigenschaft | BESCHREIBUNG | Standard |
| - | - | - |
| `RunAnalyzersDuringBuild` | Steuert, ob Analysen zum Zeitpunkt der Erstellung ausgeführt werden. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Steuert, ob Analysen Code zur Entwurfszeit Live analysieren. | `true` |
| `RunAnalyzers` | Deaktiviert Analysen sowohl bei der Erstellung als auch bei der Entwurfszeit. Diese Eigenschaft hat Vorrang vor `RunAnalyzersDuringBuild` und `RunAnalyzersDuringLiveAnalysis` . | `true` |

Beispiele:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Quellanalyse

Sie können die [Quell Analyse](roslyn-analyzers-overview.md) in Visual Studio 2017 nicht deaktivieren. Wenn Sie Analysefehler aus dem **Fehlerliste** löschen möchten, können Sie alle aktuellen Verstöße unterdrücken, indem Sie **Analyze**  >  in der Menüleiste analysieren **Code Analyse ausführen und aktive Probleme unterdrücken** auswählen. Weitere Informationen finden Sie unter unter [drücken von Verletzungen](use-roslyn-analyzers.md#suppress-violations).

Ab Visual Studio 2019 Version 16,3 können Sie die Quell Code Analyse deaktivieren oder bei Bedarf ausführen. Sie sollten ein Upgrade auf Visual Studio 2019 durchführen.

## <a name="legacy-analysis"></a>Legacyanalyse

Sie können die Legacy-und buildzeitanalyse auf der Eigenschaften Seite für die **Code Analyse** deaktivieren. Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der Legacy Code Analyse](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Verstöße unterdrücken](use-roslyn-analyzers.md#suppress-violations)
- [Gewusst wie: Aktivieren und Deaktivieren der Legacy Code Analyse](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
