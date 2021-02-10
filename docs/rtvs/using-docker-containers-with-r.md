---
title: R- und Docker-Container
description: Informationen zum Einrichten von Docker-Containern für R und ihrem Verbinden mit Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 01048bc9b21287eb62693096b34a1ea8305e0ee9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851867"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Verwenden von Docker-Containern mit R Tools für Visual Studio

Ab Version 1.3 unterstützen die R Tools für Visual Studio (RTVS) im Zusammenspiel mit einer Installation von [Docker für Windows](https://www.docker.com/docker-windows) das Arbeiten mit Docker-Containern.

## <a name="create-a-container"></a>Erstellen eines Containers

1. Klicken Sie in der rechten Ecke des Fensters **Arbeitsbereiche** (**R Tools** > **Windows** > **Arbeitsbereiche**) auf die Schaltfläche **Container**. Das Fenster informiert Sie, wenn Sie Docker für Windows nicht installiert haben, und stellt einen Link zum Download bereit. Die Installation von Docker kann einen Neustart des Computers erforderlich machen.

    ![Fenster „Arbeitsbereiche“ in R Tools für Visual Studio (VS 2017) mit dem Befehl „Container“](media/container-workspaces-window.png)

1. Klicken Sie im Fenster **Container** auf **Erstellen**:

    ![Befehl „Erstellen“ im Fenster „Container“](media/containers-window-create.png)

1. Vervollständigen Sie die erforderlichen Informationen im Dialogfeld, und klicken Sie auf **Erstellen**. Die von Ihnen eingegebenen Anmeldeinformationen dienen zum Erstellen eines Linux-Kontos, mit dem Sie sich später anmelden.

    ![Eingeben eines Containernamens und von Anmeldeinformationen beim Erstellen eines Containers](media/containers-window-create-fill.png)

1. Es kann eine Weile dauern, bis RTVS das Image erstellt hat. Das Fenster **Ausgabe** in Visual Studio zeigt den Fortschritt an, scheint aber bei langwierigen Downloads von Images nicht viel zu tun. Üben Sie sich also in Geduld. Nachdem das Image erstellt wurde, startet RTVS den Container und wird im Fenster **Container** angezeigt. Über die Steuerelemente auf der rechten Seite wird der Container angehalten, entfernt oder neu gestartet.

    ![Containerfenster mit einem vervollständigten Container](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Herstellen einer Verbindung mit einem Container

1. Im Abschnitt  **Lokal ausgeführte Container** des Fensters **Arbeitsbereiche** werden Container angezeigt, die den RTVS-Daemon an Port 5444 ausführen. (Unter [Remote R Server für Linux](setting-up-remote-r-service-on-linux.md) finden Sie Einzelheiten zur Konfiguration des Daemons.)

    ![Fenster „Arbeitsbereiche“ mit verfügbaren Containern](media/workspaces-window-running-containers.png)

1. Um eine Verbindung mit einem Container herzustellen, doppelklicken Sie auf den Containernamen, oder klicken Sie auf die Schaltfläche mit dem Vorwärtspfeil rechts daneben. Wenn die Verbindung hergestellt ist, sehen Sie ein **R Interactive**-Fenster (siehe [Arbeiten mit dem R Interactive-Fenster](interactive-repl-for-r-in-visual-studio.md)):

    ![Fenster „Arbeitsbereiche“ und das Fenster „REPL“, das für einen Container geöffnet ist](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Verwenden benutzerdefinierter Images

RTVS erkennt und erlaubt die Verwaltung von Containern, die mithilfe benutzerdefinierter Images erstellt wurden, wie z.B. dem Image „microsoft/rtvs“, das in der nachfolgenden Docker-Datei beschrieben ist. Im hier verwendeten Basisimage sind rtvs-daemon, R 3.4.2 und gängige R-Pakete vorinstalliert. **Hinweis**: Ändern Sie den hier gezeigten Benutzernamen und das Kennwort nach Bedarf.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Verwenden Sie den folgenden Befehl, um das Image zu erstellen, und ändern Sie den Containernamen (das Argument `--name`) wie gewünscht:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

Das Argument `-p 6056:5444` ordnet Port 6056 dem internen Port 5444 zu, den RTVS verwendet, um rtvs-daemon zu erkennen. Container, die den Container-Port 5444 verfügbar machen, werden im Fenster **Arbeitsbereiche** aufgelistet. Sie können dann das Fenster **Arbeitsbereiche** verwenden, um eine Verbindung mit einem Container herzustellen, indem Sie `<<unix>>\ruser1` als Benutzername und "foobar" als Kennwort verwenden, es sei denn, Sie haben in der Docker-Datei andere Anmeldeinformationen angegeben.
