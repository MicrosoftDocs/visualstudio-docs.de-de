---
title: 'Docker-Tutorial – Teil 7: Verwenden von Docker Compose'
description: Hier wird beschrieben, wie Sie Docker Compose installieren und verwenden.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f95a4f130e8ad662b3f0eca8f6f7d2162e2d1c7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841717"
---
# <a name="use-docker-compose"></a>Verwenden von Docker Compose

[Docker Compose](https://docs.docker.com/compose/) ist ein Tool, das zum Definieren und Freigeben von Multicontaineranwendungen entwickelt wurde. Mit Compose können Sie eine YAML-Datei erstellen, um die Dienste zu definieren, die Sie mit einem einzigen Befehl starten bzw. beenden können.

Der *große Vorteil* der Verwendung von Compose besteht darin, dass Sie Ihren Anwendungsstapel in einer Datei definieren, diesen im Stammverzeichnis Ihres Projektrepository aufbewahren (jetzt mit Versionskontrolle) und eine andere Person einfach an Ihrem Projekt mitwirken lassen können. Der Benutzer muss lediglich Ihr Repository klonen und die Compose-App starten. In der Tat werden Ihnen möglicherweise einige Projekte auf GitHub/GitLab angezeigt, die genau das tun.

Stellt sich also die Frage, wie Sie am besten beginnen.

## <a name="install-docker-compose"></a>Installieren von Docker Compose

Wenn Sie Docker Desktop unter Windows oder Mac installiert haben, verfügen Sie bereits über Docker Compose. In Play-with-Docker-Instanzen ist Docker Compose ebenfalls schon installiert. Wenn Sie einen Linux-Computer verwenden, müssen Sie Docker Compose mithilfe [dieser Anweisungen](https://docs.docker.com/compose/install/) installieren.

Nach der Installation sollten Sie Folgendes ausführen und Versionsinformationen anzeigen können.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Erstellen der Compose-Datei

1. Erstellen Sie im Stammverzeichnis des App-Projekts eine Datei namens `docker-compose.yml`.

1. In der Compose-Datei beginnen Sie mit dem Definieren der Schemaversion. In den meisten Fällen empfiehlt es sich, die neueste unterstützte Version zu verwenden. Informationen zu den aktuellen Schemaversionen und zur Kompatibilitätsmatrix finden Sie im [Compose-Dateiverweis](https://docs.docker.com/compose/compose-file/).

    ```yaml
    version: "3.7"
    ```

1. Definieren Sie als Nächstes die Liste der Dienste (oder Container), die Sie als Teil Ihrer Anwendung ausführen möchten.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Und jetzt beginnen Sie, nacheinander Dienste in die Compose-Datei zu migrieren.

## <a name="define-the-app-service"></a>Definieren von App Service

Dies ist der Befehl, den Sie zum Definieren des App-Containers verwendet haben (ersetzen Sie in Windows PowerShell die ` \ `-Zeichen durch `` ` ``).

```bash
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

1. Definieren Sie zunächst den Diensteintrag und das Image für den Container. Sie können einen beliebigen Namen für den Dienst auswählen. Der Name wird automatisch zu einem Netzwerkalias, der beim Definieren des MySQL-Diensts nützlich ist.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. In der Regel wird der Befehl in der Nähe der `image`-Definition angezeigt, obwohl es keine Vorgaben für die Reihenfolge gibt. Verschieben Sie ihn also in die Datei.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Migrieren Sie den Teil `-p 3000:3000` des Befehls, indem Sie die `ports` für den Dienst definieren. Sie verwenden hier die [kurze Syntax](https://docs.docker.com/compose/compose-file/#short-syntax-1), es ist jedoch auch eine ausführlichere [lange Syntax](https://docs.docker.com/compose/compose-file/#long-syntax-1) verfügbar.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Migrieren Sie als Nächstes sowohl das Arbeitsverzeichnis (`-w /app`) als auch die Volumezuordnung (`-v ${PWD}:/app`) mithilfe der Definitionen `working_dir` und `volumes`. Volumes verfügen auch über eine [kurze](https://docs.docker.com/compose/compose-file/#short-syntax-3) und [lange](https://docs.docker.com/compose/compose-file/#long-syntax-3) Syntax.

   Ein Vorteil der Docker Compose-Volumedefinitionen ist, dass Sie relative Pfade aus dem aktuellen Verzeichnis verwenden können.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Migrieren Sie schließlich die Umgebungsvariablendefinitionen mithilfe des `environment`-Schlüssels.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>Definieren des MySQL-Diensts

Nun ist es an der Zeit, den MySQL-Dienst zu definieren. Der Befehl, den Sie für diesen Container verwendet haben, lautete wie folgt (ersetzen Sie in Windows PowerShell die ` \ `-Zeichen durch `` ` ``-Zeichen):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Definieren Sie zunächst den neuen Dienst, und nennen Sie ihn `mysql`, damit er automatisch den Netzwerkalias erhält. Geben Sie auch das zu verwendende Image an.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Danach definieren Sie die Volumezuordnung. Wenn Sie den Container mit `docker run` ausgeführt haben, wurde das benannte Volume automatisch erstellt. Dies geschieht jedoch nicht, wenn die Ausführung mit Compose erfolgt. Sie müssen das Volume im Abschnitt `volumes:` der obersten Ebene definieren und dann den Bereitstellungspunkt in der Dienstkonfiguration angeben. Wenn Sie einfach nur den Volumenamen angeben, werden die Standardoptionen verwendet. Es stehen jedoch [viele weitere Optionen zur Verfügung](https://docs.docker.com/compose/compose-file/#volume-configuration-reference).

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Schließlich müssen Sie nur die Umgebungsvariablen angeben.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

Die vollständige `docker-compose.yml`-Datei sollte nun wie folgt aussehen:

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Ausführen des Anwendungsstapels

Da Sie nun über die `docker-compose.yml`-Datei verfügen, können Sie sie starten.

1. Stellen Sie zunächst sicher, dass keine anderen Kopien der App und der Datenbank ausgeführt werden (`docker ps` und `docker rm -f <ids>`).

1. Starten Sie den Anwendungsstapel mit dem Befehl `docker-compose up`. Fügen Sie das `-d`-Flag hinzu, um alles im Hintergrund auszuführen. Alternativ können Sie auch mit der rechten Maustaste auf die Compose-Datei und dann auf die **Compose Up**-Option (Compose starten) für die VS Code-Seitenleiste klicken. 

    ```bash
    docker-compose up -d
    ```

    Bei Ausführung dieser Option sollte in etwa folgende Ausgabe angezeigt werden:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Sie werden feststellen, dass das Volume und ein Netzwerk erstellt wurden. Standardmäßig erstellt Docker Compose automatisch ein Netzwerk speziell für den Anwendungsstapel (aus diesem Grund haben Sie keinen in der Compose-Datei definiert).

1. Überprüfen Sie die Protokolle mit dem Befehl `docker-compose logs -f`. Sie sehen, dass sich die Protokolle der einzelnen Dienste in einem einzigen Stream befinden. Dies ist äußerst nützlich, wenn Sie auf zeitbezogene Probleme achten möchten. Das `-f`-Flag „folgt“ dem Protokoll, sodass Sie eine Liveausgabe erhalten, wenn es generiert wird.

    Falls bisher noch nichts angezeigt wurde, sieht die Ausgabe jetzt etwa wie folgt aus:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Der Dienstname wird am Anfang der Zeile (oft in Farben) angezeigt, um Meldungen unterscheiden zu können. Wenn Sie die Protokolle für einen bestimmten Dienst anzeigen möchten, können Sie den Dienstnamen am Ende des „logs“-Befehls (z. B. `docker-compose logs -f app`) hinzufügen.

    > [!TIP]
    > **Warten auf die Datenbank vor dem Start der App:** Wenn die App gestartet wird, wartet sie, bis MySQL tatsächlich auch ausgeführt wird, bevor eine Verbindung hergestellt wird. Docker verfügt über keine integrierte Unterstützung, um zu warten, bis ein anderer Container vollständig betriebsbereit ist, ausgeführt wird und die gewünschten Aktionen durchführen kann, bevor ein anderer Container gestartet wird. Für Node-basierte Projekte können Sie die [wait-port](https://github.com/dwmkerr/wait-port)-Abhängigkeit verwenden. Ähnliche Projekte sind für andere Sprachen und Frameworks vorhanden.

1. An diesem Punkt sollten Sie Ihre App ordnungsgemäß öffnen und ausführen können. Außerdem: Sie verwenden nur einen einzigen Befehl.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Anzeigen des App-Stapels in der Docker-Erweiterung

Mithilfe von „cog“ und „group by“ können Sie die Gruppierungsoptionen im Zusammenhang mit der Docker-Erweiterung ändern. In diesem Fall möchten Sie Container nach dem Compose-Projektnamen gruppieren:

![VS-Erweiterung mit Compose](media/vs-app-project-collapsed.png)

Wenn Sie die Netzwerkoption erweitern, werden die beiden Container angezeigt, die Sie in der Compose-Datei definiert haben.

![VS-Erweiterung mit erweitertem Compose-Eintrag](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Beenden der Vorgänge

Wenn Sie alle Vorgänge beenden möchten, können Sie einfach `docker-compose down` ausführen oder mit der rechten Maustaste auf die Anwendung in der Containerliste in der VS Code-Docker-Erweiterung und dann auf **Compose Down** (Compose beenden) klicken. Die Container werden angehalten, und das Netzwerk wird entfernt.

> [!WARNING]
> **Entfernen von Volumes:** Wenn Sie `docker-compose down` ausführen, werden benannte Volumes in Ihrer Compose-Datei standardmäßig NICHT entfernt. Wenn Sie die Volumes entfernen möchten, müssen Sie das `--volumes`-Flag hinzufügen.

Nach dem Herunterfahren können Sie zu einem anderen Projekt wechseln, `docker-compose up` ausführen und etwas zu diesem Projekt beitragen. Einfacher geht es nicht.

## <a name="recap"></a>Zusammenfassung

In diesem Abschnitt haben Sie mehr über Docker Compose erfahren. Außerdem wurde erläutert, wie dieses Tool dabei hilft, das Definieren und Freigeben von Anwendungen mit mehreren Diensten erheblich zu vereinfachen. Sie haben eine Compose-Datei erstellt, indem Sie die von Ihnen verwendeten Befehle in das entsprechende Compose-Format übersetzt haben.

An dieser Stelle beginnt die Zusammenfassung des Tutorials. Es gibt jedoch einige bewährte Methoden für die Imageerstellung, über die Sie sich informieren sollten, da es ein großes Problem mit dem Dockerfile gibt, das Sie bereits verwendet haben. Nehmen Sie sich die Zeit, und sehen Sie sich das mal an.

## <a name="next-steps"></a>Nächste Schritte

Setzen Sie das Tutorial fort.

> [!div class="nextstepaction"]
> [Bewährte Methoden für die Imageerstellung](image-building-best-practices.md)
