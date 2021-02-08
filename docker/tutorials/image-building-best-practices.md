---
title: 'Docker-Tutorial – Teil 8: Imageschichten'
description: Hier erfahren Sie, wie Sie Imageschichten in Docker-Images untersuchen und verwalten.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8913c558c2860599fbfaaba03fa466d11931a528
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837956"
---
# <a name="image-layering"></a>Imageschichten

Wussten Sie, dass Sie sich ansehen können, aus welchen Schichten ein Image besteht? Mithilfe des `docker image history`-Befehls können Sie den Befehl anzeigen, der verwendet wurde, um die einzelnen Schichten eines Images zu erstellen.

1. Verwenden Sie den `docker image history`-Befehl, damit die Schichten des `getting-started`-Images angezeigt werden, das Sie zuvor im Tutorial erstellt haben.

    ```bash
    docker image history getting-started
    ```

    Sie sollten eine Ausgabe erhalten, die in etwa wie folgt aussieht (Datumsangaben/IDs unterscheiden sich möglicherweise).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Jede der Zeilen steht für eine Schicht des Images. Die Anzeige hier zeigt die Basis ganz unten, die neueste Schicht wird ganz oben angezeigt. Auf die gleiche Weise können Sie sich auch schnell die Größe der einzelnen Schichten ansehen, was bei der Diagnose großer Images hilft.

1. Wie Sie sehen können, sind mehrere der Zeilen gekürzt. Wenn Sie das `--no-trunc`-Flag hinzufügen, wird die vollständige Ausgabe angezeigt. Sie verwenden also ein gekürztes Flag zum Abrufen der ungekürzten Ausgabe.

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Zwischenspeichern von Schichten

Da Sie sich nun angesehen haben, wie Sie die einzelnen Schichten eines Images anzeigen können, können Sie davon eine wichtige Erkenntnis ableiten, mit der Sie die Zeit für die Erstellung Ihrer Containerimages verkürzen können.

> Sobald eine Schicht geändert wird, müssen alle Schichten, die sich unter dieser befinden, ebenfalls neu erstellt werden.

Sehen Sie sich das verwendete Dockerfile noch mal an.

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Wenn Sie sich die Ausgabe des Imageverlaufs ansehen, können Sie feststellen, dass jeder Befehl im Dockerfile zu einer neuen Schicht im Image wird. Möglicherweise erinnern Sie sich, dass die YARN-Abhängigkeiten bei Änderungen am Image neu installiert werden mussten. Gibt es eine Möglichkeit, dies zu beheben? Es ergibt keinen Sinn, diesen Aufwand für jedes Erstellen für dieselben Abhängigkeiten zu betreiben.

Sie können dies beheben, indem Sie Ihr Dockerfile umstrukturieren, sodass das Zwischenspeichern der Abhängigkeiten unterstützt wird. Bei Node-basierten Anwendungen sind diese Abhängigkeiten in der `package.json`-Datei definiert. Was wäre also, wenn Sie zuerst nur diese Datei kopieren, die Abhängigkeiten installieren und *dann* alles Restliche kopieren? In diesem Fall erstellen Sie die YARN-Abhängigkeiten nur neu, wenn eine Änderung an `package.json` vorgenommen wurde. Ergibt das Sinn?

1. Aktualisieren Sie das Dockerfile, damit zuerst `package.json` kopiert wird, installieren Sie dann die Abhängigkeiten, und kopieren Sie dann alles Restliche.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Erstellen Sie mithilfe von `docker build` ein neues Image.

    ```bash
    docker build -t getting-started .
    ```

    Es sollte in etwa folgende Ausgabe angezeigt werden:

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Sie können feststellen, dass alle Schichten neu erstellt wurden. Das ist perfekt, da Sie doch einige Änderungen am Dockerfile vorgenommen haben.

1. Nehmen Sie nun eine Änderung an der `src/static/index.html`-Datei vor, ändern Sie beispielsweise `<title>` in „The Awesome Todo App“.

1. Erstellen Sie nun mithilfe von `docker build` das Docker-Image noch mal. Dieses Mal sollte Ihre Ausgabe etwas anders aussehen.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    Vor allem sollten Sie jedoch feststellen, dass der Build VIEL schneller erfolgt ist. Außerdem können Sie feststellen, dass die Schritte 1–4 alle `Using cache` aufweisen. Sehr gut. Sie verwenden den Buildzwischenspeicher. Push- und Pullvorgänge für dieses Image sowie Aktualisierungen können ebenfalls viel schneller ausgeführt werden. Das ist sehr gut.

## <a name="multi-stage-builds"></a>Mehrstufige Builds

Obwohl dieses Thema im Rahmen dieses Tutorials nicht im Detail behandelt werden soll, handelt es sich bei mehrstufigen Builds um ein unglaublich leistungsfähiges Tool, das die Verwendung mehrerer Stufen für das Erstellen eines Images unterstützt. Daraus entstehen mehrere Vorteile:

- Abgrenzen von Abhängigkeiten zur Buildzeit von Laufzeitabhängigkeiten
- Reduzieren der Imagegesamtgröße, indem *nur* geliefert wird, was die App für ihre Ausführung benötigt

### <a name="maventomcat-example"></a>Maven/Tomcat-Beispiel

Wenn Java-basierte Anwendungen erstellt werden, ist ein JDK erforderlich, um den Quellcode in Java-Bytecode zu kompilieren. Dieses JDK ist jedoch nicht für die Produktion erforderlich. Außerdem verwenden Sie möglicherweise Tools wie Maven oder Gradle für die Erstellung der App.
Diese sind aber ebenfalls nicht für Ihr endgültiges Image erforderlich. Mehrstufige Builds unterstützen Sie hierbei.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

In diesem Beispiel wird eine Stufe (namens `build`) verwendet, um den tatsächlichen Java-Buildvorgang mithilfe von Maven durchzuführen. Die zweite Stufe (ab `FROM tomcat`) kopiert Dateien aus der `build`-Stufe. Beim endgültigen Image handelt es sich nur um die letzte Stufe, die erstellt wird. Diese kann jedoch mithilfe des `--target`-Flags überschrieben werden.

### <a name="react-example"></a>React-Beispiel

Für die Erstellung von React-Anwendungen benötigen Sie eine Node-Umgebung, um z. B. den JS-Code (in der Regel JSX) und SASS-Stylesheets in statische HTML-, JS- und CSS-Sprache zu kompilieren. Wenn Sie kein serverseitiges Rendering vornehmen, benötigen Sie auch keine Node-Umgebung für den Produktionsbuild. Warum stellen Sie die statischen Ressourcen nicht einfach in einem statischen nginx-Container bereit?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

Hier verwenden Sie ein `node:12`-Image, um die Erstellung durchzuführen, was die Zwischenspeicherung von Stufen erhöht. Danach kopieren Sie die Ausgabe in einen nginx-Container. Beeindruckend, nicht?

## <a name="recap"></a>Zusammenfassung

Mit Informationen dazu, wie Images strukturiert sind, können Sie Images schneller und mit weniger Änderungen erstellen und bereitstellen. Mehrstufige Builds ermöglichen es Ihnen außerdem, die Imagegesamtgröße zu reduzieren und die letztendliche Sicherheit des Containers zu erhöhen, indem Buildzeitabhängigkeiten von Laufzeitabhängigkeiten abgegrenzt werden.

## <a name="next-steps"></a>Nächste Schritte

Setzen Sie das Tutorial fort.

> [!div class="nextstepaction"]
> [Bereitstellen in der Cloud](deploy-to-cloud.md)