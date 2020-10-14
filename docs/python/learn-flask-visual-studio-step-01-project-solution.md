---
title: 'Tutorial zu Flask in Visual Studio, Schritt 1: Grundlagen für Flask'
titleSuffix: ''
description: In diesem Artikel finden Sie eine exemplarische Vorgehensweise zu den Grundlagen von Flask im Kontext von Visual Studio-Projekten sowie Voraussetzungen, Git und virtuellen Umgebungen.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 018b9a6707ea46a9b1c46f820faf7bd47dac1ff9
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809897"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Tutorial: Erste Schritte mit dem Flask-Webframework in Visual Studio

[Flask](https://palletsprojects.com/p/flask/) ist ein einfaches Python-Framework für Webanwendungen, das die Grundlagen für URL-Routing und das Rendern von Seiten bereitstellt.

Flask wird als Mikroframework bezeichnet, da es Features wie die Überprüfung von Formularen, die Datenbankabstraktion, Authentifizierung usw. nicht direkt bereitstellt. Solche Features werden stattdessen von speziellen Python-Paketen bereitgestellt, die als Flask-*Erweiterungen* bezeichnet werden. Die Erweiterungen werden nahtlos in Flask integriert, sodass es so aussieht, als wären sie selbst Teil von Flask. Flask selbst stellt z.B. keine Seitenvorlagen-Engine bereit. Die Vorlagen werden von Erweiterungen wie Jinja und Jade bereitgestellt, so wie hier in diesem Tutorial erklärt wird.

In diesem Tutorial lernen Sie, wie die folgenden Aufgaben ausgeführt werden:

> [!div class="checklist"]
> - Erstellen eines Flask-Projekts in einem Git-Repository mithilfe der Vorlage „Leeres Flask-Webprojekt“ (Schritt 1)
> - Erstellen einer einseitigen Flask-App und Rendern dieser Seite mithilfe einer Vorlage (Schritt 2)
> - Bereitstellen statischer Dateien, Hinzufügen von Seiten und Verwenden von Vorlagenvererbung (Schritt 3)
> - Verwenden der Vorlage „Flask-Webprojekt“ zum Erstellen einer mehrseitigen App mit dynamischem Design (Schritt 4)
> - Verwenden Sie die Vorlage für Flask-Webprojekte für Umfragen, um eine Umfrage-App zu erstellen, die eine Reihe von Speicheroptionen nutzt (Azure Storage, MongoDB oder Arbeitsspeicher).

Im Zuge dieser Tutorialschritte erstellen Sie eine Visual Studio-Projektmappe, die drei unterschiedliche Projekte enthält. Sie erstellen das Projekt mithilfe verschiedener Flask-Projektvorlagen, die in Visual Studio enthalten sind. Da sich die Projekte in derselben Projektmappe befinden, können Sie einfach zwischen den unterschiedlichen Dateien hin- und herwechseln, um sie zu vergleichen.

> [!Note]
> Dieses Tutorial unterscheidet sich vom [Flask-Schnellstart](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json), in dem Sie einen tieferen Einblick in Flask erhalten sowie in die Verwendung der unterschiedlichen Flask-Projektvorlagen, die einen umfangreicheren Startpunkt für Ihre eigenen Projekte bereitstellen. Beispielsweise installieren die Projektvorlagen automatisch das Flask-Paket, wenn ein Projekt erstellt wird. Sie selbst müssen das Paket also nicht selbst installieren, so wie im Schnellstart gezeigt wird.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio 2017 oder höher unter Windows mit den folgenden Optionen:
  - Die Workload **Python-Entwicklung** (Registerkarte **Workload** im Installationsprogramm). Eine Anleitung finden Sie unter [Installieren der Python-Unterstützung für Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git für Windows** und **GitHub-Erweiterung für Visual Studio** auf der Registerkarte **Einzelne Komponenten** unter **Codetools**.

Flask-Projektvorlagen sind in allen früheren Versionen von Python-Tools für Visual Studio enthalten. In einzelnen Aspekten können sie sich allerdings von diesem Tutorial unterscheiden.

Die Python-Entwicklung wird in Visual Studio für Mac derzeit nicht unterstützt. Verwenden Sie unter Mac und Linux die [Python-Erweiterung in Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Schritt 1.1: Erstellen eines Visual Studio-Projekts und einer -Projektmappe

1. Klicken Sie in Visual Studio auf **Datei** > **Neu** > **Projekt**, suchen Sie nach „Flask“, und wählen Sie die Vorlage **Leeres Flask-Webprojekt** aus. (Sie finden die Vorlage auch in der Liste auf der linken Seite unter **Python** > **Web**.)

    ![Dialogfeld „Neues Projekt“ in Visual Studio für „Leeres Flask-Webprojekt“](media/flask/step01-new-blank-project.png)

1. Geben Sie in die Felder im unteren Bereich des Dialogfelds die folgenden Informationen ein (wie in der vorherigen Abbildung gezeigt), und klicken Sie dann auf **OK**:

    - **Name**: Legen Sie den Namen des Visual Studio-Projekts auf **BasicProject** fest. Dieser Name wird auch für das Flask-Projekt verwendet.
    - **Speicherort**: Geben Sie einen Speicherort an, an dem die Visual Studio-Projektmappe und das -Projekt erstellt werden sollen.
    - **Projektmappenname**: Legen Sie den Namen auf **LearningFlask** fest, da er sich für die Projektmappe als Container für mehrere Projekte in diesem Tutorial eignet.
    - **Projektmappenverzeichnis erstellen:** Übernehmen Sie die Einstellungen (den Standardwert).
    - **Neues Git-Repository erstellen:** Aktivieren Sie das Kontrollkästchen (das standardmäßig deaktiviert ist), damit Visual Studio beim Erstellen der Projektmappe ein lokales Git-Repository erstellt. Wenn diese Option nicht angezeigt wird, führen Sie den Visual Studio-Installer aus, und fügen Sie unter **Codetools** auf der Registerkarte **Einzelne Komponenten** **Git für Windows** und die **GitHub-Erweiterung für Visual Studio** hinzu.

1. Nach kurzer Zeit wird Ihnen von Visual Studio das Dialogfeld **Dieses Projekt erfordert externe Pakete** angezeigt (siehe unten). Dieses Dialogfeld wird angezeigt, da die Vorlage eine *requirements.txt*-Datei enthält, die auf das neueste Flask-Paket 1.x verweist. (Wählen Sie die Option **Show required packages (Erforderliche Pakete anzeigen)** aus, um die genauen Abhängigkeiten anzuzeigen.)

    ![Dialogfeld „Für dieses Projekt sind externe Pakete erforderlich“](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Wählen Sie die Option **I will install them myself (Ich führe die Installation selbst durch)** aus. In einem nächsten Schritt werden Sie die virtuelle Umgebung erstellen, damit sie auch sicher aus der Quellcodeverwaltung ausgeschlossen ist. (Die Umgebung kann immer aus *requirements.txt* erstellt werden.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Schritt 1.2: Überprüfen der Git-Steuerelemente und Veröffentlichen in einem Remoterepository

Da Sie im Dialogfeld **Neues Projekt** die Option **Neues Git-Repository erstellen** ausgewählt haben, wird für das Projekt bereits ein Commit für die lokale Quellcodeverwaltung ausgeführt, sobald der Erstellungsvorgang abgeschlossen ist. In diesem Schritt können Sie sich mit den Git-Steuerelementen in Visual Studio und dem **Team Explorer**-Fenster vertraut machen, in dem Sie an der Quellcodeverwaltung arbeiten werden.

1. Überprüfen Sie die Git-Steuerelemente in der unteren Ecke des Visual Studio-Hauptfensters. Von links nach rechts zeigen die Steuerelemente Folgendes an: nicht per Push übertragene Commits, ausgecheckte Änderungen, den Namen des Repositorys sowie den aktuellen Branch:

    ![Git-Steuerelemente im Visual Studio-Fenster](media/flask/step01-git-controls.png)

    > [!Note]
    > Wenn Sie im Dialogfeld **Neues Projekt** die Option **Neues Git-Repository erstellen** nicht auswählen, zeigen die Git-Steuerelemente nur den Befehl **Zur Quellcodeverwaltung hinzufügen** an, mit dem ein lokales Repository erstellt werden kann.
    >
    > ![Anzeige von „Zur Quellcodeverwaltung hinzufügen“ in Visual Studio, wenn kein Repository erstellt wurde](media/tutorials-common/step01-git-add-to-source-control.png)

1. Klicken Sie auf die Schaltfläche für die Änderungen, damit das **Team Explorer**-Fenster auf der Seite **Änderungen** in Visual Studio geöffnet wird. Da für das neu erstellte Projekt bereits automatisch ein Commit für die Quellcodeverwaltung ausgeführt wurde, werden keine ausstehenden Änderungen angezeigt.

    ![„Team Explorer“-Fenster auf der Seite „Änderungen“](media/flask/step01-team-explorer-changes.png)

1. Klicken Sie auf der Visual Studio-Statusleiste auf die Schaltfläche für die nicht per Push übertragenen Commits (der Aufwärtspfeil mit der **2**), um die Seite **Synchronisierung** im **Team Explorer** zu öffnen. Da Sie nur über ein lokales Repository verfügen, werden auf dieser Seite einfache Optionen zum Veröffentlichen des Repositorys in verschiedenen Remoterepositorys bereitgestellt.

    ![„Team Explorer“-Fenster mit verfügbaren Git-Repositoryoptionen für die Quellcodeverwaltung](media/flask/step01-team-explorer.png)

    Sie können für Ihre Projekte einen beliebigen Dienst auswählen. In diesem Tutorial wird die Verwendung von GitHub beschrieben. Der vollständige Beispielcode für das Tutorial befindet sich im Repository [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

1. Bei der Auswahl eines beliebigen **Veröffentlichen**-Steuerelements werden Sie von **Team Explorer** zur Eingabe weiterer Informationen aufgefordert. Wenn Sie z.B. das Beispiel für dieses Tutorial veröffentlichen, musste zuerst das Repository selbst erstellt werden. In diesem Fall wurde die Option **Per Push in Remoterepository übertragen** für die Repository-URL verwendet.

    ![„Team Explorer“-Fenster für die Übertragung per Push in ein vorhandenes Remoterepository](media/flask/step01-push-to-github.png)

    Wenn Sie über kein vorhandenes Repository verfügen, können Sie über die Optionen **In GitHub veröffentlichen** und **Per Push in Azure DevOps übertragen** direkt in Visual Studio ein Repository erstellen.

1. Machen Sie sich während der Arbeit mit diesem Tutorial mit der Verwendung der Steuerelemente zur Übertragung von Änderungen per Push oder per Commit in Visual Studio vertraut. Daran werden Sie in diesem Tutorial auch zu geeigneter Zeit erinnert.

> [!Tip]
> Klicken Sie zur schnellen Navigation im **Team Explorer** auf den Header (der in den obigen Abbildungen **Changes** oder **Push** benannt ist), um ein Kontextmenü der verfügbaren Seiten anzuzeigen.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Frage: Welche Vorteile habe ich, wenn ich die Quellcodeverwaltung von Beginn eines Projekts an verwende?

Antwort: Zunächst erhalten Sie durch die Verwendung der Quellcodeverwaltung von Beginn an eine regelmäßige externe Sicherung Ihres Projekts, insbesondere bei gleichzeitiger Verwendung eines Remoterepositorys. Im Gegensatz zur Verwaltung eines Projekts nur in einem lokalen Dateisystem bietet die Quellcodeverwaltung auch einen vollständigen Änderungsverlauf und die einfache Möglichkeit, eine einzelne Datei oder das gesamte Projekt in einem früheren Zustand wiederherzustellen. Über den Änderungsverlauf kann die Ursache von Regressionen (fehlgeschlagenen Tests) ermittelt werden. Bei der Mitarbeit von mehreren Personen an einem Projekt ist die Quellcodeverwaltung zudem wichtig für die Verwaltung von Überschreibungen und bei der Konfliktauflösung. Und schließlich ermöglicht die Quellcodeverwaltung, die im Grunde eine Form der Automatisierung darstellt, die Automatisierung von Builds, Tests sowie der Releaseverwaltung. Sie stellt den ersten Schritt bei der Verwendung von DevOps für ein Projekt dar. Und da die Einstiegsbarrieren so niedrig sind, gibt es keinen Grund, die Quellcodeverwaltung nicht von Beginn an zu verwenden.

Weitere Informationen zu automatisierter Quellcodeverwaltung finden Sie unter [The Source of Truth: The Role of Repositories in DevOps (Die Quelle der Wahrheit: Die Rolle von Repositorys in DevOps)](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), einem Artikel im MSDN-Magazin, in dem mobile Apps behandelt werden. Der Inhalt des Artikels gilt jedoch auch für Web-Apps.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Frage: Kann ich verhindern, dass Visual Studio für ein neues Projekt automatisch einen Commit ausführt?

Antwort: Ja. Wenn Sie die automatische Ausführung eines Commits deaktivieren möchten, wechseln Sie im **Team Explorer** zur Seite **Einstellungen**, und klicken Sie auf **Git** > **Globale Einstellungen**. Deaktivieren Sie die Option **Änderungen nach Mergevorgängen standardmäßig committen**, und klicken Sie anschließend auf **Aktualisieren**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Schritt 1.3: Erstellen der virtuellen Umgebung und Ausschließen aus der Quellcodeverwaltung

Nachdem Sie die Quellcodeverwaltung für das Projekt konfiguriert haben, können Sie die virtuelle Umgebung mit den für das Projekt erforderlichen Flask-Paketen erstellen. Anschließend können Sie im **Team Explorer** den Umgebungsordner aus der Quellcodeverwaltung ausschließen.

1. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Knoten **Python-Umgebungen**, und wählen Sie **Virtuelle Umgebung hinzufügen** aus.

    ![Befehl „Virtuelle Umgebung hinzufügen“ im Projektmappen-Explorer](media/flask/step01-add-virtual-environment-command.png)

1. Das Dialogfeld **Virtuelle Umgebung hinzufügen** mit der Meldung **Es wurde eine Datei „requirements.txt“ gefunden.** wird angezeigt. Mit der Meldung wird angezeigt, dass Visual Studio diese Datei zur Konfiguration der virtuellen Umgebung verwendet.

    ![Dialogfeld „Virtuelle Umgebung hinzufügen“ mit Meldung zu „requirements.txt“](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Klicken Sie auf **Erstellen**, um die Standardeinstellungen zu übernehmen. (Sie können den Namen der virtuellen Umgebung ändern. Dadurch wird jedoch nur der Name des Unterordners geändert, `env` ist dagegen eine Standardkonvention.)

1. Stimmen Sie den Administratorrechten zu, wenn Sie dazu aufgefordert werden. Der anschließende Download- und Installationsvorgang der Pakete durch Visual Studio kann einige Minuten dauern, da für Flask und zugehörige Abhängigkeiten mehrere tausend Dateien in über 100 Unterordnern heruntergeladen und installiert werden müssen. Der Fortschritt wird im **Ausgabe**-Fenster in Visual Studio angezeigt. Während des Vorgangs können Sie die Fragen und Antworten in den folgenden Abschnitten lesen. Eine Beschreibung der Abhängigkeiten von Flask finden Sie ebenfalls auf der [Installationsseite von Flask](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) (flask.pcocoo.org).

1. Klicken Sie bei den Git-Steuerelementen in Visual Studio (auf der Statusleiste) auf den Änderungsindikator (der **99&#42;** anzeigt), um die Seite **Änderungen** im **Team Explorer** zu öffnen.

    Durch das Erstellen der virtuellen Umgebung wurden Hunderte von Änderungen übertragen, die Sie jedoch nicht in die Quellcodeverwaltung einbeziehen müssen, da die Umgebung von jeder Person, die das Projekt klont, immer aus *requirements.txt* neu erstellt werden kann.

    Klicken Sie zum Ausschließen der virtuellen Umgebung mit der rechten Maustaste auf den **env**-Ordner, und wählen Sie die Option **Diese lokalen Elemente ignorieren** aus.

    ![Ignorieren einer virtuellen Umgebung in den Änderungen der Quellcodeverwaltung](media/flask/step01-ignore-local-items.png)

1. Nachdem die virtuelle Umgebung ausgeschlossen wurde, bleiben nur die Änderungen an der Projektdatei und *.gitignore* übrig. Die *.gitignore*-Datei enthält einen hinzugefügten Eintrag für den Ordner der virtuellen Umgebung. Wenn Sie die Änderungen anzeigen möchten, doppelklicken Sie auf die Datei.

1. Geben Sie eine Commit-Nachricht ein, und klicken Sie auf die Schaltfläche **Alle committen**. Anschließend können Sie die Commits gegebenenfalls per Push in das Remoterepository übertragen.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Frage: Warum sollte ich eine virtuelle Umgebung erstellen?

Antwort: Eine virtuelle Umgebung ist eine hervorragende Möglichkeit, die genauen Abhängigkeiten Ihrer App zu isolieren. Mit einer solchen Isolation können Konflikte innerhalb einer globalen Python-Umgebung vermieden werden, und Tests und die Zusammenarbeit werden unterstützt. Bei der Entwicklung einer App werden im Laufe der Zeit unweigerlich viele nützliche Python-Pakete importiert. Indem Sie die Pakete in einer projektspezifischen virtuellen Umgebung beibehalten, können Sie die *requirements.txt*-Datei des Projekts auf einfache Weise aktualisieren. Mit dieser Datei wird die Umgebung beschrieben, die in der Quellcodeverwaltung enthalten ist. Beim Kopieren des Projekts auf andere Computer, einschließlich Buildserver, Bereitstellungsserver und andere Entwicklungscomputer, kann die Umgebung auf einfache Weise über *requirements.txt* neu erstellt werden (weshalb die Umgebung auch nicht in der Quellcodeverwaltung vorhanden sein muss). Weitere Informationen finden Sie unter [Verwenden von virtuellen Umgebungen](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Frage: Wie entferne ich eine virtuelle Umgebung, für die bereits ein Commit für die Quellcodeverwaltung ausgeführt wurde?

Antwort: Bearbeiten Sie zuerst die *GITIGNORE*-Datei, um den Ordner auszuschließen. Suchen Sie dazu den Abschnitt am Ende mit dem Kommentar `# Python Tools for Visual Studio (PTVS)`, und fügen Sie eine neue Zeile für den Ordner der virtuellen Umgebung hinzu, z. B. `/BasicProject/env`. (Da die Datei im **Projektmappen-Explorer** in Visual Studio nicht angezeigt wird, öffnen Sie sie direkt über den Menübefehl **Datei** > **Öffnen** > **Datei**. Sie können die Datei auch über den **Team Explorer** öffnen: Klicken Sie dazu auf der Seite **Einstellungen** auf die Option **Repositoryeinstellungen**, und wechseln Sie zum Abschnitt **Ignore- und Attributdateien**. Klicken Sie anschließend auf den Link **Bearbeiten** neben **.gitignore**.)

Öffnen Sie nun ein Befehlsfenster. Navigieren Sie zum Ordner (z.B. *BasicProject*), der den Ordner für die virtuelle Umgebung enthält (z.B. *env*), und führen Sie `git rm -r env` aus. Führen Sie dann für diese Änderungen einen Commit von der Befehlszeile (`git commit -m 'Remove venv'`) oder von der Seite **Änderungen** im **Team Explorer** aus.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Schritt 1.4: Überprüfen der Codebausteine

1. Sobald die Projekterstellung abgeschlossen ist, werden die Projektmappe und das Projekt im **Projektmappen-Explorer** angezeigt, in dem das Projekt nur zwei Dateien enthält, nämlich *app.py* und *requirements.txt*:

    ![Dateien eines leeren Flask-Projekts im Projektmappen-Explorer](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Wie bereits erwähnt, gibt die *requirements.txt*-Datei die Flask-Paketabhängigkeit an. Wegen dieser Datei werden Sie bei der erstmaligen Erstellung des Projekts zum Erstellen einer virtuellen Umgebung aufgefordert.

1. Die einzelne *app.py*-Datei enthält drei Teile. Zunächst eine `import`-Anweisung für Flask, mit der eine Instanz der `Flask`-Klasse erstellt wird, die wiederum der Variable `app` zugewiesen ist und eine `wsgi_app`-Variable zuweist (die nützlich ist, wenn eine Bereitstellung auf einen Webhost erfolgt, die jedoch im Moment nicht verwendet wird):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Der zweite Teil am Ende der Datei ist gewissermaßen ein optionaler Code, der den Flask-Entwicklungsserver mit bestimmten Host- und Portwerten startet, die aus den Umgebungsvariablen stammen (Standard „localhost:5555“ wird übernommen):

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Der dritte Teil besteht aus einem kurzen Codeabschnitt, der einer URL-Route eine Funktion zuweist. Das bedeutet, dass die Funktion die Ressource bereitstellt, die von der URL identifiziert wird. Sie definieren Routen mithilfe des Decorators `@app.route` von Flask, dessen Argument die relative URL aus dem Stammverzeichnis der Website ist. Sie können im Code sehen, dass die Funktion hier nur eine Textzeichenfolge zurückgibt, die aber schon für einen Browser für das Rendern ausreicht. In den folgenden Schritten rendern Sie aufwendigere Seiten mit HTML.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Frage: Welchem Zweck dient das Argument __name__ für die Flask-Klasse?

Antwort: Das Argument ist der Name des Moduls oder Pakets der App und gibt an, wo Flask nach Vorlagen, statischen Dateien und anderen Ressourcen suchen soll, die zur App gehören. Für Apps, die in einem einzelnen Modul enthalten sind, ist `__name__` immer der richtige Wert. Dieser ist auch für Erweiterungen wichtig, die Debuginformationen benötigen. Weitere Informationen und zusätzliche Argumente finden Sie in der [Flask-Klassendokumentation](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Frage: Kann eine Funktion über mehr als einen Route-Decorator verfügen?

Antwort: Ja, Sie können so viele Decorators verwenden, wie Sie möchten, solange die gleiche Funktion mehrere Routen bereitstellt. Um beispielsweise die `hello`-Funktion für '/' und '/hello' zu verwenden, verwenden Sie den folgenden Code:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Frage: Wie verarbeitet Flask variable URL-Routen und Abfrageparameter?

Antwort: In einer Route markieren Sie beliebige Variablen mit `<variable_name>`, und Flask übergibt diese Variablen über ein benanntes Argument an die Funktion. Die Variable kann Teil des URL-Pfads sein oder sich in einem Abfrageparameter befinden. Zum Beispiel generiert eine Route in Form von `'/hello/<name>` ein Zeichenfolgenargument namens `name` für die Funktion. Die Verwendung von `?message=<msg>` in der Route analysiert den gegebenen Wert für den Abfrageparameter „message=“ und übergibt ihn als `msg` an die Funktion:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Um den Typ zu ändern, stellen Sie der Variable die Präfixe `int`, `float`, `path` (akzeptiert Schrägstriche zur Abgrenzung von Ordnernamen) und `uuid` voran. Weitere Informationen finden Sie in der Flask-Dokumentation unter [Variable rules (Regeln für Variablen)](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules).

Abfrageparameter sind ebenso über die Eigenschaft `request.args`, genauer gesagt über die Methode `request.args.get`, verfügbar. Weitere Informationen finden Sie im Abschnitt [The Request object (Das request-Objekt)](https://flask.palletsprojects.com/en/1.0.x/quickstart/#the-request-object) in der Flask-Dokumentation.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Frage: Kann Visual Studio eine „requirements.txt“-Datei aus einer virtuellen Umgebung generieren, nachdem ich andere Pakete installiert habe?

Antwort: Ja. Erweitern Sie den Knoten **Python-Umgebungen**, klicken Sie mit der rechten Maustaste auf die virtuelle Umgebung, und klicken Sie auf den Befehl **„requirements.txt“ generieren**. Verwenden Sie diesen Befehl am besten in regelmäßigen Abständen, wenn Sie die Umgebung ändern und einen Commit der Änderungen für *requirements.txt* in der Quellcodeverwaltung ausführen sowie andere Codeänderungen committen, die von dieser Umgebung abhängen. Wenn Sie Continuous Integration auf einem Buildserver eingerichtet haben, sollten Sie bei jeder Änderung der Umgebung die Datei generieren und einen Commit der Änderungen ausführen.

## <a name="step-1-5-run-the-project"></a>Schritt 1.5: Ausführen des Projekts

1. Wählen Sie in Visual Studio die Option **Debuggen** > **Debuggen starten** (**F5**) aus, oder verwenden Sie hierzu die Schaltfläche **Webserver** auf der Symbolleiste (der bei Ihnen angezeigte Browser kann ein anderer sein):

    ![Symbolleisten-Schaltfläche „Webserver ausführen“ in Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. Jeder Befehl weist der PORT-Umgebungsvariable eine beliebige Portnummer zu und führt dann `python app.py` aus. Der Code startet die App und verwendet dazu diesen Port auf dem Entwicklungsserver von Flask. Wenn Visual Studio die Meldung **Fehler beim Starten des Debuggers** anzeigt, da keine Startdatei vorhanden ist, klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf **app.py**, und klicken Sie auf **Als Startdatei festlegen**.

1. Beim Starten des Servers wird ein Konsolenfenster geöffnet, das das Serverprotokoll anzeigt. Visual Studio öffnet daraufhin automatisch einen Browser unter `http://localhost:<port>`, wo alle von der Funktion `hello` gerenderten Meldungen angezeigt werden sollten:

    ![Standardansicht des Flask-Projekts](media/flask/step01-first-run-success.png)

1. Wenn Sie fertig sind, stoppen Sie den Server, indem Sie das Konsolenfenster schließen. Sie können hierzu auch den Befehl **Debuggen** > **Debuggen beenden** in Visual Studio verwenden.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Frage: Was ist der Unterschied zwischen den Befehlen im Menü „Debuggen“ und den Serverbefehlen im Python-Untermenü des Projekts?

Antwort: Sie können den Server über die Befehle und Schaltflächen des **Debuggen**-Menüs in der Symbolleiste oder über die Befehle **Python** > **Server ausführen** oder **Python** > **Debugserver ausführen** im Kontextmenü des Projekts starten. Mit beiden Befehlen wird ein Konsolenfenster geöffnet, in dem die lokale URL (localhost:port) für den ausgeführten Server angezeigt wird. Allerdings müssen Sie einen Browser mit dieser URL manuell öffnen. Das Ausführen des Debugservers startet auch nicht automatisch den Visual Studio-Debugger. Später können Sie gegebenenfalls mit dem Befehl **Debuggen** > **An den Prozess anhängen** einen Debugger an den laufenden Prozess anhängen.

## <a name="next-steps"></a>Nächste Schritte

Zu diesem Zeitpunkt enthält das einfache Flask-Projekt den Startcode sowie den Seitencode in der gleichen Datei. Trennen Sie am besten diese beiden Aspekte. Sie sollten auch HTML und Daten mithilfe von Vorlagen trennen.

> [!div class="nextstepaction"]
> [Erstellen einer Flask-App mit Ansichten und Seitenvorlagen](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Flask Quickstart (Flask-Schnellstart)](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (flask.pocoo.org)
- Quellcode für das Tutorial auf GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)