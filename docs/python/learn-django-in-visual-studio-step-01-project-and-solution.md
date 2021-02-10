---
title: 'Tutorial zu Django in Visual Studio, Schritt 1: Grundlagen zu Django'
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise erhalten Sie grundlegende Informationen zu Django im Zusammenhang mit Visual Studio-Projekten und zur Unterstützung der Django-Entwicklung durch Visual Studio.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: afde24347237ed3fc87d7a00ebdf21787d78909c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942659"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Tutorial: Erste Schritte mit dem Django-Webframework in Visual Studio

[Django](https://www.djangoproject.com/) ist ein allgemeines Python-Framework für die schnelle, sichere und skalierbare Webentwicklung. In diesem Tutorial wird das Django-Framework im Zusammenhang mit Visual Studio-Projektvorlagen beschrieben, die die Erstellung von Django-basierten Web-Apps optimieren sollen.

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> - Erstellen eines Django-Basisprojekts in einem Git-Repository mithilfe der Vorlage „Leeres Django-Webprojekt“ (Schritt 1)
> - Erstellen einer einseitigen Django-App und Rendern dieser Seite mithilfe einer Vorlage (Schritt 2)
> - Bereitstellen statischer Dateien, Hinzufügen von Seiten und Verwenden von Vorlagenvererbung (Schritt 3)
> - Verwenden der Vorlage „Django-Webprojekt“ zum Erstellen einer mehrseitigen App mit dynamischem Design (Schritt 4)
> - Authentifizieren von Benutzern (Schritt 5)
> - Verwenden der Vorlage „Fragt ein Django-Webprojekt ab“ zum Erstellen einer App, die Modelle, Datenbankmigrationen und Anpassungen der Verwaltungsschnittstelle verwendet (Schritt 6)

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio 2017 oder höher unter Windows mit den folgenden Optionen:
  - Die Workload **Python-Entwicklung** (Registerkarte **Workload** im Installationsprogramm). Eine Anleitung finden Sie unter [Installieren der Python-Unterstützung für Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git für Windows** und **GitHub-Erweiterung für Visual Studio** auf der Registerkarte **Einzelne Komponenten** unter **Codetools**.

Django-Projektvorlagen sind auch in allen früheren Versionen von Python-Tools für Visual Studio enthalten. In einzelnen Aspekten können sie sich allerdings von diesem Tutorial unterscheiden, insbesondere bei früheren Versionen des Django-Frameworks.

Die Python-Entwicklung wird in Visual Studio für Mac derzeit nicht unterstützt. Verwenden Sie unter Mac und Linux die [Python-Erweiterung in Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>„Visual Studio-Projekte“ und „Django-Projekte“

In der Django-Terminologie besteht ein „Django-Projekt“ aus mehreren Konfigurationsdateien auf Websiteebene sowie mindestens einer „App“ zur Bereitstellung für einen Webhost, um eine vollständige Webanwendung zu erstellen. Ein Django-Projekt kann mehrere Apps enthalten, und eine App kann gleichzeitig in mehreren Django-Projekten enthalten sein.

Ein Visual Studio-Projekt kann wiederum das Django-Projekt sowie mehrere Apps enthalten. Wenn in diesem Tutorial von einem „Projekt“ die Rede ist, ist damit ein Visual Studio-Projekt gemeint. Soll speziell auf die Komponente „Django-Projekt“ der Webanwendung verwiesen werden, wird der Begriff „Django-Projekt“ verwendet.

Im Verlauf dieses Tutorials erstellen Sie eine einzelne Visual Studio-Projektmappe, die drei separate Django-Projekte enthält, von denen jedes wieder eine einzelne Django-App enthält. Da sich die Projekte in derselben Projektmappe befinden, können Sie einfach zwischen den unterschiedlichen Dateien hin- und herwechseln, um sie zu vergleichen.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Schritt 1.1: Erstellen eines Visual Studio-Projekts und einer -Projektmappe

Beim Arbeiten mit Django über die Befehlszeile wird ein Projekt in der Regel durch Ausführen des Befehls `django-admin startproject <project_name>` gestartet. In Visual Studio wird mit der Vorlage „Leeres Django-Webprojekt“ die gleiche Struktur in einem Visual Studio-Projekt und einer -Projektmappe bereitgestellt.

1. Klicken Sie in Visual Studio auf **Datei** > **Neu** > **Projekt**, suchen Sie nach „Django“, und wählen Sie die Vorlage **Leeres Django-Webprojekt** aus. (Sie finden die Vorlage auch in der Liste auf der linken Seite unter **Python** > **Web**.)

    ![Dialogfeld „Neues Projekt“ in Visual Studio für „Leeres Django-Webprojekt“](media/django/step01-new-blank-project.png)

1. Geben Sie in die Felder im unteren Bereich des Dialogfelds die folgenden Informationen ein (wie in der vorherigen Abbildung gezeigt), und klicken Sie dann auf **OK**:

    - **Name**: Legen Sie den Namen des Visual Studio-Projekts auf **BasicProject** fest. Dieser Name wird auch für das Django-Projekt verwendet.
    - **Speicherort**: Geben Sie einen Speicherort an, an dem die Visual Studio-Projektmappe und das -Projekt erstellt werden sollen.
    - **Projektmappe**: Behalten Sie die Standardoption **Neue Projektmappe erstellen** bei.
    - **Projektmappenname**: Legen Sie den Namen auf **LearningDjango** fest, da er sich für die Projektmappe als Container für mehrere Projekte in diesem Tutorial eignet.
    - **Projektmappenverzeichnis erstellen**: Behalten Sie die Standardaktivierung bei.
    - **Neues Git-Repository erstellen**: Aktivieren Sie das Kontrollkästchen (das standardmäßig deaktiviert ist), damit Visual Studio beim Erstellen der Projektmappe ein lokales Git-Repository erstellt. Wenn diese Option nicht angezeigt wird, führen Sie den Visual Studio-Installer aus, und fügen Sie unter **Codetools** auf der Registerkarte **Einzelne Komponenten****Git für Windows** und die **GitHub-Erweiterung für Visual Studio** hinzu.

1. Nach kurzer Zeit wird Ihnen von Visual Studio das Dialogfeld **Dieses Projekt erfordert externe Pakete** angezeigt (siehe unten). Dieses Dialogfeld wird angezeigt, da die Vorlage eine *requirements.txt*-Datei enthält, die auf das neueste Django-Paket 1.x verweist. (Wählen Sie die Option **Show required packages (Erforderliche Pakete anzeigen)** aus, um die genauen Abhängigkeiten anzuzeigen.)

    ![Dialogfeld „Für dieses Projekt sind externe Pakete erforderlich“](media/django/step01-requirements-prompt-install-myself.png)

1. Wählen Sie die Option **I will install them myself (Ich führe die Installation selbst durch)** aus. In einem nächsten Schritt werden Sie die virtuelle Umgebung erstellen, damit sie auch sicher aus der Quellcodeverwaltung ausgeschlossen ist. (Die Umgebung kann immer aus *requirements.txt* erstellt werden.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Schritt 1-2: Überprüfen der Git-Steuerelemente und Veröffentlichen in einem Remoterepository

Da Sie im Dialogfeld **Neues Projekt** die Option **Neues Git-Repository erstellen** ausgewählt haben, wird für das Projekt bereits ein Commit für die lokale Quellcodeverwaltung ausgeführt, sobald der Erstellungsvorgang abgeschlossen ist. In diesem Schritt können Sie sich mit den Git-Steuerelementen in Visual Studio und dem **Team Explorer**-Fenster vertraut machen, in dem Sie an der Quellcodeverwaltung arbeiten werden.

1. Überprüfen Sie die Git-Steuerelemente in der unteren Ecke des Visual Studio-Hauptfensters. Von links nach rechts zeigen die Steuerelemente Folgendes an: nicht per Push übertragene Commits, ausgecheckte Änderungen, den Namen des Repositorys sowie den aktuellen Branch:

    ![Git-Steuerelemente im Visual Studio-Fenster](media/django/step01-git-controls.png)

    > [!Note]
    > Wenn Sie im Dialogfeld **Neues Projekt** die Option **Neues Git-Repository erstellen** nicht auswählen, zeigen die Git-Steuerelemente nur den Befehl **Zur Quellcodeverwaltung hinzufügen** an, mit dem ein lokales Repository erstellt werden kann.
    >
    > ![Anzeige von „Zur Quellcodeverwaltung hinzufügen“ in Visual Studio, wenn kein Repository erstellt wurde](media/django/step01-git-add-to-source-control.png)

1. Klicken Sie auf die Schaltfläche für die Änderungen, damit das **Team Explorer**-Fenster auf der Seite **Änderungen** in Visual Studio geöffnet wird. Da für das neu erstellte Projekt bereits automatisch ein Commit für die Quellcodeverwaltung ausgeführt wurde, werden keine ausstehenden Änderungen angezeigt.

    ![„Team Explorer“-Fenster auf der Seite „Änderungen“](media/django/step01-team-explorer-changes.png)

1. Klicken Sie auf der Visual Studio-Statusleiste auf die Schaltfläche für die nicht per Push übertragenen Commits (der Aufwärtspfeil mit der **2**), um die Seite **Synchronisierung** im **Team Explorer** zu öffnen. Da Sie nur über ein lokales Repository verfügen, werden auf dieser Seite einfache Optionen zum Veröffentlichen des Repositorys in verschiedenen Remoterepositorys bereitgestellt.

    ![„Team Explorer“-Fenster mit verfügbaren Git-Repositoryoptionen für die Quellcodeverwaltung](media/django/step01-team-explorer.png)

    Sie können für Ihre Projekte einen beliebigen Dienst auswählen. In diesem Tutorial wird die Verwendung von GitHub beschrieben. Der vollständige Beispielcode für das Tutorial befindet sich im Repository [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

1. Bei der Auswahl eines beliebigen **Veröffentlichen**-Steuerelements werden Sie von **Team Explorer** zur Eingabe weiterer Informationen aufgefordert. Wenn Sie z.B. das Beispiel für dieses Tutorial veröffentlichen, musste zuerst das Repository selbst erstellt werden. In diesem Fall wurde die Option **Per Push in Remoterepository übertragen** für die Repository-URL verwendet.

    ![„Team Explorer“-Fenster für die Übertragung per Push in ein vorhandenes Remoterepository](media/django/step01-push-to-github.png)

    Wenn Sie über kein vorhandenes Repository verfügen, können Sie über die Optionen **In GitHub veröffentlichen** und **Per Push in Azure DevOps übertragen** direkt in Visual Studio ein Repository erstellen.

1. Machen Sie sich während der Arbeit mit diesem Tutorial mit der Verwendung der Steuerelemente zur Übertragung von Änderungen per Push oder per Commit in Visual Studio vertraut. Daran werden Sie in diesem Tutorial auch zu geeigneter Zeit erinnert.

> [!Tip]
> Klicken Sie zur schnellen Navigation im **Team Explorer** auf den Header (der in den obigen Abbildungen **Changes** oder **Push** benannt ist), um ein Kontextmenü der verfügbaren Seiten anzuzeigen.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Frage: Welche Vorteile habe ich, wenn ich die Quellcodeverwaltung von Beginn eines Projekts an verwende?

Antwort: Zunächst erhalten Sie durch die Verwendung der Quellcodeverwaltung von Beginn an eine regelmäßige externe Sicherung Ihres Projekts, insbesondere bei gleichzeitiger Verwendung eines Remoterepositorys. Im Gegensatz zur Verwaltung eines Projekts nur in einem lokalen Dateisystem bietet die Quellcodeverwaltung auch einen vollständigen Änderungsverlauf und die einfache Möglichkeit, eine einzelne Datei oder das gesamte Projekt in einem früheren Zustand wiederherzustellen. Über den Änderungsverlauf kann die Ursache von Regressionen (fehlgeschlagenen Tests) ermittelt werden. Bei der Mitarbeit von mehreren Personen an einem Projekt ist die Quellcodeverwaltung zudem wichtig für die Verwaltung von Überschreibungen und bei der Konfliktauflösung. Und schließlich ermöglicht die Quellcodeverwaltung, die im Grunde eine Form der Automatisierung darstellt, die Automatisierung von Builds, Tests sowie der Releaseverwaltung. Sie stellt den ersten Schritt bei der Verwendung von DevOps für ein Projekt dar. Und da die Einstiegsbarrieren so niedrig sind, gibt es keinen Grund, die Quellcodeverwaltung nicht von Beginn an zu verwenden.

Weitere Erläuterungen zur Automatisierung durch die Quellcodeverwaltung finden Sie unter [The Source of Truth: The Role of Repositories in DevOps (Die Quelle der Wahrheit: Die Rolle von Repositorys in DevOps)](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), einem MSDN Magazine-Artikel für mobile Apps, der auch für Web-Apps gilt.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Frage: Kann ich verhindern, dass Visual Studio für ein neues Projekt automatisch einen Commit ausführt?

Antwort: Ja. Wenn Sie die automatische Ausführung eines Commits deaktivieren möchten, wechseln Sie im **Team Explorer** zur Seite **Einstellungen**, und klicken Sie auf **Git** > **Globale Einstellungen**. Deaktivieren Sie die Option **Änderungen nach Mergevorgängen standardmäßig committen**, und klicken Sie anschließend auf **Aktualisieren**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Schritt 1-3: Erstellen der virtuellen Umgebung und Ausschließen aus der Quellcodeverwaltung

Nachdem Sie die Quellcodeverwaltung für das Projekt konfiguriert haben, können Sie die virtuelle Umgebung erstellen, die die für das Projekt erforderlichen Django-Pakete enthält. Anschließend können Sie im **Team Explorer** den Umgebungsordner aus der Quellcodeverwaltung ausschließen.

1. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Knoten **Python-Umgebungen**, und wählen Sie **Virtuelle Umgebung hinzufügen** aus.

    ![Befehl „Virtuelle Umgebung hinzufügen“ im Projektmappen-Explorer](media/django/step01-add-virtual-environment-command.png)

1. Das Dialogfeld **Virtuelle Umgebung hinzufügen** mit der Meldung **Es wurde eine Datei „requirements.txt“ gefunden.** wird angezeigt. Mit der Meldung wird angezeigt, dass Visual Studio diese Datei zur Konfiguration der virtuellen Umgebung verwendet.

    ![Dialogfeld „Virtuelle Umgebung hinzufügen“ mit Meldung zu „requirements.txt“](media/django/step01-add-virtual-environment-found-requirements.png)

1. Klicken Sie auf **Erstellen**, um die Standardeinstellungen zu übernehmen. (Sie können den Namen der virtuellen Umgebung ändern. Dadurch wird jedoch nur der Name des Unterordners geändert, `env` ist dagegen eine Standardkonvention.)

1. Stimmen Sie den Administratorrechten zu, wenn Sie dazu aufgefordert werden. Der anschließende Download- und Installationsvorgang der Pakete durch Visual Studio kann einige Minuten dauern, da Django mehrere tausend Dateien in etwa genauso vielen Unterordnern erweitert. Der Fortschritt wird im **Ausgabe**-Fenster in Visual Studio angezeigt. Während des Vorgangs können Sie die Fragen und Antworten in den folgenden Abschnitten lesen.

1. Klicken Sie bei den Git-Steuerelementen in Visual Studio (auf der Statusleiste) auf den Änderungsindikator (der **99&#42;** anzeigt), um die Seite **Änderungen** im **Team Explorer** zu öffnen.

    Durch das Erstellen der virtuellen Umgebung wurden Tausende von Änderungen übertragen, die Sie jedoch nicht in die Quellcodeverwaltung einbeziehen müssen, da die Umgebung von jeder Person, die das Projekt klont, immer aus *requirements.txt* neu erstellt werden kann.

    Klicken Sie zum Ausschließen der virtuellen Umgebung mit der rechten Maustaste auf den **env**-Ordner, und wählen Sie die Option **Diese lokalen Elemente ignorieren** aus.

    ![Ignorieren einer virtuellen Umgebung in den Änderungen der Quellcodeverwaltung](media/django/step01-ignore-local-items.png)

1. Nachdem die virtuelle Umgebung ausgeschlossen wurde, bleiben nur die Änderungen an der Projektdatei und *.gitignore* übrig. Die *.gitignore*-Datei enthält einen hinzugefügten Eintrag für den Ordner der virtuellen Umgebung. Wenn Sie die Änderungen anzeigen möchten, doppelklicken Sie auf die Datei.

1. Geben Sie eine Commit-Nachricht ein, und klicken Sie auf die Schaltfläche **Alle committen**. Anschließend können Sie die Commits gegebenenfalls per Push in das Remoterepository übertragen.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Frage: Warum sollte ich eine virtuelle Umgebung erstellen?

Antwort: Eine virtuelle Umgebung ist eine hervorragende Möglichkeit, die genauen Abhängigkeiten Ihrer App zu isolieren. Mit einer solchen Isolation können Konflikte innerhalb einer globalen Python-Umgebung vermieden werden, und Tests und die Zusammenarbeit werden unterstützt. Bei der Entwicklung einer App werden im Laufe der Zeit unweigerlich viele nützliche Python-Pakete importiert. Indem Sie die Pakete in einer projektspezifischen virtuellen Umgebung beibehalten, können Sie die *requirements.txt*-Datei des Projekts auf einfache Weise aktualisieren. Mit dieser Datei wird die Umgebung beschrieben, die in der Quellcodeverwaltung enthalten ist. Beim Kopieren des Projekts auf andere Computer, einschließlich Buildserver, Bereitstellungsserver und andere Entwicklungscomputer, kann die Umgebung auf einfache Weise über *requirements.txt* neu erstellt werden (weshalb die Umgebung auch nicht in der Quellcodeverwaltung vorhanden sein muss). Weitere Informationen finden Sie unter [Verwenden von virtuellen Umgebungen](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Frage: Wie entferne ich eine virtuelle Umgebung, für die bereits ein Commit für die Quellcodeverwaltung ausgeführt wurde?

Antwort: Bearbeiten Sie zuerst die *.gitignore*-Datei, um den Ordner auszuschließen. Suchen Sie dazu den Abschnitt am Ende mit dem Kommentar `# Python Tools for Visual Studio (PTVS)`, und fügen Sie eine neue Zeile für den Ordner der virtuellen Umgebung hinzu, z.B. `/BasicProject/env`. (Da die Datei im **Projektmappen-Explorer** in Visual Studio nicht angezeigt wird, öffnen Sie sie direkt über den Menübefehl **Datei** > **Öffnen** > **Datei**. Sie können die Datei auch über den **Team Explorer** öffnen: Klicken Sie dazu auf der Seite **Einstellungen** auf die Option **Repositoryeinstellungen**, und wechseln Sie zum Abschnitt **Ignore- und Attributdateien**. Klicken Sie anschließend auf den Link **Bearbeiten** neben **.gitignore**.)

Öffnen Sie nun ein Befehlsfenster. Navigieren Sie zum Ordner (z.B. *BasicProject*), der den Ordner für die virtuelle Umgebung enthält (z.B. *env*), und führen Sie `git rm -r env` aus. Führen Sie dann für diese Änderungen einen Commit von der Befehlszeile (`git commit -m 'Remove venv'`) oder von der Seite **Änderungen** im **Team Explorer** aus.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Schritt 1-4: Überprüfen der Codebausteine

Überprüfen Sie nach Abschluss der Projekterstellung die Codebausteine des Django-Projekts (die auch hier wieder über den CLI-Befehl `django-admin startproject <project_name>` generiert werden können).

1. Das Django-Verwaltungsprogramm *manage.py* in der Befehlszeile wird im Projektstamm angezeigt. Dieses Programm wird von Visual Studio automatisch als Startdatei des Projekts festlegt. Führen Sie das Hilfsprogramm in der Befehlszeile mithilfe von `python manage.py <command> [options]` aus. Gängige Django-Aufgaben können in Visual Studio ganz komfortabel über Menübefehle ausgeführt werden. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Python** aus, um die Liste anzuzeigen. Einige dieser Befehle werden im weiteren Verlauf des Tutorials näher beschrieben.

    ![Django-Befehle im Kontextmenü eines Python-Projekts](media/django/step01-django-commands-menu.png)

2. Das Projekt enthält einen Ordner, dessen Name mit dem Projektnamen übereinstimmt. Er enthält die Basisdateien des Django-Projekts:

   - *__init.py*: Eine leere Datei, durch die Python mitgeteilt wird, dass der Ordner ein Python-Paket ist.
   - *wsgi.py*: Ein Einstiegspunkt für WSGI-kompatible Webserver zur Bereitstellung des Projekts. Diese Datei bleibt in der Regel unverändert, da sie die Hooks für Produktionswebserver bereitstellt.
   - *settings.py*: Enthält Einstellungen für das Django-Projekt, die bei der Entwicklung einer Web-App geändert werden.
   - *urls.py*: Enthält eine Tabelle mit den Inhalten des Django-Projekts, die auch bei der Entwicklung geändert wird.

     ![Django-Projektdateien im Projektmappen-Explorer](media/django/step01-django-project-in-solution-explorer.png)

3. Wie bereits erwähnt wird dem Projekt durch die Visual Studio-Vorlage auch eine *requirements.txt*-Datei hinzugefügt, in der die Paketabhängigkeit für Django angegeben wird. Wegen dieser Datei werden Sie bei der erstmaligen Erstellung des Projekts zum Erstellen einer virtuellen Umgebung aufgefordert.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Frage: Kann Visual Studio eine „requirements.txt“-Datei aus einer virtuellen Umgebung generieren, nachdem ich andere Pakete installiert habe?

Antwort: Ja. Erweitern Sie den Knoten **Python-Umgebungen**, klicken Sie mit der rechten Maustaste auf die virtuelle Umgebung, und klicken Sie auf den Befehl **„requirements.txt“ generieren**. Verwenden Sie diesen Befehl am besten in regelmäßigen Abständen, wenn Sie die Umgebung ändern und einen Commit der Änderungen für *requirements.txt* in der Quellcodeverwaltung ausführen sowie andere Codeänderungen committen, die von dieser Umgebung abhängen. Wenn Sie Continuous Integration auf einem Buildserver eingerichtet haben, sollten Sie bei jeder Änderung der Umgebung die Datei generieren und einen Commit der Änderungen ausführen.

## <a name="step-1-5-run-the-empty-django-project"></a>Schritt 1-5: Ausführen des leeren Django-Projekts

1. Wählen Sie in Visual Studio die Option **Debuggen** > **Debuggen starten** (**F5**) aus, oder verwenden Sie hierzu die Schaltfläche **Webserver** auf der Symbolleiste (der bei Ihnen angezeigte Browser kann ein anderer sein):

    ![Symbolleisten-Schaltfläche „Webserver ausführen“ in Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Das Ausführen des Servers entspricht dem Ausführen des Befehls `manage.py runserver <port>`, mit dem der integrierte Development Server von Django gestartet wird. Wenn Visual Studio die Meldung **Fehler beim Starten des Debuggers** anzeigt, da keine Startdatei vorhanden ist, klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf **manage.py**, und klicken Sie auf **Als Startdatei festlegen**.

1. Beim Starten des Servers wird ein Konsolenfenster geöffnet, das ebenfalls das Serverprotokoll anzeigt. In Visual Studio wird automatisch ein Browser mit `http://localhost:<port>` geöffnet. Da das Django-Projekt jedoch über keine Apps verfügt, zeigt Django nur eine Standardseite mit der Bestätigung an, dass bisher alles einwandfrei funktioniert:

    ![Standardansicht des Django-Projekts](media/django/step01-first-run-success.png)

1. Wenn Sie fertig sind, stoppen Sie den Server, indem Sie das Konsolenfenster schließen. Sie können hierzu auch den Befehl **Debuggen** > **Debuggen beenden** in Visual Studio verwenden.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Frage: Ist Django sowohl ein Webserver als auch ein Framework?

Antwort: Ja und nein. Django besitzt zwar einen integrierten Webserver, der für die Entwicklung verwendet wird. Dieser Webserver wird verwendet, wenn Sie die Web-App lokal ausführen, wie z.B. beim Debuggen in Visual Studio. Wenn Sie jedoch für einen Webhost bereitstellen, verwendet Django stattdessen den Webserver des Hosts. Mit dem *wsgi.py*-Modul im Django-Projekt werden Einbindungen in die Produktionsserver vorgenommen.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Frage: Was ist der Unterschied zwischen den Befehlen im Menü „Debuggen“ und den Serverbefehlen im Python-Untermenü des Projekts?

Antwort: Sie können den Server über die Befehle und Schaltflächen des **Debuggen**-Menüs in der Symbolleiste oder über die Befehle **Python** > **Server ausführen** oder **Python** > **Debugserver ausführen** im Kontextmenü des Projekts starten. Mit beiden Befehlen wird ein Konsolenfenster geöffnet, in dem die lokale URL (localhost:port) für den ausgeführten Server angezeigt wird. Allerdings müssen Sie einen Browser mit dieser URL manuell öffnen. Das Ausführen des Debugservers startet auch nicht automatisch den Visual Studio-Debugger. Später können Sie gegebenenfalls mit dem Befehl **Debuggen** > **An den Prozess anhängen** einen Debugger an den laufenden Prozess anhängen.

## <a name="next-steps"></a>Nächste Schritte

Noch enthält das Django-Basisprojekt keine Apps. Im nächsten Schritt erfahren Sie, wie Sie eine App erstellen können. Da Sie in der Regel häufiger mit Django-Apps als mit dem Django-Projekt arbeiten, müssen Sie sich derzeit nicht genauer mit den Dateibausteinen auskennen.

> [!div class="nextstepaction"]
> [Erstellen einer Django-App mit Ansichten und Seitenvorlagen](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- Django-Projektcode: [Writing your first Django app, part 1 (Erstellen Ihrer ersten Django-App – Teil 1)](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Verwaltungsprogramm: [django-admin and manage.py („django-admin“ und „manage.py“)](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Quellcode des Tutorials auf GitHub: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)