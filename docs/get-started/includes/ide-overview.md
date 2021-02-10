---
ms.date: 09/22/2020
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: afc0466e93b8bf2a71db42c08cd2e043107e3bc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924997"
---
Die *integrierte Entwicklungsumgebung* für Visual Studio ist eine kreative Startplattform, die Sie verwenden können, um Code erst zu bearbeiten, zu debuggen und zu kompilieren und anschließend eine App zu veröffentlichen. Bei einer integrierten Entwicklungsumgebung (IDE) handelt es sich um ein funktionsreiches Programm, das für viele Aspekte der Softwareentwicklung verwendet werden kann. Neben dem üblichen Editor und Debugger, den die meisten IDEs bereitstellen, enthält Visual Studio Compiler, Codevervollständigungstools, grafische Designer und viele andere Features zur Erleichterung der Softwareentwicklung.

::: moniker range="vs-2017"

![Die Visual Studio 2017-IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![Die Visual Studio 2019-IDE](../media/vs-2019/ide-overview.png)](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Auf diesem Bild sehen Sie Visual Studio mit einem geöffneten Projekt und einigen wichtigen Toolfenstern, die Sie wahrscheinlich verwenden:

- Im[Projektmappen-Explorer](../../ide/solutions-and-projects-in-visual-studio.md) (rechts oben) können Sie Ihre Codedateien anzeigen, durch die Dateien navigieren und sie verwalten. Der **Projektmappen-Explorer** kann Sie beim Ordnen Ihres Codes unterstützen, indem er die Dateien in [Projektmappen und Projekte](../tutorial-projects-solutions.md) gruppiert.

- Im [Editorfenster](../../ide/writing-code-in-the-code-and-text-editor.md) (Mitte), in dem Sie die meiste Zeit verbringen werden, werden Dateiinhalte angezeigt. Hier können Sie Code bearbeiten oder eine Benutzeroberfläche wie etwa ein Fenster mit Schaltflächen und Textfeldern entwerfen.

::: moniker range="vs-2017"

- Das Fenster [Ausgabe](../../ide/reference/output-window.md) (Mitte unten) ist der Ort, an den Visual Studio Benachrichtigungen sendet, z.B. Debug- und Fehlermeldungen, Compilerwarnungen, Nachrichten zum Veröffentlichungsstatus und mehr. Jede Nachrichtenquelle verfügt über eine eigene Registerkarte.

::: moniker-end

- Im [Team Explorer](/azure/devops/user-guide/work-team-explorer) (unten rechts) können Sie Arbeitselemente nachverfolgen und Code mithilfe von Techniken zur Versionskontrolle, wie etwa [Git](https://git-scm.com/) und [Team Foundation-Versionskontrolle (Team Foundation Version Control, TFVC)](/azure/devops/repos/tfvc/overview), mit anderen teilen.

## <a name="editions"></a>Editionen

::: moniker range="vs-2017"

Visual Studio ist für Windows und Mac verfügbar. [Visual Studio für Mac](/visualstudio/mac/) enthält viele der Features von Visual Studio 2017 und wurde für die Entwicklung plattformübergeifender und mobiler Apps optimiert. Dieser Artikel konzentriert sich auf die Windows-Version von Visual Studio 2017.

Es gibt drei Editionen von Visual Studio: Community, Professional und Enterprise. Unter [Visual Studio-Editionen im Vergleich](https://visualstudio.microsoft.com/vs/compare/) erfahren Sie, welche Features in der jeweiligen Edition unterstützt werden.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio ist für Windows und Mac verfügbar. [Visual Studio für Mac](/visualstudio/mac/) enthält viele der Features von Visual Studio 2019 und wurde für die Entwicklung plattformübergreifender und mobiler Apps optimiert. Dieser Artikel konzentriert sich auf die Windows-Version von Visual Studio 2019.

Es gibt drei Editionen von Visual Studio 2019: Community, Professional und Enterprise. Unter [Visual Studio-Editionen im Vergleich](https://visualstudio.microsoft.com/vs/compare/) erfahren Sie, welche Features in der jeweiligen Edition unterstützt werden.

::: moniker-end

## <a name="popular-productivity-features"></a>Gängige Features zur Steigerung der Produktivität

Einige gängige Features in Visual Studio, mit denen Sie bei der Entwicklung von Software noch produktiver sind:

- Wellenlinien und [schnelle Aktionen](../../ide/quick-actions.md)

   Wellenlinien sind wellenförmige Unterstreichungen, die Sie auf Fehler oder mögliche Probleme in Ihrem Code hinweisen. Dank dieser visuellen Hinweisen können Sie Probleme sofort beheben, ohne zu warten, bis der Fehler beim Kompilieren oder beim Ausführen des Programms entdeckt wird. Wenn Sie auf eine Wellenlinie zeigen, werden zusätzliche Informationen zum Fehler angezeigt. Am linken Rand wird ggf. auch eine Glühbirne mit Aktionen, schnelle Aktionen genannt, zum Beheben des Fehlers angezeigt.

   ![Wellenlinien in Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Codebereinigung

   Formatieren Sie Ihren Code mit nur einem Klick, und wenden Sie Codekorrekturen an, die Ihnen auf der Grundlage von [Einstellungen für das Codeformat](../../ide/reference/options-text-editor-csharp-formatting.md), [EditorConfig-Konventionen](../../ide/create-portable-custom-editor-options.md) und [Roslyn-Analysetools](../../code-quality/roslyn-analyzers-overview.md) vorgeschlagen werden. Mit der **Codebereinigung** können Sie Probleme in Ihrem Code vor der Code Review beheben. (Derzeit nur für C#-Code verfügbar.)

   ![Schaltfläche „Codebereinigung“ in Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Refactoring umfasst Vorgänge wie das intelligente Umbenennen von Variablen, das Extrahieren von Codezeilen in eine neue Methode, das Ändern der Reihenfolge von Methodenparametern und vieles mehr.

   ![Refactoring in Visual Studio](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense steht für eine Gruppe von Features, mit denen Informationen zum Code direkt im Editor angezeigt und in einigen Fällen kleine Codeabschnitte für Sie geschrieben werden. Damit verfügen Sie über eine grundlegende Dokumentation, die in den Editor integriert ist, sodass Sie die Typinformationen nicht mehr an anderer Stelle nachsehen müssen. Die Features von IntelliSense variieren je nach Sprache. Weitere Informationen finden Sie unter [C#-IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md) und [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). In der folgenden Abbildung ist dargestellt, wie mit IntelliSense eine Memberliste für einen Typ angezeigt wird:

   ![Visual Studio, Member-Liste](../media/intellisense-list-members.png)

- [Visual Studio-Suche](../../ide/visual-studio-search.md)

   Visual Studio kann angesichts der zahlreichen Menüs, Optionen und Eigenschaften zuweilen übermächtig wirken. Die Visual Studio-Suche (**STRG**+**Q**) ist eine gute Möglichkeit, IDE-Features und Code schnell zu finden.

   ::: moniker range="vs-2017"

   ![Suchfeld „Schnellstart“ in Visual Studio 2017](../media/quick-launch-nuget.png)

   Weitere Informationen finden Sie unter [Schnellstart](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Screenshot: Suchfeld in Visual Studio 2019](../media/vs-2019/quick-launch-nuget.png)

    Weitere Informationen und Produktivitätstipps finden Sie unter [Verwenden der Visual Studio-Suche](../../ide/visual-studio-search.md).

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Führen Sie unabhängig von App-Typ oder Programmiersprache gemeinsam und in Echtzeit Bearbeitungs- und Debugvorgänge aus. Sie können Ihr aktuelles Projekt sowie Debugsitzungen, Terminalinstanzen, Localhost-Web-Apps, Sprachanrufe und vieles mehr sofort und sicher freigeben.

- [Aufrufhierarchie](../../ide/reference/call-hierarchy.md)

   Im Fenster **Aufrufhierarchie** werden die Methoden angezeigt, mit denen eine ausgewählte Methode aufgerufen wird. Diese Informationen können nützlich sein, wenn Sie die Methode ändern oder entfernen oder einen Fehler aufspüren möchten.

   ![Fenster „Aufrufhierarchie“](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   Mit CodeLens können Sie nach Verweisen auf Ihren Code, Änderungen an Ihrem Code, verknüpften Fehlern, Arbeitselementen, Codeüberprüfungen und Komponententests suchen, ohne den Editor verlassen zu müssen.

   ![CodeLens](../media/codelens-overview.png)

- [Gehe zu Definition](../../ide/go-to-and-peek-definition.md)

   Mit der Funktion „Gehe zu Definition“ gelangen Sie direkt zu der Stelle, an der eine Funktion oder ein Typ definiert ist.

   ![Zur Definition wechseln](../media/go-to-definition-menu.png)

- [Definition einsehen](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Im Fenster **Definitionsvorschau** wird die Definition einer Methode oder eines Typs angezeigt, ohne eine separate Datei zu öffnen.

   ![Peek in Definition](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Installieren von Visual Studio-IDE

In diesem Abschnitt erstellen Sie ein einfaches Projekt, um einige Dinge auszuprobieren, die mit Visual Studio möglich sind. Sie verwenden [IntelliSense](../../ide/using-intellisense.md) als Programmierhilfe, debuggen eine App, um den Wert einer Variablen während der Ausführung des Programms anzuzeigen, und ändern das Farbschema.

::: moniker range="vs-2017"

[Laden Sie zunächst Visual Studio herunter](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), und installieren Sie es auf Ihrem System. Mit dem modularen Installationsprogramm können Sie *Workloads* auswählen und installieren, die Gruppen von Funktionen sind, die für die bevorzugte Programmiersprache oder Plattform erforderlich sind. Damit Sie die Schritte zum [Erstellen eines Programms](#create-a-program) ausführen können, müssen Sie während der Installation die Workload **Plattformübergreifende .NET Core-Entwicklung** auswählen.

::: moniker-end

::: moniker range=">=vs-2019"

[Laden Sie zunächst Visual Studio herunter](https://visualstudio.microsoft.com/downloads), und installieren Sie es auf Ihrem System. Mit dem modularen Installationsprogramm können Sie *Workloads* auswählen und installieren, die Gruppen von Funktionen sind, die für die bevorzugte Programmiersprache oder Plattform erforderlich sind. Damit Sie die Schritte zum [Erstellen eines Programms](#create-a-program) ausführen können, müssen Sie während der Installation die Workload **Plattformübergreifende .NET Core-Entwicklung** auswählen.

::: moniker-end

![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../media/dotnet-core-cross-platform-workload.png)

Wenn Sie Visual Studio zum ersten Mal öffnen, können Sie sich optional mit Ihrem Microsoft-Konto oder Ihrem Geschäfts-, Schul- oder Unikonto [anmelden](../../ide/signing-in-to-visual-studio.md).

## <a name="create-a-program"></a>Erstellen eines Programms

Darum werden wir mit Ihnen jetzt ein einfaches Programm erstellen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio.

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

   ![„Datei“ > „Neu“ > „Projekt“ in der Menüleiste](../media/file-new-project-menu.png)

   Im Dialogfeld **Neues Projekt** werden mehrere *Projektvorlagen* angezeigt. Eine Vorlage enthält die grundlegenden Dateien und Einstellungen, die für einen bestimmten Projekttyp erforderlich sind.

1. Wählen Sie unter **Visual C#** die Vorlagenkategorie **.NET Core** und anschließend die Vorlage **Konsolen-App (.NET Core)** aus. Geben Sie **HelloWorld** im Textfeld **Name** ein, und klicken Sie auf **OK**.

   ![.NET Core-App-Vorlage](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Wenn die Kategorie **.NET Core** nicht angezeigt wird, müssen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** installieren. Klicken Sie hierfür im Dialogfeld **Neues Projekt** unten links auf den Link **Visual Studio-Installer öffnen**. Nachdem der Visual Studio-Installer geöffnet wurde, wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Ändern**.

   Visual Studio erstellt daraufhin das Projekt. Die Vorlage erstellt eine einfache „Hello World“-Anwendung, mit der die <xref:System.Console.WriteLine?displayProperty=nameWithType>-Methode aufgerufen wird, um die Literalzeichenfolge „Hello World!“ im Konsolenfenster (Programmausgabe).

   Kurz darauf sollte nun etwa Folgendes angezeigt werden:

   ![Visual Studio-IDE](../media/overview-ide-console-app.png)

   Der C#-Code für Ihre Anwendung wird im Editor-Fenster angezeigt, der den meisten Raum einnimmt. Beachten Sie, dass der Text automatisch farbig hervorgehoben wird, um verschiedene Bestandteile des Codes anzuzeigen, z.B. Schlüsselwörter und Typen. Darüber hinaus zeigen kleine, vertikale gestrichelte Linien im Code an, welche geschweiften Klammern zusammengehören, und anhand der Zeilennummern können Sie sich später im Code orientieren. Sie können die kleinen Minuszeichen in Kästchen auswählen, um Codeblöcke ein- oder auszublenden. Mit dieser Codegliederungsfunktion können Sie Code ausblenden, den Sie nicht benötigen, um die Übersichtlichkeit des Bildschirms zu optimieren. Auf der rechten Seite werden im Fenster **Projektmappen-Explorer** die Projektdateien aufgelistet.

   ![Visual Studio-IDE mit roten Markierungen](../media/overview-ide-console-app-red-boxes.png)

   Es sind noch mehr Menüs und Toolfenster verfügbar, aber für den Moment wenden wir uns Anderem zu.

1. Starten Sie nun die App. Wählen Sie hierzu auf der Menüleiste im Menü **Debuggen** die Option **Ohne Debuggen starten** aus. Alternativ können Sie auch die Tastenkombination **STRG**+**F5** drücken.

   ![Menü „Debuggen“ > „Ohne Debuggen starten“](../media/overview-start-without-debugging.png)

   Visual Studio erstellt die App, und es wird ein Konsolenfenster mit der Meldung **Hello World!** geöffnet. Sie haben nun eine funktionierende App!

   ![Screenshot des „cmd.exe“-Konsolenfensters, in dem die Ausgabe „Hallo Welt!“ und „Drücken Sie eine beliebige Taste, um den Vorgang fortzusetzen“ angezeigt wird.](../media/overview-console-window.png)

1. Drücken Sie eine beliebige Taste auf der Tastatur, um das Konsolenfenster zu schließen.

1. Fügen wir der App weiteren Code hinzu. Fügen Sie vor der Zeile `Console.WriteLine("Hello World!");` den folgenden Code ein:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Der Code zeigt **What is your name?** (Wie heißen Sie?) im Konsolenfenster an und wartet, bis der Benutzer Text eingegeben und die **EINGABETASTE** gedrückt hat.

1. Ändern Sie die Zeile `Console.WriteLine("Hello World!");` in den folgenden Code:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Führen Sie die App erneut aus, indem Sie **Debuggen** > **Ohne Debuggen starten** auswählen oder **STRG**+**F5** drücken.

   Visual Studio erstellt die App neu, und Sie werden im nun geöffneten Konsolenfenster zur Eingabe Ihres Namens aufgefordert.

1. Geben Sie Ihren Namen im Konsolenfenster ein, und drücken Sie die **EINGABETASTE**.

   ![Konsolenfenstereingabe](../media/overview-console-input.png)

1. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen und das ausgeführte Programm zu beenden.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio.

   Daraufhin wird das Startfenster angezeigt. Dort können Sie unter anderem ein Repository klonen, ein kürzlich verwendetes Projekt öffnen oder ein neues Projekt erstellen.

1. Wählen Sie **Neues Projekt erstellen** aus.

   ![„Neues Projekt erstellen“ im Startfenster von Visual Studio](../media/vs-2019/start-window-create-new-project.png)

   Das Fenster **Neues Projekt erstellen** wird geöffnet und zeigt verschiedene *Vorlagen* für Projekte an. Eine Vorlage enthält die grundlegenden Dateien und Einstellungen, die für einen bestimmten Projekttyp erforderlich sind.

1. Geben Sie **.NET Core Konsole** in das Suchfeld ein, um die gewünschte Vorlage zu finden. Die Liste mit den verfügbaren Vorlagen wird automatisch nach den eingegebenen Schlüsselwörtern gefiltert. Sie können die Vorlagenergebnisse noch weiter filtern, indem Sie in der Dropdownliste **Sprache** die Option **C#** auswählen. Wählen Sie die Vorlage **Konsolen-App (.NET Core)** und anschließend **Weiter** aus.

    ![Erstellen eines neuen Projekts in Visual Studio](../media/vs-2019/create-new-project.png)

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname** die Zeichenfolge **HelloWorld** ein, ändern Sie optional das Verzeichnis für Ihre Projektdateien, und wählen Sie anschließend **Erstellen** aus.

   ![Konfigurieren eines neuen Projekts in Visual Studio](../media/vs-2019/configure-new-project.png)

   Visual Studio erstellt daraufhin das Projekt. Die Vorlage erstellt eine einfache „Hello World“-Anwendung, mit der die <xref:System.Console.WriteLine?displayProperty=nameWithType>-Methode aufgerufen wird, um die Literalzeichenfolge „Hello World!“ im Konsolenfenster (Programmausgabe).

   Kurz darauf sollte nun etwa Folgendes angezeigt werden:

   ![Visual Studio-IDE](../media/vs-2019/overview-ide-console-app.png)

   Der C#-Code für Ihre Anwendung wird im Editor-Fenster angezeigt, der den meisten Raum einnimmt. Beachten Sie, dass der Text automatisch farbig hervorgehoben wird, um verschiedene Bestandteile des Codes anzuzeigen, z.B. Schlüsselwörter und Typen. Darüber hinaus zeigen kleine, vertikale gestrichelte Linien im Code an, welche geschweiften Klammern zusammengehören, und anhand der Zeilennummern können Sie sich später im Code orientieren. Sie können die kleinen Minuszeichen in Kästchen auswählen, um Codeblöcke ein- oder auszublenden. Mit dieser Codegliederungsfunktion können Sie Code ausblenden, den Sie nicht benötigen, um die Übersichtlichkeit des Bildschirms zu optimieren. Auf der rechten Seite werden im Fenster **Projektmappen-Explorer** die Projektdateien aufgelistet.

   ![Visual Studio-IDE mit roten Markierungen](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Es sind noch mehr Menüs und Toolfenster verfügbar, aber für den Moment wenden wir uns Anderem zu.

1. Starten Sie nun die App. Wählen Sie hierzu auf der Menüleiste im Menü **Debuggen** die Option **Ohne Debuggen starten** aus. Alternativ können Sie auch die Tastenkombination **STRG**+**F5** drücken.

   ![Menü „Debuggen“ > „Ohne Debuggen starten“](../media/overview-start-without-debugging.png)

   Visual Studio erstellt die App, und es wird ein Konsolenfenster mit der Meldung **Hello World!** geöffnet. Sie haben nun eine funktionierende App!

   ![Screenshot der Microsoft Visual Studio-Debugging-Konsole, in der die Ausgabe „Hallo Welt“ und „Drücken Sie eine beliebige Taste, um das Fenster zu schließen“ angezeigt wird.](../media/vs-2019/overview-console-window.png)

1. Drücken Sie eine beliebige Taste auf der Tastatur, um das Konsolenfenster zu schließen.

1. Fügen wir der App weiteren Code hinzu. Fügen Sie vor der Zeile `Console.WriteLine("Hello World!");` den folgenden Code ein:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Der Code zeigt **What is your name?** (Wie heißen Sie?) im Konsolenfenster an und wartet, bis der Benutzer Text eingegeben und die **EINGABETASTE** gedrückt hat.

1. Ändern Sie die Zeile `Console.WriteLine("Hello World!");` in den folgenden Code:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Führen Sie die App noch mal aus, indem Sie auf **Debuggen** > **Ohne Debuggen starten** klicken oder **STRG**+**F5** drücken.

   Visual Studio erstellt die App neu, und Sie werden im nun geöffneten Konsolenfenster zur Eingabe Ihres Namens aufgefordert.

1. Geben Sie Ihren Namen im Konsolenfenster ein, und drücken Sie die **EINGABETASTE**.

   ![Screenshot der Microsoft Visual Studio-Debugging-Konsole, in der die Aufforderung zur Eingabe eines Namens, die Eingabe und die Ausgabe „Hallo Georgette!“ angezeigt wird.](../media/vs-2019/overview-console-input.png)

1. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen und das ausgeführte Programm zu beenden.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Verwenden von Refactoring und IntelliSense

Im Folgenden werden einige Methoden erläutert, wie Sie mit [Refactoring](../../ide/refactoring-in-visual-studio.md) und [IntelliSense](../../ide/using-intellisense.md) effizienter programmieren können.

Benennen Sie zunächst die Variable `name` um:

1. Doppelklicken Sie auf die Variable `name`, um sie auszuwählen.

2. Geben Sie den neuen Namen (**username**) der Variable ein.

   Achten Sie auf das graue Feld, das die Variable umgibt und auf die Glühbirne, die am Rand angezeigt wird.

::: moniker range="vs-2017"

3. Klicken Sie auf das Glühbirnensymbol, um die verfügbaren [Schnellaktionen](../../ide/quick-actions.md) anzuzeigen. Klicken Sie auf **'name' in 'username' umbenennen**.

   ![Umbenennen einer Aktion in Visual Studio](../media/rename-quick-action.png)

   Die Variable wird für im gesamten Projekt umbenannt, in diesem Fall betrifft dies nur zwei Stellen.

   ![Animiertes GIF, das das Refactoring „Umbenennen“ in Visual Studio anzeigt](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Klicken Sie auf das Glühbirnensymbol, um die verfügbaren [Schnellaktionen](../../ide/quick-actions.md) anzuzeigen. Klicken Sie auf **'name' in 'username' umbenennen**.

   ![Umbenennen einer Aktion in Visual Studio](../media/vs-2019/rename-quick-action.png)

   Die Variable wird für im gesamten Projekt umbenannt, in diesem Fall betrifft dies nur zwei Stellen.

::: moniker-end

4. Im Folgenden wird IntelliSense näher erläutert. Geben Sie unterhalb der Zeile `Console.WriteLine($"\nHello {username}!");``DateTime now = DateTime.` ein.

   Ein Feld zeigt die Members der Klasse <xref:System.DateTime> an. Darüber hinaus wird die Beschreibung des aktuell ausgewählten Members in einem separaten Feld angezeigt.

   ![Auflistung von Members durch IntelliSense in Visual Studio](../media/intellisense-list-members.png)

5. Wählen Sie den Member **Now** aus, bei dem es sich um eine Eigenschaft der Klasse handelt, indem Sie auf diesen doppelklicken oder die **TAB-Taste** drücken. Vervollständigen Sie die Codezeile, indem Sie ein Semikolon am Ende hinzufügen.

6. Geben Sie darunter folgende Codezeilen ein, oder kopieren Sie diese:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> ist ein wenig anders als <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, denn es fügt nach dem Einfügen kein Zeilenabschlusszeichen hinzu. Das bedeutet, dass der nächste Textabschnitt, der an die Ausgabe gesendet wird, in der gleichen Zeile ausgegeben wird. Sie können auf jede dieser Methoden in Ihrem Code zeigen, um deren Beschreibung anzuzeigen.

7. Anschließend wird erneut ein Refactoring durchgeführt, um den Code etwas präziser zu gestalten. Klicken Sie in der Zeile `DateTime now = DateTime.Now;` auf die Variable `now`.

   Beachten Sie, dass ein kleines Schraubendrehersymbol am Rand dieser Zeile angezeigt wird.

8. Klicken Sie auf das Schraubendrehersymbol, um zu sehen, welche Vorschläge Visual Studio macht. In diesem Fall zeigt es das Refactoring [Inline temporär variabel](../../ide/reference/inline-temporary-variable.md) an, um eine Codezeile zu entfernen, ohne das gesamte Verhalten des Codes zu ändern:

   ![Refactoring „Inline temporär variabel“ in Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Klicken Sie auf **Inline temporär variabel**, um den Code umzugestalten.

::: moniker range="vs-2017"

10. Führen Sie das Programm erneut aus, indem Sie **STRG**+**F5** drücken. Die Ausgabe sieht in etwa folgendermaßen aus:

    Screenshot der „cmd.exe“-Konsole, in der die Aufforderung zur Eingabe eines Namens, die Eingabe und die Ausgabe „Hallo Georgette! Tag des Jahres: 151“ angezeigt wird.](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Führen Sie das Programm erneut aus, indem Sie **STRG**+**F5** drücken. Die Ausgabe sieht in etwa folgendermaßen aus:

    ![Screenshot der Microsoft Visual Studio-Debugging-Konsole, in der die Aufforderung zur Eingabe eines Namens, die Eingabe und die Ausgabe „Hallo Georgette! Tag des Jahres: 43“ angezeigt wird.](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Debuggen von Code

Wenn Sie Code schreiben, müssen Sie ihn auszuführen und auf Fehler prüfen. Mit dem Debugsystem von Visual Studio können Sie Ihren Code Anweisung für Anweisung durchlaufen und dabei die Variablen untersuchen. Sie können *Breakpoints* festlegen, mit denen die Codeausführung an einer bestimmten Zeile beendet wird. Sie können sehen, wie sich der Wert einer Variablen bei der Codeausführung ändert, und vieles mehr.

Legen Sie einen Breakpoint fest, um den Wert der Variable `username` zu sehen, während das Programm ausgeführt wird.

1. Suchen Sie die Codezeile `Console.WriteLine($"\nHello {username}!");`. Wenn Sie einen Breakpoint für diese Codezeile festlegen, damit die Ausführung des Programms an dieser Zeile angehalten wird, klicken Sie auf den äußeren linken Rand des Editors. Sie können auch an einer anderen Stelle der Codezeile klicken und dann **F9** drücken.

   Ein roter Kreis wird am äußeren linken Rand angezeigt, und der Code wird rot hervorgehoben.

   ![Breakpoint an einer Codezeile in Visual Studio](../media/breakpoint.png)

1. Starten Sie das Debuggen, indem Sie auf **Debuggen** > **Debuggen starten** klicken oder **F5** drücken.

1. Wenn das Konsolenfenster angezeigt wird und Sie nach Ihrem Namen fragt, geben Sie diesen ein, und drücken Sie die **EINGABETASTE**.

   Der Fokus kehrt zum Code-Editor von Visual Studio zurück und die Codezeile mit dem Breakpoint wird gelb hervorgehoben. Das bedeutet, dass dies die nächste Codezeile ist, die vom Programm ausgeführt wird.

1. Zeigen Sie mit der Maus auf die Variable `username`, um deren Wert anzuzeigen. Alternativ können Sie mit der rechten Maustaste auf `username` klicken und **Überwachung hinzufügen** auswählen, um die Variable zum **Überwachungsfenster** hinzuzufügen. Dort wird deren Wert ebenfalls angezeigt.

   ![Variablenwert während des Debuggens in Visual Studio](../media/debugging-variable-value.png)

1. Drücken Sie erneut **F5**, damit das Programm bis zum Abschluss ausgeführt wird.

Weitere Informationen über den Debugprozess in Visual Studio finden Sie unter [Tour zu den Debuggerfeatures](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Anpassen von Visual Studio

Sie können die Benutzeroberfläche von Visual Studio personalisieren und beispielsweise das Standardfarbdesign ändern. So ändern Sie das Design in **Dunkel**:

1. Klicken Sie auf der Menüleiste auf **Extras** > **Optionen**, um das Dialogfeld **Optionen** zu öffnen.

::: moniker range="vs-2017"

2. Ändern Sie auf der Optionenseite **Umgebung** > **Allgemein** die Auswahl für **Farbdesign** in **Dunkel**, und klicken Sie dann auf **OK**.

   Das Farbdesign wird für die gesamte IDE in **Dunkel** geändert.

   ![Visual Studio im Design „Dunkel“](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Ändern Sie auf der Optionenseite **Umgebung** > **Allgemein** die Auswahl für **Farbdesign** in **Dunkel**, und klicken Sie dann auf **OK**.

   Das Farbdesign wird für die gesamte IDE in **Dunkel** geändert.

   ![Visual Studio im Design „Dunkel“](../media/vs-2019/dark-theme.png)

::: moniker-end

Weitere Informationen dazu, wie Sie die IDE personalisieren können, finden Sie unter [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).