---
title: Übersicht für Visual Basic-Entwickler
ms.date: 11/15/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9938d017d683fd27a3f303824f9568a3876c2c4d
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928042"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Willkommen in der Visual Studio-IDE | Visual Basic

Die *integrierte Entwicklungsumgebung* für Visual Studio ist eine kreative Startplattform, die Sie verwenden können, um Code erst zu bearbeiten, zu debuggen und zu kompilieren und anschließend eine App zu veröffentlichen. Bei einer integrierten Entwicklungsumgebung (IDE) handelt es sich um ein funktionsreiches Programm, das für viele Aspekte der Softwareentwicklung verwendet werden kann. Neben dem üblichen Editor und Debugger, den die meisten IDEs bereitstellen, enthält Visual Studio Compiler, Codevervollständigungstools, grafische Designer und viele andere Features zur Erleichterung der Softwareentwicklung.

::: moniker range="vs-2017"

![Die Visual Studio-IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![Die Visual Studio 2019-IDE](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Auf diesem Bild sehen Sie Visual Studio mit einem geöffneten Projekt und einigen wichtigen Toolfenstern, die Sie wahrscheinlich verwenden:

- Im [Projektmappen-Explorer](../../ide/solutions-and-projects-in-visual-studio.md) (oben rechts) können Sie Ihre Codedateien anzeigen, darin navigieren und sie verwalten. Der **Projektmappen-Explorer** kann Sie beim Ordnen Ihres Codes unterstützen, indem er die Dateien in [Projektmappen und Projekte](tutorial-projects-solutions.md) gruppiert.

- Im [Editor-Fenster](../../ide/writing-code-in-the-code-and-text-editor.md) (Mitte), in dem Sie die meiste Zeit verbringen werden, werden Dateiinhalte angezeigt. Hier können Sie Code bearbeiten oder eine Benutzeroberfläche wie etwa ein Fenster mit Schaltflächen und Textfeldern entwerfen.

- Das Fenster [Ausgabe](../../ide/reference/output-window.md) (Mitte unten) ist der Ort, an den Visual Studio Benachrichtigungen sendet, z.B. Debug- und Fehlermeldungen, Compilerwarnungen, Nachrichten zum Veröffentlichungsstatus und mehr. Jede Nachrichtenquelle verfügt über eine eigene Registerkarte.

- Im [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (unten rechts) können Sie Arbeitselemente nachverfolgen und Code mithilfe von Techniken zur Versionskontrolle, wie etwa [Git](https://git-scm.com/) und [Team Foundation-Versionskontrolle (Team Foundation Version Control, TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true), mit anderen teilen.

## <a name="editions"></a>Editionen

Visual Studio ist für Windows und Mac verfügbar. [Visual Studio für Mac](/visualstudio/mac/) enthält viele der Features von Visual Studio 2017 und wurde für die Entwicklung plattformübergeifender und mobiler Apps optimiert. Dieser Artikel konzentriert sich auf die Windows-Version von Visual Studio 2017.

Es gibt drei Editionen von Visual Studio 2017: Community, Professional und Enterprise. Unter [Visual Studio 2017-IDEs im Vergleich](https://visualstudio.microsoft.com/vs/compare/) wird erläutert, welche Features in jeder Edition unterstützt werden.

## <a name="popular-productivity-features"></a>Gängige Features zur Steigerung der Produktivität

Einige gängige Features in Visual Studio, mit denen Sie bei der Entwicklung von Software noch produktiver sind:

- Wellenlinien und [schnelle Aktionen](../../ide/quick-actions.md)

   Wellenlinien sind wellenförmige Unterstreichungen, die Sie auf Fehler oder mögliche Probleme in Ihrem Code hinweisen. Dank dieser visuellen Hinweisen können Sie Probleme sofort beheben, ohne zu warten, bis der Fehler beim Kompilieren oder beim Ausführen des Programms entdeckt wird. Wenn Sie auf eine Wellenlinie zeigen, werden zusätzliche Informationen zum Fehler angezeigt. Am linken Rand wird ggf. auch eine Glühbirne mit Aktionen, schnelle Aktionen genannt, zum Beheben des Fehlers angezeigt.

   ::: moniker range="vs-2017"

   ![Wellenlinien in Visual Studio](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Wellenlinien in Visual Studio](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Refactoring umfasst Vorgänge wie das intelligente Umbenennen von Variablen, das Extrahieren von Codezeilen in eine neue Methode, das Ändern der Reihenfolge von Methodenparametern und vieles mehr.

   ::: moniker range="vs-2017"

   ![Menü „Refactoring“ in Visual Studio](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Menü „Refactoring“ in Visual Studio](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense steht für eine Gruppe von Features, mit denen Informationen zum Code direkt im Editor angezeigt und in einigen Fällen kleine Codeabschnitte für Sie geschrieben werden. Damit verfügen Sie über eine grundlegende Dokumentation, die in den Editor integriert ist, sodass Sie die Typinformationen nicht mehr an anderer Stelle nachsehen müssen. Die Features von IntelliSense variieren je nach Sprache. Weitere Informationen finden Sie unter [C#-IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md) und [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). In der folgenden Abbildung ist dargestellt, wie mit IntelliSense eine Memberliste für einen Typ angezeigt wird:

   ::: moniker range="vs-2017"

   ![Visual Studio, Member-Liste](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio, Member-Liste](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Suchfeld

   Visual Studio kann angesichts der zahlreichen Menüs, Optionen und Eigenschaften zuweilen übermächtig wirken. Mit dem Suchfeld finden Sie in Visual Studio schnell, was Sie suchen. Wenn Sie beginnen, den Namen dessen einzugeben, wonach Sie suchen, listet Visual Studio Ergebnisse auf, mit denen Sie ans gewünschte Ziel gelangen. Wenn Sie Visual Studio Funktionalitäten wie etwa die Unterstützung für eine zusätzliche Programmiersprache hinzufügen müssen, liefert das Suchfeld Ergebnisse, mit denen Sie Visual Studio-Installer zum Installieren einer Workload oder einer einzelnen Komponente öffnen können.

   > [!TIP]
   > Verwenden Sie die Tastenkombination **STRG**+**Q**, um direkt zum Suchfeld zu wechseln.

   ::: moniker range="vs-2017"

   ![Suchfeld „Schnellstart“ in Visual Studio 2017](../media/quick-launch-nuget.png)

   Weitere Informationen finden Sie unter [Schnellstart](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Screenshot: Suchfeld in Visual Studio 2019](media/vs-2019/quick-launch.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Führen Sie unabhängig von App-Typ oder Programmiersprache gemeinsam und in Echtzeit Bearbeitungs- und Debugvorgänge aus. Sie können Ihr aktuelles Projekt sowie Debugsitzungen, Terminalinstanzen, Localhost-Web-Apps, Sprachanrufe und vieles mehr sofort und sicher freigeben.

- [Aufrufhierarchie](../../ide/reference/call-hierarchy.md)

   Im Fenster **Aufrufhierarchie** werden die Methoden angezeigt, mit denen eine ausgewählte Methode aufgerufen wird. Diese Informationen können nützlich sein, wenn Sie die Methode ändern oder entfernen oder einen Fehler aufspüren möchten.

   ::: moniker range="vs-2017"

   ![Fenster „Aufrufhierarchie“ in Visual Studio](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Fenster „Aufrufhierarchie“ in Visual Studio](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   Mit CodeLens können Sie nach Verweisen auf Ihren Code, Änderungen an Ihrem Code, verknüpften Fehlern, Arbeitselementen, Codeüberprüfungen und Komponententests suchen, ohne den Editor verlassen zu müssen.

   ::: moniker range="vs-2017"

   ![CodeLens in Visual Studio](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![CodeLens in Visual Studio](media/vs-2019/codelens.png)

   ::: moniker-end

- [Gehe zu Definition](../../ide/go-to-and-peek-definition.md)

   Mit der Funktion „Gehe zu Definition“ gelangen Sie direkt zu der Stelle, an der eine Funktion oder ein Typ definiert ist.

   ::: moniker range="vs-2017"

   ![„Zur Definition wechseln“ in Visual Studio 2017](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![„Zur Definition wechseln“ in Visual Studio 2019](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Definition einsehen](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Im Fenster **Definitionsvorschau** wird die Definition einer Methode oder eines Typs angezeigt, ohne eine separate Datei zu öffnen.

   ::: moniker range="vs-2017"

   ![„Code einsehen“ in Visual Studio](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![„Code einsehen“ in Visual Studio](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Installieren von Visual Studio-IDE

In diesem Abschnitt erstellen Sie ein einfaches Projekt, um einige Dinge auszuprobieren, die mit Visual Studio möglich sind. Sie ändern das Farbschema, verwenden [IntelliSense](../../ide/using-intellisense.md) als Programmierhilfe und debuggen eine App, um den Wert einer Variablen während der Ausführung des Programms anzuzeigen.

::: moniker range="vs-2017"

[Laden Sie zunächst Visual Studio herunter](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download), und installieren Sie es auf Ihrem System. Mit dem modularen Installationsprogramm können Sie *Workloads* auswählen und installieren, die Gruppen von Funktionen sind, die für die bevorzugte Programmiersprache oder Plattform erforderlich sind. Damit Sie die Schritte zum [Erstellen eines Programms](#create-a-program) ausführen können, müssen Sie während der Installation die Workload **Plattformübergreifende .NET Core-Entwicklung** auswählen.

::: moniker-end

::: moniker range=">=vs-2019"

[Laden Sie zunächst Visual Studio herunter](https://visualstudio.microsoft.com/downloads), und installieren Sie es auf Ihrem System. Mit dem modularen Installationsprogramm können Sie *Workloads* auswählen und installieren, die Gruppen von Funktionen sind, die für die bevorzugte Programmiersprache oder Plattform erforderlich sind. Damit Sie die Schritte zum [Erstellen eines Programms](#create-a-program) ausführen können, müssen Sie während der Installation die Workload **Plattformübergreifende .NET Core-Entwicklung** auswählen.

::: moniker-end

![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../media/dotnet-core-cross-platform-workload.png)

Wenn Sie Visual Studio zum ersten Mal öffnen, können Sie sich optional mit Ihrem Microsoft-Konto oder Ihrem Geschäfts-, Schul- oder Unikonto [anmelden](../../ide/signing-in-to-visual-studio.md).

## <a name="customize-visual-studio"></a>Anpassen von Visual Studio

Sie können die Benutzeroberfläche von Visual Studio personalisieren und beispielsweise das Standardfarbdesign ändern.

### <a name="change-the-color-theme"></a>Ändern des Farbdesigns

So ändern Sie das Design in **Dunkel**:

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio. Wählen Sie im Startfenster **Ohne Code fortfahren** aus.

   ![Startfenster in Visual Studio 2019](media/vs-2019/continue-without-code.png)

   Die IDE wird geöffnet.

::: moniker-end

2. Klicken Sie auf der Menüleiste auf **Extras** > **Optionen**, um das Dialogfeld **Optionen** zu öffnen.

3. Ändern Sie auf der Optionsseite **Umgebung** > **Allgemein** die Auswahl für **Farbdesign** in **Dunkel**, und klicken Sie dann auf **OK**.

   ![Ändern des Farbschemas in dunkel in Visual Studio](media/change-color-theme.png)

   Das Farbdesign wird für die gesamte IDE in **Dunkel** geändert.

   ::: moniker range="vs-2017"

   ![Visual Studio im Design „Dunkel“](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio im Design „Dunkel“](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Auswählen der Umgebungseinstellungen

Als nächstes konfigurieren wir Visual Studio so, dass es Umgebungseinstellungen verwendet, die auf Visual Basic-Entwickler zugeschnitten sind.

1. Klicken Sie in der Menüleiste auf **Extras** > **Einstellungen importieren und exportieren**.

2. Klicken Sie im **Assistenten zum Importieren und Exportieren von Einstellungen** auf der ersten Seite auf **Alle Einstellungen zurücksetzen** und dann auf **Weiter**.

3. Wählen Sie auf der Seite **Aktuelle Einstellungen speichern** eine Option zum Speichern oder Nichtspeichern Ihrer aktuellen Einstellungen, und wählen Sie dann **Weiter**. (Wenn Sie keine Einstellungen angepasst haben, wählen Sie **Nein, einfach die Einstellungen zurücksetzen meine aktuellen Einstellungen überschreiben**.)

4. Wählen Sie auf der Seite **Standardsammlung von Eigenschaften auswählen** die Option **Visual Basic** aus, und klicken Sie dann auf **Fertig stellen**.

5. Klicken Sie auf der Seite **Zurücksetzungsvorgang abgeschlossen** auf **Schließen**.

Weitere Informationen dazu, wie Sie die IDE personalisieren können, finden Sie unter [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Erstellen eines Programms

Darum werden wir mit Ihnen jetzt ein einfaches Programm erstellen.

::: moniker range="vs-2017"

1. Wählen Sie auf der Visual Studio-Menüleiste **Datei** > **Neues Projekt** aus.

   ![„Datei“ > „Neu“ > „Projekt“ in der Menüleiste](media/file-new-project-menu.png)

   Im Dialogfeld **Neues Projekt** werden mehrere *Projektvorlagen* angezeigt. Eine Vorlage enthält die grundlegenden Dateien und Einstellungen, die für einen bestimmten Projekttyp erforderlich sind.

1. Wählen Sie unterhalb von **Visual Basic** die Kategorie **.NET Core** aus, und wählen Sie dann die Vorlage **Konsolen-App (.NET Core)**. Geben Sie **HelloWorld** im Textfeld **Name** ein, und klicken Sie auf **OK**.

   ![.NET Core-App-Vorlage](media/overview-npd.png)

   > [!NOTE]
   > Wenn die Kategorie **.NET Core** nicht angezeigt wird, müssen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** installieren. Klicken Sie hierfür im Dialogfeld **Neues Projekt** unten links auf den Link **Visual Studio-Installer öffnen**. Nachdem der Visual Studio-Installer geöffnet wurde, wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Ändern**.

   Visual Studio erstellt daraufhin das Projekt. Die Vorlage erstellt eine einfache „Hello World“-Anwendung, mit der die <xref:System.Console.WriteLine?displayProperty=nameWithType>-Methode aufgerufen wird, um die Literalzeichenfolge „Hello World!“ im Konsolenfenster (Programmausgabe).

   Kurz darauf sollte nun etwa Folgendes angezeigt werden:

   ![Visual Studio-IDE](media/overview-ide-console-app.png)

   Der Visual Basic-Code für Ihre App wird im Editor-Fenster angezeigt, der den meisten Raum einnimmt. Beachten Sie, dass der Text automatisch farbig hervorgehoben wird, um verschiedene Bestandteile des Codes anzuzeigen, z.B. Schlüsselwörter und Typen. Darüber hinaus zeigen kleine, vertikale gestrichelte Linien im Code an, welche geschweiften Klammern zusammengehören, und anhand der Zeilennummern können Sie sich später im Code orientieren. Sie können die kleinen Minuszeichen in Kästchen auswählen, um Codeblöcke ein- oder auszublenden. Mit dieser Codegliederungsfunktion können Sie Code ausblenden, den Sie nicht benötigen, um die Übersichtlichkeit des Bildschirms zu optimieren. Auf der rechten Seite werden im Fenster **Projektmappen-Explorer** die Projektdateien aufgelistet.

   ![Visual Studio-IDE mit roten Markierungen](media/overview-ide-console-app-red-boxes.png)

   Es sind noch mehr Menüs und Toolfenster verfügbar, aber für den Moment wenden wir uns Anderem zu.

1. Starten Sie nun die App. Wählen Sie hierzu auf der Menüleiste im Menü **Debuggen** die Option **Ohne Debuggen starten** aus. Alternativ können Sie auch die Tastenkombination **STRG**+**F5** drücken.

   ![Menü „Debuggen“ > „Ohne Debuggen starten“](../media/overview-start-without-debugging.png)

   Visual Studio erstellt die App, und es wird ein Konsolenfenster mit der Meldung **Hello World!** geöffnet. Sie haben nun eine funktionierende App!

   ![Konsolenfenster](../media/overview-console-window.png)

1. Drücken Sie eine beliebige Taste auf der Tastatur, um das Konsolenfenster zu schließen.

1. Fügen wir der App weiteren Code hinzu. Fügen Sie vor der Zeile `Console.WriteLine("Hello World!")` den folgenden Visual Basic-Code ein:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Der Code zeigt **What is your name?** (Wie heißen Sie?) im Konsolenfenster an und wartet, bis der Benutzer Text eingegeben und die **EINGABETASTE** gedrückt hat.

1. Ändern Sie die Zeile `Console.WriteLine("Hello World!")` in den folgenden Code:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Führen Sie die App erneut aus, indem Sie **STRG**+**F5** drücken.

   Visual Studio erstellt die App neu, und Sie werden im nun geöffneten Konsolenfenster zur Eingabe Ihres Namens aufgefordert.

1. Geben Sie Ihren Namen im Konsolenfenster ein, und drücken Sie die **EINGABETASTE**.

   ![Konsolenfenstereingabe](../media/overview-console-input.png)

1. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen und das ausgeführte Programm zu beenden.

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie auf der Visual Studio-Menüleiste **Datei** > **Neues Projekt** aus.

   ![„Datei“ > „Neu“ > „Projekt“ in der Menüleiste](media/vs-2019/file-new-project.png)

   Das Fenster **Neues Projekt erstellen** wird geöffnet und zeigt verschiedene *Vorlagen* für Projekte an. Eine Vorlage enthält die grundlegenden Dateien und Einstellungen, die für einen bestimmten Projekttyp erforderlich sind.

1. Geben Sie **.NET Core Konsole** in das Suchfeld ein, um die gewünschte Vorlage zu finden. Die Liste mit den verfügbaren Vorlagen wird automatisch nach den eingegebenen Schlüsselwörtern gefiltert. Sie können die Vorlagenergebnisse noch weiter filtern, indem Sie in der Dropdownliste **Sprache** die Option **Visual Basic** auswählen.

1. Wählen Sie die Vorlage **Konsolen-App (.NET Core)** und anschließend **Weiter** aus.

   ![Erstellen eines neuen Projekts in Visual Studio](media/vs-2019/create-new-project.png)

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname** die Zeichenfolge **HelloWorld** ein, ändern Sie optional das Verzeichnis für Ihre Projektdateien, und wählen Sie anschließend **Erstellen** aus.

   ![Konfigurieren eines neuen Projekts in Visual Studio](media/vs-2019/configure-new-project.png)

   Visual Studio erstellt daraufhin das Projekt. Die Vorlage erstellt eine einfache „Hello World“-Anwendung, mit der die <xref:System.Console.WriteLine?displayProperty=nameWithType>-Methode aufgerufen wird, um die Literalzeichenfolge „Hello World!“ im Konsolenfenster (Programmausgabe).

   Kurz darauf sollte nun etwa Folgendes angezeigt werden:

   ![Visual Studio-IDE](media/overview-ide-console-app.png)

   Der Visual Basic-Code für Ihre App wird im Editor-Fenster angezeigt, der den meisten Raum einnimmt. Beachten Sie, dass der Text automatisch farbig hervorgehoben wird, um verschiedene Bestandteile des Codes anzuzeigen, z.B. Schlüsselwörter und Typen. Darüber hinaus zeigen kleine, vertikale gestrichelte Linien im Code an, welche geschweiften Klammern zusammengehören, und anhand der Zeilennummern können Sie sich später im Code orientieren. Sie können die kleinen Minuszeichen in Kästchen auswählen, um Codeblöcke ein- oder auszublenden. Mit dieser Codegliederungsfunktion können Sie Code ausblenden, den Sie nicht benötigen, um die Übersichtlichkeit des Bildschirms zu optimieren. Auf der rechten Seite werden im Fenster **Projektmappen-Explorer** die Projektdateien aufgelistet.

   ![Visual Studio-IDE mit roten Markierungen](media/overview-ide-console-app-red-boxes.png)

   Es sind noch mehr Menüs und Toolfenster verfügbar, aber für den Moment wenden wir uns Anderem zu.

1. Starten Sie nun die App. Wählen Sie hierzu auf der Menüleiste im Menü **Debuggen** die Option **Ohne Debuggen starten** aus. Alternativ können Sie auch die Tastenkombination **STRG**+**F5** drücken.

   ![Menü „Debuggen“ > „Ohne Debuggen starten“](media/vs-2019/start-without-debugging.png)

   Visual Studio erstellt die App, und es wird ein Konsolenfenster mit der Meldung **Hello World!** geöffnet. Sie haben nun eine funktionierende App!

   ![Konsolenfenster](../media/vs-2019/overview-console-window.png)

1. Drücken Sie eine beliebige Taste auf der Tastatur, um das Konsolenfenster zu schließen.

1. Fügen wir der App weiteren Code hinzu. Fügen Sie vor der Zeile `Console.WriteLine("Hello World!")` den folgenden Visual Basic-Code ein:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Der Code zeigt **What is your name?** (Wie heißen Sie?) im Konsolenfenster an und wartet, bis der Benutzer Text eingegeben und die **EINGABETASTE** gedrückt hat.

1. Ändern Sie die Zeile `Console.WriteLine("Hello World!")` in den folgenden Code:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Führen Sie die App erneut aus, indem Sie **STRG**+**F5** drücken.

   Visual Studio erstellt die App neu, und Sie werden im nun geöffneten Konsolenfenster zur Eingabe Ihres Namens aufgefordert.

1. Geben Sie Ihren Namen im Konsolenfenster ein, und drücken Sie die **EINGABETASTE**.

   ![Konsolenfenster](../media/vs-2019/overview-console-input.png)

1. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen und das ausgeführte Programm zu beenden.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Verwenden von Refactoring und IntelliSense

Im Folgenden werden einige Methoden erläutert, wie Sie mit [Refactoring](../../ide/refactoring-in-visual-studio.md) und [IntelliSense](../../ide/using-intellisense.md) effizienter programmieren können.

Benennen Sie zunächst die Variable `name` um:

1. Doppelklicken Sie auf die Variable `name`, um sie auszuwählen.

2. Geben Sie den neuen Namen (**username**) der Variable ein.

   Achten Sie auf das graue Feld, das die Variable umgibt und auf die Glühbirne, die am Rand angezeigt wird.

3. Klicken Sie auf das Glühbirnensymbol, um die verfügbaren [Schnellaktionen](../../ide/quick-actions.md) anzuzeigen. Klicken Sie auf **'name' in 'username' umbenennen**.

   ![Umbenennen einer Aktion in Visual Studio](media/rename-quick-action.png)

   Die Variable wird für im gesamten Projekt umbenannt, in diesem Fall betrifft dies nur zwei Stellen.

4. Im Folgenden wird IntelliSense näher erläutert. Geben Sie unter der Zeile `Console.WriteLine("Hello " + username + "!")` das folgende Codefragment ein:

    ```vb
   Dim now = Date.
   ```

   Ein Feld zeigt die Members der Klasse <xref:System.DateTime> an. Darüber hinaus wird die Beschreibung des aktuell ausgewählten Members in einem separaten Feld angezeigt.

   ![Auflistung von Members durch IntelliSense in Visual Studio](media/intellisense-list-members.png)

5. Wählen Sie den Member **Now** aus, bei dem es sich um eine Eigenschaft der Klasse handelt, indem Sie auf diesen doppelklicken, oder es mit den Pfeiltasten nach oben oder unten auswählen, und die **TAB-Taste** drücken.

6. Geben Sie darunter folgende Codezeilen ein, oder kopieren Sie diese:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> ist ein wenig anders als <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, denn es fügt nach dem Einfügen kein Zeilenabschlusszeichen hinzu. Das bedeutet, dass der nächste Textabschnitt, der an die Ausgabe gesendet wird, in der gleichen Zeile ausgegeben wird. Sie können auf jede dieser Methoden in Ihrem Code zeigen, um deren Beschreibung anzuzeigen.

7. Anschließend wird erneut ein Refactoring durchgeführt, um den Code etwas präziser zu gestalten. Klicken Sie in der Zeile `Dim now = Date.Now` auf die Variable `now`.

   Beachten Sie, dass ein kleines Schraubendrehersymbol am Rand dieser Zeile angezeigt wird.

8. Klicken Sie auf das Schraubendrehersymbol, um zu sehen, welche Vorschläge Visual Studio macht. In diesem Fall zeigt es das Refactoring [Inline temporär variabel](../../ide/reference/inline-temporary-variable.md) an, um eine Codezeile zu entfernen, ohne das gesamte Verhalten des Codes zu ändern:

   ![Refactoring „Inline temporär variabel“ in Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Klicken Sie auf **Inline temporär variabel**, um den Code umzugestalten.

::: moniker range="vs-2017"

10. Führen Sie das Programm erneut aus, indem Sie **STRG**+**F5** drücken. Die Ausgabe sieht in etwa folgendermaßen aus:

    ![Konsolenfenster mit Programmausgabe](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Führen Sie das Programm erneut aus, indem Sie **STRG**+**F5** drücken. Die Ausgabe sieht in etwa folgendermaßen aus:

    ![Konsolenfenster mit Programmausgabe](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Debuggen von Code

Wenn Sie Code schreiben, müssen Sie ihn auszuführen und auf Fehler prüfen. Mit dem Debugsystem von Visual Studio können Sie Ihren Code Anweisung für Anweisung durchlaufen und dabei die Variablen untersuchen. Sie können *Breakpoints* festlegen, mit denen die Codeausführung an einer bestimmten Zeile beendet wird. Sie können sehen, wie sich der Wert einer Variablen bei der Codeausführung ändert, und vieles mehr.

Legen Sie einen Breakpoint fest, um den Wert der Variable `username` zu sehen, während das Programm ausgeführt wird.

1. Suchen Sie die Codezeile `Console.WriteLine("Hello " + username + "!")`. Wenn Sie einen Breakpoint für diese Codezeile festlegen, damit die Ausführung des Programms an dieser Zeile angehalten wird, klicken Sie auf den äußeren linken Rand des Editors. Sie können auch an einer anderen Stelle der Codezeile klicken und dann **F9** drücken.

   Ein roter Kreis wird am äußeren linken Rand angezeigt, und der Code wird rot hervorgehoben.

   ![Breakpoint an einer Codezeile in Visual Studio](media/breakpoint.png)

1. Starten Sie das Debuggen, indem Sie auf **Debuggen** > **Debuggen starten** klicken oder **F5** drücken.

1. Wenn das Konsolenfenster angezeigt wird und Sie nach Ihrem Namen fragt, geben Sie diesen ein, und drücken Sie die **EINGABETASTE**.

   Der Fokus kehrt zum Code-Editor von Visual Studio zurück und die Codezeile mit dem Breakpoint wird gelb hervorgehoben. Das bedeutet, dass dies die nächste Codezeile ist, die vom Programm ausgeführt wird.

1. Zeigen Sie mit der Maus auf die Variable `username`, um deren Wert anzuzeigen. Alternativ können Sie mit der rechten Maustaste auf `username` klicken und **Überwachung hinzufügen** auswählen, um die Variable zum **Überwachungsfenster** hinzuzufügen. Dort wird deren Wert ebenfalls angezeigt.

   ![Variablenwert während des Debuggens in Visual Studio](media/debugging-variable-value.png)

1. Drücken Sie erneut **F5**, damit das Programm bis zum Abschluss ausgeführt wird.

Weitere Informationen über den Debugprozess in Visual Studio finden Sie unter [Tour zu den Debuggerfeatures](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Nächste Schritte

Informationen zu weiteren Features von Visual Studio finden Sie in den folgenden Artikeln:

> [!div class="nextstepaction"]
> [Informationen zur Verwendung des Code-Editors](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Erfahren Sie mehr über Projekte und Projektmappen](tutorial-projects-solutions.md)

## <a name="see-also"></a>Siehe auch

- Entdecken Sie [weitere Visual Studio-Features](../../ide/advanced-feature-overview.md).
- Besuche Sie [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/).
- Lesen Sie den [Visual Studio-Blog](https://devblogs.microsoft.com/visualstudio/).
