---
title: 'Tutorial zu Django in Visual Studio, Schritt 6: Projektvorlage für Umfragen'
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise erhalten Sie grundlegende Informationen zu Django im Zusammenhang mit Visual Studio-Projekten, insbesondere zu Features der Vorlage „Fragt ein Django-Webprojekt ab“, wie z.B. die administrative Anpassung.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 1f81c665bc742daf7e2b0e34a849aad566362a28
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099335"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Schritt 6: Verwenden der Django-Webprojektvorlage für Umfragen

**Vorheriger Schritt: [Authentifizieren von Benutzern bei Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Nachdem Sie sich erfolgreich mit der Vorlage „Django-Webprojekt“ befasst haben, können Sie nun die dritte Django-Vorlage, „Fragt ein Django-Webprojekt ab“, betrachten, die auf der gleichen Codebasis aufbaut und die Arbeit mit einer Datenbank veranschaulicht.

In diesem Schritt wird Folgendes erläutert:

> [!div class="checklist"]
> - Erstellen eines Projekts von der Vorlage und Initialisieren der Datenbank (Schritt 6-1)
> - Informationen zu Datenmodellen (Schritt 6-2)
> - Anwenden von Migrationen (Schritt 6-3)
> - Informationen zu den Ansichten und Seitenvorlagen, die von der Projektvorlage erstellt wurden (Schritt 6-4)
> - Erstellen einer benutzerdefinierten Verwaltungsschnittstelle (Schritt 6-5)

Ein mit dieser Vorlage erstelltes Projekt ähnelt dem Ergebnis, das Sie erzielen, indem Sie dem Tutorial [Writing your first Django app (Erstellen Ihrer ersten Django-App)](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) in den Django-Dokumenten folgen. Die Web-App besteht aus einer öffentlichen Website, die ermöglicht, Umfragen anzuzeigen und in ihnen abzustimmen, und einer benutzerdefinierte Verwaltungsschnittstelle, über die Sie Umfragen verwalten können. Sie verwendet das gleiche Authentifizierungssystem wie die Vorlage „Django-Webprojekt“ und nutzt zudem die Datenbank durch Implementierung von Django-Modellen, womit sich die folgenden Abschnitte befassen.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Schritt 6.1: Erstellen des Projekts und Initialisieren der Datenbank

1. Wechseln Sie in Visual Studio zum **Projektmappen-Explorer**. Klicken Sie mit der rechten Maustaste auf die Projektmappe **LearningDjango**, die Sie in diesem Tutorial bereits erstellt haben. Klicken Sie anschließend auf **Hinzufügen** > **Neues Projekt**. (Wenn Sie stattdessen eine neue Projektmappe verwenden möchten, klicken Sie auf **Datei** > **Neu** > **Projekt**.)

1. Suchen Sie im Dialogfeld „Neues Projekt“ die Vorlage **Fragt ein Django-Webprojekt ab**, und wählen Sie sie aus. Nennen Sie das Projekt „DjangoPolls“, und klicken Sie auf **OK**.

1. Wie die anderen Projektvorlagen in Visual Studio enthält die Vorlage „Fragt ein Django-Webprojekt ab“ eine Datei namens *requirements.txt*. Eine Visual Studio-Eingabeaufforderung fragt ab, wohin diese Abhängigkeiten installiert werden sollen. Wählen Sie die Option **In einer virtuellen Umgebung installieren** aus. Klicken Sie im Dialogfeld **Virtuelle Umgebung hinzufügen** auf **Erstellen**, um die Standardwerte zu übernehmen.

1. Sobald das Einrichten der virtuellen Umgebung durch Python beendet wurde, befolgen Sie die Anweisungen im angezeigten *readme.html*, um die Datenbank zu initialisieren und einen Django-Administrator zu erstellen. Klicken Sie zunächst mit der rechten Maustaste auf das Projekt **DjangoPolls** im **Projektmappen-Explorer**, und wählen Sie den Befehl **Python** > **Django migrieren** aus. Klicken Sie anschließend mit der rechten Maustaste erneut auf das Projekt, wählen Sie den Befehl **Python** > **Django-Administrator erstellen** aus, und folgen Sie den Eingabeaufforderungen. (Wenn Sie versuchen, zuerst einen Administrator zu erstellen, wird eine Fehlermeldung angezeigt, da die Datenbank noch nicht initialisiert wurde.)

1. Legen Sie das Projekt **DjangoPolls** als Standardprojekt für die Visual Studio-Projektmappe fest. Klicken Sie hierzu mit der rechten Maustaste im **Projektmappen-Explorer** auf das Projekt, und wählen Sie die Option **Set as Startup Project** (Als Startprojekt festlegen) aus. Das fett angezeigte Startprojekt wird ausgeführt, wenn Sie den Debugger starten.

1. Wählen Sie zum Ausführen des Servers **Debuggen** > **Debuggen starten** (**F5**) aus, oder verwenden Sie hierzu die Schaltfläche **Webserver** auf der Symbolleiste:

    ![Symbolleisten-Schaltfläche „Webserver ausführen“ in Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Die von der Vorlage erstellte App verfügt über drei Seiten: „Startseite“, „Info“ und „Kontakt“. Sie können über die obere Navigationsleiste zwischen diesen Seiten navigieren. Nehmen Sie sich ein paar Minuten Zeit, um die unterschiedlichen Teile der App zu untersuchen (die Seiten „Info“ und „Kontakt“ sind „Django-Webprojekt“ sehr ähnlich und werden nicht weiter besprochen).

    ![Vollständige Browseransicht der App „Fragt ein Django-Webprojekt ab“](media/django/step06-full-app-view.png)

1. Wählen Sie auch den Link **Verwaltung** in der Navigationsleiste aus, um einen Anmeldebildschirm einzublenden und zu zeigen, dass nur authentifizierte Benutzer die Berechtigung für die Verwaltungsschnittstelle haben. Verwenden Sie die Administrator-Anmeldeinformationen. Sie werden zur Seite „/admin“ weitergeleitet, die standardmäßig aktiviert ist, wenn diese Projektvorlage verwendet wird.

    ![Verwaltungsansicht der App „Fragt ein Django-Webprojekt ab“](media/django/step06-polls-administrative-interface.png)

1. Für die folgenden Abschnitte kann die App weiterhin ausgeführt werden.

    Wenn Sie die App beenden und [ein Commit der Änderungen für die Quellcodeverwaltung ausführen möchten](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), öffnen Sie zunächst im **Team Explorer** die Seite **Änderungen**. Klicken Sie mit der rechten Maustaste auf den Ordner für die virtuelle Umgebung (vermutlich **env**), und wählen Sie die Option **Diese lokalen Elemente ignorieren** aus.

### <a name="examine-the-project-contents"></a>Überprüfen des Projektinhalts

Wie bereits erwähnt. Viele Bestandteile eines auf der Grundlage der Vorlage „Fragt ein Django-Webprojekt ab“ erstellten Projekts sollten bekannt sein, sofern Sie die anderen Projektvorlagen in Visual Studio untersucht haben. Die zusätzlichen Schritte in diesem Artikel fassen die wichtigeren Änderungen und Hinzufügungen zusammen: Datenmodelle und zusätzliche Ansichten.

### <a name="question-what-does-the-django-migrate-command-do"></a>Frage: Was bewirkt der Befehl „Django migrieren“?

Antwort: Der Befehl **Django migrieren** führt den Befehl `manage.py migrate` aus, der alle Skripts im Ordner *app/migrations* ausführt, die zuvor noch nicht ausgeführt wurden. In diesem Fall führt der Befehl das Skript *0001_initial.py* in diesem Ordner aus, um das erforderliche Schema in der Datenbank einzurichten.

Das Migrationsskript selbst wird vom Befehl `manage.py makemigrations` erstellt, der die Datei *models.py* der App scannt, diese mit dem aktuellen Status der Datenbank vergleicht und dann die notwendigen Skripts generiert, um das Datenbankschema entsprechend den aktuellen Modellen zu migrieren. Dieses Feature von Django ist sehr leistungsstark, da Sie Ihre Modelle im Laufe der Zeit aktualisieren und ändern. Durch Generieren und Ausführen von Migrationen bleiben die Modelle und die Datenbank mit wenig Aufwand stets synchronisiert.

Sie arbeiten mit einer Migration in Schritt 6-3 weiter unten in diesem Artikel.

## <a name="step-6-2-understand-data-models"></a>Schritt 6.2: Informationen zu Datenmodellen

Die Modelle für die App mit den Namen „Poll“ (Umfrage) und „Choice“ (Auswahl) werden in *app/models.py* definiert. Jedes Modell ist eine Python-Klasse, die von `django.db.models.Model` abgeleitet wird und Methoden der `models`-Klasse verwendet, z.B. `CharField` und `IntegerField`, um Felder im Modell zu definieren, die Datenbankspalten zugeordnet sind.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Wie Sie sehen, hat eine „Umfrage“ eine Beschreibung im Feld `text` und ein Veröffentlichungsdatum in `pub_date`. Diese Felder sind die einzigen, die für die Umfrage in der Datenbank vorhanden sind; das Feld `total_votes` wird zur Laufzeit berechnet.

„Auswahl“ bezieht sich auf eine „Umfrage“ über das Feld `poll`, enthält eine Beschreibung in `text` und verwaltet einen Zähler für diese Auswahl in `votes`. Das Feld `votes_percentage` wird zur Laufzeit berechnet und wird in der Datenbank nicht gefunden.

Die vollständige Liste der Feldtypen ist `CharField` (begrenzter Text) `TextField` (unbegrenzter Text), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey` und `ManyToMany`. Jedes Feld hat einige Attribute, wie z.B. `max_length`. Das Attribut `blank=True` bedeutet, dass das Feld optional ist. `null=true` bedeutet, dass ein Wert optional ist. Es gibt auch ein Attribut `choices`, das die Werte auf Werte in einem Array von Datenwert/Anzeigewert-Tupeln beschränkt. (Weitere Informationen finden Sie unter [Model field reference (Modellfeldverweis)](https://docs.djangoproject.com/en/2.0/ref/models/fields/) in der Django-Dokumentation.)

Sie können genau bestätigen, was in der Datenbank gespeichert wird, indem Sie die Datei *db.sqlite3* im Projekt mithilfe eines Tools wie dem [SQLite-Browser](https://sqlitebrowser.org/) untersuchen. In der Datenbank sehen Sie, dass ein Fremdschlüsselfeld wie `poll` im Auswahlmodell als `poll_id` gespeichert ist. Django verarbeitet die Zuordnung automatisch.

Wenn Sie mit Ihrer Datenbank in Django arbeiten, bedeutet dies normalerweise, dass Sie ausschließlich über Ihre Modelle arbeiten, sodass Django die zugrunde liegende Datenbank in Ihrem Namen verwalten kann.

### <a name="seed-the-database-from-samplesjson"></a>Ausführen eines Seedings für die Datenbank von samples.json

Die Datenbank enthält anfänglich keine Umfragen. Sie können die Verwaltungsschnittstelle an der „/admin“-URL verwenden, um Umfragen manuell hinzuzufügen, und Sie können zudem die „/seed“-Seite auf der ausführenden Website besuchen, um der Datenbank in der Datei *samples.json* der App definierte Umfragen per Seeding hinzuzufügen.

Die Datei *urls.py* des Django-Projekts verfügt über ein zusätzliches URL-Muster: `url(r'^seed$', app.views.seed, name='seed'),`. Die Ansicht `seed` in *app/views.py* lädt die Datei *samples.json* und erstellt die erforderlichen Modellobjekte. Django erstellt dann automatisch die übereinstimmenden Datensätze in der zugrunde liegenden Datenbank.

Beachten Sie die Verwendung des Decorator-Elements `@login_required`, um die Berechtigungsebene für die Ansicht anzugeben.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Um die Auswirkungen anzuzeigen, führen Sie zuerst die App aus, um sich davon zu überzeugen, dass noch keine App vorhanden ist. Besuchen Sie dann die „/seed“-URL. Wenn die App zur Startseite zurückkehrt, sollten Sie feststellen, dass die Umfragen nun verfügbar sind. Sie können hier die unformatierte Datei *db.sqlite3* mit einem Tool wie dem [SQLite-Browser](https://sqlitebrowser.org/) untersuchen.

![App „Fragt ein Django-Webprojekt ab“ mit einer per Seeding hinzugefügten Datenbank](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Frage: Ist es möglich, die Datenbank mithilfe des Django-Verwaltungsprogramms zu initialisieren?

Antwort: Ja, Sie können den Befehl [django-admin-loaddata](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) verwenden, um die gleiche Aufgabe durchzuführen wie die Seeding-Seite in der App. Wenn Sie mit einer vollständigen Web-App arbeiten, verwenden Sie möglicherweise eine Kombination der beiden Methoden: Sie initialisieren eine Datenbank über die Befehlszeile und wandeln dann die Seed-Seite hier in eine API um, der Sie jedes andere beliebige JSON-Objekt senden können, anstatt sich auf eine hartcodierte Datei zu stützen.

## <a name="step-6-3-use-migrations"></a>Schritt 6.3: Verwenden von Migrationen

Wenn Sie den Befehl `manage.py makemigrations` (über das Kontextmenü in Visual Studio) ausgeführt haben, nachdem Sie das Projekt erstellt haben, hat Django die Datei *app/migrations/0001_initial.py* erstellt. Diese Datei enthält ein Skript, das die ursprünglichen Datenbanktabellen erstellt.

Da Sie zwangsläufig die Modelle mit der Zeit ändern müssen, erleichtert Django die Aufgabe, das zugrunde liegende Datenbankschema mit diesen Modellen auf dem neuesten Stand zu halten. Der allgemeine Workflow stellt sich wie folgt dar:

1. Nehmen Sie Änderungen an den Modellen in der Datei *models.py* vor.
1. Klicken Sie mit der rechten Maustaste in Visual Studio auf den **Projektmappen-Editor**, und wählen Sie den Befehl **Python** > **Django Make Migrations** (Django-Migrationen durchführen) aus. Wie zuvor beschrieben, generiert dieser Befehl Skripts in *app/migrations* zum Migrieren der Datenbank vom aktuellen Zustand in den neuen Zustand.
1. Klicken Sie zum Anwenden der Skripts auf die aktuelle Datenbank mit der rechten Maustaste erneut auf das Projekt, und wählen Sie **Python** > **Django migrieren** aus.

Django verfolgt, welche Migration auf eine bestimmte Datenbank angewendet wurde, sodass Django genau die Migration anwendet, die benötigt wird, wenn Sie den Migrationsbefehl ausführen. Wenn Sie eine neue, leere Datenbank erstellen, wird diese bei Ausführung des Migrationsbefehls auf den Stand der aktuellen Modelle gebracht, indem die einzelnen Migrationsskripts angewendet werden. Auch wenn Sie mehrere Modelländerungen vornehmen und Migrationen auf einem Entwicklungscomputer generieren, können Sie die kumulierten Migrationen auf Ihre Produktionsdatenbank anwenden, indem Sie den Migrationsbefehl auf dem Produktionsserver ausführen. Django wendet erneut nur die Migrationsskripts an, die seit der letzten Migration der Produktionsdatenbank generiert wurden.

Um die Auswirkungen der Änderung eines Modells anzuzeigen, führen Sie die folgenden Schritte aus:

1. Fügen Sie dem Umfragemodell ein optionales Autorenfeld in *app/models.py* hinzu, indem Sie die folgende Zeile nach dem Feld `pub_date` einfügen, um ein optionales Feld `author` hinzuzufügen:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Speichern Sie die Datei, klicken Sie mit der rechten Maustaste auf das Projekt **DjangoPolls** im **Projektmappen-Explorer**, und wählen Sie den Befehl **Python** > **Django Make Migrations** (Django-Migrationen durchführen) aus.
1. Wählen Sie den Befehl **Projekt** > **Alle Dateien anzeigen** aus, um das neu generierte Skript in dem **Migrations**-Ordner zu sehen, dessen Name mit **002_auto_** beginnt. Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Zu Projekt hinzufügen** aus. Sie können dann **Projekt** > **Alle Dateien anzeigen** erneut auswählen, um die ursprüngliche Ansicht wiederherzustellen. (Details zu diesem Schritt finden Sie unter der zweiten Frage weiter unten.)
1. Falls gewünscht, öffnen Sie diese Datei, die beschreibt, wie Django mit Skripts die Änderung vom vorherigen Modellzustand in den neuen Zustand durchführt.
1. Klicken Sie zum Anwenden der Änderungen auf die Datenbank erneut mit der rechten Maustaste auf das Visual Studio-Projekt, und wählen Sie **Python** > **Django migrieren** aus.
1. Falls gewünscht, öffnen Sie die Datenbank in einem geeigneten Viewer, um die Änderung zu bestätigen.

Das Migrationsfeature von Django bedeutet auch, dass Sie Ihr Datenbankschema niemals manuell verwalten müssen. Nehmen Sie nur Änderungen an den Modellen vor, generieren Sie die Migrationsskripts, und wenden Sie diese dann mit dem Migrationsbefehl an.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Frage: Was geschieht, wenn ich vergesse, den Migrationsbefehl auszuführen, nachdem ich Änderungen an Modellen vorgenommen habe?

Antwort: Wenn die Modelle nicht mit dem Inhalt der Datenbank übereinstimmen, schlägt Django zur Laufzeit mit den entsprechenden Ausnahmen fehl. Wenn Sie vergessen, die im vorherigen Abschnitt gezeigte Modelländerung zu migrieren, wird der Fehler **no such column: app_poll.author** (keine solche Spalte: app_poll.author) angezeigt:

![Fehler, der angezeigt wird, wenn eine Modelländerung nicht migriert wurde](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Frage: Weshalb zeigt der Projektmappen-Explorer neu generierte Skripts nicht an, nachdem der Befehl zur Durchführung von Django-Migrationen (Django Make Migrations) ausgeführt wurde?

Antwort: Obwohl neu generierte Skripts im Ordner *app/migrations* vorhanden sind und angewendet werden, wenn der Befehl **Django migrieren** ausgeführt wird, werden sie nicht automatisch im **Projektmappen-Explorer** angezeigt, da sie nicht dem Visual Studio-Projekt hinzugefügt wurden. Um sie einzublenden, wählen Sie zuerst den Menübefehl **Projekt** > **Alle Dateien anzeigen** oder die Symbolleisten-Schaltfläche aus, die in der folgenden Abbildung beschrieben ist. Dieser Befehl bewirkt, dass der **Projektmappen-Explorer** alle Dateien im Projektordner mit einem gepunkteten Umriss für Elemente anzeigt, die dem Projekt selbst nicht hinzugefügt wurden. Klicken Sie mit der rechten Maustaste auf die Dateien, die Sie hinzufügen möchten, und wählen Sie **Zu Projekt hinzufügen** aus. Dadurch werden Sie auch beim nächsten Commit in die Quellcodeverwaltung eingeschlossen.

![Befehl „Zu Projekt hinzufügen“ im Projektmappen-Explorer](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Frage: Kann ich sehen, welche Migrationen angewendet werden, bevor ich den Migrationsbefehl ausführe?

Antwort: Ja, verwenden Sie den Befehl [django admin showmigrations](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Schritt 6.4: Grundlegendes zu den Ansichten und Seitenvorlagen, die von der Projektvorlage erstellt wurden

Die meisten der von der Vorlage „Fragt ein Django-Webprojekt ab“ generierten Ansichten, z.B. die Ansichten für die Seiten „Info“ und „Kontakt“, sind den von der Vorlage „Django-Webprojekt“ erstellten Ansichten sehr ähnlich, mit denen Sie am Anfang des Tutorials gearbeitet haben. Die Umfrage-App unterscheidet sich dadurch, dass ihre Startseite, wie auch mehrere hinzugefügte Seiten zum Abstimmen und Anzeigen von Umfrageergebnissen, Modelle verwendet.

Zunächst sollte erwähnt werden, dass die erste Zeile im `urlpatterns`-Array in der Datei *urls.py* des Django-Projekts mehr als nur eine einfache Weiterleitung an eine App-Ansicht ist. Vielmehr führt sie einen Pull in der Datei *urls.py* der App aus:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Die Datei *app/urls.py* enthält dann noch interessanteren Routingcode (erläuternde Kommentare hinzugefügt):

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Wenn Sie nicht mit den komplexeren regulären Ausdrücken vertraut sind, die hier verwendet werden, können Sie den Ausdruck in die Datei [regex101.com](https://regex101.com/) einfügen, um eine Erklärung in natürlicher Sprache zu erhalten. (Sie müssen die Schrägstriche `/` mit Escapezeichen versehen, indem Sie einen vorgestellten umgekehrten Schrägstrich `\` hinzufügen. Escapezeichen sind in Python aufgrund des Präfix `r` für die Zeichenfolge, das „unformatiert“ bedeutet, nicht erforderlich.)

In Django erstellt die Syntax `?P<name>pattern` eine Gruppe namens `name`, die als Argumente in der Reihenfolge an Ansichten weitergegeben wird, in der diese angezeigt werden. In dem zuvor gezeigten Code erhalten `PollsDetailView` und `PollsResultsView` ein Argument mit dem Namen `pk`, und `app.views.vote` erhält ein Argument mit dem Namen `poll_id`.

Sie können auch sehen, dass die meisten Ansichten nicht nur direkte Verweise auf eine Ansichtsfunktion in *app/views.py* sind. Stattdessen verweisen die meisten auf eine Klasse in der gleichen Datei, die von `django.views.generic.ListView` oder `django.views.generic.DetailView` abgeleitet wird. Die Basisklasse bietet die `as_view`-Methoden, die ein `template_name`-Argument erhalten, um die Vorlage zu identifizieren. Die Basisklasse `ListView`, die für die Startseite verwendet wird, erwartet auch eine `queryset`-Eigenschaft, die die Daten enthält, und eine `context_object_name`-Eigenschaft mit dem Variablennamen, über den Sie auf die Daten in der Vorlage verweisen können, in diesem Fall `latest_poll_list`.

Sie können nun die `PollListView` auf der Startseite untersuchen, die wie folgt in *app/views.py* definiert ist:

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Hier wird lediglich das Modell identifiziert, mit dem die Ansicht arbeitet (Umfrage), und die `get_context_data`-Methode wird überschrieben, um die Werte `title` und `year` dem Kontext hinzuzufügen.

Der Kern der Vorlage (*templates/app/index.html*) gestaltet sich folgendermaßen:

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

Einfach ausgedrückt, die Vorlage empfängt die Liste der Umfrageobjekte in `latest_poll_list` und durchläuft dann die Liste, um unter Verwendung des `text`-Werts der Umfrage eine Tabellenzeile zu erstellen, die einen Link zu jeder Umfrage enthält. Im `{% url %}`-Tag verweist „App:detail“ auf das URL-Muster in *app/urls.py* mit dem Namen „detail“, wobei `poll.id` als Argument verwendet wird. Django erstellt dann eine URL mit dem entsprechenden Muster und verwendet dieses für den Link. Dieser Teil einer Zukunftstrategie bedeutet, dass Sie das URL-Muster jederzeit ändern können und die generierten Links automatisch entsprechend aktualisiert werden.

Die Klassen `PollDetailView` und `PollResultsView` in der Datei *app/views.py* (hier nicht dargestellt) sind optisch fast identisch mit `PollListView`, leiten stattdessen aber von `DetailView` ab. Ihre zugehörigen Vorlagen *app/templates/details.html* und *app/templates/results.html* platzieren anschließend die entsprechenden Felder aus den Modellen in verschiedene HTML-Steuerelemente. Einmalig in *details.html* ist, dass die Auswahlmöglichkeiten für eine Umfrage in einem HTML-Formular enthalten sind, das nach der Übermittlung einen POST an die /vote-URL absetzt. Wie weiter oben zu sehen war, wird dieses URL-Muster an `app.views.vote` weitergeleitet, was wie folgt implementiert ist (beachten Sie das Argument `poll_id`, das wieder eine benannte Gruppe im regulären Ausdruck ist, der für die Weiterleitung für diese Ansicht verwendet wird):

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

Die Ansicht hat hier – anders als die anderen Seiten – keine eigene entsprechende Vorlage. Stattdessen wird die ausgewählte Umfrage validiert, und ein 404-Fehler wird angezeigt, wenn die Umfrage nicht vorhanden ist (für den Fall, dass jemand eine URL wie „vote/1a2b3c“ eingibt). Anschließend wird sichergestellt, dass die Auswahlmöglichkeit, für die gestimmt wurde, für die Umfrage gültig ist. Wenn dies nicht der Fall, rendert der `except`-Block lediglich erneut die Detailseite mit einer Fehlermeldung. Wenn die Auswahl gültig ist, zählt die Ansicht die Stimmen und leitet an die Seite „Ergebnisse“ weiter.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Schritt 6.5: Erstellen einer benutzerdefinierten Verwaltungsschnittstelle

Die letzten Bestandteile der Vorlage „Fragt ein Django-Webprojekt ab“ sind benutzerdefinierte Erweiterungen der standardmäßigen Django-Verwaltungsschnittstelle, wie bereits am Anfang dieses Artikels in Schritt 6-1 gezeigt. Die Standardschnittstelle sieht lediglich eine Benutzer- und Gruppenverwaltung vor. Die Umfrageprojektvorlage fügt Features hinzu, die Ihnen ermöglichen, auch die Umfragen zu verwalten.

Zunächst einmal ist `url(r'^admin/', include(admin.site.urls)),` standardmäßig in den URL-Mustern in der Datei *urls.py* des Django-Projekts enthalten. Das Muster „admin/doc“ ist ebenfalls enthalten, aber auskommentiert.

Die App enthält außerdem die Datei *admin.py*, die von Django automatisch ausgeführt wird, wenn Sie die Verwaltungsschnittstelle besuchen. Ermöglicht wird dies durch die Berücksichtigung von `django.contrib.admin` im `INSTALLED_APPS`-Array von *settings.py*. Der Code in dieser Datei, der von der Projektvorlage bereitgestellt wird, lautet wie folgt:

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Wie Sie sehen können, leitet die Klasse `PollAdmin` von `django.contrib.admin.ModelAdmin` ab und passt eine Anzahl ihrer Felder unter Verwendung von Namen des von ihr verwalteten Modells `Poll` an. Diese Felder werden in den [ModelAdmin-Optionen](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) in der Django-Dokumentation beschrieben.

Der Aufruf von `admin.site.register` verbindet dann diese Klasse mit dem Modell (`Poll`) und schließt es in der Admin-Schnittstelle ein. Das Gesamtergebnis wird unten dargestellt:

![Verwaltungsansicht der App „Fragt ein Django-Webprojekt ab“](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Nächste Schritte

> [!Note]
> Wenn Sie im Laufe des Tutorials einen Commit der Visual Studio-Projektmappe an die Quellcodeverwaltung ausgeführt haben, ist nun ein guter Zeitpunkt für einen weiteren Commit gekommen. Ihre Lösung sollte mit dem Tutorialquellcode auf GitHub übereinstimmen: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Sie haben jetzt sämtliche Vorlagen, „Leeres Django-Webprojekt“, „Django Webprojekt“ und „Fragt Django-Webprojekt ab“, eingehend in Visual Studio untersucht. Sie haben alle Grundlagen von Django kennen gelernt, z.B. die Verwendung von Ansichten und Vorlagen, und haben sich mit der Weiterleitung, Authentifizierung und Verwendung von Datenbankmodellen näher beschäftigt. Sie sollten nun in der Lage sein, selbst eine Web-App mit allen Ansichten und Modellen zu erstellen, die Sie benötigen.

Die Ausführung einer Web-App auf Ihrem Entwicklungscomputer ist nur ein Schritt bei der Bereitstellung der App für Ihre Kunden. Die nächsten Schnitte schließen möglicherweise die folgenden Aufgaben ein:

- Stellen Sie die Web-App auf einem Produktionsserver bereit, z.B. Azure App Service. Siehe [Veröffentlichen in Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Anpassen der Seite „404“ durch Erstellen einer Vorlage mit dem Namen *templates/404.html*. Wenn vorhanden, verwendet Django diese Vorlage anstelle der standardmäßigen. Weitere Informationen finden Sie unter [Error views (Fehler-Ansichten)](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) in der Django-Dokumentation.

- Schreiben von Komponententests in *tests.py*. Die Visual Studio-Projektvorlagen bieten Ausgangspunkte für diese. Weitere Informationen finden Sie in [Writing your first Django app, part 5 - testing (Erstellen Ihrer ersten Django-App, Teil 5 – Testen)](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) und [Testing in Django (Testen in Django)](https://docs.djangoproject.com/en/2.0/topics/testing/) in der Django-Dokumentation.

- Ändern Sie die App von SQLite in einen Datenspeicher auf Produktionsebene, wie z.B. MySQL, PostgreSQL und SQL Server (können alle in Azure gehostet werden). Wie in [When to use SQLite (Empfohlene Verwendung von SQLite)](https://www.sqlite.org/whentouse.html) (sqlite.org) beschrieben, ist SQLite hervorragend für Standorte mit niedrigem bis mittleren Verkehrsaufkommen und weniger als 100.000 Treffern/Tag geeignet, wird aber bei einem höheren Verkehrsaufkommen nicht empfohlen. Da SQLite zudem auf einen einzelnen Computer beschränkt ist, kann es nicht in jedem Szenario mit mehreren Servern, z.B. Lastenausgleich und geografische Replikation, verwendet werden. Informationen über die Unterstützung von Django für andere Datenbanken finden Sie unter [Database setup (Datenbankeinrichtung)](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Sie können auch die [Azure SDK für Python](/azure/python/) verwenden, um mit Azure-Speicherdiensten wie Tabellen und Blobs zu arbeiten.

- Richten Sie eine CI/CD-Pipeline für einen Dienst wie Azure DevOps ein. Zusätzlich zur Arbeit mit der Quellcodeverwaltung (in Azure Repos, GitHub oder anderweitig) können Sie ein Azure DevOps-Projekt automatisch Ihre Komponententests als Voraussetzung für das Release ausführen lassen und die Pipeline so konfigurieren, dass vor der Bereitstellung in der Produktionsumgebung die Bereitstellung auf dem Stagingserver erfolgt, wodurch weitere Tests ermöglicht werden. Azure DevOps wird zudem in Ihre Überwachungslösungen, wie z.B. App Insights, integriert und schließt den gesamten Zyklus mit agilen Planungstools ab. Weitere Informationen finden Sie unter [Erstellen einer CI/CD-Pipeline für Python mit dem Azure DevOps-Projekt](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) sowie in der allgemeinen [Azure DevOps-Dokumentation](/azure/devops/?view=vsts&preserve-view=true).
