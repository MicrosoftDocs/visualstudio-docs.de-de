---
title: Ändern von Visual Studio 2017
titleSuffix: ''
description: Erfahren Sie Schritt für Schritt, wie Sie Visual Studio ändern.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: contperfq2
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dad71e4f52350357106ee9a9ef9ce90d18204bfb
ms.sourcegitcommit: 4eb8fe6eb7f1dc639f1d213db05a7a3007e8087e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2020
ms.locfileid: "92157374"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Ändern von Visual Studio durch Hinzufügen oder Entfernen von Arbeitsauslastungen und Komponenten

::: moniker range="vs-2019"

Es ist einfach, Visual Studio so anzupassen, dass nur das enthalten ist, was Sie möchten, wenn Sie es möchten. Hierzu öffnen Sie den Visual Studio-Installer, um Workloads und Komponenten hinzuzufügen oder zu entfernen.

::: moniker-end

::: moniker range="vs-2017"

Wir haben nicht nur das Personalisieren von Visual Studio erleichtert, um den Dienst entsprechend Ihren Aufgaben einzurichten, sondern auch die generelle Anpassung von Visual Studio. Hierzu öffnen Sie den neuen Visual Studio-Installer und nehmen die gewünschten Änderungen vor.

::: moniker-end

Gehen Sie folgendermaßen vor:

>[!IMPORTANT]
>Zum Installieren, Aktualisieren und Anpassen von Visual Studio müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt. Weitere Informationen finden Sie unter [Benutzerberechtigungen und Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!NOTE]
> Bei den folgenden Verfahren wird davon ausgegangen, dass Sie über eine Internetverbindung verfügen.
>
> Weitere Informationen dazu, wie Sie eine zuvor erstellte [Offlineinstallation](create-an-offline-installation-of-visual-studio.md) von Visual Studio ändern, finden Sie auf den Seiten [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md) und [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md).

## <a name="open-the-visual-studio-installer"></a>Öffnen des Visual Studio-Installers

::: moniker range="vs-2017"

1. Suchen Sie den Visual Studio-Installer auf Ihrem Computer.

     Auf einem Computer mit Windows 10 wählen Sie beispielsweise **Start** und blättern dann zum Buchstaben **V** , wo das Installationsprogramm als **Visual Studio-Installer** angezeigt wird.

     ![Visual Studio-Installer](media/locate-the-visual-studio-installer.png "Suchen des Microsoft Visual Studio-Installers")

     >[!TIP]
     >Auf manchen Computern ist der Visual Studio-Installer unter dem Buchstaben **„M“** als **Microsoft Visual Studio-Installer** aufgelistet.<br/><br/> Alternativ dazu finden Sie den Visual Studio-Installer in folgendem Speicherort: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Öffnen Sie das Installationsprogramm und wählen Sie dann **Ändern** aus.

     ![Starten oder Ändern von Visual Studio](media/modify-visual-studio.png "Ändern von Visual Studio 2017")

     > [!IMPORTANT]
     > Bei einem ausstehenden Update befindet sich die Schaltfläche „Ändern“ an einer anderen Stelle. Auf diese Weise können Sie bei Bedarf Visual Studio ohne Aktualisierung ändern. Klicken Sie auf **Mehr** , und wählen Sie dann **Ändern** .
     >
     > ![Aktualisieren oder Ändern von Visual Studio](media/modify-or-update-visual-studio.png "Aktualisieren oder Ändern von Visual Studio 2017")

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

1. Suchen Sie im Installer nach der Edition von Visual Studio, die Sie installiert haben, und klicken Sie dann auf **Ändern** .

     ![Auswählen der Visual Studio-Edition und anschließende Bearbeitung](media/vs-2019/vs-installer-modify.png "Auswählen der Visual Studio 2019-Edition und anschließende Bearbeitung")

     > [!IMPORTANT]
     > Bei einem ausstehenden Update befindet sich die Schaltfläche „Ändern“ an einer anderen Stelle. Auf diese Weise können Sie bei Bedarf Visual Studio ohne Aktualisierung ändern. Wählen Sie **Mehr** und dann **Ändern** aus.
     >
     > ![Aktualisieren oder Ändern von Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aktualisieren oder Ändern von Visual Studio 2019")

::: moniker-end

## <a name="modify-workloads"></a>Ändern von Arbeitsauslastungen

::: moniker range="vs-2017"

 [Workloads](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) enthalten die Funktionen, die Sie für die verwendete Programmiersprache oder Plattform benötigen. Verwenden Sie Arbeitsauslastungen, um Visual Studio so zu ändern, dass die Arbeit, die Sie ausführen möchten zum gewünschten Zeitpunkt unterstützt werden.

1. Wählen Sie im Visual Studio-Installer die Registerkarte **Workloads** und dann die gewünschten Workloads aus oder heben Sie die Auswahl bestimmter Workloads auf.

    ![Visual Studio 2017-Setupdialogfeld](media/modify-workloads.png "Auswählen einer Arbeitsauslastung in Visual Studio 2019")

1. Wählen Sie aus, ob Sie die Standardoption **Beim Herunterladen installieren** oder die Option **Alle herunterladen und dann installieren** verwenden möchten.

    ![Visual Studio 2017-Setupoptionen](media/vs-2019/vs-installer-choose-install-or-download.png "Auswählen von „Beim Herunterladen installieren“ oder „Alle herunterladen und dann installieren“")

    Die Option „Alle herunterladen und dann installieren“ ist praktisch, wenn Sie zuerst alle Dateien herunterladen und die Installation später durchführen möchten.

1. Klicken Sie auf **Ändern** .

1. Klicken Sie im Visual Studio-Installer auf **Starten** , nachdem die neuen Workloads installiert wurden, um Visual Studio zu öffnen.

::: moniker-end

::: moniker range="vs-2019"

 Arbeitsauslastungen enthalten die Features, die Sie für die verwendete Programmiersprache oder Plattform benötigen. Verwenden Sie Arbeitsauslastungen, um Visual Studio so zu ändern, dass die Arbeit, die Sie ausführen möchten zum gewünschten Zeitpunkt unterstützt werden.

 > [!TIP]
>Weitere Informationen zu den Tools und Komponentenpaketen, die Sie für die Entwicklung benötigen, finden Sie unter [Visual Studio-Workloads](https://visualstudio.microsoft.com/vs/#workloads).

1. Wählen Sie im Visual Studio-Installer die Registerkarte **Workloads** und dann die gewünschten Workloads aus oder heben Sie die Auswahl bestimmter Workloads auf.

    ![Visual Studio 2019-Setupdialogfeld](media/vs-2019/vs-installer-modify-workloads.png "Auswählen einer Arbeitsauslastung in Visual Studio 2019")

1. Wählen Sie aus, ob Sie die Standardoption **Beim Herunterladen installieren** oder die Option **Alle herunterladen und dann installieren** verwenden möchten.

    ![Visual Studio 2019-Setupoptionen](media/vs-2019/vs-installer-choose-install-or-download.png "Auswählen von „Beim Herunterladen installieren“ oder „Alle herunterladen und dann installieren“")

    Die Option „Alle herunterladen und dann installieren“ ist praktisch, wenn Sie zuerst alle Dateien herunterladen und die Installation später durchführen möchten.

1. Klicken Sie auf **Ändern** .

1. Klicken Sie im Visual Studio-Installer auf **Starten** , nachdem die neuen Workloads installiert wurden, um Visual Studio zu öffnen.

::: moniker-end

## <a name="modify-individual-components"></a>Ändern einzelner Komponenten

Wenn Sie keine Workloads zum Anpassen der Visual Studio-Installation verwenden möchten, wählen Sie die Registerkarte **Individuelle Komponenten** im Visual Studio-Installer und dann die gewünschten Komponenten aus. Anschließend befolgen Sie die Eingabeaufforderungen.

>[!TIP]
> Weitere Informationen zur SQL Server Data Tools-Komponente finden Sie unter [Herunterladen und Installieren von SQL Server Data Tools (SSDT) für Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true).

## <a name="modify-language-packs"></a>Ändern von Sprachpaketen

Standardmäßig stimmt das Installationsprogramm bei der ersten Ausführung mit der Sprache des Betriebssystems überein. Sie können jedoch jederzeit die Sprache wechseln. Wählen Sie dazu die Registerkarte **Sprachpakete** im Visual Studio-Installer und dann die gewünschte Sprache aus, und befolgen Sie anschließend die Anweisungen.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Weitere Informationen

* [Liste der Workload- und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)
* [Visual Studio aktualisieren](update-visual-studio.md)
* [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualisieren von Visual Studio innerhalb einer Baseline für die Wartung](update-servicing-baseline.md)
* [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)
