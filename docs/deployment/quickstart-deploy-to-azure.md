---
title: Veröffentlichen in Azure App Service
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 5881e1dfb1842e2a6d85efe73534f8db2e2f734e
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830743"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Veröffentlichen einer Web-App in Azure App Service mit Visual Studio

Mithilfe einer der folgenden Methoden können Sie ASP.NET-, ASP.NET Core, Node.js und .NET Core-Apps in Azure App Service oder Azure App Service Linux (mit Containern) veröffentlichen.

* Verwenden Sie Azure DevOps mit [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true) für die kontinuierliche (oder automatisierte) Bereitstellung von Apps.

* Verwenden Sie für die einmalige (oder manuelle) Bereitstellung von Apps das Tool zum **Veröffentlichen** in Visual Studio, um ASP.NET-, ASP.NET Core-, Node.js- und .NET Core-Apps in Azure App Service oder [Azure App Service für Linux](../deployment/quickstart-deploy-to-linux.md) (mit Containern) bereitzustellen. Führen Sie für Python-Apps die Schritte unter [Python – Veröffentlichen in Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) aus.

In diesem Artikel wird beschrieben, wie Sie das Tool zum **Veröffentlichen** für die einmalige Bereitstellung verwenden.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Veröffentlichen in Azure App Service unter Windows

1. Klicken Sie im Projektmappen-Explorer erst mit der rechten Maustaste auf den Projektknoten, und wählen Sie dann **Veröffentlichen** aus. Alternativ können Sie auch das Menüelement **Erstellen** > **Veröffentlichen** verwenden.

    ![Der Befehl „Veröffentlichen“ im Kontextmenü des Projekts im Projektmappen-Explorer](../deployment/media/quickstart-publish.png "„Veröffentlichen“ auswählen")

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird das Fenster **Veröffentlichen** angezeigt. Wählen Sie **Neu**aus.

1. Wählen Sie im Fenster **Veröffentlichen** die Option **Azure** aus.

    ![Auswählen eines Veröffentlichungsziels](../deployment/media/quickstart-publish-azure-new.png)

1. Wählen Sie **Azure App Service (Windows)** und **Weiter** aus.

    ![Auswählen von Azure App Service für Linux](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. Melden Sie sich mit Ihrem Azure-Konto an, wenn erforderlich. Wählen Sie **Neue Azure App Service-Instanz erstellen...** aus.

    ![Link zum Erstellen einer neuen Instanz von Azure App Service](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. Im Dialogfeld **Azure App Service erstellen (Windows)** werden die Felder **App-Name**, **Ressourcengruppe** und **App Service-Plan** mit Daten aufgefüllt. Sie können diese Namen beibehalten oder ändern. Wählen Sie **Erstellen** aus, wenn Sie dazu bereit sind.

    ![Azure App Service auswählen](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. Im Dialogfeld **Veröffentlichen** wurde die neu erstellte Instanz automatisch ausgewählt. Wenn Sie bereit sind, wählen Sie **Fertig stellen** aus.

    ![Azure App Service auswählen](../deployment/media/quickstart-publish-windows-select-instance.png)

1. Wählen Sie **Veröffentlichen**. Visual Studio stellt die App in Azure App Service bereit, und die Web-App wird in Ihrem Browser geladen. Im Bereich **Veröffentlichen** werden in den Projekteigenschaften die Website-URL und andere Details angezeigt.

    ![Bereich „Veröffentlichen“ in den Projekteigenschaften mit einer Profilzusammenfassung](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

In den vorherigen Schritten haben Sie Azure-Ressourcen in einer Ressourcengruppe erstellt. Wenn Sie sich sicher sind, dass Sie diese Ressourcen in Zukunft nicht mehr benötigen, können Sie sie löschen, indem Sie die Ressourcengruppe entfernen.
Wählen Sie links im Azure-Portal **Ressourcengruppen** und anschließend **myResourceGroup** aus.
Vergewissern Sie sich, dass es sich bei den auf der Seite „Ressourcengruppe“ aufgeführten Ressourcen wirklich um die Ressourcen handelt, die gelöscht werden sollen.
Klicken Sie auf **Löschen**, geben Sie **myResourceGroup** in das Textfeld ein, und klicken Sie anschließend erneut auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie gelernt, wie Sie mithilfe von Visual Studio ein Veröffentlichungsprofil für die Bereitstellung in Azure erstellen. Sie können ein Veröffentlichungsprofil auch durch das Importieren von Veröffentlichungseinstellungen über Azure App Service konfigurieren.

> [!div class="nextstepaction"]
> [Importieren von Veröffentlichungseinstellungen und deren Bereitstellung in Azure](tutorial-import-publish-settings-azure.md)
