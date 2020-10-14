---
title: Codeanalyse mithilfe von Roslyn-Analysetools
ms.date: 09/01/2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 72e6193d850d351dacc5361d5053fe8f06b2d4bf
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860488"
---
# <a name="overview-of-source-code-analysis"></a>Übersicht über Quellcode-Analyse

Analysetools der .NET Compiler Platform (Roslyn) analysieren Ihren C#- oder Visual Basic-Code auf Stil, Qualität, Verwaltbarkeit, Design und unter weiteren Aspekten. Diese Prüfung oder Analyse wird während der Entwurfszeit in allen geöffneten Dateien durchgeführt.

Analysetools können in folgende Gruppen unterteilt werden:

- [Codeformat](/visualstudio/ide/editorconfig-code-style-settings-reference?view=vs-2019&preserve-view=true#convention-categories)-Analysetools sind in Visual Studio integriert. Die Diagnose-ID oder der Code für diese Analysetools ist vom Format IDExxxx, z. B. IDE0067. Sie können Einstellungen auf der [Text-Editor-Optionenseite](../ide/code-styles-and-code-cleanup.md) oder in einer [EditorConfig-Datei](/dotnet/fundamentals/code-analysis/code-style-rule-options) konfigurieren. Ab .NET 5.0 sind Codeformat-Analysetools im .NET SDK enthalten und können als Buildwarnungen oder -Fehler strikt erzwungen werden. Weitere Informationen finden Sie [hier](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis).

- Tools zur Analyse der [Codequalität](/dotnet/fundamentals/code-analysis/quality-rules/index) sind jetzt im .NET 5 SDK enthalten und standardmäßig aktiviert. Die Diagnose-ID oder der Code für diese Analysetools hat das Format CAxxxx, z. B. CA1822. Weitere Informationen finden Sie unter [Analyse der .NET-Codequalität](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis).

- Sie können Analysetools von Drittanbietern als Visual Studio-Erweiterung oder NuGet-Paket installieren. Analysetools von Drittanbietern wie [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [XUnit Analyzers](https://www.nuget.org/packages/xunit.analyzers/) und [Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/).

## <a name="severity-levels-of-analyzers"></a>Schweregrade von Analysetools

Jedes Analysetool verfügt über einen der folgenden Schweregrade:

| Schweregrad (Projektmappen-Explorer) | Schweregrad (EditorConfig-Datei) | Verhalten zur Buildzeit | Editor-Verhalten |
|-|-|-|
| Fehler | `error` | Verstöße werden als *Fehler* in der Fehlerliste und in der Befehlszeilen-Buildausgabe angezeigt und bewirken, dass Builds fehlschlagen.| Der betreffende Code wird mit einer roten Wellenlinie unterstrichen und in der Scrollleiste durch ein kleines rotes Feld markiert. |
| Warnung | `warning` | Verstöße werden als *Warnungen* in der Fehlerliste und in der Befehlszeilen-Buildausgabe angezeigt, bewirken aber nicht, dass Builds fehlschlagen. | Der betreffende Code wird mit einer grünen Wellenlinie unterstrichen und in der Scrollleiste durch ein kleines grünes Feld markiert. |
| Info | `suggestion` | Verstöße werden als *Meldungen* in der Fehlerliste angezeigt, in der Befehlszeilen-Buildausgabe hingegen gar nicht. | Der betreffende Code wird mit einer grauen Wellenlinie unterstrichen und in der Scrollleiste durch ein kleines graues Feld markiert. |
| Ausgeblendet | `silent` | Für den Benutzer nicht sichtbar. | Für den Benutzer nicht sichtbar. Die Diagnose wird jedoch der IDE-Diagnose-Engine gemeldet. |
| Keine | `none` | Vollständig unterdrückt. | Vollständig unterdrückt. |
| Standard | `default` | Entspricht dem Standardschweregrad der Regel. Um den Standardwert für eine Regel zu ermitteln, ziehen Sie in der Eigenschaftenfenster zu Rate. | Entspricht dem Standardschweregrad der Regel. |

Wenn ein Analysetool Regelverstöße findet, werden sie im Code-Editor (als *Wellenlinie* unter dem fehlerhaften Code) und im Fenster „Fehlerliste“ angezeigt.

![Vom Analysetool gefundene Verstöße im Fenster „Fehlerliste“](../code-quality/media/code-analysis-error-list.png)

Die in der Fehlerliste gemeldeten vom Analysetool gefundenen Verstöße stimmen mit der [Einstellung für den Schweregrad der Regel](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) überein. Außerdem werden vom Analysetool gemeldete Verstöße auch im Code-Editor als Wellenlinie unter dem fehlerhaften Code angezeigt. In der folgenden Abbildung werden drei Verstöße angezeigt &mdash; ein Fehler (rote Wellenlinie), eine Warnung (grüne Wellenlinie) und ein Vorschlag (drei graue Punkte):

![Wellenlinien im Code-Editor in Visual Studio](media/diagnostics-severity-colors.png)

Viele Analysetoolregeln oder *-diagnosen* verfügen über mindestens einen *Codefix*, den Sie zur Korrektur von Regelverstößen anwenden können. Codekorrekturen werden zusammen mit anderen [schnellen Aktionen](../ide/quick-actions.md) im Fehlerbehebungsmenü (Glühbirnensymbol) angezeigt. Weitere Informationen zu diesen Codefixen finden Sie unter [Häufige schnelle Aktionen](../ide/quick-actions.md).

![Verstoß im Analysetool und Codefix mithilfe einer schnellen Aktion](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>Konfigurieren von Analysetool-Schweregraden

Sie können den Schweregrad von Analysetoolregeln oder -*diagnosen* in einer [EditorConfig-Datei](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) oder im [Glühbirnenmenü](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu) konfigurieren.

Analysetools können auch so konfiguriert werden, dass sie den Code zur Erstellungszeit überprüfen und während Ihrer Eingabe aktiv sind. Sie können den Bereich der Livecodeanalyse konfigurieren, um die Ausführung nur auf das aktuelle Dokument, alle geöffneten Dokumente oder die gesamte Projektmappe zu beschränken. Weitere Informationen finden Sie unter [How to: Configure the scope of live code analysis (Vorgehensweise: Konfigurieren des Bereichs der Livecodeanalyse)](./configure-live-code-analysis-scope-managed-code.md).

> [!TIP]
> Buildfehler und Warnungen von Codeanalysetools werden nur angezeigt, wenn die Analysetools als NuGet-Paket installiert wurden. Die integrierten Analysetools wie IDE0067 und IDE0068 werden nie während des Buildvorgangs ausgeführt.

## <a name="nuget-package-versus-vsix-extension"></a>NuGet-Paket im Vergleich zur VSIX-Erweiterung

Analysetools von Drittanbietern können mithilfe eines NuGet-Pakets pro Projekt installiert werden. Einige sind auch als Visual Studio-Erweiterung verfügbar. Dann können Sie sie in jeder Projektmappe anwenden, die Sie in Visual Studio öffnen. Es gibt einige grundsätzliche Verhaltensunterschiede zwischen diesen beiden Methoden zum [Installieren von Analysetools](../code-quality/install-roslyn-analyzers.md).

### <a name="scope"></a>Bereich

Wenn Sie Analysetools als Visual Studio-Erweiterung installieren, werden diese auf Projektmappenebene und für alle Instanzen von Visual Studio angewandt. Wenn Sie die Analysetools als NuGet-Paket installieren, was wir Ihnen empfehlen, werden die Tools nur für das Projekt angewandt, in dem das NuGet-Paket installiert wurde. Analysetools, die als NuGet-Pakete in Teamumgebungen installiert wurden, sind relevant für *alle Entwickler*, die an diesem Projekt arbeiten.

### <a name="build-errors"></a>Buildfehler

Damit zur Erstellungszeit Regeln erzwungen werden, auch über die Befehlszeile oder als Teil eines Continuous Integration-Builds (CI), können Sie eine der folgenden Optionen wählen:

- Erstellen Sie ein .NET 5.0-Projekt, das im .NET SDK standardmäßig Analysetools enthält. Die Codeanalyse ist für Projekte, die auf .NET 5.0 oder höher ausgerichtet sind, standardmäßig aktiviert. Sie können die Codeanalyse für Projekte aktivieren, die auf frühere Versionen von .NET abzielen, indem Sie die Eigenschaft [EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) auf „True“ festlegen.

- Installieren von Analysetools als NuGet-Paket. Warnungen und Fehler der Analysetools erscheinen nicht im Buildbericht, wenn Sie die Analysetools als Erweiterung installieren.

Der folgende Screenshot zeigt die Befehlszeilen-Buildausgabe vom Erstellen eines Projekts an, das einen Regelverstoß des Analysetools enthält:

![MSBuild-Ausgabe mit Regelverstoß](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>Regelschweregrad

Den Regelschweregrad von Analysetools, die als Visual Studio-Erweiterung installiert wurden, können Sie nicht konfigurieren. Um den [Regelschweregrad](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) zu konfigurieren, installieren Sie die Analysetools als NuGet-Paket.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Installieren von Codeanalysetools in Visual Studio](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Verwenden von Codeanalysetools in Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Weitere Informationen

- [FAQ zu Analysetools](analyzers-faq.md)
- [Schreiben Ihres eigenen Codeanalysetools](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)