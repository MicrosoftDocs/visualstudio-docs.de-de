---
title: Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung
description: Erfahren Sie, wie Sie Visual Studio aktualisieren, und dabei innerhalb einer Baseline für die Wartung bleiben.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: '>=vs-2019'
ms.openlocfilehash: 2c8510a1ba83243d2d92b538d80876a8b0f20079
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935654"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung

Während des Produktlebenszyklus wird Visual Studio häufig aktualisiert. Es gibt zwei Arten von Updates: 

* **Updates für die Nebenversion**, z. B. von &mdash;16.0 auf 16.1&mdash;, die neue Features und Komponenten enthalten.  
* **Wartungsupdates**, z. B. von 16.0.4 auf 16.0.5, die nur gezielte Korrekturen für kritische Probleme enthalten.

Unternehmensadministratoren können auswählen, ob sie für ihre Clients eine Baseline für die Wartung verwenden. Diese wird für ein Jahr über die Veröffentlichung der nächsten Baseline für die Wartung hinaus mit Wartungsupdates unterstützt.

So erhalten Entwickler und Administratoren mehr Flexibilität bei der Übernahme der neuen Features, Bugfixes oder Komponenten, die in neuen kleineren Updates enthalten sind. Die erste Baseline für die Wartung ist 16.0.x. Weitere Informationen finden Sie unter [Supportoptionen für Enterprise- und Professional-Kunden](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>So gelangen Sie in eine Baseline für die Wartung

Um mit der Verwendung einer Baseline für die Wartung zu beginnen, laden Sie einen Bootstrapper für eine bestimmte Visual Studio-Installer-Version von [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) herunter. Diese Bootstrapper enthalten Links zu den Produktkonfigurationen, Workloads und Komponenten für diese spezielle Version.

> [!NOTE]
> Beachten Sie den Unterschied zwischen einem Bootstrapper für eine bestimmte Version und den standardmäßigen Bootstrappern. Die standardmäßigen Bootstrapper sind so konfiguriert, dass sie jeweils die neueste verfügbare Version von Visual Studio verwenden. Sie enthalten eine Nummer im Dateinamen (z.B. vs_enterprise__123456789-123456789.exe), wenn sie von „My.VisualStudio.com“ heruntergeladen werden.

Während der Installation müssen Unternehmensadministratoren ihre Clients konfigurieren, um deren Aktualisierung auf die neueste Version zu verhindern. Dafür stehen verschiedene Möglichkeiten zur Verfügung:
- [Ändern Sie die `channelUri`-Einstellung in der Antwortkonfigurationsdatei](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network), um ein Kanalmanifest im Layout oder im lokalen Ordner zu verwenden.
- [Ändern Sie den channelUri über die Befehlszeile](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet), um eine nicht vorhandene Datei zu verwenden.
- [Legen Sie Richtlinien für das Clientsystem fest, um Updates zu deaktivieren](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating), damit sich Clients nicht selbsttätig aktualisieren.

### <a name="install-a-servicing-baseline-on-a-network"></a>Installieren einer Baseline für die Wartung in einem Netzwerk

Administratoren, die eine Netzwerklayoutinstallation verwenden, müssen den `channelUri`-Wert in der Datei *response.json* im Layout ändern, um die Datei *channelmanifest.json* zu verwenden, die sich im selben Verzeichnis befindet. Informationen zu den erforderlichen Schritten finden Sie unter [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md). Durch die Änderung des `channelUri`-Werts können Clients am Layoutspeicherort nach Updates suchen.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Installieren einer Baseline für die Wartung über das Internet

Bei einer internetbasierten Installation fügen Sie `--channelUri` mit einem nicht vorhandenen Kanalmanifest zur Befehlszeile hinzu, die zum Starten des Setups verwendet wird. Dadurch wird verhindert, dass Visual Studio die neueste verfügbare Version für ein Update verwendet. Im Folgenden ein Beispiel:

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Verwenden von Richtlinieneinstellungen, um Clients von der Aktualisierung auszuschließen

Eine weitere Möglichkeit zur Steuerung von Updates auf einem Client besteht darin, [Updatebenachrichtigungen zu deaktivieren](controlling-updates-to-visual-studio-deployments.md). Verwenden Sie diese Option, wenn der channelUri-Wert bei der Installation nicht geändert wurde. Dadurch erhält der Client keine Links zur neuesten verfügbaren Version. Ein Bootstrapper für eine bestimmte Version ist weiterhin erforderlich, um eine Aktualisierung auf eine bestimmte Version auf dem Client durchzuführen.

## <a name="how-to-stay-on-a-servicing-baseline"></a>So bleiben Sie in einer Baseline für die Wartung

Wenn ein Update für eine Baseline für die Wartung zur Verfügung steht, werden für das Wartungsupdate über [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) Bootstrapperdateien für eine bestimmte Version zur Verfügung gestellt.

Administratoren, die die Bereitstellung über die Netzwerklayoutinstallation durchführen, sollten den [Layoutspeicherort](update-a-network-installation-of-visual-studio.md) aktualisieren. Clients, die vom Speicherort aus installiert wurden, erhalten Updatebenachrichtigungen. Wenn das Update auf Clients bereitgestellt werden muss, folgen Sie [diesen Anweisungen](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines). Wenn Sie die Datei „response.json“ für ein Update ändern, fügen Sie keine zusätzlichen Workloads, Komponenten oder Sprachen hinzu. Die Verwaltung dieser Einstellungen muss nach dem Aktualisieren des Produkts als modify-Bereitstellung erfolgen.

Bei einer internetbasierten Installation führen Sie den neuen Bootstrapper für eine bestimmte Version mit dem Parameter `--channelUri` aus, der auf ein nicht vorhandenes Kanalmanifest auf dem Client verweist. Wenn das Update im stillen oder passiven Modus bereitgestellt wird, verwenden Sie zwei separate Befehle:

1. Aktualisieren Sie den Visual Studio-Installer:

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. Aktualisieren Sie die Visual Studio-Anwendung selbst:

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Weitere Informationen

* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
* [Gewusst wie: Definieren von Einstellungen in einer Antwortdatei](automated-installation-with-response-file.md)
* [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
* [Projektlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing/)
