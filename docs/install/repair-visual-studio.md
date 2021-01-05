---
title: Reparieren Sie Visual Studio.
titleSuffix: ''
description: Hier erfahren Sie, wie Sie eine Installation von Visual Studio 2017 reparieren.
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: f27ccf9440d0f01a5a41d69e753a6d83f81c5263
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668533"
---
# <a name="repair-visual-studio"></a>Reparieren Sie Visual Studio.

Es kann vorkommen, dass Ihre Visual Studio-Installation beschädigt wird oder fehlerhaft ist. Eine Reparatur ist nützlich, um Installationsprobleme bei allen Installationsvorgängen, einschließlich Updates, zu beheben.

## <a name="when-to-use-repair"></a>Anwendungsfälle einer Reparatur
* Wenn Sie Probleme mit der Installationsnutzlast haben. Dies kann vorkommen, wenn das Schreiben der Datei auf den Datenträger nicht erfolgreich ist und nicht durch Löschen der beschädigten Datei behoben werden kann. Bei der Reparatur können benötigte Dateien erneut abgerufen werden. 
* Wenn Sie auf Clientseite Probleme beim Herunterladen haben. Vorausgesetzt, Sie haben alle Verbindungs- oder Proxyprobleme behoben, kann eine Reparatur helfen. 
* Wenn beim Update von Visual Studio Probleme auftreten. Mit der Reparatur werden viele gängige Updateprobleme behoben. 

> [!TIP] 
> Wenn das Installationsproblem durch ein Problem in einem zugrunde liegenden Windows-Dienst, wie Windows Installer, verursacht wird, kann die Reparatur auf dasselbe Problem stoßen. Zu systemischen Problemen können ein defekter Windows Installer oder eine instabile Internetverbindung gehören. Um auf ein systemisches Problem zu prüfen, verwenden Sie den beim Installationsvorgang generierten Fehlerbericht.

> [!NOTE] 
> Bei der Reparatur von Visual Studio werden die Benutzereinstellungen zurückgesetzt und die bereits vorhandenen Assemblys neu installiert. Wenn ein Produktproblem auftritt, erstellen Sie ein [Visual Studio-Feedbackticket](https://aka.ms/feedback/suggest?space=8), da eine Reparatur das Problem möglicherweise nicht behebt.

## <a name="how-to-repair"></a>Vorgehensweise bei der Reparatur
::: moniker range="vs-2017"

1. Suchen Sie den **Visual Studio-Installer** auf Ihrem Computer.

     Auf einem Computer mit Windows 10 Anniversary Update oder höher klicken Sie beispielsweise auf **Start** und scrollen dann zum Buchstaben **V**. Dort wird das Installationsprogramm als **Visual Studio-Installer** angezeigt.

   > [!NOTE]
   > Auf manchen Computern ist der Visual Studio-Installer unter dem Buchstaben **„M“** als **Microsoft Visual Studio-Installer** aufgelistet.
   >
   > Alternativ dazu finden Sie den Visual Studio-Installer in folgendem Speicherort: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Öffnen Sie den Installer, wählen Sie **Mehr** aus, und wählen Sie dann **Reparieren** aus.

    ![Reparieren von Visual Studio über den Visual Studio-Installer](media/repair-visual-studio.png "Reparieren von Visual Studio über den Visual Studio-Installer")

   > [!NOTE]
   > Durch das Reparieren von Visual Studio wird die Umgebung zurückgesetzt. Lokale Anpassungen wie Erweiterungen pro Benutzer, die ohne erweiterte Berechtigungen installiert wurden, Benutzereinstellungen und Profile werden entfernt. Ihre synchronisierten Einstellungen wie Designs, Farben und Tastenzuordnungen werden wiederhergestellt.
   >

   > [!TIP]
   > Die Option **Reparieren** wird nur für installierte Instanzen von Visual Studio angezeigt. Ist die Option **Reparieren** nicht vorhanden, haben Sie möglicherweise **Mehr** für eine Version ausgewählt, die im Visual Studio-Installer als "Verfügbar" und nicht als "Installiert" aufgeführt ist.

::: moniker-end

::: moniker range="vs-2019"

1. Suchen Sie den **Visual Studio-Installer** auf Ihrem Computer.

     Hierzu können Sie im Windows-Startmenü nach „Installer“ suchen.

     ![Visual Studio-Installer](media/vs-2019/visual-studio-installer.png "Suchen nach dem Visual Studio-Installer")

     > [!NOTE]
     > Sie können den Visual Studio-Installer auch an folgendem Speicherort finden:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Möglicherweise müssen Sie den Installer aktualisieren, bevor Sie fortfahren. Wenn dies der Fall ist, befolgen Sie die Anweisungen.

1. Suchen Sie im Installer nach der Edition von Visual Studio, die Sie installiert haben. Als Nächstes wählen Sie **Mehr** aus, und wählen Sie dann **Reparieren** aus.

     ![Reparieren von Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Reparieren von Visual Studio 2019")

   > [!NOTE]
   > Durch das Reparieren von Visual Studio wird die Umgebung zurückgesetzt. Lokale Anpassungen wie Erweiterungen pro Benutzer, die ohne erweiterte Berechtigungen installiert wurden, Benutzereinstellungen und Profile werden entfernt. Ihre synchronisierten Einstellungen wie Designs, Farben und Tastenzuordnungen werden wiederhergestellt.
   >

   > [!TIP]
   > Die Option **Reparieren** wird nur für installierte Instanzen von Visual Studio angezeigt. Ist die Option **Reparieren** nicht vorhanden, haben Sie möglicherweise **Mehr** für eine Version ausgewählt, die im Visual Studio-Installer als "Verfügbar" und nicht als "Installiert" aufgeführt ist.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Visual Studio aktualisieren](update-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)
* [Problembehandlung bei der Visual Studio-Installation und bei Upgradefehlern](troubleshooting-installation-issues.md)
