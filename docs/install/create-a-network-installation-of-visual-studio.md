---
title: Erstellen einer netzwerkbasierten Installation
description: Erfahren Sie, wie ein Netzwerkinstallationspunkts für die Bereitstellung von Visual Studio in einem Unternehmen erstellt wird.
ms.date: 08/27/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b572a6854d505704accd79cc4da2ac4e52c193d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850170"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Erstellen einer Netzwerkinstallation von Visual Studio

Normalerweise erstellen Unternehmensadministratoren für die Bereitstellung auf Clientarbeitsstationen einen Netzwerkinstallationspfad. Visual Studio wurde so entworfen, dass die Dateien für die Erstinstallation zusammen mit allen Produktupdates in einem einzelnen Ordner zwischengespeichert werden. (Dieser Prozess wird auch als _Erstellen eines Layouts_ bezeichnet.)

Dadurch können Clientarbeitsstationen dieselbe Netzwerkadresse verwenden, um ihre Installation zu verwalten, selbst wenn sie noch nicht auf das neueste Wartungsupdate aktualisiert haben.

 > [!NOTE]
 > Wenn Sie mehrere Editionen von Visual Studio in Ihrem Unternehmen nutzen (z.B. Visual Studio Professional und Visual Studio Enterprise), benötigen Sie für jede Edition eine eigene Netzwerkinstallationsfreigabe.

## <a name="download-the-visual-studio-bootstrapper"></a>Herunterladen des Visual Studio-Bootstrappers

Laden Sie für die gewünschte Edition von Visual Studio eine Bootstrapperdatei herunter. Achten Sie darauf, auf **Speichern** zu klicken, und dann auf **Ordner öffnen**.

::: moniker range="vs-2017"

Informationen zum Herunterladen eines Bootstrappers für Visual Studio 2017 finden Sie auf der Downloadseite für [frühere Versionen von Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/).

Ihre ausführbare Setupdatei&mdash;oder genauer gesagt die Bootstrapperdatei&mdash;sollte einer der folgenden Dateien entsprechen.

| Edition | Dateiname |
|-------------|-----------------------|
|Visual Studio Enterprise | **vs_enterprise.exe** |
|Visual Studio Professional | **vs_professional.exe** |
|Visual Studio Build Tools   | **vs_buildtools.exe** |

Weitere unterstützte Bootstrapper sind **vs_feedbackclient.exe**, **vs_teamexplorer.exe**, **vs_testagent.exe**, **vs_testcontroller.exe** und **vs_testprofessional.exe**.

::: moniker-end

::: moniker range="vs-2019"

Ihre ausführbare Setupdatei&mdash;oder genauer gesagt eine Bootstrapperdatei&mdash;sollte einer der folgenden Dateien entsprechen.

|Edition | Herunterladen|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [**vs_buildtools.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

Weitere unterstützte Bootstrapper sind [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe) und [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

>[!TIP]
>Wenn Sie zuvor eine Bootstrapperdatei heruntergeladen haben und deren Version überprüfen möchten, gehen Sie wie folgt vor: Öffnen Sie in Windows den Datei-Explorer, klicken Sie mit der rechten Maustaste auf die Bootstrapperdatei, wählen Sie **Eigenschaften** aus, wählen Sie die Registerkarte **Details**  aus, und sehen Sie sich dann die Nummer der **Produktversion** an. Um diese Nummer einem Release von Visual Studio zuzuordnen, nutzen Sie die Informationen auf der Seite [Visual Studio-Buildnummern und -Veröffentlichungstermine ](visual-studio-build-numbers-and-release-dates.md).

## <a name="create-an-offline-installation-folder"></a>Erstellen eines Offlineinstallationsordners

Zum Ausführen dieses Schritts muss Ihr Computer mit dem Internet verbunden sein. Um eine Offlineinstallation mit allen Sprachen und allen Funktionen zu erstellen, verwenden Sie einen Befehl, der denen in den folgenden Beispielen ähnelt.

   > [!IMPORTANT]
   > Ein komplettes Layout für ein Gebietsschema mit einer Sprache benötigt etwa 35 GB Festplattenspeicher für Visual Studio Community und 42 GB für Visual Studio Enterprise. Jedes zusätzliche [Gebietsschema](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) benötigt etwa 0,5 GB Speicherplatz. Weitere Informationen finden Sie im Abschnitt [Anpassen des Netzwerklayouts](#customize-the-network-layout).
   >
   > [!TIP]
   > Stellen Sie sicher, dass Sie den Befehl über das Download-Verzeichnis ausführen. Dies ist in der Regel `C:\Users\<username>\Downloads` auf einem Computer, auf dem Windows 10 installiert ist.

- Führen Sie für Visual Studio Enterprise aus:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Führen Sie für Visual Studio Professional aus:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Ändern der Datei „response.json“

Sie können die Datei „response.json“ zum Festlegen von Standardwerten ändern, die verwendet werden, wenn Setup ausgeführt wird.  Sie können z. B. die Datei `response.json` so konfigurieren, dass eine bestimmte Gruppe von Workloads automatisch ausgewählt wird. Einzelheiten finden Sie unter [Automatisieren der Visual Studio-Installation mit einer Antwortdatei](automated-installation-with-response-file.md).

Wenn der Visual Studio-Bootstrapper einen Fehler auslöst, wenn Sie ihn an eine Datei vom Typ „response.json“ koppeln, finden Sie weitere Informationen dazu im Abschnitt „Die Analyse der ID des übergeordneten Prozesses ist fehlgeschlagen“ auf der Seite [Beheben von Netzwerkfehlern beim Installieren oder Verwenden von Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process).

## <a name="copy-the-layout-to-a-network-share"></a>Kopieren des Layouts in eine Netzwerkfreigabe

Hosten Sie das Layout in einer Netzwerkfreigabe, damit es auf anderen Computern ausgeführt werden kann.

Im folgenden Beispiel wird [xcopy](/windows-server/administration/windows-commands/xcopy/) verwendet. Sie können auch [robocopy](/windows-server/administration/windows-commands/robocopy/) verwenden, wenn Sie möchten.

::: moniker range="vs-2017"

Beispiel:

```cmd
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> Stellen Sie sicher, dass Ihr vollständiger Layoutpfad weniger als 80 Zeichen enthält, um einen Fehler zu vermeiden.

## <a name="customize-the-network-layout"></a>Anpassen des Netzwerklayouts

Es gibt mehrere Optionen zum Anpassen Ihres Netzwerklayouts. Sie können ein Teillayout erstellen, das nur eine bestimmte Gruppe von [Gebietsschemas](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [Workloads und Komponenten mit ihren empfohlenen oder optionalen Abhängigkeiten](workload-and-component-ids.md) enthält. Dies ist möglicherweise hilfreich, wenn Sie wissen, dass Sie nur eine Teilmenge der Workloads auf Clientarbeitsstationen bereitstellen. Es folgen übliche Befehlszeilenparameter zum Anpassen des Layouts:

* `--add` zum Angeben von [Workload- oder Komponenten-IDs](workload-and-component-ids.md). <br>Wenn `--add` verwendet wird, werden nur die Workloads und Komponenten heruntergeladen, die mit `--add` angegeben sind.  Wenn `--add` nicht verwendet wird, werden alle Workloads und Komponenten heruntergeladen.
* `--includeRecommended` zum Einschließen aller empfohlenen Komponenten für die angegebenen Workload-IDs.
* `--includeOptional` zum Einschließen aller empfohlenen und optionalen Komponenten für die angegebenen Workload-IDs.
* `--lang` zum Angeben von [Gebietsschemas](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Es folgen einige Beispiele, wie ein Teillayout benutzerdefiniert erstellt werden kann.

* Führen Sie zum Herunterladen aller Arbeitsauslastungen und Komponenten für nur eine Sprache Folgendes aus:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Führen Sie zum Herunterladen aller Arbeitsauslastungen und Komponenten für mehrere Sprachen Folgendes aus:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Führen Sie zum Herunterladen einer Workload für alle Sprachen Folgendes aus:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Führen Sie zum Herunterladen von zwei Arbeitsauslastungen und einer optionalen Komponenten für drei Sprachen Folgendes aus:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* So laden Sie zwei Workloads und alle ihre empfohlenen Komponenten herunter:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Führen Sie Folgendes aus, um zwei Workloads und alle ihre empfohlenen und optionalen Komponenten herunterzuladen:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Neuerungen in Version 15.3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Speichern der Layoutoptionen

::: moniker-end

Wenn Sie einen Layoutbefehl ausführen, werden die Optionen gespeichert, die Sie angeben (z.B. die Workoads und Sprachen). Nachfolgende Layoutbefehle enthalten alle vorherigen Optionen.  Hier ist ein Beispiel für ein Layout mit nur einer Workload für Englisch:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Wenn Sie das Layout auf eine neuere Version aktualisieren möchten, müssen Sie keine zusätzlichen Befehlszeilenparameter angeben. Die vorherigen Einstellungen werden gespeichert und durch nachfolgende Layoutbefehle in diesem Layoutordner verwendet.  Der folgende Befehl aktualisiert das vorhandene partielle Layout.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Wenn Sie eine zusätzliche Workload hinzufügen möchten, finden Sie hier ein Beispiel. In diesem Fall fügen wir die Azure-Workload und die lokalisierten Sprache hinzu.  Nun sind sowohl der verwaltete Desktop und Azure in diesem Layout enthalten.  Die Sprachressourcen für Englisch und Deutsch sind für all diese Workloads enthalten. Das Layout wird auf die neueste Version aktualisiert.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Wenn Sie ein vorhandenes Layout auf ein vollständiges Layout aktualisieren möchten, verwenden Sie die Option „--all“, wie im folgenden Beispiel dargestellt.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Bereitstellen über eine Netzwerkinstallation

Administratoren können Visual Studio auf Clientarbeitsstationen als Teil eines Installationsskripts bereitstellen. Oder Benutzer mit Administratorrechten können das Setup direkt über die Freigabe ausführen, um Visual Studio auf ihrem Computer zu installieren.

* Benutzer können die Installation initiieren, indem Sie folgenden Befehl ausführen: <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Administratoren können eine Installation im unbeaufsichtigten Modus ausführen, indem sie folgenden Befehl ausführen:

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Stellen Sie sicher, dass Ihr vollständiger Layoutpfad weniger als 80 Zeichen enthält, um einen Fehler zu vermeiden.

> [!TIP]
> Bei Ausführung als Teil einer Batchdatei wird mit der Option `--wait` sichergestellt, dass der `vs_enterprise.exe`-Prozess wartet, bis die Installation abgeschlossen ist, ehe ein Exitcode zurückgegeben wird.
>
> Dies ist hilfreich, wenn ein Unternehmensadministrator weitere Aktionen für vollständige Installation durchführen möchte (z.B. um [einen Product Key auf eine erfolgreiche Installation anzuwenden](automatically-apply-product-keys-when-deploying-visual-studio.md)), aber auf die Beendigung der Installation warten muss, um den Rückgabecode dieser Installation zu verarbeiten.
>
> Wenn Sie `--wait` nicht verwenden, wird der Prozess `vs_enterprise.exe` beendet, bevor die Installation abgeschlossen ist, und gibt ungenauen Exitcode zurück, der den Status des Installationsvorgangs nicht darstellt.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> Wenn Sie bei Offlineinstallationen die Fehlermeldung „Ein Projekt, das mit den folgenden Parametern übereinstimmt, wurde nicht gefunden“ erhalten, stellen Sie sicher, dass Sie bei Version 16.3.5 oder höher den Schalter `--noweb` verwenden.
>
::: moniker-end

Bei der Installation eines Layout werden die installierten Inhalte aus dem Layout abgerufen. Wenn Sie allerdings eine Komponente auswählen, die im Layout fehlt, wird diese aus dem Internet abgerufen.  Falls Sie verhindern möchten, dass das Visual Studio-Setup alle Inhalte, die in Ihrem Layout fehlen, herunterlädt, verwenden Sie die Option `--noWeb`. Wenn `--noWeb` verwendet wird und das Layout nicht über alle Inhalte verfügt, die installiert werden sollen, tritt beim Setup ein Fehler auf.

> [!TIP]
> Wenn Sie die Installation über eine Offlinequelle oder einen Computer ohne Internetverbindung durchführen möchten, geben Sie die beiden Optionen `--noWeb` und `--noUpdateInstaller` an. Erstere verhindert den Download aktualisierter Workloads, Komponenten und so weiter. Letztere verhindert, dass das Installationsprogramm sich selbst über das Internet aktualisiert.

> [!IMPORTANT]
> Die `--noWeb`-Option verhindert nicht, dass das Visual Studio-Setup auf Computern mit Internetverbindung nach Updates sucht. Weitere Informationen finden Sie auf der Seite [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md).

### <a name="error-codes"></a>Fehlercodes

Wenn Sie den Parameter `--wait` nicht verwenden, wird je nach Ergebnis des Vorgangs die Umgebungsvariable `%ERRORLEVEL%` auf einen der folgenden Werte festgelegt:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Aktualisieren des Layouts einer Netzwerkinstallation

Wenn Produktupdates verfügbar sind, empfiehlt es sich, [das Layout der Netzwerkinstallation zu aktualisieren](update-a-network-installation-of-visual-studio.md), um aktualisierte Pakete einzubeziehen.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Erstellen eines Layouts für ein früheres Release von Visual Studio

::: moniker range="vs-2017"

> [!NOTE]
> Die unter [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) verfügbaren Visual Studio-Bootstrapper werden heruntergeladen und installieren bei ihrer Ausführung das neueste verfügbare Release von Visual Studio.
>
> Wenn Sie also heute einen Visual Studio-*Bootstrapper* herunterladen und diesen in sechs Monaten ausführen, wird das Visual Studio-Release installiert, das zum Zeitpunkt der Ausführung des Bootstrappers aktuell ist.
>
> Wenn Sie jedoch ein *Layout* erstellen und Installationen darüber ausführen, installiert das Layout die Version von Visual Studio, die im Layout vorhanden ist. Obwohl online ggf. eine neuere Version vorhanden ist, erhalten Sie die Version von Visual Studio im Layout.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Die unter [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads) verfügbaren Visual Studio-Bootstrapper werden heruntergeladen und installieren bei ihrer Ausführung das neueste verfügbare Release von Visual Studio.
>
> Wenn Sie also heute einen Visual Studio-*Bootstrapper* herunterladen und diesen in sechs Monaten ausführen, wird das Visual Studio-Release installiert, das zum Zeitpunkt der Ausführung des Bootstrappers aktuell ist.
>
> Wenn Sie jedoch ein *Layout* erstellen und Installationen darüber ausführen, installiert das Layout die Version von Visual Studio, die im Layout vorhanden ist. Obwohl online ggf. eine neuere Version vorhanden ist, erhalten Sie die Version von Visual Studio im Layout.

::: moniker-end

Wenn Sie ein Layout für eine ältere Version von Visual Studio erstellen müssen, wechseln Sie zu [https://my.visualstudio.com](https://my.visualstudio.com), um „korrigierte“ Versionen des Visual Studio-Bootstrappers herunterzuladen.

### <a name="how-to-get-support-for-your-offline-installer"></a>Gewusst wie: Anfordern von Support für Ihr Offlineinstallationsprogramm

Wenn ein Problem mit der Offlineinstallation auftritt, möchten wir dies erfahren. Die beste Möglichkeit, uns zu informieren, ist die Verwendung des [Problem melden](../ide/how-to-report-a-problem-with-visual-studio.md)-Tools. Wenn Sie dieses Tool verwenden, können Sie uns die Telemetriedaten und Protokolle senden, die wir benötigen, um uns Diagnose und Behebung des Problems zu erleichtern.

Für installationsbezogene Probleme wird außerdem eine [**Livechat**](https://visualstudio.microsoft.com/vs/support/#talktous)-Supportoption angeboten (nur auf Englisch).

Wir bieten auch noch weitere Supportoptionen. Eine Liste finden Sie auf unserer [Feedback](../ide/feedback-options.md)-Seite.

## <a name="see-also"></a>Siehe auch

- [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
- [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Beheben von Netzwerkfehlern beim Installieren oder Verwenden von Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
- [Projektlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing/)
- [Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung](update-servicing-baseline.md)
- [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
- [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](install-certificates-for-visual-studio-offline.md)