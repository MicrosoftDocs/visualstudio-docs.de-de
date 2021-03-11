---
description: Ab Visual Studio 2019, Version 16.8, können Sie mit dem Tool Veröffentlichen Desktopanwendungen für .NET Core 3.1 oder höher und Windows mithilfe von ClickOnce aus Visual Studio veröffentlichen.
title: Bereitstellen einer .NET-Desktopanwendung unter Windows mithilfe von ClickOnce
ms.date: 10/15/2020
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder, ClickOnce
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: john-hart
ms.author: JohnHart
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: d3977408f191aabc734226fd6b637fcfaaf5e9de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165708"
---
# <a name="deploy-a-net-windows-desktop-application-using-clickonce"></a>Bereitstellen einer .NET-Desktopanwendung unter Windows mithilfe von ClickOnce

Ab Visual Studio 2019, Version 16.8, können Sie mit dem Tool **Veröffentlichen** Desktopanwendungen für .NET Core 3.1 oder höher und Windows mithilfe von ClickOnce aus Visual Studio veröffentlichen.

> [!NOTE]
> Wenn Sie eine für das .NET Framework entwickelte Windows-Anwendung veröffentlichen müssen, sollten Sie den Artikel [Bereitstellen einer Desktop-App mit ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# oder Visual Basic) lesen.

## <a name="publishing-with-clickonce"></a>Veröffentlichen mit ClickOnce

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-clickonce-solution-explorer.png "„Veröffentlichen“ auswählen")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird das Fenster **Veröffentlichen** angezeigt. Wählen Sie **Neu** aus.

1. Klicken Sie im Assistenten zum **Veröffentlichen** auf **Ordner**.

    ![Auswählen eines Ordners als Veröffentlichungsziel](../deployment/media/quickstart-clickonce-publish-folder-category.png "Auswählen eines Ordners")

1. Wählen Sie auf der Seite **Bestimmtes Ziel** die Option **ClickOnce** aus.

    ![Auswählen von ClickOnce als bestimmtes Ziel](../deployment/media/quickstart-clickonce-publish-folder-target.png "Auswählen von ClickOnce")

1. Geben Sie einen Pfad ein, oder klicken Sie auf **Durchsuchen**, um den Veröffentlichungsort auszuwählen.

    ![Angeben des Pfads für den Veröffentlichungsort](../deployment/media/quickstart-clickonce-publish-location.png "Angeben eines Pfads")

1. Wählen Sie auf der Seite **Installationspfad** aus, von wo Benutzer die Anwendung installieren können.

    ![Angeben des Pfads zum Ordner](../deployment/media/quickstart-clickonce-install-location.png "Auswählen des Installationspfads")

1. Auf der Seite **Einstellungen** können Sie die für ClickOnce erforderlichen Einstellungen konfigurieren.

1. Wenn Sie die Installation über einen UNC-Pfad oder eine Website durchführen möchten, können Sie auf dieser Seite angeben, ob die Anwendung offline verfügbar ist. Ist diese Option ausgewählt, wird die Anwendung im Startmenü des Benutzers aufgeführt und kann automatisch aktualisiert werden, wenn eine neue Version veröffentlicht wird. Updates sind standardmäßig über den Installationspfad verfügbar.  Wenn Sie Updates über einen anderen Pfad verfügen machen möchten, können Sie diesen über den Link „Einstellungen für Updates“ angeben. Falls die Anwendung nicht offline verfügbar sein soll, wird sie über den Installationspfad ausgeführt.

    ![Angeben der Veröffentlichungseinstellungen](../deployment/media/quickstart-clickonce-unc-settings.png "Auswählen der Veröffentlichungseinstellungen")

1. Bei einer Installation über eine CD, eine DVD oder ein USB-Laufwerk können Sie auf dieser Seite auch angeben, ob die Anwendung automatische Updates unterstützt. Wenn Sie die Unterstützung von Updates aktivieren, muss der Speicherort für Updates als gültiger UNC-Pfad oder gültige Website angegeben werden.

    ![Auswählen der Veröffentlichungseinstellungen](../deployment/media/quickstart-clickonce-settings.png "Auswählen der Veröffentlichungseinstellungen")

Auf dieser Seite können Sie angeben, welche **Anwendungsdateien** beim Setup eingeschlossen und welche Pakete aus **Voraussetzungen** installiert werden sollen. Außerdem können Sie andere **Optionen** über die Links oben auf der Seite konfigurieren.

Auf dieser Seite können Sie auch festlegen, welche Version veröffentlicht wird und ob die Versionsnummer automatisch mit jeder Veröffentlichung hochgezählt wird.

> [!NOTE]
> Die Versionsnummer einer Veröffentlichung ist für jedes ClickOnce-Profil eindeutig. Wenn Sie mehr als ein Profil erstellen möchten, müssen Sie dies berücksichtigen.

10. Auf der Seite **Manifeste signieren** können Sie angeben, ob und mit welchem Zertifikat die Manifeste signiert werden sollen.

    ![Signieren der ClickOnce-Manifeste](../deployment/media/quickstart-clickonce-sign-manifests.png)

1. Auf der Seite **Konfiguration** kann die gewünschte Projektkonfiguration ausgewählt werden.

     ![Angeben der Veröffentlichungskonfiguration](../deployment/media/quickstart-clickonce-configuration.png)

    Weitere Informationen zu den auszuwählenden Optionen finden Sie in den folgenden Ressourcen:

    - [Übersicht über die .NET Core-Anwendungsveröffentlichung](/dotnet/core/deploying/)
    - [.NET Core-RID-Katalog](/dotnet/core/rid-catalog)
    - [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)

1. Klicken Sie auf **Fertigstellen**, um das neue ClickOnce-Veröffentlichungsprofil zu speichern.

1. Klicken Sie auf der Seite **Zusammenfassung** auf die Option **Veröffentlichen**, woraufhin Visual Studio das Projekt erstellt und es im angegebenen Veröffentlichungsordner veröffentlicht. Auf dieser Seite wird außerdem eine Profilzusammenfassung angezeigt.

    ![Bereich „Veröffentlichen“ in den Projekteigenschaften mit einer Profilzusammenfassung](../deployment/media/quickstart-clickonce-summary.png)

1. Wenn Sie erneut eine Veröffentlichung durchführen möchten, klicken Sie auf **Veröffentlichen**.

## <a name="next-steps"></a>Nächste Schritte

Für .NET-Apps:

- [Bereitstellen von .NET Framework und Anwendungen](/dotnet/framework/deployment/)
- [ClickOnce-Referenz](clickonce-reference.md)
