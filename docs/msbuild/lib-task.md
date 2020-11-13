---
title: LIB-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild die LIB-Aufgabe verwendet, um den 32-Bit-Bibliotheks-Manager von Microsoft (lib.exe) zu umschließen, der eine Bibliothek aus COFF-Objektdateien erstellt und verwaltet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), LIB task
- LIB task (MSBuild (C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bf1029d42ce40d33e6eea1fcbe5e6434ff85a36
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904452"
---
# <a name="lib-task"></a>LIB-Aufgabe

Umschließt das 32-Bit-Tool von Microsoft zur Bibliotheksverwaltung ( *lib.exe* ). Der Bibliothek-Manager erstellt und verwaltet eine Bibliothek mit Objektdateien im Common Object File Format (COFF). Der Bibliothek-Manager kann darüber hinaus Exportdateien und Importbibliotheken erstellen, um auf exportierte Definitionen zu verweisen. Weitere Informationen finden Sie unter [LIB-Referenz](/cpp/build/reference/lib-reference) und [Ausführen von LIB](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der **LIB** -Aufgabe beschrieben. Die meisten Aufgabenparameter entsprechen einer Befehlszeilenoption.

|Parameter|Beschreibung|
|---------------|-----------------|
|**AdditionalDependencies**|Optionaler **String[]** -Parameter.<br /><br /> Gibt zusätzliche Elemente an, die zur Befehlszeile hinzugefügt werden.|
|**AdditionalLibraryDirectories**|Optionaler **String[]** -Parameter.<br /><br /> Überschreibt den Bibliothekspfad der Umgebung. Geben Sie einen Verzeichnisnamen an.<br /><br /> Weitere Informationen finden Sie unter [/LIBPATH (Libpath-Pfad hinzufügen)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|Optionaler **String** -Parameter.<br /><br /> Eine Liste von *lib.exe* -Optionen (wie in der Befehlszeile angegeben). Beispiel: /\<option1> /\<option2> /\<option#>. Verwenden Sie diesen Parameter, um *lib.exe* -Optionen anzugeben, die nicht durch einen anderen **LIB** -Aufgabenparameter repräsentiert werden.<br /><br /> Weitere Informationen finden Sie unter [Ausführen von LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Optionaler **String** -Parameter.<br /><br /> Zeigt Informationen zur Ausgabebibliothek an. Geben Sie einen Dateinamen an, um die Informationen in eine Datei umzuleiten. Geben Sie "CON" oder nichts an, um die Informationen an die Konsole umzuleiten.<br /><br /> Dieser Parameter entspricht der Option **/LIST** von *lib.exe*.|
|**ErrorReporting**|Optionaler **String** -Parameter.<br /><br /> Gibt an, wie interne Fehlerinformationen an Microsoft gesendet werden, wenn *lib.exe* zur Laufzeit fehlschlägt.<br /><br /> Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.<br /><br /> -   **NoErrorReport** -  **/ERRORREPORT:NONE**<br />-   **PromptImmediately** -  **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** -  **/ERRORREPORT:SEND**<br /><br /> Weitere Informationen finden Sie bei der **/ERRORREPORT** -Befehlszeilenoption unter [Ausführen von LIB](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Optionaler **String[]** -Parameter.<br /><br /> Gibt eine oder mehrere zu exportierende Funktionen an.<br /><br /> Dieser Parameter entspricht der Option **/EXPORT:** von *lib.exe*.|
|**ForceSymbolReferences**|Optionaler **String** -Parameter.<br /><br /> Erzwingt, dass *lib.exe* einen Verweis auf das angegebene Symbol einschließt.<br /><br /> Dieser Parameter entspricht der Option **/INCLUDE:** von *lib.exe*.|
|**IgnoreAllDefaultLibraries**|Optionaler `Boolean`-Parameter.<br /><br /> Bei `true` werden alle Standardbibliotheken aus der Liste der Bibliotheken entfernt, die *lib.exe* beim Auflösen externer Verweise durchsucht.<br /><br /> Dieser Parameter entspricht der parameterlosen Form der Option **/NODEFAULTLIB** von *lib.exe*.|
|**IgnoreSpecificDefaultLibraries**|Optionaler **String[]** -Parameter.<br /><br /> Entfernt die angegebenen Bibliotheken aus der Liste der Bibliotheken, die *lib.exe* beim Auflösen externer Verweise durchsucht.<br /><br /> Dieser Parameter entspricht der Option **/NODEFAULTLIB** von *lib.exe* , die ein `library`-Argument verwendet.|
|**LinkLibraryDependencies**|Optionaler `Boolean`-Parameter.<br /><br /> `true` gibt an, dass die Bibliotheksausgaben von Projektabhängigkeiten automatisch eingebunden werden.|
|**LinkTimeCodeGeneration**|Optionaler `Boolean`-Parameter.<br /><br /> Gibt bei `true` die Link-Zeitcodegenerierung an.<br /><br /> Dieser Parameter entspricht der Option **/LCTG** von *lib.exe*.|
|**MinimumRequiredVersion**|Optionaler **String** -Parameter.<br /><br /> Gibt die mindestens erforderliche Version des Subsystems an. Geben Sie eine durch Kommas getrennte Liste von Dezimalzahlen im Bereich von 0 bis 65535 an.|
|**ModuleDefinitionFile**|Optionaler **String** -Parameter.<br /><br /> Gibt den Namen der Moduldefinitionsdatei ( *DEF* ) an.<br /><br /> Dieser Parameter entspricht der Option **/DEF** von *lib.exe* , die ein `filename`-Argument verwendet.|
|**Name**|Optionaler **String** -Parameter.<br /><br /> Gibt beim Erstellen einer Importbibliothek den Namen der DLL an, für welche die Importbibliothek erstellt wird.<br /><br /> Dieser Parameter entspricht der Option **/NAME** von *lib.exe* , die ein `filename`-Argument verwendet.|
|**OutputFile**|Optionaler **String** -Parameter.<br /><br /> Überschreibt den Standardnamen und -speicherort des Programms, das *lib.exe* erstellt.<br /><br /> Dieser Parameter entspricht der Option **/OUT** von *lib.exe* , die ein `filename`-Argument verwendet.|
|**RemoveObjects**|Optionaler **String[]** -Parameter.<br /><br /> Unterdrückt das angegebene Objekt in der Ausgabebibliothek. *lib.exe* erstellt eine Ausgabebibliothek durch Kombinieren aller Objekte (in Objektdateien und Bibliotheken) und anschließendes Löschen aller mithilfe dieser Option angegebenen Objekte.<br /><br /> Dieser Parameter entspricht der Option **/REMOVE** von *lib.exe* , die ein `membername`-Argument verwendet.|
|**Sources**|Erforderlicher `ITaskItem[]`-Parameter.<br /><br /> Gibt eine durch Leerzeichen getrennte Liste der Quelldateien an.|
|**SubSystem**|Optionaler **String** -Parameter.<br /><br /> Gibt die Umgebung für die ausführbare Datei an. Die Wahl des Subsystems hat Einfluss auf das Einstiegspunktsymbol bzw. die Einstiegspunktfunktion.<br /><br /> Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.<br /><br /> -   **Konsole** -  **/SUBSYSTEM:CONSOLE**<br />-   **Windows** -  **/SUBSYSTEM:WINDOWS**<br />-   **Nativ** -  **/SUBSYSTEM:NATIVE**<br />-   **EFI-Anwendung** -  **/SUBSYSTEM:EFI_APPLICATION**<br />-   **EFI-Startdiensttreiber** -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** -  **/SUBSYSTEM:EFI_ROM**<br />-   **EFI-Laufzeit** -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** -  **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX** -  **/SUBSYSTEM:POSIX**<br /><br /> Weitere Informationen finden Sie unter [/SUBSYSTEM (Subsystem angeben)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Optionaler **Boolean** -Parameter.<br /><br /> Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.<br /><br /> Weitere Informationen finden Sie bei der Option **/NOLOGO** unter [Ausführen von LIB](/cpp/build/reference/running-lib).|
|**TargetMachine**|Optionaler **String** -Parameter.<br /><br /> Gibt die Zielplattform für das Programm oder die DLL an.<br /><br /> Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.<br /><br /> -   **MachineARM** -  **/MACHINE:ARM**<br />-   **MachineEBC** -  **/MACHINE:EBC**<br />-   **MachineIA64** -  **/MACHINE:IA64**<br />-   **MachineMIPS** -  **/MACHINE:MIPS**<br />-   **MachineMIPS16** -  **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** - **/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** -  **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** -  **/MACHINE:SH4**<br />-   **MachineTHUMB** -  **/MACHINE:THUMB**<br />-   **MachineX64** -  **/MACHINE:X64**<br />-   **MachineX86** -  **/MACHINE:X86**<br /><br /> Weitere Informationen finden Sie unter [/MACHINE (Zielplattform angeben)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|Optionaler **String** -Parameter.<br /><br /> Gibt das Verzeichnis des Nachverfolgungsprotokolls an.|
|**TreatLibWarningAsErrors**|Optionaler **Boolean** -Parameter.<br /><br /> Bei `true` erstellt die **LIB** -Aufgabe keine Ausgabedatei, wenn *lib.exe* eine Warnung generiert. Bei `false` wird eine Ausgabedatei generiert.<br /><br /> Weitere Informationen finden Sie bei der Option **/WX** unter [Ausführen von LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Optionaler **Boolean** -Parameter.<br /><br /> Bei `true` wird das Projektsystem angewiesen, UNICODE-Antwortdateien zu generieren, wenn der Bibliothekar erzeugt wird. Geben Sie `true` an, wenn Dateien im Projekt über UNICODE-Pfade verfügen.|
|**Verbose**|Optionaler **Boolean** -Parameter.<br /><br /> Bei `true` werden Details zum Fortschritt der Sitzung angezeigt. Dies schließt die Namen der hinzuzufügenden *OBJ* -Dateien ein. Die Informationen werden an die Standardausgabe gesendet und können in eine Datei umgeleitet werden.<br /><br /> Weitere Informationen finden Sie bei der Option **/VERBOSE** unter [Ausführen von LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)