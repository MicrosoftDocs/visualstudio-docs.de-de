---
title: Bereitstellen in einem lokalen Ordner
description: In diesem Artikel erfahren Sie, wie Sie das Veröffentlichungstool zum Veröffentlichen von ASP.NET-, ASP.NET Core-, .NET Core- und Python-Apps in einem Ordner von Visual Studio verwenden.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2b16c10d13f63be43ad2e8c3e16d24c0f9fd5e38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927430"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Bereitstellen einer App in einem Ordner mithilfe von Visual Studio

Sie können das Tool zum **Veröffentlichen** verwenden, um ASP.NET-, ASP.NET Core-, .NET Core- und Python-Apps über Visual Studio in einem Ordner zu veröffentlichen. Für Node.js können Sie zwar gleichen Schritte ausführen, jedoch ist die Benutzeroberfläche anders.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]
::: moniker range=">=vs-2017"
> [!NOTE]
> Wenn Sie eine Windows-Desktopanwendung für einen Ordner veröffentlichen müssen, sehen Sie sich den Artikel [Bereitstellen einer Desktopanwendung mit ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# oder Visual Basic) an. Informationen zu C++/CLR finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), und Informationen zu C/C++ finden Sie unter [Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

::: moniker-end

::: moniker range=">=vs-2019"
> [!NOTE]
> Wenn Sie eine Windows-Desktopanwendung mit .NET Core 3.1 oder höher in einem Ordner veröffentlichen müssen, finden Sie Informationen unter [Bereitstellen einer .NET-Windows-Anwendung mithilfe von ClickOnce](quickstart-deploy-using-clickonce-folder.md).

::: moniker-end

## <a name="deploy-to-a-local-folder"></a>Bereitstellen in einem lokalen Ordner

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "„Veröffentlichen“ auswählen")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird das Fenster **Veröffentlichen** angezeigt. Wählen Sie **Neu** aus.

1. Wählen Sie im Fenster **Veröffentlichen** die Option **Ordner** aus.

    ![Auswählen eines Ordners als Veröffentlichungsziel](../deployment/media/quickstart-publish-folder-new.png "Auswählen eines Ordners")

::: moniker range=">=vs-2019"

4. Wenn Sie eine Windows-Anwendung mit .NET Core 3.1 oder höher bereitstellen, müssen Sie im Fenster **Bestimmtes Ziel** auf **Ordner** klicken.

![Auswählen eines Ordners als bestimmtes Ziel](../deployment/media/quickstart-publish-folder-targets.png "Bestimmtes Ziel auswählen")

5. Wenn Sie eine .NET Core 3.1-Windows-Anwendung (oder höher) mit ClickOnce veröffentlichen möchten, finden Sie weitere Informationen unter [Bereitstellen einer .NET-Windows-Anwendung mit ClickOnce](quickstart-deploy-using-clickonce-folder.md).

 ::: moniker-end

4. Geben Sie einen Pfad ein, oder klicken Sie auf **Durchsuchen**, um einen Ordner anzugeben.

    ![Angeben des Pfads zum Ordner](../deployment/media/quickstart-publish-folder-path.png "Auswählen eines Ordners")

1. Wählen Sie **Veröffentlichen**. Dann erstellt Visual Studio das Projekt und veröffentlicht es im angegebenen Ordner. Anschließend wird der Bereich **Veröffentlichen** mit einer Profilübersicht angezeigt.

    ![Bereich „Veröffentlichen“ in den Projekteigenschaften mit einer Profilzusammenfassung](../deployment/media/quickstart-publish-folder-summary.png)

1. Wenn Sie Bereitstellungseinstellungen konfigurieren möchten, klicken Sie in der Zusammenfassung des Veröffentlichungsprofils zuerst auf **Bearbeiten** und dann auf die Registerkarte **Einstellungen**.

   Welche Einstellungen Sie sehen, hängt von Ihrem Anwendungstyp ab. Die folgende Abbildung enthält Beispieleinstellungen für eine ASP.NET Core-App.

    ![Profileinstellungen](../deployment/media/quickstart-profile-settings.png "Profileinstellungen")

    Weitere Hilfe zum Auswählen der Einstellungen in .NET finden Sie in den folgenden Themen:

    - [Übersicht über die .NET Core-Anwendungsveröffentlichung](/dotnet/core/deploying/)
    - [.NET Core-RID-Katalog](/dotnet/core/rid-catalog)
    - [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)

1. Konfigurieren Sie die Optionen, und legen Sie z.B. fest, ob eine Debug- oder Releasekonfiguration bereitgestellt werden soll, und klicken Sie anschließend auf **Speichern**.

1. Wenn Sie erneut eine Veröffentlichung durchführen möchten, klicken Sie auf **Veröffentlichen**.

Stellen Sie die veröffentlichen Dateien in einer beliebigen Weise bereit. Sie können sie z.B. in ein *ZIP*-Datei packen, einen einfachen Kopierbefehl verwenden, oder sie mit einem Installationspaket Ihrer Wahl bereitstellen.

## <a name="next-steps"></a>Nächste Schritte

Für .NET-Apps:

- [Bereitstellen einer .NET Core-Anwendung mit dem Tool „Veröffentlichen“](/dotnet/core/deploying/deploy-with-vs)
- [Übersicht über die .NET Core-Anwendungsveröffentlichung](/dotnet/core/deploying/)
- [Bereitstellen von .NET Framework und Anwendungen](/dotnet/framework/deployment/)
::: moniker range=">=vs-2019"
- [Bereitstellen einer .NET-Windows-Anwendung mithilfe von ClickOnce](quickstart-deploy-using-clickonce-folder.md)
 ::: moniker-end
