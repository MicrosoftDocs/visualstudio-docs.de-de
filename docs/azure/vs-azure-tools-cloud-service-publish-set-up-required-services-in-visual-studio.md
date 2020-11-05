---
title: Vorbereiten der Veröffentlichung oder Bereitstellung eines Clouddiensts
description: Lernen Sie die Verfahren zum Einrichten von Cloud- und Speicherkontodiensten und zum Konfigurieren Ihrer Azure-Anwendung kennen.
author: ghogen
manager: jillfra
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: a09b8f5c6efacab0f02a445ed78f8a3769031fa0
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399007"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Vorbereiten der Veröffentlichung und Bereitstellung eines Clouddiensts in Visual Studio

Zum Veröffentlichen eines Clouddienstprojekts müssen Sie die folgenden Dienste wie in diesem Artikel beschrieben einrichten:

* Einen **Clouddienst** zum Ausführen Ihrer Rollen in der Azure-Umgebung
* Ein **Speicherkonto** , das Zugriff auf die Blob-, Warteschlangen- und Tabellendienste bereitstellt

## <a name="create-a-cloud-service"></a>Erstellen eines Clouddiensts

Ein Clouddienst führt Ihre Rollen in der Azure-Umgebung aus. Sie können einen Clouddienst entweder in Visual Studio oder über das [Azure-Portal](https://portal.azure.com/) erstellen. Dies wird in den folgenden Abschnitten beschrieben.

### <a name="create-a-cloud-service-from-visual-studio"></a>Erstellen eines Clouddiensts in Visual Studio

1. Klicken Sie mit der rechten Maustaste auf ein zuvor erstelltes Projekt, und wählen Sie **Veröffentlichen**.
1. Melden Sie sich mit dem Microsoft- oder Organisationskonto an, das Ihrem Azure-Abonnement zugeordnet ist (falls erforderlich), und wählen Sie dann **Weiter** , um zur Seite **Einstellungen** zu gelangen.
1. Das Dialogfeld **Clouddienst und Speicherkonto erstellen** wird angezeigt (falls nicht: in der Liste **Clouddienst** die Option **Neu erstellen** wählen).
1. Geben Sie einen Namen für Ihren Clouddienst ein. Hierbei wird die Groß-/Kleinschreibung berücksichtigt, und der Name ist Teil Ihrer URL und muss eindeutig sein. Wählen Sie außerdem eine Region oder Affinitätsgruppe und eine Replikationsoption aus.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Erstellen eines Clouddiensts über das Azure-Portal

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.
1. Wählen Sie links auf der Seite die Option **Clouddienste (klassisch)**.
1. Wählen Sie **+ Hinzufügen** , und geben Sie die erforderlichen Informationen an (DNS-Name, Abonnement, Ressourcengruppe und Standort). Es ist hier nicht erforderlich, ein Paket hochzuladen, da Sie dies später in Visual Studio durchführen.
1. Wählen Sie **Erstellen** , um den Prozess abzuschließen.

## <a name="create-a-storage-account"></a>Speicherkonto erstellen

Ein Speicherkonto bietet Zugriff auf die Blob-, Warteschlangen- und Tabellendienste. Sie können ein Speicherkonto in Visual Studio oder über das [Azure-Portal](https://portal.azure.com/) erstellen.

### <a name="create-a-storage-account-from-visual-studio"></a>Erstellen eines Speicherkontos in Visual Studio

1. Suchen Sie im **Projektmappen-Explorer** für ein zuvor erstelltes Clouddienstprojekt den Knoten **Verbundene Dienste** eines Rollenprojekts, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Verbundenen Dienst hinzufügen**. (Klicken Sie in Visual Studio 2015 mit der rechten Maustaste auf den Knoten **Speicher** , und wählen Sie **Speicherkonto erstellen**.)
1. Wählen Sie in der angezeigten Liste **Verbundene Dienste** die Option **Cloudspeicher mit Azure Storage**.
1. Wählen Sie im angezeigten Azure Storage-Dialogfeld die Option **+Neues Speicherkonto erstellen**. Es wird ein Dialogfeld geöffnet, in dem Sie Ihr Abonnement, einen Namen für das Konto, einen Tarif, eine Ressourcengruppe und den Standort angeben können.
1. Wählen Sie **Erstellen** , wenn Sie fertig sind. Das neue Speicherkonto wird in der Liste mit den verfügbaren Speicherkonten Ihres Abonnements angezeigt.
1. Wählen Sie das Konto aus, und wählen Sie anschließend die Option **Hinzufügen**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Erstellen eines Speicherkontos über das Azure-Portal

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.
1. Wählen Sie oben links die Option **+ Neu**.
1. Wählen Sie unter „Azure Marketplace“ die Option **Speicher** und auf der rechten Seite dann **Speicherkonto – Blob, Datei, Tabelle, Warteschlange**.
1. Geben Sie die erforderlichen Informationen an (Name, Bereitstellungsmodell usw.).
1. Wählen Sie **Erstellen** , um den Prozess abzuschließen.

## <a name="configure-your-app-to-use-the-storage-account"></a>Konfigurieren Ihrer App für die Verwendung des Speicherkontos

Nachdem Sie ein Speicherkonto erstellt haben, werden beim Herstellen der Verbindung mit dem Konto aus Visual Studio automatisch die Dienstkonfigurationen für das Projekt aktualisiert, z.B. URLs und Zugriffsschlüssel.

Wenn Sie einen Clouddienst aus Visual Studio mit **Verbundenen Dienst hinzufügen** erstellt haben, können Sie die Verbindungen überprüfen, indem Sie `ServiceConfiguration.Cloud.cscfg` und `ServiceConfiguration.Local.cscfg` öffnen.

Wenn Sie einen Clouddienst über das Azure-Portal erstellt haben, können Sie die gleichen Schritte wie unter [Erstellen eines Speicherkontos in Visual Studio](#create-a-storage-account-from-visual-studio) ausführen. Erstellen Sie aber kein neues Konto, sondern wählen Sie ein vorhandenes aus. Visual Studio aktualisiert dann die Konfiguration für Sie.

Verwenden Sie zum manuellen Konfigurieren von Einstellungen die Eigenschaftenseiten in Visual Studio für die jeweilige Rolle in Ihrem Clouddienstprojekt. (Klicken Sie mit der rechten Maustaste auf die Rolle, und wählen Sie **Eigenschaften**.) Weitere Informationen finden Sie unter [Konfigurieren einer Verbindungszeichenfolge für ein Speicherkonto](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Informationen zu Zugriffsschlüsseln

Im Azure-Portal werden die URLs angezeigt, über die Sie auf Ressourcen in jedem der Azure-Speicherdienste zugreifen können, sowie die primären und sekundären Zugriffsschlüssel für Ihr Konto. Sie verwenden diese Schlüssel, um an die Speicherdienste gerichtete Anforderungen zu authentifizieren.

Der sekundäre Zugriffsschlüssel bietet denselben Zugriff auf Ihr Speicherkonto wie der primäre Zugriffschlüssel und wird als Reserveschlüssel generiert, sollte die Sicherheit Ihres primären Zugriffsschlüssels gefährdet sein. Darüber hinaus wird empfohlen, dass Sie Ihre Zugriffsschlüssel regelmäßig neu generieren. Sie können die Einstellung einer Verbindungszeichenfolge so ändern, dass der sekundäre Schlüssel verwendet werden soll, während Sie den primären Schlüssel neu generieren. Anschließend können Sie die Einstellung so ändern, dass der neu erstellte primäre Schlüssel genutzt werden soll, während Sie den sekundären Schlüssel neu generieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Veröffentlichen von Anwendungen in Azure aus Visual Studio finden Sie unter [Veröffentlichen eines Clouddiensts mit den Azure Tools](vs-azure-tools-publishing-a-cloud-service.md).
