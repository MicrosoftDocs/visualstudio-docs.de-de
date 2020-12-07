---
title: Neue Funktionen im Code-Editor
description: Hier erfahren Sie mehr über die Features im Visual Studio-Code-Editor, mit denen Sie Code und Text einfacher schreiben und verwalten können.
ms.custom: SEO-VS-2020
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2363d350c91ac72b21784f490778010eba12007
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480186"
---
# <a name="features-of-the-code-editor"></a>Funktionen des Code-Editors

Der Visual Studio-Editor bietet viele Funktionen, die Ihnen das Schreiben und die Verwaltung von Code und Text erleichtern. Sie können mithilfe der Gliederung verschiedene Codeblöcke reduzieren und erweitern. Wenn Sie IntelliSense, den **Objektkatalog** und die Aufrufhierarchie verwenden, können Sie mehr über Ihren Code erfahren. Sie können Code finden, indem Sie Funktionen wie **Gehe zu**, **Gehe zu Definition** und **Alle Verweise suchen** verwenden. Mit Codeausschnitten können Sie Codeblöcke einfügen und Code mithilfe von Funktionen wie **Generate From Usage** generieren. Wenn Sie noch nie mit dem Visual Studio-Editor gearbeitet haben, lesen Sie [Informationen zur Verwendung des Code-Editors](../get-started/tutorial-editor.md).

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Quellcode-Editor (Visual Studio für Mac)](/visualstudio/mac/source-editor).

Code kann auf unterschiedliche Weise angezeigt werden. Standardmäßig wird Ihr Code im **Projektmappen-Explorer** nach Dateien geordnet angezeigt. Sie können auf die Registerkarte **Klassenansicht** im unteren Bereich des Fensters klicken, damit Ihr Code nach Klassen geordnet angezeigt wird.

Sie können Text in einzelnen oder mehreren Dateien suchen und ersetzen. Weitere Informationen finden Sie unter [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md). Sie können reguläre Ausdrücke zum Suchen und Ersetzen von Text verwenden. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Für die verschiedenen Visual Studio-Sprachen werden unterschiedliche Funktionssätze angeboten, und in einigen Fällen verhalten sich die Funktionen in verschiedenen Sprachen unterschiedlich. Viele dieser Unterschiede werden in den Beschreibungen der Funktionen erläutert. Weitere Informationen können Sie den Abschnitten über einzelne Visual Studio-Sprachen entnehmen.

## <a name="editor-features"></a>Editor-Funktionen

|Feature|Beschreibung|
|-|-|
|Farben für Syntax|Einige Syntaxelemente in den Code- und Markupdateien sind unterschiedlich gefärbt, damit sie unterschieden werden können. Beispielsweise sind Schlüsselwörter (wie `using` in C# und `Imports` in Visual Basic) in einer Farbe gehalten, jedoch Typen (wie `Console` und `Uri`) haben eine andere Farbe. Andere Syntaxelemente werden auch farbig hervorgehoben, wie zum Beispiel Zeichenfolgenliterale und Kommentare. In C++ werden Farben verwendet, um Typen, Enumerationen und Makros von anderen Token zu unterscheiden.<br /><br /> Sie können die Standardfarbe für jeden Typ sehen und die Farbe für spezifische Syntaxelemente unter [Schriftarten und Farben, Umgebung, Dialogfeld „Optionen“](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) ändern, das Sie über das Menü **Extras** öffnen können.|
|Markierungen für Fehler und Warnungen|Wenn Sie Code hinzufügen und Ihre Projektmappe erstellen, werden möglicherweise (a) verschiedenfarbige Unterstreichungen (sogenannte Wellenlinien) oder (b) Glühbirnen in Ihrem Code angezeigt. Rote Wellenlinien kennzeichnen Syntaxfehler, blaue kennzeichnen Compilerfehler, grüne kennzeichnen Warnungen und lila Wellenlinien kennzeichnen alle anderen Arten von Fehlern. Unter [Schnelle Aktionen](../ide/quick-actions.md) werden Fehlerbehebungen für Probleme vorgeschlagen. Sie vereinfachen das Anwenden der jeweiligen Fehlerbehebung.<br /><br /> Sie können die Standardfarbe der jeweiligen Wellenlinien für Fehler und Warnungen im Dialogfeld **Tools** > **Optionen** > **Umgebung** > **Schriftarten und Farben** anzeigen. Suchen Sie nach **Syntaxfehler**, **Compilerfehler**, **Warnung** und **Anderer Fehler**.|
|Überprüfung des Klammergleichgewichts|Bei Platzierung der Einfügemarke auf eine öffnende geschweifte Klammer in einer Codedatei werden die öffnende und die schließende Klammer hervorgehoben. Durch diese Funktion erhalten Sie unmittelbar Feedback zu falsch platzierten oder fehlenden geschweiften Klammern. Sie können die Anzeige der zugehörigen Klammer mit der Einstellung **Trennzeichen automatisch hervorheben** aktivieren und deaktivieren (**Tools** > **Optionen** > **Text-Editor**). Sie können die Hervorhebungsfarbe in der Einstellung **Schriftarten und Farben** ändern (**Tools** > **Optionen** > **Umgebung**). Suchen Sie nach **Zugehörige Klammer (Hervorhebung)** oder **Zugehörige Klammer (Rechteck)** .|
|Strukturschnellansicht|Gepunktete Linien verbinden passende Klammern in Codedateien, wodurch sich öffnende und schließende Klammerpaare leichter erkennen lassen. Das hilft Ihnen bei der schnelleren Suchen von Code in Ihrer Codebasis. Sie können diese Linien mit der Einstellung **Strukturlinien anzeigen** im Abschnitt **Anzeige** auf der Seite **Tools** > **Optionen** > **Text-Editor** > **Allgemein** aktivieren und deaktivieren.|
|Zeilennummern|Zeilennummern können im linken Rand des Codefensters angezeigt werden. Standardmäßig werden sie nicht angezeigt. Sie können diese Option in den Einstellungen **Text-Editor –> Alle Sprachen** aktivieren (**Tools** > **Optionen** > **Text-Editor** > **Alle Sprachen**). Sie können Zeilennummern für einzelne Programmiersprachen anzeigen, indem Sie die Einstellungen für diese Sprachen ändern (**Extras** > **Optionen** > **Text-Editor** >  **\<language>** ). Damit die Zeilennummern ausgedruckt werden, müssen Sie im Dialogfeld **Drucken** die Option **Zeilennummern einschließen** auswählen.|
|Änderungsnachverfolgung|Durch die Farbe am linken Rand können Sie die Änderungen verfolgen, die Sie an einer Datei vorgenommen haben. Änderungen, die Sie seit dem Öffnen der Datei vorgenommen, jedoch nicht gespeichert haben, werden durch eine gelbe Leiste am linken Rand gekennzeichnet (auch als "Auswahlrand" bezeichnet). Nach dem Speichern der Änderungen (jedoch vor dem Schließen der Datei), wird die Statusleiste grün. Wenn Sie eine Änderung rückgängig machen, nachdem Sie die Datei gespeichert haben, wird die Leiste orange. Um diese Funktion zu aktivieren und zu deaktivieren, ändern Sie die Option **Änderungen nachverfolgen** in den **Text-Editor**-Einstellungen (**Tools** > **Optionen** > **Text-Editor**).|
|Auswählen von Text und Code|Sie können Text entweder im standardmäßigen fortlaufenden Streammodus oder im Feldmodus auswählen, indem Sie einen rechteckigen Bereich des Texts anstelle eines Zeilensatzes auswählen. Drücken Sie **ALT** während Sie die Maus über die Auswahl ziehen (oder drücken Sie **ALT**+**UMSCHALT**+ **\<arrow key>** ), um eine Auswahl im Feldmodus vorzunehmen. Die Auswahl umfasst alle Zeichen innerhalb des Rechtecks, das durch das erste und das letzte Zeichen in der Auswahl definiert wird. Eingaben oder Einfügungen im ausgewählten Bereich werden in jeder Zeile am gleichen Punkt eingefügt.|
|Zoom|Sie können die Anzeige in jedem Codefenster vergrößern oder verkleinern, indem Sie die **STRG-TASTE** gedrückt halten und das Mausrad drehen (oder zum Vergrößern **STRG**+**UMSCHALT**+ **.** und zum Verkleinern **STRG**+**UMSCHALT**+ **,** drücken). Sie können auch über das **Zoomfelds** links unten im Codefenster einen bestimmten Zoomprozentsatz festlegen. Die Zoomfunktion funktioniert nicht in Toolfenstern.|
|Virtueller Bereich|Standardmäßig enden Zeilen in Visual Studio-Editoren nach dem letzten Zeichen, sodass der Cursor am Ende einer Zeile mit der **NACH RECHTS-TASTE** an den Anfang der nächsten Zeile verschoben werden kann. In einigen Editoren endet eine Zeile nicht nach dem letzten Zeichen, und Sie können den Cursor an einer beliebigen Stelle in der Zeile platzieren. Sie können den virtuellen Bereich im Editor in den Einstellungen **Tools** > **Optionen** > **Text-Editor** > **Alle Sprachen** aktvieren. Beachten Sie, dass Sie entweder **Virtueller Bereich** oder **Zeilenumbruch** aktivieren können, jedoch nicht beide Optionen gleichzeitig.|
|Drucken|Beim Drucken einer Datei können Sie über die Optionen im Dialogfeld **Drucken** Zeilennummern einschließen oder reduzierte Bereiche des Codes ausblenden. Im Dialogfeld **Seite einrichten** können Sie auch festlegen, dass der vollständige Pfad und der Dateiname gedruckt werden, indem Sie **Kopfzeile** auswählen.<br /><br /> Sie können Farbdruckoptionen im Dialogfeld **Tools** > **Optionen** > **Umgebung** > **Schriftarten und Farben** festlegen. Wählen Sie **Drucker** in der Liste **Einstellungen anzeigen für** aus, um den Farbdruck anzupassen. Sie können zum Drucken einer Datei andere Farben als beim Bearbeiten der Datei angeben.|
|Globales Rückgängigmachen und Wiederholen|Mithilfe der Befehle **Letzte globale Aktion rückgängig machen** und **Letzte globale Aktion wiederholen** im Menü **Bearbeiten** werden globale Aktionen, die sich auf mehrere Dateien auswirken, rückgängig gemacht oder wiederholt. Globale Aktionen beinhalten das Umbenennen einer Klasse oder eines Namespaces, das Durchführen eines Such- und Ersetzungsvorgangs in einer Projektmappe, die Umgestaltung einer Datenbank oder eine beliebige andere Aktion, die mehrere Dateien ändert. Sie können die Befehle zum globalen Rückgängigmachen und Wiederholen auf Aktionen in der aktuellen Visual Studio-Sitzung anwenden, sogar nachdem Sie die Projektmappe geschlossen haben, in der eine Aktion angewendet wurde.|

## <a name="advanced-editing-features"></a>Erweiterte Bearbeitungsfunktionen

Einige erweiterte Funktionen befinden sich auf der Symbolleiste im Menü **Bearbeiten** > **Erweitert**. Nicht alle diese Funktionen sind für alle Arten von Codedateien verfügbar.

|Feature|Beschreibung|
|-|-|
|Dokument formatieren|Legt den richtigen Einzug von Codezeilen fest und verschiebt geschweifte Klammern in separate Zeilen im Dokument.|
|Auswahl formatieren|Legt den richtigen Einzug von Codezeilen fest und verschiebt geschweifte Klammern in separate Zeilen in der Auswahl.|
|Ausgewählte Zeilen mit Tabstopps versehen|Ändert führende Leerzeichen ggf. in Tabstopps.|
|Tabstopps aus ausgewählten Zeilen entfernen|Ändert führende Tabstopps in Leerzeichen. Wenn Sie in einer Datei alle Leerzeichen in Tabstopps (oder alle Tabstopps in Leerzeichen) konvertieren möchten, können Sie dazu die Befehle `Edit.ConvertSpacesToTabs` und `Edit.ConvertTabsToSpaces` verwenden. Diese Befehle werden nicht in Visual Studio-Menüs angezeigt. Sie können sie jedoch über das **Schnellzugriffsfenster** oder das Befehlsfenster aufrufen.|
|In Großbuchstaben umwandeln|Wandelt alle Zeichen in der Auswahl in Großbuchstaben um. Wenn keine Auswahl vorhanden ist, wird das Zeichen an der Einfügemarke in Großbuchstaben dargestellt. Tastenkombination: **STRG**+**UMSCHALT**+**U**.|
|In Kleinbuchstaben umwandeln|Wandelt alle Zeichen in der Auswahl in Kleinbuchstaben um. Wenn keine Auswahl vorhanden ist, wird das Zeichen an der Einfügemarke in Kleinbuchstaben dargestellt. Tastenkombination: **STRG**+**U**.|
|Ausgewählte Zeilen nach oben verschieben|Verschiebt die ausgewählte Zeilen um eine Zeile nach oben Tastenkombination: **ALT**+**NACH-OBEN-TASTE**|
|Ausgewählte Zeilen nach unten verschieben|Verschiebt die ausgewählte Zeile um eine Zeile nach unten. Tastenkombination: **ALT**+**NACH-UNTEN-TASTE**|
|Horizontale Leerstelle löschen|Löscht Tabstopps oder Leerzeichen am Ende der aktuellen Zeile. Tastenkombination: **STRG**+**K**, **STRG**+ **\\**|
|Leerstelle anzeigen|Zeigt Leerzeichen als Hochpunkte und Tabstopps als Pfeile an. Das Ende einer Datei wird als rechteckiges Symbol angezeigt. Wenn die Option **Tools** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **Zeilenumbruch** > **Sichtbare Glyphen für Zeilenumbruch anzeigen** ausgewählt ist, wird diese Glyphe ebenfalls angezeigt.|
|Zeilenumbruch|Bewirkt, dass alle Zeilen in einem Dokument im Codefenster sichtbar sind. Sie können den Zeilenumbruch in den **Text-Editor-Einstellungen für alle Sprachen** aktivieren und deaktivieren (**Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen**).|
|Auswahl kommentieren|Fügt Kommentarzeichen zur Auswahl oder aktuellen Zeile hinzu. Tastenkombination: **STRG**+**K**, **STRG**+**C**|
|Kommentar aus Auswahl entfernen|Entfernt Kommentarzeichen aus der Auswahl oder der aktuellen Zeile. Tastenkombination: **STRG**+**K**, **STRG**+**U**|
|Zeileneinzug vergrößern|Fügt eine Registerkarte (oder die entsprechenden Leerzeichen) zu den ausgewählten Zeilen oder zur aktuellen Zeile hinzu.|
|Zeileneinzug verkleinern|Entfernt eine Registerkarte (oder die entsprechenden Leerzeichen) aus den ausgewählten Zeilen oder der aktuellen Zeile.|
|Tag auswählen|Wählt das Tag in einem Dokument aus, das Tags enthält (zum Beispiel XML oder HTML).|
|Tag-Inhalt auswählen|Wählt den Tag-Inhalt in einem Dokument aus, das Tags enthält (zum Beispiel XML oder HTML).|

## <a name="navigate-and-find-code"></a>Navigieren und Suchen von Code

Es gibt verschiedene Möglichkeiten, um im Code-Editor zu navigieren: Sie können zwischen den Einfügepunkten vor- und zurückgehen, die Definition eines Typs oder Members abrufen und über die Navigationsleiste auf eine bestimmte Methode springen. Weitere Informationen finden Sie unter [Navigieren durch den Code](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Suchen von Verweisen in der Codebasis

Um den Ort zu finden, an dem bestimmte Codeelemente in Ihrer gesamten Codebasis verwiesen werden, können Sie den Befehl **Alle Verweise suchen** oder **UMSCHALT**+**F12** verwenden. Wenn Sie außerdem auf einen Typ oder Member klicken, hebt die Funktion **Reference Highlighting** („Hervorheben von Verweisen“) automatisch alle Verweise auf diesen Typ oder Member hervor. Weitere Informationen finden Sie unter [Suchen von Verweisen im Code](finding-references.md).

## <a name="customize-the-editor"></a>Anpassen des Editors

Sie können im Menü **Extras** unter **Assistent zum Importieren und Exportieren von Einstellungen** Ihre Visual Studio-Einstellungen für einen anderen Entwickler freigeben, die Einstellungen an einen Standard anpassen oder zu den Visual Studio-Standardeinstellungen zurückkehren. Im **Assistent zum Importieren und Exportieren von Einstellungen** können Sie ausgewählte allgemeine Einstellungen oder Sprachen sowie projektspezifische Einstellungen ändern.

Um neue Hotkeys zu definieren oder vorhandene Hotkeys neu zu definieren, wechseln Sie zu **Tools** > **Optionen** > **Umgebung** > **Tastatur**. Weitere Informationen zu Hotkeys finden Sie unter [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Informationen zu JavaScript-spezifischen Editor-Optionen finden Sie unter [JavaScript-Editor-Optionen](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Siehe auch

- [Quellcode-Editor (Visual Studio für Mac)](/visualstudio/mac/source-editor)
- [Visual Studio-IDE](../get-started/visual-studio-ide.md)
- [Erste Schritte mit C++ in Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Erste Schritte mit C# und ASP.NET in Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Erste Schritte mit Python in Visual Studio](../ide/quickstart-python.md)
