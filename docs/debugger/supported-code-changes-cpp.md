---
title: Unterstützte Codeänderungen (C++) | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, welche Codeänderungen unterstützt werden, wenn Sie das Feature „Bearbeiten und fortfahren“ beim Debuggen eines C++-Projekts in Visual Studio verwenden.
ms.custom: SEO-VS-2020
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: d000d2757321701c2e14427c6bbb4d3e4164d26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876302"
---
# <a name="supported-code-changes-c"></a>Unterstützte Codeänderungen (C++)
Mit „Bearbeiten und Fortfahren“ für C++-Projekte können die meisten Arten von Codeänderungen behandelt werden. Einige Änderungen können während der Programmausführung jedoch nicht übernommen werden. Um diese Änderungen zu übernehmen, müssen Sie die Ausführung anhalten und eine neue Version des Codes erstellen.

 Weitere Informationen zur Verwendung von „Bearbeiten und Fortfahren“ für C++ in Visual Studio finden Sie unter [Bearbeiten und Fortfahren (C++)](../debugger/edit-and-continue-visual-cpp.md).

## <a name="requirements"></a><a name="BKMK_Requirements"></a> Anforderungen
### <a name="build-settings-project--properties"></a>Buildeinstellungen („Projekt“ > „Eigenschaften“):
  1. **„C/C++“ > „Allgemein“ > „Debuginformationsformat“** : Programmdatenbank für Bearbeiten und Fortfahren (`/ZI`)
  2. **„C/C++“ > „Codegenerierung“ > „Minimale Neuerstellung aktivieren“** : Ja (`/Gm`)
  3. **„Linker“ > „Allgemein“ > „Inkrementelles Verknüpfen aktivieren“** : Ja (`/INCREMENTAL`)

     Bei nicht kompatiblen Linker-Einstellungen (beispielsweise `/SAFESEH` oder `/OPT:`) tritt während des Buildvorgangs die Warnung _LNK4075_ auf.  
     Ein Beispiel: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Debuggereinstellungen („Debuggen“ > „Optionen“ > „Allgemein“):
  - Natives Bearbeiten und Fortfahren aktivieren

     Bei Verwendung nicht kompatibler Compiler- oder Linker-Einstellungen tritt beim Bearbeiten und Fortfahren ein Fehler auf.  
     Ein Beispiel: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Nicht unterstützte Änderungen
 Folgende C-/C++-Änderungen können nicht im Rahmen einer Debugsitzung angewendet werden. Wenn Sie eine dieser Änderungen vornehmen und anschließend versuchen, die Codeänderungen zu übernehmen, wird im Fenster **Ausgabe** eine Warnung oder eine Fehlermeldung angezeigt.

- Die meisten Änderungen an globalen oder statischen Daten.

- Änderungen an ausführbaren Dateien, die von einem anderen Computer kopiert und nicht lokal erstellt wurden.

- Änderungen an Datentypen, die das Layout eines Objekts beeinflussen (z. B. Datenmember einer Klasse).

- Hinzufügen von mehr als 64 KB neuen Codes oder neuer Daten.

- Hinzufügen von Variablen, die an einer Stelle vor dem Anweisungszeiger einen Konstruktor benötigen.

- Änderungen, die sich auf Code auswirken, der eine Laufzeitinitialisierung benötigt.

- Das Hinzufügen von Ausnahmehandlern in bestimmten Instanzen.

- Änderungen an Ressourcendateien.

- Änderungen an Code in schreibgeschützten Dateien.

- Änderungen am Code ohne entsprechende PDB-Datei.

- Änderungen an Code ohne Objektdatei.

* Ändern von Lambdas, die:
  - über einen statischen oder globalen Member verfügen.
  - an eine Funktion vom Typ „std::function“ übergeben werden. Dies führt zu einer echten ODR-Verletzung und hat den Fehler C1092 zur Folge.

- Von "Bearbeiten und Fortfahren" werden keine statischen Bibliotheken aktualisiert. Wenn Sie eine Änderung an einer statischen Bibliothek vornehmen, wird die Ausführung ohne Warnung mit der alten Version fortgeführt.

## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Nicht unterstützte Szenarien
 "Bearbeiten und Fortfahren" steht für C/C++ in den folgenden Debugszenarien nicht zur Verfügung:

- Debuggen von systemeigenen Apps, die mit [/zo (Optimiertes Debuggen verbessern)](/cpp/build/reference/zo-enhance-optimized-debugging)kompiliert sind

- Debuggen von UWP-Apps oder -Komponenten in Versionen von Visual Studio vor Visual Studio 2015 Update 1. Ab Visual Studio 2015 Update 1 können Sie „Bearbeiten und Fortfahren“ in C++-UWP-Apps und DirectX-Apps verwenden, da jetzt die Compileroption `/ZI` mit der Option `/bigobj` unterstützt wird. Sie können „Bearbeiten und Fortfahren“ auch mit Binärdateien verwenden, die mit dem `/FASTLINK` -Schalter unterstützt wird.

- Debuggen von Store-Apps der Version 8/8.1. In diesen Projekten werden das VC 120-Toolset und die C-/C++-Option `/bigobj` verwendet. „Bearbeiten und Fortfahren“ mit `/bigobj` wird nur im VC 140-Toolset unterstützt.

- Debuggen unter Windows 98.

- Debuggen im gemischten Modus (systemeigen/verwaltet).

- Debuggen von JavaScript.

- SQL-Debuggen.

- Debuggen einer Dumpdatei.

- Bearbeiten von Code nach einer nicht behandelten Ausnahme, wenn die Option **Aufrufliste für unbehandelte Ausnahmen entladen** nicht aktiviert ist.

- Debuggen einer App über **Anfügen an** , anstatt die App durch Auswählen von **Start** im Menü **Debuggen** auszuführen.

- Debuggen von optimiertem Code.

- Debuggen einer alten Version des Codes, wenn eine neue Version aufgrund von Buildfehlern nicht erstellt werden konnte.

- Verwenden eines benutzerdefinierten Compilerpfads (*cl.exe*). Aus Sicherheitsgründen wird von Visual Studio bei der Neukompilierung einer Datei während des Bearbeitens und Fortfahrens immer der installierte Compiler verwendet. Bei Verwendung eines benutzerdefinierten Compilerpfads (beispielsweise über eine benutzerdefinierte Variable vom Typ `$(ExecutablePath)` in der Datei `*.props`) wird eine Warnung angezeigt, und Visual Studio greift auf den installierten Compiler der gleichen Version/Architektur zurück.

- FASTBuild-Buildsystem. Da FASTBuild gegenwärtig nicht mit der Compileroption „Minimale Neuerstellung aktivieren (`/Gm`)“ kompatibel ist, wird „Bearbeiten und Fortfahren“ nicht unterstützt.

- Legacyarchitekturen/VC-Toolsets. Bei Verwendung des VC 140-Toolsets wird „Bearbeiten und Fortfahren“ vom Standarddebugger sowohl für x86- als auch für x64-Anwendungen unterstützt. Von älteren Toolsets werden nur x86-Anwendungen unterstützt. Von Toolsets vor VC 120 muss der Legacydebugger verwendet werden. Aktivieren Sie hierzu unter _„Debuggen“ > „Optionen“ > „Allgemein“_ die Option „Systemeigenen Kompatibilitätsmodus verwenden“, um „Bearbeiten und Fortfahren“ verwenden zu können.

## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Einschränkungen für Verknüpfungen

### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Optionen des Linkers, durch die "Bearbeiten und Fortfahren" deaktiviert wird
 Die folgenden Optionen des Linkers deaktivieren Bearbeiten und Fortfahren:

- Durch die Einstellung **/OPT:REF**, **/OPT:ICF** oder **/INCREMENTAL:NO** wird Bearbeiten und Fortfahren deaktiviert. Folgende Warnung wird angezeigt:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- Durch Festlegen von **/ORDER**, **/RELEASE** oder **/FORCE** wird „Bearbeiten und Fortfahren“ deaktiviert und folgende Warnung angezeigt:  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- Durch das Festlegen einer beliebigen Option, die die Erstellung einer Programmdatenbankdatei (.pdb) verhindert, wird Bearbeiten und Fortfahren deaktiviert, wobei keine spezifische Warnung ausgegeben wird.

### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> Automatisches Neuverknüpfen von Einschränkungen
 In der Standardeinstellung wird durch Bearbeiten und Fortfahren das Programm am Ende der Debugsitzung neu gebunden, um eine aktuelle ausführbare Datei zu erstellen.

 Bearbeiten und Fortfahren kann das Programm nicht erneut binden, wenn Sie an einer anderen Position als der der ursprünglichen Erstellung debuggen. Ihnen wird in einer Meldung mitgeteilt, dass Sie manuell neu erstellen müssen.

 Bearbeiten und Fortfahren erstellt keine statischen Bibliotheken neu. Wenn Sie eine statische Bibliothek mit "Bearbeiten und Fortfahren" ändern, müssen Sie die Bibliothek manuell neu erstellen und die Apps anschließend mit der neuen Bibliothek erneut verknüpfen.

 Durch Bearbeiten und Fortfahren können keine benutzerdefinierten Schritte aufgerufen werden. Wenn das Programm auf benutzerdefinierten Buildschritten beruht, können Sie es manuell neu erstellen, damit benutzerdefinierte Buildschritte aufgerufen werden können. In diesem Fall können Sie die erneute Bindung nach Ausführen von Bearbeiten und Fortfahren deaktivieren. Dies gewährleistet, dass Sie aufgefordert werden, diese manuell neu zu erstellen.

 **So deaktivieren Sie das erneute Binden nach "Bearbeiten und Fortfahren"**

1. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.

2. Öffnen Sie im Dialogfeld **Optionen** den Knoten **Debugging** , und wählen Sie den Knoten **Bearbeiten und Fortfahren** aus.

3. Deaktivieren Sie das Kontrollkästchen **Codeänderungen nach dem Debuggen erneut binden** .

## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_header_limitations"></a> Einschränkungen für vorkompilierte Header
 Durch Bearbeiten und Fortfahren werden vorkompilierte Header standardmäßig im Hintergrund geladen und verarbeitet, um die Verarbeitung von Codeänderungen zu beschleunigen. Zum Laden vorkompilierter Header muss physischer Speicher belegt werden. Daher können beim Kompilieren auf einem Computer mit begrenztem Arbeitsspeicher Probleme auftreten. Sie können feststellen, ob möglicherweise ein solches Problem besteht, indem Sie mithilfe des Windows Task-Managers den während des Debuggens verfügbaren physischen Speicher bestimmen. Wenn dabei die Größe der vorkompilierten Header überschritten wird, kann Bearbeiten und Fortfahren problemlos ausgeführt werden. Wenn der Speicherplatz geringer als die vorkompilierten Header ist, können Sie das Laden von vorkompilierten Headern im Hintergrund durch Bearbeiten und Fortfahren verhindern.

 **So deaktivieren Sie das Laden vorkompilierter Header im Hintergrund für "Bearbeiten und Fortfahren"**

1. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**.

2. Öffnen Sie im Dialogfeld **Optionen** den Knoten **Debugging** , und wählen Sie den Knoten **Bearbeiten und Fortfahren** aus.

3. Deaktivieren Sie das Kontrollkästchen **Präkompilierung zulassen** .

## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_attribute_limitations"></a> Einschränkungen für IDL-Attribute
 "Bearbeiten und Fortfahren" unterstützt nicht das Neugenerieren von IDL-Dateien (Interface Definiton Language). Aus diesem Grund werden Änderungen an IDL-Attributen während des Debuggens nicht widergespiegelt. Wenn Sie die Ergebnisse von Änderungen an IDL-Attributen anzeigen möchten, müssen Sie das Debuggen beenden und die App neu erstellen. "Bearbeiten und Fortfahren" erzeugt keinen Fehler bzw. keine Fehlermeldung, wenn IDL-Attribute geändert wurden. Weitere Informationen finden Sie unter [IDL-Attribute](/cpp/windows/idl-attributes).

## <a name="diagnosing-issues"></a><a name="BKMK_Diagnosing_issues"></a> Diagnostizieren von Problemen
 Sollte für Ihr Szenario keine der oben genannten Bedingungen zutreffen, können Sie durch Festlegen des folgenden DWORD-Registrierungswerts weitere Details sammeln:
 1. Öffnen Sie eine Developer-Eingabeaufforderung.
 2. Führen Sie den folgenden Befehl aus:  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 Wenn Sie diesen Wert zu Beginn einer Debugsitzung festlegen, werden im Bereich **Ausgabefenster** > **Debuggen** ausführliche Protokollierungsinformationen der verschiedenen Komponenten von „Bearbeiten und Fortfahren“ ausgegeben.

## <a name="see-also"></a>Siehe auch
- [Bearbeiten und Fortfahren (C++)](../debugger/edit-and-continue-visual-cpp.md)
