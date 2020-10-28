---
title: Aktualisieren von Visual Studio 2017
titleSuffix: ''
description: Erfahren Sie, wie Sie Visual Studio auf das neueste Release aktualisieren.
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01bc8fe18ff32d5da3f56eb39465b3fc696239b4
ms.sourcegitcommit: 172aaf05596a9d8ded298b7b104569c1cce6160e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92007174"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Aktualisieren von Visual Studio auf die neueste Version

::: moniker range="vs-2017"

Sie sollten ein Update auf das [aktuelle Release](/visualstudio/releasenotes/vs2017-relnotes/) von Visual Studio 2017 ausführen, damit Sie immer die neuesten Features, Fehlerbehebungen und Verbesserungen erhalten.

Und wenn Sie unsere neueste Version ausprobieren möchten, können Sie stattdessen [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) herunterladen und installieren.

> [!IMPORTANT]
> Zum Installieren, Aktualisieren und Anpassen von Visual Studio müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt. Weitere Informationen finden Sie unter [Benutzerberechtigungen und Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Aktualisieren von Visual Studio für Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Aktualisieren auf Visual Studio 2017 Version 15.6 oder höher

Wir haben die Durchführung von Installation und Update optimiert, um Ihnen die direkte Verwendung aus IDE heraus zu erleichtern. Hier wird das Aktualisieren von Version 15.6 und später auf neuere Versionen von Visual Studio erklärt.

### <a name="using-the-notifications-hub"></a>Verwenden des Benachrichtigungshubs

Wenn ein Update vorhanden ist, wird ein entsprechendes Benachrichtigungsflag in Visual Studio angezeigt.

1. Speichern Sie Ihre Arbeit.

1. Klicken Sie auf das Benachrichtigungsflag, um den **Benachrichtigungshub** zu öffnen, und wählen Sie dann das Update aus, das Sie installieren möchten.

   ![Aktualisieren von Visual Studio 2017 mithilfe des Notifications Hubs](media/vs-install-notifications-hub-15dot6.png "Notifications Hub in Visual Studio 2017")

      > [!TIP]
      > Da ein Update für eine Edition von Visual Studio 2017 kumulativ ist, wählen Sie immer das mit der aktuellsten Versionsnummer zur Installation aus.

1. Wenn das **Update** -Dialogfeld geöffnet wird, wählen Sie **Jetzt aktualisieren** .

    ![Aktualisieren von Visual Studio 2017 mithilfe des Dialogfelds „Aktualisieren“ über den Notifications Hub](media/vs-update-now-from-notifications-hub.png "Dialogfeld „Aktualisieren“ des Notifications Hubs in Visual Studio")

     Wenn ein Benutzerzugriffssteuerungs-Dialogfeld geöffnet wird, wählen Sie **Ja** . Als Nächstes könnte ein Dialogfeld „Bitte warten“ einen Moment lang geöffnet werden, und dann wird der Visual Studio-Installer geöffnet, um die Aktualisierung zu starten.

     ![Die neue Benutzeroberfläche von Visual Studio-Installer in Version 15.6](media/visual-studio-15dot6-installer.png "Neue Benutzeroberfläche von Visual Studio-Installer in Version 15.6")

     Das Update wird fortgesetzt. Wenn es fertig gestellt ist, wird Visual Studio neu startet.

     > [!NOTE]
     > Wenn Sie Visual Studio im Administratormodus ausführen, müssen Sie Visual Studio nach dem Update manuell neu starten.

### <a name="using-the-ide"></a>Verwenden von IDE

Sie können nach einem Update suchen und das Update dann von der Menüleiste in Visual Studio aus installieren.

1. Speichern Sie Ihre Arbeit.

1. Wählen Sie **Hilfe** > **Nach Updates suche** aus.

     ![Das neue Hilfemenü in Visual Studio Version 15.6](media/vs-help-menu-check-for-updates.png "Neues Hilfemenü in Visual Studio Version 15.6")

1. Wenn das **Update** -Dialogfeld geöffnet wird, wählen Sie **Jetzt aktualisieren** .

   Das Update wird wie im vorherigen Abschnitt beschrieben durchgeführt, und nachdem das Update erfolgreich abgeschlossen wurde, wird Visual Studio neu gestartet.

   > [!NOTE]
   > Wenn Sie Visual Studio im Administratormodus ausführen, müssen Sie Visual Studio nach dem Update manuell neu starten.

### <a name="using-the-visual-studio-installer"></a>Verwenden des Visual Studio-Installers

Wie in früheren Versionen von Visual Studio können Sie mit dem Visual Studio-Installer ein Update installieren.

1. Speichern Sie Ihre Arbeit.

1. Öffnen Sie den Installer. Der Visual Studio-Installer könnte möglicherweise eine Aktualisierung erfordern, bevor Sie fortfahren.

   > [!NOTE]
   > Auf einem Computer unter Windows 10, finden Sie den Installer unter dem Buchstaben **V** als **Visual Studio-Installer** oder unter dem Buchstaben **M** als **Microsoft Visual Studio-Installer** .

1. Suchen Sie auf der **Produkt** -Seite im Installer nach der zuvor installierten Edition von Visual Studio.

1. Wenn ein Update verfügbar ist, sehen Sie eine Schaltfläche **Update** . (Es kann einige Sekunden dauern, bis der Installer bestimmen kann, ob ein Update verfügbar ist.)

   Klicken Sie auf die Schaltfläche **Aktualisieren** , um die Updates zu installieren.

     ![Aktualisieren von Visual Studio 2017 mithilfe des Visual Studio-Installers](media/update-visual-studio.png "Aktualisieren von Visual Studio 2017 mithilfe des Visual Studio-Installers")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aktualisieren von Visual Studio 2017 Version 15.5 oder früher

Wenn Sie eine frühere Version verwenden, erfahren Sie hier, wie Sie ein Update auf Visual Studio 2017 Version 15.0 bis Version 15.5 anwenden.

### <a name="update-by-using-the-notifications-hub"></a>Aktualisieren mithilfe des Benachrichtigungshubs

1. Wenn Updates vorhanden sind, wird ein entsprechendes Benachrichtigungsflag in Visual Studio angezeigt.

   ![Benachrichtigungsflag zum Aktualisieren von Visual Studio 2017](media/notification-flag.png "Benachrichtigungsflag für Updates in Visual Studio")

   Klicken Sie auf das Benachrichtigungsflag, um den Hub **Benachrichtigungen** zu öffnen.

   ![Visual Studio 2017-Update im Notification Hub](media/notifications-hub.png "Visual Studio 2017-Update im Notification Hub")

      > [!TIP]
      > Da ein Update für eine Edition von Visual Studio 2017 kumulativ ist, wählen Sie immer das mit der aktuellsten Versionsnummer zur Installation aus.

1. Klicken Sie auf **"Visual Studio Update" is available** („Visual Studio-Update“ steht zur Verfügung), womit das Dialogfeld **Erweiterungen und Updates** geöffnet wird.

   ![Klicken auf „Visual Studio-Update“](media/notifications-hub-select.png "Klicken auf „Visual Studio-Update“")

1. Klicken Sie im Dialogfeld **Erweiterungen und Updates** auf die Schaltfläche **Update** .

   ![Klicken auf „Update“ im Dialogfeld „Erweiterungen und Updates“](media/notifications-extensions-and-updates.png "Dialogfeld „Erweiterungen und Updates“ in Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Weitere Informationen zu Visual Studio-Benachrichtigungen

Visual Studio benachrichtigt Sie, wenn ein Update für Visual Studio selbst oder für eine der Komponenten verfügbar ist und wenn bestimmte Ereignisse in der Visual Studio-Umgebung auftreten.

* Ist das Benachrichtigungsflag gelb, steht ein Visual Studio-Produktupdate für die Installation zur Verfügung.
* Wenn das Benachrichtigungsflag rot ist, gibt es ein Problem mit Ihrer Lizenz.
* Falls das Benachrichtigungsflag schwarz ist, liegen optionale oder informative Nachrichten für Sie bereit.

Klicken Sie auf das Benachrichtigungsflag, um den Hub **Benachrichtigungen** zu öffnen, und klicken Sie dann auf die Benachrichtigungen, die Sie bearbeiten möchten. Alternativ können Sie Benachrichtigungen auch ignorieren oder verwerfen.

 ![Anzeigen einer optionalen oder Informationsmeldung im Notifications Hub](media/notification-flag-optional.png "Benachrichtigungsflag für optionale oder Informationsmeldung in Visual Studio")

Wenn Sie eine Benachrichtigung ignorieren, wird diese von Visual Studio nicht mehr angezeigt. Wenn Sie die Liste der ignorierten Benachrichtigungen zurücksetzen möchten, wählen Sie im Benachrichtigungshub die Schaltfläche **Einstellungen** .

   ![Auswählen der Schaltfläche „Einstellungen“ im Notifications Hub zum Anzeigen von Benachrichtigungsoptionen](media/vs-notifications-hub-settings-button.png "Auswählen der Schaltfläche „Einstellungen“ im Notifications Hub zum Anzeigen von Benachrichtigungsoptionen")

### <a name="update-by-using-the-visual-studio-installer"></a>Aktualisieren mithilfe des Installers für Visual Studio

1. Öffnen Sie den Installer. Möglicherweise müssen Sie den Installer aktualisieren, bevor Sie fortfahren. Ist dies der Fall, werden Sie dazu aufgefordert.

   > [!NOTE]
   > Auf einem Computer unter Windows 10, finden Sie den Installer unter dem Buchstaben **V** als **Visual Studio-Installer** oder unter dem Buchstaben **M** als **Microsoft Visual Studio-Installer** .

1. Suchen Sie auf der **Produkt** -Seite im Installer nach der zuvor installierten Edition von Visual Studio.

1. Wenn ein Update verfügbar ist, sehen Sie eine Schaltfläche **Update** . (Es kann einige Sekunden dauern, bis der Installer bestimmen kann, ob ein Update verfügbar ist.)

   Klicken Sie auf die Schaltfläche **Aktualisieren** , um die Updates zu installieren.

     ![Aktualisieren von Visual Studio 2017 mithilfe des Visual Studio-Installers](media/update-visual-studio.png "Aktualisieren von Visual Studio mithilfe des Visual Studio-Installers")

::: moniker-end

::: moniker range="vs-2019"

Sie sollten ein Update auf das [aktuelle Release](/visualstudio/releases/2019/release-notes/) von Visual Studio 2019 ausführen, damit Sie immer die neuesten Features, Fehlerbehebungen und Verbesserungen erhalten.

Wenn Sie Visual Studio 2019 noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen. Wenn Sie aktuell eine andere Version von Visual Studio verwenden, können Sie entweder die Möglichkeit zur [Parallelen Installation mehrerer Visual Studio-Versionen](../install/install-visual-studio-versions-side-by-side.md) oder zum [Deinstallieren von Visual Studio](../install/uninstall-visual-studio.md) verwenden.

> [!IMPORTANT]
> Zum Installieren, Aktualisieren und Anpassen von Visual Studio müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt. Weitere Informationen finden Sie unter [Benutzerberechtigungen und Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Aktualisieren von Visual Studio für Mac](/visualstudio/mac/update).

So aktualisieren Sie Visual&nbsp;Studio&nbsp;2019.

## <a name="use-the-visual-studio-installer"></a>Verwenden des Visual Studio-Installers

1. Suchen Sie den **Visual Studio-Installer** auf Ihrem Computer.

   Hierzu können Sie im Windows-Startmenü nach „Installer“ suchen.

   ![Visual Studio-Installer](media/vs-2019/visual-studio-installer.png "Suchen nach dem Visual Studio-Installer")

   Möglicherweise müssen Sie den Installer aktualisieren, bevor Sie fortfahren. Wenn dies der Fall ist, befolgen Sie die Anweisungen.

1. Suchen Sie im Installer nach der Edition von Visual Studio, die Sie installiert haben.

   Wenn Sie zum Beispiel zuvor Visual&nbsp;Studio Community&nbsp;2019 installiert haben und es ein Update dafür gibt, wird im Installer die Meldung **Update verfügbar** angezeigt.

     ![Auswählen der zu aktualisierenden Edition von Visual Studio 2019](media/vs-2019/vs-installer-update-visual-studio-community.png "Auswählen der zu aktualisierenden Edition von Visual Studio 2019")

1. Klicken Sie auf die Schaltfläche **Update** , um die Updates zu installieren.

    ![Auswählen der Schaltfläche „Aktualisieren“ zum Installieren der Updates](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Auswählen der Schaltfläche „Aktualisieren“ zum Installieren der Updates")

1. Nach Abschluss des Updates werden Sie möglicherweise aufgefordert, den Computer neu zu starten. Wenn dies der Fall ist, starten Sie den Computer neu, und starten Sie anschließend Visual Studio wie gewohnt.

   Wenn Sie nicht aufgefordert werden, den Computer neu zu starten, wählen Sie **Starten** aus, um Visual Studio über das Installationsprogramm zu starten.

    ![Auswählen der Schaltfläche „Starten“ zum Starten von Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Auswählen der Schaltfläche „Starten“ zum Starten von Visual Studio")

## <a name="use-the-ide"></a>Verwenden der IDE

Sie können nach einem Update suchen und es dann von der Menüleiste oder dem Suchfeld in Visual Studio 2019 aus installieren.

### <a name="open-visual-studio"></a>Öffnen Sie Visual Studio.

1. Wählen Sie im **Windows-Startmenü****Visual Studio 2019** aus.

    ![Öffnen von Visual Studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Öffnen von Visual Studio 2019 über Windows")

1. Wählen Sie unter **Erste Schritte** eine beliebige Option aus, um die IDE zu öffnen.

    ![Öffnen des Visual Studio-Installers](media/vs2019-choose-option-from-get-started.png "Öffnen des Visual Studio-Installers")

    Visual Studio wird geöffnet. In der IDE wird eine Meldung **Visual Studio 2019 Update** angezeigt.

    ![Meldung „Visual Studio 2019 Update“ in der IDE](media/vs-2019/update-visual-studio-ide-message.png "Meldung „Visual Studio 2019 Update“ in der IDE")

1. Wählen Sie in der Meldung **Visual Studio 2019 Update****Details anzeigen** aus.

   ![Auswählen der Schaltfläche „Details anzeigen“ in der Meldung „Visual Studio 2019 IDE-Update“](media/vs-2019/update-visual-studio-ide-view-details.png "Auswählen der Schaltfläche „Details anzeigen“ in der Meldung „Visual Studio 2019 Update“")

1. Wählen Sie im Dialogfeld **Das Update wurde heruntergeladen und ist installationsbereit.****Update** aus.

     ![Auswählen der Schaltfläche „Update“ im Dialogfeld „Das Update wurde heruntergeladen und ist installationsbereit“](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "Auswählen der Schaltfläche „Update“ im Dialogfeld „Das Update wurde heruntergeladen und ist installationsbereit“")

   Visual Studio wird aktualisiert, geschlossen und anschließend wieder geöffnet.

### <a name="in-visual-studio"></a>In Visual Studio

1. Wählen Sie in der Menüleiste **Hilfe** und dann **Nach Updates suchen** aus.

     ![Auswählen von „Nach Updates suchen“ aus dem Hilfemenü](media/vs-2019/vs-ide-check-updates-help-menu.png "Auswählen von „Nach Updates suchen“ aus dem Hilfemenü")

    > [!NOTE]
    > Sie können auch das Suchfeld in der IDE verwenden, um nach Updates zu suchen. Drücken Sie **STRG**+**Q** , geben Sie „Nach Updates suchen“ ein, und wählen Sie dann das passende Suchergebnis aus.

1. Wählen Sie im Dialogfeld **Update verfügbar** die Option **Aktualisieren** aus.

     ![Klicken auf die Schaltfläche „Update“ im Dialogfeld „Update verfügbar“](media/vs-2019/update-visual-studio-community-from-ide.png "Klicken auf die Schaltfläche „Update“ im Dialogfeld „Update verfügbar“")

   Visual Studio wird aktualisiert, geschlossen und anschließend wieder geöffnet.

## <a name="use-the-notifications-hub"></a>Verwenden des Benachrichtigungshubs

1. Speichern Sie Ihre Arbeit in Visual Studio.

1. Wählen Sie das Benachrichtigungssymbol in der unteren rechten Ecke der Visual Studio-IDE aus, um den **Benachrichtigungshub** zu öffnen.

   ![Benachrichtigungssymbol in der Visual Studio-IDE](media/vs-2019/notification-bar.png "Benachrichtigungssymbol in der Visual Studio-IDE")

1. Wählen Sie im **Benachrichtigungshub** das Update, das Sie installieren möchten, und dann **Details anzeigen** aus.

     ![Notifications Hub in Visual Studio 2019](media/vs-2019/notification-hub-update.png "Notifications Hub in Visual Studio 2019")

      > [!TIP]
      > Da ein Update für eine Edition von Visual Studio 2019 kumulativ ist, wählen Sie immer das mit der aktuellsten Versionsnummer zur Installation aus.

1. Wählen Sie im Dialogfeld **Update verfügbar** die Option **Aktualisieren** aus.

   Visual Studio wird aktualisiert, geschlossen und anschließend wieder geöffnet.

## <a name="customize-update-settings"></a>Anpassen von Aktualisierungseinstellungen

Sie können die Aktualisierungseinstellungen in Visual Studio auf verschiedene Weise anpassen, z.B. durch eine Änderung des Installationsmodus und durch die Auswahl automatischer Downloads.

Es stehen zwei Installationsmodi zur Auswahl:

* **Beim Herunterladen installieren**
* **Alle herunterladen und dann installieren**

Sie können außerdem die Option **Updates automatisch herunterladen** auswählen, um das Herunterladen von Updates zuzulassen, wenn sich Ihr Computer im Leerlauf befindet.

Gehen Sie dabei folgendermaßen vor:

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen** .

2. Erweitern Sie **Umgebung** , und klicken Sie dann auf **Produktupdates** .

    ![Aktualisierungseinstellungen in Visual Studio](media/vs-2019/update-settings-options.png)

3. Wählen Sie den Installationsmodus und die Optionen für den automatischen Download aus, die Sie für Visual Studio-Updates verwenden möchten.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Parallele Installation mehrerer Visual Studio-Versionen](install-visual-studio-versions-side-by-side.md)
* [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung](update-servicing-baseline.md)
* [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
* [Ändern von Visual Studio](modify-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)
