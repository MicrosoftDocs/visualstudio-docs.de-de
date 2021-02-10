---
title: Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio
titleSuffix: ''
description: Informationen zur Verwendung von Befehlszeilenparametern zum Steuern und Anpassen Ihrer Visual Studio-Installation
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d5bea30b8a046be55ba49a1cc1dbf12e3093585f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935657"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio

Wenn Sie Visual Studio von einer Befehlszeile aus installieren, können Sie die verschiedene Befehlszeilenparameter verwenden, um die Installation zu steuern und anzupassen. Über die Befehlszeile können Sie die folgenden Aktionen durchführen:

- Die Installation mit bestimmten vorab ausgewählten Optionen starten
- Den Installationsprozess automatisieren
- Einen Cache (Layout) der Installationsdateien für den späteren Gebrauch erstellen

Die Befehlszeilenoptionen werden in Verbindung mit dem Setup-Bootstrapper, die kleine Datei (1 MB), die den Downloadprozess initiiert, verwendet. Der Bootstrapper ist die erste ausführbare Datei, die gestartet wird, wenn Sie von der Visual Studio-Website herunterladen.

::: moniker range="vs-2017"

Informationen zum Herunterladen eines Bootstrappers für Visual Studio 2017 finden Sie auf der Downloadseite für [**frühere Versionen von Visual Studio**](https://visualstudio.microsoft.com/vs/older-downloads/).

::: moniker-end

::: moniker range="vs-2019"

Verwenden Sie die folgenden Links, um einen direkten Link zum neuesten Release-Bootstrapper für die Produktversion zu erhalten, die Sie installieren:

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Ihre Bootstrapperdatei entspricht oder ähnelt einem der folgenden Dateinamen:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Wenn Sie zuvor eine Bootstrapperdatei heruntergeladen haben und deren Version überprüfen möchten, gehen Sie wie folgt vor: Öffnen Sie in Windows den Datei-Explorer, klicken Sie mit der rechten Maustaste auf die Bootstrapperdatei, wählen Sie **Eigenschaften** aus, wählen Sie die Registerkarte **Details**  aus, und sehen Sie sich dann die Nummer der **Produktversion** an. Um diese Nummer einem Release von Visual Studio zuzuordnen, nutzen Sie die Informationen auf der Seite [Visual Studio-Buildnummern und -Veröffentlichungstermine ](visual-studio-build-numbers-and-release-dates.md).

## <a name="command-line-parameters"></a>Befehlszeilenparameter

 Bei Visual Studio-Befehlszeilenparametern wird zwischen Groß- und Kleinschreibung nicht unterschieden.

> Syntax: `vs_enterprise.exe [command] <options>...`

Ersetzen Sie `vs_enterprise.exe` nach Bedarf durch die Produktedition, die Sie installieren. (Alternativ können Sie auch `vs_installer.exe` verwenden.)

>[!TIP]
> Weitere Informationen zur Verwendung der Befehlszeile für die Installation von Visual Studio finden Sie auf der Seite mit [Beispielen für Befehlszeilenparameter](command-line-parameter-examples.md).

::: moniker range="vs-2017"

| **Befehl** | **Beschreibung** |
| ----------------------- | --------------- |
| (leer) | Installiert das Produkt. |
| `modify` | Ändert ein installiertes Produkt. |
| `update` | Aktualisiert ein installiertes Produkt. |
| `repair` | Repariert ein installiertes Produkt. |
| `uninstall` | Deinstalliert ein installiertes Produkt. |
| `export` | **Neuerungen in Version 15.9**: Exportieren einer Installationsauswahl in eine Installationskonfigurationsdatei **Hinweis:** Kann nur mit der Datei „vs_installer.exe“ verwendet werden. |

::: moniker-end

::: moniker range="vs-2019"

| **Befehl** | **Beschreibung** |
| ----------------------- | --------------- |
| (leer) | Installiert das Produkt. |
| `modify` | Ändert ein installiertes Produkt. |
| `update` | Aktualisiert ein installiertes Produkt. |
| `repair` | Repariert ein installiertes Produkt. |
| `uninstall` | Deinstalliert ein installiertes Produkt. |
| `export` | Exportieren einer Installationsauswahl in eine Installationskonfigurationsdatei **Hinweis:** Kann nur mit der Datei „vs_installer.exe“ verwendet werden. |

::: moniker-end

## <a name="install-options"></a>Installationsoptionen

::: moniker range="vs-2017"

| **Option installieren** | **Beschreibung** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Das Installationsverzeichnis für die Instanz, für die der Befehl ausgeführt wird. Für den Befehl „install“ ist dies **optional** und das Verzeichnis, in dem die Instanz installiert wird. Für andere Befehle ist es **erforderlich** und befindet sich dort, wo die vorherige Instanz installiert wurde. |
| `--addProductLang <language-locale>` | **Optional:** Während einer Installation oder eines Änderungsvorgangs bestimmt dies die UI-Sprachpakete, die für das Produkt installiert werden. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Wird diese Option nicht angegeben, verwendet die Installation das Gebietsschema des Computers. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--removeProductLang <language-locale>` | **Optional:** Während einer Installation oder eines Änderungsvorgangs bestimmt dies die UI-Sprachpakete, die vom Produkt entfernt werden sollen. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--add <one or more workload or component IDs>` | **Optional:** Eine oder mehrere hinzuzufügende Workload- oder Komponenten-IDs. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können mit `--includeRecommended` und/oder `--includeOptional` zusätzliche Komponenten global steuern. Wiederholen Sie den `--add`-Befehl, um mehrere Workloads oder Komponenten einzuschließen (z.B. `--add Workload1 --add Workload2`). Für eine umfassendere Steuerung können Sie `;includeRecommended` oder `;includeOptional` an die ID anfügen (z. B. `--add Workload1;includeRecommended` oder `--add Workload2;includeRecommended;includeOptional`). Weitere Informationen finden Sie auf der Seite [Workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs). Sie können dies Option bei Bedarf wiederholen.|
| `--remove <one or more workload or component IDs>` | **Optional:** Eine oder mehrere zu entfernende Workload- oder Komponenten-IDs. Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017). Sie können dies Option bei Bedarf wiederholen.|
| `--in <path>` | **Optional:** Der URI oder Pfad zu einer Antwortdatei  |
| `--all` | **Optional:** Gibt an, ob alle Workloads und Komponenten für ein Produkt installiert werden sollen |
| `--allWorkloads` | **Optional:** Installiert alle Workloads und Komponenten, aber keine empfohlenen oder optionalen Komponenten |
| `--includeRecommended` | **Optional:** Enthält die empfohlenen Komponenten für alle zu installierenden Workloads, aber keine optionalen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben. |
| `--includeOptional` | **Optional:** Enthält die optionalen Komponenten für alle zu installierenden Workloads, aber keine empfohlenen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben.  |
| `--quiet, -q` | **Optional:** Während der Installation wird keine Benutzeroberfläche angezeigt. |
| `--passive, -p` | **Optional:** Die Benutzeroberfläche wird angezeigt, es ist aber kein Eingreifen des Benutzers erforderlich. |
| `--norestart` | **Optional:** Wird diese Option angegeben, erfolgt bei Befehlen mit `--passive` oder `--quiet` kein automatischer Neustart des Computers (falls erforderlich).  Sie wird ignoriert, wenn weder `--passive` noch `--quiet` angegeben sind.  |
| `--nickname <name>` | **Optional:** Definiert den Spitznamen, der einem installierten Produkt zugewiesen wird. Der Spitzname darf nicht länger als 10 Zeichen sein.  |
| `--productKey` | **Optional:** Legt den Product Key fest, der für ein installiertes Produkt verwendet wird. Er besteht aus 25 alphanumerischen Zeichen im Format `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` oder `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Eine Offline-Version dieser Seite wird angezeigt. |
| `--config <path>` | **Optionales** und **Neues in 15.9:** Während eines Installations- oder Änderungsvorgangs werden die hinzuzufügenden Workloads und Komponenten basierend auf einer zuvor gespeicherten Installationskonfigurationsdatei ermittelt. Dieser Vorgang ist optional und entfernt keine Workloads oder Komponenten, wenn diese nicht in der Datei vorhanden sind. Außerdem werden Elemente, die nicht für das Produkt gelten, nicht hinzugefügt. Während eines Exportvorgangs wird der Speicherort bestimmt, an dem die Installationskonfigurationsdatei gespeichert wird. |

::: moniker-end

::: moniker range="vs-2019"

| **Option installieren** | **Beschreibung** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Das Installationsverzeichnis für die Instanz, für die der Befehl ausgeführt wird. Für den Befehl „install“ ist dies **optional** und das Verzeichnis, in dem die Instanz installiert wird. Für andere Befehle ist es **erforderlich** und befindet sich dort, wo die vorherige Instanz installiert wurde. |
| `--addProductLang <language-locale>` | **Optional:** Während einer Installation oder eines Änderungsvorgangs bestimmt dies die UI-Sprachpakete, die für das Produkt installiert werden. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Wird diese Option nicht angegeben, verwendet die Installation das Gebietsschema des Computers. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--removeProductLang <language-locale>` | **Optional:** Während einer Installation oder eines Änderungsvorgangs bestimmt dies die UI-Sprachpakete, die vom Produkt entfernt werden sollen. Die Option kann mehrfach in der Befehlszeile erscheinen, um mehrere Sprachpakete hinzuzufügen. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--add <one or more workload or component IDs>` | **Optional:** Eine oder mehrere hinzuzufügende Workload- oder Komponenten-IDs. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können mit `--includeRecommended` und/oder `--includeOptional` zusätzliche Komponenten global steuern. Wiederholen Sie den `--add`-Befehl, um mehrere Workloads oder Komponenten einzuschließen (z.B. `--add Workload1 --add Workload2`). Für eine umfassendere Steuerung können Sie `;includeRecommended` oder `;includeOptional` an die ID anfügen (z. B. `--add Workload1;includeRecommended` oder `--add Workload2;includeRecommended;includeOptional`). Weitere Informationen finden Sie auf der Seite [Workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs). Sie können dies Option bei Bedarf wiederholen.|
| `--remove <one or more workload or component IDs>` | **Optional:** Eine oder mehrere zu entfernende Workload- oder Komponenten-IDs. Weitere Informationen finden Sie auf unserer Seite [Visual Studio 2017 workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017). Sie können dies Option bei Bedarf wiederholen.|
| `--in <path>` | **Optional:** Der URI oder Pfad zu einer Antwortdatei  |
| `--all` | **Optional:** Gibt an, ob alle Workloads und Komponenten für ein Produkt installiert werden sollen |
| `--allWorkloads` | **Optional:** Installiert alle Workloads und Komponenten, aber keine empfohlenen oder optionalen Komponenten |
| `--includeRecommended` | **Optional:** Enthält die empfohlenen Komponenten für alle zu installierenden Workloads, aber keine optionalen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben. |
| `--includeOptional` | **Optional:** Enthält die optionalen Komponenten für alle zu installierenden Workloads, aber keine empfohlenen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben.  |
| `--quiet, -q` | **Optional:** Während der Installation wird keine Benutzeroberfläche angezeigt. |
| `--passive, -p` | **Optional:** Die Benutzeroberfläche wird angezeigt, es ist aber kein Eingreifen des Benutzers erforderlich. |
| `--norestart` | **Optional:** Wird diese Option angegeben, erfolgt bei Befehlen mit `--passive` oder `--quiet` kein automatischer Neustart des Computers (falls erforderlich).  Sie wird ignoriert, wenn weder `--passive` noch `--quiet` angegeben sind.  |
| `--nickname <name>` | **Optional:** Definiert den Spitznamen, der einem installierten Produkt zugewiesen wird. Der Spitzname darf nicht länger als 10 Zeichen sein.  |
| `--productKey` | **Optional:** Legt den Product Key fest, der für ein installiertes Produkt verwendet wird. Er besteht aus 25 alphanumerischen Zeichen im Format `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` oder `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Eine Offline-Version dieser Seite wird angezeigt. |
| `--config <path>` | **Optional:** Während eines Installations- oder Änderungsvorgangs werden die hinzuzufügenden Workloads und Komponenten basierend auf einer zuvor gespeicherten Installationskonfigurationsdatei ermittelt. Dieser Vorgang ist optional und entfernt keine Workloads oder Komponenten, wenn diese nicht in der Datei vorhanden sind. Außerdem werden Elemente, die nicht für das Produkt gelten, nicht hinzugefügt. Während eines Exportvorgangs wird der Speicherort bestimmt, an dem die Installationskonfigurationsdatei gespeichert wird. |

::: moniker-end

> [!IMPORTANT]
> Wenn Sie mehrere Workloads und Komponenten angeben, müssen Sie den `--add`- oder `--remove`-Befehlszeilenwechsel für jedes Element wiederholen.

## <a name="layout-options"></a>Layoutoptionen

::: moniker range="vs-2017"

| **Layoutoptionen** | **Beschreibung** |
| ----------------------- | --------------- |
| `--layout <dir>` | Gibt ein Verzeichnis an, in dem der Offlineinstallationscache erstellt wird. Weitere Informationen finden Sie unter [Erstellen einer Netzwerkinstallation von Visual Studio 2017](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Optional:** Wird mit `--layout` zur Vorbereitung eines Offlineinstallationscaches mit Ressourcenpaketen mit angegebenen Sprachen verwendet. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--add <one or more workload or component IDs>` | **Optional:** Eine oder mehrere hinzuzufügende Workload- oder Komponenten-IDs. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können mit `--includeRecommended` und/oder `--includeOptional` zusätzliche Komponenten global steuern. Für eine umfassendere Steuerung können Sie `;includeRecommended` oder `;includeOptional` an die ID anfügen (z. B. `--add Workload1;includeRecommended` oder `--add Workload2;includeOptional`). Weitere Informationen finden Sie auf der Seite [Workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs). <br/>**Hinweis:** Bei Verwenden von `--add` werden nur die angegebenen Workloads und Komponenten sowie deren Abhängigkeiten heruntergeladen. Wenn `--add` nicht angegeben ist, werden alle Workloads und Komponenten in das Layout heruntergeladen.|
| `--includeRecommended` | **Optional:** Enthält die empfohlenen Komponenten für alle zu installierenden Workloads, aber keine optionalen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben. |
| `--includeOptional` | **Optional:** Schließt die empfohlenen *und* optionalen Komponenten für alle Workloads in das Layout ein. Die Workloads werden mit `--add` angegeben.  |
| `--keepLayoutVersion` | **Neu in Version 15.3 (optional):** Wenden Sie Änderungen auf das Layout an, ohne die Version des Layouts aktualisieren zu müssen. |
| `--verify` | **Neu in Version 15.3 (optional):** Überprüfen Sie die Inhalte eines Layouts. Beschädigte oder fehlende Dateien werden aufgelistet. |
| `--fix` | **Neu in Version 15.3 (optional):** Überprüfen Sie die Inhalte eines Layouts. Wenn Dateien beschädigt sein oder fehlen sollten, werden sie erneut heruntergeladen. Für die Korrektur eines Layout ist ein Internetzugriff erforderlich. |
| `--clean <one or more paths to catalogs>` | **Neu in Version 15.3 (optional):** Entfernt alte Versionen der Komponenten aus einem Layout, das auf eine neuere Version aktualisiert wurde. |

| **Erweiterte Installationsoptionen** | **Beschreibung** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Optional:** Die ID des Kanals für die Instanz, die installiert werden soll. Diese Option ist für den Befehl „install“ erforderlich und kann für andere Befehle ignoriert werden, wenn `--installPath` angegeben ist. |
| `--channelUri <uri>` | **Optional:** Der URI des Kanalmanifests. Wenn keine Updates erwünscht sind, kann `--channelUri` auf eine nicht vorhandene Datei zeigen (z. B. --channelUri C:\doesntExist.chman). Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--installChannelUri <uri>` | **Optional:** Der URI des Kanalmanifests, der für die Installation verwendet werden soll. Der mit `--channelUri` festgelegte URI (der angegeben werden muss, wenn `--installChannelUri` angegeben ist) dient zum Ermitteln von Updates. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--installCatalogUri <uri>` | **Optional:** Der URI des Katalogmanifests, der für die Installation verwendet werden soll. Wird diese Option angegeben, versucht der Kanal-Manager, das Katalogmanifest von diesem URI herunterzuladen, bevor der URI im Installationskanalmanifest verwendet wird. Dieser Parameter wird zur Unterstützung der Offlineinstallation verwendet, wobei der Layoutcache mit dem bereits heruntergeladenen Produktkatalog erstellt wird. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--productId <id>` | **Optional**: Die ID des Produkts für die Instanz, die installiert wird. Diese ist bei normalen Installationsbedingungen bereits ausgefüllt. |
| `--wait` | **Optional:** Der Prozess wartet, bis die Installation abgeschlossen ist, bevor er einen Exitcode zurückgibt. Dies ist nützlich beim Automatisieren von Installationen, bei denen auf das Beenden von „install“ gewartet werden muss, um den Rückgabecode von „install“ zu verwenden. |
| `--locale <language-locale>` | **Optional:** Ändert die Anzeigesprache der Benutzeroberfläche für den Installer selbst. Die Einstellung wird beibehalten. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--cache` | **Neu in Version 15.2 (optional):** Falls vorhanden, werden Pakete nach ihrer Installation für nachfolgende Reparaturen gespeichert. Dies überschreibt die globale Richtlinieneinstellung für nachfolgende Installationen, Reparaturen und Änderungen. Die Standardrichtlinie sieht das Zwischenspeichern von Paketen im Cache vor. Dies wird für den Deinstallationsbefehl ignoriert. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |
| `--nocache` | **Neu in Version 15.2 (optional):** Falls vorhanden, werden Pakete nach ihrer Installation oder Reparatur gelöscht. Sie werden nur bei Bedarf erneut heruntergeladen und nach ihrer Verwendung wieder gelöscht. Dies überschreibt die globale Richtlinieneinstellung für nachfolgende Installationen, Reparaturen und Änderungen. Die Standardrichtlinie sieht das Zwischenspeichern von Paketen im Cache vor. Dies wird für den Deinstallationsbefehl ignoriert. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |
| `--noUpdateInstaller` | **Neu in Version 15.2 (optional):** Falls vorhanden, hindert den Installer daran, sich selbst zu aktualisieren, wenn „quiet“ angegeben ist. Der Befehl wird für den Installer einen Fehler auslösen, und der Installer gibt einen Exitcode ungleich 0 (null) zurück, falls „noUpdateInstaller“ mit „quiet“ angegeben wird, wenn ein Installerupdate erforderlich ist. |
| `--noWeb` | **Neu in Version 15.3 (optional):** Falls vorhanden, verwendet das Visual Studio-Setup die Dateien in Ihrem Layoutverzeichnis zum Installieren von Visual Studio. Wenn ein Benutzer versucht, Komponenten zu installieren, die nicht im Layout enthalten sind, wird das Setup nicht abgeschlossen.  Weitere Informationen finden Sie unter [Deploying from a network installation (Bereitstellung aus einer Netzwerkinstallation)](create-a-network-installation-of-visual-studio.md). <br/><br/> **Wichtig:** Dieser Schalter verhindert nicht, dass das Visual Studio-Setup nach Updates sucht. Weitere Informationen finden Sie unter [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **Neu in Version 15.7 (optional):** Zur Angabe der benutzerdefinierten Installationspfade für die Installation. Unterstützte Pfadnamen lauten: „shared“, „cache“ und „install“. |
| `--path cache=<path>` | **Neu in Version 15.7 (optional):** Verwendet den Speicherort, den Sie beim Herunterladen der Installationsdateien angeben. Dieser Speicherort kann nur bei der ersten Installation von Visual Studio festgelegt werden. Ein Beispiel: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Neu in Version 15.7 (optional):** Enthält freigegebene Dateien für parallele Visual Studio-Installationen. Einige Tools und SDKs werden an einen Speicherort auf diesem Datenträger installiert. Andere überschreiben möglicherweise diese Einstellung und werden auf einen anderen Datenträger installiert. Ein Beispiel: `--path shared="C:\VS\shared"` <br><br>Wichtig: Dies kann nur einmal festgelegt werden, und zwar bei der ersten Installation von Visual Studio. |
| `--path install=<path>` | **Neu in Version 15.7 (optional):** Entspricht `–-installPath`. Besonders `--installPath "C:\VS"` und `--path install="C:\VS"` sind gleichwertig. Es kann jeweils nur einer dieser Befehle verwendet werden. |

::: moniker-end

::: moniker range="vs-2019"

| **Layoutoptionen** | **Beschreibung** |
| ----------------------- | --------------- |
| `--layout <dir>` | Gibt ein Verzeichnis an, in dem der Offlineinstallationscache erstellt wird. Weitere Informationen finden Sie unter [Erstellen einer Netzwerkinstallation von Visual Studio 2017](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Optional:** Wird mit `--layout` zur Vorbereitung eines Offlineinstallationscaches mit Ressourcenpaketen mit angegebenen Sprachen verwendet. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--add <one or more workload or component IDs>` | **Optional:** Eine oder mehrere hinzuzufügende Workload- oder Komponenten-IDs. Die erforderlichen Komponenten des Artefakts werden installiert, die empfohlenen oder optionalen Komponenten jedoch nicht. Sie können mit `--includeRecommended` und/oder `--includeOptional` zusätzliche Komponenten global steuern. Für eine umfassendere Steuerung können Sie `;includeRecommended` oder `;includeOptional` an die ID anfügen (z. B. `--add Workload1;includeRecommended` oder `--add Workload2;includeOptional`). Weitere Informationen finden Sie auf der Seite [Workload and component IDs](workload-and-component-ids.md) (Arbeitsauslastungs- und Komponenten-IDs). <br/>**Hinweis:** Bei Verwenden von `--add` werden nur die angegebenen Workloads und Komponenten sowie deren Abhängigkeiten heruntergeladen. Wenn `--add` nicht angegeben ist, werden alle Workloads und Komponenten in das Layout heruntergeladen.|
| `--includeRecommended` | **Optional:** Enthält die empfohlenen Komponenten für alle zu installierenden Workloads, aber keine optionalen Komponenten. Die Workloads werden entweder mit `--allWorkloads` oder `--add` angegeben. |
| `--includeOptional` | **Optional:** Schließt die empfohlenen *und* optionalen Komponenten für alle Workloads in das Layout ein. Die Workloads werden mit `--add` angegeben.  |
| `--keepLayoutVersion` | **Optional:** Wenden Sie Änderungen auf das Layout an, ohne die Version des Layouts aktualisieren zu müssen. |
| `--verify` | **Optional:** Überprüfen Sie die Inhalte eines Layouts. Beschädigte oder fehlende Dateien werden aufgelistet. |
| `--fix` | **Optional:** Überprüfen Sie die Inhalte eines Layouts.  Wenn Dateien beschädigt sein oder fehlen sollten, werden sie erneut heruntergeladen. Für die Korrektur eines Layout ist ein Internetzugriff erforderlich. |
| `--clean <one or more paths to catalogs>` | **Optional:** Entfernt alte Versionen der Komponenten aus einem Layout, das auf eine neuere Version aktualisiert wurde. |

| **Erweiterte Installationsoptionen** | **Beschreibung** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Optional:** Die ID des Kanals für die Instanz, die installiert werden soll. Diese Option ist für den Befehl „install“ erforderlich und kann für andere Befehle ignoriert werden, wenn `--installPath` angegeben ist. |
| `--channelUri <uri>` | **Optional:** Der URI des Kanalmanifests. Wenn keine Updates erwünscht sind, kann `--channelUri` auf eine nicht vorhandene Datei zeigen (z. B. --channelUri C:\doesntExist.chman). Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--installChannelUri <uri>` | **Optional:** Der URI des Kanalmanifests, der für die Installation verwendet werden soll. Der mit `--channelUri` festgelegte URI (der angegeben werden muss, wenn `--installChannelUri` angegeben ist) dient zum Ermitteln von Updates. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--installCatalogUri <uri>` | **Optional:** Der URI des Katalogmanifests, der für die Installation verwendet werden soll. Wird diese Option angegeben, versucht der Kanal-Manager, das Katalogmanifest von diesem URI herunterzuladen, bevor der URI im Installationskanalmanifest verwendet wird. Dieser Parameter wird zur Unterstützung der Offlineinstallation verwendet, wobei der Layoutcache mit dem bereits heruntergeladenen Produktkatalog erstellt wird. Kann für den Befehl „install“ verwendet werden und wird für andere Befehle ignoriert. |
| `--productId <id>` | **Optional**: Die ID des Produkts für die Instanz, die installiert wird. Diese ist bei normalen Installationsbedingungen bereits ausgefüllt. |
| `--wait` | **Optional:** Der Prozess wartet, bis die Installation abgeschlossen ist, bevor er einen Exitcode zurückgibt. Dies ist nützlich beim Automatisieren von Installationen, bei denen auf das Beenden von „install“ gewartet werden muss, um den Rückgabecode von „install“ zu verwenden. |
| `--locale <language-locale>` | **Optional:** Ändert die Anzeigesprache der Benutzeroberfläche für den Installer selbst. Die Einstellung wird beibehalten. Weitere Informationen finden Sie im Abschnitt [Liste der Gebietsschemas](#list-of-language-locales) dieser Seite.|
| `--cache` | **Optional:** Falls vorhanden, werden Pakete nach ihrer Installation für nachfolgende Reparaturen gespeichert. Dies überschreibt die globale Richtlinieneinstellung für nachfolgende Installationen, Reparaturen und Änderungen. Die Standardrichtlinie sieht das Zwischenspeichern von Paketen im Cache vor. Dies wird für den Deinstallationsbefehl ignoriert. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |
| `--nocache` | **Optional:** Falls vorhanden, werden Pakete nach ihrer Installation oder Reparatur gelöscht. Sie werden nur bei Bedarf erneut heruntergeladen und nach ihrer Verwendung wieder gelöscht. Dies überschreibt die globale Richtlinieneinstellung für nachfolgende Installationen, Reparaturen und Änderungen. Die Standardrichtlinie sieht das Zwischenspeichern von Paketen im Cache vor. Dies wird für den Deinstallationsbefehl ignoriert. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |
| `--noUpdateInstaller` | **Optional:** Falls vorhanden, hindert den Installer daran, sich selbst zu aktualisieren, wenn „quiet“ angegeben ist. Der Befehl wird für den Installer einen Fehler auslösen, und der Installer gibt einen Exitcode ungleich 0 (null) zurück, falls „noUpdateInstaller“ mit „quiet“ angegeben wird, wenn ein Installerupdate erforderlich ist. |
| `--noWeb` | **Optional:** Falls vorhanden, verwendet das Visual Studio-Setup die Dateien in Ihrem Layoutverzeichnis zum Installieren von Visual Studio. Wenn ein Benutzer versucht, Komponenten zu installieren, die nicht im Layout enthalten sind, wird das Setup nicht abgeschlossen.  Weitere Informationen finden Sie unter [Deploying from a network installation (Bereitstellung aus einer Netzwerkinstallation)](create-a-network-installation-of-visual-studio.md). <br/><br/> **Wichtig:** Dieser Schalter verhindert nicht, dass das Visual Studio-Setup nach Updates sucht. Weitere Informationen finden Sie unter [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md). **Neu in 16.3.5**: Dieser Schalter verhindert Fehler und verbessert die Leistung bei Offlineinstallationen und -Updates.|
| `--path <name>=<path>` | **Optional:** Zur Angabe der benutzerdefinierten Installationspfade für die Installation. Unterstützte Pfadnamen lauten: „shared“, „cache“ und „install“. |
| `--path cache=<path>` | **Optional:** Verwendet den Speicherort, den Sie beim Herunterladen der Installationsdateien angeben. Dieser Speicherort kann nur bei der ersten Installation von Visual Studio festgelegt werden. Ein Beispiel: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Optional:** Enthält freigegebene Dateien für parallele Visual Studio-Installationen. Einige Tools und SDKs werden an einen Speicherort auf diesem Datenträger installiert. Andere überschreiben möglicherweise diese Einstellung und werden auf einen anderen Datenträger installiert. Ein Beispiel: `--path shared="C:\VS\shared"` <br><br>Wichtig: Dies kann nur einmal festgelegt werden, und zwar bei der ersten Installation von Visual Studio. |
| `--path install=<path>` | **Optional:** Entspricht `–-installPath`. Besonders `--installPath "C:\VS"` und `--path install="C:\VS"` sind gleichwertig. Es kann jeweils nur einer dieser Befehle verwendet werden. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>Liste der Arbeitsauslastungs-IDs und Komponenten-IDs

Eine Liste der Arbeitsauslastungs- und Komponenten-IDs, sortiert nach Visual Studio-Produkt, finden Sie auf der Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Liste der Gebietsschemas

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

## <a name="error-codes"></a>Fehlercodes

Je nach Ergebnis des Vorgangs wird die Umgebungsvariable `%ERRORLEVEL%` auf einen der folgenden Werte festgelegt:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Jeder Vorgang generiert mehrere Protokolldateien im `%TEMP%`-Verzeichnis, die den Status der Installation angeben. Sortieren Sie die Ordner nach Datum, und suchen Sie Dateien für jeweils den Bootstrapper, die Installer-App und die Setup-Engine, die mit `dd_bootstrapper`, `dd_client` und `dd_setup` beginnen.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

- [Beispiele für Befehlszeilenparameter für die Installation von Visual Studio](command-line-parameter-examples.md)
- [Erstellen einer Offlineinstallation von Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatisieren der Visual Studio-Installation mit einer Antwortdatei](automated-installation-with-response-file.md)
- [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
