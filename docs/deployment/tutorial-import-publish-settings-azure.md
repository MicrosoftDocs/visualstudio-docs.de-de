---
title: Veröffentlichen in Azure durch Importieren von Veröffentlichungseinstellungen
description: Erstellen und Importieren eines Veröffentlichungsprofils zum Bereitstellen einer Anwendung aus Visual Studio in Azure App Service
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50a65d681693bd9c1421767d2cac47f65b685e6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945044"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Veröffentlichen einer Anwendung in Azure App Service durch Importieren von Veröffentlichungseinstellungen in Visual Studio

Sie können das Tool **Veröffentlichen** zum Importieren von Veröffentlichungseinstellungen verwenden. Anschließend können Sie die App bereitstellen. In diesem Artikel werden Veröffentlichungseinstellungen für Azure App Service verwendet, allerdings können Sie die gleiche Vorgehensweise zum Importieren von Veröffentlichungseinstellungen aus [IIS](../deployment/tutorial-import-publish-settings-iis.md) verwenden. Die Verwendung eines Veröffentlichungseinstellungsprofils kann sich in einigen Szenarios als schneller als das manuelle Konfigurieren der Bereitstellung in den Dienst für jede Installation von Visual Studio erweisen.

Die in diesem Artikel genannten Schritte gelten für ASP.NET, ASP.NET Core und .NET Core-Apps in Visual Studio. Sie können auch Veröffentlichungseinstellungen für [Python-Apps](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) importieren.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Generieren einer Veröffentlichungseinstellungsdatei aus Azure App Service
> * Importieren der Veröffentlichungseinstellungsdatei in Visual Studio
> * Bereitstellen der App in Azure App Service

Eine Veröffentlichungseinstellungsdatei ( *\*.publishsettings*) unterscheidet sich von einem in Visual Studio erstellten Veröffentlichungsprofil ( *\*.pubxml*). Eine Veröffentlichungseinstellungsdatei wird von Azure App Service erstellt und kann anschließend in Visual Studio importiert werden.

> [!NOTE]
> Sie müssen lediglich ein Visual Studio-Veröffentlichungsprofil ( *\*.pubxml*-Datei) aus einer Installation von Visual Studio in eine andere kopieren. Das Veröffentlichungsprofil *\<profilename\>.pubxml* finden Sie im Ordner *\\<Projektname\>\Properties\PublishProfiles* für verwaltete Projekttypen. Suchen Sie im Ordner *\App_Data* nach Websites. Die Veröffentlichungsprofile sind XML-Dateien von MSBuild.

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"

* Sie müssen Visual Studio 2019 und die Workload **ASP.NET und Webentwicklung** installiert haben.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.
::: moniker-end

::: moniker range="vs-2017"

* Sie müssen Visual Studio 2017 und die Workload **ASP.NET und Webentwicklung** installiert haben.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.
::: moniker-end

* Erstellen von Azure App Service. Ausführliche Anweisungen finden Sie unter [Veröffentlichen einer ASP.NET Core-App in Azure mit Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Erstellen eines neuen ASP.NET-Projekts in Visual Studio

1. Erstellen Sie ein neues Projekt auf dem Computer, auf dem Visual Studio ausgeführt wird.

    Wählen Sie die richtige Vorlage aus. Wählen Sie für dieses Beispiel entweder **ASP.NET-Webanwendung (.NET Framework)** oder **ASP.NET Core-Webanwendung** (nur für C#) aus, und wählen Sie anschließend **OK** aus.

    Wenn Ihnen die angegebenen Projektvorlagen nicht angezeigt werden, navigieren Sie im linken Bereich des Dialogfelds **Neues Projekt** zum Link **Visual Studio-Installer öffnen**. Der Visual Studio-Installer wird gestartet. Installieren Sie die Workload **ASP.NET und Webentwicklung**.

    Die ausgewählte Projektvorlage (ASP.NET oder ASP.NET Core) muss der ASP.NET-Version entsprechen, die auf dem Webserver installiert ist.

1. Wählen Sie entweder **MVC** (für .NET Framework) oder **Webanwendung (Model-View-Controller)** (für .NET Core) aus, und stellen Sie sicher, dass **Keine Authentifizierung** ausgewählt ist. Wählen Sie anschließend **OK** aus.

1. Geben Sie einen Namen wie **MyWebApp** ein, und wählen Sie **OK** aus.

    Visual Studio erstellt daraufhin das Projekt.

1. Klicken Sie auf **Erstellen** > **Projektmappe erstellen**, um das Projekt zu erstellen.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Erstellen der Veröffentlichungseinstellungsdatei in Azure App Service

1. Öffnen Sie Azure App Service im Azure-Portal.

1. Gehen Sie zu **Veröffentlichungsprofil abrufen**, und speichern Sie das Profil lokal.

    ![Abrufen des Veröffentlichungsprofils](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Eine Datei mit der Erweiterung *.publishsettings* wurde an dem Speicherort generiert, an dem Sie das Profil gespeichert haben. Im folgenden Code wird ein unvollständiges Beispiel der Datei gezeigt (mit einer lesbaren Formatierung).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```

    In der Regel enthält die genannte Datei „*.publishsettings“ zwei Veröffentlichungsprofile, die Sie in Visual Studio verwenden können. Ein Profil dient zum Bereitstellen mit Web Deploy und das andere zum Bereitstellen mit FTP. Im vorhergehenden Code wird das Web Deploy-Profil dargestellt. Wenn Sie das Profil importieren, werden zu einem späteren Zeitpunkt beide Profile importiert.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importieren und Bereitstellen der Veröffentlichungseinstellungen in Visual Studio

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie eine Veröffentlichungseinstellungsdatei erstellt, diese in Visual Studio importiert und eine ASP.NET-App in Azure App Service bereitgestellt. Sie sollten sich einen Überblick über Veröffentlichungsoptionen in Visual Studio verschaffen.

> [!div class="nextstepaction"]
> [Erster Einblick in die Bereitstellung](../deployment/deploying-applications-services-and-components.md)
