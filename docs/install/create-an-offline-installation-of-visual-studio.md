---
title: Erstellen einer Offlineinstallation
description: Erfahren Sie, wie Sie Visual Studio offline installieren können, wenn Sie über eine unzuverlässige Internetverbindung oder eine geringe Bandbreite verfügen.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2e4a7e0f9335971bb026ccc1c6b977680d9e3121
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949557"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Erstellen einer Offlineinstallation von Visual Studio

::: moniker range="vs-2017"

Visual Studio 2017 wurde so gestaltet, dass es unter verschiedensten Netzwerk- und Computerbedingungen gut funktioniert. Obwohl empfohlen wird, den [Visual Studio-Webinstaller](https://visualstudio.microsoft.com/vs/older-downloads) zu verwenden – bei dem es sich um eine kleine Datei handelt und durch den Sie mit den neuesten Fehlerbehebungen und Features auf dem Laufenden bleiben können – ist es Ihnen unter Umständen nicht möglich, diesen zu nutzen.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 wurde so gestaltet, dass es unter verschiedensten Netzwerk- und Computerbedingungen gut funktioniert. Obwohl empfohlen wird, den [Visual Studio-Webinstaller](https://visualstudio.microsoft.com/downloads) zu verwenden – bei dem es sich um eine kleine Datei handelt und durch den Sie mit den neuesten Fehlerbehebungen und Features auf dem Laufenden bleiben können – ist es Ihnen unter Umständen nicht möglich, diesen zu nutzen.

::: moniker-end

Gründe hierfür können eine unzuverlässige Internetverbindung oder eine Verbindung mit geringer Bandbreite sein. Falls dies der Fall sein sollte, haben Sie die folgenden Möglichkeiten: Sie können die neue Funktion „Download all, then install“ (Alles herunterladen, dann installieren) verwenden, um die Dateien vor der Installation herunterzuladen, oder Sie können über die Befehlszeile einen lokalen Cache für die Dateien erstellen.

> [!NOTE]
> Wenn Sie Administrator in einem Unternehmen sind und Visual Studio in einem Netzwerk von Clientarbeitsstationen, die mit einer Firewall geschützt sind, bereitstellen möchten, finden Sie weitere Informationen unter [Erstellen einer Netzwerkinstallation von Visual Studio](../install/create-a-network-installation-of-visual-studio.md) und [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Verwenden der Funktion „Download all, then install“ (Alles herunterladen, dann installieren)

::: moniker range="vs-2017"

[**Neuerungen in Version 15.8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): Nachdem Sie den Webinstaller heruntergeladen haben, wählen Sie im Visual Studio-Installer die neue Option **Download all, then install** (Alles herunterladen, dann installieren) aus. Anschließend fahren Sie mit der Installation fort.

   ![Die Option „Download all, then install“ (Alles herunterladen, dann installieren)](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

Nachdem Sie den Webinstaller heruntergeladen haben, wählen Sie im Visual Studio-Installer die neue Option **Download all, then install** (Alles herunterladen, dann installieren) aus. Anschließend fahren Sie mit der Installation fort.

   ![Die Option „Download all, then install“ (Alles herunterladen, dann installieren)](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Das „Alles herunterladen, dann installieren“-Feature wurde so gestaltet, dass Sie Visual Studio als einzelne Installation für denselben Computer herunterladen können, auf den Sie es heruntergeladen haben. Auf diese Weise können Sie sich vor der Installation von Visual Studio problemlos vom Internet trennen.

> [!IMPORTANT]
> Verwenden Sie das „Alles herunterladen, dann installieren“-Feature nicht zum Erstellen eines Offlinecaches, den Sie auf einen anderen Computer übertragen möchten. Hierfür ist es nicht vorgesehen. <br><br>Wenn Sie einen Offlinecache erstellen möchten, um Visual Studio auf einem anderen Computer zu installieren, finden Sie im Abschnitt [Verwenden der Befehlszeile zum Erstellen eines lokalen Caches](#use-the-command-line-to-create-a-local-cache) dieser Seite Informationen zum Erstellen eines lokalen Caches, oder auf der Seite [Erstellen einer Netzwerkinstallation von Visual Studio](../install/create-a-network-installation-of-visual-studio.md) Informationen zum Erstellen eines Netzwerkcaches.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Verwenden der Befehlszeile zum Erstellen eines lokalen Caches

Nachdem Sie einen kleinen Bootstrapper heruntergeladen haben, erstellen Sie über die Befehlszeile einen lokalen Cache. Dann installieren Sie Visual Studio über den lokalen Cache. (Dieser Vorgang ersetzt die ISO-Dateien, die in vorherigen Versionen genutzt wurden.)

Gehen Sie folgendermaßen vor:

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Schritt 1: Herunterladen des Visual Studio-Bootstrappers

Zum Ausführen dieses Schritts muss Ihr Computer mit dem Internet verbunden sein.

::: moniker range="vs-2017"

Informationen zum Herunterladen eines Bootstrappers für Visual Studio 2017 finden Sie auf der Downloadseite für [frühere Versionen von Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/).

Ihre ausführbare Setupdatei&mdash;oder genauer gesagt die Bootstrapperdatei&mdash;sollte einer der folgenden Dateien entsprechen.

| Edition | Dateiname |
|-------------|-----------------------|
|Visual Studio-Community | vs_community.exe |
|Visual Studio Professional | vs_professional.exe |
|Visual Studio Enterprise | vs_enterprise.exe |
|Visual Studio Build Tools   | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Beginnen Sie mit dem Herunterladen des Visual Studio-Bootstrappers für die ausgewählte Edition von Visual Studio. Ihre Setupdatei, d.h. Ihre Bootstrapperdatei, entspricht oder ähnelt einer der folgenden.

| Edition                    | Datei                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio-Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

>[!TIP]
>Wenn Sie zuvor eine Bootstrapperdatei heruntergeladen haben und deren Version überprüfen möchten, gehen Sie wie folgt vor: Öffnen Sie in Windows den Datei-Explorer, klicken Sie mit der rechten Maustaste auf die Bootstrapperdatei, wählen Sie **Eigenschaften** aus, wählen Sie die Registerkarte **Details**  aus, und sehen Sie sich dann die Nummer der **Produktversion** an. Um diese Nummer einem Release von Visual Studio zuzuordnen, nutzen Sie die Informationen auf der Seite [Visual Studio-Buildnummern und -Veröffentlichungstermine ](visual-studio-build-numbers-and-release-dates.md).

### <a name="step-2---create-a-local-install-cache"></a>Schritt 2: Erstellen eines lokalen Installationscaches

Zum Ausführen dieses Schritts muss Ihr Computer mit dem Internet verbunden sein.

> [!IMPORTANT]
> Wenn Sie Visual Studio Community installieren, müssen Sie die Anwendung innerhalb von 30 Tagen nach der Installation aktivieren. Dazu ist eine Internetverbindung erforderlich.

Öffnen Sie eine Eingabeaufforderung, und rufen Sie einen der Befehle in den folgenden Beispielen auf. Bei den hier aufgeführten Beispielen wird davon ausgegangen, dass Sie die Community-Edition von Visual Studio verwenden. Passen Sie den Befehl nach Bedarf für Ihre Edition an.

> [!TIP]
> Um Fehler zu vermeiden, darf Ihr vollständiger Installationspfad nicht mehr 80 Zeichen enthalten.

- Führen Sie für die .NET-Web- und .NET-Desktopentwicklung Folgendes aus:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Führen Sie für die .NET-Desktop- und Office-Entwicklung Folgendes aus:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Führen Sie für die C++-Desktopentwicklung Folgendes aus:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Führen Sie zum Erstellen eines vollständigen lokalen Layouts mit allen Funktionen Folgendes aus. Hinweis: Das Erstellen nimmt wegen der _umfangreichen_ Funktionen einige Zeit in Anspruch.

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Ein vollständiges Visual Studio-Layout erfordert mindestens 35 GB Speicherplatz. Weitere Informationen finden Sie unter [Systemanforderungen](/visualstudio/productinfo/vs2017-system-requirements-vs/). Weitere Informationen zur Erstellung eines Layouts, das nur die gewünschten Komponenten enthält, finden Sie unter [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Ein vollständiges Visual Studio-Layout erfordert mindestens 35 GB Speicherplatz. Weitere Informationen finden Sie unter [Systemanforderungen](/visualstudio/releases/2019/system-requirements/). Weitere Informationen zur Erstellung eines Layouts, das nur die gewünschten Komponenten enthält, finden Sie unter [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

Wenn Sie eine andere Sprache als Englisch installieren möchten, ändern Sie `en-US` in das gewünschte Gebietsschema aus der [Liste der Gebietsschemas](#list-of-language-locales). Verwenden Sie dann die [Liste verfügbarer Komponenten und Workloads](workload-and-component-ids.md), um Ihren Installationscache weiter anzupassen.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Schritt 3: Installieren von Visual Studio über den lokalen Cache

> [!TIP]
> Wenn eine Installation aus einem lokalen Installationscache erfolgt, werden beim Setup die lokalen Versionen dieser Dateien verwendet. Wenn Sie während der Installation jedoch Komponenten verwenden, die sich nicht im Cache befinden, wird versucht, sie aus dem Internet herunterzuladen.

::: moniker range="vs-2019"
> [!IMPORTANT]
> Wenn Sie bei Offlineinstallationen die Fehlermeldung „Ein Projekt, das mit den folgenden Parametern übereinstimmt, wurde nicht gefunden“ erhalten, stellen Sie sicher, dass Sie bei Version 16.3.5 oder höher den Schalter `--noweb` verwenden.
>
::: moniker-end

Um sicherzustellen, dass Sie nur die Dateien installieren, die Sie zuvor heruntergeladen haben, verwenden Sie dieselben Befehlszeilenoptionen, die Sie zum Erstellen des Layoutcaches verwendet haben. Wenn Sie z. B. einen Layoutcache mit dem folgenden Befehl erstellt haben:

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Anschließend führen Sie mit dem folgenden Befehl die Installation aus:

```cmd
c:\vslayout\vs_community.exe --noweb --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

Weitere Beispiele für die Verwendung von [Befehlszeilenparametern](use-command-line-parameters-to-install-visual-studio.md) finden Sie auf der Seite [Beispiele für Befehlszeilenparameter für die Installation von Visual Studio](command-line-parameter-examples.md). 

> [!NOTE]
> Wenn eine Fehlermeldung mit dem Hinweis zurückgegeben wird, dass eine Signatur ungültig ist, müssen Sie die aktualisierten Zertifikate installieren. Öffnen Sie den Ordner „Zertifikate“ in Ihrem Offlinecache. Doppelklicken Sie auf jede der Zertifikatdateien, und schließen Sie dann den Zertifikat-Manager-Assistenten ab. Wenn Sie nach einem Kennwort gefragt werden, lassen Sie es leer.

### <a name="list-of-language-locales"></a>Liste der Gebietsschemas

| **Gebietsschema** | **Sprache** |
| ----------------------- | --------------- |
| cs-CZ | Tschechisch |
| de-DE | Deutsch |
| en-US | Englisch |
| es-ES | Spanisch |
| fr-FR | Französisch |
| it-IT | Italienisch |
| ja-JP | Japanisch |
| ko-KR | Koreanisch |
| pl-PL | Polnisch |
| pt-BR | Portugiesisch (Brasilien) |
| ru-RU | Russisch |
| tr-TR | Türkisch |
| zh-CN | Chinesisch (vereinfacht) |
| zh-TW | Chinesisch (traditionell) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

- [Erstellen einer Netzwerkinstallation von Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](../install/install-certificates-for-visual-studio-offline.md)
- [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
