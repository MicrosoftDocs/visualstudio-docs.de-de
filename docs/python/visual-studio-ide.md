---
description: Die integrierte Entwicklungsumgebung für Visual Studio ist eine kreative Startplattform für Python (und andere Sprachen), die Sie verwenden können, um Code erst zu bearbeiten, zu debuggen und zu testen und die App anschließend zu veröffentlichen.
title: Überblick über Visual Studio für Python-Entwickler
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 7e4a0c227f8c833febf20ed4e8dba82b814e3223
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223783"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Willkommen in der Visual Studio-IDE | Python

Die *integrierte Entwicklungsumgebung* für Visual Studio ist eine kreative Startplattform für Python (und andere Sprachen), die Sie verwenden können, um Code erst zu bearbeiten, zu debuggen und zu testen und die App anschließend zu veröffentlichen. Bei einer integrierten Entwicklungsumgebung (IDE) handelt es sich um ein funktionsreiches Programm, das für viele Aspekte der Softwareentwicklung verwendet werden kann. Neben dem üblichen Editor und dem Debugger, den die meisten IDEs bereitstellen, enthält Visual Studio Codevervollständigungstools, interaktive REPL-Umgebungen und weitere Features zur Erleichterung der Softwareentwicklung.

[![Visual Studio mit einem Python-Projekt](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Auf diesem Bild sehen Sie Visual Studio mit einem geöffneten Python-Projekt und einigen wichtigen Toolfenstern, die Sie wahrscheinlich verwenden:

- Im [**Projektmappen-Explorer**](../ide/solutions-and-projects-in-visual-studio.md) (oben rechts) können Sie Ihre Codedateien anzeigen, in ihnen navigieren und sie verwalten. Der **Projektmappen-Explorer** kann Sie beim Ordnen Ihres Codes unterstützen, indem er die Dateien in [Projektmappen und Projekte](../get-started/tutorial-projects-solutions.md) gruppiert.
  - Neben dem **Projektmappen-Explorer** befindet sich die [**Python-Umgebung**](managing-python-environments-in-visual-studio.md), über die Sie verschiedene Python-Interpreter verwalten können, die auf Ihrem Computer installiert sind.

  ::: moniker range=">=vs-2019"
  - Sie können auch Python-Code in einem Ordner öffnen und ausführen, ohne Projekt- und Projektmappendateien für Visual Studio zu erstellen. Weitere Informationen finden Sie unter [Schnellstart: Öffnen und Ausführen von Python-Code in einem Ordner](quickstart-05-python-visual-studio-open-folder.md).
  ::: moniker-end

- Im [Editorfenster](../ide/writing-code-in-the-code-and-text-editor.md) (Mitte), in dem Sie die meiste Zeit verbringen werden, werden Dateiinhalte angezeigt. Hier können Sie den [Python-Code](editing-python-code-in-visual-studio.md) bearbeiten, innerhalb Ihrer Codestruktur navigieren und Breakpoints während Debugsitzungen festlegen. Mit Python können Sie ebenfalls einen bestimmten Codeabschnitt auswählen und STRG+EINGABETASTE drücken, um diesen Code in einem [interaktiven REPL-Fenster](python-interactive-repl-in-visual-studio.md) auszuführen.

- Im Fenster [Ausgabe](../ide/reference/output-window.md) (unten in der Mitte) zeigt Visual Studio Benachrichtigungen, z. B. Debug- und Fehlermeldungen, Warnungen und Nachrichten zum Veröffentlichungsstatus an. Jede Nachrichtenquelle verfügt über eine eigene Registerkarte.
  - Ein [interaktives REPL-Fenster für Python](python-interactive-repl-in-visual-studio.md) wird im gleichen Bereich wie das Ausgabefenster angezeigt.

- Im [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (unten rechts) können Sie Arbeitselemente nachverfolgen und Code mithilfe von Techniken zur Versionskontrolle, wie etwa [Git](https://git-scm.com/) und [Team Foundation-Versionskontrolle (Team Foundation Version Control, TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true), mit anderen teilen.

## <a name="editions"></a>Editionen

Visual Studio ist für Windows und Mac verfügbar. Python wird jedoch nur für Visual Studio unter Windows unterstützt.

Es gibt drei Editionen von Visual Studio unter Windows: Community, Professional und Enterprise. Unter [Visual Studio-IDEs im Vergleich](https://visualstudio.microsoft.com/vs/compare/) erfahren Sie, welche Features in der jeweiligen Edition unterstützt werden.

## <a name="popular-productivity-features"></a>Gängige Features zur Steigerung der Produktivität

Einige gängige Features in Visual Studio, mit denen Sie bei der Entwicklung von Software noch produktiver sind:

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense steht für eine Gruppe von Features, mit denen Informationen zum Code direkt im Editor angezeigt und in einigen Fällen kleine Codeabschnitte für Sie geschrieben werden. Damit verfügen Sie über eine grundlegende Dokumentation, die in den Editor integriert ist, sodass Sie die Typinformationen nicht mehr an anderer Stelle nachsehen müssen. Die IntelliSense-Features unterscheiden sich je nach Sprache. Im Artikel [Bearbeiten von Python-Code](editing-python-code-in-visual-studio.md#intellisense) finden Sie die relevanten Informationen für Python. In der folgenden Abbildung ist dargestellt, wie mit IntelliSense eine Memberliste für einen Typ angezeigt wird:

   ![Membervervollständigung mit Visual Studio IntelliSense](media/code-editing-completions-simple.png)

- [Refactoring](refactoring-python-code.md)

   Wenn Sie mit der rechten Maustaste auf den Code klicken und **Schnellaktionen und Refactorings...** auswählen, stellt Visual Studio Vorgänge wie das intelligente Umbenennen von Variablen, das Extrahieren von Codezeilen in eine neue Methode und das Ändern der Reihenfolge von Methodenparametern zur Verfügung.

   ![Refactoring in Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Linting](refactoring-python-code.md)

   Durch Linting wird Ihr Python-Code auf Fehler und häufige Probleme überprüft. So können Sie einfacher bewährte Python-Programmiermuster verwenden.

   ![PyLint-Befehl im Kontextmenü für Python-Projekte](media/code-pylint-command.png)

- Suchfeld

   Visual Studio kann angesichts der zahlreichen Menüs, Optionen und Eigenschaften zuweilen übermächtig wirken. Mit dem Suchfeld finden Sie in Visual Studio schnell, was Sie suchen. Wenn Sie beginnen, den Namen dessen einzugeben, wonach Sie suchen, listet Visual Studio Ergebnisse auf, mit denen Sie ans gewünschte Ziel gelangen. Wenn Sie Visual Studio Funktionalitäten wie etwa die Unterstützung für eine zusätzliche Programmiersprache hinzufügen müssen, liefert das Suchfeld Ergebnisse, mit denen Sie Visual Studio-Installer zum Installieren einer Workload oder einer einzelnen Komponente öffnen können.

   ![Suchfeld in Visual Studio](media/tour-ide-quick-launch.png)

- Wellenlinien und [schnelle Aktionen](../ide/quick-actions.md)

   Wellenlinien sind wellenförmige Unterstreichungen, die Sie auf Fehler oder mögliche Probleme in Ihrem Code hinweisen. Dank dieser visuellen Hinweisen können Sie Probleme sofort beheben, ohne zu warten, bis der Fehler beim Kompilieren oder beim Ausführen des Programms entdeckt wird. Wenn Sie auf eine Wellenlinie zeigen, werden zusätzliche Informationen zum Fehler angezeigt. Am linken Rand wird ggf. auch eine Glühbirne mit Aktionen, schnelle Aktionen genannt, zum Beheben des Fehlers angezeigt.

   ![Wellenlinien in Visual Studio](media/tour-ide-squiggles.png)

- [„Gehe zu Definition“ und „Definition einsehen“](../ide/go-to-and-peek-definition.md)

   Mit dem Feature **Gehe zu Definition** gelangen Sie direkt zu der Stelle, an der eine Funktion oder ein Typ definiert wird. Der Befehl **Definition einsehen** zeigt die Definition in einem Fenster auf, ohne eine separate Datei zu öffnen. Der Befehl **Alle Verweise suchen** ist ebenfalls hilfreich, um zu ermitteln, wo Bezeichner definiert und verwendet werden.

   ![Codenavigationsbefehle](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Leistungsstarke Features für Python

::: moniker range=">=vs-2019"
- [Ausführen von Code ohne Projekt](quickstart-05-python-visual-studio-open-folder.md)

    Ab Visual Studio-2019 können Sie einen Ordner mit Python-Code öffnen, um Funktionen wie IntelliSense und Debuggen zu nutzen, ohne ein Visual Studio-Projekt für den Code zu erstellen.
::: moniker-end

- [Zusammenarbeiten mithilfe von Visual Studio](/visualstudio/liveshare/)

    Visual Studio Live Share ermöglicht Ihnen eine Zusammenarbeit in Echtzeit, um gemeinsam mit anderen Benutzern Projekte zu bearbeiten und zu debuggen – unabhängig von den verwendeten Programmiersprachen oder den erstellten App-Typen.

- [Interaktive Python-REPL](python-interactive-repl-in-visual-studio.md)

    Visual Studio bietet ein interaktives „Lesen-Auswerten-Ausgeben-Schleife“-Fenster (Read Eval Print Loop, REPL) für Ihre Python-Umgebungen, das eine Verbesserung gegenüber dem REPL darstellt, das Sie mit der Eingabe von *python.exe* in der Befehlszeile erhalten. Im Fenster **Interaktiv** können Sie Python-Code eingeben, damit direkt Ergebnisse angezeigt werden.

    ![Interaktives Python-Fenster](media/interactive-window.png)

- [Debuggen](debugging-python-in-visual-studio.md)

    Visual Studio bietet umfangreiche Debugfunktionen für Python, z.B.: Anfügen an ausgeführte Prozesse, Auswerten von Ausdrücken in den **Überwachungs**- und **Direktfenstern**, Untersuchen lokaler Variablen, Haltepunkte, Anweisungsausführung in Einzelschritten, Prozedurschritten oder bis Rücksprung, **Festlegen der nächsten Anweisung** und viele weitere. Sie können ebenfalls Python-Code remote debuggen, der auf Linux-Computern ausgeführt wird.

    ![Debuggen von Python in Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Interagieren mit C++](working-with-c-cpp-python-in-visual-studio.md)

    Viele Bibliotheken für Python wurden mit C++ geschrieben, um deren Leistung zu optimieren. Visual Studio bietet umfangreiche Funktionen für die Entwicklung von C++-Erweiterungen, einschließlich dem [Debuggen im gemischten Modus](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Debuggen im gemischten Modus von Python und C++ zusammen](media/mixed-mode-debugging.png)

- [Profilerstellung](profiling-python-code-in-visual-studio.md)

    Wenn Sie einen auf CPython basierenden Interpreter verwenden, können Sie die Leistung Ihres Python-Codes mit Visual Studio auswerten.

    ![Leistungsbericht für Profilerstellung](media/profiling-results.png)

- [Komponententests](unit-testing-python-in-visual-studio.md)

    Visual Studio unterstützt das Ermitteln, Ausführen und Debuggen von Komponententests in der IDE.

    ![Unittest, der einen fehlgeschlagenen Test anzeigt](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie die Möglichkeiten mit Python in Visual Studio näher kennenlernen möchten, können Sie einen der folgenden Schnellstarts bzw. eines der folgenden Tutorials aufrufen:

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen einer Web-App mit Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Arbeiten mit Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Erste Schritte mit dem Django-Webframework in Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Erste Schritte mit dem Flask-Webframework in Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Siehe auch

- Entdecken Sie [weitere Visual Studio-Features](../ide/advanced-feature-overview.md).
- Besuche Sie [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/).
- Lesen Sie den [Visual Studio-Blog](https://devblogs.microsoft.com/visualstudio/).
