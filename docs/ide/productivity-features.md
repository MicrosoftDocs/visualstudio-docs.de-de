---
title: Produktivitätsleitfaden
description: Erfahren Sie mehr über die Tastenkombinationen und Produktivitätsfunktionen in Visual Studio, die Ihnen helfen können, Code effizient zu schreiben, Code zu Debuggen und Fehler zu behandeln.
ms.custom: SEO-VS-2020
ms.date: 4/29/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 01367d821ffc74de0e9d087bfe52680508fad9e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951159"
---
# <a name="productivity-guide-for-visual-studio"></a>Produktivitätsleitfaden für Visual Studio

Wenn Sie beim Schreiben von Code Zeit sparen möchten, sind Sie hier richtig. Dieser Produktivitätsleitfaden enthält Tipps, die Sie bei ersten Schritten mit Visual Studio, beim Schreiben von Code, beim Debuggen von Code, beim Behandeln von Fehlern und bei der Verwendung von Tastenkombinationen unterstützen können. Und all dies auf einer Seite.

Informationen zu nützlichen Tastenkombinationen finden Sie unter [Tastenkombinationen für die Produktivität](../ide/productivity-shortcuts.md). Eine vollständige Liste von Tastenkombinationen für Befehle finden Sie unter [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="get-started"></a>Erste Schritte

Sparen Sie Zeit beim Durchforsten von Menüs, indem Sie schnell nach allem suchen, was Sie benötigen, einschließlich Befehlen, Einstellungen, Dokumentation und Installationsoptionen. Zeigen Sie Tastenkombinationen für Befehle innerhalb Ihrer Suchergebnisse in Visual Studio an, damit Sie sich diese leichter merken können. 

- **Mock-Code mit Aufgabenliste**. Wenn Sie nicht genügend Anforderungen haben, um ein Codesegment zu vervollständigen, verwenden Sie die Aufgabenliste, um Codekommentare, die Token wie `TODO` und `HACK` verwenden, nachzuverfolgen und um Verknüpfungen zu verwalten, mit denen Sie direkt zu einem vordefinierten Speicherort im Code gelangen. Weitere Informationen finden Sie unter [Verwenden der Aufgabenliste](../ide/using-the-task-list.md).

- **Verwenden von Tastenkombinationen im Projektmappen-Explorer**. Wenn Sie mit Visual Studio noch nicht vertraut sind, sind diese Tastenkombinationen praktisch und sparen Ihnen Zeit, während Sie schnell mit einer neuen Codebase arbeiten. Eine vollständige Liste der Tastenkombinationen finden Sie unter [Standardtastenkombinationen in Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL).

- **[Identifizieren und Anpassen von Tastenkombinationen in Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)** . Sie können Tastenkombinationen für Visual Studio-Befehle nachschlagen, diese Tastenkombinationen anpassen und sie dann exportieren, damit andere Benutzer sie verwenden können. Sie können eine Tastenkombination im Dialogfeld „Optionen“ immer nachschlagen und ändern.

- **Größere Barrierefreiheit in Visual Studio**. Visual Studio verfügt über integrierte Barrierefreiheitsfunktionen, die mit Sprachausgaben und anderen Hilfstechnologien kompatibel sind. Eine vollständige Liste der verfügbaren Funktionen finden Sie unter [Tipps und Tricks zur Barrierefreiheit für Visual Studio](../ide/reference/accessibility-tips-and-tricks.md). 

- **Informieren Sie sich über den Projektlebenszyklus und die Wartung in Visual Studio**. Informationen dazu, wie Sie Updates für Visual Studio, Supportoptionen für Enterprise- und Professional-Kunden, Support für ältere Versionen von Visual Studio und Komponenten erhalten, die nicht von der Visual Studio-Wartung abgedeckt werden, finden Sie unter [Produktlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing). 

- **Installieren und Verwalten von NuGet-Paketen in Visual Studio**. Über die Benutzeroberfläche des NuGet-Paket-Managers in Visual Studio können Sie auf einfache Weise NuGet-Pakete in Projekten und Lösungen installieren, deinstallieren und aktualisieren. Weitere Informationen finden Sie unter [Installieren und Verwalten von Paketen in Visual Studio mit dem NuGet-Paket-Manager](/nuget/consume-packages/install-use-packages-visual-studio).

## <a name="write-code"></a>Schreiben von Code

Schreiben Sie Code schneller, indem Sie die folgenden Funktionen verwenden.

- **Verwenden von benutzerfreundlichen Befehlen**. Visual Studio verfügt über verschiedene Befehle, mit denen Sie gängige Bearbeitungsaufgaben schneller bewerkstelligen können. Beispielsweise können Sie einen Befehl auswählen, um ganz einfach eine Codezeile zu duplizieren, ohne diese kopieren, die Position des Cursors ändern und die Zeile einfügen zu müssen. Wählen Sie **Bearbeiten** > **Duplizieren** oder drücken Sie die Tasten **STRG**+**E**,**V**. Sie können eine Auswahl von Texten rasch erweitern oder verkleinern, indem Sie **Bearbeiten** > **Erweitert** > **Auswahl erweitern** oder **Bearbeiten** > **Erweitert** > **Auswahl verkleinern** auswählen oder die Tasten **UMSCHALT**+**ALT**+ **=** oder **UMSCHALT**+**ALT**+ **-** drücken.

- **Verwenden von IntelliSense**. Wie Sie Code im Editor eingeben, werden IntelliSense-Informationen, wie Listenmember, Parameterinformationen, QuickInfos, Signaturhilfe und Wortvervollständigung angezeigt. Diese Funktionen unterstützen Fuzzyübereinstimmung des Texts. So umfasst die Ergebnisliste für die Listenmember nicht nur Einträge, die mit dem Zeichen beginnen, das Sie eingegeben haben, sondern auch Einträge, die die Zeichenkombination an einer beliebigen Stelle im Namen enthalten. Weitere Informationen finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md).

- **Ändern der Optionen für Autoeinfügung von IntelliSense bei der Codeeingabe**. Wenn Sie den Vorschlagsmodus in IntelliSense umschalten, können Sie festlegen, dass IntelliSense-Optionen nur eingefügt werden, wenn Sie sie explizit auswählen.

     Um den Vorschlagmodus zu aktivieren, drücken Sie die Tasten **STRG**+**ALT**+**LEERTASTE**, oder klicken Sie in der Menüleiste auf **Bearbeiten** > **IntelliSense** > **Beendigungsmodus umschalten**.

- **Verwenden von Codeausschnitten**. Sie können die integrierten Ausschnitte verwenden oder eigene Ausschnitte erstellen.

     Zum Einfügen eines Ausschnittes wählen Sie in der Menüleiste **Bearbeiten** > **IntelliSense** > **Ausschnitt einfügen** oder **Umschließen mit** aus, oder öffnen Sie das Kontextmenü in einer Datei, und wählen Sie **Ausschnitt** > **Ausschnitt einfügen** oder **Umschließen mit** aus. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).

- **Inline-Behebung von Codefehlern**. Mit schnellen Aktionen können Sie ganz leicht Code mit einer einzelnen Aktion umgestalten, generieren oder anderweitig ändern. Diese Aktionen können mithilfe des Schraubendrehers ![Schraubendrehersymbol](media/screwdriver-icon.png) oder der Glühbirne ![Glühbirnensymbol](media/light-bulb-icon.png) oder durch Drücken der Tasten **Alt**+**EINGABETASTE** oder **STRG**+ **.** angewendet werden, wenn sich Ihr Cursor in der entsprechenden Codezeile befindet. Weitere Informationen finden Sie unter [Schnelle Aktionen](quick-actions.md).

- **Anzeigen und Bearbeiten der Definition eines Codeelements**. Sie können das Modul schnell anzeigen und bearbeiten, in dem ein Codeelement, wie ein Member, eine Variable oder eine lokale Variable, definiert ist.

    Um eine Definition in einem Popupfenster zu öffnen, markieren Sie das Element, und drücken Sie dann die Tasten **ALT**+**F12**, oder öffnen Sie das Kontextmenü für das Element, und klicken Sie dann auf **Definition einsehen**. Um eine Definition in einem separaten Codefenster zu öffnen, öffnen Sie das Kontextmenü für das Codeelement, und wählen Sie dann **Gehe zu Definition** aus.

- **Verwenden von Beispielanwendungen**. Sie können Anwendungsentwicklung beschleunigen, indem Sie Beispielanwendungen von [Microsoft Developer Network](https://code.msdn.microsoft.com/) herunterladen und installieren. Sie können eine bestimmte Technologie oder ein Programmierkonzept auch kennenlernen, indem Sie ein Beispielpaket für diesen Bereich herunterladen und untersuchen.

- **Ändern der Klammerformatierung durch Formatierung/Neue Zeilen**. Auf der Optionsseite **Formatierung** können Sie Optionen zur Formatierung von Code im Code-Editor festlegen, z. B. auch neue Zeilen. Weitere Informationen zur Verwendung dieser Einstellung in C# finden Sie im [Dialogfeld „Optionen“: Text-Editor > C# > Codeformat > Formatierung](../ide/reference/options-text-editor-csharp-formatting.md). Informationen zu C++ finden Sie unter [Festlegen der C++-Codierungseinstellungen in Visual Studio](/cpp/ide/how-to-set-preferences). Informationen zu Python finden Sie unter [Formatieren von Python-Code](../python/formatting-python-code.md).

- **Ändern des Einzugs mit Tabstoppzeichen**. Verwenden Sie benutzerdefinierte Editor-Einstellungen, die auf jede CodeBase individuell zugeschnitten sind, um einen konsistente Codierungsstil für mehrere Entwickler zu erzwingen, die an demselben Projekt mit verschiedenen Editoren und IDEs arbeiten. Stellen Sie sicher, dass Ihr gesamtes Team dieselben Sprachkonventionen, Benennungskonventionen und Formatierungsregeln befolgt. Da diese benutzerdefinierten Einstellungen portabel sind und mit Ihrem Code weitergegeben werden, können Sie Codierungsstile auch außerhalb von Visual Studio durchsetzen. Weitere Informationen finden Sie unter [Optionen, Text-Editor, Alle Sprachen, Tabstoppzeichen](../ide/reference/options-text-editor-all-languages-tabs.md#tabs).

## <a name="navigate-within-your-code-and-the-ide"></a>Navigieren innerhalb des Codes und der IDE

Sie können verschiedene Methoden verwenden, um bestimmte Positionen im Code schneller zu finden und dorthin zu wechseln. Sie können auch das Layout Ihrer Visual Studio-Fenster basierend auf Ihren Einstellungen ändern. 

- **Speichern von Codezeilen als Lesezeichen**. Sie können Lesezeichen verwenden, um schnell zu bestimmten Codezeilen in einer Datei zu navigieren.

    Wählen Sie zum Festlegen einer Textmarke in der Menüleiste **Bearbeiten** > **Textmarken** > **Textmarke umschalten** aus. Sie können alle Lesezeichen für eine Projektmappe im Fenster **Lesezeichen** anzeigen. Weitere Informationen finden Sie unter [Festlegen von Lesezeichen im Code](../ide/setting-bookmarks-in-code.md).

- **Suchen nach Symboldefinitionen in einer Datei**. Sie können in einer Projektmappe nach Symboldefinitionen und Dateinamen suchen. Die Suchergebnisse enthalten jedoch keine Namespaces oder lokalen Variablen.

   Um auf dieses Feature zuzugreifen, wählen Sie in der Menüleiste **Bearbeiten** > **Navigieren zu** aus.

- **Durchsuchen der Gesamtstruktur des Codes**. Im **Projektmappen-Explorer** können Sie Klassen und ihre Typen und Member in den Projekten suchen. Sie können auch nach Symbolen suchen, die Aufrufhierarchie einer Methode anzeigen, Symbolverweise suchen und andere Aufgaben ausführen. Wenn Sie ein Codeelement im **Projektmappen-Explorer** auswählen, wird die dazugehörige Datei auf einer Registerkarte **Vorschau** angezeigt, und der Cursor wird auf das Element in der Datei verschoben. Weitere Informationen finden Sie unter [Anzeigen der Codestruktur](../ide/viewing-the-structure-of-code.md).

- **Springen zu einer Position in einer Datei mit dem Zuordnungsmodus**. Im Zuordnungsmodus werden Codezeilen als Miniaturansicht auf der Scrollleiste angezeigt. Weitere Informationen zu diesem Anzeigemodus finden Sie unter [Vorgehensweise: Anpassen der Scrollleiste](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode).

- **Verstehen der Codestruktur mit Code Map**. Codezuordnungen können Sie dabei unterstützen, Abhängigkeiten im gesamten Code visuell darzustellen und zu erkennen, wie diese zusammenspielen, ohne dass Dateien und Codezeilen gelesen werden müssen. Weitere Informationen finden Sie unter [Map dependencies with code maps (Zuordnen von Abhängigkeiten mit Code Maps)](../modeling/map-dependencies-across-your-solutions.md).

- **Weitere Informationen finden Sie unter „Häufig verwendete Dateien mit Bearbeiten/Zu zuletzt verwendeter Datei wechseln“** . Verwenden Sie die Wechseln zu-Befehle in Visual Studio, um eine zielgerichtete Suche in Ihrem Code auszuführen, damit Sie angegebene Elemente schneller finden. Ausführliche Anweisungen finden Sie unter [Suchen nach Code mithilfe von „Wechseln zu“-Befehlen](../ide/go-to.md).

- **Verschieben des [Fensters „Eigenschaften“](../ide/reference/properties-window.md) auf die rechte Seite**. Wenn Sie ein vertrauteres Fensterlayout bevorzugen, können Sie das Fenster „Eigenschaften“ in Visual Studio verschieben, indem Sie **F4** drücken.

## <a name="find-items-faster"></a>Schnelleres Suchen von Elementen

Sie können in der IDE nach Befehlen, Dateien und Optionen suchen und gleichzeitig die Inhalte der Toolfenster filtern, um relevante Informationen nur für die aktuelle Aufgabe anzuzeigen.

- **Filtern der Inhalte von Toolfenstern**. Sie können in den Inhalten vieler Toolfenster, z. B. der Fenster **Toolbox**, **Eigenschaften** und im **Projektmappen-Explorer** suchen. Es werden aber nur Elemente angezeigt, deren Namen die Zeichen enthalten, die Sie angeben.

- **Zeigen Sie nur die Fehler an, die berücksichtigt werden sollen**. Wenn Sie die Schaltfläche **Filter** auf der Symbolleiste **Fehlerliste** auswählen, können Sie die Anzahl der Fehler reduzieren, die im Fenster **Fehlerliste** angezeigt werden. Sie können nur die Fehler in den Dateien anzeigen, die im Editor geöffnet sind, nur die Fehler in der aktuellen Datei oder nur die Fehler im aktuellen Projekt. Sie können im Fenster **Fehlerliste** auch nach bestimmten Fehlern suchen.

- **Suchen von Dialogfeldern, Menübefehlen, Optionen und mehr**. Geben Sie im Suchfeld Schlüsselwörter oder Ausdrücke für die Elemente ein, die Sie suchen. Beispielsweise werden die folgenden Optionen angezeigt, wenn Sie **Neues Projekt** eingeben:

   ::: moniker range="vs-2017"

   ![Schnellstartergebnisse für "Neues Projekt"](../ide/media/productivity_quicklaunch.png)

   **Schnellstart** zeigt unter anderem Links zum Erstellen eines neuen Projekts, zum Hinzufügen eines neuen Elements zu einem Projekt und zum Wechseln zur Seite **Projekte und Projektmappen** im Dialogfeld **Optionen** an. Zu den Suchergebnissen können auch Projektdateien und Toolfenster zählen.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Screenshot: Suchergebnisse für „new project“ (Neues Projekt)](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Drücken Sie **STRG**+**Q**, um direkt zum Suchfeld zu wechseln.

## <a name="debug-code"></a>Debuggen von Code

Debuggen kann viel Zeit in Anspruch nehmen, aber die folgenden Tipps können Ihnen helfen, den Prozess zu beschleunigen.

- **Verwenden der Visual Studio-Debuggertools**. Wenn Sie *Ihre App im Visual Studio-Kontext debuggen*, bedeutet dies in der Regel, dass Sie die Anwendung im Debugmodus ausführen. Der Debugger bietet viele Möglichkeiten zum Ermitteln der Aktionen Ihres Codes während der Ausführung. Eine Anleitung für die ersten Schritte finden Sie unter [Erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md). 

- **Testen Sie die gleiche Seite, Anwendung oder Website in unterschiedlichen Browsern**. Wenn Sie den Code debuggen, können Sie zwischen den installierten Webbrowsern, einschließlich [Seitenprüfung (Visual Studio)](/previous-versions/hh974728(v=vs.140)), problemlos wechseln, ohne dass Sie das Dialogfeld **Browserauswahl** öffnen müssen. Sie können die Liste **Debugziel** verwenden, die auf der Symbolleiste **Standard** neben der Schaltfläche **Debuggen starten** zu finden ist, um beim Debuggen oder Anzeigen von Seiten schnell zu überprüfen, welchen Browser Sie verwenden.

    ![Auswählen von Debuggingoptionen für den Webbrowser](../ide/media/webbrowserdropdowntoolbar.png)

- **Legen Sie temporäre Haltepunkte fest**. Sie können einen temporären Haltepunkt in der aktuellen Zeile des Codes erstellen und gleichzeitig den Debugger starten. Wenn Sie diese Codezeile erreicht haben, gibt der Debugger Unterbrechungsmodus ein. Weitere Informationen finden Sie unter [Navigate through code with the debugger (Navigieren im Code mit dem Debugger)](../debugger/navigating-through-code-with-the-debugger.md).

    Drücken Sie die Tasten **STRG**+**F10**, um dieses Feature zu verwenden, oder öffnen Sie das Kontextmenü für die Codezeile, bei der Sie unterbrechen möchten, und klicken Sie dann auf **Ausführen bis Cursor**.

- **Verschieben Sie den Ausführungspunkt während des Debuggens**. Sie können den aktuellen Ausführungspunkt zu einem anderen Codeabschnitt verschieben und Debuggen von diesem Punkt neu starten. Diese Methode ist hilfreich, wenn Sie einen Codeabschnitt debuggen möchten, ohne alle Schritte neu erstellen zu müssen, die erforderlich sind, um diesen Abschnitt zu erreichen. Weitere Informationen finden Sie unter [Navigate through code with the debugger (Navigieren im Code mit dem Debugger)](../debugger/navigating-through-code-with-the-debugger.md).

     Ziehen Sie die gelbe Pfeilspitze zu einer Position, an der Sie die folgende Anweisung in derselben Quelldatei festlegen möchten, um den Ausführungspunkt zu verschieben, und drücken Sie dann **F5**, um das Debuggen fortzusetzen.

- **Erfassen Sie Wertinformationen für Variablen**. Sie können einer Variablen im Code einen DataTip hinzufügen und diesen fixieren, damit Sie auf den letzten bekannten Wert für die Variable zugreifen können, nachdem der Debugvorgang abgeschlossen hat. Weitere Informationen finden Sie unter [Anzeigen von Datenwerten als Datentipps](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Zum Hinzufügen eines DataTips muss sich der Debugger im Unterbrechungsmodus befinden. Platzieren Sie den Cursor in der Variablen, und wählen Sie dann die Anheftschaltfläche auf dem angezeigten DataTip aus. Wenn das Debuggen beendet wird, wird in der Quelldatei ein blaues Anheftsymbol neben der Codezeile angezeigt, die die Variable enthält. Wenn Sie auf den blauen Pin zeigen, wird der Wert der Variablen aus der letzten Debugsitzung angezeigt.

- **Löschen Sie das Direktfenster**. Sie können den Inhalt des [Direktfensters](../ide/reference/immediate-window.md) zur Entwurfszeit löschen, indem Sie `>cls` oder `>Edit.ClearAll` eingeben.

     Weitere Informationen zu weiteren Befehlen finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).

- **[Ermitteln von Änderungen am Code und anderer Verläufe mit CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)** . Mit CodeLens können Sie sich auf Ihre Arbeit konzentrieren, während Sie ermitteln, was mit Ihrem Code geschehen ist. Dazu müssen Sie nicht einmal den Editor schließen. Suchen Sie Verweise auf Codeabschnitte und -änderungen, verknüpfte Fehler, Arbeitselemente, Code Reviews und Komponententests.

- **Verwenden von Live Share, um in Echtzeit mit anderen Entwicklern zu debuggen**. Live Share ermöglicht Ihnen gemeinsames Bearbeiten und Debuggen mit anderen in Echtzeit – unabhängig von Ihren verwendeten Programmiersprachen oder erstellten App-Typen. Weitere Informationen finden Sie unter [Was ist Visual Studio Live Share?](/visualstudio/liveshare/)

- **Verwenden Sie des interaktiven Fensters zum Schreiben und Testen von kleinen Codeanschnitten**. Visual Studio bietet ein interaktives REPL-Fenster (Read-Evaluate-Print-Loop), mit dem Sie beliebigen Code eingeben und unmittelbare Ergebnisse anzeigen können. Diese Art der Codierung unterstützt Sie beim Lernen und Experimentieren mit APIs und Bibliotheken und beim interaktiven Entwickeln von funktionierendem Code, den Sie in Ihre Projekte einfügen können. Weitere Informationen für Python finden Sie unter [Arbeiten mit dem interaktiven Python-Fenster](../python/python-interactive-repl-in-visual-studio.md). Die Funktion „Interaktives Fenster“ ist auch für C# verfügbar. 

## <a name="access-visual-studio-tools"></a>Zugreifen auf Visual Studio-Tools

Sie können schnell auf die Developer-Eingabeaufforderung oder auf ein anderes Visual Studio-Tool zugreifen, wenn Sie diese bzw. dieses im Startmenü oder in der Taskleiste fixieren.

::: moniker range="vs-2017"

1. Navigieren Sie im Windows-Explorer zu *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Navigieren Sie im Windows-Explorer zu *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.

::: moniker-end

2. Klicken Sie mit der rechten Maustaste darauf, oder öffnen Sie das Kontextmenü, um **Developer-Eingabeaufforderung** auszuwählen. Wählen Sie dann **An "Start" anheften** oder **An Taskleiste anheften** aus.

## <a name="manage-files-toolbars-and-windows"></a>Verwalten von Dateien, Symbolleisten und Fenstern

Bei der Entwicklung einer Anwendung möchten Sie jederzeit in mehreren Codedateien arbeiten und sich in mehreren Toolfenstern bewegen können. Mit folgenden Tipps behalten Sie die Übersicht:

- **Halten Sie Dateien, die Sie häufig verwenden, im Editor sichtbar**. Sie können die Dateien, die Sie häufig verwenden, an der linken Seite der Registerkartenreihe anheften, damit Sie unabhängig davon, wie viele Dateien im Editor geöffnet sind, sichtbar bleiben.

   Um eine Datei anzuheften, wählen Sie die Registerkarte der Datei, und wählen Sie dann die Schaltfläche **Anheftstatus umschalten** aus.

- **Verschieben Sie Dokumente und Fenster auf andere Bildschirme**. Wenn Sie bei der Entwicklung einer Anwendung mehr als einen Bildschirm verwenden, können Sie leichter an Teilen der Anwendung arbeiten, wenn Sie Dateien, die im Editor geöffnet sind, auf einen anderen Bildschirm verschieben. Sie können Toolfenster, wie z.B. Debuggerfenster, auf einen anderen Bildschirm verschieben und Dokument- und -Toolfenster miteinander verbinden, um „Flösse“ zu erstellen. Weitere Informationen finden Sie unter [Anpassen der Fensterlayouts in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Sie können Dateien auch einfacher verwalten, indem Sie eine weitere Instanz des **Projektmappen-Explorers** erstellen und sie auf einen anderen Bildschirm verschieben. Um eine andere Instanz des **Projektmappen-Explorers** zu erstellen, öffnen Sie ein Kontextmenü im **Projektmappen-Explorer**, und wählen Sie dann **Neue Projektmappen-Explorer-Ansicht** aus.

- **Passen Sie die Schriftarten an, die in Visual Studio angezeigt werden**. Sie können die Schriftart, Größe und Farbe ändern, die für Text in der IDE verwendet wird. Beispielsweise können Sie die Farbe von bestimmten Codeelementen im Editor und die Schriftart in Toolfenstern oder in der IDE anpassen. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern von Schriftarten und Farben in Visual Studio](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) und [Vorgehensweise: Ändern der im Editor in Visual Studio 2017 verwendeten Schriftarten und Farben](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Siehe auch

- [Blogbeitrag mit Tipps und Tricks zu Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Standardtastenkombinationen für häufig verwendete Befehle](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [How to: Anpassen von Menüs und Symbolleisten in Visual Studio](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Tutorial: Create a simple application with C# or Visual Basic (Tutorial: Erstellen einer einfachen Anwendung mit C# oder Visual Basic)](../get-started/csharp/tutorial-wpf.md)
- [Tipps und Tricks zur Barrierefreiheit](../ide/reference/accessibility-tips-and-tricks.md)