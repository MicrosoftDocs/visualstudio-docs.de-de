---
title: MIDL-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie mehr über die MIDL-Aufgabe von MSBuild, die das MIDL-Compilertool (Microsoft Interface Definition Language) „midl.exe“ umschließt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), MIDL task
- MIDL task (MSBuild (C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a310cd4428232338ed46a8a54502d9956e73be15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932011"
---
# <a name="midl-task"></a>MIDL-Aufgabe

Umschließt das MIDL-Compilertool (Microsoft Interface Definition Language), *midl.exe*. Weitere Informationen finden Sie unter [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

## <a name="parameters"></a>Parameter

 Im Folgenden werden die Parameter der **MIDL**-Aufgabe beschrieben. Die meisten Aufgabenparameter und einige andere Parameter entsprechen einer Befehlszeilenoption.

- **AdditionalIncludeDirectories**

     Optionaler **String[]** -Parameter.

     Fügt ein Verzeichnis zur Liste der Verzeichnisse hinzu, die auf importierte IDL-Dateien durchsucht werden, einschließlich Headerdateien und Anwendungskonfigurationsdateien (ACF).

     Weitere Informationen finden Sie unter der Option **/I** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **AdditionalOptions**

     Optionaler **String** -Parameter.

     Eine Liste der Befehlszeilenoptionen. Beispiel: /\<option1> /\<option2> /\<option#>. Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht durch einen anderen MIDL-Aufgabenparameter repräsentiert werden.

     Weitere Informationen finden Sie unter [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **ApplicationConfigurationMode**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, dann können Sie einige ACF-Schlüsselwörter in der IDL-Datei benutzen.

     Weitere Informationen finden Sie unter der Option **/app_config** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **ClientStubFile**

     Optionaler **String** -Parameter.

     Gibt den Namen der Client-Stub-Datei für eine RPC-Schnittstelle an.

     Weitere Informationen finden Sie unter der Option **/cstub** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference). Siehe auch den Parameter **ServerStubFile** in dieser Tabelle.

- **CPreprocessOptions**

     Optionaler **String** -Parameter.

     Gibt Optionen für die Übergabe an den C++-Präprozessor an. Geben eine durch Leerzeichen getrennte Liste mit Präprozessoroptionen an.

     Weitere Informationen finden Sie unter der Option **/cpp_opt** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **DefaultCharType**

     Optionaler **String** -Parameter.

     Gibt den standardmäßigen Zeichentyp an, den der C-Compiler verwendet, um den generierten Code zu kompilieren.

     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

    |Wert|Befehlszeilenoption|
    |-----------|--------------------------|
    |**Signed**|**/char signed**|
    |**Unsigned**|**/char unsigned**|
    |**Ascii**|**/char ascii7**|

     Weitere Informationen finden Sie unter der Option **/char** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **DllDataFileName**

     Optionaler **String** -Parameter.

     Gibt den Dateinamen für die generierte *dlldata*-Datei für eine Proxy-DLL an.

     Weitere Informationen finden Sie unter der Option **/dlldata** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **EnableErrorChecks**

     Optionaler **String** -Parameter.

     Gibt den Fehlertyp an, und überprüft, dass die generierten Stubs in der Laufzeit ausgeführt werden.

     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

    |Wert|Befehlszeilenoption|
    |-----------|--------------------------|
    |**Keine**|**/error none**|
    |**EnableCustom**|**/error**|
    |**Alle**|**/error all**|

     Weitere Informationen finden Sie unter der Option **/error** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckAllocations**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, stellen Sie sicher, das keine Fehler aufgrund von unzureichendem Arbeitsspeicher aufgetreten sind.

     Weitere Informationen finden Sie unter der Option **/error allocation** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckBounds**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, dann wird die Größe der konform-variierenden und variierenden Arrays mit der Übertragungslängenspezifikation abgeglichen.

     Weitere Informationen finden Sie unter der Option **/error bounds_check** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckEnumRange**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, wird überprüft, ob sich die Enumerationswerte im zulässigen Bereich befinden.

     Weitere Informationen finden Sie unter der Option **/error enum** in der Befehlszeilenhilfe ( **/?** ) für *midl.exe*.

- **ErrorCheckRefPointers**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, stellen Sie sicher, dass keine NULL-Verweiszeiger an die Client-Stubs übergeben werden.

     Weitere Informationen finden Sie unter der Option **/error ref** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **ErrorCheckStubData**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, wird ein Stub generiert, das Unmarshalling-Ausnahmen auf Serverseite erkennt, und überträgt sie zurück an den Client.

     Weitere Informationen finden Sie unter der Option **/error stub_data** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateClientFiles**

     Optionaler **String** -Parameter.

     Legt fest, ob der Compiler clientseitige C-Quelldateien für eine RPC-Schnittstelle generiert.

     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

    |Wert|Befehlszeilenoption|
    |-----------|--------------------------|
    |**Keine**|**/client none**|
    |**Stub**|**/client stub**|

     Weitere Informationen finden Sie unter der Option **/client** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateServerFiles**

     Optionaler **String** -Parameter.

     Legt fest, ob der Compiler serverseitige C-Quelldateien für eine RPC-Schnittstelle generiert.

     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

    |Wert|Befehlszeilenoption|
    |-----------|--------------------------|
    |**Keine**|**/server none**|
    |**Stub**|**/server stub**|

     Weitere Informationen finden Sie unter der Option **/server** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateStublessProxies**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, werden vollständig interpretierte Stubs mit Proxys ohne Stubs für Objektschnittstellen generiert.

     Weitere Informationen finden Sie unter der Option **/Oicf** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **GenerateTypeLibrary**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, dann wird keine Typbibliotheksdatei ( *.tlb*) generiert.

     Weitere Informationen finden Sie unter der Option **/notlb** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **HeaderFileName**

     Optionaler **String** -Parameter.

     Gibt den Namen der generierten Headerdatei an.

     Weitere Informationen finden Sie unter der Option **/h** oder **/header** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **IgnoreStandardIncludePath**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, dann sucht die MIDL-Aufgabe nur in den angegebenen Verzeichnissen mithilfe des Schalters **AdditonalIncludeDirectories**, und ignoriert das aktuelle Verzeichnis und die durch die Umgebungsvariable „INCLUDE“ angegebenen Verzeichnisse.

     Weitere Informationen finden Sie unter der Option **/no_def_idir** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **InterfaceIdentifierFileName**

     Optionaler **String** -Parameter.

     Gibt den Namen für die *Schnittstellen-Bezeichnerdatei* für die COM-Schnittstelle an. Dies setzt den Standardnamen außer Kraft, der durch ein Anhängen von „_i.c“ an den IDL-Dateinamen entsteht.

     Weitere Informationen finden Sie unter der Option **/iid** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **LocaleID**

     Optionaler **int**-Parameter.

     Gibt den *Gebietsschemabezeichner* an, der den Gebrauch von internationalen Zeichen in der Eingabedatei, dem Dateinamen und den Verzeichnispfaden ermöglicht. Geben Sie einen dezimalen Gebietsschemabezeichner an.

     Weitere Informationen finden Sie unter der Option **/lcid** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference). Siehe auch [Gebietsschemabezeichner](/windows/desktop/intl/locale-identifiers).

- **MkTypLibCompatible**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, dann muss das Format der Eingabedatei mit *mktyplib.exe* Version 2.03 kompatibel sein.

     Weitere Informationen finden Sie unter Option **/mktyplib203** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference). Siehe auch [ODL-Dateisyntax](/previous-versions/windows/desktop/automat/odl-file-syntax) auf der MSDN-Website.

- **OutputDirectory**

     Optionaler **String** -Parameter.

     Gibt das Standardverzeichnis an, in dem die MIDL-Aufgabe Ausgabedateien schreibt.

     Weitere Informationen finden Sie unter der Option **/out** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **PreprocessorDefinitions**

     Optionaler **String[]** -Parameter.

     Gibt einen oder mehrere *defines* an; d.h., einen Namen oder einen optionalen Wert, der an einen C-Präprozessor wie von einer `#define`-Direktive weitergegeben werden soll. Jedes „define“ ist folgendermaßen aufgebaut: *name[=value]* .

     Weitere Informationen finden Sie unter der Option **/D** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference). Siehe auch die Parameter **UndefinePreprocessorDefinitions** in dieser Tabelle.

- **ProxyFileName**

     Optionaler **String** -Parameter.

     Gibt den Namen für die Schnittstellen-Proxydatei für die COM-Schnittstelle an.

     Weitere Informationen finden Sie unter der Option **/proxy** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **RedirectOutputAndErrors**

     Optionaler **String** -Parameter.

     Leitet Ausgaben, wie z.B. Fehlermeldungen und Warnungen, aus der Standardausgabe in die angegebenen Dateien weiter.

     Weitere Informationen finden Sie unter der Option **/o** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **ServerStubFile**

     Optionaler **String** -Parameter.

     Gibt den Namen der Server-Stub-Datei für eine RPC-Schnittstelle an.

     Weitere Informationen finden Sie unter der Option **/sstub** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference). Siehe auch den Parameter **ClientStubFile** in dieser Tabelle.

- **Quelle**

     Erforderlicher `ITaskItem[]`-Parameter.

     Gibt eine durch Leerzeichen getrennte Liste der Quelldateien an.

- **StructMemberAlignment**

     Optionaler **String** -Parameter.

     Gibt die Zuweisung (*Komprimierungsebene*) der Strukturen im Zielsystem an.

     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

    |Wert|Befehlszeilenoption|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**1**|**/Zp1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/Zp8**|

     Weitere Informationen finden Sie unter der Option **/Zp** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference). Die Option **/Zp** ist äquivalent zu der Option **/pack** und der älteren Option **/align**.

- **SuppressCompilerWarnings**

     Optionaler **Boolean**-Parameter.

     Wenn `true`, dann werden Warnmeldungen aus der MIDL-Aufgabe unterdrückt.

     Weitere Informationen finden Sie unter der Option **/no_warn** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **SuppressStartupBanner**

     Optionaler `Boolean`-Parameter.

     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.

     Weitere Informationen finden Sie unter der Option **/nologo** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **TargetEnvironment**

     Optionaler **String**-Parameter.

     Gibt die Umgebung an, in der die Anwendung ausgeführt wird.

     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

    |Wert|Befehlszeilenoption|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**Win32**|**/env win32**|
    |**Itanium**|**/env ia64**|
    |**X64**|**/env x64**|

     Weitere Informationen finden Sie unter der Option **/env** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **TrackerLogDirectory**

     Optionaler `String`-Parameter.

     Gibt das Zwischenverzeichnis an, in dem die Nachverfolgungsprotokolle für diese Aufgabe gespeichert sind.

- **TypeLibFormat**

     Optionaler **String**-Parameter.

     Gibt das Format der Typbibliotheksdatei an.

     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

    |Wert|Befehlszeilenoption|
    |-----------|--------------------------|
    |**NewFormat**|**/newtlb**|
    |**OldFormat**|**/oldtlb**|

     Weitere Informationen finden Sie unter den Optionen **/newtlb** und **/oldtlb** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **TypeLibraryName**

     Optionaler **String**-Parameter.

     Gibt den Namen der Typbibliotheksdatei an.

     Weitere Informationen finden Sie unter der Option **/tlb** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **UndefinePreprocessorDefinitions**

     Optionaler **String[]** -Parameter.

     Entfernt jede vorherige Definition eines Namens, indem er den Namen wie eine `#undefine`-Direktive an den C-Präprozessor weitergibt. Geben Sie eine oder mehrere vorher definierte Namen ein.

     Weitere Informationen finden Sie unter der Option **/U** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference). Siehe auch die Parameter **PreprocessorDefinitions** in dieser Tabelle.

- **ValidateAllParameters**

     Optionaler `Boolean`-Parameter.

     Wenn `true`, dann werden zusätzliche Dateifehler-Überprüfungsinformationen generiert, die für Integritätsprüfungen in der Laufzeit verwendet werden. Wenn `false`, dann werden keine Dateifehler-Überprüfungsinformationen generiert.

     Weitere Informationen finden Sie unter den Optionen **/robust** und **/no_robust** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference).

- **WarnAsError**

     Optionaler `Boolean`-Parameter.

     Wenn `true`, werden alle Warnungen als Fehler behandelt.

     Wenn der MIDL-Aufgabenparameter **WarningLevel** nicht angegeben ist, werden Warnungen auf Standardlevel und auf Level 1 wie Fehler behandelt.

     Weitere Informationen finden Sie unter der Option **/WX** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference). Siehe auch den Parameter **WarningLevel** in dieser Tabelle.

- **WarningLevel**

     Optionaler **String**-Parameter.

     Gibt den Schweregrad (*Warnstufe*) von auszugebenden Warnungen an. Für den Wert 0 wird keine Warnung ausgegeben. Andernfalls wird eine Warnung ausgegeben, wenn ihre Warnstufe numerisch kleiner als oder gleich der angegebene Wert ist.

     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.

    |Wert|Befehlszeilenoption|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     Weitere Informationen finden Sie unter der Option **/W** in der [MIDL-Befehlszeilenreferenz](/windows/desktop/Midl/midl-command-line-reference). Siehe auch den Parameter **WarningLevel** in dieser Tabelle.

## <a name="see-also"></a>Siehe auch

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
