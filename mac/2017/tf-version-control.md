---
title: Team Foundation-Versionskontrolle (TFVC)
description: Herstellen einer Verbindung zwischen Visual Studio für Mac und Team Foundation Server/Azure DevOps mit der Team Foundation-Versionskontrolle (TFVC)
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/25/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: b9aa9b718ad4618502a58185c27333d689c74300
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729378"
---
# <a name="connecting-to-team-foundation-version-control"></a>Herstellen einer Verbindung mit der Team Foundation-Versionskontrolle

> [!NOTE]
> Für die beste Versionskontrolle unter macOS empfehlen wir die Verwendung von Git anstelle von Team Foundation Version Control (TFVC). Git wird in Visual Studio für Mac unterstützt und ist die Standardoption für Repositorys, die in Team Foundation Server (TFS)/Azure DevOps gehostet werden. Weitere Informationen zur Verwendung von Git mit TFS/Azure DevOps finden Sie im Artikel [Einrichten eines Git-Repository](./set-up-git-repository.md).
>
> Wenn Sie zuvor die Vorschauversion der TFVC-Erweiterung für Visual Studio für Mac verwendet haben: Diese wird beim Upgrade auf Visual Studio 2019 für Mac nicht mehr unterstützt.

Azure Repos bietet zwei Modelle der Versionskontrolle: [Git](/azure/devops/repos/git/?view=azure-devops&preserve-view=true), ein verteiltes Versionskontrollsystem oder ein zentralisiertes Versionskontrollsystem mit [Team Foundation-Versionskontrolle](/azure/devops/repos/tfvc/index?view=azure-devops&preserve-view=true) (TFVC).

Visual Studio für Mac bietet volle Unterstützung für Git-Repositorys, erfordert aber einige Workarounds, um mit TFVC zu arbeiten. Wenn Sie heute TFVC für die Versionskontrolle verwenden, finden Sie hier einige Lösungen, mit denen Sie auf Ihren in TFVC gehosteten Quellcode zugreifen können:

* [Verwenden von Visual Studio Code und der Azure Repos-Erweiterung für eine grafische Benutzeroberfläche](#use-visual-studio-code-and-the-azure-repos-extension)
* [Verbinden mit Ihrem Repository über den Team Explorer Everywhere Command Line Client (TEE-CLC)](#connecting-using-the-team-explorer-everywhere-command-line-client)
* [Herstellen einer Verbindung mit TFVC über die (nicht unterstützte) Erweiterung für die Team Foundation-Versionskontrolle für Visual Studio für Mac](#connect-to-tfvc-using-the-team-foundation-version-control-extension)

Der Rest dieses Artikels führt Sie durch die oben aufgeführten Optionen.

## <a name="requirements"></a>Requirements (Anforderungen)

* Visual Studio Community, Professional oder Enterprise für Mac 7.8 und höher
* Azure DevOps Services, Team Foundation Server 2013 und höher oder Azure DevOps Server 2018 und höher
* Ein Projekt in Azure DevOps Services oder Team Foundation Server/Azure DevOps Server, das für die Verwendung der Team Foundation-Versionskontrolle konfiguriert ist.

## <a name="use-visual-studio-code-and-the-azure-repos-extension"></a>Verwenden von Visual Studio Code und der Azure Repos-Erweiterung

Wenn Sie mit einer grafischen Oberfläche arbeiten möchten, um Ihre Dateien in der Versionskontrolle zu verwalten, dann bietet die Azure Repos-Erweiterung für Visual Studio Code eine unterstützte Lösung von Microsoft. Um zu beginnen, laden Sie [Visual Studio Code](https://code.visualstudio.com) herunter, und erfahren Sie dann, wie Sie [die Azure Repos-Erweiterung konfigurieren](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team).

## <a name="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Verbinden über den Team Explorer Everywhere Command Line Client

Wenn Sie mit der Verwendung des macOS-Terminals vertraut sind, bietet der Team Explorer Everywhere Command Line Client (TEE-CLC) eine unterstützte Möglichkeit, sich mit Ihrer Quelle in TFVC zu verbinden.

Sie können die folgenden Schritte ausführen, um Ihre Verbindung zu TFVC einzurichten und Änderungen zu committen.

### <a name="setting-up-the-tee-clc"></a>Einrichten des TEE-CLC

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

### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Verwenden des TEE-CLC zum Verbinden mit Ihrem Repository

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

### <a name="committing-changes-using-the-tee-clc"></a>Committen von Änderungen mithilfe des TEE-CLC

Nachdem Sie Änderungen an Ihren Dateien in Visual Studio für Mac vorgenommen haben, können Sie zum Terminal zurückkehren, um Ihre Änderungen einzuchecken. Der Befehl `tf add` wird verwendet, um Dateien zur Liste der ausstehenden Änderungen hinzuzufügen, die eingecheckt werden sollen, und der Befehl `tf checkin` führt das eigentliche Einchecken auf dem Server durch. Der Befehl `checkin` enthält Parameter, um einen Kommentar hinzuzufügen oder einem zugehörigen Arbeitselement zuzuordnen. Im folgenden Codeausschnitt werden alle Dateien in einem `WebApp.Services` Ordner rekursiv zum Einchecken hinzugefügt. Anschließend wird der Code mit einem Kommentar eingecheckt und einem Arbeitselement mit der ID „42“ zugeordnet.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Um mehr über die hier genannten oder andere Befehle zu erfahren, können Sie den folgenden Befehl aus dem Terminal verwenden:

`tf help`

## <a name="connect-to-tfvc-using-the-team-foundation-version-control-extension"></a>Herstellen einer Verbindung mit TFVC über die Erweiterung für die Team Foundation-Versionskontrolle

> [!NOTE]
> Für die beste Versionskontrolle unter macOS empfehlen wir die Verwendung von Git anstelle von Team Foundation Version Control (TFVC). Git wird in Visual Studio für Mac unterstützt und ist die Standardoption für Repositorys, die in Team Foundation Server (TFS)/Azure DevOps gehostet werden. Weitere Informationen zur Verwendung von Git mit TFS/Azure DevOps finden Sie im Artikel [Einrichten eines Git-Repository](./set-up-git-repository.md).
>
> Wenn Sie zuvor die Vorschauversion der TFVC-Erweiterung für Visual Studio für Mac verwendet haben: Diese wird beim Upgrade auf Visual Studio 2019 für Mac nicht mehr unterstützt.

Im Katalog für die Visual Studio für Mac-Erweiterung finden Sie eine Team Foundation Version Control-Erweiterung, die nur begrenzte Unterstützung für die Verbindung mit TFVC bietet. Die Erweiterung wird nicht unterstützt und hat mehrere bekannte Probleme, sodass Ihre Erfahrung bei der Verwendung variieren kann.

Um die Erweiterung zu installieren, starten Sie Visual Studio für Mac und wählen Sie das Menü **Visual Studio > Erweiterungen**. Klicken Sie auf der Registerkarte **Katalog** auf **Versionskontrolle > Team Foundation-Versionskontrolle für TFS and Azure DevOps** und anschließend auf **Installieren**:

![Erweiterungs-Manager](media/tfvc-install.png)

Befolgen Sie die Anweisungen zum Installieren der Erweiterung. Starten Sie die IDE neu, sobald die Installation abgeschlossen wurde.

### <a name="updating-the-extension"></a>Aktualisieren der Erweiterung

Die TFVC-Erweiterung wird regelmäßig aktualisiert. Wählen Sie für den Zugriff auf Updates im Menü **Visual Studio > Erweiterungen...** und anschließend die Registerkarte **Updates** aus. Wählen Sie in der Liste die Erweiterung aus, und klicken Sie auf die Schaltfläche **Aktualisieren**:

Klicken Sie im nächsten Dialogfeld auf **Installieren**, um das alte Paket zu deinstallieren und das neue Paket zu installieren.

### <a name="using-the-extension"></a>Verwenden der Erweiterung

Wählen Sie nach der Installation der Erweiterung das Menüelement **Versionskontrolle > TFS/Azure DevOps > Öffnen über Remoterepository** aus.

![Menüelement zum Öffnen der Erweiterung](media/tfvc-source-control-explorer-devops.png)

Wählen Sie VSTS oder Team Foundation Server aus, und klicken Sie auf **Weiter**:

![Verbinden mit einem Server](media/tfvc-choose-server-type-devops.png)

#### <a name="azure-repos-authentication"></a>Azure Repos-Authentifizierung

Wenn Sie ein unter Azure Repos gehostetes Projekt auswählen, werden Sie aufgefordert, Ihre Microsoft-Kontoinformationen einzugeben:

![Herstellen einer Verbindung mit Azure Repos](media/tfvc-vsts-login.png)

#### <a name="tfs-authentication"></a>TFS-Authentifizierung

Geben Sie zum Verbinden mit TFS die Serverdetails und Ihre Kontoanmeldeinformationen ein. Geben Sie eine Domäne ein, um die NTLM-Authentifizierung zu verwenden. Zur Verwendung der Standardauthentifizierung geben Sie nichts ein. Wählen Sie **Server hinzufügen** aus:

![Anmelden bei einem TFS-Server](media/tfvc-login.png)

### <a name="selecting-a-project"></a>Auswählen eines Projekts

Nach der erfolgreichen Authentifizierung wird im Dialogfeld **Aus Quellcodeverwaltung öffnen** eine Liste mit Repositorys angezeigt, die mit dem Konto verknüpft sind:

![Dialogfeld „Aus Quellcodeverwaltung öffnen“ mit Projekten](media/tfvc-vsts-projects.png)

Dieses Dialogfeld ist in die folgenden Knoten unterteilt:

- Azure DevOps-Organisation oder -Sammlung: Hier werden alle Organisationen angezeigt, die mit dem Microsoft-Konto verknüpft sind, mit dem Sie sich angemeldet haben.
- Projekte: Jede Organisation oder Sammlung kann mehrere Projekte enthalten. In einem Projekt werden Quellcode, Arbeitselemente und automatisierte Builds gehostet.

Hier können Sie nach dem Namen eines Projekts oder einer Organisation suchen und filtern.

#### <a name="adding-a-new-server"></a>Hinzufügen eines neuen Servers

Klicken Sie zum Hinzufügen eines neuen Servers zur Liste im Dialogfeld **Aus Quellcodeverwaltung öffnen** auf die Schaltfläche **Host hinzufügen**:

![Hervorgehobene Schaltfläche zum Hinzufügen eines neuen Servers zur Liste](media/tfvc-add-new-server.png)

Wählen Sie in der Liste den Anbieter aus, und geben Sie Ihre Anmeldeinformationen ein:

![Dialogfeld mit der Option für den Quellcodeverwaltungsanbieter](media/tfvc-add-new-creds-devops.png)

### <a name="creating-a-new-workspace"></a>Erstellen eines neuen Arbeitsbereichs

Um mit der Arbeit mit einem Projekt beginnen zu können, benötigen Sie einen _Arbeitsbereich_. Wenn Sie noch keinen Arbeitsbereich haben, können Sie über das Kombinationsfeld **Arbeitsbereich** im Dialogfeld **Aus Quellcodeverwaltung öffnen** einen erstellen:

![Kombinationsfeldoption zum Erstellen eines neuen Arbeitsbereichs](media/tfvc-create-new-workspace.png)

Legen Sie für den neuen Arbeitsbereich einen Namen und einen lokalen Pfad fest, und wählen Sie **Arbeitsbereich erstellen** aus:

![Eingeben eines Namens und eines lokalen Pfads für den neuen Arbeitsbereich](media/tfvc-local-workspace.png)

### <a name="using-the-source-code-explorer"></a>Verwenden des Quellcode-Explorers

Nachdem Sie einen Arbeitsbereich erstellt und Ihr Projekt zugeordnet haben, können Sie den _Quellcode-Explorer_ verwenden.

Wählen Sie zum Öffnen des Quellcode-Explorers **Versionskontrolle > TFS/Azure DevOps > Quellcodeverwaltungs-Explorer** aus.

Mit dem Quellcode-Explorer können Sie durch alle zugeordneten Projekte sowie die dazu gehörenden Dateien und Ordner navigieren. Ferner können Sie damit alle grundlegenden Quellcodeverwaltungsaktionen durchführen. Hierzu zählen folgende:

- Abrufen der neuesten Version
- Abrufen einer spezifischen Version
- Ein- und Auschecken von Dateien
- Sperren und Entsperren von Dateien
- Hinzufügen, Löschen und Umbenennen von Dateien
- Anzeigen des Verlaufs
- Änderungen vergleichen.

Viele dieser Aktionen sind über Kontextaktionen für das Projekt verfügbar:

![Kontextmenüaktionen für ein Projekt](media/tfvc-sourcecode-actions.png)

### <a name="managing-workspaces"></a>Verwalten von Arbeitsbereichen

Wenn Sie noch keinen Arbeitsbereich erstellt haben (s. Abschnitt [Erstellen eines Arbeitsbereichs](#creating-a-new-workspace)), ist der Quellcode-Explorer leer:

![Leerer Quellcode-Explorer](media/tfvc-setup-empty-sce.png)

Gehen Sie wie folgt vor, um das Remoteprojekt mit einem lokalen Arbeitsbereich einzurichten:

1. Wählen Sie den **Server** im Kombinationsfeld aus.
1. Beachten Sie, dass „keine Arbeitsbereiche“ vorhanden sind und der lokale Pfad „nicht zugeordnet“ ist. Wählen Sie den Link **Nicht zugeordnet** aus, um das Dialogfeld **Neuen Arbeitsbereich erstellen** anzuzeigen.
1. Geben Sie einen Namen für den Arbeitsbereich an, und klicken Sie dann auf **Add Working Folder** (Arbeitsordner hinzufügen), um das Projekt einem lokalen Ordner auf Ihrem Computer zuzuordnen.

    ![Dialogfeld „Neuen Arbeitsbereich erstellen“ mit Standardoptionen](media/tfvc-workspace1.png)

1. Wählen Sie den Ordner „$“ aus, um alle Projekte auf Ihrem Server demselben Arbeitsbereich zuzuordnen, oder wählen Sie ein einzelnes Projekt aus, und klicken Sie auf **OK**:

    ![Suche nach Ordnerdialogfeld mit allen Projekten](media/tfvc-workspace2.png)

1. Wählen Sie den Speicherort auf Ihrem lokalen Computer aus, dem Sie die Projekte zuordnen möchten, und klicken Sie auf **Ordner auswählen**.
1. Bestätigen Sie die Details des neuen Arbeitsbereichs, indem Sie auf **OK** klicken.

    ![Dialogfeld „Neuen Arbeitsbereich erstellen“ mit hinzugefügtem Arbeitsordner](media/tfvc-workspace3.png)

Nachdem Sie Ihren Arbeitsbereich eingerichtet haben, können Sie ihn ändern oder entfernen, indem Sie im Quellcode-Explorer auf die Schaltfläche **Arbeitsbereiche verwalten** klicken.

![Arbeitsbereiche verwalten](media/tfvc-workspace4.png)

## <a name="troubleshooting-and-known-issues"></a>Problembehandlung und bekannte Probleme

#### <a name="problems-using-basic-authentication"></a>Probleme bei der Standardauthentifizierung

Mithilfe der folgenden Optionen können Sie sich bei einem Server authentifizieren:

- OAuth
- Basic
- Ntlm

Wenn Sie die Standardauthentifizierung verwenden möchten, müssen Sie **Alternative authentication credentials** (Alternative Anmeldeinformationen für die Authentifizierung) in Azure DevOps Services aktivieren, indem Sie folgende Schritte ausführen:

1. Melden Sie sich als Besitzer bei Ihrer Azure DevOps-Organisation an (https:\//dev.azure.com/{organization}/{project}).

2. Klicken Sie in der Symbolleiste Ihrer Organisation auf das Zahnradsymbol und dann auf **Richtlinie**:

    ![Screenshot der Symbolleiste der Azure DevOps-Organisation mit ausgewähltem Zahnradsymbol und der im Dropdownmenü ausgewählten Richtlinie.](media/tfvc-auth2.png)

3. Überprüfen Sie die Verbindungseinstellungen Ihrer Anwendung. Ändern Sie diese Einstellungen gemäß Ihren Sicherheitsrichtlinien:

    ![Screenshot des Richtlinienbildschirms in Azure DevOps Services mit den Einstellungen für Anwendungsverbindungsrichtlinien](media/tfvc-auth.png)

#### <a name="i-do-not-see-anything-in-tfvc"></a>In TFVC wird nichts angezeigt

Wenn Sie Team Foundation-Versionskontrolle (TFVC) auf Ihrem Entwicklungscomputer einrichten möchten, **müssen** Sie wie im Abschnitt [Verwalten von Arbeitsbereichen](#managing-workspaces) beschrieben einen Arbeitsbereich erstellen.

Klicken Sie im Quellcodeverwaltungs-Explorer auf die Schaltfläche **Arbeitsbereiche verwalten**. Führen Sie die Schritte aus, um das Projekt einem Ordner auf dem Entwicklungscomputer zuzuordnen.

#### <a name="i-do-not-see-any--all-of-my-projects"></a>Projekte werden teilweise oder gar nicht angezeigt

Nach der Authentifizierung sollte die Liste der Projekte angezeigt werden. Standardmäßig werden nur TFS-Projekte angezeigt. Aktivieren Sie das Kontrollkästchen „See all projects“ (Alle Projekte anzeigen), um andere Projekttypen anzuzeigen.

Beachten Sie, dass Projekte, die sich auf dem Server befinden, nur angezeigt werden, wenn Sie über die richtigen Berechtigungen verfügen.

##### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Der Fehler „Cannot create the workspace. Please, try again“ (Der Arbeitsbereich kann nicht erstellt werden. Wiederholen Sie den Vorgang.) wird angezeigt

Wenn Sie versuchen, [einen neuen Arbeitsbereich zu erstellen](#creating-a-new-workspace), sollten Sie sicherstellen, dass folgende Bedingungen erfüllt sind:

- Im Name des Arbeitsbereich werden keine ungültigen Zeichen verwendet.
- Der Name muss weniger als 64 Zeichen umfassen.
- Der lokale Pfad darf nicht von anderen Arbeitsbereichen verwendet werden.

### <a name="see-also"></a>Siehe auch

- [Entwickeln und Freigeben von Code in TFVC mit Visual Studio (unter Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)