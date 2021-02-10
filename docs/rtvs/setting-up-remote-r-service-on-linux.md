---
title: Einrichten von Remote R Service unter Linux
description: Einrichten des Remote R Services unter Ubuntu und des Windows-Subsystems für Linux.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 586f3038ff4bb091fb99160d7965ad927eda070a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851815"
---
# <a name="remote-r-service-for-linux"></a>Remote R Service für Linux

Remote R Service für Linux ist derzeit als Paket des Typs „rtvs-daemon“ verfügbar. Unterstützung des Daemons wurde für Ubuntu 16.04, 16.10 LTS Desktop und Server sowie das Windows-Subsystem für Linux mit Ubuntu getestet. Der Großteil dieses Artikels besteht aus Anweisungen zum Einrichten von Remote R Service für diese verschiedenen Systeme.

Nachdem Sie den Remotecomputer konfiguriert haben, werden die R Tools für Visual Studio (RTVS) durch folgende Schritte mit diesem Dienst verbunden:

1. Klicken Sie auf **R Tools** > **Windows** > **Arbeitsbereiche**, um das Fenster **Arbeitsbereiche** zu öffnen.
1. Wählen Sie **Verbindung hinzufügen** aus.
1. Geben Sie der Verbindung einen Namen und ihre URL an, z.B. `https://localhost:5444` (Windows-Subsystem für Linux) oder `https://public-ip:5444` (Azure-Container). Wählen Sie **Speichern** aus, sobald Sie fertig sind.
1. Klicken Sie auf das Verbindungssymbol, oder doppelklicken Sie auf das Verbindungselement.
1. Geben Sie Anmeldeinformationen an. Dem Benutzernamen muss `<<unix>>\` wie in `<<unix>>\ruser1` vorangestellt werden (was für alle Verbindungen mit Linux-Remotecomputern erforderlich ist).
1. Wenn Sie ein selbstsigniertes Zertifikat verwenden, wird möglicherweise eine Warnung angezeigt. Die Meldung enthält Anweisungen, wie Sie die Warnung vermeiden können.

## <a name="set-up-remote-r-service"></a>Einrichten von Remote R Service

In diesem Abschnitt werden die folgenden Optionen beschrieben:

- [Physischer Ubuntu-Computer](#physical-ubuntu-computer)
- [Ubuntu Server-VM oder Data Science-VM in Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Lokaler oder Remote-Docker-Container (bereinigter Build)](#local-or-remote-docker-container-clean-build)
- [In Azure Container Instances ausgeführter Container](#container-running-on-azure-container-instances)

Auf dem Remotecomputer muss in jedem Fall einer der folgenden R-Interpreter installiert sein:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R für Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Physischer Ubuntu-Computer

1. Sobald Sie sich auf dem Computer angemeldet haben, laden Sie“ rtvs-daemon tarball“ herunter:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Führen Sie das Installationsskript aus:

    ```bash
    sudo ./rtvs-install
    ```

    Verwenden Sie für eine automatische Installation `sudo ./rtvs-install -s`.

1. Aktivieren Sie den Dienst, und starten Sie ihn:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Konfigurieren Sie das SSL-Zertifikat (das für eine Produktionsumgebung erforderlich ist). Standardmäßig verwendet rtvs-daemon die vom `ssl-cert`-Paket generierten Dateien `ssl-cert-snakeoil.pem` und `ssl-cert-snakeoil.pem`. Während der Installation werden diese zu `ssl-cert-snakeoil.pfx` kombiniert. Verwenden Sie für Produktionszwecke das von Ihrem Administrator bereitgestellte SSL-Zertifikat. Das SSL-Zertifikat kann konfiguriert werden, indem eine *PFX*-Datei und ein optionales Importkennwort in */etc/rtvs/rtvsd.config.json* angegeben werden.

1. (Optional) Überprüfen Sie, ob der Dienst ausgeführt wird:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Wenn Sie keinen Prozess sehen, der unter dem Benutzernamen `rtvssvc` ausgeführt wird, führen Sie den folgenden Befehl aus:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Weitere Informationen zur Konfiguration von rtvs-daemon finden Sie unter `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Ubuntu Server-VM oder Data Science-VM in Azure

#### <a name="create-a-vm"></a>Erstellen einer VM

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
1. Navigieren Sie zu „Virtual Machines“, und wählen Sie dann **Hinzufügen** aus.
1. Suchen Sie in der Liste der verfügbaren VM-Images nach einer der folgenden Optionen, und wählen Sie diese aus:
    - Ubuntu Server: `Ubuntu Server 16.04 LTS`
    - Data Science-VM: `Linux Data Science` (unter [Data Science Virtual Machines](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) finden Sie Details)
1. Legen Sie das Bereitstellungsmodell auf `Resource manager` fest, und wählen Sie **Erstellen** aus.
1. Wählen Sie einen Namen für die VM. Geben Sie einen Benutzernamen und ein Kennwort an (das Kennwort ist erforderlich, da die Anmeldung mit öffentlichem SSH-Schlüssel nicht unterstützt wird).
1. Nehmen Sie sonstige gewünschten Änderungen an der VM-Konfiguration vor.
1. Wählen Sie eine VM-Größe, überprüfen Sie die Konfiguration, und klicken Sie auf **Erstellen**. Nachdem die VM erstellt wurde, fahren Sie mit dem nächsten Abschnitt fort.

#### <a name="configure-the-vm"></a>Konfigurieren der VM

1. Fügen Sie im Abschnitt **Netzwerk** der VM als erlaubten eingehenden Port 5444 hinzu. Wenn Sie einen anderen Port verwenden möchten, ändern Sie die Einstellung in der Konfigurationsdatei des RTVS-Daemons ( */etc/rtvs/rtvsd.config.json*).
1. (Optional) Legen Sie einen DNS-Namen fest. Sie können auch die IP-Adresse verwenden.
1. Stellen Sie eine Verbindung mit der VM über einen SSH-Client wie z.B. PuTTY for Windows her.
1. Befolgen Sie die vorherigen Anweisungen für einen [physischen Ubuntu-Computer](#physical-ubuntu-computer).

### <a name="windows-subsystem-for-linux-wsl"></a>Windows-Subsystem für Linux (WSL)

1. Befolgen Sie die WSL-Installationsanweisungen für entweder [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) oder [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Starten Sie bash unter Windows, und folgen Sie mit einer Ausnahme den vorherigen Anweisungen für einen [physischen Ubuntu-Computer](#physical-ubuntu-computer). Starten Sie bei Schritt 3 den Dienst stattdessen mit dem Befehl `rtvsd`, da WSL die Schnittstellen „systemd/systemctl“ derzeit nicht unterstützt.

### <a name="local-or-remote-docker-container-clean-build"></a>Lokaler oder Remote-Docker-Container (bereinigter Build)

1. Erstellen Sie eine Docker-Datei mit dem folgenden Inhalt, die den Daemon des Remote R-Diensts und die neueste Version von R installiert. **Hinweis:** Dieses Skript erstellt einen Benutzer namens „ruser1“ mit dem Kennwort „foobar“, das Sie nach Bedarf in den letzten zwei `RUN`-Anweisungen ändern können.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Erstellen Sie die Docker-Datei, und führen Sie sie aus:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Um in RTVS eine Verbindung mit dem Container herzustellen, verwenden Sie `https://localhost:5444` als Pfad, den Benutzernamen `<<unix>>\ruser1` und das Kennwort `foobar`. Wenn der Container auf einem Remotecomputer ausgeführt wird, verwenden Sie als Pfad stattdessen `https://remote-host-name:5444`. Der Port kann durch die Anpassung von */etc/rtvs/rtvsd.config.json* geändert werden.

### <a name="container-running-on-azure-container-instances"></a>In Azure Container Instances ausgeführter Container

1. Befolgen Sie die Anweisungen unter [Lokaler oder Remote-Docker-Container (bereinigter Build)](#local-or-remote-docker-container-clean-build) zum Erstellen des Images.
1. Verschieben Sie den Container per Push auf den Docker-Hub oder in das Azure Container-Repository.
1. Starten Sie die Azure CLI, und melden Sie sich mit dem Befehl `az login` an.
1. Führen Sie den Befehl `az container create` aus, um den Container zu erstellen, und verwenden Sie `--command-line "rtvsd"`, wenn Sie den Container nicht so eingerichtet haben, dass `rtvsd` als `systemd`-Dienst ausgeführt wird. Im folgenden Befehl wird erwartet, dass sich das Image auf dem Docker-Hub befindet. Sie können auch das Azure Container-Repository verwenden, indem Sie Argumente mit Anmeldeinformationen für das Container-Repository zur Befehlszeile hinzufügen.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. Führen Sie den Befehl `az container list` aus, um den Status zu überprüfen. Suchen Sie nach `provisioningState`: `Succeeded`.
1. Wenn die Bereitstellung erfolgreich war, können Sie jetzt eine Verbindung mit dem Container herstellen. Suchen Sie im Feld `ipAddress` nach der öffentlichen IP-Adresse, die Sie mit den Anmeldeinformationen in der Docker-Datei verwenden, um eine Verbindung mit dem Container aus RTVS herzustellen.
