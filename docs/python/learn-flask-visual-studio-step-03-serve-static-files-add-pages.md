---
title: 'Tutorial zu Flask in Visual Studio, Schritt 3: Statische Dateien und Seiten'
titleSuffix: ''
description: Eine exemplarische Vorgehensweise der Grundlagen von Flask im Kontext von Visual Studio-Projekten, die zeigt, wie Sie statische Dateien bereitstellen, Seiten zur App hinzufügen, und die Vorlagenvererbung verwenden
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d474236aca50a74b96689001a56e7d0701caae30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942385"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-flask-app"></a>Schritt 3: Bereitstellen statischer Dateien, Hinzufügen von Seiten und Verwenden von Vorlagenvererbung mit der Flask-App

**Vorheriger Schritt:[Erstellen einer Flask-App mit Ansichten und Seitenvorlagen](learn-flask-visual-studio-step-02-create-app.md)**

In den vorherigen Schritten dieses Tutorials haben Sie gelernt, eine minimale Flask-App mit einer einzelnen eigenständige HTML-Seite zu erstellen. Moderne Web-Apps bestehen jedoch in der Regel aus vielen Seiten und verwenden freigegebene Ressourcen, z.B. CSS- und JavaScript-Dateien, um ein einheitliches Aussehen und Verhalten bereitzustellen.

In diesem Schritt wird Folgendes erläutert:

> [!div class="checklist"]
> - Das Verwenden von Visual Studio-Elementvorlagen zum schnellen Hinzufügen neuer Dateien verschiedener Typen mit geeigneten Codebausteinen (Schritt 3.1)
> - Bereitstellen statischer Dateien über den Code (Schritt 3–2, optional)
> - Das Hinzufügen von zusätzlichen Seiten zur App (Schritt 3-3)
> - Das Verwenden der Vorlagenvererbung zur Erstellung einer Kopfzeile und einer Navigationsleiste, die seitenübergreifend verwendet werden (Schritt 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Schritt 3-1: Kennenlernen der Elementvorlagen

Bei der Entwicklung eine Flask-App fügen Sie in der Regel viele weitere Python-, HTML-, CSS- und JavaScript-Dateien hinzu. Für jeden Dateityp (sowie andere Dateien wie *web.config*, die Sie möglicherweise für die Bereitstellung benötigen), bietet Visual Studio praktische [Elementvorlagen](python-item-templates.md) für Ihren Start an.

Um die verfügbaren Vorlagen anzuzeigen, wechseln Sie zum **Projektmappen-Explorer**, klicken Sie mit der rechten Maustaste auf den Ordner, in dem Sie das Element erstellen möchten, und klicken Sie auf **Hinzufügen** > **Neues Element**:

![Dialogfeld „Neues Element hinzufügen“ in Visual Studio](media/flask/step03-add-new-item-dialog.png)

Um eine Vorlage zu verwenden, wählen Sie die gewünschte Vorlage aus, geben Sie einen Namen für die Datei an, und klicken Sie auf **OK**. Wenn Sie ein Element auf diese Weise hinzufügen, wird die Datei automatisch zum Visual Studio-Projekt hinzugefügt und die Änderungen der Quellcodeverwaltung markiert.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Frage: Woher weiß Visual Studio, welche Elementvorlagen angeboten werden sollen?

Antwort: Die Visual Studio-Projektdatei (*.pyproj*) enthält einen Projekttypbezeichner, der sie als Python-Projekt markiert. Visual Studio verwendet diese Typbezeichner, um nur die Elementvorlagen anzuzeigen, die für den Projekttyp geeignet sind. Auf diese Weise kann Visual Studio mehrere Elementvorlagen für viele Projekttypen anbieten, ohne Sie dazu aufzufordern, sie jedes Mal alle zu sortieren.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Schritt 3-2: Bereitstellen statischer Dateien aus Ihrer App

In einer mit Python (mit einem Framework) erstellten Web-App werden die Python-Dateien immer auf dem Server des Webhosts ausgeführt, und nie auf den Computer eines Benutzers übertragen. Andere Dateien, wie CSS- und JavaScript-Dateien, werden jedoch ausschließlich vom Browser verwendet, damit sie vom Hostserver einfach unbearbeitet übermittelt werden, wenn sie angefordert wurden. Solche Dateien werden als „statische“ Dateien bezeichnet, und Flask kann sie automatisch übermitteln, ohne dass Sie Code schreiben müssen. Innerhalb von HTML-Dateien können Sie beispielsweise auf statische Dateien verweisen, indem Sie einen relativen Pfad im Projekt verwenden. Im ersten Abschnitt dieses Schritts wird eine CSS-Datei zu Ihrer vorhandenen Seitenvorlage hinzugefügt.

Wenn Sie eine statische Datei aus dem Code bereitstellen müssen, z.B. über die Implementierung eines API-Endpunkts, stellt Flask eine praktische Methode bereit, um mithilfe von relativen Pfaden innerhalb eines Ordners namens *static* (im Stammverzeichnis des Projekts) auf Dateien zu verweisen. Im zweiten Abschnitt dieses Schritts wird diese Methode mithilfe einer einfachen statischen Datendatei veranschaulicht.

In beiden Fällen können Sie die Dateien in *static* beliebig anordnen.

### <a name="use-a-static-file-in-a-template"></a>Verwenden einer statischen Datei in einer Vorlage

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Ordner **HelloFlask** im Visual Studio-Projekt, wählen Sie **Hinzufügen** > **Neuer Ordner** aus, und nennen Sie den Ordner `static`.

1. Klicken Sie mit der rechten Maustaste auf den **Static**-Ordner, und wählen Sie **Hinzufügen** > **Neues Element** aus. Wählen Sie im daraufhin angezeigten Dialogfeld die Vorlage **Stylesheet** aus, nennen Sie die Datei `site.css`, und klicken Sie auf **OK**. Die Datei **site.css** wird im Projekt angezeigt und im Editor geöffnet. Ihre Ordnerstruktur sollte ungefähr wie im folgenden Beispiel aussehen:

    ![Statische Dateistruktur wie im Projektmappen-Explorer angezeigt](media/flask/step03-static-file-structure.png)

1. Ersetzen Sie den Inhalt von *site.css* durch den folgenden Code, und speichern Sie die Datei:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Ersetzen Sie den Inhalt der Datei *templates/index.html* der App durch den folgenden Code, der das `<strong>`-Element ersetzt, das in Schritt 2 mit einer `<span>` verwendet wird, die auf die `message`-Formatklasse verweist. Wenn Sie Formatklasse auf diese Weise verwenden, sind Sie viel flexibler in der Gestaltung des Elements.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Führen Sie das Projekt aus, um die Ergebnisse anzuzeigen. Beenden Sie die App, wenn Sie fertig sind, und übergeben Sie Ihre Änderungen bei Bedarf an die Quellcodeverwaltung (wie in [Schritt 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control) beschrieben).

### <a name="serve-a-static-file-from-code"></a>Bereitstellen einer statischen Datei über den Code

Flask stellt eine Funktion namens `serve_static_file` bereit, die Sie über den Code aufrufen können, um auf eine beliebige Datei im *static*-Ordner des Projekts zu verweisen. In folgendem Prozess wird ein einfacher API-Endpunkt erstellt, der eine statische Datendatei zurückgibt.

1. Wenn Sie dies nicht bereits getan haben, erstellen Sie einen *static*-Ordner, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Ordner **HelloFlask** im Visual Studio-Projekt klicken, **Hinzufügen** > **Neuer Ordner** auswählen, und den Ordner `static` nennen.

1. Erstellen Sie im *static*-Ordner eine statische JSON-Datei namens *data.json*, die folgende Beispieldaten (ohne Bedeutung) enthält:

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. Fügen Sie in *views.py* eine Funktion mit der Route „/api/data“ hinzu, die die statische Datendatei mithilfe der `send_static_file`-Methode zurückgibt:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Führen Sie die App aus, und navigieren Sie zum Endpunkt „api/data“, um zu sehen, dass die statische Datei zurückgegeben wird. Beenden Sie die App, wenn Sie fertig sind.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Frage: Gibt es Konventionen für die Organisation von statischen Dateien?

Antwort: Sie können andere CSS-, JavaScript- und HTML-Dateien zu Ihrem *Static*-Ordner beliebig hinzufügen. Eine typische Möglichkeit zum Organisieren von statischen Dateien besteht im Erstellen von Unterordnern namens *Fonts* (Schriftarten), *Skripts* und *Content* (Inhalt) (für Stylesheets und andere Dateien).

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Frage: Wie behandle ich URL-Variablen und Abfrageparameter in einer API?

Antwort: Die Antwort finden Sie in Schritt 1.4 unter [Frage: Wie verarbeitet Flask variable URL-Routen und Abfrageparameter?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables).

## <a name="step-3-3-add-a-page-to-the-app"></a>Schritt 3-3: Fügen Sie eine Seite zur App hinzu

Das Hinzufügen einer anderen Seite zur App bedeutet Folgendes:

- Fügen Sie eine Python-Funktion hinzu, die die Ansicht definiert.
- Fügen Sie eine Vorlage zum Markup der Seite hinzu.
- Fügen Sie der Datei *urls.py* des Flask-Projekts das erforderliche Routing hinzu.

Die folgenden Schritte fügen eine „Info“-Seite zum Projekt „HelloFlask“ und Verknüpfungen zu dieser Seite auf der Startseite hinzu:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den **Templates**-Ordner, wählen Sie **Hinzufügen** > **Neues Element** aus, wählen Sie die Elementvorlage **HTML-Seite** aus, nennen Sie die Datei `about.html`, und wählen Sie **OK** aus.

    > [!Tip]
    > Wenn der Befehl **Neues Element** nicht im Menü **Hinzufügen** angezeigt wird, stellen Sie sicher, dass Sie die App beendet haben, damit Visual Studio den Debugmodus beendet.

1. Ersetzen Sie den Inhalt von *about.html* durch das folgende Markup (Sie ersetzen in Schritt 3.4 den expliziten Link zur Startseite durch eine einfache Navigationsleiste in):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Öffnen Sie die Datei *views.py* der App, und fügen Sie eine Funktion namens `about` hinzu, die die folgende Vorlage verwendet:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Öffnen Sie die Datei *templates/HelloDjangoApp/index.html*, und fügen Sie die folgende Zeile innerhalb des `<body>`-Elements hinzu, um einen Link zur Seite „Info“ zu erstellen (Sie ersetzen diesen Link in Schritt 3.4 durch eine Navigationsleiste):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Speichern Sie alle Dateien mit dem Menübefehl **Datei** > **Alle speichern**, oder drücken Sie einfach auf **STRG**+**UMSCHALTTASTE**+**S**. (Technisch gesehen ist dieser Schritt nicht erforderlich, da das Ausführen des Projekts in Visual Studio die Dateien automatisch speichert. Dennoch ist es gut, wenn Sie diesen Befehl kennen!)

1. Führen Sie das Projekt zum Beobachten der Ergebnisse aus, und überprüfen Sie die Navigation zwischen den Seiten. Beenden Sie die App, wenn Sie fertig sind.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Frage: Ist der Name einer Seitenfunktion für Flask relevant?

Antwort: Nein, denn der `@app.route`-Decorator bestimmt die URLs, für die Flask die Funktion aufruft, um eine Antwort zu generieren. Entwickler passen den Funktionsnamen üblicherweise an die Route an. Dies ist jedoch nicht erforderlich.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Schritt 3-4: Verwenden Sie die Vorlagenvererbung zur Erstellung einer Kopfzeile und einer Navigationsleiste

Anstelle von expliziten Navigationsverknüpfungen auf jeder Seite verwenden moderne Web-Apps in der Regel eine Branding-Kopfzeile und eine Navigationsleiste, die die wichtigsten Seitenverknüpfungen, Popupmenüs usw. bereitstellt. Um sicherzustellen, dass die Kopfzeile und die Navigationsleiste auf allen Seiten identisch sind, sollten Sie jedoch nicht denselben Code in jeder Seitenvorlage wiederholen. Stattdessen sollten Sie die allgemeinen Teile aller Ihrer Seiten zentral definieren.

Das Flask-Vorlagensystem (standardmäßig Jinja) bietet zwei Optionen für die Wiederverwendung von bestimmten Elementen für mehrere Vorlagen: Includedateien und Vererbung.

- *Includes* sind andere Seitenvorlagen, die Sie an einer bestimmten Position in der verweisenden Vorlage mit der Syntax `{% include <template_path> %}` einfügen. Sie können auch eine Variable verwenden, wenn Sie den Pfad im Code dynamisch ändern möchten. „Includes“ werden in der Regel im Textkörper einer Seite verwendet, um die freigegebene Vorlage an einer bestimmten Stelle auf der Seite zu importieren.

- *Vererbung* verwendet `{% extends <template_path> %}` am Anfang einer Seitenvorlage, um eine freigegebene Basisvorlage anzugeben, auf der die verweisende Vorlage aufbaut. Die Vererbung wird häufig verwendet, um ein freigegebenes Layout, eine Navigationsleiste und andere Strukturen für die Seiten einer App zu definieren, damit verweisende Vorlagen bestimmte Bereiche der Basisvorlage namens *Blöcke* nur hinzufügen oder ändern müssen.

In beiden Fällen ist `<template_path>` relativ zum Ordner *Templates* der App (`../` oder `./` sind ebenfalls zulässig).

Eine Basisvorlage grenzt *Blöcke* mit `{% block <block_name> %}`- und `{% endblock %}`-Tags ab. Wenn eine verweisende Vorlage dann Tags mit den gleichen Blocknamen verwendet, überschreibt dessen Blockinhalt den der Basisvorlage.

Die folgenden Schritte veranschaulichen die Vererbung:

1. Erstellen Sie im Ordner *Templates* der App eine neue HTML-Datei (mit dem Kontextmenü **Hinzufügen** > **Neues Element** oder durch **Hinzufügen** > **HTML-Seite**) namens *layout.html*, und ersetzen Sie deren Inhalt durch folgendes Markup. Sie sehen, dass diese Vorlage einen Block mit dem Namen „content“ (Inhalt) enthält. Das ist alles, was die verweisenden Seiten ersetzen müssen:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Fügen Sie die folgenden Formate zur Datei *static/site.css* der App hinzu (in dieser exemplarischen Vorgehensweise wird kein reaktionsfähiges Design veranschaulicht; diese Formate generieren nur ein interessantes Ergebnis):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Ändern Sie *templates/index.html*, um auf die Basisvorlage zu verweisen und den Inhaltsblock zu überschreiben. Sie können sehen, dass diese Vorlage mithilfe der Vererbung einfach wird:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Ändern Sie *templates/about/html*, um ebenfalls auf die Basisvorlage zu verweisen und den Inhaltsblock zu überschreiben:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Führen Sie den Server aus, um die Ergebnisse anzuzeigen. Schließen Sie den Server, wenn Sie fertig sind.

    ![Ausgeführte App zeigt die Navigationsleiste](media/flask/step03-nav-bar.png)

1. Da Sie erhebliche Änderungen an der App vorgenommen haben, ist nun erneut ein guter Zeitpunkt, um Ihre [Änderungen an die Quellcodeverwaltung zu committen](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Verwenden der vollständigen Vorlage „Flask-Webprojekt“](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Bereitstellen der App für Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Weitere Informationen zu den Funktionen der Jinja-Vorlagen (z.B. Ablaufsteuerung) finden Sie in der [Dokumentation zum Jinja-Vorlagen-Designer](http://jinja.palletsprojects.com/en/2.10.x/templates/) unter jinja.pocoo.org.
- Weitere Informationen zur Verwendung von `url_for` finden Sie in der Dokumentation zu Flask-Anwendungsobjekten (flask.pocoo.org) unter [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for).
- Quellcode des Tutorials auf GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
