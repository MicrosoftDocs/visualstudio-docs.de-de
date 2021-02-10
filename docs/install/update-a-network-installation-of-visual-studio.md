---
title: Aktualisieren einer netzwerkbasierten Installation
description: Erfahren Sie, wie Sie eine netzwerkbasierte Installation von Visual Studio mit dem Befehl „--layout“ aktualisieren.
ms.date: 06/29/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6829bac79f747d4f9bacfe5e71f57352fcad0970
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959154"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualisieren einer netzwerkbasierten Installation von Visual Studio

Es ist möglich, ein Layout für die Netzwerkinstallation von Visual Studio mit den neuesten Produktupdates zu aktualisieren, sodass es sowohl als Installationspfad für das neueste Update von Visual Studio auch zum Warten von Installationen verwendet werden kann, die bereits auf Clientarbeitsstationen bereitgestellt wurden.

## <a name="how-to-update-a-network-layout"></a>Gewusst wie: Aktualisieren eines Netzwerklayouts

> [!IMPORTANT]
> Bei diesen Anweisungen wird vorausgesetzt, dass Sie zuvor ein Layout für die Netzwerkinstallation erstellt haben. Weitere Informationen hierzu finden Sie auf der Seite [Erstellen einer Netzwerkinstallation von Visual Studio](create-a-network-installation-of-visual-studio.md).

Wenn Sie die Netzwerkinstallationsfreigabe mit den neuesten Updates aktualisieren möchten, führen Sie den Befehl `--layout` aus, um aktualisierte Pakete schrittweise herunterzuladen.

::: moniker range="vs-2017"

**Neues in 15.3:** Wenn Sie [beim Erstellen des Netzwerklayouts](create-a-network-installation-of-visual-studio.md) ein Teillayout ausgewählt haben, werden diese Einstellungen gespeichert. Alle zukünftigen Layoutbefehle verwenden die vorherigen Optionen und alle neuen, die Sie angeben. Wenn Sie jedoch ein Layout einer früheren Version verwenden, sollten Sie dieselben Befehlszeilenparameter verwenden, die Sie beim ersten Erstellen des Layouts für die Netzwerkinstallation verwendet haben (d.h. dieselben Workloads und Sprachen), um den Inhalt zu aktualisieren.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie [beim Erstellen des Netzwerklayouts](create-a-network-installation-of-visual-studio.md) ein Teillayout ausgewählt haben, werden diese Einstellungen gespeichert. Alle zukünftigen Layoutbefehle verwenden die vorherigen Optionen und alle neuen, die Sie angeben.

::: moniker-end

Wenn Sie ein Layout in einer Dateifreigabe hosten, sollten Sie eine private Kopie des Layouts aktualisieren (z. B. C:\VSLayout) und diese, nachdem alle aktualisierten Inhalte heruntergeladen wurden, in Ihre Dateifreigabe kopieren (z. B. \\server\products\VS). Wenn Sie dies nicht tun, ist es wahrscheinlicher, dass Benutzer, die das Setup ausführen, während Sie das Layout aktualisieren, nicht alle Inhalte aus dem Layout erhalten, da es noch nicht vollständig aktualisiert wurde.

Hier finden Sie einige ausführliche Beispiele für das Erstellen und Aktualisieren eines Layouts:

* Hier ist erst einmal ein Beispiel für die Erstellung eines Layouts mit nur einer Workload für Englisch:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* So aktualisieren Sie dasselbe Layout auf eine neuere Version. Sie müssen dazu keine zusätzlichen Befehlszeilenparameter angeben. Die vorherigen Einstellungen wurden gespeichert und werden durch nachfolgende Layoutbefehle in diesem Layoutordner verwendet.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* So ändern Sie Ihr Layout unbeaufsichtigt in eine neuere Version. Der Layoutvorgang führt den Setupprozess in einem neuen Konsolenfenster aus. Das Fenster bleibt geöffnet, sodass sich die Benutzer das endgültige Ergebnis und ggf. eine Zusammenfassung der aufgetretenen Fehler ansehen können. Wenn Sie einen Layoutvorgang unbeaufsichtigt durchführen (wenn Sie z.B. über ein Skript verfügen, das regelmäßig ausgeführt wird, um ihr Layout auf die aktuelle Version zu aktualisieren), verwenden Sie den Parameter `--passive`, und der Vorgang schließt das Fenster automatisch.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* So fügen Sie eine zusätzliche Workload und lokalisierte Sprachen hinzu.  (Mit diesem Befehl wird die Workload *Azure-Entwicklung* hinzugefügt.)  Nun sind sowohl der verwaltete Desktop und Azure in diesem Layout enthalten.  Die Sprachressourcen für Englisch und Deutsch sind für all diese Workloads enthalten.  Außerdem wird das Layout auf die neueste Version aktualisiert.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Neu hinzugefügte optionale Komponenten werden nicht durch einen Updatevorgang installiert. Wenn Sie die neu hinzugefügten optionalen Komponenten benötigen, entfernen Sie die alten optionalen Komponenten in der [Antwortdatei](automated-installation-with-response-file.md) `Layout.JSON`, und fügen Sie die erforderlichen Komponenten im Abschnitt „Hinzufügen“ von `Layout.JSON` ein. 
    >
    > **Problemumgehung:** Führen Sie einen separaten modify-Vorgang nach einem Upgrade aus, um die fehlenden Komponenten zu installieren.

* Und so wird eine zusätzliche Workload und die lokalisierte Sprache hinzugefügt, ohne die Version zu aktualisieren. (Mit diesem Befehl wird die Workload *ASP.NET und Webentwicklung* hinzugefügt.)  Nun sind der verwaltete Desktop, Azure und die ASP.NET & Webentwicklungsworkloads in diesem Layout enthalten. Die Sprachressourcen für Englisch, Deutsch und Französisch sind auch für all diese Workloads enthalten.  Das Layout wurde bei der Ausführung dieses Befehls jedoch nicht auf die neueste verfügbare Version aktualisiert. Es bleibt weiterhin in der vorhandenen Version.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>Bereitstellen eines Updates auf Clientcomputern

Je nach Konfiguration Ihrer Netzwerkumgebung kann ein Update entweder von einem Unternehmensadministrator bereitgestellt oder auf einem Clientcomputer ausgelöst werden.

* Benutzer können eine Instanz von Visual Studio aktualisieren, die über einen Offlineinstallationsordner installiert wurde:
  * Führen Sie den Visual Studio-Installer aus.
  * Klicken Sie auf **Aktualisieren**.

::: moniker range="vs-2017"

* Administratoren können Clientbereitstellungen von Visual Studio ohne Benutzereingriff mit zwei separaten Befehlen aktualisieren:
  * Aktualisieren Sie zunächst den Visual Studio-Installer: <br>```vs_enterprise.exe --quiet --update```
  * Aktualisieren Sie anschließend die Visual Studio-Anwendung selbst: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Administratoren können Clientbereitstellungen von Visual Studio ohne Benutzereingriff mit zwei separaten Befehlen aktualisieren:
  * Aktualisieren Sie zunächst den Visual Studio-Installer: <br>```vs_enterprise.exe --quiet --update```
  * Aktualisieren Sie anschließend die Visual Studio-Anwendung selbst: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Verwenden Sie den Befehl [vswhere.exe](tools-for-managing-visual-studio-instances.md), um den Installationspfad einer vorhandenen Instanz von Visual Studio auf einem Clientcomputer zu bestimmen.
>
> [!TIP]
> Weitere Informationen dazu, wie Sie steuern, wann Updatebenachrichtigungen Benutzern angezeigt werden, finden Sie unter [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md).

## <a name="verify-a-layout"></a>Überprüfen eines Layouts

Verwenden Sie `--verify`, um für den angegebenen Offlinecache eine Überprüfung auszuführen. Dabei wird überprüft, ob Paketdateien fehlen oder ungültig sind. Am Ende der Überprüfung wird die Liste der fehlenden und ungültigen Dateien ausgegeben.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

Die Datei „vs_enterprise.exe“ kann innerhalb von „layoutDir“ aufgerufen werden.

> [!NOTE]
> Einige wichtige Metadatendateien, die für die Option `--verify` erforderlich sind, müssen im Layoutofflinecache vorhanden sein. Wenn diese Metadatendateien fehlen, kann "--verify" nicht ausgeführt werden, und das Setup gibt einen Fehler aus. Wenn dieser Fehler bei Ihnen auftritt, erstellen Sie ein neues Offlinelayout in einem anderen Ordner (oder im selben Offlinecacheordner). Führen Sie dazu den gleichen Layoutbefehl aus, mit dem Sie das anfängliche Offlinelayout erstellt haben. Beispielsweise `vs_enterprise.exe --layout <layoutDir>`.

Microsoft liefert in regelmäßigen Abständen Updates für Visual Studio. Ihr neues Layout hat möglicherweise nicht die gleiche Version wie das anfängliche Layout.

> [!NOTE]
> Die Überprüfung funktioniert nur mit der neuesten Version einer bestimmten Nebenversion von Visual Studio. Sobald eine neue Version veröffentlicht wird, funktioniert die Überprüfung für frühere Patchlevel-Releases der gleichen Nebenversion nicht mehr.

## <a name="fix-a-layout"></a>Korrigieren eines Layouts

Verwenden Sie `--fix`, um die gleiche Überprüfung wie mit `--verify` durchzuführen, und versuchen Sie außerdem, die identifizierten Probleme zu beheben. Der `--fix`-Prozess benötigt eine Internetverbindung, also stellen Sie sicher, dass Ihr Computer mit dem Internet verbunden ist, bevor Sie `--fix` aufrufen.

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

Die Datei „vs_enterprise.exe“ kann innerhalb von „layoutDir“ aufgerufen werden.

## <a name="remove-older-versions-from-a-layout"></a>Entfernen älterer Versionen aus einem Layout

Nach dem Ausführen von Layoutupdates für einen Offlinecache enthält der Layoutcacheordner möglicherweise einige veraltete Pakete, die für die neueste Visual Studio-Installation nicht mehr gebraucht werden. Sie können die Option `--clean` verwenden, um veraltete Pakete aus einem Offlinecacheordner zu entfernen.

Dazu benötigen Sie die Dateipfade zu den Katalogmanifesten, die diese veralteten Pakete enthalten. Die Katalogmanifeste finden Sie in einem Ordner „Archiv“ im Offlinelayoutcache. Sie werden gespeichert, wenn Sie ein Layout aktualisieren. Im Ordner „Archiv“ befindet sich mindestens ein Ordner namens „GUID“, der jeweils ein veraltetes Katalogmanifest enthält. Die Anzahl der GUID-Ordner sollte der Anzahl der Updates entsprechen, die für Ihren Offlinecache ausgeführt wurden.

Einige Dateien werden in jedem GUID-Ordner gespeichert. Die beiden interessantesten Dateien sind „catalog.json“ und „version.txt“. Die Datei „catalog.json“ ist das veraltete Katalogmanifest, das Sie an die Option `--clean` übergeben müssen. Die andere Datei, „version.txt“, enthält die Version des veralteten Katalogmanifests. Auf Grundlage der Versionsnummer können Sie entscheiden, ob veraltete Pakete aus diesem Katalogmanifest entfernt werden sollen. Sie können diesen Vorgang beim Durchgehen der anderen GUID-Ordner wiederholen. Nachdem Sie entschieden haben, welche Kataloge Sie bereinigen möchten, führen Sie den Befehl `--clean` aus, indem Sie die Dateipfade für diese Kataloge angeben.

Hier sind einige Beispiele für die Verwendung der Option „--clean“:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Sie können „vs_enterprise.exe“ auch innerhalb von &lt;layoutDir&gt; aufrufen. Im Folgenden ein Beispiel:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Wenn Sie diesen Befehl ausführen, analysiert das Setup Ihren Offlinecacheordner, um die Liste der Dateien zu suchen, die entfernt werden. Sie haben dann die Gelegenheit, die Dateien, die gelöscht werden sollen, zu überprüfen und den Löschvorgang zu bestätigen.

## <a name="get-support-for-your-offline-installer"></a>Anfordern von Support für Ihr Offlineinstallationsprogramm

Wenn ein Problem mit der Offlineinstallation auftritt, möchten wir dies erfahren. Die beste Möglichkeit, uns zu informieren, ist die Verwendung des [Problem melden](../ide/how-to-report-a-problem-with-visual-studio.md)-Tools. Wenn Sie dieses Tool verwenden, können Sie uns die Telemetriedaten und Protokolle senden, die wir benötigen, um uns Diagnose und Behebung des Problems zu erleichtern.

Für installationsbezogene Probleme wird außerdem ein [**Livechat**](https://visualstudio.microsoft.com/vs/support/#talktous) (nur auf Englisch) als Supportoption angeboten.

Wir bieten auch noch weitere Supportoptionen. Eine Liste finden Sie auf unserer [Feedback](../ide/feedback-options.md)-Seite.

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
* [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
* [Projektlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing/)
