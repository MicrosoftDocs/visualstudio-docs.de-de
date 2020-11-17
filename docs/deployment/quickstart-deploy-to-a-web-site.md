---
title: Veröffentlichen auf einer Website
description: In diesem Artikel erfahren Sie, wie Sie mit dem Veröffentlichungstool ASP.NET-, ASP.NET Core-, .NET Core- und Python-Apps über Visual Studio auf einer Website veröffentlichen.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 027350b6a51cae5e7be88643624adc6955de91e4
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350698"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Veröffentlichen einer Web-App auf einer Website mithilfe von Visual Studio

Sie können das Tool zum **Veröffentlichen** verwenden, um ASP.NET-, ASP.NET Core-, .NET Core- und Python-Apps über Visual Studio auf einer Website zu veröffentlichen. Für Node.js können Sie zwar gleichen Schritte ausführen, jedoch ist die Benutzeroberfläche anders.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Wenn Sie eine Windows-Desktopanwendung für eine Netzwerkdateifreigabe veröffentlichen müssen, sehen Sie sich den Artikel [Bereitstellen einer Desktopanwendung mit ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# oder Visual Basic) an. Informationen zu C++/CLR finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), und Informationen zu C/C++ finden Sie unter [Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Veröffentlichen auf einer Website

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "„Veröffentlichen“ auswählen")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Wählen Sie **Neu** aus.

1. Wählen Sie im Fenster **Veröffentlichen** die Option **Webserver (IIS)** aus.

    ![Auswählen eines Veröffentlichungsziels](../deployment/media/quickstart-publish-iis.png "Auswählen von IIS, FTP, usw.")

1. Wählen Sie **Web Deploy** als Bereitstellungsmethode aus. Web Deploy vereinfacht die Bereitstellung von Web-Apps und Websites auf IIS-Servern und muss auf dem Server als Anwendung installiert werden. Verwenden Sie den [Webplattform-Installer](https://www.microsoft.com/web/downloads/platform.aspx) zur Installation.

    ![Auswählen der Bereitstellungsmethode](../deployment/media/quickstart-publish-iis-web-deploy.png "Auswählen von IIS, FTP, usw.")

1. Konfigurieren Sie die erforderlichen Einstellungen für die Veröffentlichungsmethode, und wählen Sie **Fertig stellen** aus. 

    ![Web Deploy-Verbindungsdetails](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Klicken Sie zum Veröffentlichen auf der Zusammenfassungsseite auf **Veröffentlichen**. Im Ausgabefenster werden der Fortschritt und das Ergebnis der Bereitstellung angezeigt.

   Weitere Informationen zur Problembehandlung von ASP.NET Core in IIS finden Sie unter [Problembehandlung bei ASP.NET Core in Azure App Service und IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie erfahren, wie Sie Visual Studio unter Linux verwenden können, um ein Veröffentlichungsprofil zu erstellen. Sie können ein Veröffentlichungsprofil auch durch das Importieren von Veröffentlichungseinstellungen konfigurieren.

> [!div class="nextstepaction"]
> [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in IIS](tutorial-import-publish-settings-iis.md)
