---
title: Steigern Ihrer Produktivität für die .NET-Entwicklung
description: Überblick über die Navigation, die Codeanalyse, Unittests und andere Funktionen, um schneller besseren .NET Code zu schreiben
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: a3ac2e91ed9166a2eb8bdc4a19f2143c4fc71640
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161312"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Produktivitätsleitfaden für Visual Studio für C#-Entwickler

In diesem Artikel erfahren Sie, wie Visual Studio es Entwicklern ermöglicht, produktiver denn je zu arbeiten. Nutzen Sie unsere Leistungs- und Produktivitätsverbesserungen wie die Navigation zu dekompilierten Assemblys, Namensvorschläge für Variablen während der Eingabe, eine Hierarchieansicht im **Test-Explorer**, „Gehe zu allen“ (**Strg**+**T**) zur Navigation zu Datei-/Typ-/Member-/Symboldeklarationen, eine intelligente **Hilfe bei Ausnahmen**, Konfiguration und Erzwingung des Codeformats und viele Refactorings und Codekorrekturen.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Ich bin an meine Tastenkombinationen aus einem anderen Editor gewöhnt

::: moniker range="vs-2017"

**Neu in Visual Studio 2017 Version 15.8**

::: moniker-end

Wenn Sie von einer anderen IDE oder Codierungsumgebung wechseln, können Sie Ihr Tastaturschema in *Visual Studio Code* oder *ReSharper (Visual Studio)* ändern:

![Tastaturschemas in Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Einige Erweiterungen bieten auch Tastaturschemas an:

- [HotKeys für Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs-Emulation](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Im Folgenden finden Sie beliebte Tastenkombinationen für Visual Studio:

| Tastenkombination (Alle Profile) | Get-Help | Beschreibung |
|-|-|-|
| **STRG**+**T** | Gehe zu allen | Navigieren zu einer beliebigen Datei-/Typ-/Member-/Symboldeklaration |
| **F12** (oder **Strg**+**Klicken**) | Gehe zu Definition | Navigieren zum Ort, an dem ein Symbol definiert ist |
| **Strg**+**F12** | Gehe zu Implementierung | Navigieren von einem Basistyp oder Member zu seinen verschiedenen Implementierungen |
| **Umschalt**+**F12** | Alle Verweise suchen | Alle Symbol- oder Literalverweise ansehen |
| **ALT**+**POS1** | Zu Basis wechseln | In der Vererbungskette nach oben navigieren |
| **STRG**+ **.** (oder **Alt**+**Eingabetaste** im C#-Profil) | Schnellaktionen und Refactorings | Ansehen, welche Codekorrekturen, Aktionen zum Generieren von Code, Refactorings oder anderen Schnellaktionen an der Cursorposition oder für den markierten Code zur Verfügung stehen. |
| **STRG**+**D** | Zeile duplizieren | Die Codezeile, in der sich der Cursor befindet, wird dupliziert (verfügbar in **Visual Studio 2017 Version 15.6** und höher) |
| **UMSCHALT**+**ALT**+ **+** / **-** | Erweitern/Reduzieren | Erweitert oder reduziert die aktuelle Auswahl im Editor (verfügbar in **Visual Studio 2017 Version 15.5** und höher) |
| **UMSCHALTTASTE** + **ALT-TASTE** +  **.** | Nächste übereinstimmende Einfügemarken einfügen | Fügt eine Auswahl und die Einfügemarke an der nächsten Position ein, die der aktuellen Auswahl entspricht (verfügbar in **Visual Studio 2017-Version 15.8** und höher) |
| **STRG**+**Q** | Suchen | Durchsuchen aller Visual Studio-Einstellungen |
| **F5** | Debugging starten | Debugging der Anwendung starten |
| **Strg**+**F5** | Ohne Debuggen ausführen | Anwendung lokal ausführen, ohne Debuggen |
| **Strg**+**K**,**D** (Standardprofil) oder **Strg**+**E**,**D** (C#-Profil) | Dokument formatieren | Bereinigt Formatierungsverstöße in Ihrer Datei anhand Ihrer Einstellungen für Zeilenumbruch, Abstand und Einzug |
| **STRG**+ **\\** ,**STRG**+**E** (Standardprofil) oder **STRG**+**W**,**E** (C#-Profil) | Fehlerliste anzeigen | Alle Fehler in Ihrem Dokument, Projekt oder Ihrer Projektmappe ansehen |
| **ALT** + **PgUp/PgDn** | Zum nächsten/vorherigen Problem wechseln | Springt zum vorherigen/nächsten Fehler, Warnung und Vorschlag in Ihrem Dokument (verfügbar in **Visual Studio 2017-Version 15.8** und höher) |
| **STRG**+**K**, **/** | Wechseln zwischen Auskommentieren/Auskommentierung aufheben für einzelne Zeilen | Dieser Befehl fügt einen Kommentar für einzelne Zeilen hinzu oder entfernt ihn, je nachdem, ob Ihre Auswahl bereits auskommentiert ist. |
| **STRG**+**UMSCHALTTASTE**+ **/** | Wechseln zwischen Auskommentieren/Auskommentierung aufheben für Blöcke | Dieser Befehl fügt Kommentare für Blöcke hinzu oder entfernt sie, je nachdem, was Sie ausgewählt haben. |

> [!NOTE]
> Einige Erweiterungen heben die Tastenzuordnungen von Visual Studio auf. Um die obigen Befehle verwenden zu können, stellen Sie zuerst die Standardtastenzuordnungen von Visual Studio wieder her. Navigieren Sie dazu zu **Extras** > **Einstellungen importieren/exportieren** > **Alle Einstellungen zurücksetzen** oder zu **Extras** > **Optionen** > **Tastatur** > **Zurücksetzen**.

Weitere Informationen zu Tastenkombinationen und Befehlen finden Sie unter [Tastenkombinationen für die Produktivität](../ide/productivity-shortcuts.md)und [Beliebte Tastenkombinationen](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Schnelles Navigieren zu Dateien oder Typen

Visual Studio verfügt über ein Feature namens **Gehe zu allen** (**STRG**+**T**). **Gehe zu allen** ermöglicht Ihnen einen schnellen Wechsel zu jeder Datei-, Typ-, Member- oder Symboldeklaration.

- Ändern Sie die Position dieser Suchleiste, oder deaktivieren Sie die Livenavigationsvorschau mithilfe des **Zahnradsymbols**.
- Filtern Sie Ergebnisse mithilfe von Syntax wie `t mytype`.
- Beschränken Sie Ihre Suche nur auf das aktuelle Dokument.
- Der Abgleich der Groß-/Kleinschreibung wird unterstützt.

![„Gehe zu allen“ in Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Erzwingen von Codeformatregeln

Sie können eine EditorConfig-Datei zum Codieren von Codierungskonventionen verwenden, damit diese in Ihrer Quelle beibehalten werden.

![Codeformaterzwingung in Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Fügen Sie eine EditorConfig-File im Standard- oder .NET-Format zu Ihrem Projekt hinzu, indem Sie **Hinzufügen** > **Neues Element** auswählen. Suchen Sie im Dialogfeld **Neues Element hinzufügen** nach „editorconfig“. Wählen Sie eine der Elementvorlagen für eine **editorconfig-Datei** aus, und klicken Sie dann auf **Hinzufügen**.

   ![EditorConfig-Elementvorlagen in Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Erstellen Sie automatisch eine *.editorconfig*-Datei basierend auf Ihren Codeformateinstellungen über **Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat**.

   ![Screenshot: Generieren einer .editorconfig-Datei aus den Einstellungen in VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Das [Coderückschluss-Feature](/visualstudio/intellicode/code-style-inference) von IntelliCode für Visual Studio leitet Codeformate aus vorhandenem Code ab. Dann erstellt das Feature eine nicht leere EditorConfig-Datei, in der Ihre bevorzugten Codeformate bereits definiert sind.

- Konfigurieren Sie den Schweregrad einer Codestilregel direkt im Editor. Wenn Sie derzeit nicht über eine Datei „.editorconfig“ verfügen, wird eine für Sie generiert. Zeigen Sie mit dem Cursor auf den Fehler, die Warnung oder den Vorschlag, und drücken Sie **STRG**+ **.** , um das Menü „Schnellaktionen und Refactorings“ zu öffnen. Wählen Sie **Issues konfigurieren oder unterdrücken** aus. Wählen Sie dann die Regel sowie den Schweregrad aus, den Sie für die Regel konfigurieren möchten. Dadurch wird die vorhandene Editorkonfiguration mit dem neuen Schweregrad für die Regel aktualisiert.

   ![Konfigurieren Sie den Schweregrad einer Codestilregel direkt im Editor.](../ide/media/configure-severity-level.png)

Lesen Sie die Dokumentation zu den [Einstellungen für die .NET-Codierungskonventionen](/dotnet/fundamentals/code-analysis/code-style-rule-options), die auch ein Beispiel einer vollständigen EditorConfig-Datei enthält.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Codebereinigung

Mit dem Feature **Codebereinigung** bietet Visual Studio eine bedarfsgesteuerte Formatierung Ihrer Codedatei, einschließlich Codeformateinstellungen. Zum Ausführen der Codebereinigung klicken Sie auf das Besensymbol unten im Editor, oder drücken Sie **STRG**+**K**, **STRG**+**E**.

![Schaltfläche „Codebereinigung“ in Visual Studio 2019](media/execute-code-cleanup.png)

Sie können die Codebereinigung auch für Ihr gesamtes Projekt oder Ihre gesamte Projektmappe ausführen. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Namen eines Projekts oder einer Projektmappe, wählen Sie **Analysieren und Code bereinigen** aus, und klicken Sie dann auf **Codebereinigung ausführen**.

![Ausführen der Codebereinigung für ein gesamtes Projekt oder eine gesamte Projektmappe](media/run-code-cleanup-project-solution.png)

Zusätzlich zur Formatierung Ihrer Datei im Hinblick auf Leerzeichen, Einzüge usw. wendet die **Codebereinigung** auch ausgewählte Codeformate an. Ihre Einstellungen für jedes Codeformat werden aus der [EditorConfig-Datei](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) gelesen, sofern für das Projekt eine vorhanden ist, oder aus den [Codeformateinstellungen](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) im Dialogfeld **Optionen**.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refactorings und Codekorrekturen

Visual Studio bietet eine Vielzahl von Refactorings, Aktionen zum Generieren von Code und Codekorrekturen. Rote Wellenlinien stellen Fehler dar, grüne Wellenlinien Warnungen, und drei graue Punkte stellen Codevorschläge dar. Sie erhalten Zugang zu Codekorrekturen, indem Sie auf das Glühbirnen- bzw. Schraubendrehersymbol klicken oder **STRG**+ **.** oder **ALT**+**EINGABETASTE** drücken. Jede Korrektur enthält ein Vorschaufenster, das einen Livecodevergleich und die Funktionsweise der Lösung anzeigt.

Zu gängigen schnellen Problembehebungen und Refactorings zählen Folgende:

- Umbenennen
- Methode extrahieren
- Methodensignatur ändern
- Konstruktor generieren
- Methode generieren
- Typ in Datei verschieben
- NULL-Überprüfung hinzufügen
- Parameter hinzufügen
- Nicht erforderliche using-Direktiven entfernen
- Foreach-Schleife in eine LINQ-Abfrage oder LINQ-Methode konvertieren
- Hochstufen von Membern in der Hierarchie

Weitere Informationen finden Sie unter [Feature für die Codegenerierung in Visual Studio](code-generation-in-visual-studio.md).

Sie können auch [FxCop-Analysetools](../code-quality/install-fxcop-analyzers.md) installieren, um Codeprobleme zu kennzeichnen. Oder Sie schreiben mit [Roslyn-Analysetools](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md) Ihr eigenes Refactoring oder Ihre eigene Codekorrektur.

Mehrere Communitymitglieder haben kostenlose Erweiterungen geschrieben, die zusätzliche Codeüberprüfungen hinzufügen:

::: moniker range="vs-2017"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint for Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

::: moniker range="vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [SonarLint for Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

![Refactorings in Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Die Features „Find Usages“ (Verwendungen finden), „Zur Implementierung wechseln“ und „Navigate To Decompiled Assemblies“ (Navigieren zu dekompilierten Assemblys)

Visual Studio weist viele Features zum Suchen und [Navigieren in Ihrer Codebasis](../ide/navigating-code.md) auf.

| Komponente | Verknüpfung | Details oder Verbesserungen |
|- | - | -|
| Alle Verweise suchen | **Umschalt**+**F12**| Ergebnisse werden farbig hervorgehoben und können nach Projekt, Definition und Verweistyp (z.B. „read“ (Lesen) oder „write“ (Schreiben)) gruppiert werden. Sie können Ergebnisse auch „sperren“. |
| Gehe zu Implementierung | **Strg**+**F12** | Mit „Gehe zu Definition“ für das Schlüsselwort `override` können Sie zum überschriebenen Member navigieren. |
| Gehe zu Definition | **F12** oder **Strg**+**Klicken**| Klicken Sie bei gedrückter **STRG**-Taste, um zur Definition zu navigieren. |
| Peek-Definition | **ALT**+**F12** | Inlineansicht einer Definition |
| Strukturschnellansicht | Graue, gepunktete Linien zwischen geschweiften Klammern | Zeigen Sie darauf, um Ihre Codestruktur anzuzeigen. |
| Navigation zu dekompilierten Assemblys | **F12** oder **Strg**+**Klicken** | Navigieren Sie zur externen Quelle (mit ILSpy dekompiliert), indem Sie folgendes Feature aktivieren: **Extras** > **Optionen** > **Text-Editor** > **C#**  > **Erweitert** > **Navigation zu dekompilierten Quellen aktivieren**. |

![„Gehe zu allen“ und „Alle Verweise suchen“](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Verbessertes IntelliSense

Verwenden Sie IntelliCode für Visual Studio, um [kontextbezogene Codevervollständigungen](/visualstudio/intellicode/intellicode-visual-studio) zu erhalten, anstatt nur einer alphabetischer Liste. Sie können auch ein [benutzerdefiniertes IntelliSense-Modell](/visualstudio/intellicode/custom-model-faq) auf Grundlage Ihrer domänenspezifischen Bibliotheken trainieren.

## <a name="unit-testing"></a>Komponententest

Ab Visual Studio 2017 gibt es zahlreiche Verbesserungen im Bereich der Funktionen zum Testen. Sie können mit den Testframeworks „MSTest v1“, „MSTest v2“, „NUnit“ oder „XUnit“ testen.

- Das Testen mit dem **Test-Explorer** ist schnell.

- Organisieren Sie Ihre Tests im **Test-Explorer** mit *hierarchischer Sortierung*.

   ![Hierarchieansicht für den Test-Explorer in Visual Studio](../ide/media/VSGuide_Testing.png)

- [Live Unit Testing](../test/live-unit-testing.md) führt laufend Tests aus, die durch Ihre Codeänderungen beeinflusst werden, und aktualisiert Inline-Editor-Symbole, um Sie über den Status Ihres Tests zu informieren. Schließen Sie bestimmte Tests oder Testprojekte in Ihren aktiven Testsatz ein oder von diesem aus. (Nur Visual Studio Enterprise-Edition)

## <a name="debugging"></a>Debuggen

Funktionen zum Debuggen in Visual Studio:

::: moniker range=">=vs-2019"

- In den Fenstern **Überwachung**, **Auto** und **Lokal** kann nach einer Zeichenfolge gesucht werden.
- Durch *Run to click* (Ausführung bis Klick) können Sie auf eine Stelle neben einer Codezeile zeigen, auf das angezeigte grüne Wiedergabesymbol klicken und das Programm ausführen, bis es diese Zeile erreicht.
- Die **Ausnahmen-Hilfe** zeigt die wichtigsten Informationen auf der obersten Ebene im Dialogfeld am, z.B. die Information, welche Variable in einer `NullReferenceException` als `null` festgelegt ist.
- Durch Debuggen mit der Funktion [Schritt zurück](../debugger/view-historical-application-state.md) können Sie zu den vorherigen Breakpoints oder Schritten zurückkehren und den zuvor vorhandenen Status der Anwendung anzeigen.
- Durch [Debuggen von Momentaufnahmen](/azure/application-insights/app-insights-snapshot-debugger) können Sie den Status einer aktiven Webanwendung bei Auslösung einer Ausnahme (muss in Azure erfolgen) untersuchen.

::: moniker-end

::: moniker range="vs-2017"

- Durch *Run to click* (Ausführung bis Klick) können Sie auf eine Stelle neben einer Codezeile zeigen, auf das angezeigte grüne Wiedergabesymbol klicken und das Programm ausführen, bis es diese Zeile erreicht.
- Die **Ausnahmen-Hilfe** zeigt die wichtigsten Informationen auf der obersten Ebene im Dialogfeld am, z.B. die Information, welche Variable in einer `NullReferenceException` als `null` festgelegt ist.
- Durch Debuggen mit der Funktion [Schritt zurück](../debugger/view-historical-application-state.md) können Sie zu den vorherigen Breakpoints oder Schritten zurückkehren und den zuvor vorhandenen Status der Anwendung anzeigen.
- Durch [Debuggen von Momentaufnahmen](/azure/application-insights/app-insights-snapshot-debugger) können Sie den Status einer aktiven Webanwendung bei Auslösung einer Ausnahme (muss in Azure erfolgen) untersuchen.

::: moniker-end

![Screenshot: Ausnahmen-Hilfe in Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Versionskontrolle

Sie können mithilfe von Git oder der TFVC Ihren Code in Visual Studio speichern und aktualisieren.

::: moniker range=">=vs-2019"

- Installieren Sie [Pull Requests for Visual Studio (Pull Requests für Visual Studio)](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs), um Pull Requests zu erstellen, zu überprüfen, auszuchecken und auszuführen, ohne Visual Studio dafür verlassen zu müssen.

::: moniker-end

- Organisieren Sie Ihre lokalen Änderungen mit dem [Team Explorer](reference/team-explorer-reference.md), und verfolgen Sie ausstehende Commits und Änderungen mit der Statusleiste nach.

- Richten Sie mit der Erweiterung [Continuous Delivery Tools for Visual Studio (Continuous Delivery Tools für Visual Studio)](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) Continuous Integration und Delivery für Ihre ASP.NET-Projekte in Visual Studio ein.

![Quellcodeverwaltung in Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Welche anderen Features sollte ich kennen?

Hier ist eine Liste an Editor- und Produktivitätsfeatures zum einfacheren Schreiben von Code. Einige Features müssen aktiviert werden, da sie standardmäßig deaktiviert sind (sie führen möglicherweise Indizierungen auf dem Computer durch, sind kontrovers oder derzeit experimentell).

| Funktion | Details | Vorgehensweise zum Aktivieren |
|-|-|-|
| Suchen von Dateien im Projektmappen-Explorer | Markiert die aktive Datei im **Projektmappen-Explorer** | **Extras** > **Optionen** > **Projekte und Projektmappen** > **Aktives Element im Projektmappen-Explorer überwachen** |
| Hinzufügen von using-Direktiven für Typen in Referenzassemblys und NuGet-Paketen | Zeigt eine Fehlerglühbirne mit einer Codefehlerbehebung zum Installieren eines NuGet-Pakets für einen nicht referenzierten Typ an. | **Extras** > **Optionen** > **Text-Editor** > **C#**  > **Erweitert** > **using-Direktiven für Typen in Referenzassemblys vorschlagen** und **using-Direktiven für Typen in NuGet-Paketen vorschlagen** |
| Vollständige Projektmappenanalyse aktivieren | Zeigt alle Fehler in der Projektmappe in der **Fehlerliste** an. | **Tools** > **Optionen** > **Text-Editor** > **C#**  > **Erweitert** > **Vollständige Projektmappenanalyse aktivieren** |
| Aktivieren der Navigation zu dekompilierten Quellen | Lässt die Aktivierung von „Gehe zu Definition“ für Typen/Member aus externen Quellen zu und verwendet den ILSpy-Decompiler zur Anzeige von Methodentexten. | **Extras** > **Optionen** > **Text-Editor** > **C#**  > **Erweitert** > **Navigation zu dekompilierten Quellen aktivieren** |
| Vervollständigungs-/Vorschlagsmodus | Ändert das Vervollständigungsverhalten in IntelliSense. Entwickler mit IntelliJ-Hintergründen verwenden meist keine standardmäßig ausgewählte Einstellung. | **Menü** > **Bearbeiten** > **IntelliSense** > **Beendigungsmodus umschalten** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Zeigt Codereferenzinformationen an und ändert den Änderungsverlauf im Editor. (CodeLens-Indikatoren für die Quellcodeverwaltung sind in der Visual Studio Community Edition nicht verfügbar.) | **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **CodeLens** |
| [Codeausschnitte](../ide/visual-csharp-code-snippets.md) | Unterstützt die Erzeugung kurzer Codebausteine | Geben Sie einen Codeausschnittnamen ein, und drücken Sie dann zweimal die **Tab**-Taste. |
