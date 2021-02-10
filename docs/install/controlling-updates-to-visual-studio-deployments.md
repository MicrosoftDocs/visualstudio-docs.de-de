---
title: Steuern von Updates für Bereitstellungen
description: Erfahren Sie, wie Sie ändern, wo Visual Studio nach einem Update sucht, wenn die Installation aus einem Netzwerk stammt.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ffa088de8852b0d5884cd4d9db5e65e1c179164b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868542"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen

Administratoren in Unternehmen erstellen oft Layouts und hosten es in einer Netzwerkdateifreigabe, um es für ihre Benutzer bereitzustellen.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Steuern, wo Visual Studio nach Updates sucht

In der Standardeinstellung sucht Visual Studio weiterhin online nach Updates, selbst wenn die Installation über eine Netzwerkfreigabe bereitgestellt wurde. Wenn ein Update verfügbar ist, kann der Benutzer es installieren. Alle Updateinhalte, die nicht im Offlinelayout gefunden werden, werden aus dem Web heruntergeladen.

Wenn Sie direkt steuern möchten, wo Visual Studio nach Updates sucht, können Sie den dazu verwendeten Speicherort ändern. Sie können kontrollieren, auf welche Version Ihre Benutzer aktualisiert werden. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie ein Offlinelayout:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Kopieren Sie es in die Dateifreigabe, in der es gehostet werden soll:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Ändern Sie im Layout die Datei „response.json“ und den Wert von `channelUri` so, dass er auf eine Kopie der Datei „channelManifest.json“ zeigt, die der Administrator steuert.

   Umgekehrte Schrägstriche im Wert müssen wie im folgenden Beispiel dargestellt mit Escapezeichen versehen werden:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Nun können Endbenutzer das Setup über diese Freigabe für die Installation von Visual Studio ausführen.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Wenn ein Unternehmensadministrator bestimmt, dass die Benutzer ein Update auf eine neuere Version von Visual Studio vornehmen sollten, kann er [den Layoutspeicherort wie folgt aktualisieren](update-a-network-installation-of-visual-studio.md), dass die aktualisierten Dateien einbezogen werden.

1. Verwenden Sie einen Befehl wie den folgenden:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Stellen Sie sicher, dass die Datei „response.json“ im aktualisierten Layout weiterhin wie folgt Ihre Anpassungen enthält, insbesondere die Änderung von „channelUri“:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Vorhandene Installationen von Visual Studio in diesem Layout suchen in `\\server\share\VS\ChannelManifest.json` nach Updates. Wenn diese Datei „channelManifest.json“ aktueller als in der Installation des Benutzers ist, benachrichtigt Visual Studio den Benutzer, dass ein Update verfügbar ist.

   Bei neuen Installationen wird die aktualisierte Version von Visual Studio direkt und automatisch aus dem Layout installiert.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Steuern der Benachrichtigungen in der Visual Studio IDE

::: moniker range="vs-2017"

Wie zuvor beschrieben, überprüft Visual Studio den Speicherort, von dem aus es installiert wurde (z.B. Netzwerkfreigabe oder Internet), um zu prüfen, ob Updates verfügbar sind. Sobald ein Update verfügbar ist, benachrichtigt Visual Studio den Benutzer mit einem Benachrichtigungshinweis rechts oben im Fenster.

   ![Benachrichtigungshinweis für Updates](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Wie zuvor beschrieben, überprüft Visual Studio den Speicherort, von dem aus es installiert wurde (z.B. Netzwerkfreigabe oder Internet), um zu prüfen, ob Updates verfügbar sind. Sobald ein Update verfügbar ist, benachrichtigt Visual Studio den Benutzer mit einem Benachrichtigungssymbol unten rechts im Fenster.

   ![Das Benachrichtigungssymbol in der Visual Studio-IDE](media/vs-2019/notification-bar.png "Das Benachrichtigungssymbol in der Visual Studio-IDE")

::: moniker-end

Sie können die Benachrichtigungen deaktivieren, wenn Sie nicht möchten, dass Benutzer über Updates benachrichtigt werden. (Sie können Benachrichtigungen beispielsweise deaktivieren, wenn Sie Updates über einen zentralen Softwareverteilungsmechanismus übermitteln.)

::: moniker range="vs-2017"

Da Visual Studio 2017 [Registrierungseinträge in einer privaten Registrierung speichert](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), lässt sich die Registrierung nicht auf die übliche Weise direkt bearbeiten. Visual Studio bietet jedoch das Hilfsprogramm `vsregedit.exe`, mit dessen Hilfe Sie die Visual Studio-Einstellungen ändern können. Sie können Benachrichtigungen mit folgendem Befehl deaktivieren:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Da Visual Studio 2019 [Registrierungseinträge in einer privaten Registrierung speichert](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), lässt sich die Registrierung nicht auf die übliche Weise direkt bearbeiten. Visual Studio bietet jedoch das Hilfsprogramm `vsregedit.exe`, mit dessen Hilfe Sie die Visual Studio-Einstellungen ändern können. Sie können Benachrichtigungen mit folgendem Befehl deaktivieren:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Achten Sie darauf, dass Sie das Verzeichnis ersetzen, damit es der installierten Instanz entspricht, die Sie bearbeiten möchten.)

> [!TIP]
> Mithilfe von [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) können Sie eine bestimmte Instanz von Visual Studio auf einer Clientarbeitsstation finden.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Weitere Informationen

* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tools zum Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
* [Projektlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing/)
