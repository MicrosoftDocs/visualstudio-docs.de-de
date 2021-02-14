---
title: Generieren von Codemetriken über die IDE oder über die Befehlszeile
ms.date: 11/02/2018
description: Erfahren Sie, wie Sie Codemetrikdaten in Visual Studio generieren. Weitere Informationen finden Sie unter Verwenden von Projektmappen-Explorer, einer Regel Satz Datei, der Befehlszeile oder einem Menübefehl.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa0512e5d29cb1b5c5a39715e34667803b752795
ms.sourcegitcommit: 04954be0c4373f82f79181e1a5e7812be4d3e1f7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496261"
---
# <a name="how-to-generate-code-metrics-data"></a>Gewusst wie: Generieren von Codemetrikdaten

Sie können Codemetrikdaten auf drei Arten generieren:

- Durch Aktivieren von [.NET-Code Qualitätsanalysen](#net-code-quality-analyzers-code-metrics-rules) und Aktivieren der vier Code metrikregeln (Wartbarkeit), die Sie enthält.

- Durch Auswählen des Menübefehls [   >  **Code Metrik berechnen**](#calculate-code-metrics-menu-command) in Visual Studio.

- In der [Befehlszeile](#command-line-code-metrics) für c#-und Visual Basic-Projekte.

## <a name="net-code-quality-analyzers-code-metrics-rules"></a>Code metrikregeln für .net-Codequalität-Analysen

Die .NET-Code Qualitätsanalysen enthalten mehrere Regeln für [codemetrikanalytiker](roslyn-analyzers-overview.md) :

- [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)
- [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)
- [CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)
- [CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)

Diese Regeln sind standardmäßig deaktiviert, aber Sie können Sie über [**Projektmappen-Explorer**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) oder eine [Editor config](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) -Datei aktivieren. Wenn Sie z. b. Regel CA1502 als Warnung aktivieren möchten, enthält die Datei Editor config den folgenden Eintrag:

```cs
dotnet_diagnostic.CA1502.severity = warning
```

### <a name="configuration"></a>Konfiguration

Sie können die Schwellenwerte konfigurieren, bei denen die codemetrikregeln ausgelöst werden.

1. Erstellen einer Textdatei Beispielsweise können Sie *CodeMetricsConfig.txt* benennen.

2. Fügen Sie die gewünschten Schwellenwerte der Textdatei im folgenden Format hinzu:

   ```txt
   CA1502: 10
   ```

   In diesem Beispiel ist die Regel [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) so konfiguriert, dass Sie ausgelöst wird, wenn die zyklomatische Komplexität einer Methode größer als 10 ist.

3. Markieren Sie im **Eigenschaften** Fenster von Visual Studio oder in der Projektdatei die Buildaktion der Konfigurationsdatei als [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Beispiel:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Menübefehl "Code Metrik berechnen"

Generieren Sie Codemetriken für ein oder alle geöffneten Projekte in der IDE, indem Sie das  >  Menü **Code Metrik** analysieren verwenden.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generieren von Codemetrikergebnissen für eine gesamte Projekt Mappe

Sie können Code Metrikergebnisse für eine gesamte Lösung auf eine der folgenden Arten generieren:

- Wählen Sie in der Menüleiste **Analyse**  >  **Code Metrik** für Projekt Mappe berechnen aus  >  .

- Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Lösung, und wählen Sie dann **Codemetriken berechnen** aus.

- Wählen Sie im Fenster **Code Metrikergebnisse** die Schaltfläche **Code Metrik für Projekt Mappe berechnen aus** .

Die Ergebnisse werden generiert, und das Fenster **Code Metrikergebnisse** wird angezeigt. Um die Ergebnis Details anzuzeigen, erweitern Sie die Struktur in der Spalte **Hierarchie** .

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generieren von Codemetrikergebnissen für ein oder mehrere Projekte

1. Wählen Sie in **Projektmappen-Explorer** mindestens ein Projekt aus.

1. **Wählen Sie** in der Menüleiste die Option  >  **Code Metrik**  >  **für ausgewählte Projekte** berechnen aus.

Die Ergebnisse werden generiert, und das Fenster **Code Metrikergebnisse** wird angezeigt. Um die Ergebnis Details anzuzeigen, erweitern Sie die Struktur in der **Hierarchie**.

::: moniker range="vs-2017"

> [!NOTE]
> Der Befehl **Code Metriken berechnen** funktioniert nicht für .net Core-und .NET Standard-Projekte. Zum Berechnen von Codemetriken für ein .net Core-oder .NET Standard Projekt können Sie folgende Aktionen ausführen:
>
> - Berechnen Sie Codemetriken stattdessen über die [Befehlszeile](#command-line-code-metrics) .
>
> - Upgrade auf [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Befehlszeilencodemetriken

Sie können Codemetrikdaten über die Befehlszeile für c#-und Visual Basic Projekte für .NET Framework-, .net Core-und .NET Standard-apps generieren. Zum Ausführen von Codemetriken über die Befehlszeile installieren Sie das [nuget-Paket "Microsoft. Code Analysis. Metrics](#microsoftcodeanalysismetrics-nuget-package) ", oder erstellen Sie die [Metrics.exe](#metricsexe) ausführbare Datei.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft. Code Analysis. Metrics-nuget-Paket

Die einfachste Möglichkeit zum Generieren von Codemetrikdaten über die Befehlszeile besteht darin, das nuget-Paket [Microsoft. Code Analysis. Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) zu installieren. Nachdem Sie das Paket installiert haben, führen Sie `msbuild /t:Metrics` aus dem Verzeichnis aus, das die Projektdatei enthält. Beispiel:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

Sie können den Namen der Ausgabedatei überschreiben, indem Sie angeben `/p:MetricsOutputFile=<filename>` . Sie können auch Code Metrikdaten im [Legacy Stil](#previous-versions) erhalten, indem Sie angeben `/p:LEGACY_CODE_METRICS_MODE=true` . Beispiel:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Ausgabe von Codemetriken

Die generierte XML-Ausgabe hat folgendes Format:

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

::: moniker-end
::: moniker range="vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

Wenn Sie das nuget-Paket nicht installieren möchten, können Sie die ausführbare *Metrics.exe* direkt generieren und verwenden. So generieren Sie die *Metrics.exe* ausführbare Datei:

1. Klonen Sie das Repository [dotnet/Roslyn-Analyzers](https://github.com/dotnet/roslyn-analyzers) .
2. Öffnen Sie Developer-Eingabeaufforderung für Visual Studio als Administrator.
3. Führen Sie im Stamm **Verzeichnis des Roslyn-Analyzers-** Repository den folgenden Befehl aus: `Restore.cmd`
4. Wechseln Sie in das Verzeichnis *src\tools\metrics*.
5. Führen Sie den folgenden Befehl aus, um das Projekt " **Metrics. csproj** " zu erstellen:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Eine ausführbare Datei mit dem Namen *Metrics.exe* wird im Verzeichnis *artifakts\bin* unter dem Repository root generiert.

#### <a name="metricsexe-usage"></a>Metrics.exe Verwendung

Um *Metrics.exe* auszuführen, stellen Sie ein Projekt oder eine Projekt Mappe und eine XML-Ausgabedatei als Argumente bereit. Beispiel:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Legacy Modus

Sie können *Metrics.exe* im *Legacy Modus* erstellen. Die Legacy Modus-Version des Tools generiert Metrikwerte, die näher an den [von den älteren Versionen des Tools generierten](#previous-versions)Werten liegen. Außerdem generiert *Metrics.exe* im Legacy Modus Codemetriken für denselben Satz von Methoden Typen, für die vorherige Versionen des Tools Codemetriken generiert haben. Beispielsweise werden keine Codemetrikdaten für die Feld-und Eigenschafteninitialisierer generiert. Der Legacy Modus ist aus Gründen der Abwärtskompatibilität nützlich, oder Sie verfügen über Code-Check-in-Gates, die auf codemetriknummern basieren Der Befehl zum Erstellen *Metrics.exe* im Legacy Modus lautet:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Weitere Informationen finden Sie unter [Aktivieren der Erstellung von Codemetriken im Legacy Modus](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Vorherige Versionen

::: moniker range=">=vs-2019"
Visual Studio 2015 enthielt ein befehlszeilencodemetriktool, das auch als *Metrics.exe* bezeichnet wurde. Diese vorherige Version des Tools hat eine binäre Analyse, d. h. eine assemblybasierte Analyse, durchgeführt. Die neuere Version des *Metrics.exe* Tools analysiert stattdessen Quellcode. Da es sich bei dem neueren *Metrics.exe* Tool um Quell Code basiert handelt, können sich die Metrikergebnisse der Befehlszeilen Code von der Visual Studio-IDE und früheren Versionen von *Metrics.exe* unterscheiden. Ab Visual Studio 2019 analysiert die Visual Studio-IDE Quellcode wie das Befehlszeilen Tool, und die Ergebnisse müssen identisch sein.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 enthielt ein befehlszeilencodemetriktool, das auch als *Metrics.exe* bezeichnet wurde. Diese vorherige Version des Tools hat eine binäre Analyse, d. h. eine assemblybasierte Analyse, durchgeführt. Das neue *Metrics.exe* Tool analysiert stattdessen Quellcode. Da es sich bei dem neuen *Metrics.exe* Tool um Quell Code basiert, unterscheiden sich die Ergebnisse der Befehlszeilen Code Metrik von den Ergebnissen, die von der Visual Studio-IDE und früheren Versionen von *Metrics.exe* generiert werden.
::: moniker-end

Das neue befehlszeilencodemetrik-Tool berechnet Metriken, auch wenn Quell Code Fehler vorhanden sind, solange die Projekt Mappe und das Projekt geladen werden können.

#### <a name="metric-value-differences"></a>Unterschiede bei Metriken

::: moniker range=">=vs-2019"
Beginnend mit Visual Studio 2019, Version 16,4 und Microsoft. Code Analysis. metics (2.9.5), `SourceLines` und `ExecutableLines` Ersetzen Sie die vorherige `LinesOfCode` Metrik. Beschreibungen der neuen Metriken finden Sie unter [codemetrikwerte](../code-quality/code-metrics-values.md). Die `LinesOfCode` Metrik ist im Legacy Modus verfügbar.
::: moniker-end
::: moniker range="vs-2017"
Die `LinesOfCode` Metrik ist im neuen befehlszeilencodemetriktool präziser und zuverlässiger. Es ist unabhängig von CodeGen-unterschieden und ändert sich nicht, wenn sich das Toolset oder die Laufzeit ändert. Das neue Tool zählt tatsächliche Codezeilen, einschließlich leerer Zeilen und Kommentare.
::: moniker-end

Andere Metriken wie `CyclomaticComplexity` und `MaintainabilityIndex` verwenden dieselben Formeln wie frühere Versionen von *Metrics.exe*, aber das neue Tool zählt die Anzahl der `IOperations` (logischen Quell Anweisungen) anstelle von Intermediate Language (IL)-Anweisungen. Die Zahlen unterscheiden sich geringfügig von den Werten, die von der Visual Studio-IDE und früheren Versionen von *Metrics.exe* generiert werden.

## <a name="see-also"></a>Weitere Informationen

- [Verwenden des Fensters "Code Metrikergebnisse"](../code-quality/working-with-code-metrics-data.md)
- [Codemetrikwerte](../code-quality/code-metrics-values.md)