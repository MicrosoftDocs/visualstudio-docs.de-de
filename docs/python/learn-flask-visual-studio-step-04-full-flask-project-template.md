---
title: 'Tutorial „Lernen von Flask“, Visual Studio-Schritt 4: Vorlagen für Webprojekte'
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise erhalten Sie grundlegende Informationen zu Flask im Zusammenhang mit Visual Studio-Projekten, insbesondere zu Features, die durch die Vorlagen „Flask-Webprojekt“ und „Flask/Jade-Webprojekt“ bereitgestellt werden.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ef9154a34ddd08e7e0a4b9434f7f748b2603aef4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882868"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Schritt 4: Verwenden der vollständigen Vorlage „Flask-Webprojekt“

**Vorheriger Schritt: [Serve static files, add pages, and use template inheritance (Bereitstellen statischer Dateien, Hinzufügen von Seiten und Verwenden von Vorlagenvererbung)](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Nachdem Sie sich mit den grundlegenden Funktionen von Flask vertraut gemacht und eine App auf Grundlage der Vorlage „Leeres Flask-App-Projekt“ in Visual Studio erstellt haben, erhalten Sie nun weitere Informationen zu umfangreicheren Funktionen der App über die Vorlage „Flask-Webprojekt“.

In diesem Schritt werden Sie Informationen zu folgenden Inhalten erhalten:

> [!div class="checklist"]
> - Erstellen einer umfangreicheren Flask-Web-App mithilfe der Vorlage „Flask-Webprojekt“ und Informationen zur Projektstruktur (Schritt 4–1).
> - Informationen zu Ansichten und Seitenvorlagen, die mit der dreiseitigen Projektvorlage erstellt wurden. Diese Seiten erben von einer Vorlage für die Basisseite und verwenden statische JavaScript-Bibliotheken wie etwa jQuery und Bootstrap (Schritt 4-2).
> - Informationen zum URL-Routing, das von der Vorlage bereitgestellt wird (Schritt 4-3).

Dieser Artikel gilt ebenfalls für die Vorlage „Flask/Jade-Webprojekt“, die mithilfe der Jade-Vorlagen-Engine anstelle von Jinja eine App erstellt, die mit der durch „Flask-Webprojekt“ erstellten identisch ist. Weitere Details finden Sie am Ende dieses Artikels.

## <a name="step-4-1-create-a-project-from-the-template"></a>Schritt 4-1: Erstellen eines Projekts aus der Vorlage

1. Wechseln Sie in Visual Studio zum **Projektmappen-Explorer**. Klicken Sie mit der rechten Maustaste auf die Projektmappe **LearningFlask**, die Sie in diesem Tutorial bereits erstellt haben, und klicken Sie auf **Hinzufügen** > **Neues Projekt**. (Wenn Sie stattdessen eine neue Projektmappe verwenden möchten, klicken Sie auf **Datei** > **Neu** > **Projekt**.)

1. Suchen Sie im Dialogfeld „Neues Projekt“ nach der Vorlage **Flask-Webprojekt**, und wählen Sie sie aus. Nennen Sie das Projekt „FlaskWeb“, und klicken Sie auf **OK**.

1. Da die Vorlage erneut eine *requirements.txt*-Datei enthält, werden Sie von Visual Studio gefragt, wohin die Abhängigkeiten installiert werden sollen. Wählen Sie die Option **In einer virtuellen Umgebung installieren** aus. Klicken Sie im Dialogfeld **Virtuelle Umgebung hinzufügen** auf **Erstellen**, um die Standardwerte zu übernehmen.

1. Legen Sie das Projekt **FlaskWeb** als Standardprojekt für die Visual Studio-Projektmappe fest, sobald Visual Studio die Einrichtung der virtuellen Umgebung abgeschlossen hat. Klicken Sie hierzu mit der rechten Maustaste im **Projektmappen-Explorer** auf das Projekt, und wählen Sie die Option **Als Startprojekt festlegen** aus. Das fett angezeigte Startprojekt wird ausgeführt, wenn Sie den Debugger starten.

    ![Projektmappen-Explorer mit dem Projekt „FlaskWeb“ als Startprojekt](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Wählen Sie zum Ausführen des Servers **Debuggen** > **Debuggen starten** (**F5**) aus, oder verwenden Sie hierzu die Schaltfläche **Webserver** auf der Symbolleiste:

    ![Symbolleisten-Schaltfläche „Webserver ausführen“ in Visual Studio](media/flask/run-web-server-toolbar-button.png)

1. Die von der Vorlage erstellte App verfügt über drei Seiten: „Startseite“, „Info“ und „Kontakt“. Über die Navigationsleiste können Sie zwischen diesen Seiten navigieren. Nehmen Sie sich etwas Zeit, um sich mit den verschiedenen Teilen der App vertraut zu machen. Verwenden Sie für die Authentifizierung bei der App über den **Anmelden**-Befehl die Administratoranmeldeinformationen, die Sie zuvor erstellt haben.

    ![Vollständige Browseransicht der App „Flask-Webprojekt“](media/flask/step04-full-app-desktop-view.png)

1. Die aus der Vorlage „Flask-Webprojekt“ erstellte App verwendet Bootstrap für ein dynamisches Layout, das sich den Formfaktoren tragbarer Geräte anpasst. Ändern Sie die Größe des Browserfensters in eine schmale Ansicht, wenn Sie das dynamische Layout testen möchten. Dadurch wird der Inhalt vertikal gerendert, und die Navigationsleiste wird zu einem Menüsymbol:

    ![Mobile (schmale) Ansicht der App „Flask-Webprojekt“](media/flask/step04-full-app-mobile-view.png)

1. Für die folgenden Abschnitte kann die App weiterhin ausgeführt werden.

    Wenn Sie die App beenden und [ein Commit der Änderungen für die Quellcodeverwaltung ausführen möchten](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), öffnen Sie zunächst im **Team Explorer** die Seite **Änderungen**. Klicken Sie mit der rechten Maustaste auf den Ordner für die virtuelle Umgebung (vermutlich **env**), und wählen Sie die Option **Diese lokalen Elemente ignorieren** aus.

### <a name="examine-what-the-template-creates"></a>Überprüfen des von der Vorlage erstellten Ergebnisses

Die Vorlage „Flask-Webprojekt“ erstellt die untenstehende Struktur. Die Inhalte ähneln den Projekten, die Sie in vorherigen Schritten erstellt haben. Der Unterschied besteht darin, dass die Vorlage „Flask-Webprojekt“ mehr Struktur im *static*-Ordner enthält, da sie jQuery und Bootstrap für ein reaktionsfähiges Design enthält. Die Vorlage fügt ebenfalls die Seite „Kontakt“ hinzu. Wenn Sie die vorherigen Schritte in diesem Tutorial befolgt haben, sollte Ihnen diese Vorlage vertraut vorkommen.

- Dateien im Projektstamm:
  - *runserver.py*: ein Skript, um die App auf einem Entwicklungsserver auszuführen.
  - *requirements.txt*: Enthält eine Abhängigkeit von Flask 0.x.
- Der Ordner *FlaskWeb* enthält alle App-Dateien:
  - *\_\_init.py\_\_* markiert den App-Code als Python-Modul, erstellt das Flask-Objekt und importiert die App-Ansichten.
  - *views.py* enthält den Code zum Rendern von Seiten.
  - Der Ordner *static* enthält Unterordner namens *content* (CSS-Dateien), *fonts* (Schriftartdateien) und *scripts* (JavaScript-Dateien).
  - Der Ordner *templates* enthält eine *layout.html*-Basisvorlage sowie *about.html*, *contact.html* und *index.html* für spezifische Seiten, die alle *layout.html* erweitern.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Frage: Ist es möglich, eine virtuelle Umgebung für andere Visual Studio-Projekte freizugeben?

Antwort: Ja. Doch bedenken Sie dabei, dass unterschiedliche Projekte im Laufe der Zeit wahrscheinlich unterschiedliche Pakete verwenden werden und eine gemeinsam genutzte virtuelle Umgebung daher alle Pakete für sämtliche Projekte enthalten muss, von denen sie verwendet wird.

Wenn Sie dennoch eine vorhandene virtuelle Umgebung verwenden möchten, führen Sie die folgenden Schritte aus:

1. Wenn Sie aufgefordert werden, Abhängigkeiten in Visual Studio zu installieren, wählen Sie die Option **Ich führe die Installation selbst durch** aus.
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Python-Umgebungen**, und wählen Sie die Option **Vorhandene virtuelle Umgebung hinzufügen** aus.
1. Navigieren Sie zum Ordner mit der virtuellen Umgebung, wählen Sie ihn aus, und klicken Sie anschließend auf **OK**.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Schritt 4-2: Informationen zu den Ansichten und Seitenvorlagen, die von der Projektvorlage erstellt wurden

Wie Sie beim Ausführen des Projekts festgestellt haben, verfügt die App über drei Ansichten: „Startseite“, „Info“ und „Kontakt“. Der Code für diese Ansichten befindet sich im Ordner *FlaskWeb/views.py*. Jede Ansichtsfunktion ruft einfach `flask.render_template` mit dem Pfad zu einer Vorlage und einer Variablenliste mit Argumenten für die Werte auf, die an die Vorlage übergeben werden sollen. Beispielsweise wird die Seite „Info“ von der Funktion `about` verarbeitet, deren Decorator das URL-Routing bereitstellt:

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

Die Funktionen `home` und `contact` sind nahezu identisch und weisen ähnliche Decorators, aber etwas andere Argumente auf.

Vorlagen befinden sich im Ordner *Templates* der App. Die Basisvorlage *layout.html* ist am umfangreichsten. Sie verweist auf alle erforderlichen statischen Dateien (JavaScript und CSS), definiert einen Block namens „content“, der von anderen Seiten überschrieben wird, und stellt einen weiteren Block namens „scripts“ bereit. In den folgenden kommentierten Auszügen aus *layout.html* werden diese bestimmten Bereiche veranschaulicht:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
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

## <a name="the-flaskjade-web-project-template"></a>Die Vorlage „Flask/Jade-Webprojekt“

Wie am Anfang dieses Artikels bereits erwähnt wurde, ist die Vorlage „Flask/Jade-Webprojekt“ in Visual Studio enthalten, mit der eine Anwendung erstellt wird, die optisch dem entspricht, was mit der Vorlage „Flask-Webprojekt“ generiert wird. Der Hauptunterschied besteht darin, dass diese die Jade-Vorlagen-Engine verwendet, die eine Erweiterung von Jinja darstellt und die gleichen Konzepte in einer kompakteren Sprache implementiert. Insbesondere verwendet Jade Schlüsselwörter anstelle von Tags, die beispielsweise in Trennzeichen ({% %}) eingeschlossen sind, und mit denen Sie mithilfe von Schlüsselwörtern auf CSS-Stile und HTML-Elemente verweisen können.

Die Projektvorlage schließt zur Aktivierung von Jade zunächst das pyjade-Paket in *requirements.txt* ein.

Die Datei *\_\_init\_\_.py* der App enthält folgende Zeile:

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

Im Ordner *templates* finden Sie *.jade*-Dateien anstelle von *.html-Vorlagen*, und die Ansichten in *views.py* verweisen auf diese Dateien, wenn sie `flask.render_template` aufrufen. Davon abgesehen ist der Code der Ansichten identisch.

Wenn Sie eine der *.jade*-Dateien öffnen, sehen Sie den kompakteren Ausdruck einer Vorlage. Hier sehen Sie beispielsweise die Inhalte von *templates/layout.jade*, wie sie von der Vorlage „Flask/Jade-Webprojekt“ erstellt wurden:

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

Hier sehen Sie die Inhalte von *templates/about.jade*, bei denen `#{ <name>}` für Platzhalter verwendet wird:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Probieren Sie die Syntax von Jinja und Jade aus, um festzustellen, welche am besten für Sie geeignet ist.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Die Vorlage „Fragt ein Flask-Webprojekt ab“](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Writing your first Django app, part 4 - forms and generic views (Erstellen Ihrer ersten Flask-App – Teil 4: Formulare und allgemeine Ansichten)](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Jade auf GitHub (Dokumentation)](https://github.com/liuliqiang/pyjade) (github.com)
- Quellcode des Tutorials auf GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
