---
title: Debuggen von .NET Core unter Linux
description: Debuggen Sie .NET Core unter Linux mithilfe von SSH (Secure Shell) durch Anfügen an einen Prozess. Bereiten Sie Ihre App für das Debuggen vor. Erstellen Sie die App, und stellen Sie sie bereit. Fügen Sie den Debugger an.
ms.custom: SEO-VS-2020
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99bfd1df6d977830e5b8e332efa3d0af653d3aec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934610"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Debuggen von .NET Core unter Linux mithilfe von SSH durch Anhängen an einen Prozess

Ab Visual Studio 2017 können Sie .NET Core-Prozesse, die auf einer Linux-Bereitstellung (lokal oder remote) ausgeführt werden, über SSH anfügen. In diesem Artikel wird beschrieben, wie Sie Debuggen einrichten und wie es erfolgt. Weitere Informationen zu Debuggingszenarios mit Docker-Containern finden Sie stattdessen unter [Anfügen an einen in einem Docker-Container ausgeführten Prozess](../debugger/attach-to-process-running-in-docker-container.md) und unter [Containertools](../containers/edit-and-refresh.md). Informationen zum Debuggen von Linux in WSL 2 über Visual Studio (ohne Anfügen an den Prozess) finden Sie unter [Debuggen von .NET Core-Apps in WSL 2 mit Visual Studio](../debugger/debug-dotnet-core-in-wsl-2.md).

## <a name="prerequisites"></a>Voraussetzungen

- Auf dem Visual Studio-Computer müssen Sie entweder die Workload **ASP.NET und Webentwicklung** oder die Workload **Plattformübergreifende .NET Core-Entwicklung** installieren.

- Auf dem Linux-Server müssen Sie den SSH-Server installieren. Verwenden Sie zum Entpacken und Installieren curl oder wget. Unter Ubuntu können Sie beispielsweise Folgendes ausführen:

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

- Installieren Sie auf dem Linux-Server [die .NET-Runtime unter Linux](/dotnet/core/install/linux), und suchen Sie die Seite, die mit Ihrer Linux-Distribution (z. B. Ubuntu) übereinstimmt. Das .NET SDK ist nicht erforderlich.

- Ausführliche ASP.NET Core-Anweisungen finden Sie unter [Hosten von ASP.NET Core unter Linux mit Nginx](/aspnet/core/host-and-deploy/linux-nginx) und [Hosten von ASP.NET Core unter Linux mit Apache](/aspnet/core/host-and-deploy/linux-apache).

## <a name="prepare-your-application-for-debugging"></a>Vorbereiten der Anwendung für das Debuggen

Bereiten Sie Ihre Anwendung wie folgt für das Debuggen vor:

- Verwenden Sie beim Erstellen der Anwendung ggf. eine Debugkonfiguration. Das Debuggen einer Releasekonfiguration ist weitaus schwieriger als von Code, der für das Debuggen kompiliert wurde. Wenn Sie eine Releasekonfiguration verwenden müssen, deaktivieren Sie zuerst „Nur eigenen Code“. Um diese Einstellung zu deaktivieren, wählen Sie **Tools** > **Optionen** > **Debuggen** aus, und deaktivieren Sie dann **Nur meinen Code aktivieren**.

- Stellen Sie sicher, dass Ihr Projekt für die Erstellung [portierbarer PDB-Dateien](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (Standardeinstellung) konfiguriert ist, und stellen Sie sicher, dass sich die PDB-Dateien am gleichen Speicherort wie die DLL befinden. Um dies in Visual Studio zu konfigurieren, klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** > **Build** > **Erweitert** > **Debuginformationen** aus.

## <a name="build-and-deploy-the-application"></a>Erstellen und Bereitstellen der Anwendung

Sie können mehrere Methoden verwenden, um die App vor dem Debuggen bereitzustellen. Sie haben unter anderem folgende Möglichkeiten:

- Kopieren Sie die Quellen auf den Zielcomputer, und kompilieren Sie mit ```dotnet build``` auf dem Linux-Computer.

- Erstellen Sie die App unter Windows, und übertragen Sie die Buildartefakte dann auf den Linux-Computer. (Die Buildartefakte bestehen aus der Anwendung selbst, den portierbaren PDB-Dateien, allen Laufzeitbibliotheken, von denen sie abhängig sein kann, und der Datei *.deps.json*.)

Starten Sie die Anwendung, sobald die App bereitgestellt wurde.

## <a name="attach-the-debugger"></a>Fügen Sie den Debugger an.

Sie können den Debugger anfügen, sobald die Anwendung auf dem Linux-Computer ausgeführt wird.

1. Klicken Sie in Visual Studio auf **Debuggen** > **An Prozess anfügen...** .

1. Wählen Sie in der Liste **Verbindungstyp** den Typ **SSH** aus.

1. Ändern Sie das **Verbindungsziel** in die IP-Adresse oder den Hostnamen des Zielcomputers.

   Wenn Sie noch keine Anmeldeinformationen angegeben haben, werden Sie aufgefordert, ein Kennwort und/oder eine private Schlüsseldatei einzugeben.

   Es gibt keine zu konfigurierenden Port-Anforderungen, außer dem Port, auf dem der SSH-Server ausgeführt wird.

1. Suchen Sie den Prozess, den Sie debuggen möchten.

   Der Code wird entweder in einem eindeutigen Prozessnamen oder in einem Prozess mit dem Namen „dotnet“ ausgeführt. Um den gewünschten Prozess zu finden, überprüfen Sie die Spalte **Titel**, in der die Befehlszeilenargumente für den Prozess angezeigt werden.

   Im folgenden Beispiel sehen Sie eine Liste der Prozesse von einem Linux-Remotecomputer über einen SSH-Transport, die im Dialogfeld **An Prozess anfügen** angezeigt wird.

   ![Anfügen an einen Linux-Prozess](media/remote-debug-linux-over-ssh-attach.png)

1. Wählen Sie **Anfügen** aus.

1. Wählen Sie im angezeigten Dialogfeld den Codetyp aus, den Sie debuggen möchten. Wählen Sie **Verwaltet (.NET Core für Unix)** aus.

1. Debuggen Sie die App mithilfe von Visual Studio-Debugfunktionen.

   Im folgenden Beispiel wird der Visual Studio-Debugger an einem Breakpoint im Code angehalten, der auf einem Linux-Remotecomputer ausgeführt wird.

   ![Treffen eines Haltepunkts](media/remote-debug-linux-over-ssh-hit-breakpoint.png)