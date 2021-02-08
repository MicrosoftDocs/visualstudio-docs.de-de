---
title: Hinzufügen einer Verbindung mit Azure SQL-Datenbank | Microsoft-Dokumentation
description: Hinzufügen einer Azure SQL-Datenbankverbindung zu ihrer App mithilfe von Visual Studio verbundene Dienste
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 9e4a695a26e17e20fbd19081b863d9f108fc16b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841197"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Hinzufügen einer Verbindung mit der Azure SQL-Datenbank

Mit Visual Studio können Sie eine der folgenden Funktionen mit Azure SQL-Datenbank verbinden, indem Sie die **verbundene Dienste** -Funktion verwenden:

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Herstellen einer Verbindung mit der Azure SQL-Datenbank mithilfe von verbundene Dienste

1. Öffnen Sie Ihr Projekt in Visual Studio.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **verbundene Dienste** , und wählen Sie im Kontextmenü die Option **verbundenen Dienst hinzufügen** aus.

1. Wählen Sie auf der Registerkarte **verbundene Dienste** das Symbol + für **Dienst Abhängigkeiten** aus.

    ![Dienst Abhängigkeit hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Wählen Sie auf der Seite **Abhängigkeit hinzufügen** die Option **Azure SQL-Datenbank** aus.

    ![Azure SQL-Datenbankdienst hinzufügen](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Wenn Sie noch nicht angemeldet sind, melden Sie sich bei Ihrem Azure-Konto an. Wenn Sie nicht über ein Azure-Konto verfügen, können Sie sich für eine [Kostenlose Testversion](https://azure.microsoft.com/account/free)registrieren.

1. Wählen Sie auf dem Bildschirm **Azure SQL-Datenbank konfigurieren** eine vorhandene Azure SQL-Datenbank aus, und klicken Sie auf **weiter**.

    Wenn Sie eine neue Komponente erstellen müssen, fahren Sie mit dem nächsten Schritt fort. Andernfalls fahren Sie mit Schritt 7 fort.

    ![Herstellen einer Verbindung mit einer vorhandenen Azure SQL-Datenbankkomponente](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. So erstellen Sie eine Azure SQL-Datenbank:

   1. Wählen Sie unten auf dem Bildschirm die Option **SQL-Datenbank erstellen** aus.

   1. Füllen Sie die **Azure SQL-Datenbank aus: neuen** Bildschirm erstellen, und klicken Sie auf **Erstellen**.

       ![Neue Azure SQL-Datenbank](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Wenn der Bildschirm **Azure SQL-Datenbank konfigurieren** angezeigt wird, wird die neue Datenbank in der Liste angezeigt. Wählen Sie die neue Datenbank in der Liste aus, und klicken Sie auf **weiter**.

1. Geben Sie einen Namen für die Verbindungs Zeichenfolge ein, oder wählen Sie den Standardwert aus, und wählen Sie aus, ob die Verbindungs Zeichenfolge in einer lokalen Geheimnis Datei oder in [Azure Key Vault](/azure/key-vault)

   ![Verbindungs Zeichenfolge angeben](./media/azure-sql-database-add-connected-service/connection-string.png)

1. Der Bildschirm **Zusammenfassung der Änderungen** zeigt alle Änderungen an, die an Ihrem Projekt vorgenommen werden, wenn Sie den Prozess Fertigstellen. Wenn die Änderungen OK aussehen, klicken Sie auf **Fertig** stellen.

   ![Zusammenfassung der Änderungen](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Wenn Sie zum Festlegen von Firewallregeln aufgefordert werden, wählen Sie **Ja** aus.

   ![Firewallregeln](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. Die Verbindung wird im Abschnitt **Dienst Abhängigkeiten** der Registerkarte **verbundene Dienste** angezeigt.

   ![Dienstabhängigkeiten](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Weitere Informationen

- [Produktseite für Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/)
- [Dokumentation zu Azure SQL-Datenbank](/azure/azure-sql/database/)
- [Verbundene Dienste (Visual Studio für Mac)](/visualstudio/mac/connected-services)
