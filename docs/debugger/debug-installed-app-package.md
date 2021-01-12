---
title: Debuggen eines installierten UWP-App-Pakets | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie ein installiertes UWP-App-Paket (Universelle Windows-Plattform) in Visual Studio auf Windows 10-Computern, Xbox-Konsolen und IoT-Geräten (Internet of Things, Internet der Dinge) debuggen.
ms.custom: SEO-VS-2020
ms.date: 11/07/2018
ms.topic: how-to
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 04ed043dbcb09c862fcdfc5f34d77fd938bd24dc
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728923"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Debuggen eines installierten UWP-App-Pakets in Visual Studio

Visual Studio kann installierte App-Pakete der universellen Windows-Plattform (Universal Windows Platform, UWP) auf Windows 10-Computern und Xbox-, HoloLens- und IoT-Geräten debuggen.

>[!NOTE]
>Auf Smartphones wird das Visual Studio-Debugging für installierte UWP-Apps jedoch nicht unterstützt.

Weitere Informationen zum Debuggen von UWP-Apps finden Sie in den Blogbeiträgen zum [Debuggen installierter App-Pakete](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) und dem [Erstellen von UWP-Apps](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Debuggen einer installierten UWP-App auf einem lokalen Computer

1. Klicken Sie in Visual Studio auf **Debuggen** > **Andere Debugziele** > **Installiertes App-Paket debuggen**.

1. Wählen Sie im Dialogfeld **Installiertes App-Paket debuggen** unter **Verbindungstyp** die Option **Lokaler Computer** aus.

1. Wählen Sie unter **Installierte App-Pakete** die App aus, die Sie debuggen möchten, oder geben Sie den Namen in das Suchfeld ein. Installierte App-Pakete, die aktuell nicht ausgeführt werden, werden unter **Wird nicht ausgeführt** angezeigt. Apps, die ausgeführt werden, erscheinen unter **Wird ausgeführt**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Ändern Sie ggf. den Codetyp unter **Folgenden Codetyp debuggen**, und wählen Sie andere Optionen aus.
   - Klicken Sie auf **Do not launch, but debug my code when it starts** (Debugger nicht starten, sondern Code beim App-Start debuggen), um nach dem App-Start das Debugging zu starten. Das Debugging zusammen mit der App zu starten, ist eine effektive Methode, um Steuerungspfade mit [verschiedenen Startmethoden](/windows/uwp/xbox-apps/automate-launching-uwp-apps) zu debuggen, z. B. die Protokollaktivierung mit benutzerdefinierten Parametern.

1. Klicken Sie auf **Starten** oder auf **Anfügen**, wenn die App bereits ausgeführt wird.

> [!NOTE]
> Sie können den Debugger auch an alle derzeit ausgeführten UWP-Prozesse und sonstigen App-Prozesse anfügen, indem Sie in Visual Studio auf **Debuggen** > **An Prozess anhängen** klicken. Das ursprüngliche Visual Studio-Projekt muss nicht an einen laufenden Prozess angefügt werden. Es hilft beim Debuggen eines Prozesses jedoch ungemein, die App-Symbole zu laden, für die Sie nicht über den ursprünglichen Code verfügen. Weitere Informationen finden Sie unter [Angeben von Symboldateien (.pdb) und Quelldateien im Visual Studio-Debugger (C#, C++, Visual Basic, F#)](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a> Debuggen einer installierten UWP-App auf einem Remotecomputer oder -gerät

Wenn auf einem Windows 10-Gerät oder einem Remotecomputer mit einem höheren Update als Windows 10 Creators Update zum ersten Mal der Debugger in Visual Studio ausgeführt wird, werden die Remotedebuggingtools auf dem Zielgerät installiert.

1. [Aktivieren Sie den Entwicklermodus](/windows/uwp/get-started/enable-your-device-for-development) auf dem Visual Studio-Computer sowie auf dem Remotegerät oder -computer.

1. Wenn Sie eine Verbindung mit einem Remotecomputer herstellen, auf dem ein früheres Update als Windows 10 Creators Update ausgeführt wird, [installieren Sie den Remotedebugger manuell auf dem Remotecomputer, und starten Sie ihn](../debugger/remote-debugging.md).

1. Klicken Sie auf dem Visual Studio-Computer auf **Debuggen** > **Andere Debugziele** > **Installiertes App-Paket debuggen**.

1. Wählen Sie im Dialogfeld **Installiertes App-Paket debuggen** unter **Verbindungstyp** die Option **Remotecomputer** oder **Gerät** aus.

   Wenn Sie **Gerät** auswählen, muss der Computer physisch mit einem Windows 10-Gerät verbunden sein.

   Wenn die Computeradresse eines Remotecomputers nicht bei **Adresse** angezeigt wird, klicken Sie auf **Ändern**.

   1. Geben Sie im Dialogfeld **Remoteverbindung** neben **Adresse** den Namen oder die IP-Adresse des Computers ein, mit dem Sie eine Verbindung herstellen möchten.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Wenn der Debugger nicht mithilfe des Computernamens eine Verbindung zu einem Remotecomputer herstellen kann, müssen Sie stattdessen die IP-Adresse verwenden. Verwenden Sie die IP-Adresse auch für Xbox-, HoloLens- oder IoT-Geräte.
   1. Wählen Sie unter **Authentifizierungsmodus** eine Authentifizierungsmethode aus.

      Für die meisten Apps müssen Sie nur den Standardwert **Universal (Unencrypted Protocol)** (Universell [unverschlüsseltes Protokoll]) beibehalten.
   1. Wählen Sie **Auswählen**.

1. Wählen Sie unter **Installierte App-Pakete** die App aus, die Sie debuggen möchten, oder geben Sie den Namen in das Suchfeld ein. Installierte App-Pakete, die aktuell nicht ausgeführt werden, werden unter **Wird nicht ausgeführt** angezeigt. Apps, die ausgeführt werden, erscheinen unter **Wird ausgeführt**.

1. Ändern Sie ggf. den Codetyp unter **Folgenden Codetyp debuggen**, und wählen Sie andere Optionen aus.
   - Klicken Sie auf **Do not launch, but debug my code when it starts** (Debugger nicht starten, sondern Code beim App-Start debuggen), um nach dem App-Start das Debugging zu starten. Das Debugging zusammen mit der App zu starten, ist eine effektive Methode, um Steuerungspfade mit [verschiedenen Startmethoden](/windows/uwp/xbox-apps/automate-launching-uwp-apps) zu debuggen, z. B. die Protokollaktivierung mit benutzerdefinierten Parametern.

1. Klicken Sie auf **Starten** oder auf **Anfügen**, wenn die App bereits ausgeführt wird.

Wenn Sie ein installiertes App-Paket zum ersten Mal auf einem verbundenen Xbox-, HoloLens- oder IoT-Gerät debuggen, installiert Visual Studio die richtige Version des Remotedebuggers für das Zielgerät. Die Installation des Remotedebuggers kann einige Zeit in Anspruch nehmen. Während des Vorgangs wird die Meldung **Der Remotedebugger wird gestartet** angezeigt.

>[!NOTE]
>Derzeit wird die App auf Xbox- oder HoloLens-Geräten mit dem angefügten Debugger neu gestartet, wenn sie bereits ausgeführt wurde.

Weitere Informationen zur Remotebereitstellung von UWP-Apps finden Sie unter [Bereitstellen und Debuggen von UWP-Apps](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) und [Debuggen von UWP-Apps auf Remotecomputern über Visual Studio](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Remotedebuggen](../debugger/remote-debugging.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)