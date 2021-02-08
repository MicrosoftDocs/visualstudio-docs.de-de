---
title: Fügen Sie Azure cosmosdb hinzu, indem Sie verbundene Dienste | Microsoft-Dokumentation
description: Hinzufügen von Azure cosmosdb-Unterstützung zu ihrer App mithilfe von Visual Studio zum Hinzufügen eines verbundenen Dienstanbieter
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 070c1e77559e33ac398730b1bafc5a4a86825cda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841181"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Fügen Sie Azure Cosmos DB ihrer App mithilfe von Visual Studio hinzu verbundene Dienste

Mit Visual Studio können Sie eine der folgenden Funktionen mit Azure Cosmos DB verbinden, indem Sie die **verbundene Dienste** -Funktion verwenden:

- Konsolen-app .NET Framework
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .Net Core (einschließlich Konsolen-APP, WPF, Windows Forms, Klassenbibliothek)
- .Net Core-workerrolle
- Azure-Funktionen
- Universelle Windows-Plattform-App
- Xamarin
- Cordova

Mit der Funktion für verbundene Dienste werden die benötigten Verweise und der Verbindungscode zu Ihrem Projekt hinzugefügt und Ihre Konfigurationsdateien entsprechend geändert.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Verbundene Dienste in Visual Studio für Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio mit installierter Azure-Arbeitsauslastung.
- Ein Projekt mit einem der unterstützten Typen.

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Herstellen einer Verbindung mit Azure Cosmos DB mithilfe verbundene Dienste

1. Öffnen Sie Ihr Projekt in Visual Studio.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **verbundene Dienste** , und wählen Sie im Kontextmenü die Option **verbundenen Dienst hinzufügen** aus.

1. Wählen Sie auf der Registerkarte **verbundene Dienste** das Symbol + für **Dienst Abhängigkeiten** aus.

    ![Dienst Abhängigkeit hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Wählen Sie auf der Seite **Abhängigkeit hinzufügen** die Option **Azure Cosmos DB** aus.

    ![Azure Cosmos DB hinzufügen](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Wenn Sie noch nicht angemeldet sind, melden Sie sich bei Ihrem Azure-Konto an. Wenn Sie nicht über ein Azure-Konto verfügen, können Sie sich für eine [Kostenlose Testversion](https://azure.microsoft.com/account/free)registrieren.

1. Wählen Sie auf dem Bildschirm **Azure Cosmos DB** eine vorhandene Azure Cosmos DB aus, und klicken Sie auf **weiter**.

    Wenn Sie eine Datenbank erstellen müssen, fahren Sie mit dem nächsten Schritt fort. Andernfalls fahren Sie mit Schritt 7 fort.

    ![Vorhandenes Cosmos DB dem Projekt hinzufügen](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. So erstellen Sie eine Azure Cosmos DB:

   1. Wählen Sie unten auf dem Bildschirm **neue Azure Cosmos DB erstellen** aus.

   1. Füllen Sie den **Azure Cosmos DB: neuen** Bildschirm erstellen, und klicken Sie auf **Erstellen**.

       ![Neue Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Wenn das Dialogfeld " **Azure Cosmos DB konfigurieren** " angezeigt wird, wird die neue Datenbank in der Liste angezeigt. Wählen Sie die neue Datenbank in der Liste aus, und klicken Sie auf **weiter**.

1. Geben Sie einen Namen für die Verbindungs Zeichenfolge ein, und wählen Sie aus, ob die Verbindungs Zeichenfolge in einer lokalen Geheimnis Datei oder in [Azure Key Vault](/azure/key-vault)gespeichert werden soll

   ![Verbindungs Zeichenfolge angeben](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. Der Bildschirm **Zusammenfassung der Änderungen** zeigt alle Änderungen an, die an Ihrem Projekt vorgenommen werden, wenn Sie den Prozess Fertigstellen. Wenn die Änderungen OK aussehen, klicken Sie auf **Fertig** stellen.

   ![Zusammenfassung der Änderungen](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. Die Verbindung wird im Abschnitt **Dienst Abhängigkeiten** der Registerkarte **verbundene Dienste** angezeigt.

   ![Dienstabhängigkeiten](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Weitere Informationen

- [Azure Cosmos DB Produktseite](https://azure.microsoft.com/services/cosmos-db/)
- [Dokumentation zu Azure Cosmos DB](/azure/cosmos-db/)
- [Verbundene Dienste (Visual Studio für Mac)](/visualstudio/mac/connected-services)
