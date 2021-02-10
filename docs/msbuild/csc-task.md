---
title: Csc-Aufgabe | Microsoft-Dokumentation
description: In diesem Artikel wird die MSBuild-Csc-Aufgabe beschrieben, die den C#-Compiler (csc.exe) umschließt und EXE-, DLL- oder NETMODULE-Dateien erzeugt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a3787d5aa21e029ab4900bdd89c88f1cc60f3489
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901340"
---
# <a name="csc-task"></a>Csc-Aufgabe

Umschließt *csc.exe* und erzeugt ausführbare Dateien (*EXE*-Dateien), Dynamic Link Libraries (*DLL*-Dateien) und Codemodule (*NETMODULE*-Dateien). Weitere Informationen zu *csc.exe* finden Sie unter [C#-Compileroptionen](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der `Csc` -Aufgabe beschrieben.

| Parameter | Beschreibung |
|------------------------------| - |
| `AdditionalLibPaths` | Optionaler `String[]`-Parameter.<br /><br /> Gibt zusätzliche Verzeichnisse an, in denen nach Verweisen gesucht wird. Weitere Informationen finden Sie unter [-lib (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Optionaler `String`-Parameter.<br /><br /> Gibt mindestens Modul an, das Bestandteil dieser Assembly sein soll. Weitere Informationen finden Sie unter [-addmodule (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Optionaler `Boolean`-Parameter.<br /><br /> Ist der Wert `true`, wird Code kompiliert, der das[unsafe](/dotnet/csharp/language-reference/keywords/unsafe)-Schlüsselwort verwendet. Weitere Informationen finden Sie unter [-unsafe (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Optionaler `String`-Parameter.<br /><br /> Gibt die Anwendungskonfigurationsdatei mit den Assemblybindungseinstellungen an. |
| `BaseAddress` | Optionaler `String`-Parameter.<br /><br /> Gibt die bevorzugte Basisadresse an, unter der eine DLL geladen werden soll. Die Standard-Basisadresse für eine DLL-Datei wird durch die Common Language Runtime von .NET Framework festgelegt. Weitere Informationen finden Sie unter [-baseaddress (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Optionaler `Boolean`-Parameter.<br /><br /> Gibt an, ob Ganzzahlarithmetik, die die Grenzen des Datentyps überschreitet, zur Laufzeit eine Ausnahme auslöst. Weitere Informationen finden Sie unter [-checked (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Optionaler `Int32`-Parameter.<br /><br /> Gibt die für alle Quellcodedateien in der Kompilierung die zu verwendende Codepage an. Weitere Informationen finden Sie unter [-codepage (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Optionaler `String`-Parameter.<br /><br /> Gibt den Debugtyp an. `DebugType` kann `full` oder `pdbonly` sein. Die Standardeinstellung ist `full`. Dadurch kann ein Debugger einem aktiven Programm zugeordnet werden kann. Durch das Angeben von `pdbonly` ist ein Debuggen von Quellcode möglich, wenn das Programm im Debugger gestartet wird. Der Assembler wird jedoch nur angezeigt, wenn das aktive Programm an den Debugger angefügt ist.<br /><br /> Dieser Parameter überschreibt den `EmitDebugInformation`-Parameter.<br /><br /> Weitere Informationen finden Sie unter [-debug (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Optionaler `String`-Parameter.<br /><br /> Definiert Präprozessorsymbole. Weitere Informationen finden Sie unter [-define (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Optionaler `Boolean`-Parameter.<br /><br /> Ist der Wert `true`, gibt dies an, dass Sie nur den öffentlichen Schlüssel in die Assembly platzieren möchten. Ist der Wert `false`, gibt dies an, dass die Assembly vollständig signiert werden soll.<br /><br /> Dieser Parameter hat nur dann Auswirkungen, wenn Sie ihn entweder mit dem `KeyFile`- oder `KeyContainer`-Parameter verwenden.<br /><br /> Weitere Informationen finden Sie unter [-delaysign (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Optionaler `Boolean`-Parameter.<br/><br/> Wenn dieser auf `true` festgelegt ist, gibt der Compiler eine Assembly aus, deren Inhalt im Binärformat über Kompilierungen identisch ist, wenn die Eingaben identisch sind.<br/><br/>Weitere Informationen finden Sie unter [-deterministic (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Optionaler `String`-Parameter.<br /><br /> Gibt die Liste der zu deaktivierenden Warnungen an. Weitere Informationen finden Sie unter [-nowarn (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Optionaler `String`-Parameter.<br /><br /> Verarbeitet Dokumentationskommentare zu einer XML-Datei. Weitere Informationen finden Sie unter [-doc (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Optionaler `Boolean`-Parameter.<br /><br /> Ist der Wert `true`, generiert die Aufgabe Debuginformationen und platziert sie in einer Programmdatenbankdatei (PDB-Datei). Ist der Wert `false`, erzeugt die Aufgabe keine Debuginformationen. Der Standardwert ist `false`. Weitere Informationen finden Sie unter [-debug (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Optionaler `String`-Parameter.<br /><br /> Bietet eine einfache Möglichkeit, einen internen C#-Fehler an Microsoft zu melden. Dieser Parameter kann den Wert `prompt`, `send` oder `none` haben. Wenn der Parameter auf `prompt` festgelegt ist, erhalten Sie eine Aufforderung, wenn ein interner Compilerfehler auftritt. Mithilfe der Aufforderung können Sie einen Fehlerbericht elektronisch an Microsoft senden. Wenn der Parameter auf `send` festgelegt ist, wird automatisch ein Problembericht gesendet. Wenn der Parameter auf `none` festgelegt ist, wird der Fehler nur in der Textausgabe des Compilers gemeldet. Der Standardwert ist `none`. Weitere Informationen finden Sie unter [-errorreport (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Optionaler `Int32`-Parameter.<br /><br /> Gibt die Größe der Abschnitte in der Ausgabedatei an. Weitere Informationen finden Sie unter [-filealign (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Optionaler `Boolean`-Parameter.<br /><br /> Ist der Wert `true`, wird der absolute Pfad zur Datei in der Compilerausgabe angegeben. Ist der Wert `false`, wird der Dateiname angegeben. Der Standardwert ist `false`. Weitere Informationen finden Sie unter [-fullpaths (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Optionaler `String`-Parameter.<br /><br /> Gibt den Namen des kryptografischen Schlüsselcontainers an. Weitere Informationen finden Sie unter [-keycontainer (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Optionaler `String`-Parameter.<br /><br /> Gibt den Dateinamen mit dem kryptografischen Schlüssel an. Weitere Informationen finden Sie unter [-keyfile (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Optionaler `String`-Parameter.<br /><br /> Gibt die Version der zu verwendenden Sprache an. Weitere Informationen finden Sie unter [-langversion (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Erstellt einen Link zu einer .NET Framework-Ressource in der Ausgabedatei. Die Ressourcendatei wird nicht in der Ausgabedatei platziert.<br /><br /> Elemente, die an diesen Parameter übergeben werden, können optionale Metadateneinträge mit dem Namen `LogicalName` und `Access` enthalten. `LogicalName` entspricht dem `identifier`-Parameter des `/linkresource`-Switches, und `Access` entspricht dem `accessibility-modifier`-Parameter. Weitere Informationen finden Sie unter [-linkresource (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Optionaler `String`-Parameter.<br /><br /> Gibt den Speicherort der `Main`-Methode an. Weitere Informationen finden Sie unter [-main (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Optionaler `String`-Parameter.<br /><br /> Gibt den Namen der Assembly an, zu der dieses Modul gehört. |
| `NoConfig` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Compiler angewiesen, nicht mit der Datei *csc.rsp* zu kompilieren. Weitere Informationen finden Sie unter [-noconfig (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden die Compilerbannerinformationen unterdrückt. Weitere Informationen finden Sie unter [-nologo (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, wird der Import der Datei *mscorlib.dll* verhindert, die den gesamten Systemnamespace definiert. Verwenden Sie diesen Parameter, wenn Sie Ihren eigenen Systemnamespace und die entsprechenden Objekte definieren oder erstellen möchten. Weitere Informationen finden Sie unter [-nostdlib (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, schließen Sie das Win32-Standardmanifest nicht ein. |
| `Optimize` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn der Wert `true` ist, werden Optimierungen aktiviert. Wenn der Wert `false` ist, werden Optimierungen deaktiviert. Weitere Informationen finden Sie unter [-optimize (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt den Namen der Ausgabedatei an. Weitere Informationen finden Sie unter [-out (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Optionaler `String`-Parameter.<br /><br /> Gibt den Namen der ausgegebenen Referenzassemblydatei an. Weitere Informationen finden Sie unter [-refout (C# Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Optionaler `String`-Parameter.<br /><br /> Gibt den Dateinamen der Debuginformationen an. Der Standardname ist der Ausgabedateiname mit einer *PDB*-Erweiterung. |
| `Platform` | Optionaler `String`-Parameter.<br /><br /> Gibt die Prozessorplattform an, die das Ziel der Ausgabedatei darstellen soll. Dieser Parameter kann den Wert `x86`, `x64` oder `anycpu` haben. Der Standardwert ist `anycpu`. Weitere Informationen finden Sie unter [-platform (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Bewirkt, dass die Aufgabe öffentliche Typinformationen aus den angegebenen Elementen in das aktuelle Projekt importiert. Weitere Informationen finden Sie unter [-reference (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Sie können einen C#-Verweisalias in einer MSBuild-Datei angeben, indem Sie die Metadaten `Aliases` zum ursprünglichen „Verweis“-Element hinzufügen. Angenommen, Sie möchten den Alias „LS1“ in der folgenden CSC-Befehlszeile festlegen:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> In diesem Fall verwenden Sie:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Bettet eine .NET Framework-Ressource in die Ausgabedatei ein.<br /><br /> Elemente, die an diesen Parameter übergeben werden, können optionale Metadateneinträge mit dem Namen `LogicalName` und `Access` enthalten. `LogicalName` entspricht dem `identifier`-Parameter des `/resource`-Switches, und `Access` entspricht dem `accessibility-modifier`-Parameter. Weitere Informationen finden Sie unter [-resource (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Optionaler `String`-Parameter.<br /><br /> Gibt die Antwortdatei an, die Befehle für den die Aufgabe enthalten. Weitere Informationen finden Sie unter [@ (Antwortdatei festlegen)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt mindestens eine C#-Quelldatei an. |
| `TargetType` | Optionaler `String`-Parameter.<br /><br /> Gibt das Dateiformat der Ausgabedatei an. Dieser Parameter kann unterschiedliche Werte aufweisen: `library` erstellt eine Codebibliothek, `exe` erstellt eine Konsolenanwendung, `module` erstellt ein Modul, und `winexe` erstellt ein Windows-Programm. Der Standardwert ist `library`. Weitere Informationen finden Sie unter [-target (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, werden alle Warnungen als Fehler behandelt. Weitere Informationen finden Sie unter[-warnaserror (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Optionaler `Boolean`-Parameter.<br /><br /> Weist die Aufgabe an, das prozessinterne Compilerobjekt (falls verfügbar) zu verwenden. Wird nur von Visual Studio verwendet. |
| `Utf8Output` | Optionaler `Boolean`-Parameter.<br /><br /> Protokolliert die Compilerausgabe mit UTF-8-Codierung. Weitere Informationen finden Sie unter [-utf8output (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Optionaler `Int32`-Parameter.<br /><br /> Gibt die vom Compiler anzuzeigende Warnstufe an. Weitere Informationen finden Sie unter [-warn (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Optionaler `String`-Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter[-warnaserror (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Dieser Parameter überschreibt den `TreatWarningsAsErrors`-Parameter. |
| `WarningsNotAsErrors` | Optionaler `String`-Parameter.<br /><br /> Gibt eine Liste mit Warnungen an, die nicht als Fehler behandelt werden sollen. Weitere Informationen finden Sie unter[-warnaserror (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Dieser Parameter ist nur dann nützlich, wenn der `TreatWarningsAsErrors`-Parameter auf `true` gesetzt ist. |
| `Win32Icon` | Optionaler `String`-Parameter.<br /><br /> Fügt der Assembly eine *ICO*-Datei hinzu, die der Ausgabedatei im **Datei-Explorer** das gewünschte Aussehen verleiht. Weitere Informationen finden Sie unter [-win32icon (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Optionaler `String`-Parameter.<br /><br /> Gibt das Win32-Manifest an, das eingeschlossen werden sollen. |
| `Win32Resource` | Optionaler `String`-Parameter.<br /><br /> Fügt eine Win32-Ressource (*RES*-Datei) in die Ausgabedatei ein. Weitere Informationen finden Sie unter [-win32res (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die `Csc`-Aufgabe verwendet, um eine ausführbare Datei aus den Quelldateien in der `Compile`-Elementauflistung zu kompilieren.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Siehe auch

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Aufgaben](../msbuild/msbuild-tasks.md)
