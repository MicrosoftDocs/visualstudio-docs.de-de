---
title: Anpassen Ihres Builds | Microsoft-Dokumentation
description: Erfahren Sie mehr über verschiedene Erweiterungsmöglichkeiten, mit denen Sie MSBuild-Projekte anpassen können, die den Standardbuildprozess verwenden.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f2d533e4b7f275a70d20be684fbd781d62a3a109
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877357"
---
# <a name="customize-your-build"></a>Anpassen Ihres Builds

MSBuild-Projekte, die den Standardbuildprozess verwenden und *Microsoft.Common.props* und *Microsoft.Common.targets* importieren, beinhalten einige Erweiterungsmöglichkeiten, die zum Anpassen Ihres Buildprozesses verwendet werden können.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Hinzufügen von Argumenten zu MSBuild-Aufrufen Ihres Projekts über die Befehlszeile

Es wird eine *Directory.Build.rsp*-Datei innerhalb oder oberhalb des Quellverzeichnisses auf die Builds des Projekts über die Befehlszeile angewendet. Weitere Einzelheiten finden Sie unter [MSBuild-Antwortdateien](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>„Directory.Build.props“ und „Directory.Build.targets“

Wenn Sie vor Version 15 von MSBuild eine neue benutzerdefinierte Eigenschaft für Projekte in Ihrer Projektmappe bereitstellen wollten, mussten Sie zu jeder Projektdatei in der Projektmappe manuell einen Verweis auf diese Eigenschaft hinzufügen. Alternativ dazu konnten Sie unter anderem die Eigenschaft in einer *PROPS*-Datei definieren und diese dann explizit in jedes Projekt der Projektmappe importieren.

Jetzt hingegen können Sie in einem Schritt jedem Projekt eine neue Eigenschaft hinzufügen, indem Sie sie in einer einzigen Datei mit dem Namen *Directory.Build.props* im Stammverzeichnis der Quelle definieren. Beim Ausführen von MSBuild durchsucht *Microsoft.Common.props* die Verzeichnisstruktur nach der Datei *Directory.Build.props* (und *Microsoft.Common.targets* sucht nach *Directory.Build.targets*). Wenn eine Datei gefunden wird, wird die Eigenschaft importiert. Bei *Directory.Build.props* handelt es sich um eine benutzerdefinierte Datei, die Anpassungen für Projekte in einem Verzeichnis bereitstellt.

> [!NOTE]
> Bei Linux-basierten Dateisystemen wird zwischen Groß- und Kleinschreibung unterschieden. Stellen Sie sicher, dass die Schreibweise des Dateinamens „Directory.Build.props“ genau übereinstimmt, sonst wird die Datei während des Buildvorgangs nicht erkannt.
>
> Weitere Informationen finden Sie in [diesem GitHub-Problem](https://github.com/dotnet/core/issues/1991#issue-368441031).

### <a name="directorybuildprops-example"></a>Beispiel für „Directory.Build.props“

Wenn Sie beispielsweise für alle Ihre Projekte den Zugriff auf die neue Roslyn-Funktion **/deterministic** (die im `CoreCompile`-Ziel von Roslyn durch die Eigenschaft `$(Deterministic)` verfügbar gemacht wird) aktivieren möchten, können Sie wie folgt vorgehen.

1. Erstellen Sie im Stammverzeichnis Ihres Repositorys eine neue Datei mit dem Namen *Directory.Build.props*.
2. Fügen Sie der Datei das folgende XML hinzu.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Führen Sie MSBuild aus. Die vorhandenen Importe des Projekts von *Microsoft.Common.props* und *Microsoft.Common.targets* finden die Datei und importieren sie.

### <a name="search-scope"></a>Suchbereich

Bei der Suche nach einer Datei *Directory.Build.props* durchläuft MSBuild die Verzeichnisstruktur vom Speicherort des Projekts (`$(MSBuildProjectFullPath)`) aufwärts und stoppt, wenn eine Datei *Directory.Build.props* gefunden wird. Wenn `$(MSBuildProjectFullPath)` zum Beispiel *C:\users\username\code\test\case1* lautet, beginnt MSBuild an dieser Stelle und durchsucht die Verzeichnisstruktur aufwärts, bis wie in der folgenden Verzeichnisstruktur eine Datei *Directory.Build.props* gefunden wird.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Der Speicherort der Projektmappendatei ist für *Directory.Build.props* ohne Bedeutung.

### <a name="import-order"></a>Importreihenfolge

*Directory.Build.props* wird zu einem frühen Zeitpunkt in *Microsoft.Common.props* importiert, und später definierte Eigenschaften sind dafür nicht verfügbar. Vermeiden Sie deshalb das Verweisen auf Eigenschaften, die noch nicht definiert sind (und als leer ausgewertet werden).

Eigenschaften, die in *Directory.Build.props* festgelegt werden, können an anderer Stelle in der Projektdatei oder in importierten Dateien überschrieben werden, daher sollten Sie sich die Einstellungen in *Directory.Build.props* als Angabe der Standardeinstellungen für Ihre Projekte vorstellen.

*Directory.Build.targets* wird aus *Microsoft.Common.targets* importiert, nachdem *TARGETS*-Dateien aus NuGet-Paketen importiert wurden. Die Datei kann also Eigenschaften und Ziele, die in den meisten Buildlogiken definiert sind, außer Kraft setzen oder Eigenschaften für alle Ihre Projekte festlegen, und zwar unabhängig davon, was die einzelnen Projekte festlegen.

Wenn Sie eine Eigenschaft festlegen oder ein Ziel für ein einzelnes Projekt definieren müssen, das alle vorherigen Einstellungen überschreibt, platzieren Sie diese Logik nach dem letzten Import in der Projektdatei. In einem SDK-Projekt müssen Sie dazu müssen zuerst das Attribut im SDK-Stil durch die entsprechenden Importe ersetzen. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von MSBuild-Projekt-SDKs](how-to-use-project-sdk.md).

> [!NOTE]
> Die MSBuild-Engine liest alle importierten Dateien während der Auswertung ein, bevor mit der Buildausführung für ein Projekt (einschließlich aller `PreBuildEvent`-Vorgänge) begonnen wird, sodass nicht erwartet wird, dass diese Dateien durch das `PreBuildEvent` oder einen anderen Teil des Buildprozesses geändert werden. Änderungen werden erst nach dem nächsten Aufruf von *MSBuild.exe* oder dem nächsten Visual Studio-Buildvorgang wirksam.

### <a name="use-case-multi-level-merging"></a>Anwendungsfall: Zusammenführen mehrerer Ebenen

Für diesen Anwendungsfall wird beispielhaft davon ausgegangen, dass Sie die folgende Standard-Projektmappenstruktur verwenden:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Es kann sinnvoll sein, gemeinsame Eigenschaften für alle Projekte *(1)* , für *src*-Projekte *(2-src)* und für *test*-Projekte *(2-test)* zu verwenden.

Damit MSBuild die „inneren“ Dateien (*2-src* und *2-test*) mit der „äußeren“ Datei (*1*) korrekt zusammenführen kann, müssen Sie berücksichtigen, dass MSBuild nach der ersten gefundenen Datei *Directory.Build.props* den Suchvorgang abbricht. Zum Fortsetzen des Suchvorgangs und des Zusammenführens in der äußeren Datei ist es erforderlich, diesen Code in beide inneren Dateien einzufügen:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Der allgemeine Ansatz von MSBuild lässt sich folgendermaßen zusammenfassen:

- MSBuild sucht die erste Datei *Directory.Build.props*, die in der Projektmappenstruktur oberhalb der aktuellen Datei gefunden wird, führt diese mit den Standardeinstellungen zusammen und beendet anschließend den Suchvorgang.
- Wenn mehrere Ebenen gefunden und zusammengeführt werden sollen, importieren Sie wie oben gezeigt mit [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) die äußere Datei aus der inneren.
- Wenn die äußere Datei nicht ebenfalls Dateien importiert, die sich in der Projektstruktur oberhalb der äußeren Datei befinden, wird der Suchvorgang an dieser Stelle beendet.
- Verwenden Sie zum Konfigurieren des Such- und Zusammenführungsprozesses `$(DirectoryBuildPropsPath)` und `$(ImportDirectoryBuildProps)`.

Oder in einem Satz ausgedrückt: MSBuild beendet den Suchvorgang, sobald eine *Directory.Build.props*-Datei gefunden wurde, durch die keine weiteren Dateien importiert werden.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Wählen zwischen dem Hinzufügen von Eigenschaften zu einer PROPS- oder TARGETS-Datei

MSBuild ist von der Importreihenfolge abhängig, sodass die letzte Definition einer Eigenschaft (oder von `UsingTask` oder eines Ziels) die verwendete Definition ist.

Wenn Sie explizite Importe verwenden, können Sie Daten jederzeit aus einer *PROPS*- oder *TARGETS*-Datei importieren. Hier ist die weit verbreitete Konvention:

- *PROPS*-Dateien werden zu einem frühen Zeitpunkt in der Importreihenfolge importiert.

- *TARGETS*-Dateien werden später in der Buildreihenfolge importiert.

Diese Konvention wird durch `<Project Sdk="SdkName">`-Importe erzwungen (d.h. der Import von *Sdk.props* erfolgt zuerst vor dem gesamten Inhalt der Datei. *Sdk.targets* kommt zuletzt nach dem gesamten Inhalt der Datei).

Befolgen Sie bei der Entscheidung, wo Sie die Eigenschaften platzieren möchten, die folgenden allgemeinen Leitlinien:

- Bei vielen Eigenschaften spielt es keine Rolle, wo sie definiert werden, da sie nicht überschrieben und nur zur Ausführungszeit gelesen werden.

- Für Verhalten, die in einem einzelnen Projekt angepasst werden können, legen Sie in *PROPS*-Dateien Standardwerte fest.

- Vermeiden Sie es, abhängige Eigenschaften in *PROPS*-Dateien festzulegen, indem Sie den Wert einer möglicherweise angepassten Eigenschaft lesen, da die Anpassung erst erfolgt, wenn MSBuild das Projekt des Benutzers liest.

- Legen Sie abhängige Eigenschaften in *TARGETS*-Dateien fest, da bei ihnen Anpassungen aus einzelnen Projekten übernommen werden.

- Wenn Sie Eigenschaften überschreiben müssen, tun Sie dies in einer *TARGETS*-Datei, nachdem alle Anpassungen am Benutzerprojekt wirksam werden konnten. Seien Sie vorsichtig bei der Verwendung abgeleiteter Eigenschaften, da diese möglicherweise ebenfalls überschrieben werden müssen.

- Fügen Sie Elemente in *PROPS*-Dateien (abhängig von einer Eigenschaft) ein. Alle Eigenschaften werden vor jedem Element berücksichtigt. Deshalb werden Anpassungen der Eigenschaften des Benutzerprojekts übernommen. Dies gibt dem Projekt des Benutzers die Möglichkeit, die Vorgänge `Remove` oder `Update` auf jedes durch den Import eingeführte Element anzuwenden.

- Definieren Sie Ziele in *TARGETS*-Dateien. Wenn die *TARGETS*-Datei jedoch durch ein SDK importiert wird, denken Sie daran, dass dieses Szenario das Überschreiben des Ziels erschwert, da das Projekt des Benutzers standardmäßig keine Möglichkeit hat, es zu überschreiben.

- Bevorzugen Sie nach Möglichkeit die Anpassung von Eigenschaften zur Evaluierungszeit gegenüber der Änderung von Eigenschaften innerhalb eines Ziels. Diese Leitlinie erleichtert das Laden eines Projekts und das Verstehen seiner Aktivitäten.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Standardmäßig importiert *Microsoft.Common.props*`$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props`, und *Microsoft.Common.targets* importiert `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. Der Standardwert von `MSBuildProjectExtensionsPath` ist `$(BaseIntermediateOutputPath)`, `obj/`. NuGet verwendet diesen Mechanismus, um einen Verweis auf die mit Paketen bereitgestellte Buildlogik herzustellen. D.h., NuGet erstellt während der Wiederherstellung `{project}.nuget.g.props`-Dateien, die auf die Paketinhalte verweisen.

Sie können diesen Erweiterbarkeitsmechanismus deaktivieren, indem Sie die Eigenschaft `ImportProjectExtensionProps` in einer *Directory.Build.props*-Datei oder vor dem Import von *Microsoft.Common.props* auf `false` festlegen.

> [!NOTE]
> Wenn Sie MSBuildProjectExtensionsPath-Importe deaktivieren, wird die Buildlogik, die in NuGet-Paketen enthalten ist, nicht auf Ihr Projekt angewendet. Für einige NuGet-Pakete ist es erforderlich, dass die Buildlogik ausgeführt wird. Sie werden daher unnötig gerendert, wenn diese Option deaktiviert ist.

## <a name="user-file"></a>USER-Datei

*Microsoft.Common.CurrentVersion.targets* importiert `$(MSBuildProjectFullPath).user`, sofern vorhanden, damit Sie neben Ihrem Projekt eine Datei mit dieser zusätzlichen Erweiterung erstellen können. Für längerfristig geplante Änderungen, die Sie in die Quellcodeverwaltung integrieren möchten, ändern Sie besser das Projekt direkt, damit spätere Verwalter diesen Erweiterungsmechanismus nicht unbedingt kennen müssen.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath und MSBuildUserExtensionsPath

> [!WARNING]
> Wenn Sie diesen Erweiterungsmechanismus verwenden, ist es schwieriger, wiederholbare Builds für mehrere Computer zu gewährleisten. Verwenden Sie stattdessen am besten eine Konfiguration, die in Ihr Quellcodeverwaltungssystem integriert werden und für alle Entwickler Ihrer Codebasis freigegeben werden kann.

Standardmäßig importieren viele wichtige Buildlogikdateien

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

vor ihrem Inhalt und

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

danach. Dank dieser Konvention können installierte SDKs die Buildlogik häufig verwendeter Projekttypen erweitern.

In `$(MSBuildUserExtensionsPath)` wird nach der gleichen Verzeichnisstruktur (je nach Benutzerordner *%LOCALAPPDATA%\Microsoft\MSBuild*) gesucht. Dateien, die in diesem Ordner platziert werden, werden für alle Builds des jeweiligen Projekttyps importiert, die mit den Anmeldeinformationen des Benutzers ausgeführt werden. Sie können die Benutzererweiterungen deaktivieren, indem Sie die Eigenschaften festlegen, die nach der Importdatei im Muster `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` benannt werden. Wenn Sie beispielsweise `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` auf `false` festlegen, wird `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` nicht importiert.

## <a name="customize-the-solution-build"></a>Anpassen des Projektmappenbuilds

> [!IMPORTANT]
> Wenn auf diese Weise der Projektmappenbuild angepasst wird, werden die Änderungen nur auf Builds mit *MSBuild.exe* über die Befehlszeile angewendet. Sie werden **nicht** auf Builds innerhalb von Visual Studio angewendet. Aus diesem Grund ist es nicht empfehlenswert, Anpassungen auf Projektmappenebene abzulegen. Eine bessere Alternative für die benutzerdefinierte Anpassung aller Projekte in einer Projektmappe ist die Verwendung der Dateien *Directory.build.props* und *Directory.build.targets* im Projektmappenordner, wie an anderer Stelle in diesem Artikel erläutert.

Wenn MSBuild eine Projektmappendatei erstellt, wird diese zuerst intern in eine Projektdatei übersetzt, die dann erstellt wird. Die generierte Projektdatei importiert `before.{solutionname}.sln.targets`, bevor sie Ziele definiert und `after.{solutionname}.sln.targets` nachdem sie Ziele importiert hat. Dazu gehören auch die Ziele, die in den Verzeichnissen `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` und `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` installiert sind.

Sie können beispielsweise ein neues Ziel definieren, um eine benutzerdefinierte Protokollmeldung zu schreiben, nachdem *MyCustomizedSolution.sln* erstellt wurde, indem Sie eine Datei in demselben Verzeichnis mit dem Namen *after.MyCustomizedSolution.sln.targets* erstellen, die Folgendes enthält:

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

Der Projektmappenbuild ist von den Projektbuilds getrennt, sodass sich die Einstellungen hier nicht auf Projektbuilds auswirken.

## <a name="customize-all-net-builds"></a>Anpassen aller .NET-Builds

Wenn Sie einen Buildserver verwalten, müssen Sie möglicherweise die MSBuild-Einstellungen global für alle Builds auf dem Server konfigurieren.  Im Prinzip könnten Sie die globalen Dateien *Microsoft.Common.Targets* oder *Microsoft.Common.Props* ändern, aber es gibt eine bessere Möglichkeit. Sie können alle Builds eines bestimmten Projekttyps (z. B. alle C#-Projekte) beeinflussen, indem Sie bestimmte MSBuild-Eigenschaften verwenden und bestimmte benutzerdefinierte `.targets`- und `.props`-Dateien hinzufügen.

Um alle C#- oder Visual Basic-Builds, die von einer Installation von MSBuild oder Visual Studio gesteuert werden, zu beeinflussen, erstellen Sie eine Datei *Custom.Before.Microsoft.Common.Targets* oder *Custom.After.Microsoft.Common.Targets* mit Zielen, die vor oder nach *Microsoft.Common.targets* ausgeführt werden, oder eine Datei *Custom.Before.Microsoft.Common.Props* oder *Custom.After.Microsoft.Common.Props* mit Eigenschaften, die vor oder nach *Microsoft.Common.props* verarbeitet werden.

Sie können die Speicherorte dieser Dateien mithilfe der folgenden MSBuild-Eigenschaften angeben:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

Die *Common*-Versionen dieser Eigenschaften wirken sich sowohl auf C#- als auch auf Visual Basic-Projekte aus. Sie können diese Eigenschaften über die MSBuild-Befehlszeile festlegen.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

Der beste Ansatz richtet sich nach Ihrem Szenario. Mithilfe von Visual Studio-Erweiterbarkeit können Sie das Buildsystem anpassen und einen Mechanismus zum Installieren und Verwalten der Anpassungen bereitstellen.

Wenn Sie über einen dedizierten Buildserver verfügen und sicherstellen möchten, dass bestimmte Ziele immer für alle Builds des entsprechenden Projekttyps ausgeführt werden, die auf diesem Server ausgeführt werden, dann ist die Verwendung einer globalen benutzerdefinierten `.targets`- oder `.props`-Datei sinnvoll.  Wenn Sie möchten, dass die benutzerdefinierten Ziele nur unter bestimmten Bedingungen ausgeführt werden, verwenden Sie einen anderen Dateispeicherort, und legen Sie den Pfad zu dieser Datei fest, indem Sie die entsprechende MSBuild-Eigenschaft in der MSBuild-Befehlszeile nur bei Bedarf festlegen.

> [!WARNING]
> Visual Studio verwendet die benutzerdefinierten `.targets`- oder `.props`-Dateien, wenn diese bei Erstellung eines Projekts des entsprechenden Typs im MSBuild-Ordner gefunden werden. Dies kann unbeabsichtigte Folgen haben und bei falscher Verwendung dazu führen, dass Visual Studio auf Ihrem Computer keine Builds mehr erstellen kann.

## <a name="customize-c-builds"></a>Anpassen von C++-Builds

Für C++-Projekte können die zuvor erwähnten benutzerdefinierten *TARGETS*- und *PROPS*-Dateien nicht auf dieselbe Weise verwendet werden, um Standardeinstellungen zu überschreiben. *Directory.Build.props* wird von *Microsoft.Common.props* importiert. Diese Datei wird in `Microsoft.Cpp.Default.props` importiert, während die meisten Standardeinstellungen in *Microsoft.Cpp.props* definiert werden und für eine Reihe von Eigenschaften eine „wenn noch nicht definiert“-Bedingung nicht verwendet werden kann, da die Eigenschaft bereits definiert ist, aber der Standardwert für bestimmte Projekteigenschaften, die in `PropertyGroup` mit `Label="Configuration"` definiert sind, anders sein muss (siehe [VCXPROJ- und PROPS-Dateistruktur](/cpp/build/reference/vcxproj-file-structure)).

Sie können jedoch die folgenden Eigenschaften verwenden, um mindestens eine *PROPS*-Datei anzugeben, die vor/nach *Microsoft.Cpp\** -Dateien automatisch importiert werden soll:

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

Wenn Sie die Standardwerte der Eigenschaften für alle C++-Builds anpassen möchten, erstellen Sie eine weitere *PROPS*-Datei (z. B. *MyProps.props*), und definieren Sie die `ForceImportAfterCppProps`-Eigenschaft in `Directory.Build.props`, die darauf verweist:

<PropertyGroup> <ForceImportAfterCppProps>$(MsbuildThisFileDirectory)\MyProps.props<ForceImportAfterCppProps>
</PropertyGroup>

*Microsoft.Cpp.props* wird automatisch ganz am Ende von *Microsoft.Cpp.props* importiert.

## <a name="customize-all-c-builds"></a>Anpassen aller C++-Builds

Das Anpassen der Visual Studio-Installation wird nicht empfohlen, da es nicht einfach ist, solche Anpassungen nachzuverfolgen. Wenn Sie Visual Studio jedoch erweitern, um C++-Builds für eine bestimmte Plattform anzupassen, können Sie `.targets`-Dateien für jede Plattform erstellen und sie als Teil einer Visual Studio-Erweiterung in den entsprechenden Importordnern für diese Plattformen speichern.

Die `.targets`-Datei für die Win32-Plattform, *Microsoft.Cpp.Win32.targets*, enthält das folgende `Import`-Element:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Am Ende derselben Datei befindet sich ein ähnliches Element:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Ähnliche Importelemente liegen für andere Zielplattformen in *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v{version}\Platforms\* vor.

Sobald Sie die `.targets`-Datei im geeigneten Ordner `ImportAfter` der Plattform platziert haben, importiert MSBuild Ihre Datei in jeden C++-Build für diese Plattform. Falls erforderlich, können Sie mehrere `.targets`-Dateien platzieren. 

Mithilfe von Visual Studio-Erweiterbarkeit sind weitere Anpassungen möglich, z. B. das Definieren einer neuen Plattform. Weitere Informationen finden Sie unter [C++-Projekterweiterbarkeit](../extensibility/visual-cpp-project-extensibility.md).

### <a name="specify-a-custom-import-on-the-command-line"></a>Angeben eines benutzerdefinierten Imports über die Befehlszeile

Für benutzerdefinierte `.targets`-Dateien, die Sie für einen bestimmten Build eines C++-Projekts einschließen möchten, legen Sie eine oder beide der Eigenschaften `ForceImportBeforeCppTargets` und `ForceImportAfterCppTargets` über die Befehlszeile fest.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Für eine globale Einstellung (beispielsweise für alle C++-Builds einer Plattform auf einem Buildserver) gibt es zwei Methoden. Zunächst können Sie diese Eigenschaften über eine Systemumgebungsvariable festlegen, die immer festgelegt ist. Dies funktioniert, weil MSBuild immer die Umgebungseinstellungen liest und Eigenschaften für alle Umgebungsvariablen erstellt (oder überschreibt).

## <a name="see-also"></a>Siehe auch

- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)

- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
