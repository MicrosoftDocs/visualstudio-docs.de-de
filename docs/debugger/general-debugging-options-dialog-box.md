---
title: Allgemein, Debuggen, Dialogfeld „Optionen“ | Microsoft-Dokumentation
description: Legen Sie die Visual Studio-Debuggeroptionen so fest, dass Ihre Anforderungen für das Debuggen erfüllt sind. Sie können das Verhalten bei Unterbrechungen, die Debugebenen, das Anzeigeverhalten und vieles mehr konfigurieren.
ms.custom: SEO-VS-2020
ms.date: 06/04/2020
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 928499957ca90dda718f324827968f10cbb3a141
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870570"
---
# <a name="general-debugging-options"></a>Allgemeine Optionen zum Debuggen

Um Visual Studio-Debuggeroptionen festzulegen, wählen Sie **Extras** > **Optionen** aus, und aktivieren oder deaktivieren Sie unter **Debuggen** die Kontrollkästchen neben den Optionen **Allgemein**. Sie können alle Standardeinstellungen über **Extras** > **Einstellungen importieren und exportieren** > **Alle Einstellungen zurücksetzen** zurücksetzen. Wenn Sie einen Teil der Einstellungen zurücksetzen möchten, speichern Sie die Einstellungen im **Assistenten zum Importieren und Exportieren von Einstellungen**, bevor Sie die Änderungen vornehmen, die Sie testen möchten, und importieren Sie die gespeicherten Einstellungen anschließend.

Sie können die folgenden Optionen unter **Allgemein** festlegen:

**Vor Löschen aller Haltepunkte fragen**: Erfordert zum Ausführen des Befehls **Alle Haltepunkte löschen** die Bestätigung.

**Alle Prozesse anhalten, wenn ein Prozess anhält**: Hält im Falle einer Unterbrechung alle Prozesse gleichzeitig an, an die der Debugger angefügt ist.

**Bei Anwendungsdomänengrenzen oder verwaltete/native Übergänge überschreitenden Ausnahmen unterbrechen**: Beim Debuggen im verwalteten oder gemischten Modus kann die Common Language Runtime die Ausnahmen auffangen, die die Grenzen zwischen Anwendungsdomänen oder Grenzen zwischen verwaltetem und systemeigenem Code überschreiten, wenn die folgenden Bedingungen erfüllt sind:

1. Wenn in nativem Code verwalteter Code mit COM-Interop aufgerufen wird und im verwalteten Code eine Ausnahme ausgelöst wird. Weitere Informationen finden Sie unter [Einführung in COM-Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Wenn verwalteter Code, der in der Anwendungsdomäne 1 ausgeführt wird, verwalteten Code in der Anwendungsdomäne 2 aufruft und der Code in Anwendungsdomäne 2 eine Ausnahme auslöst. Siehe [Programmieren mit Anwendungsdomänen](/dotnet/articles/framework/app-domains/index).

3. Wenn im Code eine Funktion mit Reflexion aufgerufen wird und diese Funktion eine Ausnahme auslöst. Weitere Informationen finden Sie unter [Reflexion](/dotnet/framework/reflection-and-codedom/reflection).

Unter den Bedingungen 2 und 3 wird die Ausnahme gelegentlich von verwaltetem Code in `mscorlib` und nicht von der Common Language Runtime aufgefangen. Diese Option beeinträchtigt nicht das Unterbrechen bei von `mscorlib` aufgefangenen Ausnahmen.

**Debugging auf Adressebene aktivieren**: Aktiviert erweiterte Funktionen für das Debuggen auf Adressebene (das Fenster **Disassembly**, das Fenster **Register** und Adresshaltepunkte).

- **Disassembly anzeigen, wenn die Quelle nicht verfügbar ist**:   Zeigt automatisch das Fenster **Disassembly** an, wenn Sie Code debuggen, für den der Quellcode nicht verfügbar ist.

**Haltepunktfilter aktivieren**: Mit dieser Option können Sie Filter an Haltepunkten festlegen, damit diese nur für bestimmte Prozesse, Threads oder Computer gelten.

**Die neue Ausnahmen-Hilfe verwenden**: Aktiviert die Ausnahmen-Hilfe, die den Ausnahme-Assistenten ersetzt. (Die Ausnahmen-Hilfe wird ab Visual Studio 2017 unterstützt.)

> [!NOTE]
> Bei verwaltetem Code wurde diese Option früher als **Ausnahme-Assistenten aktivieren** bezeichnet.

**Nur eigenen Code aktivieren**: Der Debugger zeigt nur Benutzercode („Mein Code“) an und durchläuft ihn schrittweise, während systemeigener und sonstiger Code, der optimiert ist oder keine Debugsymbole aufweist, ignoriert wird.

- **Warnen, wenn beim Starten kein Benutzercode ausgeführt wird (nur verwaltet)** :   Wenn beim Debuggen am Anfang "Nur mein Code" aktiviert ist, warnt diese Option Sie, wenn kein Benutzercode ("Eigener Code") vorhanden ist.

**Durchlaufen des .NET Framework-Quellcodes aktivieren**: Ermöglicht es dem Debugger, die .NET Framework-Quelle schrittweise auszuführen. Wenn Sie diese Option aktivieren, wird „Nur eigenen Code“ automatisch deaktiviert. .NET Framework-Symbole werden an einen Cachespeicherort heruntergeladen. Ändern Sie den Cachespeicherort auf dem Dialogfeld **Optionen** unter der Kategorie **Debuggen** der Seite **Symbole**.

**Eigenschaften und Operatoren überspringen (nur verwaltet)** : Verhindert, dass der Debugger Eigenschaften und Operatoren in verwaltetem Code schrittweise ausführt.

**Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**: Aktiviert die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen in Variablenfenstern und im Dialogfeld **Schnellüberwachung**.

- **Zeichenfolgenkonvertierungsfunktion für Objekte in Variablenfenstern aufrufen (nur C# und JavaScript)** : Führt einen impliziten Zeichenkonvertierungsaufruf beim Auswerten von Objekten in Variablenfenstern aus. Dieses Ergebnis wird nicht als Typname, sondern als Zeichenfolge angezeigt. Gilt nur für Debuggen in C#-Code. Diese Einstellung kann durch das Attribut „DebuggerDisplay“ außer Kraft gesetzt werden (siehe [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)).

**Quellserverunterstützung aktivieren**: Weist den Visual Studio-Debugger an, die Quelldateien aus den Quellservern abzurufen, die das SrcSrv-Protokoll (`srcsrv.dll`) implementieren. Team Foundation Server und die Debugtools für Windows sind zwei Quellserver, die das Protokoll implementieren. Weitere Informationen über das Setup von SrcSrv finden Sie in der Dokumentation zu [SrcSrv](/windows-hardware/drivers/debugger/srcsrv). Zusätzliche Informationen finden Sie unter [Angeben von Symboldateien (PDB) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Da das Lesen von *PDB*-Dateien beliebigen Code in den Dateien ausführen kann, vergewissern Sie sich, dass Sie dem Server vertrauen können.

- **Diagnosemeldungen für Quellserver im Ausgabefenster drucken**:   Wenn die Quellserverunterstützung aktiviert ist, aktiviert diese Einstellung die diagnostische Anzeige.

- **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen**:   Wenn die Quellserverunterstützung aktiviert ist, überschreibt diese Einstellung das Standardverhalten beim Nichtabrufen von Quellen für teilweise vertrauenswürdige Assemblys.

- **Alle nicht vertrauenswürdigen Quellserverbefehle ohne Aufforderung ausführen**:   Wenn die Quellserverunterstützung aktiviert ist, setzt diese Einstellung das Standardverhalten der Eingabeaufforderung bei der Ausführung eines nicht vertrauenswürdigen Befehls außer Kraft.

**Quelllinkunterstützung aktivieren**: Weist den Visual Studio-Debugger an, Quelldateien für *PDB*-Dateien herunterzuladen, die Quelllinkinformationen enthalten. Weitere Informationen zu Quelllinks finden Sie in der [Quelllinkspezifikation](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Da Quelllinkdateien über HTTP oder HTTPS herunterlädt, stellen Sie sicher, dass Sie der *PDB*-Datei vertrauen.

- **Für alle Quellenlinkanforderungen Fallback auf die Authentifizierung über die Git-Anmeldeinformationsverwaltung durchführen**:   Wenn die Quelllinkunterstützung aktiviert ist und bei der Authentifizierung einer Quelllinkanforderung ein Fehler auftritt, ruft Visual Studio den Git Credential Manager auf.

**Bei Haltepunkten und aktueller Anweisung gesamte Quellzeile markieren (nur C++)** : Wenn der Debugger einen Haltepunkt oder die aktuelle Anweisung hervorhebt, wird die ganze Zeile hervorgehoben.

**Quelldateien müssen exakt mit der Originalversion übereinstimmen**: Fordert den Debugger auf, zu prüfen, ob die Quelldatei mit der Version des Quellcodes übereinstimmt, mit dem die ausführbare Datei erstellt wurde, die Sie debuggen. Wenn die Version nicht übereinstimmt, werden Sie aufgefordert, eine übereinstimmende Quelle zu suchen. Wenn keine übereinstimmende Quelle gefunden wird, wird der Quellcode während des Debuggens nicht angezeigt.

**Gesamten Text aus Ausgabefenster an das Direktfenster umleiten**: Sendet alle Debuggermeldungen, die normalerweise im **Ausgabefenster** angezeigt werden, an das **Direktfenster**.

**Unformatierte Struktur von Objekten in Variablenfenstern anzeigen**: Deaktiviert alle Anpassungen von Objektstrukturansichten. Weitere Informationen zum Anzeigen von Anpassungen finden Sie unter [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-managed-objects.md).

**JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)** : Deaktiviert die JIT-Optimierung von verwaltetem Code, wenn ein Modul geladen und JIT kompiliert wird, während der Debugger angefügt ist. Durch das Deaktivieren der Optimierung kann das Debuggen einiger Probleme vereinfacht werden, allerdings auf Kosten der Leistung. Die Verwendung von "Nur mein Code" bei unterdrückter JIT-Optimierung kann dazu führen, dass Nichtbenutzercode als Benutzercode (Nur eigenen Code) angezeigt wird. Weitere Informationen finden Sie unter [JIT-Optimierung und -Debuggen](../debugger/jit-optimization-and-debugging.md).

**JavaScript-Debugging für ASP.NET aktivieren (Chrome, Microsoft Edge und IE)** : Aktiviert den Skriptdebugger für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie sich möglicherweise beim Browser anmelden, um Chrome-Erweiterungen zu aktivieren, die Sie installiert haben. Deaktivieren Sie diese Option, um zum Legacy-Verhalten zurückzukehren.

::: moniker range=">= vs-2019"
**Verwendung des JavaScript-Debuggers mit mehreren Zielen zum Debuggen von JavaScript in anwendbaren Zielen aktivieren (erfordert Neustart des Debuggens)** Ermöglicht die gleichzeitige Verbindung mit dem Browser und dem Back-End, sodass Sie Ihren im Client und auf dem Server ausgeführten Code direkt im Editor debuggen können.
::: moniker-end

**DLL-Exporte laden (nur native)** : Lädt DLL‑Exporttabellen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.

Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](/cpp/build/reference/dash-exports).

**Diagramm mit parallelen Stapeln von unten nach oben anzeigen**: Steuert die Richtung, in der Stapel im Fenster **Parallele Stapel** angezeigt werden.

**Ausnahmen für den GPU-Speicherzugriff ignorieren, wenn der Wert durch die geschriebenen Daten nicht geändert wurde**: Ignoriert Racebedingungen, die während des Debuggens erkannt wurden, wenn sich die Daten nicht geändert haben. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md).

**Verwalteten Kompatibilitätsmodus verwenden**: Ersetzt die Standarddebug-Engine durch eine Legacyversion, um die folgenden Szenarien zu ermöglichen:

- Sie verwenden eine andere .NET-Sprache als C#, Visual Basic oder F#, die eine eigene Ausdrucksauswertung bereitstellt (dies schließt C++/CLI mit ein).

- Sie möchten „Bearbeiten und Fortfahren“ für C++-Projekte beim Debuggen im gemischten Modus aktivieren.

> [!NOTE]
> Durch Auswählen des verwalteten Kompatibilitätsmodus werden einige Funktionen deaktiviert, die nur in der standardmäßigen Debug-Engine implementiert werden. Die Legacy-Debug-Engine wurde in Visual Studio 2012 ersetzt.

::: moniker range="vs-2017"
**Die älteren C#- and VB-Ausdrucksauswertungen verwenden**: Der Debugger verwendet anstelle der Visual Studio 2015 Roslyn-basierten Ausdrucksauswertungen die Visual Studio 2013 C# oder Visual Basic-Ausdrucksauswertungen.
::: moniker-end

**Warnen, wenn benutzerdefinierte Debugger für die Anzeige potenziell unsicherer Prozesse verwendet werden (nur verwaltet)** : Visual Studio warnt Sie bei Verwendung einer benutzerdefinierten Debuggerschnellansicht, die im zu debuggenden Prozess Code ausführt, da es sich um unsicheren Code handeln könnte.

**Debugging-Heapzuweisung von Windows verwenden (nur nativ)** : Aktiviert den Debugheap von Windows, um die Heapdiagnose zu verbessern. Das Aktivieren dieser Option wirkt sich auf die Debugleistung aus.

**UI-Debugtools für XAML aktivieren**: Die Fenster „Visuelle Echtzeitstruktur“ und „Echtzeit-Eigenschaften-Explorer“ werden angezeigt, wenn Sie mit dem Debuggen eines unterstützten Projekttyps beginnen (**F5**). Weitere Informationen finden Sie unter [Überprüfen von XAML-Eigenschaften beim Debuggen](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Voransicht für ausgewählte Elemente in der visuellen Echtzeitstruktur anzeigen**:   Das XAML-Element, dessen Kontext ausgewählt ist, ist auch im Fenster **Visuelle Echtzeitstruktur** ausgewählt.

- **Laufzeittools in Anwendung anzeigen**: Zeigt die Befehle für **Visuelle Echtzeitstruktur** auf einer Symbolleiste im Hauptfenster der XAML-Anwendung an, die das Debuggen durchläuft. Diese Option wurde in Visual Studio 2015 Update 2 eingeführt.

- **XAML Hot Reload aktivieren**: Ermöglicht Ihnen die Verwendung des XAML Hot Reload-Features mit XAML-Code, wenn Ihre App ausgeführt wird. (Dieses Feature wurde zuvor als „Bearbeiten und Fortfahren – XAML“ bezeichnet.)

::: moniker range=">= vs-2019" 
- **Nur meine XAML aktivieren**: Ab Visual Studio 2019, Version 16.4, zeigt die **visuelle Echtzeitstruktur** standardmäßig nur XAML-Code an, der als Benutzercode klassifiziert ist. Wenn Sie diese Option deaktivieren, wird der gesamte generierte XAML-Code im Tool angezeigt.

- **Bei Auswahl eines Elements Auswahlmodus deaktivieren**: Ab Visual Studio 2019, Version 16.4, wird die Elementauswahlschaltfläche der App-Symbolleiste (**Auswahl aktivieren**) deaktiviert, wenn ein Element ausgewählt wird. Wenn Sie diese Option deaktivieren, bleibt die Elementauswahl aktiviert, bis Sie erneut auf die Schaltfläche der App-Symbolleiste klicken.

- **XAML Hot Reload beim Speichern des Dokuments anwenden** Ab Visual Studio 2019 Version 16.6 wird beim Speichern Ihres Dokuments XAML Hot Reload angewendet.

::: moniker-end

**Diagnosetools beim Debuggen aktivieren**: Das Fenster **Diagnosetools** wird während des Debuggens angezeigt.

**PerfTip für verstrichene Zeit beim Debuggen anzeigen**: Das Codefenster zeigt an, wie viel Zeit bei einem bestimmten Methodenaufruf während des Debuggens verstrichen ist.

**„Bearbeiten und Fortfahren“ aktivieren**: Aktiviert die Funktion „Bearbeiten und Fortfahren“ während des Debuggens.

- **natives Bearbeiten und Fortfahren aktivieren**: Sie können die Funktion „Bearbeiten und Fortfahren“ während des Debuggens von systemeigenem C++-Code verwenden. Weitere Informationen hierzu finden Sie unter [Bearbeiten und Fortfahren (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Änderungen beim Fortfahren anwenden (nur nativ)** : Beim Fortsetzen eines unterbrochenen Prozesses kompiliert Visual Studio automatisch alle ausstehenden Codeänderungen und wendet sie an. Ist diese Option nicht aktiviert, können Sie Änderungen mit der Option **Codeänderungen übernehmen** im Menü **Debuggen** übernehmen.

- **Warnung bei veraltetem Code (nur nativ)** :   Ruft Warnungen über veralteten Code ab.

**Beim Debuggen die Schaltfläche „Ausführung bis Klick“ im Editor anzeigen**: Wenn diese Option aktiviert ist, wird während des Debuggens die Schaltfläche [Ausführung bis Klick](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) angezeigt.

**Konsole beim Beenden des Debuggings automatisch schließen**: Weist Visual Studio an, die Konsole am Ende einer Debugsitzung zu schließen.

::: moniker range=">= vs-2019"
**Schnelle Ausdrucksauswertung aktivieren (nur verwaltet)** : Ermöglicht es dem Debugger, eine schnellere Auswertung zu versuchen, indem er die Ausführung einfacher Eigenschaften und Methoden simuliert.

**Debugsymbole in externem Prozess laden (nur nativ)** Aktiviert diese [Arbeitsspeicheroptimierung](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/) beim Debuggen.

**Visual Studio beim Wechsel zum Debugger in den Vordergrund rücken** Schaltet Visual Studio in den Vordergrund um, wenn Sie im Debugger anhalten.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>In älteren Versionen von Visual Studio verfügbare Optionen

Wenn Sie eine ältere Version von Visual Studio verwenden, sind möglicherweise einige zusätzliche Optionen vorhanden.

**Microsoft Edge-Entwicklertools für UWP-JavaScript-Apps aktivieren (experimentell)** : Aktiviert Entwicklertools für UWP-JavaScript-Apps in Microsoft Edge.

**Legacy-Chrome-JavaScript-Debugger für ASP.NET aktivieren**: Aktiviert den Legacy-JavaScript-Skriptdebugger von Chrome für ASP.NET-Apps. Bei der ersten Verwendung in Chrome müssen Sie sich möglicherweise beim Browser anmelden, um Chrome-Erweiterungen zu aktivieren, die Sie installiert haben.

**Ausnahmen-Assistent aktivieren**: Aktiviert für verwalteten Code den Ausnahme-Assistenten. Ab Visual Studio 2017 ersetzte die Ausnahmen-Hilfe den Ausnahme-Assistenten.

**Aufrufliste für Ausnahmefehler entladen**: Führt dazu, dass das Fenster **Aufrufliste** die Aufrufliste an den Punkt zurücksetzt, bevor der Ausnahmefehler aufgetreten ist.

**Bei der Ausführung von Visual Studio als Administrator experimentelle Möglichkeit zum Starten des Chrome-JavaScript-Debuggens verwenden**: Weist Visual Studio an, eine neue Methode zum Starten von Chrome während des JavaScript-Debuggens auszuprobieren.

**Warnung, wenn keine Symbole beim Starten gefunden werden (nur nativ)** : Zeigt eine Warnungsdialogfeld an, wenn Sie ein Programm debuggen, für das der Debugger keine Symbolinformationen hat.

**Warnung, wenn Skriptdebugging beim Start deaktiviert ist**: Zeigt ein Warnungsdialogfeld an, wenn der Debugger mit deaktiviertem Skriptdebuggen gestartet wird.

**nativen Kompatibilitätsmodus verwenden**: Wenn diese Option ausgewählt ist, wird der native Debugger von Visual Studio 2010 anstelle des neuen nativen Debuggers verwendet.

- Verwenden Sie diese Option beim Debuggen von .NET C++-Code, da die neue Debug-Engine das Auswerten von .NET C++-Ausdrücken nicht unterstützt. Durch das Aktivieren des systemeigenen Kompatibilitätsmodus werden aber viele Features deaktiviert, für deren Verwendung die aktuelle Debuggerimplementierung erforderlich ist. In der Legacy-Engine sind z. B. viele Schnellansichten für integrierte Typen wie `std::string` in Visual Studio 2015-Projekten nicht verfügbar.   Verwenden Sie für ein optimales Debugging in diesen Fällen Visual Studio 2013-Projekte.

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
