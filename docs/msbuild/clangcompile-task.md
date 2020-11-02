---
title: ClangCompile-Aufgabe | Microsoft-Dokumentation
description: Beschreibt den Zweck und die Parameter der MSBuild-Aufgabe „ClangCompile“, die das C++-Compilertool (clang.exe) umschließt.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ClangCompile task
- ClangCompile task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 63b278f322e66e6622064288d322709c51df336d
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796822"
---
# <a name="clangcompile-task"></a>ClangCompile-Aufgabe

Umschließt das Microsoft C++-Compilertool (clang.exe).

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der Aufgabe **ClangCompile** beschrieben:

|Parameter|Beschreibung|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Optionaler **string[]** -Parameter.<br/><br/>Gibt mindestens ein Verzeichnis an, das dem include-Pfad hinzugefügt werden soll. Verwenden Sie Semikolons als Trennzeichen, wenn mehrere Verzeichnisse vorhanden sind.<br/><br/>Verwenden Sie `-I[path]`.|
|**AdditionalOptions**|Optionaler **string** -Parameter|
|**BufferSecurityCheck**|Optionaler **string** -Parameter<br/><br/>Die Sicherheitsprüfung hilft bei der Erkennung von Überläufen des Stapelpuffers. Hierbei handelt es sich um gängige Versuche, die Sicherheit eines Programms zu gefährden. <br/><br/>Verwenden Sie `fstack-protector`.|
|**BuildingInIde**|Optionaler **bool** -Parameter.|
|**CLanguageStandard**|Optionaler **string** -Parameter<br/><br/>Bestimmt den C-Sprachstandard.<br/><br/>Verwenden Sie `std=[value]` mit einem der folgenden Werte: **c89** , **c99** , **c11** , **gnu99** oder **gnu11** .|
|**ClangVersion**|Optionaler **string** -Parameter|
|**CompileAs**|Optionaler **string** -Parameter<br/><br/>Wählen Sie die Kompilierungssprachenoption für C- und CPP-Dateien aus. Standardmäßig erfolgt die Erkennung anhand der Erweiterung „.c“ oder „.cpp“.<br/><br/>Verwenden Sie `-x c`, `-x c++`.|
|**CppLanguageStandard**|Optionaler **string** -Parameter<br/><br/>Bestimmt den C++-Sprachstandard<br/><br/>Verwenden Sie `std=[value]` mit einem der folgenden Werte: **c++98** , **c++11** , **c++1y** , **gnu++98** , **gnu++11** oder **gnu++1y** .|
|**DataLevelLinking**|Optionaler **bool** -Parameter.<br/><br/>Ermöglicht Linker-Optimierungen, nicht verwendete Daten zu entfernen, indem jedes Datenelement in einem separaten Feld ausgegeben wird.|
|**DebugInformationFormat**|Optionaler **string** -Parameter<br/><br/>Gibt den Typ der Debuginformationen an, die vom Compiler generiert werden.<br/><br/>**None** : Generiert keine Debuginformationen, sodass die Kompilierung ggf. schneller erfolgt. (Verwenden Sie `g0`.)<br/>**FullDebug** : Generiert DWARF2-Debuginformationen. (Verwenden Sie `g2 -gdwarf-2`.)<br/>**LineNumber** : Generiert nur Informationen zur Zeilennummer. (Verwenden Sie `gline-tables-only`.)|
|**EnableNeonCodegen**|Optionaler **bool** -Parameter.<br/><br/>Aktiviert die Codegenerierung für NEON-Gleitkomma-Hardware. Dies gilt nur für die ARM-Architektur.|
|**ExceptionHandling**|Optionaler **string** -Parameter<br/><br/>Gibt das Ausnahmebehandlungsmodell an, das vom Compiler verwendet wird.<br/><br/>**Disabled** : Deaktiviert die Ausnahmebehandlung. (Verwenden Sie `fno-exceptions`.)<br/>**Enabled** : Die Ausnahmebehandlung wird aktiviert. (Verwenden Sie `fexceptions`.)<br/>**UnwindTables** : Generiert alle erforderlichen Statistikdaten, aber ohne Auswirkungen auf den generierten Code. (Verwenden Sie `funwind-tables`.)|
|**FloatABI**|Optionaler **string** -Parameter<br/><br/>Wählen Sie eine Option aus, um die Gleitkomma-ABI auszuwählen.<br/><br/>**soft** : Sorgt dafür, dass der Compiler eine Ausgabe mit Bibliotheksaufrufen für Gleitkommavorgänge generiert. (Verwenden Sie `mfloat-abi=soft`.)<br/>**softfp** : Ermöglicht die Generierung von Code unter Verwendung hardwarebasierter Gleitkomma-Anweisungen, verwendet jedoch weiterhin die Konventionen für den soft-float-Aufruf. (Verwenden Sie `mfloat-abi=softfp`.)<br/>**hard** : Ermöglicht die Generierung von Gleitkomma-Anweisungen und verwendet FPU-spezifische Aufrufkonventionen. (Verwenden Sie `mfloat-abi=hard`.)|
|**ForcedIncludeFiles**|Optionaler **string[]** -Parameter<br/><br/>Mindestens eine erzwungene Includedatei.<br/><br/>Verwenden Sie `-include [name]`.|
|**FunctionLevelLinking**|Optionaler **bool** -Parameter.<br/><br/>Ermöglicht dem Compiler, einzelne Funktionen in Form von kompilierten Funktionen (COMDATs) zu kompilieren. Zur Bearbeitung erforderlich, funktionieren weiterhin.<br/><br/>Verwenden Sie `ffunction-sections`.|
|**GccToolChain**|Optionaler **string** -Parameter<br/><br/>Ordnerpfad zur Gcc-Toolkette.|
|**GNUMode**|Optionaler **bool** -Parameter.<br/><br/>|
|**MSCompatibility**|Optionaler **bool** -Parameter.<br/><br/>Ermöglicht vollständige Microsoft C++-Kompatibilität.|
|**MSCompatibilityVersion**|Optionaler **string** -Parameter<br/><br/>Ein durch Punkte getrennter Wert, der die Versionsnummer des Microsoft-Compilers darstellt, die in _MSC_VER gemeldet wird (0 = nicht definieren (Standard)).|
|**MSExtensions**|Optionaler **bool** -Parameter.<br/><br/>Dient zum Akzeptieren einiger Nicht-Standardkonstrukte, die vom Microsoft-Compiler unterstützt werden.|
|**MSCompilerVersion**|Optionaler **string** -Parameter<br/><br/>Die Versionsnummer des Microsoft-Compilers, die in _MSC_VER gemeldet wird (0 = nicht definieren (Standard)).|
|**MSVCErrorReport**|Optionaler **bool** -Parameter.<br/><br/>Dient zum Melden von Fehlern, die Visual Studio zum Analysieren von Datei- und Zeileninformationen verwenden kann.|
|**ObjectFileName**|Optionaler **string** -Parameter<br/><br/>Gibt einen Namen an, um den Standardnamen der Objektdatei zu überschreiben. Dies kann ein Datei- oder Verzeichnisname sein.<br/><br/>Verwenden Sie `/Fo[name]`.|
|**OmitFramePointers**|Optionaler **bool** -Parameter.<br/><br/>Unterdrückt die Erstellung von Framezeigern im Anrufstapel.|
|**Optimierung**|Optionaler **string** -Parameter<br/><br/>Gibt die Optimierungsstufe für die Anwendung an.<br/><br/>**Custom** : Benutzerdefinierte Optimierung.<br/>**Disabled** : Deaktiviert die Optimierung. (Verwenden Sie `O0`.)<br/>**MinSize** : Größenoptimierung. (Verwenden Sie `Os`.)<br/>**MaxSpeed** : Geschwindigkeitsoptimierung. (Verwenden Sie `O2`.)<br/>**Full** : Aufwändige Optimierungen. (Verwenden Sie `O3`.)|
|**PositionIndependentCode**|Optionaler **bool** -Parameter.<br/><br/>Generieren von positionsunabhängigem Code (Position Independent Code, PIC) für die Verwendung in einer freigegebenen Bibliothek.|
|**PrecompiledHeader**|Optionaler **string** -Parameter<br/><br/>Ermöglicht die Erstellung oder Verwendung eines vorkompilierten Headers während der Erstellung.|
|**PrecompiledHeaderFile**|Optionaler **string** -Parameter<br/><br/>Gibt den Namen einer Headerdatei an, die als vorkompilierte Headerdatei verwendet werden soll. Diese Datei wird während des Erstellungsvorgangs auch zu **Erzwungene Includedateien** hinzugefügt.|
|**PrecompiledHeaderOutputFileDirectory**|Optionaler **string** -Parameter<br/><br/>Gibt das Verzeichnis für den generierten vorkompilierten Header an. Dieses Verzeichnis wird während des Erstellungsvorgangs auch zu **Zusätzliche Includeverzeichnisse** hinzugefügt.|
|**PrecompiledHeaderCompileAs**|Optionaler **string** -Parameter<br/><br/>Dient zum Auswählen der Kompilierungssprachenoption für die vorkompilierte Headerdatei.<br/><br/>Verwenden Sie `-x c-header`, `-x c++-header`.|
|**PreprocessorDefinitions**|Optionaler **string[]** -Parameter<br/><br/>Definiert Präprozessorsymbole für Ihre Quelldatei.<br/><br/>Verwenden Sie `-D`.|
|**RuntimeLibrary**|Optionaler **string** -Parameter<br/><br/>Dient zum Angeben der zu verknüpfenden Laufzeitbibliothek.<br/><br/>Zu verwendende Schalter: `MSVC /MT`, `/MTd`, `/MD`, `/MDd`.<br/><br/>**MultiThreaded** : Bewirkt, dass die Anwendung die statische Multithread-Version der Laufzeitbibliothek verwendet.<br/>**MultiThreadedDebug** : Definiert „_DEBUG“ und „_MT“. Diese Option führt auch dazu, dass der Compiler den Bibliotheksnamen "LIBCMTD.lib" in der .obj-Datei positioniert, sodass der Linker "LIBCMTD.lib" für das Auflösen externer Symbole verwendet.<br/>**MultiThreadedDLL** : Bewirkt, dass Ihre Anwendung die Multithread- und DLL-spezifische Version der Laufzeitbibliothek verwendet. Definiert „_MT“ und „_DLL“ und bewirkt, dass der Compiler den Bibliotheksnamen "MSVCRT.lib" in der OBJ-Datei platziert.<br/>**MultiThreadedDebugDLL** : Definiert „_DEBUG“, „_MT“ und „_DLL“ und bewirkt, dass Ihre Anwendung die Multithread- und DLL-spezifische Debugversion der Laufzeitbibliothek verwendet. Außerdem wird verursacht, dass der Compiler den Bibliotheksnamen "MSVCRTD.lib" in der .obj-Datei positioniert.|
|**RuntimeTypeInfo**|Optionaler **bool** -Parameter.<br/><br/>Fügt Code für die Überprüfung der C++-Objekttypen während der Laufzeit hinzu (Laufzeit-Typinformationen).<br/><br/>Verwenden Sie `frtti`, `fno-rtti`.|
|**ShowIncludes**|Optionaler **bool** -Parameter.<br/><br/>Generiert eine Liste der Includedateien mit Compilerausgabe.<br/><br/>Verwenden Sie `-H`.|
|**Sources**|Erforderlicher **ITaskItem[]** -Parameter.|
|**StrictAliasing**|Optionaler **bool** -Parameter.<br/><br/>Annehmen der strengsten Aliasingregeln. Bei einem Objekt eines Typs wird niemals davon ausgegangen, dass es sich an derselben Adresse wie ein Objekt eines anderen Typs befindet.|
|**Sysroot**|Optionaler **string** -Parameter<br/><br/>Ordnerpfad zum Stammverzeichnis für Header und Bibliotheken.|
|**TargetArch**|Optionaler **string** -Parameter<br/><br/>Zielarchitektur|
|**ThumbMode**|Optionaler **string** -Parameter<br/><br/>Generieren Sie Code, der für die Thumb-Mikroarchitektur ausgeführt wird. Dies gilt nur für die ARM-Architektur.<br/><br/>**Thumb** : Generiert Thumb-Code. (Verwenden Sie `mthumb`.)<br/>**ARM** : Generiert ARM-Code. (Verwenden Sie `marm`.)<br/>**Disabled** : Die Option ist für die ausgewählte Plattform nicht gültig.|
|**TrackerLogDirectory**|Optionaler **string** -Parameter<br/><br/>Nachverfolgungsprotokollverzeichnis|
|**TreatWarningAsError**|Optionaler **bool** -Parameter.<br/><br/>Behandelt alle Compilerwarnungen als Fehler.<br/><br/>Bei einem neuen Projekt kann es empfehlenswert sein, `/WX` in allen Kompilierungen zu verwenden. Die Auflösung aller Warnungen stellt sicher, dass möglichst wenig schwer zu findende Codefehler vorhanden sind.|
|**UndefinePreprocessorDefinitions**|Optionaler **string[]** -Parameter<br/><br/>Gibt mindestens eine aufgehobene Präprozessordefinition an.<br/><br/>Verwenden Sie `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions**|Optionaler **bool** -Parameter.<br/><br/>Hebt die Definition aller zuvor definierten Präprozessorwerte auf.<br/><br/>Verwenden Sie `-undef`.|
|**UseMultiToolTask**|Optionaler **bool** -Parameter.<br/><br/>Kompilierung mit mehreren Prozessoren|
|**UseShortEnums**|Optionaler **bool** -Parameter.<br/><br/>Dieser Enumerationstyp verwendet nur so viele Bytes, wie das Eingabeset an möglichen Werten erfordert.|
|**Ausführlich**|Optionaler **bool** -Parameter.<br/><br/>Befehle zum Ausführen und Verwenden der ausführlichen Ausgabe anzeigen.|
|**WarningLevel**|Optionaler **string** -Parameter<br/><br/>Wählen Sie aus, wie streng der Compiler bei Codefehlern sein soll. Weitere Flags sollten direkt zu **Zusätzliche Optionen** hinzugefügt werden. (Verwenden Sie `/w`, `/Weverything`.)<br/><br/>**TurnOffAllWarnings** : Deaktiviert alle Compilerwarnungen. (Verwenden Sie `w`.)<br/>**EnableAllWarnings** : Aktiviert alle Warnungen, einschließlich standardmäßig deaktivierter Warnungen. (Verwenden Sie `Wall`.)|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
