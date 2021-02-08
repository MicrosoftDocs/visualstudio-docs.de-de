---
title: 'Docker-Tutorial – Teil 3: Freigeben der App'
description: In diesem Tutorial wird beschrieben, wie Docker-Images mithilfe der Docker Hub-Registrierung freigegeben werden.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 676668b1247377597bed55b293efb8ad8b5cd253
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841704"
---
# <a name="share-your-app"></a>Freigeben der App

Nachdem Sie ein Image erstellt haben, besteht Ihr nächster Schritt darin, dieses freizugeben. Zum Freigeben von Docker-Images müssen Sie eine Docker-Registrierung verwenden. Docker Hub ist die Standardregistrierung und der Ort, von dem alle bisher verwendeten Images stammen.

## <a name="create-a-repo"></a>Erstellen eines Repositorys

Zum Pushen eines Images müssen Sie zunächst ein Repository in Docker Hub erstellen.

1. Rufen Sie [Docker Hub](https://hub.docker.com) auf, und melden Sie sich bei Bedarf an.

1. Klicken Sie auf **Repository erstellen**.

1. Verwenden Sie `getting-started` als Repositoryname. Stellen Sie sicher, dass für die Sichtbarkeit `Public` festgelegt ist.

1. Klicken Sie auf **Erstellen**.

Rechts auf der Seite finden Sie einen Abschnitt namens **Docker-Befehle**. Dort finden Sie einen Beispielbefehl, den Sie zum Pushen in dieses Repository ausführen müssen.

![Docker-Befehl mit Pushbeispiel](media/push-command.png)

## <a name="push-the-image"></a>Pushen des Images

1. Versuchen Sie, den Pushbefehl aus Docker Hub in der Befehlszeile auszuführen. Beachten Sie, dass der Befehl Ihren Namespace und nicht „docker“ nutzt.

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Wieso schlägt der Befehl fehl? Der Pushbefehl hat nach einem Image namens „docker/getting-started“ gesucht, aber es wurde nicht gefunden. Wenn Sie `docker image ls` ausführen, werden Sie es ebenfalls nicht finden.

    Sie müssen Ihr zuvor erstelltes, vorhandenes Image mit einem „Tag“ versehen, um dem Image einen anderen Namen zu geben und dies zu beheben.

1. Melden Sie sich mit dem Befehl `docker login -u <username>` bei Docker Hub an.

1. Verwenden Sie den Befehl `docker tag`, um dem Image `getting-started` einen neuen Namen zu geben. Stellen Sie sicher, dass Sie `<username>` durch Ihre Docker-ID austauschen.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Versuchen Sie nun nochmal, den Pushbefehl auszuführen. Wenn Sie den Wert aus Docker Hub kopieren, können Sie den Abschnitt `tagname` löschen, da Sie kein Tag zum Namen des Images hinzugefügt haben. Wenn Sie kein Tag angeben, verwendet Docker das Tag `latest`.

    ```bash
    docker push <username>/getting-started
    ```

    Statt die Befehlszeile zu verwenden, können Sie auch mit der rechten Maustaste in der Docker-Ansicht im Abschnitt **Images** auf das Imagetag klicken und dann **Pushen**, **Verbindung mit Registrierung herstellen** und **Docker Hub** auswählen.

## <a name="run-the-image-on-a-new-instance"></a>Ausführen des Images auf einer neuen Instanz

Da Sie Ihr Image nun erstellt und in eine Registrierung gepusht haben, versuchen Sie als Nächstes, die App in einer neuen Instanz auszuführen, die dieses Containerimage noch nicht kennt. Hierzu verwenden Sie Play with Docker.

1. Öffnen Sie [Play with Docker](http://play-with-docker.com) in Ihrem Browser.

1. Melden Sie sich mit Ihrem Docker Hub-Konto an.

1. Klicken Sie nach der Anmeldung auf den Link „+ ADD NEW INSTANCE“ (Neue Instanz hinzufügen) in der linken Seitenleiste. (Wenn die Leiste nicht angezeigt wird, sollten Sie das Browserfenster vergrößern.) Nach einigen Sekunden wird ein Terminalfenster in Ihrem Browser geöffnet.

    ![Hinzufügen einer neuen Instanz in Play with Docker](media/pwd-add-new-instance.png)

1. Starten Sie im Terminal die App, die Sie zuvor gepusht haben.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Sie sollten sehen, dass das Image gepullt und schließlich gestartet wird.

1. Klicken Sie auf den 3000-Badge, wenn er angezeigt wird. Daraufhin sollte Ihre App mit Ihren Änderungen angezeigt werden. Gut gemacht. Wenn der 3000-Badge nicht angezeigt wird, können Sie auf **Open Port** (Port öffnen) klicken und „3000“ eingeben.

## <a name="recap"></a>Zusammenfassung

In diesem Abschnitt haben Sie erfahren, wie Sie Images freigeben, indem Sie sie an eine Registrierung pushen. Anschließend haben Sie eine neue Instanz geöffnet und das gepushte Image darin ausgeführt. Dieser Vorgang ist in CI-Pipelines recht gängig, bei denen die Pipeline das Image erstellt und an eine Registrierung pusht. Anschließend kann die Produktionsumgebung die neueste Version des Images verwenden.

Erinnern Sie sich an das Ende des letzten Abschnitts, bei dem Sie die App neu gestartet und alle Elemente Ihrer Aufgabenliste verloren haben? Das ist natürlich keine benutzerfreundliche Funktionsweise, daher lernen Sie als Nächstes, wie Sie Daten zwischen Neustarts beibehalten.

## <a name="next-steps"></a>Nächste Schritte

Tutorial fortsetzen!

> [!div class="nextstepaction"]
> [Beibehalten Ihrer Datenbank](persist-your-data.md)