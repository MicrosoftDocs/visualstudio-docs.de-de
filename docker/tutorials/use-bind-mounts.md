---
title: 'Docker-Tutorial – Teil 5: Verwenden von Bindungsbereitstellungen'
description: In diesem Tutorial wird beschrieben, wie Bindungsbereitstellungen verwendet werden, um den Bereitstellungspunkt auf dem Host zu steuern.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 57cb56d0d9a93d0f11e4047f6e25b64841c47e93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841678"
---
# <a name="use-bind-mounts"></a>Verwenden von Bindungsbereitstellungen

Im vorherigen Kapitel haben Sie Informationen zu einem **benannten Volume** erhalten und eines verwendet, um die Daten in Ihrer Datenbank aufzubewahren. Benannte Volumes eignen sich hervorragend, wenn Sie Daten einfach nur speichern möchten, da Sie sich dabei keine Gedanken darüber machen müssen, *wo* die Daten gespeichert werden.

Mithilfe von **Bindungsbereitstellungen** können Sie den exakten Bereitstellungspunkt auf dem Host bestimmen. So können Sie Daten aufbewahren, oft wird diese Möglichkeit aber auch dazu verwendet, zusätzliche Daten in Containern bereitzustellen. Wenn Sie an einer Anwendung arbeiten, können Sie eine Bindungsbereitstellung verwenden, um Quellcode in Container einzubinden, damit Codeänderungen erkannt werden können und darauf reagiert werden kann und damit Sie die Änderungen sofort sehen.

Für Node-basierte Anwendungen eignet sich das Tool [nodemon](https://npmjs.com/package/nodemon) ideal für die Erkennung von Dateiänderungen und ein anschließendes Neustarten der Anwendung. In den meisten anderen Sprachen und Frameworks stehen ähnliche Tools zur Verfügung.

## <a name="quick-volume-type-comparisons"></a>Schnellvergleich von Volumetypen

Bindungsbereitstellungen und benannte Volumes sind die zwei Haupttypen von Volumes, die über die Docker-Engine zur Verfügung stehen. Es stehen jedoch auch weitere Volumetreiber zur Verfügung, um andere Anwendungsfälle zu unterstützen (z B. [SFTP](https://github.com/vieux/docker-volume-sshfs), [Ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/) und [S3](https://github.com/elementar/docker-s3-volume)).

| Eigenschaft | Benannte Volumes | Binden von Bereitstellungen |
| -------- | ------------- | ----------- |
| Hoststandort | Wird von Docker ausgewählt | Wird von Ihnen bestimmt |
| Beispiel für Volumebereitstellung (mithilfe von `-v`) | my-volume:/usr/local/data | /path/to/data:/usr/local/data |
| Auffüllen des neuen Volumes mit Containerinhalten | Ja | Nein |
| Unterstützung für Volumetreiber | Ja | Nein |

## <a name="start-a-dev-mode-container"></a>Starten eines Containers im Entwicklermodus

Wenn Sie einen Container so ausführen möchten, dass ein Entwicklungsworkflow unterstützt wird, müssen Sie Folgendes tun:

- Einbinden des Quellcodes in den Container
- Installieren aller Abhängigkeiten einschließlich der „dev“-Abhängigkeiten
- Starten des nodemon-Tools zur Erkennung möglicher Änderungen im Dateisystem

1. Sorgen Sie dafür, dass keine zuvor genutzten `getting-started`-Container ausgeführt werden.

1. Führen Sie den folgenden Befehl in Windows PowerShell aus, und ersetzen Sie dabei die ` \ `-Zeichen durch `` ` ``. Sie erfahren später, was genau hier geschieht:

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000`: wie zuvor. Führen Sie den Befehl im Hintergrund (getrennter Modus) aus, und erstellen Sie eine Portzuordnung.
    - `-w /app` legt das Arbeitsverzeichnis oder das aktuelle Verzeichnis fest, in dem der Befehl ausgeführt wird.
    - `-v ${PWD}:/app` Hier wird eine Bindungsbereitstellung für das aktuelle Verzeichnis vom Host im Container in das `/app`-Verzeichnis durchgeführt.
    - `node:12-alpine`: Dies ist das zu verwendende Image. Beachten Sie, dass es sich hierbei um das Basisimage für Ihre App aus dem Dockerfile handelt.
    - `sh -c "yarn install && yarn run dev"`: der Befehl. Hier wird mithilfe von `sh` (alpine verfügt nicht über `bash`) eine Shell gestartet und `yarn install` ausgeführt, um *alle* Abhängigkeiten zu installieren und dann `yarn run dev` auszuführen. Wenn Sie `package.json` ansehen, stellen Sie fest, dass das `dev`-Skript `nodemon` startet.

1. Mithilfe von `docker logs -f <container-id>` können Sie sich die Protokolle ansehen. Wenn Folgendes angezeigt wird, sind Sie soweit:

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    Wenn Sie die Untersuchung der Protokolle abgeschlossen haben, können Sie sie schließen, indem Sie `Ctrl`+`C` drücken.

1. Nehmen Sie nun eine Änderung an der App vor. Ändern Sie in der `src/static/js/app.js`-Datei die Schaltfläche **Element hinzufügen** so, dass nur noch **Hinzufügen** angezeigt wird. Diese Änderung findet in Zeile 109 statt.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Aktualisieren Sie die Seite einfach, oder öffnen Sie sie neu, dann sollte die Änderung im Browser beinahe sofort wiedergegeben werden. Möglicherweise dauert es einige Sekunden, bis der Node-Server neu gestartet wurde. Wenn Sie also eine Fehlermeldung erhalten, aktualisieren Sie die Seite einfach nach einigen Sekunden noch mal.

    ![Screenshot: Aktualisierte Bezeichnung für die Schaltfläche „Hinzufügen“](media/updated-add-button.png)

1. Auf Wunsch können Sie beliebige andere Änderungen vornehmen. Wenn Sie soweit sind, halten Sie den Container an, und erstellen Sie Ihr neues Image mithilfe von `docker build -t getting-started .`.

Die Verwendung von Bindungsbereitstellungen ist *sehr* gängig bei lokalen Entwicklungssetups. Der Vorteil besteht darin, dass der Entwicklungscomputer nicht über Installationen aller Buildtools und Umgebungen verfügen muss. Die Entwicklungsumgebung wird mit einem einzigen `docker run`-Befehl gepullt und ist sofort einsatzbereit. In einem weiteren Schritt werden Sie weitere Informationen zu Docker Compose erhalten. Dies unterstützt Sie beim Vereinfachen Ihrer Befehle, denn Sie erhalten aktuell bereits viele Flags.

## <a name="recap"></a>Zusammenfassung

Bisher können Sie Ihre Datenbank speichern und schnell auf die Anforderungen und Wünsche Ihrer Investoren und Gründer reagieren. Das ist sehr gut. Aber wissen Sie was? Sie haben großartige Neuigkeiten erfahren.

**Ihr Projekt soll zukünftig weiter ausgebaut werden.**

Dazu müssen Sie Ihre Datenbank von SQLite zu einer Lösung migrieren, die sich noch etwas besser skalieren lässt, um sie für die Produktion vorzubereiten. Aus Gründen der Einfachheit verwenden Sie weiterhin eine relationale Datenbank, ändern Ihre Anwendung jedoch so, dass MySQL verwendet wird. Wie können Sie jedoch MySQL ausführen? Wie ermöglichen Sie die Kommunikation zwischen den Containern? In einem weiteren Teil erhalten Sie Informationen dazu.

## <a name="next-steps"></a>Nächste Schritte

Setzen Sie das Tutorial fort.

> [!div class="nextstepaction"]
> [Apps mit mehreren Containern](multi-container-apps.md)