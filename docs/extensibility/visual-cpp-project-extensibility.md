---
title: Visual C++ Projekt Erweiterbarkeit
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1c699c835c6a53ec346dadb8bbbbf787aacc9206
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926033"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++ Projekt System-Erweiterbarkeit und toolsetintegration

Das Visual C++-Projekt System wird für vcxproj-Dateien verwendet. Es basiert auf dem [allgemeinen CPS (Common Project System) von Visual Studio](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) und bietet zusätzliche, C++ spezifische Erweiterungs Punkte für eine einfache Integration neuer Toolsets, buildarchitekturen und Zielplattformen.

## <a name="c-msbuild-targets-structure"></a>C++ MSBuild-Zielstruktur

Alle vcxproj-Dateien importieren diese Dateien:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Diese Dateien definieren nur wenig eigenständig. Stattdessen importieren Sie andere Dateien auf der Grundlage dieser Eigenschaftswerte:

- `$(ApplicationType)`

   Beispiele: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Dabei muss es sich um eine gültige Versions Zeichenfolge im Format major. Minor [. Build [. Revision]] handeln.

   Beispiele: 1,0, 10.0.0.0

- `$(Platform)`

   Die buildarchitektur mit dem Namen "Platform" aus historischen Gründen.

   Beispiele: Win32, x86, x64, Arm

- `$(PlatformToolset)`

   Beispiele: V140, v141, v141_xp, llvm

Diese Eigenschaftswerte geben Ordnernamen unter dem Stamm `$(VCTargetsPath)` Ordner an:

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*Anwendungstyp*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Formen*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Platformtoolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*Formen*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Platformtoolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

Der `$(VCTargetsPath)` \\ Ordner " *Platforms* " \\ wird verwendet `$(ApplicationType)` , wenn für Windows-Desktop Projekte leer ist.

### <a name="add-a-new-platform-toolset"></a>Hinzufügen eines neuen Platt Form Toolsets

Um ein neues Toolset hinzuzufügen, z. b. "mytoolset" für die vorhandene Win32-Plattform, erstellen Sie einen *mytoolset* -Ordner unter `$(VCTargetsPath)` *\\ Plattformen \\ Win32 \\ platformtoolsets \\*, und erstellen Sie *Toolset.* -Eigenschaften und *Toolset. targets* -Dateien darin.

Jeder Ordnername unter " *platformtoolsets* " wird im Dialogfeld " **Projekteigenschaften** " als verfügbares **Platt Form Toolset** für die angegebene Plattform angezeigt, wie hier gezeigt:

![Die Platt Form Toolset-Eigenschaft im Dialogfeld Eigenschaften Seiten des Projekts](media/vc-project-extensibility-platform-toolset-property.png "Die Platt Form Toolset-Eigenschaft im Dialogfeld Eigenschaften Seiten des Projekts")

Erstellen Sie ähnliche *mytoolset* -Ordner und *Toolset.* -Eigenschaften und *Toolset. targets* -Dateien in jedem vorhandenen Platt Form Ordner, den dieses Toolset unterstützt.

### <a name="add-a-new-platform"></a>Neue Plattform hinzufügen

Um eine neue Plattform hinzuzufügen, z. b. "myplatform", erstellen Sie einen *myplatform* -Ordner unter `$(VCTargetsPath)` *\\ \\ Plattformen*, und erstellen Sie *Platform. default.*-Eigenschaften, *Platform.*-Eigenschaften und *Platform. targets* -Dateien darin. Erstellen Sie außerdem den `$(VCTargetsPath)` Ordner *\\ Plattformen \\*<strong><em>myplatform</em></strong>*\\ \\ platformtoolsets* , und erstellen Sie mindestens ein Toolset darin.

Alle Ordnernamen im Ordner " *Platforms* " für jeden `$(ApplicationType)` und werden `$(ApplicationTypeRevision)` in der IDE als verfügbare **Platt Form** Auswahl für ein Projekt angezeigt.

![Die neue Platt Form Auswahl im Dialogfeld "Neue Projektplattform"](media/vc-project-extensibility-new-project-platform.png "Die neue Platt Form Auswahl im Dialogfeld "Neue Projektplattform"")

### <a name="add-a-new-application-type"></a>Neuen Anwendungstyp hinzufügen

Um einen neuen Anwendungstyp hinzuzufügen, erstellen Sie einen Ordner *myapplicationtype* unter `$(VCTargetsPath)` *\\ Anwendungstyp \\* , und erstellen Sie darin eine *default. defaults* -Datei. Mindestens eine Revision ist für einen Anwendungstyp erforderlich. Erstellen Sie daher auch den Ordner " `$(VCTargetsPath)` *\\ \\ myapplicationtype \\ 1,0" des Anwendungs Typs* , und erstellen Sie darin eine " *defaults. defaults* "-Datei. Sie sollten auch einen `$(VCTargetsPath)` *\\ applicationtype-Ordner " \\ myapplicationtype \\ 1,0 \\ Platforms* " erstellen und mindestens eine Plattform darin erstellen.

`$(ApplicationType)``$(ApplicationTypeRevision)`die Eigenschaften und sind in der Benutzeroberfläche nicht sichtbar. Sie werden in den Projektvorlagen definiert und können nach dem Erstellen des Projekts nicht mehr geändert werden.

## <a name="the-vcxproj-import-tree"></a>Die vcxproj-Importstruktur

Eine vereinfachte Struktur von Importen für Microsoft C++-Eigenschaften und Targets-Dateien sieht wie folgt aus:

> `$(VCTargetsPath)`\\*Microsoft. cpp. default.-Eigenschaften* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common.-Eigenschaften* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importbefore* \\ *Standard* \\ \* .  Eigenschaften \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Anwendungstyp* \\ `$(ApplicationType)` \\ *Default.* -Eigenschaften \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Anwendungstyp* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` \\ *Default.* -Eigenschaften \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Anwendungstyp* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` \\ *Platt* \\ `$(Platform)` Formen \\ *Platform. default.* -Eigenschaften \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importafter* \\ *Standard* \\ \* .  Eigenschaften

Windows-Desktop Projekte definieren nicht `$(ApplicationType)` , sodass Sie nur importieren

> `$(VCTargetsPath)`\\*Microsoft. cpp. default.-Eigenschaften* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common.-Eigenschaften* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importbefore* \\ *Standard* \\ \* .  Eigenschaften \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platt* \\ `$(Platform)` Formen \\ *Platform. default.* -Eigenschaften \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importafter* \\ *Standard* \\ \* .  Eigenschaften

Wir verwenden die- `$(_PlatformFolder)` Eigenschaft, um die Speicher `$(Platform)` Orte der Platt Form Ordner zu speichern. Diese Eigenschaft ist

> `$(VCTargetsPath)`\\*Formen*\\`$(Platform)`

für Windows-Desktop-Apps und

> `$(VCTargetsPath)`\\*Anwendungstyp* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` \\ *Plattformen*\\`$(Platform)`

für alles andere.

Die Eigenschaften Dateien werden in dieser Reihenfolge importiert:

> `$(VCTargetsPath)`\\*Microsoft. cpp.-Eigenschaften* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.-Eigenschaften* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform.-Eigenschaften* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importbefore* \\ \* .  Eigenschaften \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platformtoolsets* \\ `$(PlatformToolset)` \\ *Toolset.* -Eigenschaften \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importafter* \\ \* .  Eigenschaften

Die Targets-Dateien werden in dieser Reihenfolge importiert:

> `$(VCTargetsPath)`\\*Microsoft. cpp. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Current. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importbefore* \\ \* . *Ziele* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platformtoolsets* \\ `$(PlatformToolset)` \\ *Toolset. Target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importafter* \\ \* . *Ziele*

Wenn Sie einige Standardeigenschaften für das Toolset definieren müssen, können Sie den entsprechenden importbefore-und importafter-Ordnern Dateien hinzufügen.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Erstellen von Toolset.-Eigenschaften und Toolset. targets-Dateien

*Toolset.* -Eigenschaften und *Toolset. targets* -Dateien haben vollständige Kontrolle darüber, was während eines Builds geschieht, wenn dieses Toolset verwendet wird. Sie können auch die verfügbaren Debugger steuern, z. b. den Inhalt im Dialogfeld " **Eigenschaften Seiten** " und einige andere Aspekte des Projekt Verhaltens.

Obwohl ein Toolset den gesamten Buildprozess überschreiben kann, sollten Sie in der Regel nur das Toolset ändern oder einige Buildschritte hinzufügen oder andere Buildtools als Teil eines vorhandenen Buildprozesses verwenden. Um dieses Ziel zu erreichen, gibt es eine Reihe allgemeiner Eigenschaften und Zieldateien, die ihr Toolset importieren kann. Je nachdem, was das Toolset tun soll, können diese Dateien für die Verwendung als Importe oder als Beispiele nützlich sein:

- `$(VCTargetsPath)`\\*Microsoft. cppcommon. targets*

  Diese Datei definiert die Hauptbestandteile des systemeigenen Buildprozesses und importiert außerdem Folgendes:

  - `$(VCTargetsPath)`\\*Microsoft. cppbuild. targets*

  - `$(VCTargetsPath)`\\*Microsoft. buildsteps. targets*

  - `$(MSBuildToolsPath)`\\*Microsoft. Common. targets*

- `$(VCTargetsPath)`\\*Microsoft. cpp. Common.-Eigenschaften*

   Legt Standardwerte für Toolsets fest, die die Microsoft-Compiler und-Zielfenster verwenden.

- `$(VCTargetsPath)`\\*Microsoft. cpp. windowssdk.-Eigenschaften*

   Diese Datei bestimmt den Windows SDK Speicherort und definiert einige wichtige Eigenschaften für apps, die auf Windows abzielen.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrieren von toolsetspezifischen Zielen in den standardmäßigen C++-Buildprozess

Der standardmäßige C++-Buildprozess wird in " *Microsoft. cppcommon. targets*" definiert. Die Ziele, für die keine bestimmten Buildtools aufgerufen werden. Sie geben die wichtigsten Buildschritte, ihre Reihenfolge und die Abhängigkeiten an.

Der C++-Build umfasst drei Hauptschritte, die durch die folgenden Ziele dargestellt werden:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Da jeder Buildschritt unabhängig voneinander ausgeführt werden kann, können Ziele, die in einem Schritt ausgeführt werden, nicht auf den Elementgruppen und-Eigenschaften basieren, die in den Zielen definiert sind, die als Teil eines anderen Schritts ausgeführt werden. Diese Division ermöglicht bestimmte Optimierungen der Buildleistung. Obwohl Sie nicht standardmäßig verwendet wird, werden Sie trotzdem empfohlen, diese Trennung zu berücksichtigen.

Die Ziele, die in jedem Schritt ausgeführt werden, werden durch folgende Eigenschaften gesteuert:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Jeder Schritt verfügt auch über die Eigenschaften before und After.

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Beispiele für die Ziele, die in den einzelnen Schritten enthalten sind, finden Sie in der Datei *Microsoft. cppbuild. targets* :

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Wenn Sie sich die Ziele ansehen (z. b.), `_ClCompile` werden Sie feststellen, dass Sie nichts direkt selbst ausführen, sondern stattdessen von anderen Zielen abhängig sind, darunter `ClCompile` :

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` und andere buildtoolspezifische Ziele werden als leere Ziele in " *Microsoft. cppbuild. targets*" definiert:

```xml
<Target Name="ClCompile"/>
```

Da das `ClCompile` Ziel leer ist, wird keine wirkliche Buildaktion ausgeführt, es sei denn, es wird von einem Toolset überschrieben. Die toolsetziele können das Ziel überschreiben `ClCompile` , d. h., Sie können `ClCompile` nach dem Importieren von *Microsoft. cppbuild. targets* eine andere Definition enthalten:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Trotz des Namens, der vor der Implementierung der plattformübergreifenden Unterstützung durch Visual Studio erstellt wurde, `ClCompile` muss das Ziel nicht CL.exe aufgerufen werden. Mit den entsprechenden MSBuild-Tasks können auch clang-, gcc-oder andere Compiler aufgerufen werden.

Das `ClCompile` Ziel darf keine Abhängigkeiten außer dem Ziel aufweisen `SelectClCompile` , das erforderlich ist, damit der Befehl zur Kompilierung der einzelnen Dateien in der IDE funktioniert.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>In toolsetzielen zu verwendende MSBuild-Aufgaben

Um ein tatsächliches Buildtool aufzurufen, muss das Ziel eine MSBuild-Aufgabe aufrufen. Es gibt eine einfache [Exec-Aufgabe](../msbuild/exec-task.md) , mit der Sie eine Befehlszeile für die Ausführung angeben können. Buildtools verfügen jedoch in der Regel über viele Optionen, Eingaben. und Ausgaben, die für inkrementelle Builds nachverfolgt werden sollen. Daher ist es sinnvoller, spezielle Aufgaben für diese auszuführen. Beispielsweise übersetzt der `CL` Task MSBuild-Eigenschaften in CL.exe Switches, schreibt Sie in eine Antwortdatei und ruft CL.exe auf. Außerdem werden alle Eingabe-und Ausgabedateien für spätere inkrementelle Builds nachverfolgt. Weitere Informationen finden Sie unter [inkrementelle Builds und aktuelle Überprüfungen](#incremental-builds-and-up-to-date-checks).

Der Microsoft.Cpp.Common.Tasks.dll implementiert diese Aufgaben:

- `BSCMake`

- `CL`

- `ClangCompile` (clang-gcc-Switches)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (wie exec, aber mit der Eingabe-und Ausgabe Nachverfolgung)

- `SetEnv`

- `GetOutOfDateItems`

Wenn Sie über ein Tool verfügen, das dieselbe Aktion wie ein vorhandenes Tool ausführt und über ähnliche Befehls Zeilenschalter verfügt (wie clang-cl und CL), können Sie die gleiche Aufgabe für beide verwenden.

Wenn Sie eine neue Aufgabe für ein Buildtool erstellen müssen, können Sie eine der folgenden Optionen auswählen:

1. Wenn Sie diese Aufgabe nur selten verwenden oder einige Sekunden für den Build keine Rolle spielen, können Sie MSBuild-Inline Aufgaben verwenden:

   - XAML-Aufgabe (eine benutzerdefinierte Buildregel)

     Ein Beispiel für eine XAML-Aufgaben Deklaration finden Sie unter `$(VCTargetsPath)` \\ *buildcustomiationsmasm.xml* . Informationen \\ ** zu deren Verwendung finden Sie unter `$(VCTargetsPath)` \\ *buildcustomiationsmasm* \\ *. targets*.

   - [Codetask](../msbuild/msbuild-inline-tasks.md)

1. Wenn Sie eine bessere Aufgaben Leistung wünschen oder nur komplexere Funktionen benötigen, verwenden Sie den regulären Prozess zum Schreiben von MSBuild- [Aufgaben](../msbuild/task-writing.md) .

   Wenn nicht alle Eingaben und Ausgaben des Tools in der Befehlszeile des Tools aufgelistet sind, wie in den `CL` `MIDL` Fällen, und `RC` , und wenn Sie die automatische Nachverfolgung von Eingabe-und Ausgabedateien und TLog-Dateien erstellen möchten, leiten Sie Ihre Aufgabe von der- `Microsoft.Build.CPPTasks.TrackedVCToolTask` Klasse ab. Zurzeit gibt es in der Dokumentation für die [basistooltask](/dotnet/api/microsoft.build.utilities.tooltask) -Klasse keine Beispiele oder Dokumentation für die Details der- `TrackedVCToolTask` Klasse. Wenn dies ein besonderes Interesse ist, fügen Sie Ihrer Stimme eine Anforderung in der [Entwickler Community](https://aka.ms/feedback/suggest?space=62)hinzu.

## <a name="incremental-builds-and-up-to-date-checks"></a>Inkrementelle Builds und aktuelle Überprüfungen

Die standardmäßigen MSBuild-inkrementellen Buildziele verwenden die `Inputs` `Outputs` Attribute Wenn Sie diese angeben, ruft MSBuild das Ziel nur auf, wenn eine der Eingaben einen neueren Zeitstempel aufweist als alle Ausgaben. Da Quelldateien häufig andere Dateien einschließen oder importieren und die Buildtools abhängig von den Tool Optionen verschiedene Ausgaben erstellen, ist es schwierig, alle möglichen Eingaben und Ausgaben in MSBuild-Zielen anzugeben.

Um dieses Problem zu beheben, verwendet der C++-Build eine andere Technik zur Unterstützung inkrementeller Builds. Die meisten Ziele geben keine Eingaben und Ausgaben an und werden daher immer während des Builds ausgeführt. Die Tasks, die von aufgerufen werden, schreiben Informationen zu allen Eingaben und Ausgaben in *TLog* -Dateien, die über die Erweiterung ". TLog" verfügen. Die TLog-Dateien werden von späteren Builds verwendet, um zu überprüfen, was geändert wurde und neu erstellt werden muss und was auf dem neuesten Stand ist. Die TLog-Dateien sind auch die einzige Quelle für die standardmäßige Aktualisierungs Überprüfung in der IDE.

Um alle Eingaben und Ausgaben zu ermitteln, verwenden Native Tool Tasks tracker.exe und die von MSBuild bereitgestellte [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) -Klasse.

Microsoft.Build.CPPTasks.Common.dll die die `TrackedVCToolTask` öffentliche abstrakte Basisklasse definiert. Die meisten nativen Tool Aufgaben werden von dieser Klasse abgeleitet.

Ab Visual Studio 2017 Update 15,8 können Sie die `GetOutOfDateItems` in Microsoft.Cpp.Common.Tasks.dll implementierte Aufgabe verwenden, um TLog-Dateien für benutzerdefinierte Ziele mit bekannten Eingaben und Ausgaben zu entwickeln.
Alternativ können Sie Sie mit dem-Task erstellen `WriteLinesToFile` . Sehen Sie `_WriteMasmTlogs` sich das Ziel in `$(VCTargetsPath)` \\ *buildcustomizierungen* \\ *MASM. targets* als Beispiel an.

## <a name="tlog-files"></a>TLog-Dateien

Es gibt drei Typen von TLog-Dateien: *Lesen*, *Schreiben* und *Befehlszeile*. Lese-und Schreibvorgänge. TLog-Dateien werden von inkrementellen Builds und der aktuellen Überprüfung in der IDE verwendet. Befehlszeilen-TLog-Dateien werden nur in inkrementellen Builds verwendet.

MSBuild stellt diese Hilfsklassen zum Lesen und Schreiben von TLog-Dateien bereit:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

Die [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) -Klasse kann verwendet werden, um auf Lese-und Schreibvorgänge. TLog-Dateien zuzugreifen und Eingaben zu identifizieren, die neuer als Ausgaben sind, oder, wenn eine Ausgabe fehlt. Sie wird in der aktuellen Überprüfung verwendet.

Befehlszeilen-TLog-Dateien enthalten Informationen zu Befehlszeilen, die im Build verwendet werden. Sie werden nur für inkrementelle Builds und nicht für aktuelle Überprüfungen verwendet, sodass das interne Format von der MSBuild-Aufgabe bestimmt wird, die Sie erstellt.

### <a name="read-tlog-format"></a>Format "Read. TLog"

*Lesen Sie* die TLog-Dateien ( \* . Read. \* ). TLOG) enthält Informationen zu Quelldateien und deren Abhängigkeiten.

Ein **^** Caretzeichen () am Anfang einer Zeile gibt eine oder mehrere Quellen an. Quellen mit denselben Abhängigkeiten werden durch einen senkrechten Strich () getrennt **\|** .

Abhängigkeits Dateien werden nach den Quellen aufgelistet, jeweils in einer eigenen Zeile. Alle Dateinamen sind vollständige Pfade.

Nehmen Sie beispielsweise an, dass sich Ihre Projekt Quellen in *F: \\ Test \\ ConsoleApplication1 \\ ConsoleApplication1* befinden. Wenn die Quelldatei *Class1. cpp* diese umfasst,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

dann enthält die Datei *cl. Read. 1. TLog* die Quelldatei gefolgt von den beiden Abhängigkeiten:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Es ist nicht erforderlich, Dateinamen in Großbuchstaben zu schreiben, aber es ist für einige Tools praktisch.

### <a name="write-tlog-format"></a>Write. TLog-Format

*Write* . TLog ( \* . Write. \* . TLOG) Dateien verbinden Quellen und Ausgaben.

Ein **^** Caretzeichen () am Anfang einer Zeile gibt eine oder mehrere Quellen an. Mehrere Quellen werden durch einen senkrechten Strich ( **\|** ) getrennt.

Die aus den Quellen erstellten Ausgabedateien müssen nach den Quellen, jeweils in einer eigenen Zeile, aufgeführt werden. Alle Dateinamen müssen vollständige Pfade sein.

Für ein einfaches ConsoleApplication-Projekt, das über eine zusätzliche Quelldatei *Class1. cpp* verfügt, kann die Datei *Link. Write. 1. TLog* beispielsweise Folgendes enthalten:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Build zur Entwurfszeit

In der IDE verwenden vcxproj-Projekte eine Reihe von MSBuild-Zielen, um zusätzliche Informationen aus dem Projekt zu erhalten und Ausgabedateien erneut zu generieren. Einige dieser Ziele werden nur in Entwurfszeit Builds verwendet, aber viele von Ihnen werden sowohl in regulären Builds als auch in Entwurfszeit Builds verwendet.

Allgemeine Informationen zu Entwurfszeit Builds finden Sie in der CPS-Dokumentation zu [Entwurfszeit Builds](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Diese Dokumentation ist nur teilweise auf Visual C++ Projekte anwendbar.

Die `CompileDesignTime` `Compile` in der Dokumentation zur Entwurfszeit Erstellung erwähnten Ziele werden nie für vcxproj-Projekte ausgeführt. Visual C++. vcxproj-Projekte verwenden unterschiedliche Entwurfszeit Ziele, um IntelliSense-Informationen zu erhalten.

### <a name="design-time-targets-for-intellisense-information"></a>Entwurfszeit Ziele für IntelliSense-Informationen

Die Entwurfszeit Ziele, die in vcxproj-Projekten verwendet werden, sind in `$(VCTargetsPath)` \\ *Microsoft. cpp. designtime. targets* definiert.

Das `GetClCommandLines` Ziel sammelt Compileroptionen für IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – nur Entwurfszeit Ziele, die für die Entwurfs Initialisierung zur Entwurfszeit benötigt werden. Unter anderem deaktivieren diese Ziele einige der regulären Buildfunktionen, um die Leistung zu verbessern.

- `ComputeCompileInputsTargets` – eine Gruppe von Zielen, die Compileroptionen und-Elemente ändert. Diese Ziele werden sowohl in der Entwurfszeit als auch in regulären Builds ausgeführt.

Das Ziel Ruft die- `CLCommandLine` Aufgabe auf, um die Befehlszeile zu erstellen, die für IntelliSense verwendet werden soll. Auch hier gilt, dass es trotz seines Namens nicht nur CL-Optionen, sondern auch clang-und gcc-Optionen verarbeiten kann. Der Typ der Compilerschalter wird von der- `ClangMode` Eigenschaft gesteuert.

Derzeit verwendet die Befehlszeile, die von der Aufgabe erstellt wird, `CLCommandLine` immer cl-Switches (auch im clang-Modus), da Sie für die IntelliSense-Engine einfacher zu analysieren sind.

Wenn Sie ein Ziel hinzufügen, das vor der Kompilierung ausgeführt wird, unabhängig davon, ob es sich um eine reguläre oder Entwurfszeit handelt, sollten Sie sicherstellen, dass es keine Entwurfszeit-Builds Die einfachste Möglichkeit, Ihr Ziel zu testen, besteht darin, eine Developer-Eingabeaufforderung zu öffnen und den folgenden Befehl auszuführen:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Dieser Befehl erzeugt ein detailliertes Buildprotokoll, *MSBuild. log*, das eine Leistungsübersicht für die Ziele und Aufgaben am Ende aufweist.

Stellen Sie sicher, `Condition ="'$(DesignTimeBuild)' != 'true'"` dass Sie in allen Vorgängen verwenden, die nur für reguläre Builds sinnvoll sind, und nicht für die Entwurfszeit Builds.

### <a name="design-time-targets-that-generate-sources"></a>Entwurfszeit Ziele, die Quellen generieren

*Diese Funktion ist für Native Desktop-Projekte standardmäßig deaktiviert und wird derzeit nicht für zwischengespeicherte Projekte unterstützt*.

Wenn `GeneratorTarget` Metadaten für ein Projekt Element definiert sind, wird das Ziel automatisch ausgeführt, wenn das Projekt geladen wird und wenn die Quelldatei geändert wird.

::: moniker range="vs-2017"

Zum automatischen Generieren von cpp-oder h-Dateien aus XAML-Dateien definieren die `$(VSInstallDir)` \\ *MSBuild*-Dateien \\ *Microsoft* \\ *windowsxaml* \\ *v 15,0* \\ \* \\ *Microsoft. Windows. UI. XAML. cpp. targets* diese Entitäten:

::: moniker-end

::: moniker range=">=vs-2019"

Zum automatischen Generieren von cpp-oder h-Dateien aus XAML-Dateien definieren die `$(VSInstallDir)` \\ *MSBuild*-Dateien \\ *Microsoft* \\ *windowsxaml* \\ *v 16,0* \\ \* \\ *Microsoft. Windows. UI. XAML. cpp. targets* diese Entitäten:

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Um mit `Task.HostObject` den nicht gespeicherten Inhalt von Quelldateien zu erhalten, sollten die Ziele und die Aufgabe als [msbuildhostobjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017&preserve-view=true) für die angegebenen Projekte in einem pkgdef registriert werden:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++ Projekt Erweiterbarkeit in der Visual Studio-IDE

Das Visual C++-Projekt System basiert auf dem [vs-Projekt System](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)und verwendet seine Erweiterungs Punkte. Die Implementierung der Projekt Hierarchie ist jedoch spezifisch für Visual C++ und nicht auf CPS-Basis, sodass die Erweiterbarkeit der Hierarchie auf Projekt Elemente beschränkt ist.

### <a name="project-property-pages"></a>Seiten mit Projekteigenschaften

Allgemeine Entwurfs Informationen finden Sie unter [Framework-Ziel Versionen für VC + +-Projekte](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

Die Eigenschaften Seiten, die Sie im Dialogfeld " **Projekteigenschaften** " für ein C++-Projekt sehen, werden in einfachen Begriffen durch *Regel* Dateien definiert. Eine Regeldatei gibt eine Gruppe von Eigenschaften an, die auf einer Eigenschaften Seite angezeigt werden sollen, und wie und wo Sie in der Projektdatei gespeichert werden sollen. Regel Dateien sind XML-Dateien, die das XAML-Format verwenden. Die Typen, die für die Serialisierung verwendet werden, werden in [Microsoft. Build. Framework. XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes)beschrieben. Weitere Informationen zur Verwendung von Regel Dateien in-Projekten finden Sie unter [XML-Regel Dateien der Eigenschaften Seite](/cpp/build/reference/property-page-xml-files).

Die Regel Dateien müssen der Element Gruppe hinzugefügt werden `PropertyPageSchema` :

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` die durch den Regeltyp kontrollierte Sichtbarkeit von Metadaten schränkt die Regel ein und kann einen der folgenden Werte aufweisen:

`Project` | `File` | `PropertySheet`

CPS unterstützt andere Werte für den Kontexttyp, aber Sie werden nicht in Visual C++ Projekten verwendet.

Wenn die Regel in mehr als einem Kontext sichtbar sein soll, verwenden Sie Semikolons (**;**), um die Kontext Werte zu trennen, wie hier gezeigt:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Regel Format und Haupttypen

Das Regel Format ist unkompliziert. Daher werden in diesem Abschnitt nur die Attribute beschrieben, die beeinflussen, wie die Regel in der Benutzeroberfläche aussieht.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

Das- `PageTemplate` Attribut definiert, wie die Regel im Dialogfeld " **Eigenschaften Seiten** " angezeigt wird. Das Attribut kann einen der folgenden Werte aufweisen:

| attribute | BESCHREIBUNG |
|------------| - |
| `generic` | Alle Eigenschaften werden auf einer Seite unter Kategorieüberschriften angezeigt.<br/>Die Regel kann für `Project` -und- `PropertySheet` Kontexte sichtbar sein, jedoch nicht `File` .<br/><br/> Beispiel: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Kategorien werden als Unterseiten angezeigt.<br/>Die Regel kann in allen Kontexten sichtbar sein: `Project` , `PropertySheet` und `File` .<br/>Die Regel ist nur in den Projekteigenschaften sichtbar, wenn das Projekt über Elemente verfügt `ItemType` , die in definiert `Rule.DataSource` sind, es sei denn, der Regelname ist in der `ProjectTools` Element Gruppe enthalten.<br/><br/>Beispiel: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | Die Seite wird als Teil der debuggingseite angezeigt.<br/>Kategorien werden zurzeit ignoriert.<br/>Der Regelname muss mit dem-Attribut des debugstartprogrammmef-Objekts identisch sein `ExportDebugger` .<br/><br/>Beispiel: `$(VCTargetsPath)` \\ *1033* \\ *Debugger \_ local \_windows.xml* |
| *Zollunion* | Benutzerdefinierte Vorlage. Der Name der Vorlage sollte mit dem- `ExportPropertyPageUIFactoryProvider` Attribut des `PropertyPageUIFactoryProvider` MEF-Objekts identisch sein. Siehe **Microsoft. VisualStudio. projectsystem. Designers. Properties. ipropertypageuifactor Provider**.<br/><br/> Beispiel: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Wenn die Regel eine der Eigenschaften Raster basierten Vorlagen verwendet, kann Sie diese Erweiterbarkeits Punkte für die zugehörigen Eigenschaften verwenden:

- [Eigenschafts Wert-Editors](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Dynamischer enumerationsvalues-Anbieter](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Erweitern einer Regel

Wenn Sie eine vorhandene Regel verwenden möchten, aber nur einige wenige Eigenschaften hinzufügen oder entfernen (d. h. ausblenden) möchten, können Sie eine [Erweiterungs Regel](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md)erstellen.

#### <a name="override-a-rule"></a>Regel außer Kraft setzen

Vielleicht möchten Sie, dass Ihr Toolset die meisten Projekt Standardregeln verwendet, aber nur ein oder einige davon ersetzen kann. Nehmen Sie beispielsweise an, dass Sie nur die C/C++-Regel ändern möchten, um unterschiedliche compilerswitches anzuzeigen. Sie können eine neue Regel mit demselben Namen und anzeigen Amen wie die vorhandene Regel bereitstellen und Sie `PropertyPageSchema` nach dem Importieren von cpp-Standardzielen in die Element Gruppe einschließen. Im Projekt wird nur eine Regel mit einem bestimmten Namen verwendet, und die letzte Regel, die in der `PropertyPageSchema` Element Gruppe enthalten ist, gewinnt.

#### <a name="project-items"></a>Projektelemente

Die *ProjectItemsSchema.xml* -Datei definiert die `ContentType` -und- `ItemType` Werte für Elemente, die als Projekt Elemente behandelt werden, und definiert- `FileExtension` Elemente, um zu bestimmen, welcher Element Gruppe eine neue Datei hinzugefügt wird.

Die standardmäßige projectitemsschema-Datei befindet sich in `$(VCTargetsPath)` \\ *1033* \\ *ProjectItemsSchema.xml*. Um es zu erweitern, müssen Sie eine Schema Datei mit einem neuen Namen erstellen, z. b. *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Fügen Sie dann in der targets-Datei Folgendes hinzu:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Beispiel: `$(VCTargetsPath)` \\ *buildcustomizierungen* \\ *masm.xml*

### <a name="debuggers"></a>Debugger

Der Debugdienst in Visual Studio unterstützt die Erweiterbarkeit für die Debug-Engine. Weitere Informationen finden Sie in den folgenden Beispielen:

- [Miengine, Open Source-Projekt, das lldb-Debugging unterstützt](https://github.com/Microsoft/MIEngine)

- [Visual Studio-Debug-Engine-Beispiel](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Zum Angeben der Debug-engines und anderer Eigenschaften für die Debugsitzung müssen Sie eine [debugstartprogramm](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) -MEF-Komponente implementieren und eine Regel hinzufügen `debugger` . Ein Beispiel finden Sie in der `$(VCTargetsPath)` \\ lokalenwindows.xml-Datei des 1033- \\ Debuggers \_ \_ .

### <a name="deploy"></a>Bereitstellen

vcxproj-Projekte verwenden die Erweiterbarkeit von Visual Studio-Projekt Systemen für Bereitstellungs [Anbieter](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Aktuelle Überprüfung erstellen

Standardmäßig erfordert die Überprüfung des aktuellen Builds, dass die Dateien "Read. TLog" und "Write. TLog" im `$(TlogLocation)` Ordner während des Builds für alle buildeingaben und-Ausgaben erstellt werden.

So verwenden Sie eine benutzerdefinierte Aktualisierungs Überprüfung:

1. Deaktivieren Sie die standardmäßige Aktualisierungs Überprüfung, indem Sie die `NoVCDefaultBuildUpToDateCheckProvider` Funktion in der Datei *Toolset. targets* hinzufügen:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implementieren Sie einen eigenen [ibuildupumdatecheckprovider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Projekt Upgrade

### <a name="default-vcxproj-project-upgrader"></a>Default. vcxproj-Projekt Upgrader

Das default. vcxproj-Projekt Upgrader ändert `PlatformToolset` die `ApplicationTypeRevision` Versionen,, MSBuild-Toolset und .NET Framework. Die letzten beiden werden stets in die Standardeinstellungen der Visual Studio-Version geändert, Sie `PlatformToolset` `ApplicationTypeRevision` können jedoch über spezielle MSBuild-Eigenschaften gesteuert werden.

Der Upgrader verwendet diese Kriterien, um zu entscheiden, ob ein Projekt aktualisiert werden kann oder nicht:

1. Für Projekte, die `ApplicationType` und definieren `ApplicationTypeRevision` , gibt es einen Ordner mit einer höheren Revisionsnummer als der aktuelle.

1. Die `_UpgradePlatformToolsetFor_<safe_toolset_name>` -Eigenschaft ist für das aktuelle Toolset definiert, und der zugehörige Wert ist nicht gleich dem aktuellen Toolset.

   In diesen Eigenschaftsnamen *\<safe_toolset_name>* stellt den toolsetnamen dar, wobei alle nicht alphanumerischen Zeichen durch einen Unterstrich () ersetzt werden **\_** .

Wenn für ein Projekt ein Upgrade durchgeführt werden kann, ist es Teil der *Lösungs Neuausrichtung*. Weitere Informationen finden Sie unter [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Wenn Sie Projektnamen in **Projektmappen-Explorer** schmücken möchten, wenn Projekte ein bestimmtes Toolset verwenden, definieren Sie eine `_PlatformToolsetShortNameFor_<safe_toolset_name>` Eigenschaft.

Beispiele für `_UpgradePlatformToolsetFor_<safe_toolset_name>` -und- `_PlatformToolsetShortNameFor_<safe_toolset_name>` Eigenschafts Definitionen finden Sie in der Datei " *Microsoft. cpp. default.* -Eigenschaften". Beispiele für die Verwendung finden Sie in der `$(VCTargetPath)` \\ Datei *Microsoft. cpp. Platform. targets* .

### <a name="custom-project-upgrader"></a>Benutzerdefiniertes Projekt Upgrade

Wenn Sie ein benutzerdefiniertes Projekt Upgrader-Objekt verwenden möchten, implementieren Sie eine MEF-Komponente, wie hier gezeigt:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Der Code kann das default. vcxproj Upgrader-Objekt importieren und aufrufen:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` wird in *Microsoft.VisualStudio.ProjectSystem.VS.dll* definiert und ähnelt `IVsRetargetProjectAsync` .

Definieren Sie die- `VCProjectUpgraderObjectName` Eigenschaft, um das Projekt System anzuweisen, das benutzerdefinierte Upgrader-Objekt zu verwenden:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Projekt Upgrade deaktivieren

Verwenden Sie zum Deaktivieren von Projekt Upgrades einen `NoUpgrade` Wert:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Projekt Cache und Erweiterbarkeit

Um die Leistung bei der Arbeit mit großen C++-Lösungen in Visual Studio 2017 zu verbessern, wurde der [Projekt Cache](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) eingeführt. Sie wird als SQLite-Datenbank implementiert, die mit Projektdaten aufgefüllt ist, und dann zum Laden von Projekten verwendet, ohne MSBuild-oder CPS-Projekte in den Arbeitsspeicher zu laden.

Da keine CPS-Objekte für vcxproj-Projekte vorhanden sind, die aus dem Cache geladen wurden, werden die MEF-Komponenten der Erweiterung, die importiert `UnconfiguredProject` oder `ConfiguredProject` nicht erstellt werden können, nicht erstellt. Um die Erweiterbarkeit zu unterstützen, wird der Projekt Cache nicht verwendet, wenn Visual Studio erkennt, ob ein Projekt MEF-Erweiterungen verwendet (oder wahrscheinlich verwendet).

Diese Projekttypen sind immer vollständig geladen und verfügen über CPS-Objekte im Arbeitsspeicher, sodass alle MEF-Erweiterungen für Sie erstellt werden:

- Start Projekte

- Projekte mit einem benutzerdefinierten Projekt Upgrader, d. h., Sie definieren eine `VCProjectUpgraderObjectName` Eigenschaft.

- Projekte, die nicht auf Desktop Fenster abzielen, d. h., Sie definieren eine `ApplicationType` Eigenschaft.

- Projekte mit freigegebenen Elementen (. vcxitems) und alle Projekte, die durch den Import von vcxitems-Projekten darauf verweisen.

Wenn keine dieser Bedingungen erkannt wird, wird ein Projekt Cache erstellt. Der Cache enthält alle Daten aus dem MSBuild-Projekt, die zum Beantworten von `get` Abfragen für `VCProjectEngine` Schnittstellen erforderlich sind. Dies bedeutet, dass alle Änderungen auf der von einer Erweiterung durchgeführten MSBuild-Eigenschaften-und Ziel Dateiebene nur in Projekten funktionieren, die aus dem Cache geladen wurden.

## <a name="shipping-your-extension"></a>Versenden der Erweiterung

Informationen zum Erstellen von VSIX-Dateien finden Sie unter [Versand von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md). Informationen zum Hinzufügen von Dateien zu speziellen Installations Standorten, z. b. zum Hinzufügen von Dateien unter `$(VCTargetsPath)` , finden Sie unter [Installieren außerhalb des Ordners "Erweiterungen](../extensibility/set-install-root.md)".

## <a name="additional-resources"></a>Zusätzliche Ressourcen

Das Microsoft-Buildsystem ([MSBuild](../msbuild/msbuild.md)) stellt die Build-Engine und das erweiterbare XML-basierte Format für Projektdateien bereit. Sie sollten mit den grundlegenden [MSBuild-Konzepten](../msbuild/msbuild-concepts.md) und mit der Funktionsweise [von MSBuild für Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) vertraut sein, um das Visual C++ Projekt System zu erweitern.

Der Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) stellt die Erweiterungs-APIs bereit, die von CPS und dem Visual C++-Projekt System verwendet werden. Einen Überblick über die Verwendung von MEF durch CPS finden Sie unter [CPS und MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) in der [Übersicht über das vsprojectsystem in MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Sie können das vorhandene Buildsystem so anpassen, dass Buildschritte oder neue Dateitypen hinzugefügt werden. Weitere Informationen finden Sie unter [Übersicht über MSBuild (Visual C++)](/cpp/build/reference/msbuild-visual-cpp-overview) und [unter Arbeiten mit Projekteigenschaften](/cpp/build/working-with-project-properties).
