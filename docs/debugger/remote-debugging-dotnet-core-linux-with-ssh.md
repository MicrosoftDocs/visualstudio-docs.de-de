---
title: Remotedebuggen von .NET Core unter Linux | Microsoft-Dokumentation
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d66181f5e6720348e18c34b735ef29e24c0111a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796302"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>Remotedebuggen von .NET Core unter Linux mit SSH

Ab Visual Studio 2017 können Sie .NET Core-Prozesse, die unter Linux ausgeführt werden, über SSH anfügen. In diesem Artikel wird beschrieben, wie Sie Debuggen einrichten und wie es erfolgt.

## <a name="prerequisites"></a>Voraussetzungen

Auf dem Visual Studio-Computer müssen Sie entweder die Workload **ASP.NET und Webentwicklung** oder die Workload **Plattformübergreifende .NET Core-Entwicklung** installieren.

Auf dem Linux-Server müssen Sie den SSH-Server installieren. Verwenden Sie zum Entpacken und Installieren curl oder wget. Unter Ubuntu können Sie beispielsweise Folgendes ausführen:

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>Erstellen und Bereitstellen der Anwendung

Bereiten Sie Ihre Anwendung wie folgt für das Debuggen vor:

- Verwenden Sie beim Erstellen der Anwendung ggf. eine Debugkonfiguration. Das Debuggen einer Releasekonfiguration ist weitaus schwieriger als von Code, der für das Debuggen kompiliert wurde. Wenn Sie eine Releasekonfiguration verwenden müssen, deaktivieren Sie zuerst „Nur eigenen Code“. Um diese Einstellung zu deaktivieren, wählen Sie **Tools** > **Optionen** > **Debuggen** aus, und deaktivieren Sie dann **Nur meinen Code aktivieren** .

- Stellen Sie sicher, dass Ihr Projekt für die Erstellung [portabler PDB-Dateien](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (Standardeinstellung) konfiguriert ist, und stellen Sie sicher, dass sich die PDB-Dateien am gleichen Speicherort wie die DLL befinden. Um dies in Visual Studio zu konfigurieren, klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** > **Build** > **Erweitert** > **Debuginformationen** aus.

Sie können mehrere Methoden verwenden, um die App vor dem Debuggen bereitzustellen. Sie haben unter anderem folgende Möglichkeiten:

- Kopieren Sie die Quellen auf den Zielcomputer, und kompilieren Sie mit ```dotnet build``` auf dem Linux-Computer.

- Erstellen Sie die App unter Windows, und übertragen Sie die Buildartefakte dann auf den Linux-Computer. (Die Buildartefakte bestehen aus der Anwendung selbst, allen Laufzeitbibliotheken, von denen sie abhängig sein kann, und der Datei *.deps.json* .)

## <a name="attach-the-debugger"></a>Fügen Sie den Debugger an.

Nachdem die Computer konfiguriert sind, starten Sie die Anwendung auf dem Linux-Computer. Anschließend können Sie den Debugger anfügen.

1. Klicken Sie in Visual Studio auf **Debuggen** > **An Prozess anfügen...** .

1. Wählen Sie in der Liste **Verbindungstyp** den Typ **SSH** aus.

1. Ändern Sie das **Verbindungsziel** in die IP-Adresse oder den Hostnamen des Zielcomputers.

1. Suchen Sie den Prozess, den Sie debuggen möchten.

   Der Code wird entweder in einem eindeutigen Prozessnamen oder in einem Prozess mit dem Namen „dotnet“ ausgeführt. Um den gewünschten Prozess zu finden, überprüfen Sie die Spalte **Titel** , in der die Befehlszeilenargumente für den Prozess angezeigt werden.

   Im folgenden Beispiel sehen Sie eine Liste der Prozesse von einem Linux-Remotecomputer über einen SSH-Transport, die im Dialogfeld **An Prozess anfügen** angezeigt wird.

   ![Anfügen an einen Linux-Prozess](media/remote-debug-linux-over-ssh-attach.png)

1. Wählen Sie **Anfügen** aus.

1. Wählen Sie im angezeigten Dialogfeld den Codetyp aus, den Sie debuggen möchten. Wählen Sie **Verwaltet (.NET Core für Unix)** aus.

1. Debuggen Sie die App mithilfe von Visual Studio-Debugfunktionen.

   Im folgenden Beispiel wird der Visual Studio-Debugger an einem Breakpoint im Code angehalten, der auf einem Linux-Remotecomputer ausgeführt wird.

   ![Treffen eines Haltepunkts](media/remote-debug-linux-over-ssh-hit-breakpoint.png)