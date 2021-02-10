---
title: Vbc-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „Vbc“ die Datei „vbc.exe“ umschließt, die ausführbare Dateien, Dynamic Link Libraries (DLLs) oder Codemodule erzeugt.
ms.custom: SEO-VS-2020
ms.date: 04/12/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6596dd0893d0ab302a738cb12856fc6758df039
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908871"
---
# <a name="vbc-task"></a>Vbc-Aufgabe

Umschließt die Datei *vbc.exe*, die ausführbare Dateien (*EXE*), Dynamic Link Libraries (*DLL*) oder Codemodule (*NETMODULE*) produziert. Weitere Informationen zu *vbc.exe* finden Sie unter [Visual Basic-Befehlszeilencompiler](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `Vbc` -Aufgabe beschrieben.

| Parameter | Beschreibung |
|------------------------------| - |
| `AdditionalLibPaths` | Optionaler `String[]`-Parameter.<br /><br /> Gibt weitere Ordner an, in denen nach im Verweisattribut angegebenen Assemblys gesucht werden soll |
| `AddModules` | Optionaler `String[]`-Parameter.<br /><br /> Bewirkt, dass der Compiler dem Projekt, das Sie aktuell kompilieren, sämtliche Typinformationen aus den angegebenen Dateien bereitstellt. Dieser Parameter entspricht der Option [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) des Compilers *vbc.exe*. |
| `BaseAddress` | Optionaler `String`-Parameter.<br /><br /> Gibt die Basisadresse einer DLL an. Dieser Parameter entspricht der Option [-baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) des Compilers *vbc.exe*. |
| `CodePage` | Optionaler `Int32`-Parameter.<br /><br /> Gibt die für alle Quellcodedateien in der Kompilierung die zu verwendende Codepage an. Dieser Parameter entspricht der Option [-codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) des Compilers *vbc.exe*. |
| `DebugType` | Optionaler `String[]`-Parameter.<br /><br /> Veranlasst, dass der Compiler Debuginformationen generiert. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Der Standardwert ist `full`, wodurch ermöglicht wird, einen Debugger an ein ausgeführtes Programm anzufügen. Der Wert `pdbonly` macht das Debuggen von Quellcode möglich, wenn das Programm im Debugger gestartet wird. Der Assembler wird jedoch nur angezeigt, wenn das aktive Programm an den Debugger angefügt ist. Weitere Informationen finden Sie unter [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Optionaler `String[]`-Parameter.<br /><br /> Definiert Konstanten für die bedingte Kompilierung. Symbol-Wert-Paare werden durch Semikolons getrennt und mit der folgenden Syntax angegeben:<br /><br /> *Symbol1* `=` *Wert1* `;` *Symbol2* `=` *Wert2*<br /><br /> Dieser Parameter entspricht der Option [-define](/dotnet/visual-basic/reference/command-line-compiler/define) des Compilers *vbc.exe*. |
| `DelaySign` | Optionaler `Boolean`-Parameter.<br /><br /> Ist der Wert `true`, legt die Aufgabe den öffentlichen Schlüssel in der Assembly ab. Ist der Wert `false`, signiert die Aufgabe die Assembly vollständig. Der Standardwert ist `false`. Dieser Parameter hat keine Auswirkung, es sei denn, er wird mit den Parametern `KeyFile` oder `KeyContainer` verwendet. Dieser Parameter entspricht der Option [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) des Compilers *vbc.exe*. |
| `Deterministic` | Optionaler `Boolean`-Parameter.<br/><br/> Wenn dieser auf `true` festgelegt ist, gibt der Compiler eine Assembly aus, deren Inhalt im Binärformat über Kompilierungen identisch ist, wenn die Eingaben identisch sind.<br/><br/>Weitere Informationen finden Sie unter [-deterministic](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Optionaler `String`-Parameter.<br /><br /> Unterdrückt die angegebenen Warnungen. Sie müssen lediglich den numerischen Teil des Warnungsbezeichners angeben. Mehrere Warnungen werden durch Semikolons getrennt. Dieser Parameter entspricht der Option [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) des Compilers *vbc.exe*. |
| `DocumentationFile` | Optionaler `String`-Parameter.<br /><br /> Verarbeitet Dokumentationskommentare zu der angegebenen XML-Datei. Dieser Parameter überschreibt das `GenerateDocumentation`-Attribut. Weitere Informationen finden Sie unter [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Optionaler `Boolean`-Parameter.<br /><br /> Ist der Wert `true`, generiert die Aufgabe Debuginformationen und platziert sie in einer Programmdatenbankdatei (*PDB*-Datei). Weitere Informationen finden Sie unter [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Optionaler `String`-Parameter.<br /><br /> Gibt an, wie interne Compilerfehler von der Aufgabe gemeldet werden sollen. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Wenn `prompt` angegeben ist und ein interner Compilerfehler auftritt, wird der Benutzer gefragt, ob die Fehlerdaten an Microsoft gesendet werden sollen.<br /><br /> Wenn `send` angegeben ist und ein interner Compilerfehler auftritt, sendet die Aufgabe Fehlerdaten an Microsoft.<br /><br /> Der Standardwert ist `none`, der Fehler im nur als Textausgabe berichtet.<br /><br /> Dieser Parameter entspricht der Option [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) des Compilers *vbc.exe*. |
| `FileAlignment` | Optionaler `Int32`-Parameter.<br /><br /> Gibt die Ausrichtung der Abschnitte der Ausgabedatei in Bytes an. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Dieser Parameter entspricht der Option [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) des Compilers *vbc.exe*. |
| `GenerateDocumentation` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` lautet, werden Dokumentationsinformationen generiert und zusammen mit dem Namen der ausführbaren Datei oder der Bibliothek, die von der Aufgabe erstellt wurde, in einer XML-Datei gespeichert. Weitere Informationen finden Sie unter [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Importiert Namespaces aus den angegebenen Auflistungen. Dieser Parameter entspricht der Option [-imports](/dotnet/visual-basic/reference/command-line-compiler/imports) des Compilers *vbc.exe*. |
| `KeyContainer` | Optionaler `String`-Parameter.<br /><br /> Gibt den Namen des kryptografischen Schlüsselcontainers an. Dieser Parameter entspricht der Option [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) des Compilers *vbc.exe*. |
| `KeyFile` | Optionaler `String`-Parameter.<br /><br /> Gibt den Dateinamen mit dem kryptografischen Schlüssel an. Weitere Informationen finden Sie unter [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Optionaler <xref:System.String?displayProperty=fullName>-Parameter.<br /><br /> Gibt die [Sprachversion](/dotnet/visual-basic/language-reference/configure-language-version) (z.B. 15.5) an. |
| `LinkResources` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Erstellt einen Link zu einer .NET Framework-Ressource in der Ausgabedatei. Die Ressourcendatei wird nicht in der Ausgabedatei platziert. Dieser Parameter entspricht der Option [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) des Compilers *vbc.exe*. |
| `MainEntryPoint` | Optionaler `String`-Parameter.<br /><br /> Gibt die Klasse oder das Modul mit dem Speicherort der `Sub Main`-Prozedur an. Dieser Parameter entspricht der Option [-main](/dotnet/visual-basic/reference/command-line-compiler/main) des Compilers *vbc.exe*. |
| `ModuleAssemblyName` | Optionaler `String`-Parameter.<br /><br /> Gibt die Assembly an, zu der dieses Modul gehört. |
| `NoConfig` | Optionaler `Boolean`-Parameter.<br /><br /> Gibt an, dass der Compiler die Datei *vbc.rsp* nicht verwenden soll. Dieser Parameter entspricht dem Parameter [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) des Compilers *vbc.exe*. |
| `NoLogo` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden die Compilerbannerinformationen unterdrückt. Dieser Parameter entspricht der Option [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) des Compilers *vbc.exe*. |
| `NoStandardLib` | Optionaler `Boolean`-Parameter.<br /><br /> Bewirkt, dass der Compiler nicht auf die Standardbibliotheken verweist. Dieser Parameter entspricht der Option [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) des Compilers *vbc.exe*. |
| `NoVBRuntimeReference` | Optionaler `Boolean`-Parameter.<br /><br /> Nur zur internen Verwendung. Wenn der Wert TRUE ist, wird der automatische Verweis auf *Microsoft.VisualBasic.dll* verhindert. |
| `NoWarnings` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn dieser auf `true` festgelegt ist, unterdrückt die Aufgabe alle Warnungen. Weitere Informationen finden Sie unter [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden Compileroptimierungen aktiviert. Dieser Parameter entspricht der Option [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) des Compilers *vbc.exe*. |
| `OptionCompare` | Optionaler `String`-Parameter.<br /><br /> Gibt an, wie Zeichenfolgenvergleiche durchgeführt werden. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Der Wert `binary` gibt an, dass die Aufgabe binäre Zeichenfolgenvergleiche verwendet. Der Wert `text` gibt an, dass die Aufgabe Textzeichenfolgenvergleiche verwendet. Der Standardwert dieses Parameters ist `binary`. Dieser Parameter entspricht der Option [-optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) des Compilers *vbc.exe*. |
| `OptionExplicit` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, ist die explizite Deklaration von Variablen erforderlich. Dieser Parameter entspricht der Option [-optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) des Compilers *vbc.exe*. |
| `OptionInfer` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden Typrückschlüsse von Variablen zugelassen. |
| `OptionStrict` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, erzwingt die Aufgabe eine strikte Typsemantik, um implizite Typkonvertierungen zu beschränken. Dieser Parameter entspricht der Option [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) des Compilers *vbc.exe*. |
| `OptionStrictType` | Optionaler `String`-Parameter.<br /><br /> Gibt an, welche strikte Typsemantik eine Warnung generiert. Derzeit wird nur „custom“ unterstützt. Dieser Parameter entspricht der Option [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) des Compilers *vbc.exe*. |
| `OutputAssembly` | Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt den Namen der Ausgabedatei an. Dieser Parameter entspricht der Option [-out](/dotnet/visual-basic/reference/command-line-compiler/out) des Compilers *vbc.exe*. |
| `Platform` | Optionaler `String`-Parameter.<br /><br /> Gibt die Prozessorplattform an, die das Ziel der Ausgabedatei darstellen soll. Dieser Parameter kann den Wert `x86`, `x64`, `Itanium` oder `anycpu` aufweisen. Der Standardwert ist `anycpu`. Dieser Parameter entspricht der Option [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform) des Compilers *vbc.exe*. |
| `References` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Bewirkt, dass die Aufgabe öffentliche Typinformationen aus den angegebenen Elementen in das aktuelle Projekt importiert. Dieser Parameter entspricht der Option [-reference](/dotnet/visual-basic/reference/command-line-compiler/reference) des Compilers *vbc.exe*. |
| `RemoveIntegerChecks` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden die Fehlerüberprüfungen auf Ganzzahlüberlauf deaktiviert. Der Standardwert ist `false`. Dieser Parameter entspricht der Option [-removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) des Compilers *vbc.exe*. |
| `Resources` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Bettet eine .NET Framework-Ressource in die Ausgabedatei ein. Dieser Parameter entspricht der Option [-resource](/dotnet/visual-basic/reference/command-line-compiler/resource) des Compilers *vbc.exe*. |
| `ResponseFiles` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Antwortdatei an, die Befehle für den die Aufgabe enthalten. Dieser Parameter entspricht der Option [@ (Antwortdatei festlegen)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) des Compilers *vbc.exe*. |
| `RootNamespace` | Optionaler `String`-Parameter.<br /><br /> Gibt den Stammnamespace für alle Typdeklarationen an. Dieser Parameter entspricht der Option [-rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) des Compilers *vbc.exe*. |
| `SdkPath` | Optionaler `String`-Parameter.<br /><br /> Gibt den Speicherort von *mscorlib.dll* und *microsoft.visualbasic.dll* an. Dieser Parameter entspricht der Option [-sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) des Compilers *vbc.exe*. |
| `Sources` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt mindestens eine Visual Basic-Quelldatei an. |
| `TargetCompactFramework` | Optionaler `Boolean`-Parameter.<br /><br /> Bei Festlegung auf `true` wird das Ziel auf das .NET Compact Framework ausgerichtet. Dieser Parameter entspricht der Option [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) des Compilers *vbc.exe*. |
| `TargetType` | Optionaler `String`-Parameter.<br /><br /> Gibt das Dateiformat der Ausgabedatei an. Dieser Parameter kann unterschiedliche Werte aufweisen: `library` erstellt eine Codebibliothek, `exe` erstellt eine Konsolenanwendung, `module` erstellt ein Modul, und `winexe` erstellt ein Windows-Programm. Der Standardwert ist `library`. Dieser Parameter entspricht der Option [-target](/dotnet/visual-basic/reference/command-line-compiler/target) des Compilers *vbc.exe*. |
| `Timeout` | Optionaler `Int32`-Parameter.<br /><br /> Gibt die Zeitdauer in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird. Der Standardwert ist `Int.MaxValue`. Dieser gibt an, dass es kein Zeitlimit gibt. |
| `ToolPath` | Optionaler `String`-Parameter.<br /><br /> Gibt den Speicherort an, von dem aus die Aufgabe die zugrunde liegende ausführbare Datei (*vbc.exe*) lädt. Wenn dieser Parameter nicht angegeben ist, verwendet die Aufgabe den SDK-Installationspfad der Version des Frameworks, die von MSBuild ausgeführt wird. |
| `TreatWarningsAsErrors` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden alle Warnungen wie Fehler behandelt. Weitere Informationen finden Sie unter [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Optionaler `Boolean`-Parameter.<br /><br /> Weist die Aufgabe an, das prozessinterne Compilerobjekt (falls verfügbar) zu verwenden. Wird nur von Visual Studio verwendet. |
| `Utf8Output` | Optionaler `Boolean`-Parameter.<br /><br /> Protokolliert die Compilerausgabe mit UTF-8-Codierung. Dieser Parameter entspricht der Option [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) des Compilers *vbc.exe*. |
| `Verbosity` | Optionaler `String`-Parameter.<br /><br /> Gibt den Ausführlichkeitsgrad der Ausgabe des Compilers an. Der Ausführlichkeitsgrad kann `Quiet`, `Normal` (Standard) oder `Verbose` lauten. |
| `WarningsAsErrors` | Optionaler `String`-Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Dieser Parameter überschreibt den `TreatWarningsAsErrors`-Parameter. |
| `WarningsNotAsErrors` | Optionaler `String`-Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die nicht als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Dieser Parameter ist nur dann nützlich, wenn der `TreatWarningsAsErrors`-Parameter auf `true` gesetzt ist. |
| `Win32Icon` | Optionaler `String`-Parameter.<br /><br /> Fügt der Assembly eine *ICO*-Datei hinzu, die der Ausgabedatei im **Datei-Explorer** das gewünschte Aussehen verleiht. Dieser Parameter entspricht der Option [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) des Compilers *vbc.exe*. |
| `Win32Resources` | Optionaler `String`-Parameter.<br /><br /> Fügt eine Win32-Ressource (*RES*-Datei) in die Ausgabedatei ein. Dieser Parameter entspricht der Option [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) des Compilers *vbc.exe*. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Beispiel

 Im folgenden Beispiel wird ein Visual Basic-Projekt kompiliert.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>Siehe auch

- [Visual Basic command-line compiler (Visual Basic-Befehlszeilencompiler)](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
