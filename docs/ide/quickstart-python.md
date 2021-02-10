---
title: 'Schnellstart: Erstellen einer Python-Web-App mit Visual Studio'
titleSuffix: ''
description: In diesem Schnellstart verwenden Sie Visual Studio und das Flask-Framework, um eine einfache Web-App in Python zu erstellen.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: dc47bdb2913e2d18998663967d4da3c0a7dcdd9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939941"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Schnellstart: Erstellen einer ersten Python-Web-App mit Visual Studio

In dieser fünf- bis zehnminütigen Einführung in Visual Studio als Python-IDE erstellen Sie eine einfache Python-Webanwendung, die auf dem Flask-Framework basiert. Sie erstellen das Projekt über einzelne Schritte, in denen Sie mehr über die grundlegenden Features von Visual Studio erfahren.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen. Wählen Sie im Installer die Workload **Python-Entwicklung** aus.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen. Wählen Sie im Installer die Workload **Python-Entwicklung** aus.

::: moniker-end

## <a name="create-the-project"></a>Erstellen eines Projekts

In den folgenden Schritten wird ein leeres Projekt erstellt, das als Container für die Anwendung fungiert:

::: moniker range="vs-2017"
1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie oben in der Menüleiste auf **Datei > Neu > Projekt**.

3. Geben Sie im Dialogfeld **Neues Projekt** „Python-Webprojekt“ in das Suchfeld im oberen rechten Bereich ein, wählen Sie **Webprojekt** aus der mittleren Liste aus, geben Sie dem Projekt einen Namen wie „HelloPython“ (HalloPython), und klicken Sie dann auf **OK**.

    ![Dialogfeld „Neues Projekt“ mit der Auswahl „Python-Webprojekt“](media/quickstart-python-00-web-project.png)

    Wenn die Python-Projektvorlagen nicht angezeigt werden, führen Sie den **Visual Studio-Installer** aus, klicken Sie auf **Mehr** > **Ändern**, wählen Sie die Workload **Python-Entwicklung** aus, und klicken Sie dann auf **Ändern**.

    ![Arbeitsauslastung zur Python-Entwicklung im Visual Studio-Installationsprogramm](../python/media/installation-python-workload.png)

4. Das neue Projekt wird im **Projektmappen-Explorer** im rechten Bereich geöffnet. Zu diesem Zeitpunkt ist das Projekt noch leer und enthält keine anderen Dateien.

    ![Projektmappen-Explorer mit dem neu erstellten leeren Projekt](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Öffnen Sie Visual Studio 2019.
2. Wählen Sie auf dem Startbildschirm **Neues Projekt erstellen** aus.
3. Geben Sie oben im Dialogfeld **Neues Projekt erstellen** in das Suchfeld „Python web“ ein, wählen Sie in der Mitte der Liste **Webprojekt** aus, und klicken Sie auf **Weiter**:

    ![Anzeige „Neues Projekt erstellen“ mit der Auswahl „Python-Webprojekt“](media/quickstart-python-00-web-project-2019a.png)

    Wenn die Python-Projektvorlagen nicht angezeigt werden, führen Sie den **Visual Studio-Installer** aus, klicken Sie auf **Mehr** > **Ändern**, wählen Sie die Workload **Python-Entwicklung** aus, und klicken Sie dann auf **Ändern**.

    ![Arbeitsauslastung zur Python-Entwicklung im Visual Studio-Installationsprogramm](../python/media/installation-python-workload.png)

4. Geben Sie im daraufhin angezeigten Dialogfeld **Neues Projekt konfigurieren** als **Projektname** „HelloPython“ ein, wählen Sie einen Speicherort aus, und klicken Sie auf **Erstellen**. (Der **Projektmappenname** wird automatisch entsprechend dem **Projektnamen** festgelegt.)

    ![Dialogfeld „Neues Projekt konfigurieren“](media/quickstart-python-00-web-project-2019b.png)

5. Das neue Projekt wird im **Projektmappen-Explorer** im rechten Bereich geöffnet. Zu diesem Zeitpunkt ist das Projekt noch leer und enthält keine anderen Dateien.

    ![Projektmappen-Explorer mit dem neu erstellten leeren Projekt](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Frage: Welche Vorteile bestehen beim Erstellen eines Projekts für eine Python-Anwendung in Visual Studio?**

**Antwort:** Python-Anwendungen werden in der Regel nur mit Ordnern und Dateien definiert. Diese Struktur kann jedoch bei größeren Anwendungen, die möglicherweise automatisch generierte Dateien, JavaScript für Webanwendungen usw. einbeziehen, komplex werden. Ein Visual Studio-Projekt kann Sie beim Verwalten dieser komplexen Struktur unterstützen. Das Python-Projekt (eine *PYPROJ*-Datei) identifiziert alle Quell- und Inhaltsdateien des Projekts, enthält Buildinformationen für jede Datei, verwaltet die Informationen zur Integration in Quellcodeverwaltungssysteme und unterstützt Sie beim Organisieren Ihrer Anwendung in logische Komponenten.

**Frage: Welche Funktion haben die im Projektmappen-Explorer angezeigten „Projektmappen“?**

**Antwort:** Eine Visual Studio-Projektmappe ist ein Container, der Ihnen das Verwalten von einem oder mehreren in Zusammenhang stehenden Projekten als Gruppe ermöglicht, und Konfigurationseinstellungen speichert, die nicht für ein Projekt spezifisch sind. Die Projekte in einer Projektmappe können ebenfalls aufeinander verweisen. Dadurch kann das Ausführen eines Projekts (z.B. eine Python-App) beispielsweise automatisch zum Erstellen eines anderen Projekts (z.B. eine C++-Erweiterung, die in der Python-App verwendet wird) führen.

## <a name="install-the-flask-library"></a>Installieren der Flask-Bibliothek

Web-Apps in Python verwenden fast immer eine der vielen verfügbaren Python-Bibliotheken, um Details auf unterer Ebene wie das Routing von Webanforderungen und Strukturieren von Antworten zu verarbeiten. Visual Studio stellt hierfür eine Vielzahl von Vorlagen für Web-Apps bereit, von denen Sie eine im Verlauf dieses Schnellstarts verwenden werden.

Hier verwenden Sie folgende Schritte, um die Flask-Bibliothek in der „globalen Umgebung“ (Standardeinstellung) zu installieren, die Visual Studio für dieses Projekt verwendet.

::: moniker range="vs-2017"
1. Erweitern Sie den Knoten **Python-Umgebungen** im Projekt, um die entsprechende Standardumgebung aufzurufen.

    ![Projektmappen-Explorer mit der Standardumgebung](media/quickstart-python-02-default-environment.png)

2. Klicken Sie mit der rechten Maustaste auf die Umgebung und dann auf **Python-Paket installieren**. Dieser Befehl öffnet das Fenster **Python-Umgebungen** in der Registerkarte **Pakete**.

3. Geben Sie „Flask“ in das Suchfeld ein, und wählen Sie **pip install flask from PyPI** aus. Akzeptieren Sie die Aufforderungen zu Administratorberechtigungen, und beobachten Sie den Fortschritt im Fenster **Ausgabe** in Visual Studio. (Eine Aufforderung zur Erhöhung der Rechte wird angezeigt, wenn der Ordner „Pakete“ für die globale Umgebung sich in einem geschützten Bereich wie *C:\Programme* befindet.)

    ![Installieren der Flask-Bibliothek mithilfe von pip](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Erweitern Sie den Knoten **Python-Umgebungen** im Projekt, um die entsprechende Standardumgebung aufzurufen.

    ![Projektmappen-Explorer mit der Standardumgebung](media/quickstart-python-02-default-environment-2019.png)

2. Klicken Sie mit der rechten Maustaste auf die Umgebung und dann auf **Python-Pakete verwalten...** . Dieser Befehl öffnet das Fenster **Python-Umgebungen** in der Registerkarte **Pakete (PyPI)** .

3. Geben Sie in das Suchfeld „flask“ ein. Wenn unterhalb des Suchfelds **Flask** angezeigt wird, können Sie diesen Schritt überspringen. Wählen Sie andernfalls **Run command: pip install flask** (Ausführungsbefehl: pip install flask) aus. Akzeptieren Sie die Aufforderungen zu Administratorberechtigungen, und beobachten Sie den Fortschritt im Fenster **Ausgabe** in Visual Studio. (Eine Aufforderung zur Erhöhung der Rechte wird angezeigt, wenn der Ordner „Pakete“ für die globale Umgebung sich in einem geschützten Bereich wie *C:\Programme* befindet.)

    ![Installieren der Flask-Bibliothek mithilfe von pip](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Nach der Installation wird die Bibliothek in der Umgebung im **Projektmappen-Explorer** angezeigt, d.h., dass Sie sie in Python-Code verwenden können.

    ::: moniker range="vs-2017"
    ![Installierte Flask-Bibliothek, angezeigt im Projektmappen-Explorer](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Installierte Flask-Bibliothek, angezeigt im Projektmappen-Explorer](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Statt Bibliotheken in der globalen Umgebung zu installieren, erstellen Entwickler in der Regel eine „virtuelle Umgebung“, in der Bibliotheken für ein bestimmtes Projekt installiert werden. Visual Studio-Vorlagen stellen diese Option in der Regel bereit. Dies wird unter [Schnellstart: Erstellen eines Python-Projekts mithilfe einer Vorlage](../python/quickstart-02-python-in-visual-studio-project-from-template.md) erläutert.

**Frage: Wo erfahre ich mehr über andere verfügbare Python-Pakete?**

**Antwort:** Besuchen Sie die Seite [Python Package Index (Python-Paketindex)](https://pypi.org/).

## <a name="add-a-code-file"></a>Hinzufügen einer Codedatei

Nun können Sie Python-Code einfügen, um eine rudimentäre Web-App zu implementieren.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Hinzufügen > Neues Element**.

1. Klicken Sie im daraufhin angezeigten Dialogfeld auf **Leere Python-Datei**, geben Sie dieser den Namen *app.py*, und klicken Sie auf **Hinzufügen**. Die Datei wird in Visual Studio automatisch in einem Editorfenster geöffnet.

1. Kopieren Sie den folgenden Code, und fügen Sie diesen in *app.py* ein:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. Sie werden feststellen, dass im Dialogfeld **Hinzufügen > Neues Element** viele weitere Dateitypen angezeigt werden, die Sie zu einem Python-Projekt hinzufügen können, zu denen unter anderem eine Python-Klasse, ein Python-Paket, ein Python-Komponententest und *web.config*-Dateien zählen. Im Allgemeinen sind diese sogenannten Elementvorlagen eine gute Möglichkeit, um schnell Dateien mit nützlichen Codebausteinen zu erstellen.

**Frage: Wo erfahre ich mehr über Flask?**

**Antwort:** Lesen Sie die Flask-Dokumentation. Beginnen Sie dabei mit dem [Quickstart (Schnellstart)](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart).

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf *app.py*, und klicken Sie auf **Als Startdatei festlegen**. Dieser Befehl ermittelt die Codedatei, die in Python bei der Ausführung der App startet.

    ::: moniker range="vs-2017"
    ![Festlegen der Startdatei für ein Projekt in Projektmappen-Explorer](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Festlegen der Startdatei für ein Projekt in Projektmappen-Explorer](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus. Wählen Sie dann die Registerkarte **Debuggen** aus, und legen Sie die Eigenschaft **Portnummer** auf `4449` fest. Dadurch wird sichergestellt, dass Visual Studio entsprechend der `app.run`-Argumente im Code einen Browser mit `localhost:4449` ausführt.

3. Klicken Sie auf **Debuggen > Starten ohne Debugging** (**STRG**+**F5**). Dadurch werden Änderungen an Dateien gespeichert, und die App wird ausgeführt.

4. Ein Befehlsfenster mit der Meldung **Running in https:\//localhost:4449** wird angezeigt, und ein Browserfenster zu `localhost:4449` sollte geöffnet werden, in dem die Meldung „Hello, Python!“ angezeigt wird. Die GET-Anforderung wird ebenfalls mit dem Status „200“ im Befehlsfenster angezeigt.

    Wenn kein Browser automatisch geöffnet wird, starten Sie Ihren bevorzugten Browser, und navigieren Sie zu `localhost:4449`.

    Wenn nur die interaktive Python-Shell im Befehlsfenster angezeigt wird oder das Fenster kurz auf dem Bildschirm aufblinkt, sollten Sie überprüfen, ob Sie in Schritt 1 *app.py* als Startdatei festgelegt haben.

5. Navigieren Sie zu `localhost:4449/hello`, um zu testen, dass der Decorator der `/hello`-Ressource ebenfalls funktioniert. Die GET-Anforderung wird erneut mit dem Status „200“ im Befehlsfenster angezeigt. Sie sollten ebenfalls andere URLs ausprobieren, um festzustellen, dass diese den Statuscode „404“ im Befehlsfenster anzeigen.

6. Schließen Sie das Befehlsfenster, um die App zu beenden, und schließen Sie dann das Browserfenster.

**Frage: Was ist der Unterschied zwischen den Befehlen „Starten ohne Debugging“ und „Debugging starten“?**

**Antwort:** Sie verwenden **Debugging starten**, um die App mit dem [Visual Studio-Debugger](../python/debugging-python-in-visual-studio.md) zu starten. Dadurch können Sie Breakpoints setzen, Variablen untersuchen und Ihren Code Zeile für Zeile durchlaufen. Apps werden im Debugger aufgrund der zahlreichen Hooks, die das Debuggen ermöglichen, möglicherweise langsamer ausgeführt. Im Gegensatz dazu wird die App durch **Starten ohne Debugging** ohne Debugging direkt so ausgeführt, als würden Sie diese über die Befehlszeile ausführen. Außerdem wird ein Browser gestartet, der zu der URL navigiert, die in der Registerkarte **Debuggen** in den Projekteigenschaften angegeben wurde.

## <a name="next-steps"></a>Nächste Schritte

Glückwunsch zum Ausführen Ihrer ersten Python-App über Visual Studio! Dabei haben Sie mehr über das Verwenden von Visual Studio als Python-IDE erfahren.

> [!div class="nextstepaction"]
> [Deploy the app to Azure App Service (Bereitstellen der App in Azure App Service)](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Da die Schritte, die Sie in diesem Schnellstart befolgt haben, relativ allgemein sind, können und sollten diese automatisiert werden. Visual Studio-Projektvorlagen sind für diese Automatisierungen zuständig. Führen Sie den [Schnellstart: Erstellen eines Python-Projekts aus einer Vorlage](../python/quickstart-02-python-in-visual-studio-project-from-template.md) durch. Dort wird veranschaulicht, wie eine Web-App in weniger Schritten erstellt wird, die der ähnelt, die Sie in diesem Artikel erstellt haben.

Ein umfangreicheres Tutorial zu Python in Visual Studio, in dem auch die Verwendung des interaktiven Fensters, das Debuggen, die Datenvisualisierung und das Arbeiten mit Git behandelt wird, finden Sie unter [Tutorial: Arbeiten mit Python in Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Klicken Sie für weitere Informationen zu den Features von Visual Studio auf folgende Links.

- Weitere Informationen zu [Python-Web-App-Vorlagen in Visual Studio](../python/python-web-application-project-templates.md)
- Weitere Informationen zum [Debuggen in Python](../python/debugging-python-in-visual-studio.md)
- Weitere allgemeine Informationen zur [Visual Studio-IDE](../get-started/visual-studio-ide.md)
