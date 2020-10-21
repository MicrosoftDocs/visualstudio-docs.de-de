---
title: 'Tutorial zu Flask in Visual Studio, Schritt 5: Projektvorlage für Umfragen'
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise erhalten Sie grundlegende Informationen zu Flask im Zusammenhang mit Visual Studio-Projekten, insbesondere zu den Features der Vorlagen „Fragt ein Flask-Webprojekt ab“ und „Fragt ein Flask/Jade-Webprojekt ab“.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c9adda5eb9edba5e1ba62097d55c033be6c85d2e
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099361"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Schritt 5: Verwenden der Vorlage „Fragt ein Flask-Webprojekt ab“

**Vorheriger Schritt:[ Verwenden der vollständigen Vorlage „Flask-Webprojekt“](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Nachdem Sie sich erfolgreich mit der Vorlage „Flask-Webprojekt“ befasst haben, können Sie nun die dritte Flask-Vorlage („Fragt ein Flask-Webprojekt ab“) betrachten, die auf der gleichen Codebasis aufbaut.

In diesem Schritt wird Folgendes erläutert:

> [!div class="checklist"]
> - Erstellen eines Projekts von der Vorlage und Initialisieren der Datenbank (Schritt 5–1)
> - Grundlegendes zu Datenmodellen (Schritt 5–2)
> - Grundlegendes zu den Sicherungsdatenspeichern (Schritt 5.3)
> - Grundlegendes zu Umfragedetails und Ergebnisansichten (Schritt 5–4)

Visual Studio bietet ebenfalls die Vorlage „Fragt ein Flask/Jade-Webprojekt ab“, die eine identische App erzeugt, aber die Jade-Erweiterung für die Jinja-Vorlagen-Engine verwendet. Weitere Informationen finden Sie unter [Schritt 4 – Die Vorlage „Flask/Jade-Webprojekt“](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Schritt 5–1: Erstellen des Projekts

1. Wechseln Sie in Visual Studio zum **Projektmappen-Explorer**. Klicken Sie mit der rechten Maustaste auf die Projektmappe **LearningFlask**, die Sie in diesem Tutorial bereits erstellt haben, und klicken Sie auf **Hinzufügen** > **Neues Projekt**. (Wenn Sie stattdessen eine neue Projektmappe verwenden möchten, klicken Sie auf **Datei** > **Neu** > **Projekt**.)

1. Suchen Sie im Dialogfeld „Neues Projekt“ die Vorlage **Fragt ein Flask-Webprojekt ab**, und wählen Sie sie aus. Nennen Sie das Projekt **FlaskPolls**, und klicken Sie auf OK.

1. Wie die anderen Projektvorlagen in Visual Studio enthält die Vorlage „Fragt ein Flask-Webprojekt ab“ eine Datei namens *requirements.txt*. Visual Studio fragt, wohin diese Abhängigkeiten installiert werden sollen. Wählen Sie die Option **In einer virtuellen Umgebung installieren** aus. Klicken Sie im Dialogfeld **Virtuelle Umgebung hinzufügen** auf **Erstellen**, um die Standardwerte zu übernehmen. (Diese Vorlage erfordert Flask sowie die Pakete „azure-storage“ und „pymongo“. Die Vorlage „Fragt ein Flask/Jade-Webprojekt ab“ erfordert außerdem pyjade.)

1. Legen Sie das Projekt **FlaskPolls** als Standardprojekt für die Visual Studio-Projektmappe fest. Klicken Sie hierzu mit der rechten Maustaste im **Projektmappen-Explorer** auf das Projekt, und wählen Sie die Option **Als Startprojekt festlegen** aus. Das fett angezeigte Startprojekt wird ausgeführt, wenn Sie den Debugger starten.

1. Wählen Sie zum Ausführen des Servers **Debuggen** > **Debuggen starten** (**F5**) aus, oder verwenden Sie hierzu die Schaltfläche **Webserver** auf der Symbolleiste:

    ![Symbolleisten-Schaltfläche „Webserver ausführen“ in Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Die von der Vorlage erstellte App verfügt über drei Seiten: „Startseite“, „Info“ und „Kontakt“. Sie können über die obere Navigationsleiste zwischen diesen Seiten navigieren. Nehmen Sie sich ein paar Minuten Zeit, um die unterschiedlichen Teile der App zu überprüfen (die Seiten „Info“ und „Kontakt“ sind „Flask-Webprojekt“ sehr ähnlich und werden nicht weiter besprochen).

    ![Vollständige Ansicht der App „Fragt ein Flask-Webprojekt ab“](media/flask/step06-full-app-view.png)

1. Auf der Homepage initialisiert die Schaltfläche **Create Sample Polls** (Beispielumfragen erstellen) den Datenspeicher der App mit drei verschiedenen Umfragen, die auf der Seite *models/samples.json* beschrieben werden. Standardmäßig verwendet die App eine In-Memory-Datenbank (wie auf der Seite „Info“ dargestellt), die bei jedem Neustart der App zurückgesetzt wird. Die App enthält ebenfalls Code, um wie im Verlauf dieses Artikels beschrieben mit Azure Storage und MongoDB zu arbeiten.

1. Sobald Sie den Datenspeicher initialisiert haben, können Sie wie auf der Homepage dargestellt in den verschiedenen Umfragen abstimmen (die Navigationsleiste und die Fußzeile wurden aus Gründen der Übersichtlichkeit weggelassen):

    ![Ansicht der Umfrage-App nach der Initialisierung des Datenspeichers](media/flask/step06-polls-initialized.png)

1. Wenn Sie eine Umfrage anklicken, werden spezifische Optionen angezeigt:

    ![Benutzeroberfläche zur Abstimmung für eine Umfrage](media/flask/step06-polls-voting-interface.png)

1. Sobald Sie abstimmen, zeigt die App eine Ergebnisseite an, und Sie können erneut abstimmen:

    ![Ergebnisansicht nach der Abstimmung](media/flask/step06-polls-results.png)

1. Für die folgenden Abschnitte kann die App weiterhin ausgeführt werden.

    Wenn Sie die App beenden und [ein Commit der Änderungen für die Quellcodeverwaltung ausführen möchten](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), öffnen Sie zunächst im **Team Explorer** die Seite **Änderungen**. Klicken Sie mit der rechten Maustaste auf den Ordner für die virtuelle Umgebung (vermutlich **env**), und wählen Sie die Option **Diese lokalen Elemente ignorieren** aus.

### <a name="examine-the-project-contents"></a>Überprüfen des Projektinhalts

Wie bereits erwähnt. Viele Bestandteile eines auf der Grundlage der Vorlage „Fragt ein Flask-Webprojekt ab“ (und „Fragt ein Flask/Jade-Webprojekt ab“) erstellten Projekts sollten Ihnen bekannt vorkommen, wenn Sie die anderen Projektvorlagen in Visual Studio kennen. Die zusätzlichen Schritte in diesem Artikel fassen die wichtigeren Änderungen und Hinzufügungen zusammen: Datenmodelle und zusätzliche Ansichten.

## <a name="step-5-2-understand-the-data-models"></a>Schritt 5-2: Grundlegendes zu Datenmodellen

Die Datenmodelle für die App sind Python-Klassen namens „Poll“ (Umfrage) und „Choice“ (Auswahl). Diese werden in *models/\_\_init\_\_.py* definiert. Eine Poll-Klasse stellt eine Frage dar, und mehrere Choice-Instanzen stellen die verfügbaren Antworten dar. Eine Poll-Klasse verwaltet ebenfalls die Gesamtanzahl der Stimmen (für jede Option) und eine Methode, um Statistiken zu berechnen, die zum Generieren von Ansichten verwendet werden:

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Diese Datenmodelle sind generische Abstraktionen, durch die ermöglicht wird, dass die Ansichten der App für mehrere verschiedene Arten von Sicherungsdatenspeichern funktionieren. Diese werden im nächsten Schritt beschrieben.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Schritt 5–3: Grundlegendes zu den Sicherungsdatenspeichern

Die App, die von der Vorlage „Fragt ein Flask-Webprojekt“ erstellt wurde, kann für einen Datenspeicher im Arbeitsspeicher, im Azure-Tabellenspeicher oder in einer MongoDB-Datenbank ausgeführt werden.

Der Datenspeichermechanismus funktioniert folgendermaßen:

1. Der Repositorytyp wird durch die Umgebungsvariable `REPOSITORY_NAME` angegeben. Diese kann auf „memory“, „azuretablestore“ oder „mongodb“ festgelegt werden. Ein Teil des Codes in *settings.py* ruft den Namen ab und verwendet dabei standardmäßig „memory“. Wenn Sie den Sicherungsspeicher ändern möchten, müssen Sie die Umgebungsvariable festlegen und die App neu starten.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. Der Code von *settings.py* initialisiert dann ein `REPOSITORY_SETTINGS`-Objekt. Wenn Sie den Azure-Tabellenspeicher oder MongoDB verwenden möchten, müssen Sie diese Datenspeicher zunächst an anderer Stelle initialisieren und anschließend die erforderlichen Umgebungsvariablen festlegen, die der App mitteilen, wie eine Verbindung mit dem Datenspeicher hergestellt werden kann:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. In *views.py* ruft die App eine Factorymethode auf, um ein `Repository`-Objekt mithilfe des Namens und der Einstellungen des Datenspeichers zu initialisieren:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. Die `factory.create_repository`-Methode befindet sich in *models\factory.py*. Diese importiert das geeignete Repositorymodul und erstellt anschließend eine Instanz von `Repository`:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Die Implementierungen der `Repository`-Klasse, die für jeden Datenspeicher spezifisch sind, befinden sich in *models\azuretablestorage.py*, *models\mongodb.py* und *models\memory.py*. Die Azure Storage-Implementierung verwendet das Paket „azure-storage“. Die MongoDB-Implementierung verwendet das Paket „pymongo“. Wie bereits in Schritt 5.1 erwähnt wurde, sind beide Pakete in der Datei *requirements.txt* der Projektvorlage enthalten. Die Details zu ergründen wird als Übung für den Leser offen gelassen.

Kurz gesagt abstrahiert die Klasse `Repository` die spezifischen Eigenschaften eines Datenspeichers, und die App verwendet Umgebungsvariablen zur Laufzeit, um auszuwählen und zu konfigurieren, welche der drei Implementierungen verwendet werden soll.

Durch folgende Schritte wird Unterstützung für einen anderen Datenspeicher als die drei von der Projektvorlage bereitgestellten hinzugefügt, wenn Sie dies wünschen:

1. Kopieren Sie *memory.py* in eine neue Datei, sodass die Basisschnittstelle für die Klasse `Repository` vorhanden ist.
1. Ändern Sie die Implementierung der Klasse, damit diese dem verwendeten Datenspeicher entspricht.
1. Ändern Sie *factory.py* in einen weiteren `elif`-Fall, der den Namen für Ihren hinzugefügten Datenspeicher erkennt und das entsprechende Modul importiert.
1. Ändern Sie *settings.py*, damit ein weiterer Name in der Umgebungsvariable `REPOSITORY_NAME` erkannt und `REPOSITORY_SETTINGS` entsprechend initialisiert wird.

### <a name="seed-the-data-store-from-samplesjson"></a>Ausführen eines Seedings für den Datenspeicher von „samples.json“

Zu Beginn enthält ein ausgewählter Datenspeicher keine Umfragen. Deshalb zeigt die Startseite der App die Meldung **No polls available** (Keine Umfragen verfügbar) zusammen mit der Schaltfläche **Create Sample Polls** (Beispielumfragen erstellen) an. Sobald Sie auf die Schaltfläche klicken, ändert sich die Ansicht jedoch, und verfügbare Umfragen werden angezeigt. Dieser Wechsel wird von bedingten Tags in *templates\index.html* durchgeführt (einige leere Zeilen wurden aus Gründen der Übersichtlichkeit weggelassen):

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

Die Variable `polls` in der Vorlage stammt aus einem Aufruf von `repository.get_polls`, der nichts zurückgibt, bis der Datenspeicher initialisiert wurde.

Wenn Sie auf die Schaltfläche **Create Sample Polls** (Beispielumfragen erstellen) klicken, wird zur URL „/seed“ navigiert. Der Handler für diese Route wird in *views.py* definiert:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Der Aufruf von `repository.add_sample_polls()` endet bei einer der spezifischen `Repository`-Implementierungen für den ausgewählten Datenspeicher. Jede Implementierung ruft die `_load_samples_json`-Methode auf, die sich in *models\_\_init\_\_.py* befindet, um die Datei *models\samples.json* in den Arbeitsspeicher zu laden. Anschließend werden die Daten durchlaufen, um die erforderlichen `Poll`- und `Choice`-Objekte im Datenspeicher zu erstellen.

Sobald dieser Vorgang abgeschlossen ist, navigiert die `redirect('/')`-Anweisung in der `seed`-Methode zurück zur Startseite. Da `repository.get_polls` nun ein Datenobjekt zurückgibt, rendern die bedingten Tags in *templates\index.html* nun eine Tabelle, die die Umfragen enthält.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Frage: Wie werden neue Umfragen zur App hinzugefügt?

Antwort: Die App enthält in der Form, in der sie von der Projektvorlage bereitgestellt wird, keine Möglichkeit zum Hinzufügen oder Bearbeiten von Umfragen. Sie können *models\samples.json* ändern, um neue Initialisierungsdaten zu erstellen. Dadurch wird jedoch der Datenspeicher zurückgesetzt. Wenn Sie Bearbeitungsfeatures implementieren möchten, müssen Sie die Schnittstelle der Klasse `Repository` mit Methoden erweitern, um die erforderlichen Instanzen von `Choice` und `Poll` zu erstellen. Anschließend wird eine Benutzeroberfläche in zusätzliche Seiten implementiert, die diese Methoden verwenden.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Schritt 5–4: Grundlegendes zu Umfragedetails und Ergebnisansichten

Die meisten der von den Vorlagen „Fragt ein Flask-Webprojekt ab“ und „Fragt ein Flask/Jade-Webprojekt ab“ generierten Ansichten, z.B. die Ansichten für die Seiten „Info“ und „Kontakt“, sind den von der Vorlage „Flask-Webprojekt“ (oder Flask/Jade-Webprojekt) erstellten Ansichten sehr ähnlich, mit denen Sie am Anfang des Tutorials gearbeitet haben. Im vorherigen Abschnitt haben Sie bereits gelernt, wie die Startseite implementiert wird, um die Schaltfläche zur Initialisierung oder die Liste der Umfragen anzuzeigen.

Nun müssen noch die Ansicht für die Abstimmung (Details) und die Ergebnisse einer einzelnen Umfrage untersucht werden.

Wenn Sie eine Umfrage auf der Startseite auswählen, navigiert die App zur URL „/poll/\<key\>“. Hierbei entspricht *key* dem eindeutigen Bezeichner einer Umfrage. In *views.py* können Sie erkennen, dass die Funktion `details` zugewiesen wird, um das URL-Routing für GET- und POST-Anforderungen zu verarbeiten. Sie werden ebenfalls feststellen, dass durch das Verwenden von `<key>` in der URL-Route jede Route dieses Formulars derselben Funktion zugeordnet wird. Außerdem wird ein Argument für die Funktion mit gleichem Namen generiert:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Zum Anzeigen einer Umfrage (GET-Anforderungen) ruft diese Funktion einfach *templates\details.html* ab. Dadurch wird das Array `choices` der Umfrage durchlaufen und ein Optionsfeld für jede Option erstellt.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Da die Schaltfläche **Vote** (Abstimmen) den Typ `type="submit"` aufweist, generiert das Klicken auf diese Schaltfläche eine weitere POST-Anforderung zur gleichen URL, die an die `details`-Funktion weitergeleitet wird. Diesmal wird jedoch die Option aus den Formulardaten extrahiert und an „/results/\<choice\>“ weitergeleitet.

Die URL „/results/\<key\>“ wird dann zur `results`-Funktion in *views.py* weitergeleitet, die anschließend die `calculate_stats`-Methode der Umfrage aufruft und *templates\results.html* für das Rendering verwendet:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

Die Vorlage *results.html* durchläuft die Optionen der Umfrage und generiert eine Statusanzeige für jede:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Nächste Schritte

> [!Note]
> Wenn Sie im Laufe des Tutorials einen Commit der Visual Studio-Projektmappe an die Quellcodeverwaltung ausgeführt haben, ist nun ein guter Zeitpunkt für einen weiteren Commit gekommen. Ihre Projektmappe sollte mit dem Tutorial-Quellcode auf GitHub übereinstimmen: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Sie haben jetzt sämtliche Vorlagen („Leeres Flask-Webprojekt“, „Flask(/Jade) Webprojekt“ und „Fragt ein Flask(/Jade)-Webprojekt ab“) eingehend in Visual Studio kennengelernt. Sie haben die Grundlagen von Flask erlernt, z.B. das Verwenden von Ansichten, Vorlagen und Routing, und wissen nun, wie Sicherungsdatenspeicher verwendet werden. Sie sollten nun damit beginnen können, selbst eine Web-App mit allen Ansichten und Modellen zu erstellen, die Sie benötigen.

Die Ausführung einer Web-App auf Ihrem Entwicklungscomputer ist nur ein Schritt bei der Bereitstellung der App für Ihre Kunden. Die nächsten Schnitte schließen möglicherweise die folgenden Aufgaben ein:

- Stellen Sie die Web-App auf einem Produktionsserver bereit, z.B. Azure App Service. Siehe [Veröffentlichen in Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Fügen Sie eine Repositoryimplementierung hinzu, die einen anderen Datenspeicher auf Produktionsebene verwendet, z.B. MySQL, PostgreSQL und SQL Server (alle können in Azure gehostet werden). Sie können auch die [Azure SDK für Python](/azure/python/) verwenden, um mit Azure-Speicherdiensten wie Tabellen und Blobs sowie mit Cosmos DB zu arbeiten.

- Richten Sie eine CI/CD-Pipeline für einen Dienst wie Azure DevOps ein. Zusätzlich zur Arbeit mit der Quellcodeverwaltung (in Azure Repos, GitHub oder anderweitig) können Sie ein Azure DevOps-Projekt automatisch Ihre Komponententests als Voraussetzung für das Release ausführen lassen und die Pipeline so konfigurieren, dass vor der Bereitstellung in der Produktionsumgebung die Bereitstellung auf dem Stagingserver erfolgt, wodurch weitere Tests ermöglicht werden. Azure DevOps wird zudem in Ihre Überwachungslösungen, wie z.B. App Insights, integriert und schließt den gesamten Zyklus mit agilen Planungstools ab. Weitere Informationen finden Sie unter [Erstellen einer CI/CD-Pipeline für Python mit dem Azure DevOps-Projekt](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) sowie in der allgemeinen [Azure DevOps-Dokumentation](/azure/devops/?view=vsts&preserve-view=true).
