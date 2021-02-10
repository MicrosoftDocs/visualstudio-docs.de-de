---
title: Anfügen an einen in einem Docker-Container ausgeführten Prozess
description: Hier erfahren Sie, wie Sie eine App debuggen, die in einem Docker-Container ausgeführt wird. Dazu verwenden Sie Visual Studio.
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 4f39d4ecd69b726c1d549d723fadd324b1edd722
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857928"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Anfügen an einen in einem Docker-Container ausgeführten Prozess 

Sie können Apps, die entweder in einem Docker-Container unter Windows oder einen Docker-Container für .NET Core unter Linux ausgeführt werden, mithilfe von Visual Studio debuggen.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a> Anfügen an einen Prozess, der in einem Linux-Docker-Container ausgeführt wird

Sie können den Visual Studio-Debugger an einen Prozess anfügen, der in einem .NET Core Linux-Docker-Container auf Ihrem lokalen oder Remotecomputer ausgeführt wird, indem Sie das Dialogfeld **An den Prozess anhängen** verwenden.

> [!IMPORTANT]
> Um dieses Feature nutzen zu können, müssen Sie die Workload für die plattformübergreifende .NET Core-Entwicklung installieren und über lokalen Zugriff auf den Quellcode verfügen.

**So fügen Sie an einen aktiven Prozess in einem Linux-Docker-Container an**

1. Wählen Sie in Visual Studio **Debuggen > An den Prozess anhängen (STRG+ALT+P)** aus, um das Dialogfeld **An den Prozess anhängen** zu öffnen.

![Screenshot des Dialogfelds „An Prozess anhängen“ in Visual Studio, das den Verbindungstyp „Docker (Linux-Container)“ zeigt.](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Legen Sie den **Verbindungstyp** auf **Docker (Linux-Container)** fest.
3. Wählen Sie **Suchen...** aus, um das **Verbindungsziel** über das Dialogfeld **Docker-Container auswählen** festzulegen.

    Sie können einen Docker-Containerprozess entweder lokal oder remote debuggen.

    **So debuggen Sie einen Docker-Containerprozess lokal**
    1. Legen Sie **Docker-CLI-Host** auf **Lokaler Computer** fest.
    1. Wählen Sie einen aktiven Container zum Anfügen aus der Liste aus, und klicken Sie auf **OK**.

    ![Menü „Docker-Container auswählen“](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. So debuggen Sie einen Docker-Containerprozess remote**

    > [!NOTE]
    > Es gibt zwei Möglichkeiten, eine Remoteverbindung mit einem aktiven Prozess in einem Docker-Container herzustellen. Die erste Option, die Verwendung von SSH, ist ideal, wenn Sie keine Docker-Tools auf Ihrem lokalen Computer installiert haben.  Wenn Sie die Docker-Tools lokal installiert haben und Sie über einen Docker-Daemon verfügen, der so konfiguriert ist, dass er Remoteanforderungen akzeptiert, probieren Sie die zweite Option mit einem Docker-Daemon aus.

    1. ***So stellen Sie über SSH eine Verbindung mit einem Remotecomputer her***
        1. Wählen Sie **Hinzufügen...** aus, um eine Verbindung mit einem Remotesystem herzustellen.<br/>
        ![Herstellen einer Verbindung mit einem Remotesystem](../debugger/media/connect-remote-system.png "Herstellen einer Verbindung mit einem Remotesystem")
        1. Wählen Sie einen aktiven Container zum Anfügen aus, nachdem die Verbindung mit SSH oder dem Daemon erfolgreich hergestellt wurde, und drücken Sie auf **OK**.

    1. ***So legen Sie das Ziel auf einen Remotecontainer fest, der einen Prozess über einen [Docker-Daemon ausführt](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Geben Sie die Daemonadresse (d. h. über TCP, IP usw.) unter **Docker-Host (Optional)** an, und klicken Sie auf den Link „Aktualisieren“.
        1. Wählen Sie einen aktiven Container zum Anfügen aus, nachdem die Verbindung mit dem Daemon erfolgreich hergestellt wurde, und drücken Sie auf **OK**.

4. Wählen Sie den entsprechenden Containerprozess aus der Liste der **Verfügbaren Prozesse** und dann die Option **Anfügen** aus, um mit dem Debuggen Ihres C#-Containerprozesses in Visual Studio zu beginnen.

    ![Screenshot des Dialogfelds „An Prozess anhängen“ in Visual Studio. Der Verbindungstyp ist auf „Docker (Linux-Container)“ festgelegt, und der dotnet-Prozess ist ausgewählt.](../debugger/media/docker-attach-complete.png "Abgeschlossenes Menü „Anfügen“ für Linux-Docker")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a> Anfügen an einen Prozess, der in einem Windows-Docker-Container ausgeführt wird

Sie können den Visual Studio-Debugger an einen Prozess anfügen, der in einem Windows-Docker-Container auf Ihrem lokalen Computer ausgeführt wird, indem Sie das Dialogfeld **An den Prozess anhängen** verwenden.

> [!IMPORTANT]
> Um dieses Feature mit einem .NET Core-Prozess nutzen zu können, müssen Sie die Workload für die plattformübergreifende .NET Core-Entwicklung installieren und über lokalen Zugriff auf den Quellcode verfügen.

**So fügen Sie an einen aktiven Prozess in einem Windows-Docker-Container an**

1. Wählen Sie in Visual Studio **Debuggen > An den Prozess anhängen** (oder **STRG+ALT+P**) aus, um das Dialogfeld **An den Prozess anhängen** zu öffnen.

   ![Screenshot des Dialogfelds „An Prozess anhängen“ in Visual Studio, das den Verbindungstyp „Docker (Windows-Container)“ zeigt.](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Legen Sie den **Verbindungstyp** auf **Docker (Windows-Container)** fest.
3. Wählen Sie **Suchen...** aus, um das **Verbindungsziel** über das Dialogfeld **Docker-Container auswählen** festzulegen.

    > [!IMPORTANT]
    > Der Zielprozess muss dieselbe Prozessorarchitektur aufweisen wie der Windows-Docker-Container, in dem er ausgeführt wird.

   Das Festlegen des Ziels auf einen Remotecontainer über SSH ist derzeit nicht verfügbar und kann nur über einen Docker-Daemon erfolgen.

    ***So legen Sie das Ziel auf einen Remotecontainer fest, der einen Prozess über einen [Docker-Daemon ausführt](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Geben Sie die Daemonadresse (d. h. über TCP, IP usw.) unter **Docker-Host (Optional)** an, und klicken Sie auf den Link „Aktualisieren“.

    1. Wählen Sie einen aktiven Container zum Anfügen aus, nachdem die Verbindung mit dem Daemon erfolgreich hergestellt wurde, und wählen Sie „OK“ aus.

4. Wählen Sie den entsprechenden Containerprozess aus der Liste der **Verfügbaren Prozesse** und dann die Option **Anfügen** aus, um mit dem Debuggen Ihres C#-Containerprozesses zu beginnen.

    ![Screenshot des Dialogfelds „An Prozess anhängen“ in Visual Studio. Der Verbindungstyp ist auf „Docker (Windows-Container)“ festgelegt, und der „dotnet.exe“-Prozess ist ausgewählt.](../debugger/media/docker-attach-complete-windows.png "Abgeschlossenes Menü „Anfügen“ für Windows-Docker")

5. Wählen Sie den entsprechenden Containerprozess aus der Liste der verfügbaren Prozesse und dann die Option **Anfügen** aus, um mit dem Debuggen Ihres C#-Containerprozesses zu beginnen.