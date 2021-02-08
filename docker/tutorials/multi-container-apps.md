---
title: 'Docker-Tutorial – Teil 6: Apps mit mehreren Containern'
description: Hier erfahren Sie, wie Sie eine Netzwerkverbindungen zwischen Containern einrichten und einen Container für eine MySQL-Datenbank hinzufügen.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 0c8c9fb4072da071ba06d5dc371e85db8291353a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841782"
---
# <a name="multi-container-apps"></a>Apps mit mehreren Containern

Bis zu diesem Zeitpunkt haben Sie mit Apps mit einem einzelnen Container gearbeitet. Nun fügen Sie dem Anwendungsstapel MySQL hinzu. Häufig kommt die Frage auf: „Wo wird MySQL ausgeführt? Ist eine Installation im gleichen Container oder eine separate Ausführung ratsam?“ Im Allgemeinen sollte **jeder Container eine Aufgabe haben und diese erfolgreich ausführen**. Einige Gründe:

- Die Wahrscheinlichkeit ist groß, dass Sie APIs und Front-Ends anders als Datenbanken skalieren müssen.
- Separate Container ermöglichen das Verwalten und Aktualisieren von Versionen in Isolation.
- Obwohl Sie möglicherweise einen Container lokal für die Datenbank verwenden, sollten Sie in der Produktion einen verwalteten Dienst für die Datenbank verwenden. Sie möchten die Datenbank-Engine nicht mit Ihrer App versenden.
- Das Ausführen mehrerer Prozesse erfordert einen Prozess-Manager (der Container startet nur einen Prozess), wodurch sich die Komplexität beim Starten bzw. Herunterfahren des Containers erhöht.

Es gibt aber noch weitere Gründe. Daher aktualisieren Sie die Anwendung so, dass sie wie folgt funktioniert:

![Mit MySQL-Container verbundene To-Do-App](media/multi-app-architecture.png)

## <a name="container-networking"></a>Containernetzwerke

Beachten Sie, dass Container standardmäßig isoliert ausgeführt werden und nichts über andere Prozesse oder Container auf dem gleichen Computer wissen. Wie schaffen Sie es also, dass ein Container mit einem anderen kommunizieren kann? Die Antwort ist: **Netzwerke**. Zum Glück müssen Sie hierfür kein Netzwerktechniker sein (Hurra!). Bedenken Sie diese Regel:

> [!NOTE]
> Wenn sich zwei Container im gleichen Netzwerk befinden, können sie miteinander kommunizieren. Wenn dies nicht der Fall ist, ist das eben nicht möglich.

## <a name="start-mysql"></a>Starten Sie MySQL.

Es gibt zwei Möglichkeiten, einen Container in einem Netzwerk zu platzieren: Entweder Sie weisen ihn beim Start zu, oder Sie verbinden ihn mit einem vorhandenen Container. In diesem Fall erstellen Sie zuerst das Netzwerk und fügen dann den MySQL-Container beim Start an.

1. Erstellen Sie das Netzwerk.

    ```bash
    docker network create todo-app
    ```

1. Starten Sie einen MySQL-Container, und fügen Sie ihn dem Netzwerk an. Außerdem definieren Sie einige Umgebungsvariablen, die von der Datenbank zum Initialisieren der Datenbank verwendet werden (weitere Informationen im Abschnitt „Umgebungsvariablen“ in der [MySQL-Docker Hub-Liste](https://hub.docker.com/_/mysql/)). Ersetzen Sie in Windows PowerShell die ` \ `-Zeichen durch `` ` ``-Zeichen.

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Sie sehen auch, dass Sie das Flag `--network-alias` angegeben haben. Dies wird in Kürze erläutert.

    > [!TIP]
    > Sie stellen fest, dass Sie hier den Volumenamen `todo-mysql-data` verwenden und unter `/var/lib/mysql` bereitstellen, wo MySQL Daten speichert. Sie haben jedoch noch nie einen `docker volume create`-Befehl ausgeführt. Docker erkennt, dass Sie ein benanntes Volume verwenden möchten und erstellt daher automatisch eines.

1. Stellen Sie eine Verbindung mit der Datenbank her, und überprüfen Sie diese Verbindung, um zu bestätigen, dass die Datenbank erfolgreich ausgeführt wird.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Wenn Sie zur Eingabe des Kennworts aufgefordert werden, geben Sie **secret** ein. In der MySQL-Shell werden die Datenbanken aufgelistet. Überprüfen Sie, ob die Datenbank `todos` angezeigt wird.

    ```cli
    mysql> SHOW DATABASES;
    ```

    Eine ähnliche Ausgabe wie die folgende sollte angezeigt werden:

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    Sehr gut! Sie verfügen über die `todos`-Datenbank und können diese verwenden.

## <a name="connect-to-mysql"></a>Herstellen einer Verbindung mit MySQL

Da Sie nun wissen, dass MySQL ausgeführt wird, können Sie das System verwenden. Die Frage ist nur: Wie wird es verwendet? Wie finden Sie den Container, wenn Sie einen anderen Container im selben Netzwerk ausführen? (Denken Sie daran, dass jeder Container über eine eigene IP-Adresse verfügt.)

Sie verwenden hierfür den Container [nicolaka/netshoot](https://github.com/nicolaka/netshoot), der *viele* Tools umfasst, die für die Problembehandlung oder das Debuggen von Netzwerkproblemen nützlich sind.

1. Starten Sie einen neuen Container mithilfe des Images `nicolaka/netshoot`. Stellen Sie sicher, dass Sie mit demselben Netzwerk verbunden sind.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. Verwenden Sie innerhalb des Containers den `dig`-Befehl, der ein nützliches DNS-Tool ist. Suchen Sie nach der IP-Adresse für den Hostnamen `mysql`.

    ```bash
    dig mysql
    ```

    Sie erhalten eine Ausgabe wie die folgende:

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    Im Abschnitt „ANSWER SECTION“ wird ein `A`-Datensatz für `mysql` angezeigt, der in `172.23.0.2` aufgelöst wird (Ihre IP-Adresse hat wahrscheinlich einen anderen Wert). Obwohl `mysql` normalerweise kein gültiger Hostname ist, konnte Docker ihn in die IP-Adresse des Containers auflösen, der diesen Netzwerkalias besaß (erinnern Sie sich an das `--network-alias`-Flag, das Sie zuvor verwendet haben?).

    Dies bedeutet, dass Ihre App lediglich eine Verbindung mit einem Host namens `mysql` herstellen muss, um mit der Datenbank kommunizieren zu können. Einfacher geht es nicht.

## <a name="run-your-app-with-mysql"></a>Ausführen der App mit MySQL

Die To-Do-App unterstützt das Festlegen einiger Umgebungsvariablen zum Angeben von MySQL-Verbindungseinstellungen. Es handelt sich hierbei um die folgenden Topologien:

- `MYSQL_HOST`: Dies ist der Hostname für den ausgeführten MySQL-Server
- `MYSQL_USER`: Dies ist der für die Verbindung zu verwendende Benutzername.
- `MYSQL_PASSWORD`: Dies ist das für die Verbindung zu verwendende Kennwort.
- `MYSQL_DB`: Dies ist die Datenbank, die nach dem Herstellen der Verbindung verwendet werden soll.

> [!WARNING]
> **Festlegen von Verbindungseinstellungen über Umgebungsvariablen:** Während die Verwendung von Umgebungsvariablen zum Festlegen der Verbindungseinstellungen in der Entwicklung im Allgemeinen geeignet ist, wird für die Ausführung von Anwendungen in der Produktion dringend davon abgeraten. Weitere Informationen hierzu finden Sie unter [Warm Umgebungsvariablen nicht für geheime Daten verwendet werden sollten](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/).
> Ein sicherer Mechanismus ist die Verwendung der vom Containerorchestrierungsframework bereitgestellten Geheimnisunterstützung. In den meisten Fällen werden diese Geheimnisse als Dateien im laufenden Container bereitgestellt. Sie sehen, dass viele Apps (einschließlich MySQL-Image und To-Do-App) auch Umgebungsvariablen mit einem `_FILE`-Suffix unterstützen, um auf eine Datei zu verweisen, die die Datei enthält.
> Beispielsweise bewirkt das Festlegen der `MYSQL_PASSWORD_FILE`-Variable, dass die App den Inhalt der Datei, auf die verwiesen wird, als Verbindungskennwort verwendet. Docker trägt nicht zur Unterstützung dieser Umgebungsvariablen bei. Ihre App muss nach der Variablen suchen und den Dateiinhalt abrufen.

Nachdem all dies erläutert wurde, können Sie nun Ihren Container bereitstellen, der bereit für die Entwicklung ist.

1. Geben Sie die oben aufgeführten Umgebungsvariablen an, und verbinden Sie den Container mit Ihrem App-Netzwerk (ersetzen Sie in Windows PowerShell die ` \ `-Zeichen durch `` ` ``-Zeichen).

    ```bash hl_lines="3 4 5 6 7"
    docker run -dp 3000:3000 \
      -w /app -v ${PWD}:/app \
      --network todo-app \
      -e MYSQL_HOST=mysql \
      -e MYSQL_USER=root \
      -e MYSQL_PASSWORD=secret \
      -e MYSQL_DB=todos \
      node:12-alpine \
      sh -c "yarn install && yarn run dev"
    ```

1. Wenn Sie sich die Protokolle für den Container (`docker logs <container-id>`) ansehen, sollte eine Meldung angezeigt werden, die angibt, dass die MySQL-Datenbank verwendet wird.

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. Öffnen Sie die App in Ihrem Browser, und fügen Sie Ihrer To-Do-Liste einige Elemente hinzu.

1. Stellen Sie eine Verbindung mit der MySQL-Datenbank her, und prüfen Sie, ob die Elemente in die Datenbank geschrieben werden. Beachten Sie, dass **secret** das Kennwort ist.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    Führen Sie in der MySQL-Shell Folgendes aus:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Natürlich sieht Ihre Tabelle anders aus, da diese Ihre Elemente enthält. Sie sollten jedoch dort angezeigt werden.

Wenn Sie sich die Docker-Erweiterung kurz ansehen, werden Sie feststellen, dass zwei App-Container ausgeführt werden. Es gibt allerdings keinen wirklichen Hinweis darauf, dass diese in einer einzelnen App gruppiert werden. Sie erfahren in Kürze, wie Sie dies verbessern können.

![Docker-Erweiterung mit zwei App-Containern, deren Gruppierung aufgehoben wurde](media/vs-multi-container-app.png)

## <a name="recap"></a>Zusammenfassung

An diesem Punkt verfügen Sie über eine Anwendung, die Ihre Daten nun in einer externen Datenbank speichert, die in einem separaten Container ausgeführt wird. Sie haben etwas über Containernetzwerke gelernt und gesehen, wie die Dienstermittlung mithilfe von DNS ausgeführt werden kann.

Möglicherweise sind Sie anfangs von all den Schritten etwas überwältigt, die zum Starten dieser Anwendung nötig sind. Sie müssen unter anderem ein Netzwerk erstellen, Container starten, alle Umgebungsvariablen angeben und Ports verfügbar machen. Dabei müssen Sie sich also viel merken, und es ist sicherlich noch schwieriger, dies anderen Personen zu erklären.

Im nächsten Abschnitt wird Docker Compose erläutert. Mit Docker Compose können Sie Ihre Anwendungsstapel auf viel einfachere Weise freigeben, und andere können diese mit einem einzelnen (und einfachen) Befehl starten.

## <a name="next-steps"></a>Nächste Schritte

Setzen Sie das Tutorial fort.

> [!div class="nextstepaction"]
> [Verwenden von Docker Compose](use-docker-compose.md)
