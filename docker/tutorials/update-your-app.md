---
title: 'Docker-Tutorial – Teil 2: Aktualisieren Ihrer App'
description: Beschreibt, wie eine Docker-App aktualisiert wird.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: df2102c38250aa5c1bda52b4324cba808501db3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841743"
---
# <a name="update-the-app"></a>Aktualisieren der App

Als kleine Funktionsanforderung wurden Sie vom Produktteam aufgefordert, den „leeren Text“ zu ändern, wenn keine Aufgabenlistenelemente vorhanden sind. Es soll Folgendes angezeigt werden:

> You have no todo items yet! (Es sind noch keine Aufgabenelemente vorhanden!) Add one above! (Fügen Sie oben ein Element hinzu!)

Ganz einfach, nicht wahr? Nehmen wir die Änderung vor.

## <a name="update-the-source-code"></a>Aktualisieren des Quellcodes

1. Aktualisieren Sie in der Datei `src/static/js/app.js` Zeile 56, um den neuen „leeren Text“ zu verwenden.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Erstellen Sie die aktualisierte Version des Images mit dem gleichen Befehl, den Sie zuvor verwendet haben.

    ```bash
    docker build -t getting-started .
    ```

1. Starten Sie einen neuen Container mit dem aktualisierten Code.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**Seltsam.** Es wurde möglicherweise ein Fehler wie dieser angezeigt (die IDs unterscheiden sich):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Was ist passiert? Der neue Container konnte nicht gestartet werden, weil der alte Container noch ausgeführt wird. Der Grund für dieses Problem liegt darin, dass dieser Container Port 3000 des Hosts verwendet und nur ein Prozess auf dem Computer (Container eingeschlossen) auf einen bestimmten Port lauschen kann. Um dieses Problem zu beheben, entfernen Sie den alten Container.

## <a name="replace-the-old-container"></a>Ersetzen des alten Containers

Um einen Container zu entfernen, muss er zuerst beendet werden. Nachdem er beendet wurde, kann er entfernt werden. Sie haben zwei Möglichkeiten, den alten Container zu entfernen. Sie können den Pfad wählen, der Ihnen am besten gefällt.

### <a name="remove-a-container-using-the-cli"></a>Entfernen eines Containers mithilfe der CLI

1. Verwenden Sie den Befehl `docker ps`, um die ID des Containers abzurufen.

    ```bash
    docker ps
    ```

1. Verwenden Sie den Befehl `docker stop`, um den Container zu beenden.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Nachdem der Container beendet wurde, können Sie ihn mithilfe des Befehls `docker rm` entfernen.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Sie können einen Container mit einem einzigen Befehl beenden und entfernen, indem Sie dem Befehl `docker rm` das Flag „force“ hinzufügen. Beispiel: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-view"></a>Entfernen eines Containers mithilfe der Docker-Ansicht

Wenn Sie die VS Code-Erweiterung öffnen, können Sie einen Container mit zwei Mausklicks entfernen! Dies ist sicherlich viel einfacher, als nach der Container-ID zu suchen und den Container zu entfernen.

1. Navigieren Sie bei geöffneter Erweiterung zum Container, und klicken Sie mit der rechten Maustaste.

1. Klicken Sie auf die Option **Entfernen**.

1. Bestätigen Sie den Entfernungsvorgang, und schon sind Sie fertig!

![Docker-Ansicht: Entfernen eines Containers](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Starten des aktualisierten App-Containers

1. Starten Sie nun Ihre aktualisierte App.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Aktualisieren Sie Ihren Browser unter [http://localhost:3000](http://localhost:3000). Der aktualisierte Hilfetext sollte angezeigt werden!

![Aktualisierte Anwendung mit aktualisiertem „leeren Text“](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Zusammenfassung

Während Sie ein Update erstellt haben, sind Ihnen vielleicht zwei Dinge aufgefallen:

- Alle zuvor vorhandenen Elemente in der Aufgabenliste sind nicht mehr vorhanden! Das ist keine gute App! Darüber werden wir in Kürze sprechen.
- Für eine so kleine Änderung waren *zahlreiche* Schritte erforderlich. In einem späteren Abschnitt erfahren Sie, wie Sie Codeaktualisierungen realisieren können, ohne bei jeder Änderung einen neuen Container erneut erstellen und starten zu müssen.

Bevor Sie sich mit Persistenz vertraut machen, werden Sie schnell erfahren, wie Sie diese Images mit anderen Benutzern teilen können.

## <a name="next-steps"></a>Nächste Schritte

Tutorial fortsetzen!

> [!div class="nextstepaction"]
> [Freigeben der App](share-your-app.md)
