---
title: XAML-Code-Editor
description: Lernen Sie den XAML-Code-Editor in Visual Studio kennen
ms.date: 06/16/2020
ms.topic: overview
monikerRange: vs-2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 29fa854ab00764fc0166a53d8b48989f2c74f036
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833298"
---
# <a name="xaml-code-editor"></a>XAML-Code-Editor

Der XAML-Code-Editor in der [Visual Studio-IDE](../get-started/visual-studio-ide.md) enthält alle Tools, die Sie zum Erstellen von WPF- und UWP-Apps für die Windows-Plattform und für [Xamarin.Forms](/xamarin/xamarin-forms/user-interface/text/editor/) benötigen. In diesem Artikel wird die Rolle des Code-Editors bei der Entwicklung von XAML-basierten Apps beschrieben und es werden die Funktionen des XAML-Code-Editors in Visual Studio 2019 erläutert.

Betrachten wir zunächst einmal die IDE (Integrated Development Environment, integrierte Entwicklungsumgebung) anhand eines geöffneten WPF-Projekts. In der folgenden Abbildung sind zentrale IDE-Tools dargestellt, die im XAML-Code-Editor verwendet werden.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="Die IDE in Visual Studio 2019 anhand eines geöffneten WPF-Projekts in XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

Die zentralen IDE-Tools von unten links im Uhrzeigersinn:

- Das Fenster **[XAML-Code-Editor](#xaml-code-editor-ui)**  – Thema dieses Artikels. Hier wird Code erstellt und bearbeitet.
- Das Fenster **[XAML-Designer](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** . Hier wird die Benutzeroberfläche entworfen.
- Das andockbare Fenster **[Toolbox](../ide/reference/toolbox.md)** . Hier werden der Benutzeroberfläche Steuerelemente hinzugefügt.
- Die Schaltfläche **[Debuggen](../debugger/debugger-feature-tour.md)** . Damit wird Code ausgeführt und gedebuggt. <br>(Code kann beim Debuggen mit [XAML Hot Reload](xaml-hot-reload.md) auch in Echtzeit bearbeitet werden.)
- Das Fenster **[Projektmappen-Explorer](../ide/solutions-and-projects-in-visual-studio.md)** . Hier werden Dateien, Projekte und Projektmappen verwaltet.
- Das Fenster **[Eigenschaften](../ide/reference/properties-window.md)** . Hier werden die Darstellung der Benutzeroberfläche und die Funktionsweise der Steuerelemente geändert.

Im Folgenden erfahren Sie mehr über den XAML-Code-Editor.

## <a name="xaml-code-editor-ui"></a>Benutzeroberfläche des XAML-Code-Editors

Das Code-Editor-Fenster für XAML-Apps enthält einige Benutzeroberflächenelemente, die auch in der Standard-IDE angezeigt werden. Darüber hinaus enthält es jedoch auch einige Funktionen, die nur in diesem Fenster zu finden sind und die die Entwicklung von XAML-Apps erleichtern.

Und so sieht das Fenster des XAML-Code-Editors aus.

![Das Fenster des XAML-Code-Editors in Visual Studio](media/xaml-code-editor-window.png "Screenshot: Fenster des XAML-Code-Editors in Visual Studio 2019")

Sehen wir uns als Nächstes nun die Funktionen der einzelnen Benutzeroberflächenelemente im Code-Editor an.

### <a name="first-row"></a>Erste Leiste

In der ersten Leiste oben im XAML-Code-Fenster sehen Sie links die Registerkarte **Entwurf**, die Schaltfläche **Bereiche austauschen**, die Registerkarte **XAML** und die Schaltfläche **XAML aufklappen**.

![Die ersten beiden oberen Leisten des Fensters von XAML-Code-Editor in Visual Studio: die linke Seite der ersten Leiste ist hervorgehoben](media/xaml-code-editor-top-row-left.png "Screenshot: Die ersten beiden oberen Leisten des Fensters von XAML-Code-Editor in Visual Studio 2019, in dem Benutzeroberflächenelemente auf der linken Seite hervorgehoben sind")

Funktionsweise:

- Über die Registerkarte **Entwurf** können Sie vom XAML-Code-Editor zum XAML-Designer wechseln.
- Über die Schaltfläche **Bereiche austauschen** können Sie in der IDE vom XAML-Designer zum XAML-Code-Editor wechseln.
- Über die Registerkarte **XAML** können Sie wieder zum XAML-Code-Editor wechseln.
- Über die Schaltfläche **XAML aufklappen** können Sie ein neues XAML-Code-Editor-Fenster außerhalb der IDE erstellen.

Auf der rechten Seite befinden sich die Schaltflächen **Vertikale Aufteilung**, **Horizontale Aufteilung** und **Bereiche zuklappen**.

![Die ersten beiden oberen Leisten des Fensters von XAML-Code-Editor in Visual Studio: Die rechte Seite der ersten Leiste ist hervorgehoben.](media/xaml-code-editor-top-row-right.png "Screenshot: Die ersten beiden oberen Leisten des Fensters von XAML-Code-Editor in Visual Studio 2019, in dem Benutzeroberflächenelemente auf der rechten Seite hervorgehoben sind")

Funktionsweise:

- Über die Schaltfläche **Vertikale Aufteilung** können Sie die Ausrichtung des XAML-Designers und des XAML-Code-Editors von horizontal in vertikal ändern.
- Über die Schaltfläche **Horizontale Aufteilung** können Sie die Ausrichtung des XAML-Designers und des XAML-Code-Editors von vertikal in horizontal ändern.
- Über die Schaltfläche **Bereiche zuklappen** können Sie den unteren Bereich (Code-Editor oder Designer) zuklappen. (Wenn Sie den unteren Bereich wieder anzeigen möchten, klicken Sie noch mal auf die Schaltfläche, die dann **Bereich aufklappen** heißt.)

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Zweite Leiste

In der zweiten Leiste oben im XAML-Code-Fenster befinden sich zwei Dropdownlisten mit der Bezeichnung „Fenster“. Wenn Sie die QuickInfo für diese Benutzeroberflächenelemente anzeigen, werden sie näher bezeichnet mit „Element: Fenster“ und „Member: Fenster“.

![Die zweite der beiden oberen Leisten im Fenster des XAML-Code-Editors in Visual Studio: Beide Dropdownlisten mit der Bezeichnung „Fenster“ werden angezeigt.](media/xaml-code-editor-top-row-windows.png "Screenshot: Die zweite der beiden oberen Leisten im Fenster des XAML-Code-Editors in Visual Studio 2019, in dem beide Dropdownlisten mit der Bezeichnung „Fenster“ werden angezeigt")

Die Dropdownlisten mit der Bezeichnung „Fenster“ haben unterschiedliche Funktionen:

- Über die Dropdownliste **Element: Fenster** links können Sie gleichgeordnete oder übergeordnete Elemente anzeigen oder zu ihnen navigieren.

  Vor allem wird hier jedoch eine Gliederung mit der Tagstruktur des Codes angezeigt. Wenn Sie in der Liste ein Element auswählen, wird im Code-Editor die Codezeile mit dem ausgewählten Element angezeigt.

    ![Die Dropdownliste „Element: Fenster“ in Visual Studio](media/xaml-element-window-dropdown.png "Screenshot: Dropdownliste „Element: Fenster“ in Visual Studio 2019")

- Über die Dropdownliste **Member: Fenster** rechts können Sie Attributelemente oder untergeordnete Elemente anzeigen und zu ihnen navigieren.

    Vor allem wird hier jedoch eine Liste mit den Eigenschaften im Code angezeigt. Wenn Sie in der Liste eine Eigenschaft auswählen, wird im Code-Editor die Codezeile mit der ausgewählten Eigenschaft angezeigt.

    ![Die Dropdownliste „Member: Fenster“ in Visual Studio](media/xaml-member-window-dropdown.png "Screenshot: Dropdownliste „Member: Fenster“ in Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Mittlerer Bereich, Code-Editor

Beim mittleren Bereich handelt es sich um den „Code“-Teil des XAML-Code-Editors. Er enthält die meisten Funktionen des [IDE-Code-Editors](../get-started/tutorial-editor.md). Hier werden einige allgemeine IDE-Funktionen beschrieben, die Sie bei der Entwicklung von XAML-Code nutzen können. Zudem werden die für XAML spezifischen Funktionen in der IDE beschrieben.

![Der XAML-Code-Editor, nur mittlerer Bereich, in Visual Studio](media/xaml-code-editor-middle.png "Screenshot: XAML-Code-Editor, nur mittlerer Bereich, in Visual Studio 2019")

#### <a name="quick-actions"></a>Schnelle Aktionen

Sie können [schnellen Aktionen](../ide/quick-actions.md) verwenden, um mit einer einzelnen Aktion Code umzugestalten, zu generieren oder anderweitig zu ändern.

Eine nützliche Aufgabe, die Sie mithilfe von schnellen Aktionen durchführen können ist beispielsweise die Aufgabe **Nicht benötigte Using-Direktiven entfernen** in C#-Code auf der Registerkarte **MainWindow.xaml.cs**.

Gehen Sie dazu wie folgt vor:

1. Zeigen Sie auf eine Using-Anweisung, wählen Sie das Glühbirnensymbol aus, und wählen Sie in der Dropdownliste den Eintrag **Nicht benötigte Using-Direktiven entfernen** aus.

    ![Die Option „Nicht benötigte Using-Direktiven entfernen“ im Menü „Schnelle Aktionen“ im IDE-Editor](media/xaml-code-editor-remove-usings.png "Screenshot: Die Option „Nicht benötigte Using-Direktiven entfernen“ im Menü „Schnelle Aktionen“ im IDE-Editor")

1. Geben Sie an, ob Sie alle Vorkommen im **Dokument**, im **Projekt** oder in der **Projektmappe** korrigieren möchten.
1. Rufen Sie das Dialogfeld **Vorschau** an, und wählen Sie **Anwenden** aus.

Diese Funktion ist auch in der Menüleiste verfügbar. Wählen Sie hierzu **Bearbeiten** > **IntelliSense** > **Using-Direktiven entfernen und sortieren** aus.

Weitere Informationen zu Einstellungen für Using-Direktiven finden Sie auf der Seite [Using-Direktiven sortieren](../ide/reference/sort-usings.md). Weitere Informationen zu IntelliSense finden Sie auf der Seite [IntelliSense in Visual Studio](../ide/using-intellisense.md). Weitere Informationen zu Möglichkeiten der Verwendung von schnellen Aktionen finden Sie auf der Seite [Häufige schnelle Aktionen](../ide/common-quick-actions.md).

#### <a name="change-tracking"></a>Änderungsnachverfolgung

Durch die Farbe am linken Rand können Sie die Änderungen verfolgen, die Sie an einer Datei vorgenommen haben. Im Folgenden wird beschrieben, wie von Ihnen ausgeführte Aktionen mit Farben gekennzeichnet werden:

- Änderungen, die Sie seit dem Öffnen der Datei vorgenommen, jedoch nicht gespeichert haben, werden durch eine **gelbe** Leiste am linken Rand gekennzeichnet (auch als „Auswahlrand“ bezeichnet).

    ![Code-Editor-Bearbeitung mit gelber Leiste](media/code-editor-edit-yellow.png "Screenshot: Code-Editor, in dem eine Änderung mit einer gelben Leiste im Auswahlrand markiert ist")

- Nach dem Speichern der Änderungen (jedoch vor dem Schließen der Datei), wird die Statusleiste **grün**.

    ![Code-Editor-Bearbeitung mit grüner Leiste](media/code-editor-edit-green.png "Screenshot: Code-Editor, in dem eine Änderung mit einer grünen Leiste im Auswahlrand markiert ist")

Um diese Funktion zu aktivieren und zu deaktivieren, ändern Sie die Option **Änderungen nachverfolgen** in den **Text-Editor**-Einstellungen (**Tools** > **Optionen** > **Text-Editor**).

Weitere Informationen zur Änderungsnachverfolgung – mit Wellenlinien, die unter Zeichenfolgen im Code angezeigt werden – finden Sie im Abschnitt **[Editor-Funktionen](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** der Seite [Funktionen des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md).

#### <a name="right-click-context-menu"></a>Kontextmenü (Rechtsklick)

Beim Bearbeiten von Code im XAML-Code-Editor haben Sie per Rechtsklick Zugriff auf ein Kontextmenü mit verschiedenen Funktionen. Die meisten dieser Funktionen sind allgemein in der Visual Studio-IDE verfügbar. Einige werden jedoch nur in einem Code-Editor im Fenster „Entwurf“ angezeigt.

![Screenshot: Rechtsklick-Kontextmenü des XAML-Code-Editors in Visual Studio 2019](media/xaml-code-editor-right-click-menu.png)

Funktionsweise und Verwendung der einzelnen Funktionen:

- **Code anzeigen**: Mit dieser Funktion wird das Fenster für den Code in der Programmiersprache meist mit mehreren Registerkarte neben der Standardansicht angezeigt, die das Fenster „Entwurf“ und den XAML-Code-Editor enthält.
- **Designer anzeigen**: Mit dieser Funktion wird die Standardansicht angezeigt, die das Fenster „Entwurf“ und den XAML-Code-Editor enthält. (Wenn Sie sich bereits in der Standardansicht befinden, hat diese Funktion keine Auswirkungen.)
- **Schnellaktionen und Refactorings**: Mit dieser Funktion wird Code mit nur einer Aktion umgestaltet, generiert oder anderweitig geändert. Wenn Sie auf den Code zeigen und eine schnelle Aktion oder ein Refactoring vorhanden ist, wird ein Glühbirnensymbol angezeigt. <br>Siehe auch: [Schnelle Aktionen](../ide/quick-actions.md) und [Refactoring von Code](../ide/refactoring-in-visual-studio.md).
- **Umbenennen...** : Mit dieser Funktion werden nur Namespaces umbenannt. Wenn Sie keinen Namespace umbenennen, wird eine Fehlermeldung angezeigt, die besagt, dass nur Namespacepräfixe umbenannt werden können.
- **Namespaces entfernen und sortieren**: Mit dieser Funktion werden nicht verwendete Namespaces entfernt und die verbleibenden Namespaces sortiert.
- **Definition einsehen**: Mit dieser Funktion wird die Definition eines Typs angezeigt, ohne dass Sie Ihre Position im Editor verlassen müssen. <br>Siehe auch: [Definition einsehen](../ide/go-to-and-peek-definition.md#peek-definition) und [Anzeigen und Bearbeiten von Code mithilfe von „Definition einsehen“](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Gehe zu Definition**: Mit dieser Funktion können Sie zur Quelle eines Typs oder Members navigieren und die Ergebnisse in einer neuen Registerkarte öffnen. <br>Siehe auch: [Gehe zu Definition](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Umschließen mit...** : Damit werden „Umschließen mit“-Codeausschnitte verwendet, die um einen ausgewählten Codeblock eingefügt werden. <br>Siehe auch: [Erweiterungsausschnitte und umschließende Ausschnitte](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Codeausschnitt einfügen**: Mit dieser Funktion wird an der Cursorposition ein Codeausschnitt eingefügt.
- **Ausschneiden**: selbsterklärend
- **Kopieren**: selbsterklärend
- **Einfügen**: selbsterklärend
- **Gliedern**: Damit werden Codeabschnitte ein- und ausgeblendet. <br>Siehe auch: [Gliedern](../ide/outlining.md).
- **Quellcodeverwaltung**: Mit dieser Funktion wird der Verlauf von Codebeiträgen zu einem Open-Source-Repository angezeigt.

### <a name="middle-pane-scroll-bar"></a>Mittlerer Bereich, Scrollleiste

Mit der Scrollleiste können Sie nicht nur durch Ihren Code scrollen. Sie können damit auch einen weiteren Code-Editor-Bereich öffnen. Darüber hinaus können Sie mit der Scrollleiste Code effizienter schreiben, indem Sie Anmerkungen hinzufügen oder verschiedene Anzeigemodi verwenden.

#### <a name="split-the-code-window"></a>Teilen des Codefensters

Oben in der Scrollleiste des Code-Editors befindet sich die Schaltfläche **Teilen**. Wenn Sie diese Option auswählen, können Sie einen weiteren Code-Editor-Bereich anzeigen. Das ist nützlich, weil die Bereiche unabhängig voneinander verwendet werden können. Somit können Sie Code an verschiedenen Stellen bearbeiten.

![Screenshot: Mittlerer Bereich des XAML-Code-Editors in Visual Studio 2019 mit hervorgehobener Schaltfläche „Teilen“ oben rechts](media/code-editor-split-window-button.png)

Weitere Informationen zum Teilen eines Editorfensters finden Sie auf der Seite [Verwalten von Editorfenstern](../ide/how-to-manage-editor-windows.md).

#### <a name="use-annotations-or-map-mode"></a>Verwenden von Anmerkungen oder des Zuordnungsmodus

Sie können die Darstellung der Scrollleiste ändern und festlegen, welche Funktionen sie enthält. Viele Benutzer möchten beispielsweise *Anmerkungen* in der Scrollleiste verwenden. Diese zeigen visuelle Hinweise wie Codeänderungen, Haltepunkte, Textmarken, Fehler und Position der Einfügemarke an.

Andere verwenden gerne den *Zuordnungsmodus*. In diesem Modus werden Codezeilen als Miniaturansicht in der Scrollleiste angezeigt. Entwickler, die mit einer Datei mit viel Code arbeiten, werden möglicherweise feststellen, dass sie im Zuordnungsmodus Codezeilen effektiver nachverfolgen können als mit der Standardscrollleiste.

Weitere Informationen zum Ändern der Standardeinstellungen der Scrollleiste finden Sie auf der Seite [Anpassen der Scrollleiste](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="xaml-specific-features"></a>XAML-spezifische Funktionen

Die meisten der folgenden Funktionen sind in der Visual Studio-IDE allgemein verfügbar. Einige weisen jedoch zusätzliche Aspekte auf, die XAML-Entwicklern die Programmierung erleichtern.

### <a name="xaml-code-snippets"></a>XAML-Codeausschnitte

Codeausschnitte sind kleine Blöcke mit wiederverwendbarem Code, die Sie in einer Codedatei per Rechtsklick über den Befehl **Ausschnitt einfügen** im Kontextmenü oder eine Tastenkombination (**STRG**+**K**, **STRG**+**X**) einfügen können. Wir haben [IntelliSense](../ide/using-intellisense.md) erweitert, sodass nun die Anzeige von XAML-Ausschnitten unterstützt wird. Dies funktioniert sowohl für integrierte Ausschnitte als auch für alle benutzerdefinierten Ausschnitte, die Sie manuell hinzufügen. `#region`, `Column definition`, `Row definition`, `Setter` und `Tag` sind Beispiele für sofort verwendbare XAML-Codeausschnitte.

![Der XAML-Code-Editor mit Optionen für XAML-Codeausschnitte in IntelliSense](media/xaml-code-snippets.png "Screenshot: XAML-Code-Editor mit Optionen für XAML-Codeausschnitte in IntelliSense")

Weitere Informationen finden Sie auf den Seiten [Codeausschnitte](../ide/code-snippets.md) und [C#-Codeausschnitte](../ide/visual-csharp-code-snippets.md).

### <a name="xaml-region-support"></a>XAML-Unterstützung für #region

Ab Visual Studio 2015 haben wir die Unterstützung für #region-Anweisungen für XAML-Entwickler in WPF und UWP und seit Kurzem auch in [Xamarin.Forms](/xamarin/xamarin-forms/user-interface/text/editor/) verfügbar gemacht. In Visual Studio 2019 haben wir weitere Verbesserungen an der Unterstützung für #region-Anweisungen vorgenommen. So werden beispielsweise in [Version 16.4](/visualstudio/releases/2019/release-notes-v16.4/) und höher #region-Optionen angezeigt, wenn Sie mit der Eingabe von `<!` beginnen.

![Der XAML-Code-Editor mit #region-Optionen in IntelliSense](media/code-editor-xaml-region.png "Screenshot: XAML-Code-Editor mit Optionen für #region-Optionen in IntelliSense")

Mithilfe von Regionen können Sie Abschnitte im Code gruppieren, die ein- oder ausgeblendet werden sollen.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Weitere Informationen zu Regionen finden Sie auf der Seite [#region (C#-Referenz)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/). Informationen zum Ein- und Ausblenden von Codeabschnitten finden Sie auf der Seite [Gliedern](../ide/outlining.md).

### <a name="xaml-comments"></a>XAML-Kommentare

Entwickler dokumentieren ihren Code gerne mit Kommentaren. Dabei gibt es folgende Möglichkeiten, dem XAML-Code auf der Registerkarte **MainWindow.xaml** Kommentare hinzuzufügen:

- Geben Sie vor einem Kommentar `<!--` ein, und fügen Sie nach dem Kommentar `-->` hinzu.
- Geben Sie `<!` ein, und wählen Sie in der Liste mit Optionen `!--` aus.

  ![XAML-Code-Editor, Rechtsklick, Dialogfeld zum Hinzufügen von Kommentaren](media/xaml-code-editor-comments.png "Screenshot: Kontextmenü (Rechtsklick) zum Hinzufügen von Kommentaren im XAML-Code-Editor")

- Wählen Sie zunächst den Code aus, den Sie in einen Kommentar einschließen möchten, und klicken Sie anschließend in der Symbolleiste der IDE auf die Schaltfläche **Kommentar**. Wenn Sie die Aktion rückgängig machen möchten, klicken Sie auf die Schaltfläche **Auskommentierung aufheben**.

  ![Die Schaltflächen „Kommentar“ und „Auskommentierung aufheben“ in der IDE-Symbolleiste](media/comment-undo-comment-buttons.png "Screenshot: Schaltflächen „Kommentar“ und „Auskommentierung aufheben“ in der IDE-Symbolleiste")

- Wählen Sie zunächst den Code aus, den Sie in einen Kommentar einschließen möchten, und drücken Sie anschließend die Tasten **STRG**+**K**, **STRG**+**C**. Wenn Sie die Auskommentierung des ausgewählten Codes aufheben möchten, klicken Sie auf **STRG**+**K**, **STRG**+**U**.

Weitere Informationen zur Verwendung von Kommentaren im C#-Code auf der Registerkarte **MainWindow.xaml.cs** finden Sie auf der Seite [Dokumentationskommentare](/dotnet/csharp/language-reference/language-specification/documentation-comments/).

### <a name="xaml-lightbulbs"></a>XAML-Fehlerbehebungsmenüs

Glühbirnensymbole, die im XAML-Code angezeigt werden, sind Teil der [schnellen Aktionen](../ide/quick-actions.md), die Sie zum Umgestalten, Generieren oder anderweitigen Ändern von Code verwenden können.

Im Folgenden werden einige Beispiele beschrieben, wie Sie beim Schreiben von XAML-Code davon profitieren können:

- **Unnötige Namespaces entfernen**. Im XAML-Code-Editor werden unnötige Namespaces als abgeblendeter Text angezeigt. Wenn Sie mit dem Cursor auf eine nicht erforderliche using-Direktive zeigen, wird eine Glühbirne angezeigt. Wenn Sie in der Dropdownliste die Option **Unnötige Namespaces entfernen** auswählen, wird eine Vorschau der Namespaces angezeigt, die Sie entfernen können.

  ![Die Option „Unnötige Namespaces entfernen“ im XAML-Code-Editor über die Glühbirne für schnelle Aktionen](media/xaml-code-editor-dimmed-namespaces-preview.png "Screenshot: Option „Unnötige Namespaces entfernen“ im XAML-Code-Editor, die bei Verwendung der Glühbirne für schnelle Aktionen angezeigt wird")

- **Namespace umbenennen**. Diese Funktion ist per Rechtsklick im Kontextmenü verfügbar, nachdem Sie einen Namespace markiert haben. Damit können Sie mehrere Instanzen einer Einstellung gleichzeitig ändern. Diese Funktion ist auch in der Menüleiste über **Bearbeiten** > **Umgestalten** > **Umbenennen** oder über die Tastenkombination **STRG**+**R** und erneutes Drücken der Tastenkombination **STRG**+**R** verfügbar.

  ![Die Option „Namespace umbenennen“ per Rechtsklick über das Kontextmenü im XAML-Code-Editor](media/code-editor-rename-namespace.png "Screenshot: Option „Namespace umbenennen“ im XAML-Code-Editor, die bei Verwendung des Kontextmenüs (Rechtsklick) angezeigt wird")

  Weitere Informationen finden Sie auf der Seite [Refactoring des Umbenennens eines Codesymbols](../ide/reference/rename.md).

### <a name="conditional-xaml-for-uwp"></a>Bedingtes XAML für UWP

Bedingtes XAML bietet eine Möglichkeit, die Methode [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) in XAML-Markup zu verwenden. Sie sind damit in der Lage, im Markup nur dann Eigenschaften festzulegen und Objekte zu initialisieren, wenn die entsprechende API vorhanden ist, ohne CodeBehind zu verwenden.

Weitere Informationen finden Sie auf den Seiten [Bedingtes XAML](/windows/uwp/debug-test-perf/conditional-xaml/) und [Hosten von UWP XAML-Steuerelementen in Desktop-Apps (XAML Islands)](/windows/apps/desktop/modernize/xaml-islands/).

### <a name="xaml-structure-visualizer"></a>XAML-Strukturschnellansicht

Die Funktion „Strukturschnellansicht“ im Code-Editor zeigt Strukturführungslinien an. Hierbei handelt es sich um vertikal gestrichelte Linien, die im Code zusammengehörende öffnende und schließende Tagelemente kennzeichnen. Mithilfe dieser vertikalen Linien können Sie leichter erkennen, wo logische Blöcke anfangen und aufhören.

Weitere Informationen finden Sie auf der Seite [Navigieren durch den Code](../ide/navigating-code.md).

### <a name="intellicode-for-xaml"></a>IntelliCode für XAML

Beim Hinzufügen eines XAML-Tags zu Code beginnen Sie in der Regel mit einer linken spitzen Klammer `<`. Beim Eingeben dieser spitzen Klammer wird ein IntelliCode-Menü mit verschiedenen häufig verwendeten XAML-Tags angezeigt. Wählen Sie das gewünschte Tag aus, um es dem Code schnell hinzuzufügen.

Die IntelliCode-Optionen können Sie daran erkennen, dass sie in der Liste ganz oben mit einem Stern angezeigt werden.

![Die IntelliCode-Liste für den XAML-Text-Editor](media/xaml-intellicode-selection.png "Screenshot: IntelliCode-Liste für den XAML-Text-Editor")

Weitere Informationen finden Sie auf der Seite [Übersicht über IntelliCode](/visualstudio/intellicode/overview/).

### <a name="settings"></a>Einstellungen

Weitere Informationen zu *allen* Einstellungen in der Visual Studio-IDE finden Sie auf der Seite [Funktionen des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md).

## <a name="xaml-optional-settings"></a>Optionale XAML-Einstellungen

Mithilfe des Dialogfelds [Optionen](../ide/reference/options-dialog-box-visual-studio.md) können Sie die Standardeinstellungen für den XAML-Code-Editor ändern. Zeigen Sie die Einstellungen an, indem Sie auf **Extras** > **Optionen** > **Text-Editor** > **XAML** klicken.

![Die Liste „Optionen“ für den XAML-Text-Editor](media/xaml-tools-options.png "Screenshot: Liste „Optionen“ für den XAML-Text-Editor")

> [!NOTE]
> Sie können auch Tastenkombinationen verwenden, um das Dialogfeld „Optionen“ aufzurufen. Gehen Sie dabei folgendermaßen vor: Drücken Sie **STRG**+**Q**, um die IDE zu suchen. Geben Sie **Optionen** ein, und drücken Sie die **EINGABETASTE**. Drücken Sie als Nächstes **STRG**+**E**, um das Dialogfeld „Optionen“ zu suchen. Geben Sie **Text-Editor** ein, drücken Sie die **EINGABETASTE**, geben Sie **XAML** ein, und drücken Sie die **EINGABETASTE**.
>  
> Weitere Informationen zu Tastenkombinationen finden Sie auf der Seite [Tipps zu Tastenkombinationen in Visual Studio](../ide/productivity-shortcuts.md#code-editor).

### <a name="universal-text-editor-options"></a>Allgemeine Text-Editor-Optionen

Im Dialogfeld [Optionen](../ide/reference/options-text-editor-xaml-formatting.md) für XAML werden die folgenden drei Elemente in allen von der Visual Studio-IDE unterstützten Programmiersprachen gleich verwendet. Weitere Informationen zu diesen Optionen und ihrer Verwendung finden Sie in den verknüpften Informationen in der folgenden Tabelle.

|Name  |Weitere Informationen  |
|---------|---------|
|Allgemein  | [Dialogfeld „Optionen“: Text-Editor > Alle Sprachen](../ide/reference/options-text-editor-all-languages.md) |
|Bildlaufleisten | [Optionen, Text-Editor, Alle Sprachen, Scrollleisten](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Registerkarten  |  [Optionen, Text-Editor, Alle Sprachen, Registerkarten](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>XAML-spezifische Text-Editor-Optionen

In der folgenden Tabelle sind die Einstellungen im Dialogfeld [Optionen](../ide/reference/options-text-editor-xaml-formatting.md) aufgeführt, mit denen Sie Code bei der Entwicklung von XAML-basierten Apps besser bearbeiten können. Weitere Informationen zu diesen Optionen und ihrer Verwendung finden Sie in den verknüpften Informationen.

|Name  |Weitere Informationen  |
|---------|---------|
|Formatierung | [Optionen, Text-Editor, XAML, Formatierung](../ide/reference/options-text-editor-xaml-formatting.md) |
|Verschiedenes |  [Optionen, Text-Editor, XAML, Sonstiges](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> Die Einstellung **Große Anfangsbuchstaben für Ereignishandler-Methodennamen** im Abschnitt **Sonstiges** ist für XAML-Entwickler besonders nützlich. Diese Einstellung ist standardmäßig *deaktiviert*, da es eine neue Einstellung ist. Es wird jedoch empfohlen, diese Einstellung zu *aktivieren*, um die ordnungsgemäße Groß-/Kleinschreibung im Code zu unterstützen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Bearbeiten von Code in Echtzeit beim Ausführen der App im Debugmodus finden Sie auf der Seite [XAML Hot Reload](xaml-hot-reload.md).

## <a name="see-also"></a>Siehe auch

- [Funktionen des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
- [XAML in UWP-Apps](/windows/uwp/xaml-platform/xaml-overview/)
- [XAML in Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)
- [Entwicklung mobiler Apps mit Xamarin (Mac)](/visualstudio/mac/xamarin/)
- [Visual Studio 2019 für Mac: Überblick](/visualstudio/mac/ide-tour/)
