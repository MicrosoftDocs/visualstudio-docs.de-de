---
title: Link-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild die Link-Aufgabe verwendet, um das Microsoft C++-Linkertool „link.exe“ zu umschließen, das COFF-Objektdateien und -Bibliotheken miteinander verbindet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), Link task
- Link task (MSBuild (C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 160d4fa3a1058e0cb81e5d25720d9194d90fdc39
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904054"
---
# <a name="link-task"></a>Link-Aufgabe

Umschließt das Microsoft C++-Linkertool ( *link.exe* ). Das Linkertool ist ein Tool, das Objektdateien und Bibliotheken im COFF-Format (Common Object File Format) miteinander verbindet, um eine ausführbare Datei ( *.exe* ) oder eine DLL (Dynamic Link Library) zu erstellen. Weitere Informationen finden Sie unter [Linkeroptionen](/cpp/build/reference/linker-options), [Verwenden von MSBuild über die Befehlszeile](/cpp/build/msbuild-visual-cpp) und [Verwenden des Microsoft C++-Toolsets über die Befehlszeile](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parameter

 Im Folgenden werden die Parameter der **Link** -Aufgabe beschrieben. Die meisten Aufgabenparameter und einige Parametersätze entsprechen einer Befehlszeilenoption.

- **AdditionalDependencies**

  Optionaler **String[]** -Parameter.

  Gibt eine Liste von Eingabedateien an, die dem Befehl hinzugefügt werden sollen.

  Weitere Informationen finden Sie unter [LINK-Eingabedateien](/cpp/build/reference/link-input-files).

- **AdditionalLibraryDirectories**

  Optionaler **String[]** -Parameter.

  Überschreibt den Bibliothekspfad der Umgebung. Geben Sie einen Verzeichnisnamen an.

  Weitere Informationen finden Sie unter [/LIBPATH (Libpath-Pfad hinzufügen)](/cpp/build/reference/libpath-additional-libpath).

- **AdditionalManifestDependencies**

  Optionaler **String[]** -Parameter.

  Gibt Attribute an, die in den `dependency`-Abschnitt der Manifestdatei eingefügt werden.

  Weitere Informationen finden Sie unter [/MANIFESTDEPENDENCY (Manifestabhängigkeiten angeben)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Siehe auch [Konfigurationsdateien des Verlegers](/windows/desktop/SbsCs/publisher-configuration-files).

- **AdditionalOptions**

  Optionaler **String** -Parameter.

  Eine Liste von Linkeroptionen, wie in der Befehlszeile angegeben. Beispiel: /\<option1> /\<option2> /\<option#>. Verwenden Sie diesen Parameter, um Linkeroptionen anzugeben, die nicht durch einen anderen **Link** -Aufgabenparameter repräsentiert werden.

  Weitere Informationen finden Sie unter [Linkeroptionen](/cpp/build/reference/linker-options).

- **AddModuleNamesToAssembly**

  Optionaler **String[]** -Parameter.

  Fügt einer Assembly einen Modulverweis hinzu.

  Weitere Informationen finden Sie unter [/ASSEMBLYMODULE (MSIL-Modul zur Assembly hinzufügen)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **AllowIsolation**

  Optionaler **Boolean** -Parameter.

  `true` bewirkt, dass das Betriebssystem Manifestsuch- und -ladevorgänge durchführt. `false` gibt an, dass DLLs geladen werden, als ob es kein Manifest gäbe.

  Weitere Informationen finden Sie unter [/ALLOWISOLATION (Manifestsuche)](/cpp/build/reference/allowisolation-manifest-lookup).

- **AssemblyDebug**

  Optionaler **Boolean** -Parameter.

  `true` gibt das **DebuggableAttribute** -Attribut mit Debuginformationsnachverfolgung aus und deaktiviert die JIT-Optimierungen. Wenn `false` das **DebuggableAttribute** -Attribut ausgibt, aber Debuginformationsnachverfolgung deaktiviert und JIT-Optimierungen aktiviert.

  Weitere Informationen finden Sie unter [/ASSEMBLYDEBUG (DebuggableAttribute hinzufügen)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **AssemblyLinkResource**

  Optionaler **String[]** -Parameter.

  Erstellt einen Link zu einer .NET Framework-Ressource in der Ausgabedatei. Die Ressourcendatei wird nicht in der Ausgabedatei platziert. Geben Sie den Namen der Ressource an.

  Weitere Informationen finden Sie unter [/ASSEMBLYLINKRESOURCE (Mit .NET Framework-Ressource verknüpfen)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **AttributeFileTracking**

  Impliziter **boolescher** Parameter.

  Ermöglicht die Nachverfolgung tieferer Dateien, um das inkrementelle Verhalten des Links zu erfassen. Gibt immer `true` zurück.

- **BaseAddress**

  Optionaler **String** -Parameter.

  Legt eine Basisadresse für das Programm oder die erstellte DLL fest. Geben Sie `{address[,size] | @filename,key}`an.

  Weitere Informationen finden Sie unter [/BASE (Basisadresse)](/cpp/build/reference/base-base-address).

- **BuildingInIDE**

  Optionaler **Boolean** -Parameter.

  Zeigt bei TRUE an, dass MSBuild von der IDE aufgerufen wird. Andernfalls zeigt er an, dass MSBuild von der Befehlszeile aufgerufen wird.

  Dieser Parameter hat keine entsprechende Linkeroption.

- **CLRImageType**

  Optionaler **String** -Parameter.

  Legt den Typ eines Common Language Runtime (CLR) Images fest.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Default** -  *\<none>*

  - **ForceIJWImage** -  **/CLRIMAGETYPE:IJW**

  - **ForcePureILImage** -  **/CLRIMAGETYPE:PURE**

  - **ForceSafeILImage** -  **/CLRIMAGETYPE:SAFE**

  Weitere Informationen finden Sie unter [/CLRIMAGETYPE (CLR-Bildtyp angeben)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).

- **CLRSupportLastError**

  Optionaler **String** -Parameter.

  Behält den letzten Fehlercode von Funktionen bei, die vom P/Invoke-Mechanismus aufgerufen werden.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Aktiviert** -  **/CLRSupportLastError**

  - **Deaktiviert** -  **/CLRSupportLastError:NO**

  - **SystemDlls** -  **/CLRSupportLastError:SYSTEMDLL**

  Weitere Informationen finden Sie unter [/CLRSUPPORTLASTERROR (Letzten Fehlercode für PInvoke-Aufrufe beibehalten)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).

- **CLRThreadAttribute**

  Optionaler **String** -Parameter.

  Gibt das Threadingattribut für den Einstiegspunkt des CLR-Programms explizit an.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **DefaultThreadingAttribute** -  **/CLRTHREADATTRIBUTE:NONE**

  - **MTAThreadingAttribute** -  **/CLRTHREADATTRIBUTE:MTA**

  - **STAThreadingAttribute** -  **/CLRTHREADATTRIBUTE:STA**

  Weitere Informationen finden Sie unter [/CLRTHREADATTRIBUTE (CLR-Threadattribut festlegen)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  Optionaler **Boolean** -Parameter.

  Gibt an, ob der Linker **SuppressUnmanagedCodeSecurityAttribute** auf vom Linker generierte PInvoke-Anrufe von verwaltetem Code an nativen DLLs anwendet.

  Weitere Informationen finden Sie unter [/CLRUNMANAGEDCODECHECK (Hinzufügen von SuppressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **CreateHotPatchableImage**

  Optionaler **String** -Parameter.

  Bereitet ein Image für Hotpatching vor.

  Geben Sie einen der folgenden Werte an, der einer Linkeroption entspricht.

  - **Aktiviert** -  **/FUNCTIONPADMIN**

  - **X86Image** -  **/FUNCTIONPADMIN:5**

  - **X64Image** -  **/FUNCTIONPADMIN:6**

  - **ItaniumImage** -  **/FUNCTIONPADMIN:16**

  Weitere Informationen finden Sie unter [/FUNCTIONPADMIN (Hotpatchfähiges Image erstellen)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).

- **DataExecutionPrevention**

  Optionaler **Boolean** -Parameter.

  `true` gibt an, dass eine ausführbare Datei mit der Windows-Funktion zur Datenausführungsverhinderung kompatibel ist.

  Weitere Informationen finden Sie unter [/NXCOMPAT (kompatibel mit Datenausführungsverhinderung)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDLLs**

  Optionaler **String[]** -Parameter.

  Dieser Parameter bewirkt ein *verzögertes Laden* des DLLs. Geben Sie den Namen einer DLL an, die mit einer Verzögerung geladen werden soll.

  Weitere Informationen finden Sie unter [/DELAYLOAD (Laden von Import verzögern)](/cpp/build/reference/delayload-delay-load-import).

- **DelaySign**

  Optionaler **Boolean** -Parameter.

  `true` signiert eine Assembly teilweise. In der Standardeinstellung ist der Wert `false`.

  Weitere Informationen finden Sie unter [/DELAYSIGN (Assembly teilweise signieren)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Treiber**

  Optionaler **String** -Parameter.

  Geben Sie diesen Parameter an, um einen Windows NT-Kernelmodustreiber zu erstellen.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **NotSet** -  *\<none>*

  - **Treiber** -  **/Driver**

  - **UpOnly** -  **/DRIVER:UPONLY**

  - **WDM** -  **/DRIVER:WDM**

  Weitere Informationen finden Sie unter [/DRIVER (Treiber für den Kernelmodus von Windows NT)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).

- **EmbedManagedResourceFile**

  Optionaler **String[]** -Parameter.

  Bettet eine Ressourcendatei in eine Assembly ein. Geben Sie den Dateinamen für die angeforderte Ressource an. Geben Sie optional den logischen Namen ein, der zum Laden der Ressource verwendet wird, und die **PRIVATE** -Option, die im Assemblymanifest angibt, dass die Ressourcendatei privat ist.

  Weitere Informationen finden Sie unter [/ASSEMBLYRESOURCE (Verwaltete Ressource einbetten)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **EnableCOMDATFolding**

  Optionaler **Boolean** -Parameter.

  `true` ermöglicht eine identische COMDAT-Faltung.

  Weitere Informationen finden Sie unter dem `ICF[= iterations]`-Argument der [/OPT (Optimierungen)](/cpp/build/reference/opt-optimizations).

- **EnableUAC**

  Optionaler **Boolean** -Parameter.

  `true` gibt an, dass Informationen zur Benutzerkontensteuerung (UAC) in das Programmmanifest eingebettet werden.

  Weitere Informationen finden Sie unter [/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  Optionaler **String** -Parameter.

  Gibt eine Einstiegspunktfunktion als Startadresse für eine *EXE* -Datei oder DLL an. Geben Sie einen Funktionsnamen als Parameterwert an.

  Weitere Informationen finden Sie unter [/ENTRY (Symbol für Einstiegspunkt)](/cpp/build/reference/entry-entry-point-symbol).

- **FixedBaseAddress**

  Optionaler **Boolean** -Parameter.

  `true` erstellt ein Programm oder eine DLL, das nur an seiner bevorzugten Basisadresse geladen werden kann.

  Weitere Informationen finden Sie unter [/FIXED (Feste Basisadresse)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  Optionaler **String** -Parameter.

  Weist den Linker an, eine gültige *EXE* -Datei oder DLL auch dann zu erstellen, wenn auf ein Symbol verwiesen wird, dieses Symbol aber nicht oder mehrmals definiert wurde.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Aktiviert** -  **/FORCE**

  - **MultiplyDefinedSymbolOnly** -  **/FORCE:MULTIPLE**

  - **UndefinedSymbolOnly** -  **/FORCE:UNRESOLVED**

  Weitere Informationen finden Sie unter [//FORCE (Dateiausgabe erzwingen)](/cpp/build/reference/force-force-file-output).

- **ForceSymbolReferences**

  Optionaler **String[]** -Parameter.

  Dieser Parameter weist den Linker an, der Symboltabelle ein bestimmtes Symbol hinzuzufügen.

  Weitere Informationen finden Sie unter [/INCLUDE (Symbolverweise erzwingen)](/cpp/build/reference/include-force-symbol-references).

- **FunctionOrder**

  Optionaler **String** -Parameter.

  Dieser Parameter optimiert das Programm durch die Platzierung der angegebenen Paketfunktionen (COMDATs) in das Image in einer vorherbestimmten Reihenfolge.

  Weitere Informationen finden Sie unter [/ORDER (Reihenfolge von Funktionen festlegen)](/cpp/build/reference/order-put-functions-in-order).

- **GenerateDebugInformation**

  Optionaler **Boolean** -Parameter.

  `true` erstellt Debuginformationen für die *EXE* -Datei oder DLL.

  Weitere Informationen finden Sie unter [/DEBUG (Debuginfo generieren)](/cpp/build/reference/debug-generate-debug-info).

- **GenerateManifest**

  Optionaler **Boolean** -Parameter.

  `true` erstellt eine parallele Manifestdatei.

  Weitere Informationen finden Sie unter [/MANIFEST (Paralleles Assemblymanifest erstellen)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **GenerateMapFile**

  Optionaler **Boolean** -Parameter.

  `true` erstellt eine *Zuordnungsdatei*. Die Dateinamenerweiterung der Zuordnungsdatei lautet *MAP*.

  Weitere Informationen hierzu finden Sie unter [/MAP (Zuordnungsdatei generieren)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize**

  Optionaler **String** -Parameter.

  Gibt die physische Speichermenge auf dem Heap an, die zu einem Zeitpunkt zugeordnet werden soll.

  Weitere Informationen finden Sie unter dem `commit`-Argument in [/HEAP (Heapgröße festlegen)](/cpp/build/reference/heap-set-heap-size). Siehe auch den **HeapReserveSize** -Parameter.

- **HeapReserveSize**

  Optionaler **String** -Parameter.

  Gibt die Gesamtgröße der Heapzuordnung im virtuellen Speicher an.

  Weitere Informationen finden Sie unter dem `reserve`-Argument in [/HEAP (Heapgröße festlegen)](/cpp/build/reference/heap-set-heap-size). Siehe auch den Parameter **HeapCommitSize** in dieser Tabelle.

- **IgnoreAllDefaultLibraries**

  Optionaler **Boolean** -Parameter.

  `true` weist den Linker an, mindestens eine Standardbibliothek aus der Liste der Bibliotheken, die durchsucht werden, zu entfernen, wenn externe Verweise aufgelöst werden.

  Weitere Informationen finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **IgnoreEmbeddedIDL**

  Optionaler **Boolean** -Parameter.

  `true` gibt an, dass IDL-Attribute im Quellcode nicht in einer *IDL* -Datei verarbeitet werden sollten.

  Weitere Informationen finden Sie unter [/IGNOREIDL (Attribute nicht in MIDL verarbeiten)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **IgnoreImportLibrary**

  Optionaler **Boolean** -Parameter.

  `true` gibt an, dass die von dieser Konfiguration generierte Importbibliothek nicht in abhängige Projekte importiert werden sollte.

  Dieser Parameter entspricht keiner Linkeroption.

- **IgnoreSpecificDefaultLibraries**

  Optionaler **String[]** -Parameter.

  Gibt einen oder mehrere Namen der zu ignorierenden Standardbibliotheken an. Trennen Sie mehrere Bibliotheken mit Semikolons.

  Weitere Informationen finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **ImageHasSafeExceptionHandlers**

  Optionaler **Boolean** -Parameter.

  Bei `true` erstellt der Linker nur dann ein Image, wenn auch eine Tabelle mit den sicheren Ausnahmehandlern des Images erstellt werden kann.

  Weitere Informationen finden Sie unter [/SAFESEH (Image verfügt über sichere Ausnahmehandler)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **ImportLibrary**

  Ein benutzerdefinierter Importbibliotheksname, der den Standard-Bibliotheksnamen ersetzt.

  Weitere Informationen finden Sie unter [/IMPLIB (Name der Importbibliothek)](/cpp/build/reference/implib-name-import-library).

- **KeyContainer**

  Optionaler **String** -Parameter.

  Container, der den Schlüssel für eine signierte Assembly enthält.

  Weitere Informationen finden Sie unter [/KEYCONTAINER (Schlüsselcontainer zum Signieren einer Assembly festlegen)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Siehe auch den Parameter **KeyFile** in dieser Tabelle.

- **KeyFile**

  Optionaler **String** -Parameter.

  Gibt eine Datei an, die den Schlüssel für eine signierte Assembly enthält.

  Weitere Informationen finden Sie unter [/KEYFILE (Schlüsselcontainer oder Schlüsselpaar zum Signieren einer Assembly festlegen)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Siehe auch den Parameter **KeyContainer**.

- **LargeAddressAware**

  Optionaler **Boolean** -Parameter.

  Bei `true` kann die Anwendung Adressen verarbeiten, die größer als 2 GB sind.

  Weitere Informationen finden Sie unter [/LARGEADDRESSAWARE (Umfangreiche Adressen verarbeiten)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL**

  Optionaler **Boolean** -Parameter.

  `true` erstellt eine DLL als Hauptausgabedatei.

  Weitere Informationen finden Sie unter [/DLL (DLL erstellen)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  Optionaler **String** -Parameter.

  Ermöglicht Ihnen, Informationen über interne Compilerfehler direkt an Microsoft zu senden.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **NoErrorReport** -  **/ERRORREPORT:NONE**

  - **PromptImmediately** -  **/ERRORREPORT:PROMPT**

  - **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**

  - **SendErrorReport** -  **/ERRORREPORT:SEND**

  Weitere Informationen finden Sie unter [/ERRORREPORT (Interne Linkerfehler melden)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **LinkIncremental**

  Optionaler **Boolean** -Parameter.

  `true` aktiviert die inkrementelle Verknüpfung.

  Weitere Informationen finden Sie unter [/INCREMENTAL (inkrementell verknüpfen)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryDependencies**

  Optionaler **Boolean** -Parameter.

  `true` gibt an, dass die Bibliotheksausgaben von Projektabhängigkeiten automatisch eingebunden werden.

  Dieser Parameter entspricht keiner Linkeroption.

- **LinkStatus**

  Optionaler **Boolean** -Parameter.

  `true` gibt an, dass der Linker eine Statusanzeige ausgibt, die anzeigt, welcher Prozentsatz des Links abgeschlossen ist.

  Weitere Informationen finden Sie unter dem`STATUS`-Argument in [/LTCG (Code zur Verknüpfungszeit generieren)](/cpp/build/reference/ltcg-link-time-code-generation).

- **LinkTimeCodeGeneration**

  Optionaler **String** -Parameter.

  Gibt Optionen für die profilgesteuerte Optimierung an.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **Default** -  *\<none>*

  - **UseLinkTimeCodeGeneration** -  **/LTCG**

  - **PGInstrument** -  **/LTCG:PGInstrument**

  - **PGOptimization** -  **/LTCG:PGOptimize**

  - **PGUpdate**

    \- **/LTCG:PGUpdate**

  Weitere Informationen finden Sie unter [/LTCG (Code zur Verknüpfungszeit generieren)](/cpp/build/reference/ltcg-link-time-code-generation).

- **ManifestFile**

  Optionaler **String** -Parameter.

  Ändert den Standardnamen der Manifestdatei in den angegebenen Dateinamen.

  Weitere Informationen finden Sie unter [/MANIFESTFILE (Manifestdatei benennen)](/cpp/build/reference/manifestfile-name-manifest-file).

- **MapExports**

  Optionaler **Boolean** -Parameter.

  `true` weist den Linker an, exportierte Funktionen in eine Zuordnungsdatei einzufügen.

  Weitere Informationen finden Sie unter dem `EXPORTS`-Argument in [/MAPINFO (Daten in Zuordnungsdatei einfügen)](/cpp/build/reference/mapinfo-include-information-in-mapfile).

- **MapFileName**

  Optionaler **String** -Parameter.

  Ändert den Standardnamen der Zuordnungsdatei in den angegebenen Dateinamen.

- **MergedIDLBaseFileName**

  Optionaler **String** -Parameter.

  Gibt den Dateinamen und die Dateinamenerweiterung der *IDL* -Datei an.

  Weitere Informationen finden Sie unter [/IDLOUT (Namen der MIDL-Ausgabedateien)](/cpp/build/reference/idlout-name-midl-output-files).

- **MergeSections**

  Optionaler **String** -Parameter.

  Kombiniert Abschnitte in einem Image. Geben Sie `from-section=to-section`an.

  Weitere Informationen finden Sie unter [/MERGE (Abschnitte kombinieren)](/cpp/build/reference/merge-combine-sections).

- **MidlCommandFile**

  Optionaler **String** -Parameter.

  Geben Sie den Namen einer Datei an, die MIDL-Befehlszeilenoptionen enthält.

  Weitere Informationen finden Sie unter [/MIDL (Optionen für MIDL-Befehlszeile festlegen)](/cpp/build/reference/midl-specify-midl-command-line-options).

- **MinimumRequiredVersion**

  Optionaler **String** -Parameter.

  Gibt die mindestens erforderliche Version des Subsystems an. Die Argumente sind Dezimalzahlen im Bereich von 0 bis 65535.

- **ModuleDefinitionFile**

  Optionaler **String** -Parameter.

  Gibt den Namen einer [Moduldefinitionsdatei](/cpp/build/reference/module-definition-dot-def-files) an.

  Weitere Informationen finden Sie unter [/DEF (Moduldefinitionsdatei festlegen)](/cpp/build/reference/def-specify-module-definition-file).

- **MSDOSStubFileName**

  Optionaler **String** -Parameter.

  Fügt ein MS-DOS-Stubprogramm an ein Win32-Programm an.

  Weitere Informationen finden Sie unter [/STUB (Name der MS-DOS-Stubdatei)](/cpp/build/reference/stub-ms-dos-stub-file-name).

- **NoEntryPoint**

  Optionaler **Boolean** -Parameter.

  `true` gibt eine DLL an, die nur als Ressource dient.

  Weitere Informationen finden Sie unter [/NOENTRY (Kein Einstiegspunkt)](/cpp/build/reference/noentry-no-entry-point).

- **ObjectFiles**

  Impliziter **String[]** -Parameter.

  Gibt die Objektdateien an, die verknüpft sind.

- **OptimizeReferences**

  Optionaler **Boolean** -Parameter.

  `true` schließt Funktionen und/oder Daten aus, auf die nie verwiesen wird.

  Weitere Informationen finden Sie unter dem `REF`-Argument der [/OPT (Optimierungen)](/cpp/build/reference/opt-optimizations).

- **OutputFile**

  Optionaler **String** -Parameter.

  Überschreibt den Standardnamen und den Speicherort des Programms, das der Linker erstellt.

  Weitere Informationen finden Sie unter [/OUT (Ausgabedateiname)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection**

  Optionaler **Boolean** -Parameter.

  Wenn `true` und Ausgabe registrieren aktiviert ist, erzwingen die Registrierungsschreibvorgänge die Umleitung von **HKEY_CLASSES_ROOT** nach **HKEY_CURRENT_USER**.

- **PreprocessOutput**

  Optionaler `ITaskItem[]`-Parameter.

  Definiert ein Array von Präprozessor-Ausgabeelementen, die verbraucht und von Aufgaben ausgegeben werden können.

- **PreventDllBinding**

  Optionaler **Boolean** -Parameter.

  `true` gibt *Bind.exe* an, dass das verknüpfte Image nicht gebunden werden soll.

  Weitere Informationen finden Sie unter [/ALLOWBIND (DLL-Bindung verhindern)](/cpp/build/reference/allowbind-prevent-dll-binding).

- **Profil**

  Optionaler **boolescher** Parameter.

  `true` erstellt eine Ausgabedatei, die mit dem **Leistungstools** -Profiler verwendet werden kann.

  Weitere Informationen finden Sie unter [/PROFILE (Leistungstools-Profiler)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfileGuidedDatabase**

  Optionaler **String** -Parameter.

  Gibt den Namen der *PGD* -Datei an, die zum Speichern von Informationen zum ausgeführten Programm verwendet wird

  Weitere Informationen finden Sie unter [/PGD (Datenbank für profilgesteuerte Optimierungen angeben)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

- **ProgramDatabaseFile**

  Optionaler **String** -Parameter.

  Gibt einen Namen für die Programmdatenbank (PDB) an, die der Linker erstellt.

  Weitere Informationen finden Sie unter [/PDB (Programmdatenbank verwenden)](/cpp/build/reference/pdb-use-program-database).

- **RandomizedBaseAddress**

  Optionaler **Boolean** -Parameter.

  `true` generiert ein ausführbares Image, für das zur Ladezeit mit der *Address Space Layout Randomization* -Funktion (ASLR) von Windows nach dem Zufallsprinzip ein Rebase-Vorgang ausgeführt werden kann.

  Weitere Informationen finden Sie unter [/DYNAMICBASE (Address Space Layout Randomization verwenden)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).

- **RegisterOutput**

  Optionaler **Boolean** -Parameter.

  `true` registriert die primäre Ausgabe dieses Builds.

- **SectionAlignment**

  Optionaler **Integer** -Parameter.

  Gibt die Ausrichtung der einzelnen Abschnitte innerhalb des linearen Adressraums des Programms an. Der Parameterwert ist eine Einheit von Bytes und eine Potenz von zwei.

  Weitere Informationen finden Sie unter [/ALIGN (Abschnittsausrichtung)](/cpp/build/reference/align-section-alignment).

- **SetChecksum**

  Optionaler **Boolean** -Parameter.

  `true` legt die Prüfsumme im Header einer *EXE* -Datei fest.

  Weitere Informationen finden Sie unter [/RELEASE (Prüfsumme festlegen)](/cpp/build/reference/release-set-the-checksum).

- **ShowProgress**

  Optionaler **String** -Parameter.

  Gibt den Ausführlichkeitsgrad von Statusberichten für die Verknüpfungsoperation an.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **NotSet** -  *\<none>*

  - **LinkVerbose** -  **/VERBOSE**

  - **LinkVerboseLib** -  **/VERBOSE:Lib**

  - **LinkVerboseICF** -  **/VERBOSE:ICF**

  - **LinkVerboseREF** -  **/VERBOSE:REF**

  - **LinkVerboseSAFESEH** -  **/VERBOSE:SAFESEH**

  - **LinkVerboseCLR** -  **/VERBOSE:CLR**

  Weitere Informationen finden Sie unter [/VERBOSE (Statusmeldungen ausgeben)](/cpp/build/reference/verbose-print-progress-messages).

- **Sources**

  Erforderlicher `ITaskItem[]`-Parameter.

  Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.

- **SpecifySectionAttributes**

  Optionaler **String** -Parameter.

  Gibt die Attribute eines Abschnitts an. Dadurch werden die Attribute überschrieben, die beim Kompilieren der *OBJ* -Datei für den Abschnitt festgelegt wurden.

  Weitere Informationen finden Sie unter [/SECTION (Abschnittsattribute angeben)](/cpp/build/reference/section-specify-section-attributes).

- **StackCommitSize**

  Optionaler **String** -Parameter.

  Gibt die Menge an physikalischem Speicher in jeder Zuordnung an, wenn zusätzlicher Speicher belegt wird.

  Weitere Informationen finden Sie unter dem `commit`-Argument in [/STACK (Stapelreservierungen)](/cpp/build/reference/stack-stack-allocations).

- **StackReserveSize**

  Optionaler **String** -Parameter.

  Gibt die Gesamtgröße der Stapelreservierung im virtuellen Speicher an.

  Weitere Informationen finden Sie unter dem `reserve`-Argument in [/STACK (Stapelreservierungen)](/cpp/build/reference/stack-stack-allocations).

- **StripPrivateSymbols**

  Optionaler **String** -Parameter.

  Erstellt eine zweite Programmdatenbank (PDB)-Datei, die keine Symbole enthält, die Sie nicht an Ihre Kunden verteilen möchten. Geben Sie den Namen der zweiten PDB-Datei an.

  Weitere Informationen finden Sie unter [/PDBSTRIPPED (Private Symbole entfernen)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **SubSystem**

  Optionaler **String** -Parameter.

  Gibt die Umgebung für die ausführbare Datei an.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **NotSet** -  *\<none>*

  - **Konsole** -  **/SUBSYSTEM:CONSOLE**

  - **Windows** -  **/SUBSYSTEM:WINDOWS**

  - **Nativ** -  **/SUBSYSTEM:NATIVE**

  - **EFI-Anwendung** -  **/SUBSYSTEM:EFI_APPLICATION**

  - **EFI-Startdiensttreiber** -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**

  - **EFI-ROM** -  **/SUBSYSTEM:EFI_ROM**

  - **EFI-Laufzeit** -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**

  - **WindowsCE** -  **/SUBSYSTEM:WINDOWSCE**

  - **POSIX** -  **/SUBSYSTEM:POSIX**

  Weitere Informationen finden Sie unter [/SUBSYSTEM (Subsystem angeben)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL**

  Optionaler **Boolean** -Parameter.

  `true` weist den Linker an, keine bindbare Importadresstabelle (IAT) in das endgültige Image einzuschließen.

  Weitere Informationen finden Sie unter dem `NOBIND`-Argument in [/DELAY (Laden von Importeinstellungen verzögern)](/cpp/build/reference/delay-delay-load-import-settings).

- **SupportUnloadOfDelayLoadedDLL**

  Optionaler **Boolean** -Parameter.

  `true` weist die Hilfsfunktion für das verzögerte Laden an, das explizite Entladen der DLL zu unterstützen.

  Weitere Informationen finden Sie unter dem `UNLOAD`-Argument in [/DELAY (Laden von Importeinstellungen verzögern)](/cpp/build/reference/delay-delay-load-import-settings).

- **SuppressStartupBanner**

  Optionaler **Boolean** -Parameter.

  Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.

  Weitere Informationen finden Sie unter [/NOLOGO (Startbanner unterdrücken) (Linker)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  Optionaler **Boolean** -Parameter.

  `true` weist das Betriebssystem an, zuerst die Linker-Ausgabe in eine Auslagerungsdatei zu kopieren und dann das Image von dort aus auszuführen.

  Weitere Informationen finden Sie unter dem `CD`-Argument in [/SWAPRUN (Linkerausgabe in Auslagerungsdatei laden)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Siehe auch den **SwapRunFromNET** -Parameter.

- **SwapRunFromNET**

  Optionaler **Boolean** -Parameter.

  `true` weist das Betriebssystem an, zuerst die Linker-Ausgabe in eine Auslagerungsdatei zu kopieren und dann das Image von dort aus auszuführen.

  Weitere Informationen finden Sie unter dem `NET`-Argument in [/SWAPRUN (Linkerausgabe in Auslagerungsdatei laden)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Siehe auch den **SwapRunFromCD** -Parameter in dieser Tabelle.

- **TargetMachine**

  Optionaler **String** -Parameter.

  Gibt die Zielplattform für das Programm oder die DLL an.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **NotSet** -  *\<none>*

  - **MachineARM** -  **/MACHINE:ARM**

  - **MachineEBC** -  **/MACHINE:EBC**

  - **MachineIA64** -  **/MACHINE:IA64**

  - **MachineMIPS** -  **/MACHINE:MIPS**

  - **MachineMIPS16** -  **/MACHINE:MIPS16**

  - **MachineMIPSFPU** -  **/MACHINE:MIPSFPU**

  - **MachineMIPSFPU16** -  **/MACHINE:MIPSFPU16**

  - **MachineSH4** -  **/MACHINE:SH4**

  - **MachineTHUMB** -  **/MACHINE:THUMB**

  - **MachineX64** -  **/MACHINE:X64**

  - **MachineX86** -  **/MACHINE:X86**

  Weitere Informationen finden Sie unter [/MACHINE (Zielplattform angeben)](/cpp/build/reference/machine-specify-target-platform).

- **TerminalServerAware**

  Optionaler **Boolean** -Parameter.

  `true` setzt ein Flag in das Feld IMAGE_OPTIONAL_HEADER DllCharacteristics im optionalen Header des Programm-Images. Wenn dieses Flag festgelegt ist, wird der Terminalserver keine bestimmten Änderungen an der Anwendung vornehmen.

  Weitere Informationen finden Sie unter [/TSAWARE (An Terminalserver gebundene Anwendung erstellen)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).

- **TrackerLogDirectory**

  Optionaler **String** -Parameter.

  Gibt das Verzeichnis des Nachverfolgungsprotokolls an.

- **TreatLinkerWarningAsErrors**

  Optionaler **Boolean** -Parameter.

  `true` bewirkt, dass keine Ausgabedatei generiert wird, wenn der Linker eine Warnung generiert.

  Weitere Informationen finden Sie unter [/WX (Linkerwarnungen als Fehler behandeln)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnOffAssemblyGeneration**

  Optionaler **Boolean** -Parameter.

  `true` erstellt ein Image für die aktuelle Ausgabedatei ohne eine .NET Framework-Assembly.

  Weitere Informationen finden Sie unter [/NOASSEMBLY (MSIL-Modul erstellen)](/cpp/build/reference/noassembly-create-a-msil-module).

- **TypeLibraryFile**

  Optionaler **String** -Parameter.

  Gibt den Dateinamen und die Dateinamenerweiterung der *TLB* -Datei an. Geben Sie einen Dateinamen oder einen Pfad und Dateinamen ein.

  Weitere Informationen finden Sie unter [/TLBOUT (TLB-Datei benennen)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  Optionaler **Integer** -Parameter.

  Kennzeichnet einen benutzerdefinierten Wert für die vom Linker erstellte Typbibliothek. Geben Sie einen Wert von 1 bis 65535 an.

  Weitere Informationen finden Sie unter [/TLBID (Ressourcen-ID für TypeLib festlegen)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **UACExecutionLevel**

  Optionaler **String** -Parameter.

  Gibt die angeforderte Ausführungsebene für die Anwendung an, wenn diese mit Benutzerkontensteuerung ausgeführt wird.

  Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

  - **AsInvoker** - `level='asInvoker'`

  - **HighestAvailable** - `level='highestAvailable'`

  - **RequireAdministrator** - `level='requireAdministrator'`

  Weitere Informationen finden Sie unter dem `level`-Argument in [/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UACUIAccess**

  Optionaler **Boolean** -Parameter.

  Bei `true` umgeht die Anwendung Sicherheitsebenen für Benutzeroberflächen und steuert die Eingabe in Fenster mit höheren Berechtigungen auf dem Desktop; andernfalls `false`.

  Weitere Informationen finden Sie unter dem `uiAccess`-Argument in [/MANIFESTUAC (bettet UAC-Informationen in Manifest ein)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UseLibraryDependencyInputs**

  Optionaler **Boolean** -Parameter.

  Bei `true` werden die Eingaben in das Bibliothekstool eher verwendet als die Bibliotheksdatei selbst, wenn Bibliotheksausgaben von Projektabhängigkeiten verknüpft sind.

- **Version**

  Optionaler **String** -Parameter.

  Fügen Sie im Header der *EXE* - oder *DLL* -Datei eine Versionsnummer ein. Geben Sie „`major[.minor]`“ an. Die `major` und `minor`-Argumente sind Dezimalzahlen von 0 bis 65535.

  Weitere Informationen finden Sie unter [/VERSION (Versionsinformationen)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Siehe auch

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
