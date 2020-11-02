---
title: CL-Aufgabe | Microsoft-Dokumentation
description: Beschreibt den Zweck und die Parameter der MSBuild-CL-Aufgabe, die das Microsoft C++-Compilertool (cl.exe) umschließt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d930ed8d918a08503a6eaa6b60848abeec7683a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796835"
---
# <a name="cl-task"></a>CL-Aufgabe

Umschließt das Microsoft C++-Compilertool ( *cl.exe* ). Der Compiler generiert ausführbare Dateien ( *EXE* ), Dynamic-Link Library-Dateien ( *DLL* ) oder Codemoduldateien ( *NETMODULE* ). Weitere Informationen finden Sie unter [Compileroptionen](/cpp/build/reference/compiler-options), [Verwenden von MSBuild über die Befehlszeile](/cpp/build/msbuild-visual-cpp) und [Verwenden des Microsoft C++-Toolsets über die Befehlszeile](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parameter

 Im Folgenden werden die Parameter der **CL** -Aufgabe beschrieben. Die meisten Aufgabenparameter und einige Parametersätze entsprechen einer Befehlszeilenoption.

- **AdditionalIncludeDirectories**

   Optionaler String[]-Parameter.

   Fügt ein Verzeichnis zur Liste der Verzeichnisse hinzu, die nach Includedateien durchsucht werden.

   Weitere Informationen finden Sie unter [/I (Zusätzliche Includeverzeichnisse)](/cpp/build/reference/i-additional-include-directories).

- **AdditionalOptions**

   Optionaler String-Parameter.

   Eine Liste von Befehlszeilenoptionen. Beispiel: „/\<option1> /\<option2> /\<option#>“. Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht durch einen anderen Aufgabenparameter dargestellt werden.

   Weitere Informationen finden Sie unter [Compileroptionen](/cpp/build/reference/compiler-options).

- **AdditionalUsingDirectories**

   Optionaler String[]-Parameter.

   Gibt ein Verzeichnis an, das der Compiler durchsucht, um Dateiverweise aufzulösen, die an die **#using** -Anweisung übergeben wurden.

   Weitere Informationen finden Sie unter [/AI (Metadatenverzeichnisse festlegen)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   Optionaler String-Parameter.

   Eine Zeichenfolge, die immer in der Befehlszeile ausgegeben wird. Ihr Standardwert ist „ **/c** “.

- **AssemblerListingLocation**

   Erstellt eine Listendatei, die Assemblycode enthält.

   Weitere Informationen finden Sie unter der Option **/Fa** in [/FA, /Fa (Listingdatei)](/cpp/build/reference/fa-fa-listing-file).

- **AssemblerOutput**

   Optionaler String-Parameter.

   Erstellt eine Listendatei, die Assemblycode enthält.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **NoListing** -  *\<none>*

  - **AssemblyCode** -  **/FA**

  - **AssemblyAndMachineCode** -  **/FAc**

  - **AssemblyAndSourceCode** -  **/FAs**

  - **All** -  **/FAcs**

    Weitere Informationen finden Sie unter den Optionen **/FA** , **/FAc** , **/FAs** und **/FAcs** in [/FA, /Fa (Listingdatei)](/cpp/build/reference/fa-fa-listing-file).

- **BasicRuntimeChecks**

   Optionaler String-Parameter.

   Aktiviert und deaktiviert die Funktion für Laufzeitfehlerüberprüfungen in Verbindung mit dem [runtime_checks](/cpp/preprocessor/runtime-checks)-Pragma.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Default** -                           *\<none>*

  - **StackFrameRuntimeCheck** -  **/RTCs**

  - **UninitializedLocalUsageCheck** -  **/RTCu**

  - **EnableFastChecks** -                           **/RTC1**

    Weitere Informationen finden Sie unter [/RTC (Laufzeitfehlerüberprüfungen)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   Optionaler boolescher Parameter.

   Bei `true` wird eine Browseinformationsdatei erstellt.

   Weitere Informationen finden Sie unter der Option **/FR** in [/FR, /Fr (SBR-Datei erstellen)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BrowseInformationFile**

   Optionaler String-Parameter.

   Gibt einen Dateinamen für die Browseinformationsdatei an.

   Weitere Informationen finden Sie unter dem Parameter **BrowseInformation** in dieser Tabelle und unter [/FR, /Fr (SBR-Datei erstellen)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BufferSecurityCheck**

   Optionaler boolescher Parameter.

   Bei `true` werden einige Pufferüberläufe erkannt, die die Rückgabeadresse überschreiben – ein gängiges Verfahren zur Nutzung von Code, der keine Puffergrößeneinschränkungen erzwingt.

   Weitere Informationen finden Sie unter [/GS (Puffer-Sicherheitsüberprüfung)](/cpp/build/reference/gs-buffer-security-check).

- **BuildingInIDE**

   Optionaler boolescher Parameter.

   Zeigt bei `true` an, dass **MSBuild** von der IDE aufgerufen wird. Andernfalls wird **MSBuild** in der Befehlszeile aufgerufen.

- **CallingConvention**

   Optionaler String-Parameter.

   Gibt die Aufrufkonvention an, mit der festgelegt wird, in welcher Reihenfolge die Funktionsargumente auf den Stapel verschoben werden, ob die aufrufende oder die aufgerufene Funktion die Argumente am Ende des Aufrufs aus dem Stapel entfernt, und welche Namensergänzungskonvention der Compiler zur Erkennung einzelner Funktionen verwendet.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Cdecl** -  **/Gd**

  - **FastCall** -                           **/Gr**

  - **StdCall** -                           **/Gz**

    Weitere Informationen finden Sie unter [/Gd, /Gr, /Gv, /Gz (Aufrufkonvention)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **CompileAs**

   Optionaler String-Parameter.

   Gibt an, ob die Eingabedatei als C- oder C++-Quelldatei kompiliert wird.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Default** -  *\<none>*

  - **CompileAsC** -  **/TC**

  - **CompileAsCpp** -  **/TP**

    Weitere Informationen finden Sie unter [/Tc, /Tp, /TC, /TP (Typ der Quelldatei angeben)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   Optionaler String-Parameter.

   Ermöglicht Anwendungen und Komponenten, Funktionen aus der Common Language Runtime (CLR) zu verwenden.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **false** -  *\<none>*

  - **true** -  **/clr**

  - **Pure** -  **/clr:pure**

  - **Safe** -  **/clr:safe**

  - **OldSyntax** -  **/clr:oldSyntax**

    Weitere Informationen finden Sie unter [/clr (Common Language Runtime-Kompilierung)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   Optionaler boolescher Parameter.

   Bei `true` wird der Compiler angewiesen, ein Abbild für *Hotpatching* vorzubereiten. Durch diesen Parameter wird sichergestellt, dass die erste Anweisung jeder Funktion mindestens über die für das Hotpatching erforderliche Größe von zwei Bytes verfügt.

   Weitere Informationen finden Sie unter [/hotpatch (Hotpatchfähiges Image erstellen)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   Optionaler String-Parameter.

   Wählt den Typ der Debuginformationen aus, der für Ihr Programm erstellt wird, und ob diese Informationen in Objektdateien ( *OBJ* ) oder in einer Programmdatenbank (PDB) gespeichert werden sollen.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **OldStyle** -  **/Z7**

  - **ProgramDatabase** -  **/Zi**

  - **EditAndContinue** -  **/ZI**

    Weitere Informationen finden Sie unter [/Z7, /Zi, /ZI (Debuginformationsformat)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   Optionaler boolescher Parameter.

   Bei **TRUE** wird der Compiler angewiesen, einen Fehler für Sprachkonstrukte auszugeben, die weder mit ANSI C noch mit ANSI C++ kompatibel sind.

   Weitere Informationen finden Sie unter der Option **/Za** in [/Za, /Ze (Spracherweiterungen deaktivieren)](/cpp/build/reference/za-ze-disable-language-extensions).

- **DisableSpecificWarnings**

   Optionaler String[]-Parameter.

   Deaktiviert die Warnzahlen, die in einer durch Semikolons getrennten Liste angegeben werden.

   Weitere Informationen finden Sie unter der Option `/wd` in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Warnstufe)](/cpp/build/reference/compiler-option-warning-level).

- **EnableEnhancedInstructionSet**

   Optionaler String-Parameter.

   Gibt die Architektur für die Codegenerierung an, die Streaming SIMD Extensions (SSE)- und Streaming SIMD Extensions 2 (SSE2)-Anweisungen enthält.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **StreamingSIMDExtensions** -  **/arch:SSE**

  - **StreamingSIMDExtensions2** -  **/arch:SSE2**

    Weitere Informationen finden Sie unter [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   Optionaler boolescher Parameter.

   Bei `true` wird Fiber-Sicherheit für Daten unterstützt, die mit statischem lokalen Threadspeicher zugewiesen werden, d.h. mit `__declspec(thread)` zugewiesene Daten.

   Weitere Informationen finden Sie unter [/GT (Fiber-sicheren lokalen Thread-Speicher unterstützen)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   Optionaler boolescher Parameter.

   Bei `true` wird die Codeanalyse aktiviert.

   Weitere Informationen finden Sie unter [/analyze (Codeanalyse)](/cpp/build/reference/analyze-code-analysis).

- **ErrorReporting**

   Optionaler String-Parameter.

   Ermöglicht es Ihnen, Informationen über interne Compilerfehler (ICE) direkt an Microsoft zu senden. Standardmäßig lautet die Einstellung in IDE-Builds **Prompt** und in Befehlszeilenbuilds **Queue** .

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **None** -  **/errorReport:none**

  - **Prompt** -  **/errorReport:prompt**

  - **Queue** -  **/errorReport:queue**

  - **Send** -  **/errorReport:send**

    Weitere Informationen finden Sie unter [/errorReport (Interne Compilerfehler melden)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   Optionaler String-Parameter.

   Gibt das Ausnahmebehandlungsmodell an, das vom Compiler verwendet wird.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **false** -  *\<none>*

  - **Async** -  **/EHa**

  - **Sync** -  **/EHsc**

  - **SyncCThrow** -  **/EHs**

    Weitere Informationen finden Sie unter [/EH (Ausnahmebehandlungsmodell)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   Optionaler boolescher Parameter.

   Bei `true` wird eine Listendatei mit erweiterten Attributen erstellt, die in die Quelldatei eingefügt wird.

   Weitere Informationen finden Sie unter [/Fx (Eingefügten Code zusammenführen)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   Optionaler String-Parameter.

   Gibt an, ob Codegröße oder Codegeschwindigkeit bevorzugt wird.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Neither** -  *\<none>*

  - **Size** -  **/Os**

  - **Speed** -  **/Ot**

    Weitere Informationen finden Sie unter [/Os, /Ot (Kompakten Code bevorzugen, schnellen Code bevorzugen)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   Optionaler boolescher Parameter.

   Bei `true` wird das verlässliche Modell für Gleitkommaausnahmen aktiviert. Ausnahmen werden sofort ausgelöst, wenn sie auftreten.

   Weitere Informationen finden Sie unter der Option / **fp:except** in [/fp (Gleitkommaverhalten festlegen)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **FloatingPointModel**

   Optionaler String-Parameter.

   Legt das Gleitkommamodell fest.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Precise** -  **/fp:precise**

  - **Strict** -  **/fp:strict**

  - **Fast** -  **/fp:fast**

    Weitere Informationen finden Sie unter [/fp (Gleitkommaverhalten festlegen)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceInForLoopScope**

   Optionaler boolescher Parameter.

   Bei `true` wird Standard-C++-Verhalten in [for](/cpp/cpp/for-statement-cpp)-Schleifen implementiert, die Microsoft-Erweiterungen ([/Ze](/cpp/build/reference/za-ze-disable-language-extensions)) verwenden.

   Weitere Informationen finden Sie unter [/Zc:forScope (Übereinstimmung in for-Schleifenbereich erzwingen)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   Optionaler `String[]`-Parameter.

   Weist den Präprozessor an, eine oder mehrere angegebene Headerdateien zu verarbeiten.

   Weitere Informationen finden Sie unter [/FI (Name der expliziten Includedatei)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   Optionaler **String[]** -Parameter.

   Weist den Präprozessor an, eine oder mehrere angegebene **#using** -Datei zu verarbeiten.

   Weitere Informationen finden Sie unter [/FU (Name der expliziten #using-Datei)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird dem Compiler ermöglicht, einzelne Funktionen in Form von kompilierten Funktionen (COMDATs) zu kompilieren.

   Weitere Informationen finden Sie unter [/Gy (Funktionslevel-Linking aktivieren)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   Optionaler `Boolean`-Parameter.

   Bei `true` werden vom Compiler Dokumentationskommentare in Quellcodedateien verarbeitet, und für jede derartige Quellcodedatei mit Dokumentationskommentaren wird eine *XDC* -Datei erstellt.

   Weitere Informationen finden Sie unter [/doc (Dokumentationskommentare verarbeiten) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Siehe auch den Parameter **XMLDocumentationFileName** in dieser Tabelle.

- **IgnoreStandardIncludePath**

   Optionaler `Boolean`-Parameter.

   Hindert bei `true` den Compiler daran, in den Verzeichnissen, die in den Umgebungsvariablen PATH und INCLUDE angegeben sind, nach Includedateien zu suchen.

   Weitere Informationen finden Sie unter [/X (Standardincludepfade ignorieren)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   Optionaler **String** -Parameter.

   Gibt die Ebene der Inlinefunktionserweiterung für den Build an.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Default** -  *\<none>*

  - **Disabled** -  **/Ob0**

  - **OnlyExplicitInline** -  **/Ob1**

  - **AnySuitable** -  **/Ob2**

    Weitere Informationen finden Sie unter [/Ob (Inlinefunktionserweiterung)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   Optionaler `Boolean`-Parameter.

   Bei `true` werden einige Funktionsaufrufe durch systeminterne oder sonstige spezielle Formen der Funktion ersetzt, die dazu beitragen, dass die Arbeitsgeschwindigkeit der Anwendung erhöht wird.

   Weitere Informationen finden Sie unter [/Oi (Systeminterne Funktionen erstellen)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird die Mindestneuerstellung aktiviert, die bestimmt, ob C++-Quelldateien, die geänderte C++-Klassendefinitionen enthalten (die in Headerdateien (H) gespeichert sind), neu kompiliert werden müssen.

   Weitere Informationen finden Sie unter [/Gm (Minimale Neuerstellung aktivieren)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **MultiProcessorCompilation**

   Optionaler `Boolean`-Parameter.

   Bei `true` werden mehrere Prozessoren für das Kompilieren verwendet. Dieser Parameter erstellt einen Prozess für jeden effektiven Prozessor auf dem Computer.

   Weitere Informationen finden Sie unter [/MP (Erstellen mit mehreren Prozessen)](/cpp/build/reference/mp-build-with-multiple-processes). Siehe auch den Parameter **ProcessorNumber** in dieser Tabelle.

- **ObjectFileName**

   Optionaler **String** -Parameter.

   Gibt einen Namen für die Objektdatei (OBJ) oder das Verzeichnis an, der anstelle des Standardwerts verwendet werden soll.

   Weitere Informationen finden Sie unter [/Fo (Name der Objektdatei)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   Optionaler **String[]** -Parameter.

   Eine Liste von Objektdateien.

- **OmitDefaultLibName**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird der Name der Standard-C-Laufzeitbibliothek in der Objektdatei ( *OBJ* ) weggelassen. Standardmäßig legt der Compiler den Namen der Bibliothek in der *OBJ* -Datei ab, um den Linker zur richtigen Bibliothek zu leiten.

   Weitere Informationen finden Sie unter [/Zl (Kein Standardbibliotheksname)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird die Erstellung von Framezeigern in der Anrufliste unterdrückt.

   Weitere Informationen finden Sie unter [/Oy (Framezeiger unterdrücken)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   Optionaler `Boolean`-Parameter.

   Bei `true` verarbeitet der Compiler OpenMP-Klauseln und -Direktiven.

   Weitere Informationen finden Sie unter [/openmp (OpenMP 2.0-Unterstützung aktivieren)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **Optimization**

   Optionaler **String** -Parameter.

   Gibt die verschiedenen Codeoptimierungen für Geschwindigkeit und Größe an.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Disabled** -  **/Od**

  - **MinSpace** -  **/O1**

  - **MaxSpeed** -  **/O2**

  - **Full** -  **/Ox**

    Weitere Informationen finden Sie unter [/O-Optionen (Code optimieren)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   Optionaler **String** -Parameter.

   Erstellt oder verwendet eine vorkompilierte Headerdatei ( *PCH* ) während des Builds.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **NotUsing** -  *\<none>*

  - **Create** -  **/Yc**

  - **Use** -  **/Yu**

    Weitere Informationen finden Sie unter [/Yc (Vorkompilierte Headerdatei erstellen)](/cpp/build/reference/yc-create-precompiled-header-file) und [/Yu (vorkompilierte Headerdatei verwenden)](/cpp/build/reference/yu-use-precompiled-header-file). Siehe auch die Parameter **PrecompiledHeaderFile** und **PrecompiledHeaderOutputFile** in dieser Tabelle.

- **PrecompiledHeaderFile**

   Optionaler **String** -Parameter.

   Gibt den Namen einer vorkompilierten Headerdatei an, die erstellt oder verwendet werden soll.

   Weitere Informationen finden Sie unter [/Yc (Vorkompilierte Headerdatei erstellen)](/cpp/build/reference/yc-create-precompiled-header-file) und [/Yu (vorkompilierte Headerdatei verwenden)](/cpp/build/reference/yu-use-precompiled-header-file).

- **PrecompiledHeaderOutputFile**

   Optionaler **String** -Parameter.

   Gibt einen Pfadnamen für einen vorkompilierten Header an, der anstelle des Standardpfadnamens verwendet wird.

   Weitere Informationen finden Sie unter [/Fp (Name der PCH-Datei)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments**

   Optionaler `Boolean`-Parameter.

   Bei `true` werden Kommentare bei der Vorverarbeitung beibehalten.

   Weitere Informationen finden Sie unter [/C (Kommentare bei der Vorverarbeitung beibehalten)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **PreprocessorDefinitions**

   Optionaler `String[]`-Parameter.

   Definiert ein Präprozessorsymbol für Ihre Quelldatei.

   Weitere Informationen finden Sie unter [/D (Präprozessordefinitionen)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   Optionaler `ITaskItem[]`-Parameter.

   Definiert ein Array von Präprozessorausgabeelementen, die verbraucht und von Aufgaben ausgegeben werden können.

- **PreprocessOutputPath**

   Optionaler `String`-Parameter.

   Gibt den Namen der Ausgabedatei an, in die der **PreprocessToFile** -Parameter die vorverarbeitete Ausgabe schreibt.

   Weitere Informationen finden Sie unter [/Fi (Ausgabedateinamen vorverarbeiten)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   Optionaler `Boolean`-Parameter.

   Bei `true` werden C- und C++-Quelldateien vorverarbeitet, und die vorverarbeiteten Dateien werden auf das Standardausgabegerät kopiert.

   Weitere Informationen finden Sie unter [/EP (Vorverarbeitung an „stdout“ ohne #line-Direktiven)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   Optionaler `Boolean`-Parameter.

   Bei `true` werden C- und C++-Quelldateien vorverarbeitet, und die vorverarbeitete Ausgabe wird in eine Datei geschrieben.

   Weitere Informationen finden Sie unter [/P (Vorverarbeitung in eine Datei)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   Optionaler `Integer`-Parameter.

   Gibt die maximale Anzahl von Prozessoren an, die in einer Kompilierung mit mehreren Prozessoren verwendet werden. Verwenden Sie diesen Parameter in Kombination mit dem Parameter **MultiProcessorCompilation** .

- **ProgramDataBaseFileName**

   Optionaler `String`-Parameter.

   Gibt einen Dateinamen für die Programmdatenbankdatei (PDB) an.

   Weitere Informationen finden Sie unter [/Fd (Programmdatenbank-Dateiname)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   Optionaler `String`-Parameter.

   Zeigt an, ob es sich bei einem Multithread-Modul um eine DLL handelt, und wählt Veröffentlichungs- oder Debugversionen der Laufzeitbibliothek aus.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **MultiThreaded** -  **/MT**

  - **MultiThreadedDebug** -  **/MTd**

  - **MultiThreadedDLL** -  **/MD**

  - **MultiThreadedDebugDLL** -  **/MDd**

    Weitere Informationen finden Sie unter [/MD, /MT, /LD (Laufzeitbibliothek verwenden)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird Code hinzugefügt, um C++-Objekttypen während der Laufzeit zu überprüfen (Laufzeit-Typeninformationen).

   Weitere Informationen finden Sie unter [/GR (Laufzeittypinformation aktivieren)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes**

   Optionaler `Boolean`-Parameter.

   Bei `true` gibt der Compiler eine Liste der Includedateien aus.

   Weitere Informationen finden Sie unter [/showIncludes (Includedateien auflisten)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird ein Laufzeitfehler gemeldet, wenn ein Wert einem kleineren Datentyp zugewiesen wird und dies einen Datenverlust verursacht.

   Weitere Informationen finden Sie unter der Option **/RTCc** in [/RTC (Laufzeitfehlerüberprüfungen)](/cpp/build/reference/rtc-run-time-error-checks).

- **Sources**

   Erforderlicher `ITaskItem[]`-Parameter.

   Gibt eine durch Leerzeichen getrennte Liste der Quelldateien an.

- **StringPooling**

   Optionaler `Boolean`-Parameter.

   Bei `true` kann der Compiler eine Kopie identischer Zeichenfolgen im Programmabbild erstellen.

   Weitere Informationen finden Sie unter [/GF (Doppelte Zeichenfolgen beseitigen)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   Optionaler `String`-Parameter.

   Gibt die Byte-Ausrichtung für alle Member in einer Struktur an.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Default** -  **/Zp1**

  - **1Byte** -  **/Zp1**

  - **2Bytes** -  **/Zp2**

  - **4Bytes** -  **/Zp4**

  - **8Bytes** -  **/Zp8**

  - **16Bytes** -  **/Zp16**

    Weitere Informationen finden Sie unter [/Zp (Ausrichten des Strukturmembers)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.

   Weitere Informationen finden Sie unter [/nologo (Startbanner unterdrücken) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   Optionaler `String`-Parameter.

   Gibt das Zwischenverzeichnis an, in dem die Nachverfolgungsprotokolle für diese Aufgabe gespeichert sind.

   Weitere Informationen finden Sie unter den Parametern **TLogReadFiles** und **TLogWriteFiles** in dieser Tabelle.

- **TreatSpecificWarningsAsErrors**

   Optionaler **String[]** -Parameter.

   Behandelt die angegebene Liste von Compilerwarnungen als Fehler.

   Weitere Informationen finden Sie unter der Option **/we**`n` in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Warnstufe)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   Optionaler `Boolean`-Parameter.

   Bei `true` werden alle Compilerwarnungen als Fehler behandelt.

   Weitere Informationen finden Sie unter der Option **/WX** in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Warnstufe)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird der `wchar_t`-Typ als nativer Typ behandelt.

   Weitere Informationen finden Sie unter[/Zc:wchar_t (wchar_t ist der native Typ)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird die Definition der Microsoft-spezifischen Symbole aufgehoben, die der Compiler definiert.

   Weitere Informationen finden Sie unter der Option **/u** in [/U, /u (Symboldefinitionen aufheben)](/cpp/build/reference/u-u-undefine-symbols).

- **UndefinePreprocessorDefinitions**

   Optionaler `String[]`-Parameter.

   Gibt eine Liste mit einem oder mehreren Präprozessorsymbolen an, deren Definition aufgehoben werden soll.

   Weitere Informationen finden Sie unter der Option **/U** in [/U, /u (Symboldefinitionen aufheben)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird der vollständige Pfad der Quellcodedateien angezeigt, die in der Diagnostik an den Compiler übergeben werden.

   Weitere Informationen finden Sie unter [/FC (Vollständiger Pfad der Quellcodedatei in Diagnostik)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird die Ausgabedatei im UTF-8-Format erstellt.

   Weitere Informationen finden Sie unter der Option **/FAu** in [/FA, /Fa (Listingdatei)](/cpp/build/reference/fa-fa-listing-file).

- **WarningLevel**

   Optionaler `String`-Parameter.

   Gibt die höchste Warnstufe an, die vom Compiler generiert werden soll.

   Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **TurnOffAllWarnings** -  **/W0**

  - **Level1** -  **/W1**

  - **Level2** -  **/W2**

  - **Level3** -  **/W3**

  - **Level4** -  **/W4**

  - **EnableAllWarnings** -  **/Wall**

    Weitere Informationen finden Sie unter der Option **/W**_n_ in [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Warnstufe)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird die Optimierung des ganzen Programms aktiviert.

   Weitere Informationen finden Sie unter [/GL (Optimierung des ganzen Programms)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   Optionaler `String`-Parameter.

   Gibt den Namen der generierten XML-Dokumentationsdateien an. Bei diesem Parameter kann es sich um einen Datei- oder Verzeichnisnamen handeln.

   Weitere Informationen finden Sie unter dem `name`-Argument in [/doc (Dokumentationskommentare verarbeiten) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Beachten Sie auch den Parameter **GenerateXMLDocumentationFiles** in dieser Tabelle.

- **MinimalRebuildFromTracking**

   Optionaler `Boolean`-Parameter.

   Bei `true` wird ein nachverfolgter inkrementeller Build ausgeführt; bei `false` erfolgt eine Neuerstellung.

- **TLogReadFiles**

   Optionaler `ITaskItem[]`-Parameter.

   Gibt ein Array von Elementen an, die die *Read-Datei-Nachverfolgungsprotokolle* darstellen.

   Ein Read-Datei-Nachverfolgungsprotokoll ( *TLOG* ) enthält die Namen der Eingabedateien, die von einer Aufgabe gelesen und vom Projektbuildsystem verwendet werden, um inkrementelle Builds zu unterstützen. Weitere Informationen finden Sie unter den Parametern **TrackerLogDirectory** und **TrackFileAccess** in dieser Tabelle.

- **TLogWriteFiles**

   Optionaler `ITaskItem[]`-Parameter.

   Gibt ein Array von Elementen an, die die *Write-Datei-Nachverfolgungsprotokolle* darstellen.

   Ein Write-Datei-Nachverfolgungsprotokoll ( *TLOG* ) enthält die Namen der Ausgabedateien, die von einer Aufgabe geschrieben und vom Projektbuildsystem verwendet werden, um inkrementelle Builds zu unterstützen. Weitere Informationen finden Sie unter den Parametern **TrackerLogDirectory** und **TrackFileAccess** in dieser Tabelle.

- **TrackFileAccess**

   Optionaler `Boolean`-Parameter.

   Bei `true` werden Dateizugriffsmuster nachverfolgt.

   Weitere Informationen finden Sie unter den Parametern **TLogReadFiles** und **TLogWriteFiles** in dieser Tabelle.

## <a name="see-also"></a>Siehe auch

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
