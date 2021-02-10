---
title: F#-Tools
description: Hier erfahren Sie, welche Features von Visual Studio in F# unterstützt werden.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
f1_keywords:
- fs.ProjectPropertiesDebug
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: a97bd1010a9c739c253f9b5f0a536800fd1f8b69
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838616"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Entwickeln mit Visual F# in Visual Studio

Dieser Artikel enthält Informationen zu Visual Studio-Features für die Entwicklung mit F#.

## <a name="install-f-support"></a>Installieren der F#-Unterstützung

Installieren Sie für die Entwicklung mit F# in Visual Studio zunächst die Workload **.NET-Desktopentwicklung**, sofern Sie dies nicht bereits getan haben. Visual Studio-Workloads werden über den Visual Studio-Installer installiert, den Sie öffnen können, indem Sie **Extras** > **Tools und Features abrufen** auswählen.

![Workload „.NET-Desktopentwicklung“ in Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>F#-Projektfeatures

Für F# in Visual Studio sind verschiedene Projekt- und Elementvorlagen verfügbar. In der folgenden Abbildung sind einige F#-Projektvorlagen für .NET Core und .NET Standard dargestellt:

![F#-Projektvorlagen in Visual Studio](media/fsharp-project-templates.png)

In der folgenden Abbildung sind einige F#-Elementvorlagen dargestellt:

![F#-Elementvorlagen in Visual Studio](media/fsharp-item-templates.png)

Weitere Informationen zu den Elementvorlagen für den Datenzugriff finden Sie unter [F#-Typanbieter](/dotnet/fsharp/tutorials/type-providers/index).

In der folgenden Tabelle sind Features in Projekteigenschaften für F# zusammengefasst:

|Projekteinstellung|In F# unterstützt?|Notizen|
|---------------|----------------|-----|
|Ressourcendateien|Ja||
|Build-, Debug- und Verweiseinstellungen|Ja||
|Festlegung von Zielversionen|Ja||
|Symbol und Manifest|Nein|Über Befehlszeilenoptionen des Compilers verfügbar.|
|ASP.NET-Clientdienste|Nein||
|ClickOnce|Nein|Verwenden Sie ggf. ein Clientprojekt in einer anderen .NET-Sprache.|
|Starke Namen|Nein|Über Befehlszeilenoptionen des Compilers verfügbar.|
|Veröffentlichen einer Assembly und Versionsverwaltung bei einer Assembly|Nein||
|Codeanalyse|Nein|Codeanalysetools können manuell oder im Rahmen eines Postbuildbefehls ausgeführt werden.|
|Sicherheit (Wechsel der Vertrauensebene)|Nein||

## <a name="project-designer"></a>Projekt-Designer

Der **Projekt-Designer** enthält mehrere Projekteigenschaftenseiten, die nach verwandten Funktionalitäten gruppiert sind. Bei den für F#-Projekte verfügbaren Seiten handelt es sich im Wesentlichen um eine Teilmenge der für andere Sprachen verfügbaren Seiten. Sie werden in der folgenden Tabelle beschrieben. Dabei werden Links für die entsprechenden **Projekt-Designer**-Seiten für C# angegeben.

|Projekt-Designer-Seite|Verwandte Links|Beschreibung|
| - |-------------|-----------|
|Application|[Seite „Anwendung“, Projekt-Designer](reference/application-page-project-designer-csharp.md)|Hier können Sie Einstellungen und Eigenschaften auf Anwendungsebene angeben und beispielsweise festlegen, ob Sie eine Bibliothek oder eine ausführbare Datei erstellen und auf welche .NET-Version die Anwendung abzielt. Ferner können Sie Informationen zum Speicherort der von der Anwendung verwendeten Ressourcendateien bereitstellen.|
|Build|[Seite „Erstellen“, Projekt-Designer](reference/build-page-project-designer-csharp.md)|Damit können Sie festlegen, wie der Code kompiliert wird.|
|Buildereignisse|[Seite „Buildereignisse“, Projekt-Designer](reference/build-events-page-project-designer-csharp.md)|Damit können Sie Befehle angeben, die vor oder nach dem Kompilieren ausgeführt werden sollen.|
|Debuggen|[Seite "Debuggen", Projekt-Designer](reference/debug-page-project-designer.md)|Damit können Sie festlegen, wie die Anwendung beim Debuggen ausgeführt wird. So legen Sie beispielsweise fest, welche Befehle verwendet werden und welches Verzeichnis als Startverzeichnis für die Anwendung dient. Ferner legen Sie alle Debugmodi fest, die Sie aktivieren möchten, wie etwa den Modus zum Debuggen von nativem Code und SQL.|
|Paket (nur .NET SDK)|N/V|Damit können Sie NuGet-Paketmetadaten beim Veröffentlichen als NuGet-Paket definieren.|
|Verweispfade|[Verwalten von Verweisen in einem Projekt](managing-references-in-a-project.md)|Damit können Sie angeben, wo nach Assemblys gesucht werden soll, von denen der Code abhängt.|
|Ressourcen (nur .NET SDK)|N/V|Damit können Sie eine Standardressourcendatei generieren und verwalten.|

### <a name="f-specific-settings"></a>F#-spezifische Einstellungen

In der folgenden Tabelle sind F#-spezifische Einstellungen zusammengefasst:

|Projekt-Designer-Seite|Einstellung|Beschreibung|
| - |-------|-----------|
|Build|Endeaufrufe generieren|Wenn diese Option ausgewählt wird, kann die MSIL-Anweisung (Microsoft Intermediate Language) „tail“ verwendet werden. Dadurch kann der Stapelrahmen für endrekursive Funktionen wiederverwendet werden. Entspricht der Compileroption `--tailcalls`.|
|Build|Andere Flags|Damit können Sie zusätzliche Compilerbefehlszeilenoptionen angeben.|

## <a name="code-and-text-editor-features"></a>Code- und Text-Editorfeatures

Folgende Features der Code- und Text-Editoren von Visual Studio werden in F# unterstützt:

|Feature|Beschreibung|In F# unterstützt?|
|-------|-----------|----------------|
|Automatically comment (Automatisch auskommentieren)|Damit können Sie Codeabschnitte auskommentieren bzw. die Auskommentierung aufheben.|Ja|
|Automatically format (Automatisch formatieren)|Damit wird Code mit Standardeinzügen und -formaten neu formatiert.|Nein|
|Lesezeichen|Damit können Sie Stellen im Editor speichern.|Ja|
|Einzug ändern|Damit werden ausgewählte Zeilen eingerückt oder ausgerückt.|Ja|
|Intelligenter Einzug|Damit wird der Cursor automatisch gemäß den F#-Bereichsregeln ein- und ausgerückt.|Ja|
|[Suchen und Ersetzen von Text](finding-and-replacing-text.md)|Damit können Sie eine Datei, ein Projekt oder eine Projektmappe durchsuchen und ggf. Text ändern.|Ja|
|„Zur Definition wechseln“ für die .NET-API|Wenn der Cursor auf eine .NET-API zeigt, wird der aus .NET-Metadaten generierte Code angezeigt.|Nein|
|Go to definition for user-defined API (Zur Definition für benutzerdefinierte API wechseln)|Wenn sich der Cursor auf einer Programmentität befindet, die Sie definiert haben, wird der Cursor an die Stelle in Ihrem Code verschoben, an der die Entität definiert wird.|Ja|
|Gehe zu Zeile|Damit können Sie anhand der Zeilennummer zu einer bestimmten Zeile in einer Datei wechseln.|Ja|
|Navigation bars at top of file (Navigationsleisten oben in der Datei)|Damit können Sie beispielsweise anhand des Funktionsnamens an bestimmte Stellen im Code springen.|Ja|
|Führungslinien für Blockstruktur|Zeigt Führungslinien an, die F#-Bereiche angeben, auf die gezeigt werden kann, um eine Vorschau anzuzeigen.|Ja|
|[Gliedern](outlining.md)|Damit können Sie Codeabschnitte reduzieren, um eine kompaktere Ansicht zu erzeugen.|Ja|
|Mit Tabstopps versehen|Konvertiert Leerzeichen in Tabstopps.|Ja|
|Farbliche Kennzeichnung von Typen|Zeigt definierte Typnamen in einer bestimmten Farbe an.|Ja|
|Schnellsuche. Siehe „Schnellsuche“, Fenster „Suchen und Ersetzen“.|Damit können Sie eine Datei oder ein Projekt durchsuchen.|Ja|
|**STRG**+**Klicken**, um zur Definition zu wechseln|Damit können Sie „Zur Definition wechseln“ aufrufen, indem Sie die **STRG**-TASTE gedrückt halten und auf ein F#-Symbol klicken.|Ja|
|Go to Definition from QuickInfo (Von QuickInfo aus zur Definition wechseln)|Klickbare Symbole in QuickInfos zum Aufrufen von „Zur Definition wechseln“.|Ja|
|Gehe zu allen|Ermöglicht eine globale Fuzzyübereinstimmungsnavigation für alle F#-Konstrukte per **STRG**+**T**.|Ja|
|Inline-Umbenennung|Benennt alle Vorkommen eines Symbol-Inlines um.|Ja|
|Alle Verweise suchen|Sucht nach allen Vorkommen eines Symbols in einer Codebasis.|Ja|
|Simplify Name code fix (Codekorrektur: Name vereinfachen)|Entfernt unnötige Qualifizierer für F#-Symbole.|Ja|
|Codekorrektur: Nicht verwendete „`open`“-Anweisung entfernen|Entfernt alle unnötigen `open`-Anweisungen in einem Dokument.|Ja|
|Unused value code fix (Codekorrektur: Nicht verwendeter Wert)|Schlägt vor, einen nicht verwendeten Bezeichner in einen Unterstrich umzubenennen.|Ja|

Allgemeine Informationen zum Bearbeiten von Code in Visual Studio sowie zu den Features des Text-Editors finden Sie im Artikel zu den [Features des Code-Editors](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>IntelliSense-Funktionen

In der folgenden Tabelle sind die in F# unterstützten und nicht unterstützten IntelliSense-Features zusammengefasst:

|Feature|Beschreibung|In F# unterstützt?|
|-------|-----------|----------------|
|Automatically implement interfaces (Schnittstellen automatisch implementieren)|Generiert Codestubs für Schnittstellenmethoden.|Ja|
|Codeausschnitte|Fügt Code aus einer Bibliothek allgemeiner Codierungskonstrukte in Themen ein.|Nein|
|Wort vervollständigen|Erspart die Eingabe durch Vervollständigen von Wörtern und Namen beim Tippen.|Ja|
|Automatische Vervollständigung|Wenn diese Option aktiviert ist, wählt die Wortvervollständigung während Sie tippen die erste Übereinstimmung aus, statt zu warten, bis Sie eine Option auswählen oder die Tastenkombination **STRG**+**Leertaste** drücken.|Ja|
|Offer completion for symbols in unopened namespaces (Vervollständigung für Symbole in nicht geöffneten Namespaces anbieten)|Mit der automatischen Vervollständigung wird ein übereinstimmendes Symbol vorgeschlagen, das sich in einem nicht geöffneten Namespace befindet. Ist diese Option aktiviert, wird die Vervollständigung mit der entsprechenden `open`-Anweisung angeboten.|Ja|
|Generate code elements (Codeelement generieren)|Damit können Sie Stubcode für verschiedene Konstrukte generieren.|Nein|
|Member auflisten|Bei der Eingabe eines Memberzugriffsoperators (.) werden Member für einen Typ angezeigt.|Ja|
|Using-/Open-Direktiven organisieren|Organisiert Namespaces, die von **Using**-Anweisungen in C# **Open**-Direktiven in F# referenziert werden.|Nein|
|Parameterinfo|Zeigt bei der Eingabe eines Funktionsaufrufs nützliche Informationen zu Parametern an.|Ja|
|QuickInfo|Zeigt die vollständige Deklaration eines beliebigen Bezeichners im Code an.|Ja|
|Automatische Vervollständigung mit Klammern|Vervollständigt automatisch klammerähnliche Syntaxkonstrukte in F# auf transaktionale Weise.|Ja|

Allgemeine Informationen zu IntelliSense finden Sie unter [IntelliSense in Visual Studio](using-intellisense.md).

## <a name="debugging-features"></a>Debugfeatures

In der folgenden Tabelle sind die Features zusammengefasst, die beim Debuggen von F#-Code verfügbar sind.

|Feature|Beschreibung|In F# unterstützt?|
|-------|-----------|----------------|
|Fenster {1}{2}|Zeigt automatische oder temporäre Variablen an.|Nein|
|Haltepunkte|Damit können Sie beim Debuggen die Codeausführung an bestimmten Punkten anhalten.|Ja|
|Bedingte Haltepunkte|Aktiviert Breakpoints, mit denen eine Bedingung geprüft wird, die bestimmt, ob die Ausführung angehalten wird.|Ja|
|Bearbeiten und Fortfahren|Ermöglicht beim Debuggen eines aktiven Programms das Ändern und Kompilieren von Code, ohne den Debugger zu beenden und neu zu starten.|Nein|
|Ausdrucksauswertung|Wertet Code zur Laufzeit aus, und führt ihn aus.|Nein, die C#-Ausdrucksauswertung kann verwendet werden, jedoch nur für C#-Syntax.|
|Verlaufsbezogenes Debuggen|Damit können Sie zuvor ausgeführten Code schrittweise ausführen.|Ja|
|Lokalfenster|Zeigt lokal definierte Werte und Variablen an.|Ja|
|Ausführen bis Cursor|Damit können Sie Code bis zu der Zeile ausführen, die den Cursor enthält.|Ja|
|Einzelschritt|Damit können Sie während der Ausführung in die einzelnen Funktionsaufrufe springen.|Ja|
|Prozedurschritt|Damit können Sie während der Ausführung im aktuellen Stapelrahmen in vergangene Funktionsaufrufe springen.|Ja|

Weitere Informationen zum Visual Studio-Debugger finden Sie unter [Debugging in Visual Studio](../debugger/index.yml).

## <a name="additional-tools"></a>Zusätzliche Tools

In der folgenden Tabelle ist die Unterstützung für F# in Visual Studio-Tools zusammengefasst.

|Tool|Beschreibung|In F# unterstützt?|
|----|-----------|----------------|
|Aufrufhierarchie|Zeigt die geschachtelte Struktur von Funktionsaufrufen im Code an.|Nein|
|Codemetriken|Sammelt Informationen zum Code wie etwa die Zeilenanzahl.|Nein|
|Klassenansicht|Stellt eine typbasierte Ansicht des Codes in einem Projekt bereit.|Nein|
|[Fehlerliste (Fenster)](reference/error-list-window.md)|Zeigt eine Liste mit Fehlern im Code an.|Ja|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Damit können Sie F#-Code eingeben (oder kopieren und einfügen) und ihn sofort unabhängig von der Erstellung des Projekts ausführen. Beim Fenster „F# Interactive“ handelt es sich um eine Read, Evaluate, Print Loop (REPL).|Ja|
|Objektkatalog|Damit können Sie die Typen in einer Assembly anzeigen.|In kompilierten Assemblys dargestellte F#-Typen werden nicht exakt so angezeigt, wie Sie sie erstellen. Sie können die kompilierte Darstellung von F#-Typen zwar durchsuchen, jedoch nicht so anzeigen, wie sie in F# dargestellt werden.|
|[Ausgabefenster](reference/output-window.md)|Zeigt die Buildausgabe an.|Ja|
|Leistungsanalyse|Stellt Tools zum Messen der Codeleistung bereit.|Ja|
|Eigenschaftenfenster|Zeigt Eigenschaften des Objekts in der Entwicklungsumgebung an, die den Fokus hat, und ermöglicht deren Bearbeitung.|Ja|
|Server-Explorer|Bietet Möglichkeiten zur Interaktion mit verschiedenen Serverressourcen.|Ja|
|Projektmappen-Explorer|Damit können Sie Projekte und Dateien anzeigen und verwalten.|Ja|
|Aufgabenliste|Damit können Sie Arbeitselemente verwalten, die sich auf den Code beziehen.|Nein|
|Testprojekte|Stellt Features zum Testen des Codes bereit.|Nein|
|Toolbox|Zeigt Registerkarten an, die ziehbare Objekte wie etwa Steuerelemente und Text- oder Codeabschnitte enthalten.|Ja|

## <a name="see-also"></a>Weitere Informationen

- [Leitfaden für F# (.NET Framework)](/dotnet/fsharp/)
- [Erste Schritte mit F# in Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)
