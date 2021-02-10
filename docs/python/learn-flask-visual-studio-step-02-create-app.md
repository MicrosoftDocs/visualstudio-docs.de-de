---
title: 'Tutorial „Lernen von Flask“, Visual Studio-Schritt 2: Ansichten und Vorlagen'
titleSuffix: ''
description: In diesem Tutorial erhalten Sie grundlegende Informationen zu Flask im Zusammenhang mit Visual Studio-Projekten, insbesondere zu Schritten zur Erstellung einer App sowie zur Verwendung von Ansichten und Vorlagen.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8e9d55d9c1c22edea1ff826b23beb6d0ec6b392c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942411"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>Schritt 2: Erstellen einer Flask-App mit Ansichten und Seitenvorlagen

**Vorheriger Schritt: [Erstellen eines Visual Studio-Projekts und einer -Projektmappe](learn-flask-visual-studio-step-01-project-solution.md)**

In Schritt 1 dieses Tutorials haben Sie eine Flask-App erstellt, die eine Seite enthält und deren gesamter Code sich in einer einzigen Datei befindet. Zur Weiterentwicklung empfiehlt es sich, den Code umzugestalten und eine Struktur für Seitenvorlagen zu erstellen. Insbesondere sollte der Code für die App-Ansichten von anderen Aspekten wie dem Startcode getrennt werden.

In diesem Schritt wird Folgendes erläutert:

> [!div class="checklist"]
> - Umgestalten des App-Codes zur Trennung von Ansichten und Startcode (Schritt 2.1)
> - Rendern einer Ansicht mit einer Seitenvorlage (Schritt 2.2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>Schritt 2.1: Umgestalten des Projekts zur Erleichterung der weiteren Entwicklung

Durch die Vorlage „Leeres Flask-Webprojekt“ wurde die Datei *app.py* erstellt, die den Startcode und eine Ansicht enthält. Diese Elemente sollten getrennt werden, damit die App so weiterentwickelt werden kann, dass mehrere Ansichten und Vorlagen unterstützt werden.

1. Erstellen Sie im Projektordner einen App-Ordner mit dem Namen `HelloFlask`. Klicken Sie dazu im **Projektmappen-Explorer** mit der rechten Maustaste zuerst auf das Projekt und anschließend auf **Hinzufügen** > **Neuer Ordner**.

2. Erstellen Sie im Ordner *HelloFlask* eine Datei mit dem Namen *\_\_init\_\_.py* und dem unten gezeigten Inhalt. Durch diese Datei wird die `Flask`-Instanz erstellt, und die App-Ansichten, die im folgenden Schritt erzeugt werden, werden geladen:

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. Erstellen Sie im Ordner *HelloFlask* eine Datei mit dem Namen *views.py* und dem unten gezeigten Inhalt. Der Name *views.py* ist wichtig, da Sie `import HelloFlask.views` in *\_\_init\_\_.py* verwendet haben. Wenn die Namen nicht übereinstimmen, wird zur Laufzeit ein Fehler angezeigt.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    Der Code enthält zusätzlich zur Umbenennung der Funktion und der Route in `home` den Code zum Rendern der Seite aus *app.py* und importiert das in *\_\_init\_\_.py* deklarierte `app`-Objekt.

4. Erstellen Sie einen Unterordner mit dem Namen *HelloFlask* in *Templates*. Dieser Ordner bleibt zunächst leer.

5. Benennen Sie im Stammordner des Projekts *app.py* in *runserver.py* um, und stellen Sie sicher, dass der Inhalt dem folgenden Code entspricht:

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```

6. Die Projektstruktur sollte nun so wie auf dem folgenden Bild aussehen:

    ![Projektstruktur nach der Umgestaltung des Codes](media/flask/step02-project-structure.png)

7. Klicken Sie auf **Debuggen** > **Debuggen starten** (**F5**), oder klicken Sie auf die Schaltfläche **Webserver** in der Symbolleiste, um die App zu starten und einen Browser zu öffnen. Der bei Ihnen aufgerufene Browser kann variieren. Verwenden Sie probeweise sowohl die URL-Route „/“ als auch „/home“.

8. Sie können in verschiedenen Teilen des Codes auch Breakpoints festlegen und die App neu starten, wenn Sie die Startsequenz nachvollziehen möchten. Legen Sie beispielsweise einen Haltepunkt für die ersten Zeilen von *runserver.py* und *HelloFlask\_* init *_.py* und für die Zeile `return "Hello Flask!"` in *views.py* fest. Starten Sie dann die App neu (**Debuggen** > **Neu starten**, **STRG**+**UMSCHALT**+**F5** oder über die unten gezeigte Symbolleistenschaltfläche), und gehen Sie schrittweise durch den Code (**F10**), oder führen Sie ihn von jedem Haltepunkt aus mit **F5** aus.

    ![Schaltfläche „Neu starten“ auf der Debugging-Symbolleiste in Visual Studio](media/debugging-restart-toolbar-button.png)

9. Beenden Sie die App, wenn Sie fertig sind.

### <a name="commit-to-source-control"></a>Ausführen eines Commits für die Quellcodeverwaltung

Da Sie Änderungen an Ihrem Code vorgenommen und erfolgreich getestet haben, ist jetzt ein guter Zeitpunkt zum Überprüfen und Fortschreiben von Änderungen der Quellcodeverwaltung. Spätere Schritte in diesem Tutorial erinnern Sie an den geeigneten Zeitpunkt für ein erneutes Commit für die Quellcodeverwaltung und verweisen wieder auf diesen Abschnitt.

1. Klicken Sie im unteren Bereich von Visual Studio auf die Schaltfläche „Änderungen“ (unten eingekreist). Dadurch wird der **Team Explorer** aufgerufen.

    ![Schaltfläche für Änderungen der Quellcodeverwaltung in der Statusleiste von Visual Studio](media/flask/step02-source-control-changes-button.png)

1. Geben Sie im **Team Explorer** beispielsweise die Commitnachricht „Codeumgestaltung“ ein, und klicken Sie anschließend auf **Commit All** (Alle committen). Nachdem der Commit abgeschlossen ist, wird die Meldung „**Commit \<hash> lokal erstellt“ angezeigt. Synchronisieren, um Änderungen auf den Server zu übertragen.** Wenn Sie die Änderungen per Push in Ihr Remoterepository übertragen möchten, wählen Sie **Synchronisieren** und anschließend **Push** unter **Ausgehende Commits** aus. Sie können auch mehrere lokale Commits vor dem Pushvorgang auf Remotecomputer sammeln.

    ![Commits per Push an den Remotecomputer in Team Explorer übertragen](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>Frage: Wie häufig sollte ein Commit in der Quellcodeverwaltung erfolgen?

Antwort: Durch das Committen von Änderungen in der Quellcodeverwaltung wird eine Zeile im Änderungsprotokoll und ein Punkt erstellt, auf den Sie das Repository bei Bedarf zurücksetzen können. Jeder Commit kann außerdem auf bestimmte Änderungen überprüft werden. Da Commits in Git effizient ausgeführt werden, empfiehlt es sich, anstelle eines einzigen Commits mit vielen Änderungen häufige Commits auszuführen. Selbstverständlich müssen Sie nicht jede einzelne Änderung an einer Datei committen. Üblicherweise führen Sie einen Commit durch, wenn Sie ein Feature hinzufügen, eine Struktur verändern (wie in diesem Schritt) oder den Code umgestalten. Sie sollten den Umfang der Commits außerdem mit Ihren Teammitgliedern abklären.

Wie oft Sie Commits ausführen ist getrennt von der Frage zu betrachten, wie häufig Sie Commits in ein Remote-Repository pushen sollten. Sie können z.B. mehrere Commits in Ihrem lokalen Repository verwalten, bevor Sie diese in ein Remote-Repository pushen. Auch hier hängt die Häufigkeit der Commits davon ab, wie Ihr Team das Repository verwalten möchte.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>Schritt 2.2: Verwenden einer Vorlage zum Rendern einer Seite

Die Funktion `home`, die bisher in *views.py* enthalten ist, generiert lediglich eine Nur-Text-HTTP-Antwort für die Seite. In der Praxis erstellen die meisten Webseiten eine Antwort mit Rich-HTML-Seiten, die häufig Livedaten enthalten. Der Hauptgrund für die Definition einer Ansicht mithilfe einer Funktion besteht darin, dass auf diese Weise der Inhalt dynamisch generiert werden kann.

Da der Rückgabewert für die Ansicht nur eine Zeichenfolge ist, können Sie beliebigen HTML-Code innerhalb einer Zeichenfolge und damit dynamischen Inhalt erstellen. Es empfiehlt sich jedoch, das Markup von den Daten zu trennen und dieses in einer Vorlage zu verwalten. Die Daten sollten hingegen im Code verbleiben.

1. Fügen Sie in *views.py* den folgenden Code ein. In diesem wird für die Seite Inline-HTML zusammen mit einigen dynamischen Inhalten verwendet:

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. Führen Sie die App aus, und aktualisieren Sie die Seite mehrmals, um sich Aktualisierungen bei Datum und Uhrzeit anzeigen zu lassen. Beenden Sie die App, wenn Sie fertig sind.

1. Wenn Sie zum Rendern der Seite eine Vorlage verwenden möchten, müssen Sie im Ordner *Templates* eine Datei mit dem Namen *index.html* erstellen, wobei `{{ content }}` ein Platzhalter oder ein Ersatztoken (auch als *Vorlagenvariable* bezeichnet) ist, für das Sie im Code einen Wert angeben:

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. Passen Sie die Funktion `home` so an, dass zum Laden der Vorlage `render_template` verwendet wird. Geben Sie anschließend für „content“ einen Wert an, indem Sie ein benanntes Argument verwenden, das dem Namen des Platzhalters entspricht. Flask sucht im Ordner *templates* automatisch nach Vorlagen. Der Pfad zur Vorlage ist daher relativ zum Ordner:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. Führen Sie die App aus, und sehen Sie sich die Ergebnisse an. Beachten Sie, dass das Inline-HTML in `content`*nicht als HTML* gerendert wird, da die Vorlagenengine (Jinja) HTML-Inhalte automatisch mit Escapezeichen versieht. Automatische Escapezeichen verhindern, dass unbeabsichtigte Sicherheitslücken durch Injection-Angriffe ausgenutzt werden. Entwickler nutzen nämlich häufig die Eingaben auf einer Seite und verwenden diese mithilfe eines Vorlagenplatzhalters als Wert auf einer anderen Seite. Auch Escapezeichen verdeutlichen, dass HTML nicht im Code verwendet werden sollte.

    Sie sollten daher *templates\index.html* so anpassen, dass für die jeweiligen Datenelemente im Markup unterschiedliche Platzhalter verwendet werden:

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

    Anschließend aktualisieren Sie die `home`-Funktion so, dass für alle Platzhalter Werte angeben werden:

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. Wenn Sie die App nun erneut ausführen, ist die gerenderte Ausgabe korrekt.

    ![Ausführen der App mithilfe der Vorlage](media/flask/step02-result.png)

1. Committen Sie die Änderungen in der Quellcodeverwaltung, und aktualisieren Sie ggf. das Remote-Repository wie unter [Schritt 2.1](#commit-to-source-control) beschrieben.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Frage: Müssen Seitenvorlagen in einer separaten Datei vorliegen?

Antwort: Obwohl Vorlagen in der Regel in separaten HTML-Dateien gespeichert sind, können Sie auch eine Inlinevorlage verwenden. Die Verwendung einer separaten Datei wird jedoch empfohlen, um eine saubere Trennung zwischen Markup und Code aufrechtzuerhalten.

### <a name="question-must-templates-use-the-html-file-extension"></a>Frage: Müssen Vorlagen die Dateierweiterung „.html“ verwenden?

Antwort: Antwort: Die *.html*-Erweiterung für Seitenvorlagendateien ist optional, da Sie immer den genauen relativen Pfad zur Datei im ersten Argument der Funktion `render_template` angeben. Visual Studio (und andere Editoren) verfügt jedoch in der Regel über Features wie Codevervollständigung und Syntaxfarbcodierung für *.html*-Dateien, die schwerer wiegen als die Tatsache, dass es sich bei den Seitenvorlagen nicht um HTML im eigentlichen Sinne handelt.

Wenn Sie mit einem Flask-Projekt arbeiten, erkennt Visual Studio automatisch, ob die HTML-Datei, die Sie gerade bearbeiten, tatsächlich eine Flask-Vorlage ist, und stellt bestimmte Features zur automatischen Vervollständigung bereit. Wenn Sie beispielsweise einen Kommentar zu der Flask-Seitenvorlage, `{#`, eingeben, bietet Visual Studio Ihnen automatisch die schließenden `#}`-Zeichen. Die Befehle **Auswahl kommentieren** und **Kommentar der Auswahl entfernen** (im Menü **Bearbeiten** > **Erweitert** und in der Symbolleiste) verwenden ebenfalls anstelle von HTML-Kommentaren Vorlagenkommentare.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>Frage: Können Vorlagen in weiteren Unterordnern verwaltet werden?

Antwort: Ja, Sie können Unterordner verwenden und dann auf den relativen Pfad unter *Templates* bei Aufrufen von `render_template` verweisen. Dadurch erstellen Sie gleichzeitig auf einfache Weise Namespaces für Ihre Vorlagen.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Bereitstellen statischer Dateien, Hinzufügen von Seiten und Verwenden von Vorlagenvererbung](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Flask Quickstart - Rendering Templates (Flask-Schnellstart: Rendern von Vorlagen)](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) (flask.pocoo.org)
- Quellcode für das Tutorial auf GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
