---
title: Verwenden von Cloud Services (erweiterter Support) (Vorschau)
description: Weitere Informationen zum Erstellen und Bereitstellen einer Cloud Services (erweiterter Support) mithilfe Azure Resource Manager in Visual Studio
author: ghogen
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: ff45cf05a6811c02881c26f76193d4c1f5a5e735
ms.sourcegitcommit: 7d34ab111614ae6bde5fb3c2bb91dd79e29a0a78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2021
ms.locfileid: "98750223"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio-preview"></a>Erstellen und Bereitstellen für Cloud Services (erweiterter Support) in Visual Studio (Vorschau)

Ab [Visual Studio 2019 Version 16,9](https://visualstudio.microsoft.com/vs/preview) (derzeit in der Vorschau Phase) können Sie mit Clouddiensten arbeiten, indem Sie Azure Resource Manager verwenden, wodurch die Wartung und Verwaltung von Azure-Ressourcen erheblich vereinfacht und optimiert wird. Dies wird durch einen neuen Azure-Dienst ermöglicht, der als *Cloud Services (erweiterter Support)* bezeichnet wird. Sie können einen vorhandenen clouddienst in Cloud Services veröffentlichen (erweiterter Support). Informationen zu diesem Azure-Dienst finden Sie in der [Dokumentation zu Cloud Services (erweiterter Support)](/azure/cloud-services-extended-support/overview).

## <a name="publish-to-cloud-services-extended-support"></a>In Cloud Services veröffentlichen (erweiterter Support)

Wenn Sie Ihr vorhandenes Azure-clouddienstprojekt in Cloud Services veröffentlichen (erweiterter Support), behalten Sie weiterhin die Möglichkeit, in einem klassischen Azure-clouddienst zu veröffentlichen. In Visual Studio 2019 Version 16,9 Preview 3 und höher verfügen klassische clouddienstprojekte über eine spezielle Version des **Veröffentlichungs** Befehls. **veröffentlichen (erweiterter Support)**. Dieser Befehl wird im Kontextmenü in **Projektmappen-Explorer** angezeigt.

Beim Veröffentlichen in Cloud Services (erweiterter Support) gibt es einige Unterschiede. Sie werden z. b. nicht gefragt, ob Sie in der **Staging** -oder **Produktions** Umgebung veröffentlichen, da diese Bereitstellungs Slots nicht Teil des erweiterten Unterstützungs Veröffentlichungs Modells sind. Stattdessen können Sie mit Cloud Services (erweiterter Support) mehrere bereit Stellungen einrichten und bereit Stellungen im Azure-Portal austauschen. Obwohl das Visual Studio-Tool das Festlegen dieser Einstellung in 16,9 Preview 3 ermöglicht, wird die swapfunktion erst nach einer neueren Version von Cloud Services (erweiterter Support) aktiviert und kann zur Bereitstellungs Zeit während der Vorschau zu einem Fehler führen.

Überprüfen Sie vor dem Veröffentlichen eines klassischen Azure-clouddiensts für Cloud Services (erweiterter Support) die Speicher Konten, die Ihr Projekt verwendet, und stellen Sie sicher, dass es sich um Storage v1-oder Storage v2 Bei den klassischen Speicherkonto Typen tritt zum Zeitpunkt der Bereitstellung eine Fehlermeldung auf. Stellen Sie sicher, dass Sie das von der Diagnose verwendete Speicherkonto überprüfen. Informationen zum Überprüfen des Diagnose Speicher Kontos finden Sie unter [Einrichten der Diagnose für Azure Cloud Services und virtuelle](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)Computer. Wenn Ihr Dienst ein klassisches Speicherkonto verwendet, können Sie es aktualisieren. Weitere Informationen finden [Sie unter Upgrade auf ein allgemeines v2-Speicherkonto](/azure/storage/common/storage-account-upgrade?tabs=azure-portal).  Allgemeine Informationen zu den Typen von Speicher Konten finden Sie unter [Übersicht über das Speicherkonto](/azure/storage/common/storage-account-overview).

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>So veröffentlichen Sie ein klassisches Azure-clouddienstprojekt in Cloud Services (erweiterter Support)

1. Cloud Services (erweiterter Support) befindet sich derzeit in der Vorschau Phase. Registrieren Sie das Feature wie folgt für Ihr Abonnement:

   ```azurepowershell-interactive
   Register-AzProviderFeature -FeatureName CloudServices -ProviderNamespace Microsoft.Compute
   ```

1. Klicken Sie mit der rechten Maustaste auf den Projekt Knoten in Ihrem Azure-clouddienst-Projekt (klassisch), und wählen Sie **veröffentlichen (erweiterter Support)...** aus. Der **Veröffentlichungs-Assistent** wird auf dem ersten Bildschirm geöffnet.

   ![Wählen Sie im Menü "veröffentlichen (erweiterter Support)" aus.](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   Der **Veröffentlichungs** -Assistent wird angezeigt.

   ![Anmeldeseite](./media/cloud-services-extended-support/publish-step1.png)

1. **Konto**: Wählen Sie ein Konto aus, oder wählen Sie in der Konto-Dropdownliste **Konto hinzufügen** aus.

1. **Abonnement wählen**: Wählen Sie das Abonnement aus, das Sie für Ihre Bereitstellung verwenden möchten.

1. Wählen Sie **weiter** aus, um zur Seite **Einstellungen** zu wechseln.

   ![Allgemeine Einstellungen](./media/cloud-services-extended-support/publish-settings.png)

1. **Clouddienst (erweiterter Support)** : Wählen Sie in der Dropdown Liste einen vorhandenen clouddienst (erweiterter Support) aus, oder wählen Sie **neu erstellen** aus, und erstellen Sie einen. Das Daten Center wird für jeden clouddienst (erweiterter Support) in Klammern angezeigt. Es wird empfohlen, dass der Speicherort des Rechenzentrums für den clouddienst (erweiterter Support) mit dem Speicherort des Rechenzentrums für das Speicherkonto identisch ist.

   Wenn Sie sich für die Erstellung eines neuen Diensts entscheiden, wird das Dialogfeld **clouddienst erstellen (erweiterter Support)** angezeigt. Geben Sie den Speicherort und die Ressourcengruppe an, die Sie für den clouddienst verwenden möchten (erweiterter Support).

   ![Erstellen eines clouddiensts (erweiterter Support)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **Buildkonfiguration**: Wählen Sie entweder **Debuggen** oder **Release** aus.

1. **Dienstkonfiguration**: Wählen Sie entweder **Cloud** oder **Lokal** aus.

1. **Speicherkonto** : Wählen Sie das für diese Bereitstellung zu verwendende Speicherkonto aus, oder **Erstellen Sie neu** , um ein Speicherkonto zu erstellen. Die Region wird für jedes Speicherkonto in Klammern angezeigt. Es wird empfohlen, für das Speicherkonto den gleichen Rechenzentrumsstandort wie für den Clouddienst zu verwenden (Erweiterte Einstellungen).

   Das Azure-Speicherkonto speichert das Paket für die Bereitstellung der Anwendung.

1. **Key Vault** : Geben Sie den Schlüssel Tresor an, der die geheimen Schlüssel für diesen Cloud-Dienst enthält (erweiterter Support). Diese Option ist aktiviert, wenn Remote Desktop aktiviert ist, oder wenn der Konfiguration Zertifikate hinzugefügt werden.

1. **Remotedesktop für alle Rollen aktivieren**: Aktivieren Sie diese Option, wenn Sie eine Remoteverbindung mit dem Dienst herstellen möchten. Sie werden aufgefordert, Anmelde Informationen anzugeben.

   ![Remote Desktop Einstellungen](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. Wählen Sie **weiter** aus, um zur Seite **Diagnose Einstellungen** zu wechseln.

   ![Diagnoseeinstellungen](./media/cloud-services-extended-support/diagnostics-settings.png)

   Die Diagnose ermöglicht Ihnen das Beheben von Problemen mit einem Azure-clouddienst (erweiterter Support). Informationen zur Diagnose finden Sie unter [Konfigurieren der Diagnose für Azure Cloud Services und Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) . Weitere Informationen zu Application Insights finden Sie unter [Was ist Application Insights?](/azure/application-insights/app-insights-overview).

1. Wählen Sie **weiter** aus, um zur Seite **Zusammenfassung** zu wechseln.

   ![Zusammenfassung](./media/cloud-services-extended-support/publish-summary.png)

1. **Zielprofil**: Sie können sich entscheiden, ein Veröffentlichungsprofil auf der Grundlage der von Ihnen ausgewählten Einstellungen zu erstellen. Sie können beispielsweise ein Profil für eine Testumgebung und ein weiteres für die Produktion verwenden. Um dieses Profil zu speichern, wählen Sie das Symbol **Speichern**. Der Assistent erstellt das Profil und speichert es im Visual Studio-Projekt. Um den Profilnamen zu ändern, öffnen Sie die Liste **Ziel Profil** , und wählen Sie dann **verwalten...** aus.

   > [!Note]
   > Das Veröffentlichungs Profil wird in Projektmappen-Explorer in Visual Studio angezeigt, und die Profileinstellungen werden in eine Datei mit der Erweiterung *azurepubxml* geschrieben. Einstellungen werden als Attribute der XML-Tags gespeichert.

1. Nachdem Sie alle Einstellungen für die Bereitstellung Ihres Projekts konfiguriert haben, wählen Sie unten im Dialogfeld **Veröffentlichen** aus. Sie können den Prozessstatus im Fenster Ausgabe des **Azure-Aktivitäts Protokolls** in Visual Studio überwachen. Wählen Sie den Link **im Portal öffnen zu aus** . 

Herzlichen Glückwunsch! Sie haben Ihr clouddienst-Projekt (Erweitertes Support) in Azure veröffentlicht. Wenn Sie mit denselben Einstellungen erneut veröffentlichen möchten, können Sie das Veröffentlichungs Profil wieder verwenden, oder Sie können diese Schritte wiederholen, um ein neues zu erstellen. Die Azure Resource Manager (Arm)-Vorlage und die Parameter, die für die Bereitstellung verwendet werden, werden im Ordner " *bin/ \<configuration\> /Publish* " gespeichert.

## <a name="clean-up-azure-resources"></a>Bereinigen von Azure-Ressourcen

Wechseln Sie zum Bereinigen der Azure-Ressourcen, die Sie in diesem Tutorial erstellt haben, zum [Azure-Portal](https://portal.azure.com), wählen Sie **Ressourcengruppen** aus, suchen Sie die Ressourcengruppe, die Sie zum Erstellen des clouddiensts verwendet haben (erweiterter Support), und wählen Sie dann **Ressourcengruppe löschen** aus.

## <a name="next-steps"></a>Nächste Schritte

Richten Sie Continuous Integration (CI) mithilfe der Schaltfläche **Konfigurieren** auf dem Bildschirm **veröffentlichen** ein. Weitere Informationen finden Sie unter [Azure Pipelines-Dokumentation](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).
