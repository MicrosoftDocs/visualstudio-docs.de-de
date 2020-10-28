---
title: Festlegen von Symboldateien (PDB-Dateien) und Quelldateien im Debugger
description: Informationen zum Konfigurieren und Verwalten von Symbol- und Quelldateien in Visual Studio
ms.custom: ''
ms.date: 10/31/2019
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eceffab5b8c179734b1abb5f1005c240912115f1
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "89599587"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Angeben von Symboldateien (PDB-Dateien) und Quelldateien im Visual Studio Debugger (C#, C++, Visual Basic, F#)

Programmdatenbankdateien ( *PDB-Dateien* ), die auch als Symboldateien bezeichnet werden, ordnen Bezeichner und Anweisungen im Quellcode des Projekts entsprechenden Bezeichnern und Anweisungen in kompilierten Apps zu. Diese Zuordnungsdateien verknüpfen den Debugger mit dem Quellcode, damit das Debuggen ermöglicht wird.

Wenn Sie ein Projekt aus der Visual Studio-IDE mit der Standardkonfiguration für Debugbuilds erstellen, erstellt der Compiler die entsprechenden Symboldateien. Dieser Artikel beschreibt die Verwaltung von Symboldateien in der IDE, z. B. wie [die Position von Symbolen in den Debugger-Optionen angegeben werden kann](#BKMK_Specify_symbol_locations_and_loading_behavior), wie der [Ladestatus von Symbolen während des Debuggens überprüft werden kann](#work-with-symbols-in-the-modules-window) und wie [Symboloptionen in Code festgelegt werden können](#compiler-symbol-options).

Eine ausführliche Erläuterung zu Symboldateien finden Sie in den folgenden Themen:

- [Grundlegendes zu Symboldateien und Symboleinstellungen in Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Warum müssen Debuggersymboldateien genau den Binärdateien entsprechen, mit denen sie erstellt wurden?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>Funktionsweise von Symboldateien

Die *PDB-Datei* enthält Debug- und Projekstatusinformationen, die die inkrementelle Verknüpfung einer Debugkonfiguration Ihrer App ermöglichen. Der Visual Studio-Debugger verwendet *PDB* -Dateien, um beim Debuggen zwei wichtige Informationen zu ermitteln:

* Den Namen der Quelldatei und die Zeilennummer, die in der Visual Studio-IDE angezeigt werden sollen.
* Wo in der App bei einem Breakpoint angehalten werden soll.

Symboldateien zeigen auch den Speicherort der Quelldateien und optional den Server an, von dem sie abgerufen werden sollen.

Der Debugger lädt nur *PDB* -Dateien, die genau mit den *PDB* -Dateien übereinstimmen, die beim Buildvorgang einer App erstellt wurden (d. h. die ursprünglichen *PDB* -Dateien oder Kopien davon). Diese [genaue Duplizierung](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) ist erforderlich, da sich das Layout von Apps ändern kann, auch wenn sich der Code selbst nicht geändert hat.

> [!TIP]
> Um Code außerhalb des Quellcodes Ihres Projekts zu debuggen, z. B. Windows-Code oder Code von Drittanbietern, den Ihr Projekt aufruft, müssen Sie den Speicherort der *PDB* -Dateien des externen Codes (und optional der Quelldateien) angeben, der genau mit den Builds in Ihrer App übereinstimmen muss.

## <a name="symbol-file-locations-and-loading-behavior"></a>Symboldateispeicherorte und Ladeverhalten

Wenn Sie ein Projekt in der Visual Studio-IDE debuggen, lädt der Debugger automatisch Symboldateien, die sich im Projektordner befinden.

> [!NOTE]
> Beim Debuggen von verwaltetem Code auf einem Remotegerät müssen sich alle Symbol Dateien entweder auf dem lokalen Computer oder an einem Speicherort befinden, der [in den Debuggeroptionen angegeben wird](#BKMK_Specify_symbol_locations_and_loading_behavior).

Der Debugger sucht auch an den folgenden Speicherorten nach Symboldateien:

1. Der Speicherort, der in der DLL-Datei oder der ausführbaren Datei ( *EXE-Datei* ) angegeben wird.

   Wenn Sie eine DLL-Datei oder eine *EXE* -Datei auf dem Computer erstellt haben, platziert der Linker standardmäßig den vollständigen Pfad und Dateinamen der zugehörigen *PDB* -Datei in der DLL- oder *EXE* -Datei. Der Debugger überprüft, ob die Symboldatei an diesem Speicherort vorhanden ist.

2. Der gleiche Ordner wie die DLL- oder *EXE* -Datei.

3. Alle Speicherorte, die in den Debuggeroptionen für Symboldateien angegeben werden. Informationen zum Hinzufügen und Aktivieren von Symboldateien finden Sie unter [Konfigurieren von Symbolspeicherorten und Ladeoptionen](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Ein beliebiger Symbolcacheordner.

   - Angegebenes Netzwerk-, Internet- oder lokale Symbolserver und Speicherorte, z. B. die Microsoft-Symbolserver, sofern ausgewählt. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kann Debugsymboldateien von Symbolservern herunterladen, die das `symsrv`-Protokoll implementieren. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) und die [Debugtools für Windows](/windows-hardware/drivers/debugger/index) sind zwei Tools, die Symbolserver verwenden können.

     Folgende Symbolserver können verwendet werden:

     **Öffentliche Microsoft-Symbolserver** : Um einen Absturz zu debuggen, der beim Aufruf einer System-DLL oder der Bibliothek eines Drittanbieters auftritt, benötigen Sie oftmals *PDB* -Systemdateien. *PDB* -Systemdateien enthalten Symbole für Windows-DLLs, *EXE* -Dateien und Gerätetreiber. Sie können Symbole für Windows-Betriebssysteme, MDAC, IIS, ISA und .NET von den öffentlichen Microsoft-Symbolservern abrufen.

     **Symbolserver auf einem internen Netzwerk oder auf Ihrem lokalen Computer** : Ihr Team oder Ihr Unternehmen kann Symbolserver für eigene Produkte und als Cache für Symbole aus externen Quellen erstellen. Sie haben möglicherweise einen Symbolserver auf dem eigenen Computer.

     **Symbolserver von Drittanbietern** : Drittanbieter von Windows-Anwendungen und Bibliotheken können Zugriff auf Symbolserver im Internet gewähren.

     > [!WARNING]
     > Wenn Sie einen anderen Symbolserver als die öffentlichen Microsoft-Symbolserver verwenden, vergewissern Sie sich, dass der Symbolserver und der zugehörige Pfad vertrauenswürdig sind. Da Symboldateien beliebigen ausführbaren Code enthalten können, können Sie möglicherweise Sicherheitsbedrohungen ausgesetzt sein.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Konfigurieren der Symboldateispeicherorte und Ladeoptionen

Auf der Seite **Extras** > **Optionen** > **Debuggen** > **Symbole** können Sie die folgende Aktionen ausführen:

- Angeben und Auswählen von Suchpfaden und Symbolservern für Microsoft, Windows oder Komponenten von Drittanbietern.
- Angeben von Modulen, für die der Debugger automatisch Symbole laden (oder nicht laden) soll.
- Ändern dieser Einstellungen, während Sie aktiv debuggen. Weitere Informationen finden Sie unter [Verwalten von Symbolen beim Debuggen](#manage-symbols-while-debugging).

**So geben Sie Symboldateispeicherorte und Ladeoptionen an:**

1. Öffnen Sie in Visual Studio **Extras** > **Optionen** > **Debuggen** > **Symbole** (oder **Debuggen** > **Optionen** > **Symbole** ).

2. Gehen Sie unter **Speicherorte für Symboldateien (.pdb)** folgendermaßen vor:
   - Aktivieren Sie das Kontrollkästchen, um die **Microsoft-Symbolserver** oder die **Symbolserver von NuGet.org** zu verwenden.

   - Zum Hinzufügen eines neuen Speicherorts für Symbolserver:
     1. Wählen Sie in der Symbolleiste das Symbol **+** aus.
     1. Geben Sie die URL (HTTP), die Netzwerkfreigabe oder den lokalen Pfad des Symbolservers oder des Symbolspeicherorts in das Textfeld ein. Durch Anweisungsvervollständigung wird Ihnen die Bestimmung des richtigen Formats erleichtert.

     ![Seite „Extras &#45; Optionen &#45; Debuggen &#45; Symbole“](media/dbg-options-symbols.gif "Seite „Extras &#45; Optionen &#45; Debuggen &#45; Symbole“")

     >[!NOTE]
     >Es wird nur der angegebene Ordner durchsucht. Sie müssen Einträge für alle Unterordner hinzufügen, die durchsucht werden sollen.

   - Zum Hinzufügen eines neuen Speicherorts für einen VSTS-Symbolserver:
     1. Wählen Sie auf der Symbolleiste das Symbol ![Extras &#47; Optionen &#47; Debuggen &#47; Symbole neuer Server](media/dbg_tools_options_foldersicon.png "Neues Serversymbol „Extras &#45; Optionen &#45; Debuggen &#45; Symbole“") aus.
     1. Wählen Sie im Dialogfeld **Verbindung mit VSTS-Symbolserver herstellen** einen der verfügbaren Symbolserver aus, und wählen Sie dann **Verbinden** aus.

   - Um die Ladereihenfolge für die Symbolspeicherorte zu ändern, verwenden Sie **STRG**+**NACH-OBEN** und **STRG**+**NACH-UNTEN** oder die Symbole **Pfeil-nach-oben** oder **Pfeil-nach-unten** .
   - Zum Bearbeiten einer URL oder eines Pfads doppelklicken Sie auf den Eintrag, oder wählen Sie ihn aus, und drücken Sie dann **F2** .
   - Um einen Eintrag zu entfernen, wählen Sie ihn aus, und wählen Sie dann das Symbol **-** aus.

3. (Optional) Um die Symbolladeleistung zu verbessern, geben Sie unter **Symbole in diesem Verzeichnis zwischenspeichern** einen lokalen Ordnerpfad ein, in den Symbolserver Symbole kopieren können.

   > [!NOTE]
   > Platzieren Sie den lokalen Symbolcache nicht in einem geschützten Ordner wie „C:\Windows“ oder einem Unterordner. Verwenden Sie stattdessen einen Ordner mit Lese-/Schreibzugriff.

   > [!NOTE]
   > Wenn für C++-Projekte die Umgebungsvariable `_NT_SYMBOL_PATH` festgelegt ist, wird der Wert überschrieben, der unter **Symbole in diesem Verzeichnis zwischenspeichern** festgelegt ist.

4. Geben Sie die Module an, die der Debugger aus **Speicherorte für Symboldateien (.pdb)** laden soll, wenn er gestartet wird.

   - Wählen Sie **Alle Module laden, sofern nicht ausgeschlossen** (die Standardeinstellung) aus, um alle Symbole für alle Module am Symboldatei-Speicherort zu laden, mit Ausnahme der Module, die Sie ausdrücklich ausschließen. Um bestimmte Module auszuschließen, wählen Sie **Ausgeschlossene Module angeben** aus, wählen Sie das Symbol **+** aus, geben Sie die Namen der auszuschließenden Module ein, und wählen Sie dann **OK** aus.

   - Wenn Sie nur angegebene Module aus dem Symboldatei-Speicherort laden möchten, wählen Sie **Nur angegebene Module laden** aus. Wählen Sie **Eingeschlossene Module angeben** aus, wählen Sie das Symbol **+** aus, geben Sie die Namen der einzuschließenden Module ein, und wählen Sie dann **OK** aus. Die Symboldateien für andere Module werden nicht geladen.

5. Klicken Sie auf **OK** .

## <a name="other-symbol-options-for-debugging"></a>Weitere Symboloptionen für das Debuggen

Sie können zusätzliche Symboloptionen unter **Extras** > **Optionen** > **Debuggen** > **Allgemein** (oder **Debuggen** > **Optionen** > **Allgemein** ) auswählen:

- **DLL-Exporte laden (nur native)**

  Lädt DLL‑Exporttabellen für C/C++. Weitere Informationen finden Sie unter [DLL-Exporttabellen](#use-dumpbin-exports). Das Lesen von DLL-Exportinformationen erfordert einen gewissen Mehraufwand, sodass das Laden von Exporttabellen standardmäßig deaktiviert ist. Sie können auch `dumpbin /exports` in einer C/C++-Buildbefehlszeile verwenden.

- **Debuggen auf Adressebene aktivieren** und **Disassemblierung anzeigen, wenn die Quelle nicht verfügbar ist**

  Zeigt immer die Disassemblierung an, wenn Quell- oder Symboldateien nicht gefunden werden.

  ![Optionen &#47; Debuggen &#47; Allgemeine Disassemblierungsoptionen](../debugger/media/dbg_options_general_disassembly_checkbox.png "Optionen &#47; Debuggen &#47; Allgemeine Disassemblierungsoptionen")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Quellserverunterstützung aktivieren**

  Verwendet den Quellserver, um das Debuggen einer Anwendung zu unterstützen, wenn auf dem lokalen Computer kein Quellcode vorhanden ist oder die *PDB* -Datei nicht mit dem Quellcode übereinstimmt. Der Quellserver nimmt Dateianforderungen entgegen und gibt die entsprechenden Dateien aus der Quellcodeverwaltung zurück. Der Quellserver wird mithilfe einer DLL mit dem Namen *srcsrv.dll* ausgeführt, um die *PDB* -Datei der App zu lesen. Die *PDB* -Datei enthält Verweise auf das Quellcoderepository sowie Befehle zum Abrufen von Quellcode aus dem Repository.

  Sie können die Befehle einschränken, die *srcsrv.dll* aus der *PDB* -Datei der App ausführen kann, indem Sie die zulässigen Befehle in einer Datei namens *srcsrv.ini* auflisten. Platzieren Sie die Datei *srcsrv.ini* in demselben Ordner wie *srcsrv.dll* und *devenv.exe* .

  >[!IMPORTANT]
  >In der *PDB* -Datei einer App können beliebige Befehle eingebettet sein. Deshalb sollten Sie sicherstellen, dass Sie der Datei *srcsrv.ini* nur die Befehle hinzufügen, die ausführt werden sollen. Beim Versuch, einen nicht in der Datei *srcsvr.ini* enthaltenen Befehl auszuführen, wird ein Bestätigungsdialogfeld geöffnet. Weitere Informationen finden Sie unter [Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Es wird keine Validierung für Befehlsparameter durchgeführt, seien Sie deshalb bei vertrauenswürdigen Befehlen vorsichtig. Wenn Sie z. B. *cmd.exe* in Ihrer Datei *srcsrv.ini* aufgeführt haben, könnte ein böswilliger Benutzer Parameter für *cmd.exe* angeben, die ein Risiko darstellen.

  Wählen Sie dieses Element und die gewünschten untergeordneten Elemente aus. Die Optionen **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen** und **Alle nicht vertrauenswürdigen Quellserverbefehle ohne Aufforderung ausführen** können die Sicherheitsrisiken erhöhen.

  ![Quellserveroptionen aktivieren](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Compilersymboloptionen

Wenn Sie ein Projekt aus der Visual Studio-IDE erstellen und die standardmäßige **Debug** -Buildkonfiguration verwenden, erstellen die Compiler für C++-Code und verwalteten Code die entsprechenden Symboldateien für Ihren Code. Sie können auch Compileroptionen im Code festlegen.

### <a name="net-options"></a>.NET-Optionen

Erstellen Sie die App mit **/debug** , um eine *PDB* -Datei zu erstellen. Sie können Anwendungsentwicklung mit **/debug:full** oder **/debug:pdbonly** erstellen. Beim Erstellen mit **/debug:full** wird debugfähiger Code generiert. Beim Erstellen mit **/debug:pdbonly** werden *PDB* -Dateien generiert, nicht jedoch das `DebuggableAttribute`-Attribut, das den JIT-Compiler darüber informiert, dass die Debuginformationen verfügbar sind. Verwenden Sie **/debug:pdbonly** , wenn Sie *PDB* -Dateien für einen Releasebuild generieren möchten, der nicht debugfähig sein soll. Weitere Informationen finden Sie unter [/debug (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) oder [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="cc-options"></a>C/C++-Optionen

- *VC\<x>.pdb* - und *\<project>PDB* -Dateien

  Eine *PDB* -Datei für C/C++ wird erstellt, wenn Sie [/ZI oder /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) für den Build verwenden. In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] wird die vom Compiler erstellte *PDB* -Datei durch die Option [/Fd](/cpp/build/reference/fd-program-database-file-name) benannt. Wenn Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein Projekt mithilfe der IDE erstellen, wird durch die Option **/Fd** eine *PDB* -Datei mit dem Namen *\<project>.pdb* erstellt.

  Wird Sie die C/C++-Anwendung mithilfe eines Makefile erstellen und **/ZI** oder **/Zi** ohne **/Fd** angegeben, erstellt der Compiler zwei *PDB* -Dateien:

  - *VC\<x>.pdb* , wobei *\<x>* die Version des Microsoft C++-Compilers darstellt, beispielsweise *VC11.pdb* .

    In der Datei *VC\<x>-pdb* werden alle Debuginformationen für die einzelnen Objektdateien gespeichert. Sie wird im selben Verzeichnis wie das Makefile des Projekts gespeichert. Wenn eine Objektdatei erstellt wird, mergt der C/C++-Compiler Debuginformationen in *VC\<x>.pdb* . Selbst wenn jede Quelldatei allgemeine Headerdateien, z. B. *\<windows.h>* enthält, werden die Typdefinitionen aus diesen Headerdateien nur ein Mal anstatt in jeder einzelnen Objektdatei gespeichert. Die eingefügten Informationen umfassen zwar Typinformationen, jedoch wie Funktionsdefinitionen keine Symbolinformationen.

  - *\<project>.pdb*

    Die Datei *\<project>.pdb* speichert alle Debuginformationen für die *EXE* -Datei des Projekts und befindet sich im Unterverzeichnis *\debug* . Die Datei *\<project>.pdb* enthält nicht nur die in *VC\<x>.pdb* gespeicherten Typinformationen, sondern die vollständigen Debuginformationen (einschließlich der Funktionsprototypen).

  Sowohl die Datei *VC\<x>.pdb* als auch die Datei *\<project>.pdb* ermöglicht inkrementelle Aktualisierungen. Der Linker bettet den Pfad zu den *PDB* -Dateien in die erstellte *EXE* - bzw. *DLL* -Datei ein.

- <a name="use-dumpbin-exports"></a>DLL-Exporttabellen

  Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Symbole sind für alle 32-Bit-System-DLLs verfügbar. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird.

  In der Ausgabe von `dumpbin /exports` werden die genauen Funktionsnamen angezeigt, einschließlich nicht alphanumerischer Zeichen. Die Anzeige genauer Funktionsnamen ist hilfreich, um einen Breakpoint für eine Funktion festzulegen, weil Funktionsnamen an anderer Stelle im Debugger abgeschnitten werden können. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).

### <a name="web-applications"></a>Webanwendungen

Legen Sie die Datei *web.config* Ihrer ASP.NET-Anwendung auf den Debugmodus fest. Der Debugmodus veranlasst ASP.NET zum Erstellen von Symbolen für dynamisch generierte Dateien und ermöglicht dem Debugger das Anfügen an die ASP.NET-Anwendung. Visual Studio legt dies beim Starten des Debugvorgangs automatisch fest, wenn Sie das Projekt anhand der Webprojekte-Vorlage erstellt haben.

## <a name="manage-symbols-while-debugging"></a>Verwalten von Symbolen beim Debuggen

Sie können die Fenster **Module** , **Aufrufliste** , **Lokal** , **Auto** oder ein beliebiges **Überwachungsfenster** verwenden, um Symbole zu laden oder Symboloptionen beim Debuggen zu ändern. Weitere Informationen erhalten Sie unter [Informieren Sie sich darüber, wie der Debugger an Ihre App angefügt wird](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="work-with-symbols-in-the-modules-window"></a>Arbeiten mit Symbolen im Fenster „Module“

Während des Debuggens zeigt das Fenster **Module** die Codemodule, die der Debugger als Benutzercode oder eigenen Code behandelt, und ihren Symbolladestatus an. Sie können im Fenster **Module** auch den Status von Symbolladevorgängen überwachen, Symbole laden und Symboloptionen ändern.

**So überwachen oder ändern Sie Symbolspeicherorte oder -optionen beim Debuggen:**

1. Wählen Sie zum Öffnen des Fensters **Module** während des Debuggens **Debuggen** > **Windows** > **Module** aus.
1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf die Überschriften **Symbolstatus** oder **Symboldatei** oder auf ein beliebiges Modul.
1. Wählen Sie im Kontextmenü eine der folgenden Optionen aus:

|Option|Beschreibung|
|------------|-----------------|
|**Symbole laden**|Wird für Module mit übersprungenen, nicht gefundenen oder nicht geladenen Symbolen angezeigt. Lädt Symbole aus den Speicherorten, die auf der Seite **Optionen** > **Debuggen** > **Symbole** angegeben werden. Wenn die Symboldatei nicht gefunden oder nicht geladen wird, wird der **Datei-Explorer** gestartet, damit Sie einen neuen Speicherort für die Suche angeben können.|
|**Symbolladeinformationen**|Zeigt den Speicherort einer geladenen Symboldatei oder die Speicherorte an, die durchsucht wurden, wenn der Debugger die Datei nicht finden kann.|
|**Symboleinstellungen**|Öffnet die Seite **Optionen** > **Debuggen** > **Symbole** , auf der Sie Symbolspeicherorte bearbeiten und hinzufügen können.|
|**Immer automatisch laden**|Fügt die ausgewählte Symboldatei der Liste der Dateien hinzu, die automatisch vom Debugger geladen werden.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Verwenden der Seite „Keine Symbole geladen/Keine Quelle geladen“

Es gibt mehrere Methoden, damit der Debugger im Code unterbrochen wird, der keine verfügbaren Symbol- oder Quelldateien aufweist:

- Einzelschritt.
- Unterbrechen im Code von einem Breakpoint oder einer Ausnahme.
- Wechseln zu einem anderen Thread.
- Ändern des Stapelrahmens durch Doppelklicken auf einen Rahmen im Fenster **Aufrufliste** .

Wenn dies geschieht, wird im Debugger die Seite **Keine Symbole geladen** oder **Keine Quelle geladen** angezeigt, auf der Sie die erforderlichen Symbole oder die Quelle suchen und laden können.

 ![Seite „Keine Symbole geladen“](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**So verwenden Sie die Seite „Keine Symbole geladen“, um fehlende Symbole zu suchen und zu laden:**

- Um den Suchpfad zu ändern, wählen Sie einen nicht ausgewählten Pfad aus, oder wählen Sie **Neuer Pfad** oder **Neuer VSTS-Pfad** aus, und geben Sie einen neuen Pfad ein, oder wählen Sie ihn aus. Wählen Sie **Laden** aus, um die Pfade erneut zu suchen und die Symboldatei zu laden, sofern sie gefunden wurde.
- Wählen Sie **Nach \<executable-name> suchen** aus, um alle Symboloptionen zu überschreiben und einen Wiederholungsversuch für die Suchpfade auszuführen. Die Symboldatei wird geladen, sofern sie gefunden wird, oder der **Datei-Explorer** wird geöffnet, damit Sie die Symboldatei manuell auswählen können.
- Um die Seite **Optionen** > **Debuggen** > **Symbole** zu öffnen, wählen Sie **Symboleinstellungen ändern** aus.
- Um die Disassemblierung einmalig in einem neuen Fenster anzuzeigen, wählen Sie **Disassemblierung anzeigen** aus, oder wählen Sie das **Dialogfeld „Optionen“** aus, um die Option festzulegen, die Disassemblierung immer anzuzeigen, wenn Quell- oder Symboldateien nicht gefunden wurden.
- Um die durchsuchten Speicherorte und das Ergebnis anzuzeigen, erweitern Sie **Symbolladeinformationen** .

Wenn der Debugger die *PDB* -Datei findet, nachdem Sie eine der Optionen ausgeführt haben, und die Quelldatei anhand der Informationen in der *PDB* -Datei abrufen kann, zeigt er die Quelle an. Andernfalls wird eine Seite **Keine Quelle geladen** angezeigt, die das Problem beschreibt und Links zu Aktionen bereitstellt, die das Problem möglicherweise beheben.

**So fügen Sie einer Projektmappe Quelldateisuchpfade hinzu:**

Sie können die Speicherorte angeben, an denen der Debugger nach Quelldateien sucht, und bestimmte Dateien aus der Suche ausschließen.

1. Wählen Sie die Projektmappe im **Projektmappen-Explorer** aus, und wählen Sie dann das Symbol **Eigenschaften** aus, drücken Sie **ALT**+**EINGABETASTE** , oder klicken Sie mit der rechten Maustaste und wählen dann **Eigenschaften** aus.

1. Wählen Sie **Quelldateien debuggen** aus.

1. Geben Sie unter **Verzeichnisse mit Quellcode** Quellcodespeicherorte für die Suche ein, oder wählen Sie diese aus. Verwenden Sie das Symbol **Neue Zeile** , um weitere Speicherorte hinzuzufügen, die Pfeilsymbole **NACH-OBEN** und **NACH-UNTEN** , um Speicherorte neu anzuordnen, oder das Symbol **X** , um sie zu löschen.

   >[!NOTE]
   >Der Debugger durchsucht nur das angegebene Verzeichnis. Sie müssen Einträge für alle Unterverzeichnisse hinzufügen, die durchsucht werden sollen.

1. Geben Sie unter **Nach folgenden Quelldateien nicht suchen** die Namen der Quelldateien ein, die aus der Suche ausgeschlossen werden sollen.

1. Wählen Sie **OK** oder **Anwenden** aus.

## <a name="see-also"></a>Siehe auch
- [Grundlegendes zu Symboldateien und Symboleinstellungen in Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [.NET remote symbol loading changes in Visual Studio 2012 and 2013 (Änderungen am Remoteladen von Symboldateien mit .NET in Visual Studio 2012 und 2013)](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)