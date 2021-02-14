---
title: Team Foundation-Versionskontrolle (TFVC)
description: Ein Leitfaden zur Problembehandlung für TFVC und macOS.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: 11b0788317cd0a20dd27159aa241db32e3818daf
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722125"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Unterstützt Visual Studio für Mac die Team Foundation-Versionskontrolle?

> [!CAUTION]
> Die Vorschauversion der TFVC-Erweiterung für Visual Studio für Mac wird in Visual Studio 2019 für Mac nicht mehr unterstützt.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Alternative Optionen für die Versionskontrolle in Visual Studio für Mac

Um die beste Versionskontrolle unter macOS zu erzielen, empfehlen wir die Verwendung von **Git** anstelle von Team Foundation Version Control (TFVC). 

Git wird in Visual Studio für Mac unterstützt und ist die Standardoption für Repositorys, die in Team Foundation Server (TFS)/Azure DevOps gehostet werden. Weitere Informationen zur Verwendung von Git mit TFS/Azure DevOps finden Sie im Artikel [Einrichten eines Git-Repositorys](./set-up-git-repository.md).

## <a name="unsupported-workarounds-for-tfvc"></a>Nicht unterstützte Problemumgehungen für TFVC

Obwohl Visual Studio für Mac TFVC offiziell nicht unterstützt, finden Sie im Rest dieses Leitfadens einige Problemumgehungen für TFVC unter macOS. Wenn Sie heute TFVC für die Versionskontrolle verwenden, finden Sie hier einige Lösungen, mit denen Sie auf Ihren in TFVC gehosteten Quellcode zugreifen können:

* Option 1. [ Verwenden von Visual Studio Code und der Azure Repos-Erweiterung für eine grafische Benutzeroberfläche](#use-visual-studio-code-and-the-azure-repos-extension)
* Option 2. [Verbinden mit Ihrem Repository über den Team Explorer Everywhere Command Line Client (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>Option 1. <a id="use-visual-studio-code-and-the-azure-repos-extension"></a> Verwenden von Visual Studio Code und der Azure Repos-Erweiterung

Wenn Sie mit einer grafischen Oberfläche arbeiten möchten, um Ihre Dateien in der Versionskontrolle zu verwalten, dann bietet die Azure Repos-Erweiterung für Visual Studio Code eine unterstützte Lösung von Microsoft. Um zu beginnen, laden Sie [Visual Studio Code](https://code.visualstudio.com) herunter, und erfahren Sie dann, wie Sie [die Azure Repos-Erweiterung konfigurieren](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>Option 2. <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a> Verbinden über den Team Explorer Everywhere Command Line Client

> [!IMPORTANT]
> Gemäß der README-Datei von Team Explorer Everywhere wird dieses Projekt [nicht mehr gewartet](https://github.com/microsoft/team-explorer-everywhere).

Wenn Sie mit der Verwendung des macOS-Terminals vertraut sind, bietet der Team Explorer Everywhere Command Line Client (TEE-CLC) eine unterstützte Möglichkeit, sich mit Ihrer Quelle in TFVC zu verbinden.

Sie können die folgenden Schritte ausführen, um Ihre Verbindung zu TFVC einzurichten und Änderungen zu committen.

#### <a name="setting-up-the-tee-clc"></a>Einrichten des TEE-CLC

Es gibt zwei Möglichkeiten, einen TEE-CLC einzurichten.

* Verwenden von Homebrew, um den Client installieren oder
* Herunterladen und den Client manuell zu installieren

Die einfachste Lösung ist **HomeBrew**, ein Paket-Manager für macOS. So führen Sie die Installation mit dieser Methode aus:

1. Starten Sie die MacOS-Terminal-Anwendung.
1. Installieren Sie Homebrew mit dem Terminal und den Anweisungen auf der [Homebrew-Homepage](https://brew.sh/).
1. Sobald Homebrew installiert ist, führen Sie den folgenden Befehl über Ihr Terminal aus: `brew install tee-clc`

So **richten Sie TEE-CLC manuell ein**:

1. [Laden Sie die neueste Version des TEE-CLC](https://github.com/Microsoft/team-explorer-everywhere/releases) von Seite zum Release von Team Explorer Everywhere--GitHub-Repository herunter (z.B. tee-clc-14.134.0.0.zip zum Zeitpunkt der Erstellung dieses Artikels).
1. Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner auf Ihrem Datenträger.
1. Öffnen Sie die macOS-Terminal-App und wechseln Sie mit dem Befehl `cd` zu dem Ordner, den Sie im vorherigen Schritt verwendet haben.
1. Führen Sie innerhalb des Ordners den Befehl `./tf` aus, um zu testen, ob der CLS ausgeführt werden kann. Sie werden möglicherweise aufgefordert, Java oder andere Abhängigkeiten zu installieren.

Sobald die TEE-CLC installiert ist, können Sie den Befehl `tf eula` ausführen, um die Lizenzvereinbarung für den Client anzuzeigen und anzunehmen.

Um sich mit Ihrer TFS/Azure DevOps-Umgebung zu authentifizieren, müssen Sie schließlich einen persönlichen Zugriffstoken auf dem Server erstellen. Erfahren Sie mehr über [Authentifizierung mit persönlichen Zugriffstoken](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops&preserve-view=true). Wenn Sie ein persönliches Zugriffstoken für TFVC erstellen, stellen Sie sicher, dass Sie bei der Konfiguration des Token vollen Zugriff haben.

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Verwenden des TEE-CLC zum Verbinden mit Ihrem Repository

Um eine Verbindung zu Ihrem Quellcode herzustellen, müssen Sie zunächst mit dem Befehl `tf workspace` einen Arbeitsbereich erstellen. Die folgenden Befehle stellen beispielsweise einen Verbindung mit einer Organisation in Azure DevOps Services namens „MyOrganization“ her: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Die Umgebungseinstellung `TF_AUTO_SAVE_CREDENTIALS` wird verwendet, um Ihre Anmeldeinformationen zu speichern, damit Sie sie nicht mehrmals eingeben müssen. Wenn Sie nach einem Benutzernamen gefragt werden, verwenden Sie den persönlichen Zugangscode, den Sie im vorherigen Abschnitt erstellt haben, und verwenden Sie ein leeres Kennwort.

Um eine Zuordnung Ihrer Quelldateien zu einem lokalen Ordner zu erstellen, verwenden Sie den Befehl `tf workfold`. Das folgende Beispiel bildet einen Ordner namens „WebApp.Services“ aus dem TFVC-Projekt „MyRepository“ ab und richtet ihn so ein, dass er in den lokalen Ordner ~/Projekte/ kopiert wird (d.h. einen Ordner „Projects“ im Ausgangsordner des aktuellen Benutzers).

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Abschließend verwenden Sie den folgenden Befehl, um die Quelldateien vom Server abzurufen und lokal zu kopieren:

```bash
tf get
```

#### <a name="committing-changes-using-the-tee-clc"></a>Committen von Änderungen mithilfe des TEE-CLC

Nachdem Sie Änderungen an Ihren Dateien in Visual Studio für Mac vorgenommen haben, können Sie zum Terminal zurückkehren, um Ihre Änderungen einzuchecken. Der Befehl `tf add` wird verwendet, um Dateien zur Liste der ausstehenden Änderungen hinzuzufügen, die eingecheckt werden sollen, und der Befehl `tf checkin` führt das eigentliche Einchecken auf dem Server durch. Der Befehl `checkin` enthält Parameter, um einen Kommentar hinzuzufügen oder einem zugehörigen Arbeitselement zuzuordnen. Im folgenden Codeausschnitt werden alle Dateien in einem `WebApp.Services` Ordner rekursiv zum Einchecken hinzugefügt. Anschließend wird der Code mit einem Kommentar eingecheckt und einem Arbeitselement mit der ID „42“ zugeordnet.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Um mehr über die hier genannten oder andere Befehle zu erfahren, können Sie den folgenden Befehl aus dem Terminal verwenden:

`tf help`

## <a name="see-also"></a>Siehe auch

- [Entwickeln und Freigeben von Code in TFVC mit Visual Studio (unter Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)