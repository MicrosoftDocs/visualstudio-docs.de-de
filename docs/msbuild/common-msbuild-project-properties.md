---
title: Gemeinsame MSBuild-Projekteigenschaften | Microsoft-Dokumentation
description: Erfahren Sie mehr über gemeinsame MSBuild-Projekteigenschaften, die in Projektdateien definiert oder verwendet werden bzw. in den von MSBuild bereitgestellten TARGETS-Dateien enthalten sein können.
ms.custom: SEO-VS-2020
ms.date: 01/18/2018
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- msbuild, common properties
- msbuild, project file properties
- ExcludeDeploymentUrl property
- project file properties (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 548116fc3c9b360a866f14e32074111dfdc872d9
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533874"
---
# <a name="common-msbuild-project-properties"></a>Gemeinsame MSBuild-Projekteigenschaften

In der folgenden Tabelle werden häufig verwendete Eigenschaften aufgelistet, die in den Visual Studio-Projektdateien definiert oder in den *TARGETS*-Dateien enthalten sind, die von MSBuild bereitgestellt werden.

 Projektdateien in Visual Studio (*CSPROJ-* , *VBPROJ-* , *VCXPROJ*-Dateien und andere) enthalten MSBuild-XML-Code, der ausgeführt wird, wenn Sie ein Projekt mithilfe der IDE erstellen. Projekte importieren in der Regel mindestens eine *TARGETS*-Datei, um den entsprechenden Buildprozess zu definieren. Weitere Informationen finden Sie unter [TARGETS-Dateien von MSBuild](../msbuild/msbuild-dot-targets-files.md).

## <a name="list-of-common-properties-and-parameters"></a>Liste häufig verwendeter Eigenschaften und Parameter

| Eigenschaften- oder Parametername | Projekttypen | Beschreibung |
|------------------------------------| - | - |
| AdditionalLibPaths | .NET | Gibt weitere Ordner an, in denen Compiler nach Verweisassemblys suchen sollen. |
| AddModules | .NET | Bewirkt, dass der Compiler dem Projekt, das Sie kompilieren, sämtliche Typinformationen aus den angegebenen Dateien bereitstellt. Diese Eigenschaft entspricht dem `/addModules`-Compilerschalter. |
| ALToolPath | .NET | Der Pfad, unter dem *AL.exe* gespeichert ist. Diese Eigenschaft überschreibt die aktuelle Version von *AL.exe*, um die Verwendung einer anderen Version zu ermöglichen. |
| ApplicationIcon | .NET | Die *ICO*-Symboldatei, die zum Einbetten als Win32-Symbol an den Compiler übergeben wird. Die Eigenschaft entspricht dem `/win32icon`-Compilerschalter. |
| ApplicationManifest | Alle | Gibt den Pfad der Datei an, die verwendet wird, um externe Manifestinformationen zur Benutzerkontensteuerung (User Account Control, UAC) zu erzeugen. Gilt nur für Visual Studio-Projekte für Windows Vista.<br /><br /> In den meisten Fällen wird das Manifest eingebettet. Wenn Sie jedoch COM ohne Registrierung oder eine ClickOnce zur Bereitstellung verwenden, kann das Manifest eine externe Datei sein, die zusammen mit Ihren Anwendungsassemblys installiert wird. Weitere Informationen finden Sie unter der "NoWin32Manifest"-Eigenschaft in diesem Thema. |
| AssemblyOriginatorKeyFile | .NET | Gibt die Datei an, die verwendet wird, um die Assembly (*SNK* oder *PFX*) zu signieren, und die an die [ResolveKeySource](../msbuild/resolvekeysource-task.md)-Aufgabe übergeben wird, um den tatsächlichen Schlüssel zu generieren, mit dem die Assembly signiert wird. |
| AssemblySearchPaths | .NET | Eine Liste von Speicherorten, die bei der Verweisassemblyauflösung zur Buildzeit durchsucht werden sollen. Die Reihenfolge der aufgelisteten Pfade ist von Bedeutung, da Pfade weiter oben in der Liste Vorrang vor weiter unten stehenden Pfaden haben. |
| AssemblyName | .NET | Der Name der endgültigen Ausgabeassembly, nachdem das Projekt erstellt wurde. |
| BaseAddress | .NET | Gibt die Basisadresse der Hauptausgabeassembly an. Diese Eigenschaft entspricht dem `/baseaddress`-Compilerschalter. |
| BaseIntermediateOutputPath | Alle | Der Ordner der obersten Ebene, in dem alle konfigurationsspezifischen Zwischenausgabeordner erstellt werden. Der Standardwert ist `obj\`. Codebeispiel: `<BaseIntermediateOutputPath>c:\xyz\obj\</BaseIntermediateOutputPath>` |
| BaseOutputPath | Alle | Gibt den Basispfad für die Ausgabedatei an. Sofern festgelegt, verwendet MSBuild `OutputPath = $(BaseOutputPath)\$(Configuration)\`. Beispielsyntax: `<BaseOutputPath>c:\xyz\bin\</BaseOutputPath>` |
| BuildInParallel | Alle | Ein boolescher Wert, der angibt, ob Projektverweise bei der Verwendung von MSBuild mit Multiprocessing parallel erstellt oder bereinigt werden. Der Standardwert ist `true`. Das bedeutet, dass Projekte parallel erstellt werden, wenn das System über mehrere Kerne oder Prozessoren verfügt. |
| BuildProjectReferences | Alle | Ein boolescher Wert, der angibt, ob Projektverweise durch MSBuild erstellt werden. Automatisch auf `false` festgelegt, wenn Sie Ihr Projekt in der integrierten Entwicklungsumgebung (IDE) von Visual Studio erstellen, andernfalls `true`. `-p:BuildProjectReferences=false` kann in der Befehlszeile eingegeben werden, um die Überprüfung von Projekten, auf die verwiesen wird, auf Aktualität zu vermeiden. |
| CleanFile | Alle | Der Name der Datei, die als "Löschcache" verwendet wird. Der Löschcache ist eine Liste generierter Dateien, die während des Bereinigungsvorgangs gelöscht werden. Die Datei wird vom Buildprozess im Zwischenausgabepfad abgelegt.<br /><br /> Diese Eigenschaft gibt nur Dateinamen an, die keine Pfadinformationen aufweisen. |
| CodePage | .NET | Gibt für alle Quellcodedateien in der Kompilierung die zu verwendende Codepage an. Diese Eigenschaft entspricht dem `/codepage`-Compilerschalter. |
| CompilerResponseFile | .NET | Eine optionale Antwortdatei, die an die Compileraufgaben übergeben werden kann. |
| Konfiguration | Alle | Die Konfiguration, die Sie erstellen, in der Regel `Debug` oder `Release`, die jedoch auf Projektmappen- und Projektebene konfigurierbar ist. |
| CscToolPath | C# | Der Pfad von *csc.exe*, dem C#-Compiler. |
| CustomBeforeMicrosoftCommonTargets | Alle | Der Name einer Projektdatei oder TARGETS-Datei, die vor dem allgemeinen TARGETS-Import automatisch importiert werden soll. |
| DebugSymbols | Alle | Ein boolescher Wert, der angibt, ob Symbole vom Build generiert werden.<br /><br /> Durch das Festlegen von **-p:DebugSymbols=false** in der Befehlszeile wird die Generierung von Programmdatenbank-Symboldateien (*PDB*-Dateien) deaktiviert. |
| DebugType | Alle | Definiert den Umfang der zu generierenden Debuginformationen. Gültige Werte sind „full“, „pdbonly“, „portable“, „embedded“ und „none“. |
| DefineConstants | .NET | Definiert Konstanten für die bedingte Kompilierung. Symbol-Wert-Paare werden durch Semikolons getrennt und mit der folgenden Syntax angegeben:<br /><br /> *symbol1 = value1 ; symbol2 = value2*<br /><br /> Die Eigenschaft entspricht dem `/define`-Compilerschalter. |
| DefineDebug | Alle |  Ein boolescher Wert, der angibt, ob die DEBUG-Konstante definiert werden soll. |
| DefineTrace | Alle | Ein boolescher Wert, der angibt, ob die TRACE-Konstante definiert werden soll. |
| DelaySign | .NET | Ein boolescher Wert, der angibt, ob Sie die Assembly verzögert oder voll signieren möchten. |
| Deterministic | .NET | Ein boolescher Wert, der angibt, ob der Compiler identische Assemblys für identische Eingaben erzeugen sollte. Dieser Parameter entspricht dem Schalter `/deterministic` des Compilers. |
| DisableFastUpToDateCheck | Alle | Ein boolescher Wert, der nur für Visual Studio gilt. Der Visual Studio-Build-Manager stellt mithilfe des FastUpToDateCheck-Prozesses fest, ob ein Projekt neu erstellt werden muss, damit es auf dem neuesten Stand ist. Dieser Prozess ist schneller als die Verwendung von MSBuild. Durch Festlegen der DisableFastUpToDateCheck-Eigenschaft auf `true` können Sie den Visual Studio-Build-Manager umgehen und erzwingen, dass mit MSBuild bestimmt wird, ob das Projekt aktuell ist. |
| DocumentationFile | .NET | Der Name der Datei, die als XML-Dokumentationsdatei generiert wird. Dieser Name umfasst nur den Dateinamen und weist keine Pfadinformationen auf. |
| ErrorReport | .NET | Gibt an, wie interne Compilerfehler von der Compileraufgabe gemeldet werden sollen. Gültige Werte sind "prompt", "send" und "none". Diese Eigenschaft entspricht dem `/errorreport`-Compilerschalter. |
| ExcludeDeploymentUrl | .NET | Dem Bereitstellungsmanifest wird durch die [GenerateDeploymentManifest-Aufgabe](../msbuild/generatedeploymentmanifest-task.md) ein deploymentProvider-Tag hinzugefügt, wenn die Projektdatei eines der folgenden Elemente enthält:<br /><br /> – UpdateUrl<br />– InstallUrl<br />– PublishUrl<br /><br /> Sie können mithilfe von „ExcludeDeploymentUrl“ jedoch verhindern, dass das „deploymentProvider“-Tag zum Bereitstellungsmanifest hinzugefügt wird, auch wenn eine der vorgenannten URLs angegeben wird. Fügen Sie der Projektdatei zu diesem Zweck die folgende Eigenschaft hinzu:<br /><br /> `<ExcludeDeploymentUrl>true</ExcludeDeploymentUrl>` <br /><br />**Hinweis**:  ExcludeDeploymentUrl wird in der Visual Studio-IDE nicht verfügbar gemacht und kann nur festgelegt werden, indem die Projektdatei manuell bearbeitet wird. Das Festlegen dieser Eigenschaft hat keine Auswirkung auf die Veröffentlichung in Visual Studio. Dies bedeutet, dass das deploymentProvider-Tag weiterhin zu der durch „PublishUrl“ angegebenen URL hinzugefügt wird. |
| FileAlignment | .NET | Gibt die Ausrichtung der Abschnitte der Ausgabedatei in Bytes an. Gültige Werte sind 512, 1024, 2048, 4096 und 8192. Diese Eigenschaft entspricht dem `/filealignment`-Compilerschalter. |
| FrameworkPathOverride | Visual Basic | Gibt den Speicherort von *mscorlib.dll* und *microsoft.visualbasic.dll* an. Dieser Parameter entspricht der `/sdkpath`-Option des Compilers *vbc.exe*. |
| GenerateDocumentation | .NET | Ein boolescher Parameter, der angibt, ob eine Dokumentation vom Build generiert wird. Wenn der Wert `true` lautet, werden Dokumentationsinformationen vom Build generiert und zusammen mit dem Namen der ausführbaren Datei oder der Bibliothek, die von der Buildaufgabe erstellt wurde, in einer *XML*-Datei gespeichert. |
| GenerateFullPaths | C# | Mit dieser Eigenschaft werden vollständige Pfade für Dateinamen in der Ausgabe mithilfe der Compileroption [-fullpaths](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) generiert. |
| GenerateSerializationAssemblies | .NET | Gibt an, ob das XML-Serialisierungsassemblys durch *SGen.exe* generiert werden soll. Die Ausführung kann automatisiert, aktiviert oder deaktiviert werden. Diese Eigenschaft wird für Assemblys verwendet, deren Ziel nur das .NET Framework ist. Zum Generieren von XML-Serialisierungsassemblys für .NET Standard oder .NET Core-Assemblys verweisen Sie auf das NuGet-Paket *Microsoft.XmlSerializer.Generator*. |
| IntermediateOutputPath | Alle | Der vollständige Zwischenausgabepfad wie von `BaseIntermediateOutputPath` abgeleitet, wenn kein Pfad angegeben wird. Beispiel: *\obj\debug\\* . |
| KeyContainerName | Alle | Der Name des Containers mit dem Schlüssel für einen starken Namen. |
| KeyOriginatorFile | Alle | Der Name der Datei mit dem Schlüssel für einen starken Namen. |
| ModuleAssemblyName | .NET | Der Name der Assembly, in die das kompilierte Modul integriert werden soll. Die Eigenschaft entspricht dem `/moduleassemblyname`-Compilerschalter. |
| MSBuildProjectExtensionsPath | Alle | Gibt den Pfad an, unter dem Projekterweiterungen gespeichert sind. Standardmäßig entspricht dies dem Wert von `BaseIntermediateOutputPath`. |
| NoLogo | Alle | Ein boolescher Wert, der angibt, ob das Compilerlogo deaktiviert werden soll. Diese Eigenschaft entspricht dem `/nologo`-Compilerschalter. |
| NoStdLib | .NET | Ein boolescher Wert, der angibt, ob Verweise auf die Standardbibliothek (*mscorlib.dll*) vermieden werden sollen. Der Standardwert ist `false`. |
| NoVBRuntimeReference | Visual Basic | Ein boolescher Wert, der angibt, ob die Visual Basic-Runtime (*Microsoft.VisualBasic.dll*) als Verweis in das Projekt eingefügt werden soll. |
| NoWarn | .NET | Unterdrückt die angegebenen Warnungen. Lediglich der numerische Teil des Warnungsbezeichners muss angegeben werden. Mehrere Warnungen werden durch Semikolons getrennt. Dieser Parameter entspricht dem Schalter `/nowarn` des Compilers. |
| NoWin32Manifest | .NET | Ein boolescher Wert, der angibt, ob Manifestinformationen zur Benutzerkontensteuerung (User Account Control, UAC) in die ausführbare Datei der Anwendung eingebettet werden. Gilt nur für Visual Studio-Projekte für Windows Vista. In Projekten, die mit ClickOnce und COM ohne Registrierung bereitgestellt werden, wird dieses Element ignoriert. `False` (der Standardwert) gibt an, dass Manifestinformationen zur Benutzerkontensteuerung in die ausführbare Datei der Anwendung eingebettet werden. `True` gibt an, dass UAC-Manifestinformationen nicht eingebettet werden.<br /><br /> Diese Eigenschaft gilt nur für Visual Studio-Projekte für Windows Vista. In Projekten, die mit ClickOnce und COM ohne Registrierung bereitgestellt werden, wird diese Eigenschaft ignoriert.<br /><br /> Sie dürfen „NoWin32Manifest“ nur hinzufügen, wenn Visual Studio keine Manifestinformationen in die ausführbare Datei der Anwendung einbetten soll. Dieser Vorgang wird als *Virtualisierung* bezeichnet. Legen Sie zur Verwendung der Virtualisierung `<ApplicationManifest>` zusammen mit `<NoWin32Manifest>` wie folgt fest:<br /><br /> – Für Visual Basic-Projekte: Entfernen Sie den `<ApplicationManifest>`-Knoten. (In Visual Basic-Projekten wird `<NoWin32Manifest>` ignoriert, wenn ein `<ApplicationManifest>`-Knoten vorhanden ist.)<br />– Legen Sie bei C#-Projekten für `<ApplicationManifest>` den Wert `False` und für `<NoWin32Manifest>` den Wert `True` fest. (In C#-Projekten wird `<ApplicationManifest>` von `<NoWin32Manifest>` überschrieben.)<br /> Diese Eigenschaft entspricht der `/nowin32manifest`-Compileroption von *vbc.exe*. |
| Optimize | .NET | Ein boolescher Wert, der Compileroptimierungen aktiviert, wenn er auf `true` festgelegt ist. Diese Eigenschaft entspricht dem `/optimize`-Compilerschalter. |
| OptionCompare | Visual Basic | Gibt an, wie Zeichenfolgenvergleiche durchgeführt werden. Gültige Werte sind "binary" oder "text". Diese Eigenschaft entspricht der `/optioncompare`-Compileroption von *vbc.exe*. |
| OptionExplicit | Visual Basic | Ein boolescher Wert, der angibt, dass Variablen im Quellcode explizit deklariert werden müssen, wenn er auf `true` festgelegt ist. Diese Eigenschaft entspricht dem `/optionexplicit`-Compilerschalter. |
| OptionInfer | Visual Basic | Ein boolescher Wert, der den Typrückschluss von Variablen aktiviert, wenn er auf `true` festgelegt ist. Diese Eigenschaft entspricht dem `/optioninfer`-Compilerschalter. |
| OptionStrict | Visual Basic | Ein boolescher Wert, bei dessen Festlegung auf `true` von der Buildaufgabe eine strikte Typsemantik erzwungen wird, um implizite Typkonvertierungen einzuschränken. Diese Eigenschaft entspricht der `/optionstrict`-Option des Compilers *vbc.exe*. |
| OutDir | Alle | Gibt den endgültigen Ausgabespeicherort des Projekts oder der Projektmappe an. Beim Entwickeln einer Lösung lassen sich mit OutDir mehrere Projektausgaben an einem Speicherort erfassen. Außerdem ist OutDir in der Eigenschaft „AssemblySearchPaths“ enthalten, die zum Auflösen von Verweisen verwendet wird. Beispiel: *bin\Debug*. |
| OutputPath | Alle | Gibt den Pfad zum Ausgabeverzeichnis relativ zum Projektverzeichnis an, zum Beispiel *bin\Debug*. |
| OutputType | Alle |  Gibt das Dateiformat der Ausgabedatei an. Dieser Parameter kann einen der folgenden Werte aufweisen:<br /><br /> – Library. Erstellt eine Codebibliothek. (Standardwert)<br />– Exe. Erstellt eine Konsolenanwendung.<br />– Module. Erstellt ein Modul.<br />– Winexe. Erstellt ein Windows-Programm.<br /><br /> Für C# und Visual Basic entspricht diese Eigenschaft dem Schalter `/target`. |
| OverwriteReadOnlyFiles | Alle | Ein boolescher Wert, der angibt, ob schreibgeschützte Dateien vom Build überschrieben werden sollen oder ob ein Fehler ausgelöst werden soll. |
| PathMap | .NET | Gibt an, wie physische Pfade den Quellpfadnamen zugeordnet werden, die vom Compiler ausgegeben werden. Diese Eigenschaft entspricht dem Schalter `/pathmap` des Compilers. |
| PdbFile | .NET | Der Dateiname der *PDB*-Datei, die Sie ausgeben. Diese Eigenschaft entspricht der `/pdb`-Option des Compilers *csc.exe*. |
| Plattform | Alle | Das Betriebssystem, für das Sie erstellen. Beispiele für .NET Framework-Builds sind Any CPU, x86 und x64. |
| ProcessorArchitecture | .NET | Die Prozessorarchitektur, die zum Auflösen von Assemblyverweisen verwendet wird. Gültige Werte sind "msil", "x86", "amd64" und "ia64". |
| ProduceOnlyReferenceAssembly | .NET | Ein boolescher Wert, der den Compiler anweist, nur eine Verweisassembly und keinen kompilierten Code ausgegeben. Kann nicht in Verbindung mit `ProduceReferenceAssembly` verwendet werden.  Diese Eigenschaft entspricht der `/refonly`-Option der Compiler *vbc.exe* und *csc.exe*. |
| ProduceReferenceAssembly | .NET | Ein boolescher Wert, der auf `true` festgelegt wurde, ermöglicht die Produktion von [Verweisassemblys](/dotnet/standard/assembly/reference-assemblies) für die aktuelle Assembly. `Deterministic` sollte beim Verwenden dieser Funktion `true` entsprechen. Diese Eigenschaft entspricht der `/refout`-Option der Compiler *vbc.exe* und *csc.exe*. |
| RemoveIntegerChecks | Visual Basic | Ein boolescher Wert, der angibt, ob Überprüfungen auf Ganzzahlüberlauf-Fehler deaktiviert werden sollen. Der Standardwert ist `false`. Diese Eigenschaft entspricht der `/removeintchecks`-Option des Compilers *vbc.exe*. |
| RootNamespace | Alle | Der zu verwendende Stammnamespace, wenn Sie eine eingebettete Ressource benennen. Dieser Namespace ist Teil des Manifestnamens der eingebetteten Ressource. |
| Satellite_AlgorithmId | .NET | Die ID des zu verwendenden *AL.exe*-Hashalgorithmus beim Erstellen von Satellitenassemblys. |
| Satellite_BaseAddress | .NET | Die zu verwendende Basisadresse, wenn kulturspezifische Satellitenassemblys mit dem `CreateSatelliteAssemblies`-Ziel erstellt werden. |
| Satellite_CompanyName | .NET | Der Unternehmensname, der während der Erstellung der Satellitenassembly an *AL.exe* übergeben werden soll. |
| Satellite_Configuration | .NET | Der Konfigurationsname, der während der Erstellung der Satellitenassembly an *AL.exe* übergeben werden soll. |
| Satellite_Description | .NET | Der Beschreibungstext, der während der Erstellung der Satellitenassembly an *AL.exe* übergeben werden soll. |
| Satellite_EvidenceFile | .NET | Bettet die angegebene Datei in die Satellitenassembly mit dem Ressourcennamen "Security.Evidence" ein. |
| Satellite_FileVersion | .NET | Gibt eine Zeichenfolge für das Feld "File Version" in der Satellitenassembly an. |
| Satellite_Flags | .NET | Gibt einen Wert für das Feld "Flags" in der Satellitenassembly an. |
| Satellite_GenerateFullPaths | .NET | Veranlasst die Buildaufgabe, absolute Pfade für alle Dateien zu verwenden, die in einer Fehlermeldung gemeldet werden. |
| Satellite_LinkResource | .NET | Verknüpft die angegebenen Ressourcendateien mit einer Satellitenassembly. |
| Satellite_MainEntryPoint | .NET | Gibt den voll qualifizierten Namen (also "Klasse.Methode") der Methode an, die als Einstiegspunkt zu verwenden ist, wenn ein Modul während der Erstellung einer Satellitenassembly in eine ausführbare Datei konvertiert wird. |
| Satellite_ProductName | .NET | Gibt eine Zeichenfolge für das Feld "Product" in der Satellitenassembly an. |
| Satellite_ProductVersion | .NET | Gibt eine Zeichenfolge für das Feld "ProductVersion" in der Satellitenassembly an. |
| Satellite_TargetType | .NET | Gibt das Dateiformat der Ausgabedatei der Satellitenassembly als "library", "exe" oder "win" an. Der Standardwert ist "library". |
| Satellite_Title | .NET | Gibt eine Zeichenfolge für das Feld "Title" in der Satellitenassembly an. |
| Satellite_Trademark | .NET | Gibt eine Zeichenfolge für das Feld "Trademark" in der Satellitenassembly an. |
| Satellite_Version | .NET | Gibt die Versionsinformationen für die Satellitenassembly an. |
| Satellite_Win32Icon | .NET | Fügt eine *ICO*-Symboldatei in die Satellitenassembly ein. |
| Satellite_Win32Resource | .NET | Fügt eine Win32-Ressource (*RES*-Datei) in die Satellitenassembly ein. |
| SGenToolPath | .NET | Ein optionaler Toolpfad, der angibt, von wo *SGen.exe* abgerufen werden kann, wenn die aktuelle Version von *SGen.exe* überschrieben wurde. |
| SGenUseProxyTypes | .NET | Ein boolescher Wert, der angibt, ob Proxytypen von *SGen.exe* generiert werden sollen. Dies gilt nur, wenn *GenerateSerializationAssemblies* aktiviert ist.<br /><br /> Das SGen-Ziel verwendet diese Eigenschaft, um das "UseProxyTypes"-Flag festzulegen. Diese Eigenschaft wird standardmäßig auf "true" festgelegt. Es ist keine Benutzeroberfläche verfügbar, um diesen Wert zu ändern. Fügen Sie diese Eigenschaft der Projektdatei hinzu, und legen Sie sie auf FALSE fest, bevor Sie *Microsoft.Common.Targets* oder *C#/VB.targets* importieren, um die Serialisierungsassembly für nicht webdienstbezogene Typen zu generieren. |
| SkipInvalidConfigurations | Alle | Wenn `true`, wird eine Warnung zu ungültigen Plattform- und Konfigurationskombinationen generiert, aber der Build schlägt nicht fehl. Wenn `false` oder undefiniert (Standardeinstellung), wird ein Fehler generiert. |
| StartupObject | .NET | Gibt die Klasse oder das Modul an, die bzw. das die "Main"-Methode oder die "Sub Main"-Prozedur enthält. Diese Eigenschaft entspricht dem `/main`-Compilerschalter. |
| SubsystemVersion | .NET | Gibt die mindestens erforderliche Version des Subsystems an, die die generierte ausführbare Datei verwenden kann. Diese Eigenschaft entspricht dem `/subsystemversion`-Compilerschalter. Informationen zum Standardwert dieser Eigenschaft finden Sie unter [/subsystemversion (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/subsystemversion) oder [/subsystemversion (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/subsystemversion-compiler-option). |
| TargetCompactFramework | .NET | Die Version von .NET Compact Framework, die zur Ausführung der zu erstellenden Anwendung erforderlich ist. Durch diese Angabe können Sie auf bestimmte Frameworkassemblys verweisen, auf die andernfalls möglicherweise nicht verwiesen werden kann. |
| TargetFrameworkVersion | .NET | Die Version von .NET Framework, die zur Ausführung der zu erstellenden Anwendung erforderlich ist. Durch diese Angabe können Sie auf bestimmte Frameworkassemblys verweisen, auf die andernfalls möglicherweise nicht verwiesen werden kann. |
| TreatWarningsAsErrors | .NET | Ein boolescher Parameter. Wenn sein Wert `true` lautet, werden alle Warnungen als Fehler behandelt. Dieser Parameter entspricht dem `/nowarn`-Compilerschalter. |
| UseHostCompilerIfAvailable | .NET | Ein boolescher Parameter. Wenn sein Wert `true` lautet, verwendet die Buildaufgabe das prozessinterne Compilerobjekt, falls es verfügbar ist. Dieser Parameter wird nur von Visual Studio verwendet. |
| Utf8Output | .NET | Ein boolescher Parameter. Wenn sein Wert `true` lautet, wird die Compilerausgabe mithilfe der UTF-8-Codierung protokolliert. Dieser Parameter entspricht dem `/utf8Output`-Compilerschalter. |
| VbcToolPath | Visual Basic | Ein optionaler Pfad, der einen anderen Speicherort für *vbc.exe* angibt, wenn die aktuelle Version von *vbc.exe* überschrieben wurde. |
| VbcVerbosity | Visual Basic | Gibt den Ausführlichkeitsgrad der Ausgabe des Visual Basic-Compilers an. Gültige Werte sind "Quiet", "Normal" (der Standardwert) und "Verbose". |
| VisualStudioVersion | Alle | Gibt die Version von Visual Studio an, mit der dieses Projekt ausgeführt werden sollte. Wenn diese Eigenschaft nicht angegeben wird, wird ein angemessener Standardwert von MSBuild festgelegt.<br /><br /> Diese Eigenschaft wird in mehreren Projekttypen verwendet, um den Satz der Ziele anzugeben, die für den Build verwendet werden. Wenn für `ToolsVersion` "4.0" oder ein höherer Wert für ein Projekt festgelegt wird, wird das zu verwendende Unter-Toolset mithilfe von `VisualStudioVersion` festgelegt. Weitere Informationen finden Sie unter [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md). |
| WarningsAsErrors | .NET | Gibt eine Liste mit Warnungen an, die als Fehler behandelt werden sollen. Dieser Parameter entspricht dem `/warnaserror`-Compilerschalter. |
| WarningsNotAsErrors | .NET | Gibt eine Liste mit Warnungen an, die nicht als Fehler behandelt werden sollen. Dieser Parameter entspricht dem `/warnaserror`-Compilerschalter. |
| Win32Manifest | .NET | Der Name der Manifestdatei, die in die endgültige Assembly eingebettet werden soll. Dieser Parameter entspricht dem `/win32Manifest`-Compilerschalter. |
| Win32Resource | .NET | Der Dateiname der Win32-Ressource, die in die endgültige Assembly eingebettet werden soll. Dieser Parameter entspricht dem `/win32resource`-Compilerschalter. |

## <a name="see-also"></a>Siehe auch

- [Gemeinsame MSBuild-Projektelemente](../msbuild/common-msbuild-project-items.md)
- [Gemeinsame MSBuild-Elementmetadaten](common-msbuild-item-metadata.md)
- [Reservierte und bekannte Eigenschaften für MSBuild](msbuild-reserved-and-well-known-properties.md)
- [MSBuild-Referenz für .NET SDK-Projekte](/dotnet/core/project-sdk/msbuild-props)
