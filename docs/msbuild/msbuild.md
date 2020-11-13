---
title: MSBuild | Microsoft-Dokumentation
description: Erfahren Sie, wie die MSBuild-Plattform (Microsoft-Build-Engine) eine Projektdatei mit einem XML-Schema zum Steuern von Builds bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7e42452d8ee59142c4f906d928378d1fb44bf67
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904516"
---
# <a name="msbuild"></a>MSBuild

Die Microsoft-Build-Engine ist eine Plattform zum Erstellen von Anwendungen. Diese Engine, die auch als MSBuild bezeichnet wird, stellt ein XML-Schema für Projektdateien bereit, mit dem sich steuern lässt, wie die Buildplattform Software und Prozesse erstellt und verarbeitet. Visual Studio verwendet MSBuild, MSBuild ist jedoch nicht von Visual Studio abhängig. Wenn Sie *msbuild.exe* im Projekt oder in der Projektmappendatei aufrufen, können Sie Produkte in Umgebungen orchestrieren und erstellen, in denen Visual Studio nicht installiert ist.

 Visual Studio verwendet MSBuild, um verwaltete Projekte zu laden und zu erstellen. Die Projektdateien in Visual Studio ( *CSPROJ* -, *VBPROJ* -, *VCXPROJ* -Dateien und andere) enthalten MSBuild-XML-Code, der ausgeführt wird, wenn Sie ein Projekt mithilfe der IDE erstellen. Alle erforderlichen Einstellungen und Buildprozesse werden für die reguläre Entwicklungsarbeit in Visual Studio-Projekte importiert. Sie können diese jedoch in Visual Studio oder mithilfe eine XML-Editors erweitern oder ändern.

 Weitere Informationen zu MSBuild für C++ finden Sie unter [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Die folgenden Beispiele veranschaulichen, wann es sich anbietet, MSBuild zum Auszuführen von Builds über die Befehlszeile anstatt über die Visual Studio-IDE aufzurufen.

- Visual Studio ist nicht installiert. ([Hier können Sie MSBuild ohne Visual Studio herunterladen.](https://visualstudio.microsoft.com/downloads/?q=build+tools))

- Sie möchten die 64-Bit-Version von MSBuild verwenden. Diese Version von MSBuild ist normalerweise nicht erforderlich, ermöglicht MSBuild jedoch den Zugriff auf mehr Arbeitsspeicher.

- Sie möchten einen Build in mehreren Prozessen ausführen. Sie können die IDE jedoch verwenden, um die gleichen Ergebnisse in Projekten in C++ und C# zu erzielen.

- Sie möchten das Buildsystem ändern. Möglicherweise möchten Sie z. B. die folgenden Aktionen aktivieren:

  - Dateien vorverarbeiten, bevor sie den Compiler erreichen.

  - Kopieren Sie die Buildausgaben an eine andere Stelle.

  - Erstellen Sie komprimierte Dateien aus den Buildausgaben.

  - Führen Sie einen Nachverarbeitungsschritt durch. Beispielsweise können Sie eine Assembly mit einer anderen Version stempeln.

Sie können Code in der Visual Studio-IDE schreiben, aber Builds mit MSBuild ausführen. Des Weiteren können Sie Code in der IDE auf einem Entwicklungscomputer schreiben, MSBuild jedoch über die Befehlszeile ausführen und damit Code kompilieren, der von mehreren Entwicklern integriert wurde. Außerdem können Sie die [.NET Core-Befehlszeilenschnittstelle (command-line interface, CLI)](/dotnet/core/tools/) verwenden, die MSBuild für das Kompilieren von .NET Core-Projekten verwendet.

> [!NOTE]
> Mit Azure Pipelines lassen sich Anwendungen automatisch kompilieren, testen und bereitstellen. Das Buildsystem kann Builds automatisch ausführen, wenn Entwickler Code z. B. als Teil einer fortlaufenden Integrationsstrategie oder gemäß einem Zeitplan (z. B. bei einem Build für einen nächtlichen Buildüberprüfungstest) einchecken. Azure Pipelines kompiliert Code mithilfe von MSBuild. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

Dieser Artikel enthält eine Übersicht über MSBuild. Ein Einführungstutorial finden Sie unter [Exemplarische Vorgehensweise: Verwenden von MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Verwenden von MSBuild an einer Eingabeaufforderung

 Um MSBuild an einer Eingabeaufforderung auszuführen, übergeben Sie eine Projektdatei mit den entsprechenden Befehlszeilenoptionen an *MSBuild.exe*. Über Befehlszeilenoptionen können Sie Eigenschaften festlegen, bestimmte Ziele ausführen und weitere Optionen für die Steuerung des Buildprozesses festlegen. Beispielsweise verwenden Sie die folgende Befehlszeilensyntax zum Erstellen der Datei *MyProj.proj* , deren `Configuration`-Eigenschaft auf `Debug` festgelegt ist.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Weitere Informationen zu MSBuild-Befehlszeilenoptionen finden Sie in der [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Bevor Sie ein Projekt herunterladen, bestimmen Sie die Vertrauenswürdigkeit des Codes.

## <a name="project-file"></a>Projektdatei

 MSBuild verwendet ein einfaches und erweiterbares XML-basiertes Projektdateiformat. Mithilfe des MSBuild-Projektdateiformats können Entwickler die zu erstellenden Elemente beschreiben und angeben, wie diese Elemente für verschiedene Betriebssysteme und Konfigurationen erstellt werden müssen. Zusätzlich können Entwickler im Projektdateiformat wiederverwendbare Buildregeln erstellen, die in separate Dateien unterteilt werden können, um Builds im Produkt über verschiedene Projekte hinweg konsistent auszuführen.

 In den folgenden Abschnitten werden einige der Grundelemente des MSBuild-Projektdateiformats beschrieben. Ein Tutorial zum Erstellen einer einfachen Projektdatei finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer neuen MSBuild-Projektdatei](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="properties"></a><a name="BKMK_Properties"></a> Eigenschaften

 Eigenschaften stellen Schlüssel/Wert-Paare dar, die zur Konfiguration von Builds verwendet werden können. Eigenschaften werden deklariert, indem ein Element mit dem Namen der jeweiligen Eigenschaft als untergeordnetes Element eines [PropertyGroup](../msbuild/propertygroup-element-msbuild.md)-Elements erstellt wird. Durch den folgenden Code wird beispielsweise die Eigenschaft `BuildDir` mit dem Wert `Build` erstellt.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Sie können eine Eigenschaft bedingt definieren, indem Sie ein `Condition`-Attribut im Element platzieren. Sofern wenn die Bedingung nicht `true` ergibt, wird der Inhalt bedingter Elemente ignoriert. Im folgenden Beispiel wird das `Configuration`-Element definiert, wenn es noch nicht definiert wurde.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 In der Projektdatei wird mit der Syntax $(\<PropertyName>) auf Eigenschaften verwiesen. Beispielsweise wird mit `$(BuildDir)` und `$(Configuration)` auf die Eigenschaft in den vorangehenden Beispielen verwiesen.

 Weitere Informationen zu Eigenschaften finden Sie unter [MSBuild Properties (MSBuild-Eigenschaften)](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a> Elemente

 Elemente sind Eingaben in das Buildsystem und stellen in der Regel Dateien dar. Elemente werden auf Grundlage von benutzerdefinierten Elementnamen in Elementtypen gruppiert. Diese Elementtypen können als Parameter für Aufgaben verwendet werden, die mithilfe der einzelnen Elemente die Schritte des Buildprozesses ausführen.

 In der Projektdatei werden Elemente deklariert, indem ein Element mit dem Namen des jeweiligen Elementtyps als untergeordnetes Element eines [ItemGroup](../msbuild/itemgroup-element-msbuild.md)-Elements erstellt wird. Im folgenden Code wird z. B. der Elementtyp `Compile` mit zwei Dateien erstellt.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Auf Elementtypen kann in der gesamten Projektdatei mit der Syntax @(\<ItemType>) verwiesen werden. Auf den Elementtyp im Beispiel wird beispielsweise mit `@(Compile)` verwiesen.

 In MSBuild muss bei Elementen und Attributnamen die Groß-/Kleinschreibung beachtet werden. Bei Namen von Eigenschaften, Elementen und Metadaten ist dies nicht der Fall. Im folgenden Beispiel werden der `Compile`-Elementtyp oder der `comPile`-Elementtyp oder eine beliebige andere Fallvariante erstellt und der Wert "one.cs;two.cs" zugewiesen.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 Elemente können mit Platzhalterzeichen deklariert werden und zusätzliche Metadaten für erweiterte Buildszenarios enthalten. Weitere Informationen zu Elementen finden Sie unter [Items](../msbuild/msbuild-items.md) (MSBuild-Elemente).

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Aufgaben

 Aufgaben sind Einheiten ausführbaren Codes, die in MSBuild-Projekten zum Ausführen von Buildvorgängen verwendet werden. Eine Aufgabe kann beispielsweise Eingabedateien kompilieren oder ein externes Tool ausführen. Aufgaben können wiederverwendet werden, auch von verschiedenen Entwicklern in unterschiedlichen Projekten.

 Die Ausführungslogik einer Aufgabe wird in verwaltetem Code geschrieben und MSBuild mithilfe des [UsingTask](../msbuild/usingtask-element-msbuild.md)-Elements zugeordnet. Sie können eine eigene Aufgabe schreiben, indem Sie einen verwalteten Typ erstellen, der die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert. Weitere Informationen zum Erstellen von Aufgaben finden Sie unter [Schreiben von Aufgaben](../msbuild/task-writing.md).

 MSBuild umfasst allgemeine Aufgaben, die Sie an Ihre jeweiligen Anforderungen anpassen können. Beispiele hierfür sind [Copy](../msbuild/copy-task.md) zum Kopieren von Dateien, [MakeDir](../msbuild/makedir-task.md) zum Erstellen von Verzeichnissen und [Csc](../msbuild/csc-task.md) zum Kompilieren von Visual C#-Quellcodedateien. Eine Liste der verfügbaren Aufgaben sowie Informationen zu ihrer jeweiligen Verwendung finden Sie unter [MSBuild-Aufgabenreferenz](../msbuild/msbuild-task-reference.md).

 Eine Aufgabe wird in einer MSBuild-Projektdatei ausgeführt, indem ein Element mit dem Namen der Aufgabe als untergeordnetes Element eines [Target](../msbuild/target-element-msbuild.md)-Elements erstellt wird. Die meisten Aufgaben akzeptieren Parameter, die als Attribute des Elements übergeben werden. Als Parameter können Eigenschaften und Elemente von MSBuild verwendet werden. Der folgende Code ruft z.B. die [MakeDir](../msbuild/makedir-task.md)-Aufgabe auf und übergibt ihr den im vorangehenden Beispiel deklarierten Wert der Eigenschaft `BuildDir`.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Weitere Informationen zu Aufgaben finden Sie unter [Aufgaben](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a>Ziele

 Durch Ziele werden Aufgaben in einer bestimmten Reihenfolge gruppiert und Abschnitte der Projektdatei als Einstiegspunkte in den Buildprozess verfügbar gemacht. Ziele werden oft in logischen Abschnitten gruppiert, um ihre Lesbarkeit zu erhöhen und Erweiterungen zu ermöglichen. Wenn die Buildschritte in Ziele unterteilt werden, können Sie einen Teil des Buildprozesses in anderen Zielen aufrufen, ohne diesen Codeabschnitt in jedes Ziel kopieren zu müssen. Wenn mehrere Einstiegspunkte in den Buildprozess die Erstellung von Verweisen erfordern, können Sie beispielsweise ein Ziel erstellen, durch das Verweise erstellt werden, und dieses Ziel anschließend über jeden Einstiegspunkt ausführen, für den es erforderlich ist.

 Ziele werden in der Projektdatei mithilfe des [Target](../msbuild/target-element-msbuild.md)-Elements deklariert. Der folgende Code erstellt z.B. ein Ziel mit dem Namen `Compile`, das anschließend die [Csc](../msbuild/csc-task.md)-Aufgabe mit der im vorangehenden Beispiel deklarierten Elementliste aufruft.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 In fortgeschritteneren Szenarios können Ziele die zwischen verschiedenen Zielen bestehenden Beziehungen beschreiben und Abhängigkeitsanalysen durchführen. Wenn das jeweilige Ziel aktuell ist, können daher ganze Bereiche des Buildprozesses übersprungen werden. Weitere Informationen zu Zielen finden Sie unter [Targets (MSBuild-Ziele)](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Buildprotokolle

 Sie können Buildfehler, Warnungen und Meldungen in der Konsole oder auf anderen Ausgabegeräten protokollieren. Weitere Informationen finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md) und [Protokollierung in MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Verwenden von MSBuild in Visual Studio

 Visual Studio verwendet das MSBuild-Projektdateiformat zum Speichern von Erstellungsinformationen zu verwalteten Projekten. Die Projekteinstellungen, die mithilfe der Visual Studio-Schnittstelle hinzugefügt oder geändert werden, werden in der *.\*proj* -Datei gespeichert, die für das jeweilige Projekt generiert wird. Visual Studio erstellt verwaltete Projekte mithilfe einer gehosteten Instanz von MSBuild. Das bedeutet, dass ein verwaltetes Projekt mit demselben Ergebnis entweder in Visual Studio oder über eine Befehlszeile erstellt werden kann (auch wenn Visual Studio nicht installiert ist).

 Ein Tutorial zur Verwendung von MSBuild in Visual Studio finden Sie unter [Exemplarische Vorgehensweise: Verwenden von MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a>Festlegen von Zielversionen

 Mit Visual Studio können Sie eine Anwendung für bestimmte Versionen von .NET Framework kompilieren. Sie können eine Anwendung z. B. zweimal kompilieren: einmal so, dass sie unter .NET Framework 2.0 auf einer 32-Bit-Plattform ausgeführt werden kann, und einmal so, dass sie auf .NET Framework 4.5 auf einer 64-Bit-Plattform ausgerichtet ist. Die Möglichkeit, für mehr als ein Framework zu kompilieren, wird Festlegung von Zielversionen genannt.

 In Folgenden sind einige Vorteile der Festlegung auf mehrere Zielversionen aufgeführt:

- Sie können Anwendungen für frühere Versionen von .NET Framework entwickeln, z. B. Version 2.0, 3.0 oder 3.5.

- Sie können auch für andere Frameworks als .NET Framework entwickeln, z. B. für Silverlight.

- Sie können auf ein *Frameworkprofil* abzielen, das einer vordefinierten Teilmenge eines Zielframeworks entspricht.

- Wenn ein neues Service Pack für die aktuelle .NET Framework-Version veröffentlicht wird, können Sie auch dafür Software schreiben.

- Durch die Festlegung von Zielversionen wird garantiert, dass von einer Anwendung nur die im Zielframework und die auf der Zielplattform verfügbaren Funktionen verwendet werden.

Weitere Informationen finden Sie unter [Multitargeting](../msbuild/msbuild-multitargeting-overview.md) (Festlegen von Zielversionen).

## <a name="see-also"></a>Siehe auch

| Titel | Beschreibung |
| - | - |
| [Exemplarische Vorgehensweise: Erstellen einer neuen MSBuild-Projektdatei](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Hier wird veranschaulicht, wie eine Projektbasisdatei nur mit einem Texteditor inkrementell erstellt wird. |
| [Exemplarische Vorgehensweise: Verwenden von MSBuild](../msbuild/walkthrough-using-msbuild.md) | Die Bausteine von MSBuild werden eingeführt, und es wird gezeigt, wie MSBuild-Projekte erstellt, bearbeitet und debuggt werden, ohne die Visual Studio-IDE zu schließen. |
| [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md) | Stellt die vier Bausteine von MSBuild dar: Eigenschaften, Elemente, Ziele und Aufgaben. |
| [Elemente](../msbuild/msbuild-items.md) | Beschreibt die allgemeinen Konzepte hinter dem MSBuild-Dateiformat sowie das Zusammenwirken der einzelnen Teile. |
| [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md) | Hierin werden Eigenschaften und Eigenschaftenauflistungen eingeführt. Eigenschaften sind Schlüssel/Wert-Paare, die zur Konfiguration von Builds verwendet werden können. |
| [Ziele](../msbuild/msbuild-targets.md) | Es wird erläutert, wie Aufgaben in einer bestimmten Reihenfolge gruppiert werden und wie Sie es ermöglichen, dass Abschnitte des Buildprozesses über die Befehlszeile aufgerufen werden. |
| [Aufgaben](../msbuild/msbuild-tasks.md) | Zeigt, wie eine Einheit von ausführbarem Code erstellt wird, die von MSBuild zum Ausführen unteilbarer Buildvorgänge verwendet werden kann. |
| [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen) | Hier wird erläutert, wie das `Condition`-Attribut in einem MSBuild-Element verwendet wird. |
| [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md) | Hier werden die Batchverarbeitung, das Ausführen von Transformationen, die Festlegung von Zielversionen sowie andere erweiterte Verfahren veranschaulicht. |
| [Protokollierung in MSBuild](../msbuild/logging-in-msbuild.md) | Hier wird erläutert, wie Buildereignisse, Meldungen, Fehler protokolliert werden. |
| [So erstellt MSBuild Projekte](build-process-overview.md) | Beschreibt den internen Buildprozess, der in MSBuild verwendet wird. |
| [Zusätzliche Ressourcen](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Hierin werden Community- und Unterstützungsressourcen für weitere Informationen zu MSBuild aufgeführt. |

## <a name="reference"></a>Referenz

- [MSBuild-Referenz](../msbuild/msbuild-reference.md)\
 Links zu Themen mit Referenzinformationen.

- [Glossar](msbuild-glossary.md)\
 Hier werden allgemeine Begriffe zu MSBuild definiert.
