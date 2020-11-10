---
title: Reservierte und bekannte Eigenschaften für MSBuild | Microsoft-Dokumentation
description: Erfahren Sie mehr über reservierte und bekannte MSBuild-Eigenschaften – vordefinierte Eigenschaften zum Speichern von Informationen über die Projektdatei und die MSBuild-Binärdateien.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0480b427b92ca43603deedf84e5fd7cb39e6e065
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049158"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Reservierte und bekannte Eigenschaften für MSBuild

MSBuild stellt eine Reihe vordefinierter Eigenschaften zum Speichern von Informationen über die Projektdatei und die MSBuild-Binärdateien bereit. Diese Eigenschaften werden auf dieselbe Weise ausgewertet wie andere MSBuild-Eigenschaften. Zum Verwenden der `MSBuildProjectFile`-Eigenschaft geben Sie beispielsweise `$(MSBuildProjectFile)` ein.

 MSBuild verwendet die Werte in der folgenden Tabelle, um die reservierten und bekannten Eigenschaften vorzudefinieren. Reservierte Eigenschaften können nicht überschrieben werden, aber bekannte Eigenschaften können überschrieben werden, indem identisch benannte Umgebungseigenschaften, globale Eigenschaften oder Eigenschaften verwendet werden, die in der Projektdatei deklariert sind.

## <a name="reserved-and-well-known-properties"></a>Reservierte und bekannte Eigenschaften

In der folgenden Tabelle sind die vordefinierten MSBuild-Eigenschaften enthalten. Die Beispielspalte in der Tabelle bezieht sich auf die folgende Beispielprojektdatei, von der angenommen wird, dass sie sich unter `C:\Source\Repos\ConsoleApp1\ConsoleApp1` befindet. Sie enthält die Werte dieser Eigenschaften beim Zugriff in der Projektdatei, wenn MSBuild ohne spezielle Befehlszeilenoptionen aufgerufen wird. Dabei ist ein Vorschaubuild von Visual Studio 2019 Version 16.7 installiert.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

| Eigenschaft | Reserviert oder bekannt | Beschreibung | Beispiel |
|----------------------------------|------------------------| - | - |
| `MSBuildBinPath` | Reserviert | Der absolute Pfad des Ordners, in dem sich die zurzeit verwendeten MSBuild-Binärdateien befinden (z. B. *C:\Windows\Microsoft.Net\Framework\\\<versionNumber>* ). Diese Eigenschaft ist nützlich, wenn Sie auf Dateien im MSBuild-Verzeichnis verweisen müssen.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | Bekannt | Seit .NET Framework 4 gibt es keinen Unterschied zwischen den Standardwerten von `MSBuildExtensionsPath` und `MSBuildExtensionsPath32`. Sie können die Umgebungsvariable `MSBUILDLEGACYEXTENSIONSPATH` auf einen Wert ungleich NULL festlegen, um das Verhalten des Standardwerts von `MSBuildExtensionsPath` in früheren Versionen zu ermöglichen.<br /><br /> In .NET Framework 3.5 und Vorgängerversionen verweist der Standardwert von `MSBuildExtensionsPath` auf den Pfad des MSBuild-Unterordners unter dem Ordner *\Programme\\* oder *\Programme (x86)* , je nach Bitanzahl des aktuellen Prozesses. Bei einem 32-Bit-Prozess auf einem 64-Bit-Computer zeigt diese Eigenschaft beispielsweise auf den Ordner *\Programme (x86)* . Bei einem 64-Bit-Prozess auf einem 64-Bit-Computer zeigt diese Eigenschaft auf den Ordner *\Programme*.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein.<br /><br /> Dieser Speicherort ist nützlich zum Ablegen benutzerdefinierter Zieldateien. Ihre Zieldateien können beispielsweise unter *\Programme\MSBuild\MyFiles\Northwind.targets* installiert sein und dann mithilfe des folgenden XML-Codes in Projektdateien importiert werden:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | Bekannt | Der Pfad zu dem MSBuild-Unterordner unter dem Ordner *\Programme* oder *\Programme (x86)* . Dieser Pfad führt stets zum 32-Bit-Ordner *\Programme* auf einem 32-Bit-Computer und zu *\Programme (x86)* auf einem 64-Bit-Computer. Siehe auch `MSBuildExtensionsPath` und `MSBuildExtensionsPath64`.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | Bekannt | Der Pfad des MSBuild-Unterordners im Ordner *\Programme*. Bei einem 64-Bit-Computer zeigt dieser Pfad immer auf den Ordner *\Programme*. Bei einem 32-Bit-Computer ist dieser Pfad leer. Siehe auch `MSBuildExtensionsPath` und `MSBuildExtensionsPath32`.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein. | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | Reserviert | Der Wert dieser Eigenschaft ist `true`, wenn MSBuild interaktiv ausgeführt wird, wodurch Benutzereingaben zugelassen werden. Diese Einstellung wird von der Befehlszeilenoption `-interactive` gesteuert. | `false` |
| `MSBuildLastTaskResult` | Reserviert | `true`, wenn die vorherige Aufgabe ohne Fehler (auch wenn Warnungen auftraten) abgeschlossen wurde, oder `false`, wenn bei der vorherigen Aufgabe Fehler aufgetreten sind. Wenn ein Fehler in einer Aufgabe auftritt, ist das Auftreten des Fehlers in der Regel das letzte Ereignis in dem jeweiligen Projekt. Daher ist der Wert dieser Eigenschaft niemals `false`, außer in diesen Szenarien:<br /><br /> – Wenn für das `ContinueOnError`-Attribut des [Aufgabenelements (MSBuild)](../msbuild/task-element-msbuild.md)`WarnAndContinue` (oder `true`) bzw. `ErrorAndContinue` festgelegt wird.<br /><br /> – Wenn `Target` über ein [OnError-Element (MSBuild)](../msbuild/onerror-element-msbuild.md) als untergeordnetes Element verfügt. | `true` |
| `MSBuildNodeCount` | Reserviert | Die maximale Anzahl nebenläufiger Prozesse, die beim Erstellen verwendet werden. Dies ist der Wert, den Sie in der Befehlszeile für **-maxcpucount** angegeben haben. Wenn Sie **-maxcpucount** ohne einen Wert angegeben haben, wird die Anzahl der Prozessoren im Computer durch `MSBuildNodeCount` angegeben. Weitere Informationen finden Sie unter [MSBuild-Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md) sowie unter [Paralleles Erstellen von mehreren Projekten mit MSBuild](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). | 1 |
| `MSBuildProgramFiles32` | Reserviert | Der Speicherort des Ordners für 32-Bit-Programme, beispielsweise *C:\Programme (x86)* .<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein. | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | Reserviert | Die vollständige Liste der Ziele, die im `DefaultTargets`-Attribut des `Project`-Elements angegeben sind. Das folgende `Project`-Element würde beispielsweise über einen `MSBuildDefaultTargets`-Eigenschaftswert von `A;B;C` verfügen:<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | Reserviert | Der absolute Pfad des Verzeichnisses, in dem sich die Projektdatei befindet, beispielsweise *C:\MyCompany\MyProduct*.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein. | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | Reserviert | Der Wert der `MSBuildProjectDirectory`-Eigenschaft, ausschließlich des Stammlaufwerks.<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein. | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | Reserviert | Die Erweiterung der Projektdatei, einschließlich des Punkts, z.B. *.proj*. | `.csproj`|
| `MSBuildProjectFile` | Reserviert | Der vollständige Dateiname der Projektdatei, einschließlich der Erweiterung, z.B. *MyApp.proj*. | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | Reserviert | Der absolute Pfad und der vollständige Dateiname der Projektdatei, einschließlich der Erweiterung, beispielsweise *C:\MyCompany\MyProduct\MyApp.proj*. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | Reserviert | Der Dateiname der Projektdatei ohne die Erweiterung, z.B. *MyApp*. | `ConsoleApp1` |
| `MSBuildRuntimeType` | Reserviert | Der Typ der Laufzeit, der derzeit ausgeführt wird. Eingeführt in MSBuild 15. Der Wert ist möglicherweise nicht definiert (vor MSBuild 15). `Full` gibt an, dass MSBuild auf dem Desktop .NET Framework ausgeführt wird, `Core`, dass MSBuild unter .NET Core ausgeführt wird (z. B. in `dotnet build`) und `Mono`, dass MSBuild unter Mono ausgeführt wird. | `Full` |
| `MSBuildStartupDirectory` | Reserviert | Der absolute Pfad des Ordners, in dem MSBuild aufgerufen wird. Wenn Sie diese Eigenschaft verwenden, können Sie alles unterhalb eines bestimmten Punkts in einer Projektstruktur erstellen, ohne *\<dirs>.proj* -Dateien in jedem Verzeichnis zu erstellen. Stattdessen haben Sie wie hier gezeigt nur ein Projekt, beispielsweise *C:\traversal.proj* :<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Geben Sie für die Erstellung an einem beliebigen Punkt in der Struktur Folgendes ein:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Schließen Sie nicht den abschließenden umgekehrten Schrägstrich in dieser Eigenschaft ein. | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | Reserviert | Der Teil von `MSBuildThisFileFullPath`, der den Dateinamen und die Dateierweiterung angibt. | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | Reserviert | Der Teil von `MSBuildThisFileFullPath`, der das Verzeichnis angibt.<br /><br /> Schließen Sie den abschließenden umgekehrten Schrägstrich in den Pfad ein. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | Reserviert | Der Teil von `MSBuildThisFileFullPath`, der das Verzeichnis angibt, ausschließlich des Stammlaufwerks.<br /><br /> Schließen Sie den abschließenden umgekehrten Schrägstrich in den Pfad ein. | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | Reserviert | Der Teil von `MSBuildThisFileFullPath`, der die Dateinamenerweiterung angibt. | `.csproj` |
| `MSBuildThisFileFullPath` | Reserviert | Der absolute Pfad des Projekts oder der TARGETS-Datei, die das gerade ausgeführte Ziel enthält.<br /><br /> Tipp: Sie können einen relativen Pfad in einer TARGETS-Datei angegeben, der relativ zur TARGETS-Datei und nicht relativ zur ursprünglichen Projektdatei ist. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | Reserviert | Der Teil von `MSBuildThisFileFullPath`, der den Dateinamen angibt, jedoch ohne die Dateinamenerweiterung. | `ConsoleApp1` |
| `MSBuildToolsPath` | Reserviert | Der Installationspfad der MSBuild-Version, die mit dem Wert von `MSBuildToolsVersion` verknüpft ist.<br /><br /> Schließen Sie den abschließenden umgekehrten Schrägstrich nicht in den Pfad ein.<br /><br /> Diese Eigenschaft kann nicht überschrieben werden. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | Reserviert | Die Version des MSBuild-Toolsets, das zum Erstellen des Projekts verwendet wird.<br /><br /> Hinweis: Ein MSBuild-Toolset besteht aus Aufgaben, Zielen und Tools, die zum Erstellen einer Anwendung verwendet werden. Zu den Tools zählen Compiler wie *csc.exe* und *vbc.exe*. Weitere Informationen finden Sie unter [MSBuild-Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) sowie unter [Standardmäßige und benutzerdefinierte Toolsetkonfigurationen](../msbuild/standard-and-custom-toolset-configurations.md). | `Current` |
| `MSBuildVersion` | Reserviert | Die Version von MSBuild, die zum Erstellen des Projekts verwendet wird. <br /><br/> Diese Eigenschaft kann nicht überschrieben werden. Andernfalls wird die Fehlermeldung `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` zurückgegeben. | 16.7.0 |

## <a name="names-that-conflict-with-msbuild-elements"></a>Namen, die Konflikte mit MSBuild-Elementen auslösen

Zusätzlich zu den oben genannten können MSBuild-Sprachelemente entsprechende Namen nicht für benutzerdefinierte Eigenschaften, Elemente oder Elementmetadaten verwendet werden:

* VisualStudioProject
* Target
* PropertyGroup
* Output
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Choose
* When
* Otherwise

## <a name="see-also"></a>Siehe auch

- [MSBuild-Referenz](../msbuild/msbuild-reference.md)

- [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md)
