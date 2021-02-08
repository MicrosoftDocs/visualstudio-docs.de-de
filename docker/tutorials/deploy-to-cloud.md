---
title: 'Docker-Tutorial – Teil 9: Bereitstellen in der Cloud'
description: Hier erfahren Sie mehr über das Bereitstellen einer Docker-App zum Hosting in einem Clouddienst.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 3167dd58a593a426644c3658fbd660f517e10b39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837982"
---
# <a name="deploy-to-the-cloud"></a>Bereitstellen in der Cloud

Nachdem Sie Ihre App lokal ausgeführt haben, können Sie sich Gedanken über die Ausführung in der Cloud machen, damit andere Benutzer darauf zugreifen und sie verwenden können. Zu diesem Zweck verwenden Sie Docker-Kontexte. Ein Kontext ist der Ort, an dem Sie derzeit mit Containern arbeiten. Zurzeit verfügen Sie nur über Ihren „Standardkontext“, sodass Sie einen Cloudkontext hinzufügen und Ihre App darin bereitstellen müssen.

## <a name="create-your-cloud-context"></a>Erstellen des Cloudkontexts

1. Sie können zunächst den Abschnitt „Kontexte“ des Docker-Panels anzeigen, um herauszufinden, über welche Kontexte Sie verfügen:

   ![Nur Standardkontext wird angezeigt](media/defaultcontext.png)

Lediglich der Standardkontext für lokale Arbeiten sollte angezeigt werden.

1. Für die Bereitstellung in der Cloud müssen Sie einen neuen ACI-Kontext erstellen. Hierzu benötigen Sie aber zunächst die Azure-Kontoerweiterung für die Authentifizierung bei Azure.

   ![Hinzufügen der Azure-Erweiterung](media/addazureextension.png)

Falls Sie noch nicht über ein Konto verfügen, müssen Sie ein Azure-Konto einrichten.

1. Nun können Sie den neuen ACI-Kontext erstellen. Klicken Sie hierzu im Bereich **Kontexte** der Docker-Ansicht auf die Schaltfläche mit dem Pluszeichen.

   ![Erstellen Ihres ACI-Kontexts](media/createnewcontext.png)

Sie werden daraufhin gefragt, unter welcher Ressourcengruppe Sie diese Container ausführen möchten. Wählen Sie entweder mithilfe der Pfeiltasten eine vorhandene Gruppe aus, oder verwenden Sie die Standardoption, um die neue Gruppe zu verwenden.

![Auswählen der Ressourcengruppe](media/selectresourcegroup.png)

Nun wird Ihr ACI-Kontext aufgelistet, und Sie können mit der rechten Maustaste darauf klicken, um ihn als aktuellen Kontext auszuwählen:

![Möglichkeit zum Auswählen des neuen ACI-Kontexts](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Ausführen von Containern in der Cloud

1. Verwenden Sie nun Ihren ACI-Kontext, und führen Sie den Container aus.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Werfen Sie nach der Ausführung jetzt einen Blick auf den Container in Ihrem Kontext.

   ![Ausführung des Containers im ACI-Kontext](media/contextcontainer.png)

1. Sie können mit der rechten Maustaste auf den ausgeführten Container und dann auf **Im Browser anzeigen** klicken, um zu überprüfen, ob alles ordnungsgemäß funktioniert.

   ![Container im ACI-Kontext mit öffentlicher IP-Adresse](media/containerinaci.png)

Außerdem sehen Sie, dass der Container in einem öffentlichen IP-Adressbereich ausgeführt wird und alles ordnungsgemäß funktioniert.

1. Werfen Sie nun einen Blick auf den ausgeführten Container, um zu überprüfen, ob er fehlerfrei funktioniert. Sehen Sie sich hierzu zunächst die Containerprotokolle an:
 
 ```bash
   docker logs distracted-jackson
   ```

1. Wie bei einem lokalen Container können Sie auch „exec“ in den Container einfügen.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Klicken Sie zum Abschluss mit der rechten Maustaste auf den ausgeführten Container und dann auf **Entfernen**, um den Arbeitsbereich zu bereinigen und um sicherzustellen, dass weiterhin keine Kosten für die Ausführung des Testcontainers anfallen.

## <a name="recap"></a>Zusammenfassung

Fantastisch, Sie haben Ihre Arbeitsauslastung nun zum ersten Mal erfolgreich in der Cloud bereitgestellt. Sie können all diese Schritte über die Befehlszeile oder mithilfe von `docker run` und `docker compose up` im ACI-Kontext durchführen, um Ihre Multicontaineranwendungen auszuführen. Weitere Informationen zum Ausführen Ihrer Container in der Cloud finden Sie in der erweiterten [Dokumentation zur Verwendung von ACI](https://docs.docker.com/engine/context/aci-integration/).

## <a name="next-steps"></a>Nächste Schritte

Setzen Sie das Tutorial fort.

> [!div class="nextstepaction"]
> [Ausblick](whats-next.md)
