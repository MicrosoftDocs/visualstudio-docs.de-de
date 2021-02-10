---
title: Importieren oder Exportieren von Installationskonfigurationen
titleSuffix: ''
description: Erfahren Sie, wie Sie die Installationskonfiguration in eine Datei vom Typ „.vsconfig“ exportieren, für andere Benutzer freigeben und zum Klonen importieren.
ms.date: 05/18/2019
ms.topic: how-to
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 043622d08b5389db8bf4cce80450f62c070a0ace
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949466"
---
# <a name="import-or-export-installation-configurations"></a>Importieren oder Exportieren von Installationskonfigurationen

Mit Installationskonfigurationsdateien können Sie Visual Studio in Ihrer gesamten Organisation konfigurieren. Dazu exportieren Sie einfach die Workload- und Komponenteninformationen mithilfe des Visual Studio-Installationsprogramms in eine .vsconfig-Datei. Sie können die Konfiguration dann in neue oder vorhandene Installationen importieren und für andere freigeben.

Gehen Sie folgendermaßen vor:

::: moniker range="vs-2017"

> [!NOTE]
> Diese Funktion ist nur in Visual Studio 2017 Version 15.9 und höher verfügbar.

::: moniker-end

## <a name="export-a-configuration"></a>Exportieren einer Konfiguration

Sie können wählen, ob Sie eine Installationskonfigurationsdatei entweder aus einer zuvor installierten Instanz von Visual Studio oder einer Instanz, die Sie gerade installieren, exportieren möchten.

1. Öffnen Sie den Visual Studio-Installer.

1. Wählen Sie auf der Produktkarte die Schaltfläche **Mehr** und dann **Konfiguration exportieren** aus.

   ![Exportieren der Konfiguration von der Produktkarte im Visual Studio-Installer](../install/media/vs-2019/vs-installer-export-config.png)

1. Navigieren Sie zum Speicherort, an dem Sie Ihre .vsconfig-Datei speichern möchten, oder geben Sie ihn ein, und wählen Sie dann **Details überprüfen** aus.

   ![Exportieren der Konfiguration aus dem Visual Studio-Installer](../install/media/vs-2019/export-configuration-confirmation.png)

1. Stellen Sie sicher, dass Sie über die Workloads und Komponenten verfügen, die Sie benötigen, und wählen Sie dann **Exportieren**.

## <a name="import-a-configuration"></a>Importieren einer Konfiguration

Wenn Sie bereit sind, eine Installationskonfigurationsdatei zu importieren, führen Sie diese Schritte aus.

1. Öffnen Sie den Visual Studio-Installer.

1. Wählen Sie auf der Produktkarte die Schaltfläche **Mehr** und dann **Konfiguration importieren** aus.

1. Suchen Sie die .vsconfig-Datei, die Sie importieren möchten, und wählen Sie dann **Details überprüfen**.

1. Stellen Sie sicher, dass Sie über die Workloads und Komponenten verfügen, die Sie benötigen, und wählen Sie dann **Schließen**.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>Automatisches Installieren fehlender Komponenten

**Neu in Visual Studio 2019**: Wenn Sie eine .vsconfig-Datei in Ihrem Stammverzeichnis der Projektmappe speichern und dann eine Projektmappe öffnen, erkennt Visual Studio automatisch, welche Komponenten fehlen und fordert Sie auf, diese zu installieren.

![Projektmappen-Explorer schlägt zusätzliche Komponenten vor](../install/media/vs-2019/solution-explorer-config-file.png)

Sie können auch eine .vsconfig-Datei direkt aus dem Projektmappen-Explorer generieren.

1. Klicken Sie mit der rechten Maustaste auf die Projektmappendatei.

1. Wählen Sie **Hinzufügen** > **Installationskonfigurationsdatei** aus.

1. Bestätigen Sie den Speicherort, an dem Sie die .vconfig-Datei speichern möchten, und wählen Sie dann **Details überprüfen** aus.

1. Stellen Sie sicher, dass Sie über die Workloads und Komponenten verfügen, die Sie benötigen, und wählen Sie dann **Exportieren**.

::: moniker-end

> [!NOTE]
> Weitere Informationen finden Sie im Blogbeitrag [Configure Visual Studio across your organization with .vsconfig](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) (Konfigurieren von Visual Studio in der gesamten Organisation mit .vsconfig).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Erstellen einer Netzwerkinstallation von Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Steuern von Updates für Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
* [Festlegen von Standardeinstellungen für Unternehmensbereitstellungen](set-defaults-for-enterprise-deployments.md)
