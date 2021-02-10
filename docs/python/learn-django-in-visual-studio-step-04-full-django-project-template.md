---
title: 'Tutorial zu Django in Visual Studio, Schritt 4: Webprojektvorlage'
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise erhalten Sie grundlegende Informationen zu Django im Zusammenhang mit Visual Studio-Projekten, insbesondere zu Features, die durch die Vorlage „Django-Webprojekt“ bereitgestellt werden.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3c0a0f0f4e009d689a69e840b31281e65bc5a0e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942554"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Schritt 4: Verwenden der vollständigen Vorlage „Django-Webprojekt“

**Vorheriger Schritt: [Serve static files, add pages, and use template inheritance (Bereitstellen statischer Dateien, Hinzufügen von Seiten und Verwenden von Vorlagenvererbung)](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Nachdem Sie sich mit den grundlegenden Funktionen von Django vertraut gemacht und eine App auf Grundlage der Vorlage „Leeres Django-Webprojekt“ in Visual Studio erstellt haben, erhalten Sie nun weitere Informationen zu umfangreicheren Funktionen der App über die Vorlage „Django-Webprojekt“.

In diesem Schritt werden Sie Informationen zu folgenden Inhalten erhalten:

> [!div class="checklist"]
> - Erstellen einer umfangreicheren Django-Web-App mithilfe der Vorlage „Django-Webprojekt“ und Informationen zur Projektstruktur (Schritt 4-1).
> - Informationen zu Ansichten und Seitenvorlagen, die mit der dreiseitigen Projektvorlage erstellt wurden. Diese Seiten erben von einer Vorlage für die Basisseite und verwenden statische JavaScript-Bibliotheken wie etwa jQuery und Bootstrap (Schritt 4-2).
> - Informationen zum URL-Routing, das von der Vorlage bereitgestellt wird (Schritt 4-3).

Durch die Vorlage wird auch eine Standardauthentifizierung bereitgestellt, die in Schritt 5 beschrieben wird.

## <a name="step-4-1-create-a-project-from-the-template"></a>Schritt 4-1: Erstellen eines Projekts aus der Vorlage

1. Wechseln Sie in Visual Studio zum **Projektmappen-Explorer**. Klicken Sie mit der rechten Maustaste auf die Projektmappe **LearningDjango**, die Sie in diesem Tutorial bereits erstellt haben. Klicken Sie anschließend auf **Hinzufügen** > **Neues Projekt**. (Wenn Sie stattdessen eine neue Projektmappe verwenden möchten, klicken Sie auf **Datei** > **Neu** > **Projekt**.)

1. Suchen Sie im Dialogfeld „Neues Projekt“ nach der Vorlage **Django-Webprojekt**, und wählen Sie sie aus. Nennen Sie das Projekt „DjangoWeb“, und klicken Sie auf **OK**.

1. Da die Vorlage erneut eine *requirements.txt*-Datei enthält, werden Sie von Visual Studio gefragt, wohin die Abhängigkeiten installiert werden sollen. Wählen Sie die Option **In einer virtuellen Umgebung installieren** aus. Klicken Sie im Dialogfeld **Virtuelle Umgebung hinzufügen** auf **Erstellen**, um die Standardwerte zu übernehmen.

1. Sobald das Einrichten der virtuellen Umgebung durch Visual Studio beendet wurde, befolgen Sie die Anweisungen im angezeigten *readme.html*, um einen Django-Administrator zu erstellen. Klicken Sie dazu mit der rechten Maustaste auf das Visual Studio-Projekt, wählen Sie den Befehl **Python** > **Django-Administrator erstellen** aus, und befolgen Sie die Anweisungen. Stellen Sie sicher, dass Sie Ihren Benutzernamen und das Kennwort für die Nutzung der Authentifizierungsfeatures der App sicher aufbewahren.

1. Legen Sie das Projekt **DjangoWeb** als Standardprojekt für die Visual Studio-Projektmappe fest. Klicken Sie hierzu mit der rechten Maustaste im **Projektmappen-Explorer** auf das Projekt, und wählen Sie die Option **Als Startprojekt festlegen** aus. Das fett angezeigte Startprojekt wird ausgeführt, wenn Sie den Debugger starten.

    ![Projektmappen-Explorer mit dem Projekt „DjangoWeb“ als Startprojekt](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Wählen Sie zum Ausführen des Servers **Debuggen** > **Debuggen starten** (**F5**) aus, oder verwenden Sie hierzu die Schaltfläche **Webserver** auf der Symbolleiste:

    ![Symbolleisten-Schaltfläche „Webserver ausführen“ in Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Die von der Vorlage erstellte App verfügt über drei Seiten: „Startseite“, „Info“ und „Kontakt“. Über die Navigationsleiste können Sie zwischen diesen Seiten navigieren. Nehmen Sie sich etwas Zeit, um sich mit den verschiedenen Teilen der App vertraut zu machen. Verwenden Sie für die Authentifizierung bei der App über den **Anmelden**-Befehl die Administratoranmeldeinformationen, die Sie zuvor erstellt haben.

    ![Vollständige Browseransicht der App „Django-Webprojekt“](media/django/step04-full-app-desktop-view.png)

1. Die von der Vorlage „Django-Webprojekt“ erstellte App verwendet Bootstrap für ein dynamisches Layout, das sich den Formfaktoren tragbarer Geräte anpasst. Ändern Sie die Größe des Browserfensters in eine schmale Ansicht, wenn Sie das dynamische Layout testen möchten. Dadurch wird der Inhalt vertikal gerendert, und die Navigationsleiste wird zu einem Menüsymbol:

    ![Mobile (schmale) Ansicht der App „Django-Webprojekt“](media/django/step04-full-app-mobile-view.png)

1. Für die folgenden Abschnitte kann die App weiterhin ausgeführt werden.

    Wenn Sie die App beenden und [ein Commit der Änderungen für die Quellcodeverwaltung ausführen möchten](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), öffnen Sie zunächst im **Team Explorer** die Seite **Änderungen**. Klicken Sie mit der rechten Maustaste auf den Ordner für die virtuelle Umgebung (vermutlich **env**), und wählen Sie die Option **Diese lokalen Elemente ignorieren** aus.

### <a name="examine-what-the-template-creates"></a>Überprüfen des von der Vorlage erstellten Ergebnisses

Die Vorlage „Django-Webprojekt“ erstellt weitestgehend die folgende Struktur:

- Dateien im Projektstamm:
  - *manage.py*: Das Django-Verwaltungsprogramm.
  - *db.sqlite3*: Eine SQLite-Standarddatenbank.
  - *requirements.txt*: Enthält eine Abhängigkeit von Django 1.x.
  - *readme.html*: Eine Datei, die nach dem Erstellen des Projekts in Visual Studio angezeigt wird. Befolgen Sie wie im vorherigen Abschnitt erwähnt die Anweisungen zum Erstellen eines Administratorkontos für die App.
- Der *App*-Ordner enthält alle App-Dateien, einschließlich Ansichten, Modellen, Tests, Formularen, Vorlagen und statischen Dateien (siehe Schritt 4-2). In der Regel sollte dieser Ordner umbenannt werden, damit er einen aussagekräftigeren App-Namen erhält.
- Der Ordner *DjangoWeb* (Django-Projekt) enthält die typischen Projektdateien eines Django-Projekts: *\_\_init\_\_.py*, *settings.py*, *urls.py* und *wsgi.py*. Durch die Verwendung der Projektvorlage ist *settings.py* bereits für die App und die Datenbankdatei konfiguriert. Zudem ist *urls.py* bereits mit Routen zu allen App-Seiten, einschließlich des Anmeldeformulars, konfiguriert.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Frage: Ist es möglich, eine virtuelle Umgebung für andere Visual Studio-Projekte freizugeben?

Antwort: Ja. Doch bedenken Sie dabei, dass unterschiedliche Projekte im Laufe der Zeit wahrscheinlich unterschiedliche Pakete verwenden werden und eine gemeinsam genutzte virtuelle Umgebung daher alle Pakete für sämtliche Projekte enthalten muss, von denen sie verwendet wird.

Wenn Sie dennoch eine vorhandene virtuelle Umgebung verwenden möchten, führen Sie die folgenden Schritte aus:

1. Wenn Sie aufgefordert werden, Abhängigkeiten in Visual Studio zu installieren, wählen Sie die Option **Ich führe die Installation selbst durch** aus.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Python-Umgebungen**, und wählen Sie die Option **Vorhandene virtuelle Umgebung hinzufügen** aus.
1. Navigieren Sie zum Ordner mit der virtuellen Umgebung, wählen Sie ihn aus, und klicken Sie anschließend auf **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Schritt 4-2: Informationen zu den Ansichten und Seitenvorlagen, die von der Projektvorlage erstellt wurden

Wie Sie beim Ausführen des Projekts festgestellt haben, verfügt die App über drei Ansichten: „Startseite“, „Info“ und „Kontakt“. Der Code für diese Ansichten befindet sich im Ordner *app/views*. Jede Ansichtsfunktion ruft `django.shortcuts.render` mit dem Pfad zu einer Vorlage und einem einfachen Wörterbuchobjekt auf. Die Seite „Info“ wird beispielsweise von der `about`-Funktion behandelt:

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

Vorlagen befinden sich im Ordner *templates/app* der App (*app* sollte dabei in der Regel in den Namen der tatsächlichen App umbenannt werden). Die Basisvorlage *layout.html* ist am umfangreichsten. Sie verweist auf alle erforderlichen statischen Dateien (JavaScript und CSS), definiert einen Block namens „content“, der von anderen Seiten überschrieben wird, und stellt einen weiteren Block namens „scripts“ bereit. In den folgenden kommentierten Auszügen aus *layout.html* werden diese bestimmten Bereiche veranschaulicht:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

Die einzelnen Seitenvorlagen *about.html*, *contact.html* und *index.html* erweitern alle die Basisvorlage *layout.html*. *about.html* ist die einfachste Vorlage. Sie enthält die Tags `{% extends %}` und `{% block content %}`:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* und *contact.html* verwenden die gleiche Struktur. Außerdem ist ihr Inhalt im Block „content“ umfangreicher.

Im Ordner *templates/app* befindet sich ebenso eine vierte Seite, *login.html* zusammen mit *loginpartial.html*, die über `{% include %}` in *layout.html* verschoben wird. Diese Vorlagendateien werden bei der Authentifizierung in Schritt 5 näher erläutert.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Frage: Können {% block %} und {% endblock %} in der Django-Seitenvorlage eingerückt werden?

Antwort: Ja. Django-Seitenvorlagen funktionieren problemlos mit eingerückten Blocktags, etwa zur Ausrichtung im entsprechenden übergeordneten Element. In den Seitenvorlagen, die von der Visual Studio-Projektvorlage erstellt wurden, werden die Blocktags nicht eingerückt, damit ihre Position deutlich zu erkennen ist.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Schritt 4-3: Informationen zum URL-Routing, das von der Vorlage erstellt wurde

Die Datei *urls.py* des Django-Projekts, die von der Vorlage „Django-Webprojekt“ erstellt wurde, enthält den folgenden Code:

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

Die ersten drei URL-Muster werden direkt den Ansichten `home`, `contact` und `about` in der Datei *views.py* der App zugeordnet. Die Muster `^login/$` und `^logout$` verwenden hingegen integrierte Django-Ansichten anstelle der von der App definierten Ansichten. Auch die Aufrufe der `url`-Methode enthalten zusätzliche Daten, um die Ansicht anzupassen. Diese Aufrufe werden in Schritt 5 näher beschrieben.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Frage: Warum verwendet das URL-Muster „about“ in dem Projekt, das ich erstellt habe, den Ausdruck „^about“ anstatt „^about$“, wie hier dargestellt?

Antwort: Das nachgestellte „$“ im regulären Ausdruck wurde in vielen Versionen der Projektvorlage versehentlich weggelassen. Das URL-Muster funktioniert problemlos für eine Seite mit dem Namen „about“. Ohne das nachgestellte „$“ gleicht das URL-Muster auch URLs wie etwa „about=django“, „about09876“ oder „aboutoflaughter“ ab. Das nachgestellte „$“ wird hier verwendet, um ein URL-Muster zu erstellen, das *nur* mit „about“ übereinstimmt.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Authentifizieren von Benutzern bei Django](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Bereitstellen der App für Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Writing your first Django app, part 4 - forms and generic views (Erstellen Ihrer ersten Django-App – Teil 4: Formulare und allgemeine Ansichten)](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- Quellcode des Tutorials auf GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
