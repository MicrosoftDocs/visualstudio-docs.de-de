---
title: 'Tutorial zu Django in Visual Studio, Schritt 2: Ansichten und Seitenvorlagen'
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise erhalten Sie grundlegende Informationen zu Django im Zusammenhang mit Visual Studio-Projekten, insbesondere zu Schritten zur Erstellung einer App oder Verwendung von Ansichten und Vorlagen.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 9c8da2566be9b389b3ae36f2e6aa46686011ac0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942593"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Schritt 2: Erstellen einer Django-App mit Ansichten und Seitenvorlagen

**Vorheriger Schritt: [Erstellen eines Visual Studio-Projekts und einer -Projektmappe](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Bisher enthält Ihr Visual Studio-Projekt lediglich die Komponenten auf Website-Ebene eines Django-*Projekts*, das mindestens eine Django-*App* ausführen kann. Der nächste Schritt ist die Erstellung Ihrer ersten App mit einer Einzelseite.

In diesem Schritt wird Folgendes erläutert:

> [!div class="checklist"]
> - Erstellen einer Django-App mit einer Einzelseite (Schritt 2-1)
> - Ausführen der App aus dem Django-Projekt (Schritt 2-2)
> - Rendern einer Ansicht mithilfe von HTML (Schritt 2-3)
> - Rendern einer Ansicht mithilfe einer Django-Seitenvorlage (Schritt 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Schritt 2.1: Erstellen einer App mit einer Standardstruktur

Eine Django-App ist ein separates Python-Paket, das einen Satz von zugehörigen Dateien für einen bestimmten Zweck enthält. Ein Django-Projekt kann eine beliebige Anzahl von Apps enthalten, da ein Webhost eine beliebige Anzahl getrennter Einstiegspunkte über einen Domänennamen bedienen kann. Beispielsweise enthält ein Django-Projekt für eine Domäne wie contoso.com möglicherweise eine App für `www.contoso.com`, eine zweite App für support.contoso.com und eine dritte App für docs.contoso.com. In diesem Fall verarbeitet das Django-Projekt das URL-Routing auf Websiteebene (in seinen Dateien *urls.py* und *settings.py*), während jede App durch ihr internes Routing, ihre Ansichten und Modelle, ihre statischen Dateien und ihre Verwaltungsschnittstelle ihren eigenen Stil und ihr eigenes Verhalten hat.

Eine Django-App beginnt normalerweise mit einen Standardsatz von Dateien. Visual Studio bietet Elementvorlagen, um eine Django-App in einem Django-Projekt zusammen mit einem integrierten Menübefehl zu initialisieren, der demselben Zweck dient:

- Vorlagen: Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen** > **Neues Element** aus. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Vorlage **Django 1.9-App** aus, geben Sie den Namen der App im Feld **Name** an, und wählen Sie **OK** aus.

- Integrierter Befehl: Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Hinzufügen** > **Django-App** aus. Dieser Befehl fordert Sie auf, einen Namen einzugeben, und erstellt eine Django 1.9-App.

    ![Menübefehl für das Hinzufügen einer Django-App](media/django/step02-add-django-app-command.png)

Verwenden Sie eine der Methoden, und erstellen Sie eine App mit dem Namen „HelloDjangoApp“. Das Ergebnis ist ein Ordner in Ihrem Projekt mit diesem Namen, der Elemente enthält, die in der folgenden Tabelle beschrieben werden.

![Django-App-Dateien im Projektmappen-Explorer](media/django/step02-django-app-in-solution-explorer.png)

| Element | Beschreibung |
| --- | --- |
| **\_\_init\_\_.py** | Die Datei, die die App als Paket identifiziert. |
| **Migrations** | Ordner, in dem Django Skripts speichert, die die Datenbank aktualisieren und an den Änderungen an Modellen ausrichten. Anschließend wenden die Migrationstools von Django die notwendigen Änderungen auf Vorversionen der Datenbank an, sodass sie mit den aktuellen Modellen übereinstimmen. Mithilfe von Migrationen konzentrieren Sie sich weiterhin auf Ihre Modelle und lassen Django das zugrunde liegende Datenbankschema verarbeiten. Migrationen werden in Schritt 6 erörtert. Momentan enthält der Ordner einfach eine Datei *\_\_init\_\_.py* (die angibt, dass der Ordner ein eigenes Python-Paket definiert). |
| **Templates** (Vorlagen) | Ein Ordner für Django-Seitenvorlagen, der eine einzelne *index.html*-Datei in einem Ordner enthält, dessen Name mit dem der App übereinstimmt. (In Visual Studio 2017 Version 15.7 und früher ist die Datei direkt unter *Vorlagen* enthalten und Schritt 2-4 weist Sie an, den Unterordner zu erstellen.) Vorlagen sind HTML-Blöcke, in denen Sichten Informationen hinzufügen können, um eine Seite dynamisch zu rendern. „Variablen“ von Seitenvorlagen, z.B. `{{ content }}` in *index.html*, sind Platzhalter für dynamische Werte, wie später in diesem Artikel (Schritt 2) erläutert wird. Django-Apps erstellen in der Regel einen Namespace für ihre Vorlagen, indem sie sie in einen Unterordner stellen, der mit dem Namen der App übereinstimmt. |
| **admin.py** | Python-Datei, in die Sie die Verwaltungsschnittstelle (siehe Schritt 6) der App erweitern, mit der Sie ein Seeding für Daten in einer Datenbank ausführen und Daten in einer Datenbank bearbeiten können. Diese Datei enthält zunächst nur die Anweisung `from django.contrib import admin`. Django enthält standardmäßig eine Standard-Verwaltungsschnittstelle über Einträge in der Datei *settings.py* des Django-Projekts, die Sie durch Auskommentieren vorhandener Einträge in *urls.py* aktivieren können. |
| **apps.py** | Ein Python-Datei, die eine Konfigurationsklasse für die App definiert (weitere Informationen finden Sie im Anschluss an die Tabelle). |
| **models.py** | Modelle sind Datenobjekte, die von Funktionen identifiziert werden, über die Ansichten mit der zugrunde liegenden Datenbank der App interagieren (siehe Schritt 6). Django stellt die Datenbankverbindungsschicht bereit, sodass sich Apps nicht selbst mit diesen Details befassen müssen. Die Datei *models.py* ist ein Standard-Ausgangspunkt für die Erstellung Ihrer Modelle und enthält zunächst nur die Anweisung `from django.db import models`. |
| **tests.py** | Python-Datei, die die grundlegende Struktur der Komponententests enthält. |
| **views.py** | Ansichten sind das, was Sie normalerweise für Webseiten halten. Sie erhalten HTTP-Anforderungen und geben eine HTTP-Antwort zurück. Ansichten werden in der Regel als HTML gerendert, das Webbrowser anzeigen können, aber eine Ansicht muss nicht notwendigerweise sichtbar sein (z.B. ein vorläufiges Formular). Eine Ansicht wird durch eine Python-Funktion definiert, die dafür verantwortlich ist, das HTML zu rendern und an den Browser zu senden. Die Datei *views.py* ist ein Standard-Ausgangspunkt für die Erstellung von Ansichten und enthält zunächst nur die Anweisung `from django.shortcuts import render`. |

Der Inhalt der Datei *apps.py* sieht wie folgt aus, wenn Sie den Namen „HelloDjangoApp“ verwenden:

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Frage: Unterscheidet sich die Erstellung einer Django-App in Visual Studio von der Erstellung einer App auf der Befehlszeile?

Antwort: Wenn Sie den Befehl **Hinzufügen** > **Django-App** ausführen oder **Hinzufügen** > **Neues Element** mit einer Django-App-Vorlage verwenden, werden die gleichen Dateien erstellt wie mit dem Django-Befehl `manage.py startapp <app_name>`. Die Erstellung der App in Visual Studio hat den Vorteil, dass der App-Ordner und alle enthaltenen Dateien automatisch in das Projekt integriert werden. Sie können den gleichen Visual Studio-Befehl verwenden, um eine beliebige Anzahl von Apps in Ihrem Projekt zu erstellen.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Schritt 2.2: Ausführen der App aus dem Django-Projekt

Wenn Sie an diesem Punkt das Projekt in Visual Studio erneut ausführen (über die Schaltfläche der Symbolleiste oder mit **Debuggen** > **Debuggen starten**), wird die Standardseite weiterhin angezeigt. Es werden keine App-Inhalte angezeigt, da Sie eine App-spezifische Seite definieren und die App dem Django-Projekt hinzufügen müssen:

1. Ändern Sie im Ordner *HelloDjangoApp* die Datei *views.py* entsprechend dem nachfolgenden Code, der eine Ansicht namens „index“ definiert:

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. Ändern Sie im Ordner *BasicProject* (den Sie in Schritt 1 erstellt haben) die Datei *urls.py* mindestens entsprechend dem folgenden Code (Sie können die aufschlussreichen Kommentare nach Wunsch beibehalten):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Jedes URL-Muster beschreibt die Ansichten, an die Django bestimmte websitebezogene URLs weiterleitet (d.h. der Teil, der auf „`https://www.domain.com/`“ folgt). Der erste Eintrag in `urlPatterns`, der mit dem regulären Ausdruck `^$` beginnt, ist das Routing für das Stammverzeichnis der Website, "/". Der zweite Eintrag, `^home$`, leitet "/ home"weiter. Eine beliebige Anzahl von Routings zu derselben Ansicht ist möglich.

1. Führen Sie das Projekt erneut aus, um die Meldung **Hello, Django!** , wie in der Ansicht definiert, zu sehen. Stoppen Sie den Server, wenn Sie fertig sind.

### <a name="commit-to-source-control"></a>Ausführen eines Commits für die Quellcodeverwaltung

Da Sie Änderungen an Ihrem Code vorgenommen und erfolgreich getestet haben, ist jetzt ein guter Zeitpunkt zum Überprüfen und Fortschreiben von Änderungen der Quellcodeverwaltung. Spätere Schritte in diesem Tutorial erinnern Sie an den geeigneten Zeitpunkt für ein erneutes Commit für die Quellcodeverwaltung und verweisen wieder auf diesen Abschnitt.

1. Klicken Sie im unteren Bereich von Visual Studio auf die Schaltfläche „Änderungen“ (unten eingekreist). Dadurch wird der **Team Explorer** aufgerufen.

    ![Schaltfläche für Änderungen der Quellcodeverwaltung in der Statusleiste von Visual Studio](media/django/step02-source-control-changes-button.png)

1. Geben Sie in **Team Explorer** eine Commit-Nachricht wie „Erste Django-App erstellen“ ein, und wählen Sie **Alle committen** aus. Nachdem der Commit abgeschlossen ist, wird die Meldung „**Commit \<hash> lokal erstellt“ angezeigt. Synchronisieren, um Änderungen auf den Server zu übertragen.** Wenn Sie die Änderungen per Push in Ihr Remoterepository übertragen möchten, wählen Sie **Synchronisieren** und anschließend **Push** unter **Ausgehende Commits** aus. Sie können auch mehrere lokale Commits vor dem Pushvorgang auf Remotecomputer sammeln.

    ![Commits per Push an den Remotecomputer in Team Explorer übertragen](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Frage: Was bedeutet das Präfix „R“ vor den Routing-Zeichenfolgen?

Antwort: Das Präfix „R“ für eine Zeichenfolge in Python bedeutet „unformatiert“. Python wird auf diese Weise angewiesen, keine Escapezeichen in der Zeichenfolge zu verwenden. Da reguläre Ausdrücke viele Sonderzeichen verwenden, können solche Zeichenfolgen mit dem Präfix „R“ wesentlich einfacher gelesen werden als Zeichenfolgen, die mehrere '\\-Escapezeichen enthalten.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Frage: Was bedeuten die Zeichen „^“ und „$“ in URL-Routing-Einträgen?

Antwort: In regulären Ausdrücken, die URL-Muster definieren, bedeutet „^“ „Zeilenanfang“ und „$“ bedeutet „Zeilenende“, wobei sich die URLs erneut auf das Stammverzeichnis der Website beziehen (der Teil, der auf `https://www.domain.com/` folgt). Der reguläre Ausdruck `^$` bedeutet „leer“ und entspricht daher der vollständigen URL `https://www.domain.com/` (dem Stammverzeichnis der Website wurde nichts hinzugefügt). Das Muster `^home$` entspricht genau `https://www.domain.com/home/`. (Django verwendet den nachgestellten / nicht im Mustervergleich.)

Wenn Sie in einem regulären Ausdruck kein nachgestelltes „$“ verwenden, wie z.B. bei `^home`, stimmt das URL-Muster mit *allen* URLs überein, die mit „home“ beginnen, z.B. „home“, „homework“, „homestead“ und „home192837“.

Zum Experimentieren mit anderen regulären Ausdrücken verwenden Sie Onlinetools, wie z.B. [regex101.com](https://regex101.com) auf [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Schritt 2.3: Rendern einer Ansicht mithilfe von HTML

Die Funktion `index`, die bisher in *views.py* enthalten ist, generiert lediglich eine Nur-Text-HTTP-Antwort für die Seite. Die meisten realen Webseiten antworten natürlich mit Rich-HTML-Seiten, die häufig Live-Daten enthalten. Dies ist der Hauptgrund für die Definition einer Ansicht mit einer Funktion, sodass der Inhalt dynamisch generiert werden kann.

Da das Argument von `HttpResponse` nur eine Zeichenfolge ist, können Sie jedes beliebige gewünschte HTML in einer Zeichenfolge erstellen. Einfaches Beispiel: Ersetzen Sie die Funktion `index` durch folgenden Code (behalten Sie die vorhandenen `from`-Anweisungen bei), der eine HTML-Antwort unter Verwendung des dynamischen Inhalts generiert, der bei jeder Aktualisierung der Seite aktualisiert wird:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Führen Sie das Projekt erneut aus, um die Meldung "**Hello Django!** am Montag, d. 16. April 2018, um 16:28:10“ zu sehen. Aktualisieren Sie die Seite, um die Zeit zu aktualisieren und zu bestätigen, dass der Inhalt mit jeder Anforderung generiert wird. Stoppen Sie den Server, wenn Sie fertig sind.

> [!Tip]
> Kurzbefehle für das Stoppen und erneute Starten des Projekts sind die Verwendung der Menübefehle **Debuggen** > **Neustart** (**STRG**+**UMSCHALTTASTE**+**F5**) oder die Verwendung der Schaltfläche **Neu starten** auf der Debugging-Symbolleiste:
>
> ![Schaltfläche „Neu starten“ auf der Debugging-Symbolleiste in Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Schritt 2.4: Rendern einer Ansicht mit einer Seitenvorlage

Das Generieren von HTML im Code funktioniert gut bei sehr kleinen Seiten. Bei komplexeren Seiten sollten jedoch die statischen HTML-Teile Ihrer Seite (zusammen mit Verweisen auf CSS- und JavaScript-Dateien) als „Seitenvorlagen“ beibehalten werden, in die Sie dann dynamischen, codegenerierten Inhalt einfügen. Im vorherigen Abschnitt sind nur das Datum und die Uhrzeit aus dem `now.strftime`-Aufruf dynamisch. Dies bedeutet, dass der übrige Inhalt in eine Seitenvorlage gestellt werden kann.

Eine Django-Seitenvorlage ist ein HTML-Block, der eine Reihe von „Variablen“ genannten Ersatztoken enthalten kann, die durch `{{` und `}}` abgegrenzt sind, wie z.B. in `{{ content }}`. Das Vorlagenmodell von Django ersetzt dann Variablen mit dynamischem Inhalt, den Sie im Code bereitstellen.

Die folgenden Schritte veranschaulichen die Verwendung von Seitenvorlagen:

1. Öffnen Sie im Ordner *BasicProject*, der das Django-Projekt enthält, die Datei *settings.py*, und fügen Sie der Liste `INSTALLED_APPS` den App-Namen „HelloDjangoApp“ hinzu. Durch Hinzufügen der App zur Liste erfährt das Django-Projekt, dass ein Ordner mit diesem Namen vorhanden ist, der eine App enthält:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Stellen Sie außerdem in *settings.py* sicher, dass das `TEMPLATES`-Objekt die folgende Zeile enthält (standardmäßig enthalten), durch die Django angewiesen wird, Vorlagen im Ordner *Templates* einer installierten App zu suchen:

    ```json
    'APP_DIRS': True,
    ```

1. Öffnen Sie im Ordner *HelloDjangoApp* die Seitenvorlagendatei *templates/HelloDjangoApp/index.html* (oder *templates/index.html* in VS 2017 Version 15.7 oder früher), um zu prüfen, ob sie eine Variable `{{ content }}` enthält:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. Öffnen Sie im Ordner *HelloDjangoApp* die Datei *views.py*, und ersetzen Sie die Funktion `index` durch den folgenden Code, der die Hilfsfunktion `django.shortcuts.render` enthält. Das Hilfsprogramm `render` stellt eine einfache Schnittstelle für das Arbeiten mit Seitenvorlagen bereit. Achten Sie darauf, dass Sie alle vorhandenen `from`-Anweisungen beibehalten.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    Das erste Argument für `render` ist das Anforderungsobjekt, gefolgt vom relativen Pfad zur Vorlagendatei im Ordner *Templates* der App. Ggf. wird eine Vorlagendatei nach der Ansicht benannt, die sie unterstützt. Das dritte Argument, `render`, ist ein Variablen-Dictionary, auf das die Vorlage verweist. Sie können Objekte in das Dictionary einschließen. In diesem Fall kann eine Variable in der Vorlage auf `{{ object.property }}` verweisen.

1. Führen Sie das Projekt aus, und berücksichtigen Sie die Ausgabe. Sie sollten eine ähnliche Meldung wie in Schritt 2-2 sehen, die angibt, dass die Vorlage funktioniert.

    Beachten Sie jedoch, dass der HTML-Code, den Sie in der Eigenschaft `content` verwenden, nur als Nur-Text gerendert wird, da die Funktion `render` das HTML automatisch mit Escapezeichen versieht. Automatische Escapezeichen verhindern, dass unbeabsichtigte Sicherheitslücken durch Injectionangriffe ausgenutzt werden. Entwickler nutzen nämlich häufig die Eingaben auf einer Seite und verwenden diese mithilfe eines Vorlagenplatzhalters als Wert auf einer anderen Seite. Escapezeichen sind auch eine Erinnerung daran, dass es am besten ist, HTML-Code außerhalb des Codes in der Seitenvorlage zu schreiben. Glücklicherweise ist es eine einfache Angelegenheit, bei Bedarf zusätzliche Variablen zu erstellen. Ändern Sie z.B. *index.html* mit *Vorlagen* entsprechend dem folgenden Markup, das einen Seitentitel hinzufügt und die gesamte Formatierung in der Seitenvorlage beibehält:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Schreiben Sie dann `index`-Ansichtsfunktion folgendermaßen, um Werte für alle Variablen in der Seitenvorlage bereitzustellen:

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. Stoppen Sie den Server, und starten Sie das Projekt neu. Beachten Sie, dass die Seite jetzt ordnungsgemäß gerendert wird:

    ![Ausführen der App mithilfe der Vorlage](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 Version 15.7 und früher: Als letzten Schritt verschieben Sie Ihre Vorlagen in einen Unterordner, der den gleichen Namen hat wie Ihre App. Dadurch wird ein Namespace erstellt, und potenzielle Konflikte mit anderen Apps, die Sie möglicherweise dem Projekt hinzufügen, können vermieden werden. (Die Vorlagen in VS 2017 15.8 und höher erledigen dies automatisch.) Erstellen Sie also einen Unterordner in *Templates* mit dem Namen *HelloDjangoApp*, verschieben Sie *index.html* in diesen Unterordner, und ändern Sie die Ansichtsfunktion `index` so, dass sie auf den neuen Pfad der Vorlage, *HelloDjangoApp/index.html*, verweist. Führen Sie anschließend das Projekt aus, stellen Sie sicher, dass die Seite ordnungsgemäß gerendert wird, und stoppen Sie den Server.

1. Führen Sie einen Commit der Änderungen an der Quellcodeverwaltung aus, und aktualisieren ggf. Sie das Remoterepository, wie unter [Schritt 2-2](#commit-to-source-control) beschrieben.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Frage: Müssen Seitenvorlagen in einer separaten Datei vorliegen?

Antwort: Obwohl Vorlagen in der Regel in separaten HTML-Dateien gespeichert sind, können Sie auch eine Inlinevorlage verwenden. Die Verwendung einer separaten Datei wird jedoch empfohlen, um eine saubere Trennung zwischen Markup und Code aufrechtzuerhalten.

### <a name="question-must-templates-use-the-html-file-extension"></a>Frage: Müssen Vorlagen die Dateierweiterung „.html“ verwenden?

Antwort: Die Erweiterung *.html* für Seitenvorlagendateien ist komplett optional, da Sie immer den genauen relativen Pfad zur Datei im zweiten Argument der Funktion `render` verwenden. Visual Studio (und andere Editoren) verfügt jedoch in der Regel über Features wie Codevervollständigung und Syntaxfarbcodierung für *.html*-Dateien, die schwerer wiegen als die Tatsache, dass es sich bei den Seitenvorlagen nicht um HTML im eigentlichen Sinne handelt.

Wenn Sie mit einem Django-Projekt arbeiten, erkennt Visual Studio automatisch, ob die HTML-Datei, die Sie gerade bearbeiten, tatsächlich eine Django-Vorlage ist, und stellt bestimmte Features zur automatischen Vervollständigung bereit. Wenn Sie beispielsweise einen Kommentar zu der Django-Seitenvorlage, `{#`, eingeben, bietet Visual Studio Ihnen automatisch die schließenden `#}`-Zeichen. Die Befehle **Auswahl kommentieren** und **Kommentar der Auswahl entfernen** (im Menü **Bearbeiten** > **Erweitert** und in der Symbolleiste) verwenden ebenfalls anstelle von HTML-Kommentaren Vorlagenkommentare.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Frage: Beim Ausführen des Projekts wird eine Fehlermeldung angezeigt, die besagt, dass die Vorlage nicht gefunden werden kann. Wo liegt der Fehler?

Antwort: Wenn Sie von einer Fehlermeldung informiert werden, dass die Vorlage nicht gefunden werden kann, stellen Sie sicher, dass Sie die App der Datei *settings.py* des Django-Projekts in der Liste `INSTALLED_APPS` hinzugefügt haben. Ohne diesen Eintrag weiß Django nicht, dass der Ordner *Templates* der App überprüft werden soll.

### <a name="question-why-is-template-namespacing-important"></a>Frage: Weshalb ist Vorlagen-Namespacing wichtig?

Antwort: Wenn Django eine Vorlage sucht, auf die in der Funktion `render` verwiesen wird, wird zuerst die gefundene Datei verwendet, die mit dem relativen Pfad übereinstimmt. Wenn mehrere Django-Apps im selben Projekt vorhanden sind, die die gleichen Ordnerstrukturen für Vorlagen verwenden, ist es wahrscheinlich, dass eine App unabsichtlich eine Vorlage einer anderen App verwendet. Um solche Fehler zu vermeiden, erstellen Sie immer einen Unterordner unter dem Ordner *Templates* einer App, der mit dem Namen der App übereinstimmt. Auf diese Weise lassen sich Duplizierungen vermeiden.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Bereitstellen statischer Dateien, Hinzufügen von Seiten und Verwenden von Vorlagenvererbung](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Writing your first Django app, part 1 - views (Erstellen Ihrer ersten Django-App – Teil 1: Ansichten)](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Weitere Funktionen von Django-Vorlagen, z.B. „includes“ und Vererbung, finden Sie unter [The Django template language (Django-Vorlagensprache)](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Regular expression training on inLearning (Schulung zu regulären Ausdrücken auf inLearning)](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Quellcode für das Tutorial auf GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
