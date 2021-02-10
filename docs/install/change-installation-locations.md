---
title: Auswählen von Installationspfaden
description: Erfahren Sie, wie Sie den Speicherbedarf für die Installation von Visual Studio auf dem Systemlaufwerk reduzieren können, indem Sie den Downloadcache, die freigegebenen Komponenten, die SDKs und die Tools auf verschiedene Laufwerke verteilen. Verschieben Sie beispielsweise einige Dateien vom C- auf das D-Laufwerk.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4db3a31c8baa578a17d14b3a740ff40a444ba208
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868633"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Auswählen der Installationspfade in Visual Studio

::: moniker range="vs-2019"

Sie können den Installationsspeicherbedarf von Visual Studio auf Ihrem Systemlaufwerk reduzieren, indem Sie den Speicherort für einige Dateien ändern. Genauer gesagt können Sie verschiedene Speicherorte für den Downloadcache, für freigegebene Komponenten, SDKs und Tools verwenden.

::: moniker-end

::: moniker range="vs-2017"

**Neuerungen in Version 15.7**: Sie können den Installationsspeicherbedarf von Visual Studio auf Ihrem Systemlaufwerk reduzieren, indem Sie den Speicherort für einige Dateien ändern. Genauer gesagt können Sie verschiedene Speicherorte für den Downloadcache, für freigegebene Komponenten, SDKs und Tools verwenden.

::: moniker-end

   > [!NOTE]
   > Es gibt einige Tools und SDKs, für die andere Regeln dafür gelten, an welchem Speicherort sie installiert werden können. Diese Tools und SDKs werden auch auf Ihrem Systemlaufwerk installiert, wenn Sie einen anderen Speicherort auswählen.

Sind Sie bereit? Gehen Sie folgendermaßen vor:

::: moniker range="vs-2017"

1. Klicken Sie beim Installieren von Visual Studio auf die Registerkarte **Installationspfade**.

   ![Visual Studio 2017 – Auswählen des Installationspfads](media/vs-installation-locations.png "Wählen Sie den Installationspfad aus.")

1. Übernehmen Sie im Abschnitt **Visual Studio-IDE** die Standardeinstellungen. Visual Studio installiert das Hauptprodukt sowie die Dateien, die in der spezifischen Version von Visual Studio enthalten sind.

   ![Visual Studio-IDE-Abschnitt der Registerkarte „Installationspfade“](media/vs-installation-locations-ide.png "Akzeptieren Sie den Standardpfad für den Abschnitt „Visual Studio-IDE“ der Registerkarte „Installationspfade“.")

   > [!TIP]
   > Wenn es sich bei Ihrem Systemlaufwerk um ein SSD (Solid State Drive) handelt, wird empfohlen, dass Sie den Standardpfad auf Ihrem Systemlaufwerk akzeptieren. Begründung: Bei der Entwicklung mit Visual Studio werden mehrere Dateien gelesen und in diese geschrieben, wodurch die E/A-Aktivität des Datenträgers erhöht wird. Sie sollten daher ihr schnellstes Laufwerk auswählen, um diese Auslastung zu bewältigen.

1. Wählen Sie im Abschnitt **Downloadcache** aus, ob der Downloadcache beibehalten werden soll, und wählen Sie dann aus, wo dessen Dateien gespeichert werden sollen.

     ![Abschnitt „Downloadcache“ der Registerkarte „Installationspfade“](media/vs-installation-locations-cache.png "Wählen Sie aus, ob der Downloadcache nach der Installation beibehalten werden soll, und geben Sie dann das Laufwerk an, auf dem Dateien gespeichert werden sollen.")

    1. Aktivieren oder deaktivieren Sie die Option **Downloadcache nach der Installation beibehalten**.

       Wenn Sie den Downloadcache nicht beibehalten möchten, wird der Speicherort nur vorübergehend verwendet. Diese Aktion wirkt sich nicht auf Dateien aus vorherigen Installationen aus oder löscht diese.

    1. Legen Sie das Laufwerk fest, auf dem Installationsdateien und Manifeste aus dem Downloadcache gespeichert werden sollen.

        Wenn Sie beispielsweise die Workload „Desktopentwicklung mit C++“ auswählen, ist temporär ein Speicherplatz von 1,58 GB auf Ihrem Systemlaufwerk erforderlich. Dieser wird nach Abschluss der Installation freigegeben.

       > [!IMPORTANT]
       > Dieser Speicherort wird bei der ersten Installation festgelegt und kann im Nachhinein nicht über die Benutzeroberfläche des Installers geändert werden. Sie müssen [Befehlszeilenparameter](use-command-line-parameters-to-install-visual-studio.md) verwenden, um den Downloadcache zu verschieben.

1. Geben Sie im Abschnitt **Freigegebene Komponenten, Tools und SDKs** das Laufwerk an, auf dem Sie Dateien speichern möchten, die von parallelen Installationen von Visual Studio freigegeben werden. SDKs und Tools werden ebenfalls in diesem Verzeichnis gespeichert.

   ![Abschnitt „Gemeinsam genutzte Komponenten, Tools und SDKs“ der Registerkarte „Installationspfad“](media/vs-installation-locations-shared.png "Geben Sie den Speicherort an, an dem Sie gemeinsam genutzte Komponenten, Tools und SDKs speichern möchten.")

::: moniker-end

::: moniker range="vs-2019"

1. Klicken Sie beim Installieren von Visual Studio auf die Registerkarte **Installationspfade**.

   ![Visual Studio 2019 – Auswählen des Installationspfads](media/vs-2019/vs-installer-installation-locations.png "Wählen Sie den Installationspfad aus.")

1. Übernehmen Sie im Abschnitt **Visual Studio-IDE** die Standardeinstellungen. Visual Studio installiert das Hauptprodukt sowie die Dateien, die in der spezifischen Version von Visual Studio enthalten sind.

   > [!TIP]
   > Wenn es sich bei Ihrem Systemlaufwerk um ein SSD (Solid State Drive) handelt, wird empfohlen, dass Sie den Standardpfad auf Ihrem Systemlaufwerk akzeptieren. Begründung: Bei der Entwicklung mit Visual Studio werden mehrere Dateien gelesen und in diese geschrieben, wodurch die E/A-Aktivität des Datenträgers erhöht wird. Sie sollten daher ihr schnellstes Laufwerk auswählen, um diese Auslastung zu bewältigen.

1. Wählen Sie im Abschnitt **Downloadcache** aus, ob der Downloadcache beibehalten werden soll, und wählen Sie dann aus, wo dessen Dateien gespeichert werden sollen.

    * Aktivieren oder deaktivieren Sie die Option **Downloadcache nach der Installation beibehalten**.

       Wenn Sie den Downloadcache nicht beibehalten möchten, wird der Speicherort nur vorübergehend verwendet. Diese Aktion wirkt sich nicht auf Dateien aus vorherigen Installationen aus oder löscht diese.

    * Legen Sie das Laufwerk fest, auf dem Installationsdateien und Manifeste aus dem Downloadcache gespeichert werden sollen.

        Wenn Sie beispielsweise die Workload „Desktopentwicklung mit C++“ auswählen, ist temporär ein Speicherplatz von 1,58 GB auf Ihrem Systemlaufwerk erforderlich. Dieser wird nach Abschluss der Installation freigegeben.

       > [!IMPORTANT]
       > Dieser Speicherort wird bei der ersten Installation festgelegt und kann im Nachhinein nicht über die Benutzeroberfläche des Installers geändert werden. Sie müssen [Befehlszeilenparameter](use-command-line-parameters-to-install-visual-studio.md) verwenden, um den Downloadcache zu verschieben.

1. Beachten Sie im Abschnitt **Freigegebene Komponenten, Tools und SDKs**, dass hier dasselbe Laufwerk verwendet wird, das Sie im Abschnitt „Downloadcache“ ausgewählt haben. Visual Studio speichert im Verzeichnis „\Microsoft\VisualStudio\Shared“ die Dateien, die von parallelen Visual Studio-Installationen freigegeben wurden. SDKs und Tools werden ebenfalls in diesem Verzeichnis gespeichert.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Visual Studio aktualisieren](update-visual-studio.md)
* [Ändern von Visual Studio](update-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)
