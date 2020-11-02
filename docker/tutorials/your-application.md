---
title: 'Docker-Tutorial – Teil 1: Erstellen und Ausführen der Aufgabenlisten-Beispiel-App'
description: Dieser Artikel enthält eine Übersicht über die Aufgabenlisten-Beispiel-App, die in Node.js ausgeführt wird.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: a66b747eda633d666518bf2d8a48328a25e038d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046191"
---
# <a name="build-and-run-the-todo-sample-app"></a>Erstellen und Ausführen der Aufgabenlisten-Beispiel-App

Im Verlauf dieses Tutorials arbeiten Sie mit einem einfachen Aufgabenlisten-Manager, der in Node.js ausgeführt wird. Es ist kein Problem, wenn Sie nicht mit Node.js vertraut sind. Es sind keine Kenntnisse über JavaScript erforderlich.

Aktuell ist Ihr Entwicklungsteam recht klein, und Sie entwickeln einfach eine App, um Ihr Minimum Viable Product (MVP) auszulegen. Sie möchten veranschaulichen, wie die App funktioniert und was sie kann, ohne sich Gedanken darüber machen zu müssen, wie sie für ein großes Team mit mehreren Entwicklern funktioniert.

![Screenshot: Aufgabenlisten-Manager](media/todo-list-sample.png)

## <a name="get-the-app"></a>Abrufen der App

Bevor Sie die Anwendung ausführen können, benötigen Sie den Anwendungsquellcode auf Ihrem Computer. Für tatsächliche Projekte klonen Sie hierzu in der Regel das Repository. Für dieses Tutorial wird jedoch eine ZIP-Datei bereitgestellt, die die Anwendung enthält.

1. Stellen Sie sicher, dass auf dem lokalen Computer Docker für Windows oder die Docker Community Edition installiert ist. Weitere Informationen finden Sie in der [Dokumentation zu Docker für Windows](https://docs.docker.com/docker-for-windows/install/). Beim Installationsvorgang wird die ZIP-Datei mit dem Beispiel unter der localhost-Adresse verfügbar gemacht.

1. [Laden Sie die ZIP-Datei herunter](http://localhost/assets/app.zip). Öffnen Sie die ZIP-Datei, und extrahieren Sie die Inhalte.

1. Verwenden Sie anschließend Ihren bevorzugten Code-Editor, um das Projekt zu öffnen. Wenn Sie über keinen Editor verfügen, können Sie [Visual Studio Code](https://code.visualstudio.com/) verwenden. Ihnen sollte `package.json` und die zwei Unterverzeichnisse `src` und `spec` angezeigt werden.

    ![Screenshot: Visual Studio Code mit geladener App](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Erstellen des Containerimages für die App

Zum Erstellen der Anwendung, benötigen Sie ein `Dockerfile`. Ein Dockerfile ist lediglich ein auf Text basierendes Skript mit Anweisungen, das zum Erstellen eines Containerimages verwendet wird. Wenn Sie bereits Dockerfiles erstellt haben, fallen Ihnen möglicherweise einige Probleme im Dockerfile unten auf. Darüber müssen Sie sich keine Gedanken machen. Diese werden behandelt.

1. Erstellen Sie eine Datei namens `Dockerfile` im gleichen Ordner wie die Datei `package.json` mit den folgenden Inhalten.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Stellen Sie sicher, dass die Datei `Dockerfile` keine Erweiterung wie `.txt` aufweist. Einige Editoren fügen diese Erweiterung möglicherweise automatisch an. Dies führt im nächsten Schritt jedoch zu einem Fehler.

1. Öffnen Sie ein Terminal und navigieren Sie zum `app`-Verzeichnis mit dem `Dockerfile`, wenn Sie dies noch nicht getan haben. Erstellen Sie jetzt das Containerimage mithilfe des Befehls `docker build`.

    ```bash
    docker build -t getting-started .
    ```

    Alternativ dazu können Sie auch mit der rechten Maustaste auf die Dockerfile-Datei klicken, **Image erstellen...** auswählen und dann das Tag an der Eingabeaufforderung angeben.

    Dieser Befehl nutzt das Dockerfile zum Erstellen eines neuen Containerimages. Möglicherweise haben Sie festgestellt, dass einige „Layer“ (Schichten) heruntergeladen wurden. Das liegt daran, dass Sie den Generator angewiesen haben, dass Sie mit dem Image `node:12-alpine` beginnen möchten. Da dieses jedoch nicht auf Ihrem Computer vorhanden ist, musste das Image zunächst heruntergeladen werden.

    Nachdem das Image heruntergeladen wurde, haben Sie Ihre Anwendung kopiert und `yarn` verwendet, um die Abhängigkeiten Ihrer Anwendung zu installieren. Mit der Anweisung `CMD` wird der Standardbefehl festgelegt, der ausgeführt werden soll, wenn ein Container über dieses Image gestartet wird.

    Schließlich wird Ihr Image mit dem Flag `-t` gekennzeichnet. Dies können Sie sich als für Menschen lesbaren Namen für das endgültige Image vorstellen. Da Sie dem Image den Namen `getting-started` gegeben haben, können Sie auf das Image verweisen, wenn Sie einen Container ausführen.

    Der `.` am Ende des Befehls `docker build` weist Docker an, dass im aktuellen Verzeichnis nach `Dockerfile` gesucht werden soll.

## <a name="starting-an-app-container"></a>Starten eines App-Containers

Da Sie nun über ein Image verfügen, führen Sie die Anwendung aus. Verwenden Sie hierzu den Befehl `docker run` (diesen kennen Sie von zuvor).

1. Starten Sie Ihren Container mithilfe des Befehls `docker run`, und legen Sie den Namen des Images fest, das Sie soeben erstellt haben:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    Erinnern Sie sich an die Flags `-d` und `-p`? Sie führen den neuen Container im Modus „detached“ (im Hintergrund) aus und erstellen eine Zuordnung zwischen dem Port 3000 des Hosts und dem Port 3000 des Containers. Ohne die Portzuordnung könnten Sie nicht auf die Anwendung zugreifen.

1. Öffnen Sie [http://localhost:3000](http://localhost:3000) nach einigen Sekunden in Ihrem Webbrowser.
    Daraufhin sollte Ihnen die App angezeigt werden.

    ![Leere Aufgabenliste](media/todo-list-empty.png)

1. Fügen Sie ein Element oder zwei hinzu, und sehen Sie sich an, ob die App erwartungsgemäß funktioniert. Sie können Elemente als abgeschlossen kennzeichnen oder entfernen. Ihr Front-End speichert Elemente erfolgreich im Back-End. Das war einfach und schnell.

Sie sollten nun über einen funktionierenden Aufgabenlisten-Manager mit ein paar Elementen verfügen, den Sie eigenständig erstellt haben. Als Nächstes nehmen Sie einige Änderungen vor und erfahren, wie Sie Ihre Container verwalten.

Wenn Sie sich die VS Code-Erweiterung ansehen, sollten Sie Ihre zwei Container sehen, die ausgeführt wurde (dieses Tutorial und der neu gestartete App-Container).

![Docker-Erweiterung mit ausgeführten Containern für das Tutorial und die App](media/vs-two-containers.png)

## <a name="recap"></a>Zusammenfassung

In diesem kurzen Abschnitt haben Sie die Grundlagen zum Erstellen eines Containerimages gelernt und ein Dockerfile dazu erstellt. Sobald Sie ein Image erstellt haben, haben Sie den Container gestartet und die ausgeführte App gesehen.

Als Nächstes nehmen Sie eine Änderung an der App vor und erfahren, wie Sie die ausgeführte Anwendung mit einem neuen Image aktualisieren. Dabei lernen Sie einige weitere nützliche Befehle.

## <a name="next-steps"></a>Nächste Schritte

Tutorial fortsetzen!

> [!div class="nextstepaction"]
> [Aktualisieren Ihrer App](update-your-app.md)
