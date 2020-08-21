---
title: Einrichten eines Git-Repositorys
description: Verwenden von Git und Subversion in Visual Studio für Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/15/2018
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.topic: how-to
ms.openlocfilehash: c226e1a8160d0eb1321d244b26177119ec3a5846
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238555"
---
# <a name="set-up-a-git-repository"></a>Einrichten eines Git-Repositorys

Bei Git handelt es sich um ein verteiltes Versionskontrollsystem, mit dem die Mitglieder eines Teams gleichzeitig an den gleichen Dokumenten arbeiten können. Dies bedeutet, dass es einen einzelnen Server mit allen Dateien gibt. Wenn aber ein Repository aus dieser zentralen Quelle ausgecheckt wird, wird das gesamte Repository auf Ihrem Computer lokal geklont.

Es gibt viele Remotehosts, die Ihnen ermöglichen, mit Git für die Versionskontrolle zu arbeiten, der am häufigsten verwendete Host ist jedoch GitHub. Im folgenden Beispiel wird ein GitHub-Host verwendet, sie können allerdings einen beliebigen Git-Host für die Versionskontrolle in Visual Studio für Mac verwenden.

Wenn Sie GitHub verwenden möchten, stellen Sie sicher, dass Sie ein Konto erstellt und konfiguriert haben, bevor Sie die Schritte in diesem Artikel ausführen.

## <a name="creating-a-remote-repo-on-github"></a>Erstellen eines Remoterepository auf GitHub

Im folgenden Beispiel wird ein GitHub-Host verwendet, sie können allerdings einen beliebigen Git-Host für die Versionskontrolle in Visual Studio für Mac verwenden.

Führen sie die folgenden Schritte aus, um ein Git-Repository einzurichten:

1. Erstellen Sie ein neues Git-Repository auf github.com:

    ![Erstellen eines neuen Git-Repositorys](media/version-control-git1-sml.png)

2. Legen Sie den Namen des Repository, die Beschreibung und den Datenschutz fest. Initialisieren Sie das Repository **nicht**. Legen Sie „.gitignore“ und „Lizenz“ auf „Keine“ fest:

    ![Festlegen von Details des Git-Repositorys](media/version-control-git2.png)

3. Auf der nächsten Seite haben Sie die Option, entweder die HTTPS- oder die SSH-Adresse für das Repository, das Sie erstellt haben, anzuzeigen und zu kopieren:

    ![Adresse anzeigen und kopieren](media/version-control-git3.png)

   Sie benötigen die HTTPS-Adresse, um Visual Studio für Mac auf dieses Repository zu verweisen.

## <a name="publishing-an-existing-project"></a>Veröffentlichen eines vorhandenen Projekts

Gehen Sie folgendermaßen vor, um ein vorhandenes Projekt, das sich _noch nicht_ in der Versionskontrolle befindet, in Git einzurichten:

1. Wählen Sie aus dem Projektmappenpad in Visual Studio für Mac den Namen der Projektmappe aus.

2. Klicken Sie in der Menüleiste auf **Versionskontrolle > Publish in Version Control** (In Versionskontrolle veröffentlichen), damit das Dialogfeld **Repository auswählen** angezeigt wird.

    ![Beginnen des Auscheckens in Visual Studio für Mac](media/version-control-git4-sml.png)

    Falls dieses Menüelement im Menü abgeblendet ist, stellen Sie sicher, dass Sie den Namen der Projektmappe ausgewählt haben.

3. Wählen Sie die Registerkarte **Registered Repositories** (Registrierte Repositorys), und klicken Sie auf die Schaltfläche **Add** (Hinzufügen):

    ![Die Registerkarte „Registrierte Repositorys“ des Dialogfelds „Repository auswählen“ verfügt über Schaltflächen zum Hinzufügen, Entfernen und Bearbeiten sowie über Felder für Modulname und Nachricht.](media/version-control-git5.png)

4. Geben Sie den Namen des Repositorys an, den Sie lokal angezeigt haben möchten, und kopieren Sie diesen in die URL aus Schritt 3. Das Dialogfeld „Repositorykonfiguration“ sollte nun der folgenden Abbildung ähneln. Klicken Sie auf „OK“:

    ![Dialogfeld „Git-Details eingeben“](media/version-control-git6.png)

    Auch die Verwendung von SSH ist möglich, um eine Verbindung zu Git herzustellen.

5. Wählen Sie für einen Versuch, die App auf Git zu veröffentlichen, das Repository aus, und vergewissern Sie sich, dass die Textfelder **Modulname** und **Meldung** ausgefüllt sind:

    ![Versuch, ein Projekt auf Git zu veröffentlichen](media/version-control-git7.png)

6. Klicken Sie auf **OK** und dann auf **Veröffentlichen** im Warndialogfeld.

7. Geben Sie im Fenster **Git-Anmeldeinformationen** Ihren Benutzernamen und das Kennwort für GitHub ein. 

> [!NOTE]
> Wenn für Ihr Konto die zweistufige Authentifizierung aktiviert ist, müssen Sie ein Zugriffstoken erstellen, das anstelle eines Kennworts verwendet wird. Wenn Sie kein Zugriffstoken erstellt haben, führen Sie die Schritte in der Git-[Zugriffstoken](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)-Dokumentation aus.

8. Geben Sie den Benutzernamen und den persönlichen Zugriffstoken ein, und klicken Sie auf **OK**:

    ![Eingeben des Benutzernamens und Kennworts für Git](media/version-control-git9-sml.png)

9. Nach ein paar Sekunden sollte die Projektmappe mit ihrem anfänglichen Commit veröffentlicht sein. Bestätigen Sie ihre Veröffentlichung, indem Sie nach dem Menüelement „Versionskontrolle“ suchen, das nun mit vielen Optionen aufgefüllt sein sollte:

    ![Versionskontrolle](media/version-control-git10.png)

10. Wenn Sie zusätzliche Änderungen vornehmen, klicken Sie auf **Änderungen mit Push übertragen**, um die Änderungen per Push an das **Remoterepository** zu übertragen. Dadurch wird es allen entsprechenden Benutzern ermöglicht, diese auf github.com anzusehen:

    ![Übertragen von Änderungen mit einem Push an ein Remoterepository](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Veröffentlichen eines neuen Projekts

Das Dialogfeld „Neues Projekt“ kann zum Erstellen eines neuen Projekts mit einem lokalen Git-Repository verwendet werden. Aktivieren Sie wie im folgenden Screenshot zu sehen das Kontrollkästchen **Use git for version control** (Git zur Versionskontrolle verwenden), damit Sie dieses Dialogfeld verwenden können. Dadurch wird Ihr Repository initialisiert, außerdem wird eine optionale GITIGNORE-Datei hinzugefügt:

![Erstellen eines neuen Projekts mit Git-Unterstützung](media/version-control-git-publish-new1.png)

Führen Sie die folgenden Schritte aus, um Ihr neues lokales Repository auf ein neues GitHub-Repository zu pushen:

> [!NOTE]
> Wenn Sie noch kein GitHub-Repository erstellt haben, lesen Sie sich den Abschnitt [Erstellen eines Remoterepository auf GitHub](#creating-a-remote-repo-on-github) durch.

1. Erstellen Sie Ihren ersten Commit, indem Sie in der Menüleiste zu **Versionskontrolle > Review Solution and Commit** (Projektmappe überprüfen und committen) navigieren.

2. Klicken Sie auf der Registerkarte „Status“ oben links auf **Committen**.

3. Schreiben Sie eine Commitnachricht wie „First Commit“ (Erster Commit), und klicken Sie anschließend auf **Committen**:

    ![Committen von ersten Änderungen am Git-Repository](media/version-control-git-publish-new2.png)

4. Navigieren Sie als Nächstes in der Menüleiste zu **Versionskontrolle > Branches und Git-Remotespeicherorte verwalten**.

5. Gehen Sie zur Registerkarte **Remotequellen**, und klicken Sie auf **Hinzufügen**.

6. Fügen Sie im Fenster **Remotequelle** die Details zu Ihrem zuvor erstellten GitHub-Repository hinzu, und klicken Sie auf **OK**.

    ![Konfigurieren von Remotequellen für das Git-Repository](media/version-control-git-publish-new3.png)

7. Schließen Sie das Fenster **Git-Repositorykonfiguration**, und navigieren Sie anschließend in der Menüleiste zu **Versionskontrolle > Änderungen mit Push übertragen**.

8. Klicken Sie im Fenster **Mit Push an Repository übertragen** auf die Schaltfläche **Änderungen mit Push übertragen**.

    ![Änderungen auf das Remoterepository pushen](media/version-control-git-publish-new4.png)

9. Geben Sie Ihren Benutzernamen und Ihre Kennwort für GitHub ein, wenn Sie dazu aufgefordert werden.

> [!NOTE]
> Wenn für Ihr Konto die zweistufige Authentifizierung aktiviert ist, müssen Sie ein Zugriffstoken erstellen, das anstelle eines Kennworts verwendet wird. Wenn Sie kein Zugriffstoken erstellt haben, führen Sie die Schritte in der Git-[Zugriffstoken](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)-Dokumentation aus.

Dann pusht Visual Studio für Mac die Änderungen auf das GitHub-Remoterepository:

![Bestätigung eines erfolgreichen Pushvorgangs](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Auschecken eines vorhandenen Repositorys

Es ist wahrscheinlich, dass Sie mit einem GitHub-Repository arbeiten müssen, dass nur auf dem Remotecomputer und nicht auf dem lokalen Computer vorhanden ist. Mit Visual Studio für Mac können Sie dieses Repository schnell auschecken. Führen Sie die unten stehenden Schritte durch, um das Repository auf Ihrem Computer zu klonen:

1. Klicken Sie in der Menüleiste auf **Versionskontrolle > Check-Out**:

2. Die Registerkarte **Connect to Repository** (Mit Repository verbinden) wird geöffnet:

    ![Registerkarte „Mit Repository verbinden“ mit ausgefüllten Angaben](media/version-control-git13.png)

3. Klicken Sie auf der GitHub-Seite des Remoterepositorys auf **Clone or Download** (Klonen oder Herunterladen), und kopieren die dort angegebene URL:

    ![angegebene GitHub-URL](media/version-control-git14.png)

4. Ersetzen Sie den Text im Eingabefeld **URL** auf der Registerkarte **Mit Repository verbinden**. Dadurch wird ein Großteil der anderen Felder auf dieser Registerkarte wie auf dem Bild in Schritt 2 ausgefüllt.

5. Geben Sie das Verzeichnis ein, in das das Repository geklont werden soll, und klicken Sie auf **Check-Out**.

> [!NOTE]
> Möglicherweise treten Probleme auf, wenn das Repository größer als 4 GB ist.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Probleme beim Initialisieren Ihres Projekts mit einem leeren Remoterepository haben, können Sie die folgenden Schritte ausführen:

1. Navigieren Sie zu Ihrem Projektmappenordner.
1. Drücken Sie **CMD+UMSCHALT+.** , um ausgeblendete Dateien und Ordner anzuzeigen.
1. Wenn ein **.git**-Ordner vorhanden ist, löschen Sie diesen.
1. Wenn eine **GITIGNORE**-Datei vorhanden ist, löschen Sie diese.
1. Drücken Sie **CMD+UMSCHALT+.** , um die Dateien und Ordner auszublenden.
1. Öffnen Sie Ihre Projektmappe in Visual Studio für Mac.
1. Klicken Sie auf den Knoten „Projektmappe“ im Projektmappenpad.
1. Navigieren Sie zum Menü „Versionskontrolle“, und klicken Sie auf **Publish in Version Control** (In Versionskontrolle veröffentlichen).
1. Führen Sie die Schritte des obenstehenden Tutorials beginnend bei Schritt 6 aus.

## <a name="see-also"></a>Siehe auch

- [Versionskontrolle in Visual Studio (unter Windows)](/visualstudio/version-control/)
