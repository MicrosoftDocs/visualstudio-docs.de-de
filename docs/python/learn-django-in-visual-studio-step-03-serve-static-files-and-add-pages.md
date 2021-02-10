---
title: 'Tutorial zu Django in Visual Studio, Schritt 3: Statische Dateien und Seiten'
titleSuffix: ''
description: Eine exemplarische Vorgehensweise der Grundlagen von Django im Kontext von Visual Studio-Projekten, die zeigt, wie Sie statische Dateien bereitstellen, Seiten zur App hinzufügen, und die Vorlagenvererbung verwenden
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7aabfa91f7f6c6204919c4a06d2d3080b5174c5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942580"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-django-app"></a>Schritt 3: Bereitstellen statischer Dateien, Hinzufügen von Seiten und Verwenden von Vorlagenvererbung mit der Django-App

**Vorheriger Schritt: [Erstellen einer Django-App mit Ansichten und Seitenvorlagen](learn-django-in-visual-studio-step-02-create-an-app.md)**

In den vorherigen Schritten dieses Tutorials haben Sie gelernt, eine minimale Django-App mit einer einzelnen eigenständige HTML-Seite zu erstellen. Moderne Web-Apps bestehen jedoch in der Regel aus vielen Seiten und verwenden freigegebene Ressourcen, z.B. CSS- und JavaScript-Dateien, um ein einheitliches Aussehen und Verhalten bereitzustellen.

In diesem Schritt wird Folgendes erläutert:

> [!div class="checklist"]
> - Das Verwenden von Visual Studio-Elementvorlagen zum schnellen Hinzufügen neuer Dateien verschiedener Typen mit geeigneten Codebausteinen (Schritt 3.1)
> - Das Konfigurieren des Django-Projekts zur Bereitstellung von statischen Dateien (Schritt 3-2)
> - Das Hinzufügen von zusätzlichen Seiten zur App (Schritt 3-3)
> - Das Verwenden der Vorlagenvererbung zur Erstellung einer Kopfzeile und einer Navigationsleiste, die seitenübergreifend verwendet werden (Schritt 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Schritt 3.1: Kennenlernen der Elementvorlagen

Bei der Entwicklung eine Django-App fügen Sie in der Regel viele weitere Python-, HTML-, CSS- und JavaScript-Dateien hinzu. Für jeden Dateityp (sowie andere Dateien wie *web.config*, die Sie möglicherweise für die Bereitstellung benötigen), bietet Visual Studio praktische [Elementvorlagen](python-item-templates.md) für Ihren Start an.

Um die verfügbaren Vorlagen anzuzeigen, wechseln Sie zum **Projektmappen-Explorer**, klicken Sie mit der rechten Maustaste auf den Ordner, in dem Sie das Element erstellen möchten, und klicken Sie auf **Hinzufügen** > **Neues Element**:

![Dialogfeld „Neues Element hinzufügen“ in Visual Studio](media/django/step03-add-new-item-dialog.png)

Um eine Vorlage zu verwenden, wählen Sie die gewünschte Vorlage aus, geben Sie einen Namen für die Datei an, und klicken Sie auf **OK**. Wenn Sie ein Element auf diese Weise hinzufügen, wird die Datei automatisch zum Visual Studio-Projekt hinzugefügt und die Änderungen der Quellcodeverwaltung markiert.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Frage: Woher weiß Visual Studio, welche Elementvorlagen angeboten werden sollen?

Antwort: Die Visual Studio-Projektdatei ( *.pyproj*) enthält einen Projekttypbezeichner, der sie als Python-Projekt markiert. Visual Studio verwendet diese Typbezeichner, um nur die Elementvorlagen anzuzeigen, die für den Projekttyp geeignet sind. Auf diese Weise kann Visual Studio mehrere Elementvorlagen für viele Projekttypen anbieten, ohne Sie dazu aufzufordern, sie jedes Mal alle zu sortieren.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Schritt 3.2: Bereitstellen statischer Dateien aus Ihrer App

In einer mit Python (mit einem Framework) erstellten Web-App werden die Python-Dateien immer auf dem Server des Webhosts ausgeführt, und nie auf den Computer eines Benutzers übertragen. Andere Dateien, wie CSS- und JavaScript-Dateien, werden jedoch ausschließlich vom Browser verwendet, damit sie vom Hostserver einfach unbearbeitet übermittelt werden, wenn sie angefordert wurden. Solche Dateien werden als „statische“ Dateien bezeichnet, und Django kann sie automatisch übermitteln, ohne dass Sie Code schreiben müssen.

Ein Django-Projekt wird standardmäßig konfiguriert, um statische Dateien aus dem *Static*-Ordner der App bereitstellen zu können. Dies gelingt dank der folgenden Zeilen in der Datei *settings.py* des Django-Projekts:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Sie können Dateien mithilfe einer beliebigen Ordnerstruktur im Ordner *Static* organisieren, und dann relative Pfade in diesem Ordner verwenden, um auf die Dateien zu verweisen. Um diesen Prozess zu veranschaulichen, wird mit den folgenden Schritten eine CSS-Datei zur App hinzugefügt, und das Stylesheet wird dann in der *index.html*-Vorlage verwendet:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Ordner **HelloDjangoApp** im Visual Studio-Projekt, wählen Sie **Hinzufügen** > **Neuer Ordner** aus, und nennen Sie den Ordner `static`.

1. Klicken Sie mit der rechten Maustaste auf den **Static**-Ordner, und wählen Sie **Hinzufügen** > **Neues Element** aus. Wählen Sie im daraufhin angezeigten Dialogfeld die Vorlage **Stylesheet** aus, nennen Sie die Datei `site.css`, und klicken Sie auf **OK**. Die Datei **site.css** wird im Projekt angezeigt und im Editor geöffnet. Ihre Ordnerstruktur sollte ungefähr wie im folgenden Beispiel aussehen:

    ![Statische Dateistruktur wie im Projektmappen-Explorer angezeigt](media/django/step03-static-file-structure.png)

1. Ersetzen Sie den Inhalt von *site.css* durch den folgenden Code, und speichern Sie die Datei:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Ersetzen Sie den Inhalt der Datei *templates/HelloDjangoApp/index.html* der App durch den folgenden Code, der das `<strong>`-Element ersetzt, das in Schritt 2 mit einer `<span>` verwendet wird, die auf die `message`-Formatklasse verweist. Wenn Sie Formatklasse auf diese Weise verwenden, sind Sie viel flexibler in der Gestaltung des Elements. (Wenn Sie Visual Studio 2017 15.7 und früher verwenden und *index.html* nicht in einem Unterordner von *Templates* verschoben haben, finden Sie Informationen dazu in Schritt 2-4 zum [Vorlagen-Namespacing](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing).)

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Führen Sie das Projekt aus, um die Ergebnisse anzuzeigen. Beenden Sie den Server, wenn Sie fertig sind, und übergeben Sie Ihre Änderungen an die Quellcodeverwaltung, wenn Sie möchten (wie in [Schritt 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control) beschrieben).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Frage: Welche Bedeutung hat das Tag {% load staticfiles %}?

Antwort: Die `{% load staticfiles %}`-Zeile ist erforderlich, bevor auf statische Dateien in Elementen wie `<head>` und `<body>` verwiesen werden kann. Im Beispiel in diesem Abschnitt verweist „staticfiles“ auf eine benutzerdefinierte Reihe an Django-Vorlagentags, wodurch Sie die `{% static %}`-Syntax zum Verweisen auf statische Dateien verwenden können.  Ohne `{% load staticfiles %}` wird eine Ausnahme angezeigt, wenn die App ausgeführt wird.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Frage: Gibt es Konventionen für die Organisation von statischen Dateien?

Antwort: Sie können andere CSS-, JavaScript- und HTML-Dateien beliebig zu Ihrem *Static*-Ordner hinzufügen. Eine typische Möglichkeit zum Organisieren von statischen Dateien besteht im Erstellen von Unterordnern namens *Fonts* (Schriftarten), *Skripts* und *Content* (Inhalt) (für Stylesheets und andere Dateien). Schließen Sie in jedem Fall diese Ordner im relativen Pfad zur Datei in `{% static %}`-Verweisen ein.

### <a name="question-can-i-complete-the-same-task-without-using-the--load-staticfiles--tag"></a>Frage: Kann ich dieselbe Aufgabe erledigen, ohne das Tag {% load staticfiles %} zu verwenden?

Antwort: Ja, das ist möglich.

```html
<html>
    <head>
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="../../static/site.css" />
    </head>
    <body>
        <span class="message">{{ message }}</span>{{ content }}
    </body>
</html>
```

## <a name="step-3-3-add-a-page-to-the-app"></a>Schritt 3.3: Hinzufügen einer Seite zur App

Das Hinzufügen einer anderen Seite zur App bedeutet Folgendes:

- Fügen Sie eine Python-Funktion hinzu, die die Ansicht definiert.
- Fügen Sie eine Vorlage zum Markup der Seite hinzu.
- Fügen Sie der Datei *urls.py* des Django-Projekts das erforderliche Routing hinzu.

Die folgenden Schritte fügen eine „Info“-Seite zum Projekt „HelloDjangoApp“ und Verknüpfungen zu dieser Seite auf der Startseite hinzu:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Ordner **templates/HelloDjangoApp**, wählen Sie **Hinzufügen** > **Neues Element** aus, wählen Sie die Elementvorlage **HTML-Seite** aus, nennen Sie die Datei `about.html`, und klicken Sie auf **OK**.

    > [!Tip]
    > Wenn der Befehl **Neues Element** nicht im Menü **Hinzufügen** angezeigt wird, stellen Sie sicher, dass Sie den Server beendet haben, damit Visual Studio den Debugging-Modus beendet.

1. Ersetzen Sie den Inhalt von *about.html* durch das folgende Markup (Sie ersetzen in Schritt 3.4 den expliziten Link zur Startseite durch eine einfache Navigationsleiste in):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Öffnen Sie die Datei *views.py* der App, und fügen Sie eine Funktion namens `about` hinzu, die die folgende Vorlage verwendet:

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Öffnen Sie die Datei *urls.py* des Django-Projekts, und fügen Sie die folgende Zeile zum `urlPatterns`-Array hinzu:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. Öffnen Sie die Datei *templates/HelloDjangoApp/index.html*, und fügen Sie die folgende Zeile unterhalb des `<body>`-Elements hinzu, um einen Link zur Seite „Info“ hinzuzufügen (Sie ersetzen diesen Link in Schritt 3.4 durch eine Navigationsleiste):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Speichern Sie alle Dateien mit dem Menübefehl **Datei** > **Alle speichern**, oder drücken Sie einfach auf **STRG**+**UMSCHALTTASTE**+**S**. (Technisch gesehen ist dieser Schritt nicht erforderlich, da das Ausführen des Projekts in Visual Studio die Dateien automatisch speichert. Dennoch ist es gut, wenn Sie diesen Befehl kennen!)

1. Führen Sie das Projekt zum Beobachten der Ergebnisse aus, und überprüfen Sie die Navigation zwischen den Seiten. Schließen Sie den Server, wenn Sie fertig sind.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Frage: Ich habe versucht, „index“ für den Link zur Startseite zu verwenden, aber es funktioniert nicht. Warum?

Antwort: Die Ansichtsfunktion in *views.py* lautet `index`, aber die URL-Routingmuster in der Datei *urls.py* des Django-Projekts enthalten keinen regulären Ausdruck, der mit der Zeichenfolge „index“ übereinstimmt. Um mit diese Zeichenfolge übereinzustimmen, müssen Sie einen anderen Eintrag für das `^index$`-Muster hinzufügen.

Wie im nächsten Abschnitt dargestellt, ist es viel besser, das `{% url '<pattern_name>' %}`-Tag in der Seitenvorlage zu verwenden, um auf den *Namen* eines Musters zu verweisen. In diesem Fall erstellt Django die richtige URL für Sie. Ersetzen Sie z.B. `<div><a href="home">Home</a></div>` in *about.html* durch `<div><a href="{% url 'index' %}">Home</a></div>`. Die Verwendung von „index“ funktioniert hier, da das erste URL-Muster in *urls.py* in der Tat „index“ heißt (aufgrund des `name='index'`-Arguments). Sie können auch „home“ verwenden, um auf das zweite Muster zu verweisen.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Schritt 3.4: Verwenden der Vorlagenvererbung zur Erstellung einer Kopfzeile und einer Navigationsleiste

Anstelle von expliziten Navigationsverknüpfungen auf jeder Seite verwenden moderne Web-Apps in der Regel eine Branding-Kopfzeile und eine Navigationsleiste, die die wichtigsten Seitenverknüpfungen, Popupmenüs usw. bereitstellt. Um sicherzustellen, dass die Kopfzeile und die Navigationsleiste auf allen Seiten identisch sind, sollten Sie jedoch nicht denselben Code in jeder Seitenvorlage wiederholen. Stattdessen sollten Sie die allgemeinen Teile aller Ihrer Seiten zentral definieren.

Das Django-Vorlagensystem bietet zwei Optionen für die Wiederverwendung von bestimmten Elementen über mehrere Vorlagen hinweg: „includes“ und Vererbung.

- *Includes* sind andere Seitenvorlagen, die Sie an einer bestimmten Position in der verweisenden Vorlage mit der Syntax `{% include <template_path> %}` einfügen. Sie können auch eine Variable verwenden, wenn Sie den Pfad im Code dynamisch ändern möchten. „Includes“ werden in der Regel im Textkörper einer Seite verwendet, um die freigegebene Vorlage an einer bestimmten Stelle auf der Seite zu importieren.

- *Vererbung* verwendet `{% extends <template_path> %}` am Anfang einer Seitenvorlage, um eine freigegebene Basisvorlage anzugeben, auf der die verweisende Vorlage aufbaut. Die Vererbung wird häufig verwendet, um ein freigegebenes Layout, eine Navigationsleiste und andere Strukturen für die Seiten einer App zu definieren, damit verweisende Vorlagen bestimmte Bereiche der Basisvorlage namens *Blöcke* nur hinzufügen oder ändern müssen.

In beiden Fällen ist `<template_path>` relativ zum Ordner *Templates* der App (`../` oder `./` sind ebenfalls zulässig).

Eine Basisvorlage grenzt Blöcke mit `{% block <block_name> %}`- und `{% endblock %}`-Tags ab. Wenn eine verweisende Vorlage dann Tags mit den gleichen Blocknamen verwendet, überschreibt dessen Blockinhalt den der Basisvorlage.

Die folgenden Schritte veranschaulichen die Vererbung:

1. Erstellen Sie im Ordner *templates/HelloDjangoApp* der App eine neue HTML-Datei (über das Kontextmenü **Hinzufügen** > **Neues Element** oder **Hinzufügen** > **HTML-Seite**) namens *layout.html*, und ersetzen Sie deren Inhalt durch folgenden Markup-Code. Sie sehen, dass diese Vorlage einen Block mit dem Namen „content“ (Inhalt) enthält. Das ist alles, was die verweisenden Seiten ersetzen müssen:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
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

1. Ändern Sie *templates/HelloDjangoApp/index.html*, um auf die Basisvorlage zu verweisen und den Inhaltsblock zu überschreiben. Sie können sehen, dass diese Vorlage mithilfe der Vererbung einfach wird:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Ändern Sie *templates/HelloDjangoApp/about.html*, um ebenfalls auf die Basisvorlage zu verweisen und den Inhaltsblock zu überschreiben:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Führen Sie den Server aus, um die Ergebnisse anzuzeigen. Schließen Sie den Server, wenn Sie fertig sind.

    ![Ausgeführte App zeigt die Navigationsleiste](media/django/step03-nav-bar.png)

1. Da Sie erhebliche Änderungen an der App vorgenommen haben, ist nun erneut ein guter Zeitpunkt, um Ihre [Änderungen zur Quellcodeverwaltung hinzuzufügen](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Use the full Django Web Project template (Verwenden Sie die vollständige Vorlage „Django-Webprojekt“)](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Bereitstellen der App für Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Writing your first Django app, part 3 (views) (Erstellen Ihrer ersten Django-App – Teil 3: Ansichten)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Weitere Funktionen von Django-Vorlagen, z.B. die Ablaufsteuerung, finden Sie unter [The Django template language (Django-Vorlagensprache)](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Ausführliche Informationen zur Verwendung des `{% url %}`-Tags finden Sie unter der [URL](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) innerhalb von [Built-in template tags and filters for Django templates reference (Integrierte Vorlagentags und Filter für die Django-Vorlagenreferenz)](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) (docs.djangoproject.com)
- Quellcode für das Tutorial auf GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
