---
title: 'Docker-Tutorial: Erste Schritte mit Docker'
description: Dies ist ein mehrstufiges Tutorial, in dem die Grundlagen der Arbeit mit Docker mit Visual Studio Code behandelt werden.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 554badf01122b6c41d89c00b740574d28185e35e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837969"
---
# <a name="tutorial-get-started-with-docker"></a>Tutorial: Erste Schritte mit Docker

In diesem Tutorial erfahren Sie mehr über das Erstellen und Bereitstellen von Docker-Apps einschließlich der Verwendung mehrerer Container mit einer Datenbank sowie über die Verwendung von Docker Compose. Außerdem stellen Sie Ihre containerisierte App in Azure bereit.

## <a name="start-the-tutorial"></a>Starten des Tutorials

Herzlichen Glückwunsch, falls Sie den Befehl bereits zum Einstieg in das Tutorial ausgeführt haben.  Falls nicht, öffnen Sie ein Eingabeaufforderungs- oder Bash-Fenster, und führen Sie den Befehl aus:

```cli
docker run -d -p 80:80 docker/getting-started
```

Sie werden feststellen, dass einige Flags verwendet werden. Hier finden Sie weitere Informationen dazu:

- `-d`: Hiermit wird der Container im getrennten Modus ausgeführt (im Hintergrund)
- `-p 80:80`: Hiermit wird Port 80 des Hosts zu Port 80 im Container zugeordnet.
- `docker/getting-started`: Dies ist das zu verwendende Image.

> [!TIP]
> Sie können einzelne Zeichenflags kombinieren, um den vollständigen Befehl zu verkürzen.
> Der obige Befehl könnte z. B. wie folgt geschrieben werden:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>VS Code-Erweiterung

Bevor dies zu weit geht, soll der Fokus auf der Docker-VS Code-Erweiterung liegen, die Ihnen einen schnellen Überblick über die Container bietet, die auf Ihrem Computer ausgeführt werden. Sie ermöglicht Ihnen den schnellen Zugriff auf Containerprotokolle, das Abrufen einer Shell innerhalb des Containers und die einfache Verwaltung des Containerlebenszyklus (Anhalten, Entfernen usw.).

Befolgen Sie [diese](https://code.visualstudio.com/docs/containers/overview) Anweisungen, um auf die Erweiterung zuzugreifen. Verwenden Sie das Docker-Symbol auf der linken Seite, um die Docker-Ansicht zu öffnen. Wenn Sie die Erweiterung jetzt öffnen, wird dieses Tutorial ausgeführt. Der Containername (`angry_taussig` unten) ist ein zufällig erstellter Name. Ihnen wird daher wahrscheinlich ein anderer Name angezeigt.

![Ausführung des Containers in der Docker-Erweiterung im Rahmen des Tutorials](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Was ist ein Container?

Nachdem Sie nun einen Container ausgeführt haben: *Was genau ist ein Container*? Einfach ausgedrückt handelt es sich bei einem Container um einen weiteren Prozess auf dem Computer, der von allen anderen Prozessen auf dem Hostcomputer isoliert ist. Bei dieser Isolation können Features wie [Kernelnamespaces und cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504) verwendet werden, die unter Linux bereits seit langer Zeit verfügbar sind. Docker hat diese Funktionen zugänglich und benutzerfreundlich gemacht.

> [!NOTE]
> **Erstellen von Containern von Grund auf:** Wenn Sie wissen möchten, wie Container von Grund auf erstellt werden, können Sie sich das Video von Liz Rice von Aqua Security ansehen, in dem sie einen Container von Grund auf erstellt:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Was ist ein Containerimage?

Beim Ausführen eines Containers wird ein isoliertes Dateisystem verwendet. Dieses benutzerdefinierte Dateisystem wird von einem **Containerimage** bereitgestellt. Da das Image das Dateisystem des Containers umfasst, muss es alles enthalten, was zum Ausführen einer Anwendung erforderlich ist. Dazu gehören unter anderem alle Abhängigkeiten, Konfigurationen, Skripts, und Binärdateien. Das Image enthält auch weitere Konfigurationen wie Umgebungsvariablen, einen Standardbefehl für die Ausführung und andere Metadaten für den Container.

Images werden zu einem späteren Zeitpunkt genauer erläutert, und es werden unter anderem Themen wie Ebenen und bewährte Methoden abgedeckt.

> [!NOTE]
> Wenn Sie mit `chroot` vertraut sind, stellen Sie sich einen Container als erweiterte Version von `chroot` vor. Das Dateisystem stammt einfach aus dem Image. Ein Container bietet jedoch zusätzliche Isolation, die bei der einfachen Verwendung von chroot nicht verfügbar ist.

## <a name="next-steps"></a>Nächste Schritte

Setzen Sie das Tutorial fort.

> [!div class="nextstepaction"]
> [Die Anwendung](your-application.md)
