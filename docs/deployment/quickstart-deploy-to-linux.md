---
title: Veröffentlichen in App Service unter Linux
description: In diesem Artikel werden Methoden zum Veröffentlichen von ASP.NET Core-Apps in Azure App Service unter Linux mithilfe von Containern, einschließlich fortlaufender und einmaliger Optionen vorgestellt.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 27002d9360d36330249167b2cc8b75b7cd832135
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815632"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Veröffentlichen einer ASP.NET Core-App in Azure App Service mit Visual Studio unter Linux

Ab Version 15.7 von Visual Studio 2017 können Sie ASP.NET Core-Apps in Azure App Service Linux (mit Containern) mithilfe einer der folgenden Methoden veröffentlichen.

* Verwenden Sie Azure DevOps mit [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true) für die kontinuierliche (oder automatisierte) Bereitstellung von Apps.

* Verwenden Sie für die einmalige (oder manuelle) Bereitstellung von Apps das Tool zum **Veröffentlichen** in Visual Studio, um ASP.NET Core-Apps in App Service für Linux (mit Containern) zu veröffentlichen.

In diesem Artikel wird beschrieben, wie Sie das Tool zum **Veröffentlichen** für die einmalige Bereitstellung verwenden.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Veröffentlichen in Azure App Service für Linux

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf das Projekt und anschließend mit der linken auf **Veröffentlichen**. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "„Veröffentlichen“ auswählen")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird das Fenster **Veröffentlichen** angezeigt. Wählen Sie **Neu** aus.

1. Wählen Sie im Fenster **Veröffentlichen** die Option **Azure** aus.

    ![Auswählen eines Veröffentlichungsziels](../deployment/media/quickstart-publish-azure-new.png)

1. Wählen Sie **Azure App Service (Linux)** und dann **Weiter** aus.

    ![Auswählen von Azure App Service für Linux](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. Melden Sie sich mit Ihrem Azure-Konto an, wenn erforderlich. Wählen Sie **Neue Azure App Service-Instanz erstellen...** aus.

    ![Link zum Erstellen einer neuen Instanz von Azure App Service](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. Im Dialogfeld **Azure App Service erstellen (Linux)** werden die Felder **App-Name**, **Ressourcengruppe** und **App Service-Plan** mit Daten aufgefüllt. Sie können diese Namen beibehalten oder ändern. Wählen Sie **Erstellen** aus, wenn Sie dazu bereit sind.

    ![Screenshot: Dialogfeld „Azure App Service erstellen (Linux)“ mit Werten in den Feldern für „Name“, „Abonnement“, „Ressourcengruppe“ und „Hostingplan“](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. Im Dialogfeld **Veröffentlichen** wurde die neu erstellte Instanz automatisch ausgewählt. Wenn Sie dazu bereit sind, klicken Sie auf **Fertig stellen**.

    ![Screenshot: Dialogfeld „Veröffentlichen“ mit Auswahl des neu erstellten Diensts „MyASpCoreWebAppOnAzure“ als App Service für die Veröffentlichung](../deployment/media/quickstart-publish-linux-select-instance.png)

1. Wählen Sie **Veröffentlichen**. Visual Studio stellt die App in Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen. Im Bereich **Veröffentlichen** werden in den Projekteigenschaften die Website-URL und andere Details angezeigt.

    ![Bereich „Veröffentlichen“ in den Projekteigenschaften mit einer Profilzusammenfassung](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

In den vorherigen Schritten haben Sie Azure-Ressourcen in einer Ressourcengruppe erstellt. Wenn Sie sich sicher sind, dass Sie diese Ressourcen in Zukunft nicht mehr benötigen, können Sie sie löschen, indem Sie die Ressourcengruppe entfernen.
Wählen Sie links im Azure-Portal **Ressourcengruppen** und anschließend **myResourceGroup** aus.
Vergewissern Sie sich, dass es sich bei den auf der Seite „Ressourcengruppe“ aufgeführten Ressourcen wirklich um die Ressourcen handelt, die gelöscht werden sollen.
Klicken Sie auf **Löschen**, geben Sie **myResourceGroup** in das Textfeld ein, und klicken Sie anschließend erneut auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie erfahren, wie Sie Visual Studio unter Linux verwenden können, um ein Veröffentlichungsprofil für die Bereitstellung in App Service zu erstellen. Möglicherweise benötigen Sie weitere Informationen zum Veröffentlichen mit Azure unter Linux.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)