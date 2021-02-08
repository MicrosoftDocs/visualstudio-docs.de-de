---
title: 'Docker-Tutorial – Teil 4: Beibehalten von Daten'
description: In diesem Tutorial erfahren Sie, wie Sie Daten in einer Datenbank beibehalten und Verzeichnisse in einem Container freigeben, indem Sie ein Volume einbinden.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9ee4109c888888d2dee36804a178f7db8d41753f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841769"
---
# <a name="persist-your-data"></a> Beibehalten von Daten

Falls es Ihnen noch nicht aufgefallen ist: Die Aufgabenliste wird jedes Mal bereinigt, wenn Sie den Container starten. Warum? Im folgenden wird erläutert, wie der Container funktioniert.

## <a name="the-containers-filesystem"></a>Dateisystem des Containers

Wenn ein Container ausgeführt wird, werden die verschiedenen Ebenen eines Images für das Dateisystem verwendet. Jeder Container verfügt außerdem über einen eigenen „temporären Speicherbereich“ zum Erstellen, Aktualisieren oder Entfernen von Dateien. Änderungen werden nicht in anderen Containern angezeigt, *selbst wenn* sie dasselbe Image verwenden.

### <a name="see-this-in-practice"></a>Praxisbeispiel

Im Folgenden erstellen Sie zwei Container und jeweils eine Datei in diesen Containern, um dies in Aktion zu sehen. Dann werden Sie sehen, dass die in einem Container erstellten Dateien nicht in einem anderen Container verfügbar sind.

1. Starten Sie einen `ubuntu`-Container, der eine Datei namens `/data.txt` mit einer zufälligen Zahl zwischen 1 bis 10.000 enthalten soll.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Mit diesem Befehl starten Sie eine Bash-Shell und rufen zwei Befehle auf (daher enthält der Befehl `&&`). Im ersten Abschnitt wird eine einzelne zufällige Zahl ausgewählt und in `/data.txt` geschrieben. Mit dem zweiten Befehl wird lediglich eine Datei überwacht, damit der Container weiter ausgeführt wird.

1. Überprüfen Sie, ob Sie die Ausgabe anzeigen können, indem Sie `exec` zum Abrufen des Containers verwenden. Öffnen Sie hierzu die VS Code-Erweiterung, und klicken Sie auf die Option **Attach Shell** (Shell anfügen). Dadurch wird `exec` zum Öffnen einer Shell im Container innerhalb des VS Code-Terminals verwendet.

    ![Öffnen der CLI im Ubuntu-Container mit VS Code](media/attach_shell.png)

    Daraufhin wird Ihnen ein Terminal angezeigt, das eine Shell im Ubuntu-Container ausführt. Führen Sie den folgenden Befehl aus, um den Inhalt der `/data.txt`-Datei anzuzeigen. Schließen Sie dieses Terminal anschließend.

    ```bash
    cat /data.txt
    ```

    Wenn Sie die Befehlszeile bevorzugen, können Sie stattdessen den Befehl `docker exec` verwenden. Sie müssen die ID des Containers abrufen (verwenden Sie hierzu `docker ps`), und rufen Sie dann den Inhalt mit dem folgenden Befehl ab.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Ihnen sollte nun eine zufällige Zahl angezeigt werden.

1. Als Nächstes starten Sie einen weiteren `ubuntu`-Container (dasselbe Image). Ihnen sollte auffallen, dass Sie nicht über dieselbe Datei verfügen.

    ```bash
    docker run -it ubuntu ls /
    ```

    Beachten Sie außerdem, dass keine `data.txt`-Datei vorliegt. Das liegt daran, dass die Datei nur für den ersten Container in den temporären Speicher geschrieben wurde.

1. Entfernen Sie den ersten Container mithilfe des `docker rm -f`-Befehls.

## <a name="container-volumes"></a>Containervolumes

In der letzten Übung haben Sie erfahren, dass jeder Container bei jedem Start mit der Imagedefinition beginnt. Zwar können Container Dateien erstellen, aktualisieren und löschen, jedoch werden diese Änderungen verworfen, wenn der Container entfernt wird und alle Änderungen in diesem Container isoliert sind. Mit Volumes können Sie das ändern.

[Volumes](https://docs.docker.com/storage/volumes/) bieten die Möglichkeit, eine Verbindung mit spezifischen Dateisystempfaden des Containers zurück zum Hostcomputer herzustellen. Wenn ein Verzeichnis im Container eingebunden wird, werden die Änderungen in diesem Verzeichnis auch auf dem Hostcomputer widergespiegelt. Wenn Sie dasselbe Verzeichnis nach einem Neustart des Containers einbinden, stehen Ihnen dieselben Dateien zur Verfügung.

Es gibt zwei Haupttypen von Volumes. Sie werden im Laufe der Zeit beide verwenden, doch hier beginnen Sie mit **benannten Volumes**.

## <a name="persist-your-todo-data"></a>Speichern von Daten für die Aufgabenliste

Die Aufgabenlisten-App speichert Daten standardmäßig in einer [SQLite-Datenbank](https://www.sqlite.org/index.html) unter `/etc/todos/todo.db`. Sie benötigen keine Vorkenntnisse über SQLite. Es handelt sich dabei lediglich um eine relationale Datenbank, bei der alle Daten in einer einzigen Datei gespeichert werden. Dies ist zwar nicht die beste Lösung für umfangreiche Anwendungen, funktioniert jedoch hervorragend für kleine Demos. Das Wechseln zu einer tatsächlichen Datenbank-Engine wird später erläutert.

Wenn Sie die Datei auf dem Hostcomputer speichern und für den nächsten Container zur Verfügung stellen können, sollte der Container dort fortfahren können, wo der vorherige Container aufgehört hat, da es sich bei der Datenbank um eine einzelne Datei handelt. Indem Sie ein Volume erstellen und an das Verzeichnis anfügen (dies wird oft als „Einbindung“ bezeichnet), können Sie die Daten speichern. Wenn der Container in die Datei `todo.db` schreibt, wird dies auf dem Host im Volume gespeichert.

Wie bereits erwähnt, verwenden Sie ein **benanntes Volume**. Sie können sich ein benanntes Volume einfach als Bucket mit Daten vorstellen. Docker verwaltet den physischen Speicherort auf dem Datenträger, und Sie müssen sich lediglich den Namen des Volumes merken. Jedes Mal, wenn Sie das Volume verwenden, stellt Docker sicher, dass die richtigen Daten bereitgestellt werden.

1. Erstellen Sie mithilfe des Befehls `docker volume create` ein Volume.

    ```bash
    docker volume create todo-db
    ```

1. Beenden Sie den Container der Aufgabenlisten-App wieder in der Docker-Ansicht (oder mit `docker rm -f <id>`), da er weiterhin ausgeführt wird, ohne das persistente Volume zu verwenden.

1. Starten Sie den Container der Aufgabenlisten-App, aber fügen Sie das Flag `-v` hinzu, um eine Volumebereitstellung anzugeben. Sie verwenden das benannte Volume und binden es in `/etc/todos` ein, wodurch alle in dem Pfad erstellten Dateien erfasst werden.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Sobald der Container gestartet wurde, öffnen Sie die App, und fügen Sie einige Elemente zur Aufgabenliste hinzu.

    ![Zur Aufgabenliste hinzugefügte Elemente](media/items-added.png)

1. Entfernen Sie den Container für die Aufgabenlisten-App. Verwenden Sie die Docker-Ansicht oder `docker ps`, um die ID abzurufen, und dann `docker rm -f <id>`, um sie zu entfernen.

1. Starten Sie mithilfe desselben Befehls, den Sie oben verwendet haben, einen neuen Container.

1. Öffnen Sie die App. Ihnen sollten weiterhin die Elemente in Ihrer Liste angezeigt werden.

1. Entfernen Sie den Container, wenn Sie damit fertig sind, Ihre Liste zu begutachten.

Gut gemacht. Sie wissen nun, wie Sie Daten speichern können.

> [!TIP]
> Während benannte Volumes und Bindungsbereitstellungen (die in Kürze erläutert werden) die zwei Haupttypen der Volumes darstellen, die von der Standardinstallation der Docker-Engine unterstützt werden, stehen viele Treiber-Plug-Ins für Volumes zur Verfügung, um beispielsweise NFS, SFTP, NetApp und mehr zu unterstützen. Das ist insbesondere Wichtig, wenn Sie damit beginnen, Container mit Swarm, Kubernetes usw. auf mehreren Hosts in einer Clusterumgebung auszuführen.

## <a name="dive-into-your-volume"></a>Untersuchen des Volumes

Oft wird die Frage gestellt „Wo speichert Docker die Daten *tatsächlich*, wenn ich ein benanntes Volume verwende?“. Dies können Sie mithilfe des Befehls `docker volume inspect` in Erfahrung bringen.

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

`Mountpoint` entspricht dem tatsächlichen Speicherort auf dem Datenträger, an dem die Daten gespeichert werden. Beachten Sie, dass Sie auf den meisten Computern über Stammzugriffsberechtigungen verfügen müssen, um auf dieses Verzeichnis des Hosts zuzugreifen. Sie können sich jedoch sicher sein, dass es sich dabei um den Speicherort handelt.

> [!NOTE]
> **Direkter Zugriff auf Volumedaten in Docker Desktop:** Wenn Sie Docker Desktop ausführen, werden die Docker-Befehle tatsächlich in einer kleinen VM auf Ihrem Computer ausgeführt. Wenn Sie die tatsächlichen Inhalte des *Mountpoint*-Verzeichnisses (Bereitstellungspunkt) untersuchen möchten, müssen Sie zunächst auf die VM zugreifen. In WSL 2 befindet diese sich in einer WSL 2-Verteilung, auf die über den Datei-Explorer zugegriffen werden kann.

## <a name="recap"></a>Zusammenfassung

Sie verfügen nun über eine funktionierende Anwendung, die neu gestartet werden kann. Diese können Sie Ihren Investoren präsentieren und hoffen, dass sie Ihre Vision unterstützen.

Allerdings haben Sie auch gelernt, dass das Neuerstellen von Images für jede Änderung einige Zeit beansprucht. Also stellen Sie sich bestimmt die Frage, ob es nicht einen besseren Weg gibt, um Änderungen vorzunehmen. Mit den zuvor erwähnten Bindungsbereitstellungen gibt es eine bessere Vorgehensweise. Diese sehen Sie sich als Nächstes an.

## <a name="next-steps"></a>Nächste Schritte

Tutorial fortsetzen!

> [!div class="nextstepaction"]
> [Verwenden von Bindungsbereitstellungen](use-bind-mounts.md)
