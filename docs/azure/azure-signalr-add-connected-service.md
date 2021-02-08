---
title: Hinzufügen von Azure signalr mithilfe verbundene Dienste | Microsoft-Dokumentation
description: Hinzufügen von Azure signalr zu ihrer App mithilfe von Visual Studio zum Hinzufügen eines verbundenen Dienstanbieter
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: a3b76115e7d5cfe484c9aea00246e4d42acf6268
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841158"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Hinzufügen von Azure signalr mithilfe von Visual Studio verbundene Dienste

Mit Visual Studio können Sie eine der folgenden Funktionen mit dem Azure signalr-Dienst verbinden, indem Sie die **verbundene Dienste** -Funktion verwenden:

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

## <a name="connect-to-azure-signalr-using-connected-services"></a>Herstellen einer Verbindung mit Azure signalr mithilfe von verbundene Dienste

1. Öffnen Sie Ihr Projekt in Visual Studio.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **verbundene Dienste** , und wählen Sie im Kontextmenü die Option **verbundenen Dienst hinzufügen** aus.

1. Wählen Sie auf der Registerkarte **verbundene Dienste** das Symbol + für **Dienst Abhängigkeiten** aus.

    ![Dienst Abhängigkeit hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Wählen Sie auf der Seite **Abhängigkeit hinzufügen** die Option **Azure signalr-Dienst** aus.

    ![Azure signalr Service hinzufügen](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Wenn Sie noch nicht angemeldet sind, melden Sie sich bei Ihrem Azure-Konto an. Wenn Sie nicht über ein Azure-Konto verfügen, können Sie sich für eine [Kostenlose Testversion](https://azure.microsoft.com/account/free)registrieren.

1. Wählen Sie auf dem Bildschirm **Konfigurieren von Azure signalr** eine vorhandene Azure signalr-Komponente aus, und klicken Sie auf **weiter**.

    Wenn Sie eine neue Komponente erstellen müssen, fahren Sie mit dem nächsten Schritt fort. Andernfalls fahren Sie mit Schritt 7 fort.

    ![Herstellen einer Verbindung mit einer vorhandenen Azure signalr-Komponente](./media/azure-signalr-add-connected-service/created-signalr.png)

1. So erstellen Sie eine Azure signalr-Dienst Instanz:

   1. Wählen Sie unten auf dem Bildschirm **eine neue Azure signalr-Dienst Instanz erstellen** aus.

   1. Füllen Sie den **Azure signalr-Dienst aus: neuen** Bildschirm erstellen, und klicken Sie auf **Erstellen**.

       ![Neue Azure signalr-Dienst Instanz](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Wenn der Bildschirm **Azure signalr-Dienst konfigurieren** angezeigt wird, wird die neue Instanz in der Liste angezeigt. Wählen Sie die neue Instanz in der Liste aus, und klicken Sie auf **weiter**.

1. Geben Sie einen Namen für die Verbindungs Zeichenfolge ein, oder wählen Sie den Standardwert aus, und wählen Sie aus, ob die Verbindungs Zeichenfolge in einer lokalen Geheimnis Datei oder in [Azure Key Vault](/azure/key-vault)

   ![Verbindungs Zeichenfolge angeben](./media/azure-signalr-add-connected-service/connection-string.png)

1. Der Bildschirm **Zusammenfassung der Änderungen** zeigt alle Änderungen an, die an Ihrem Projekt vorgenommen werden, wenn Sie den Prozess Fertigstellen. Wenn die Änderungen OK aussehen, klicken Sie auf **Fertig** stellen.

   ![Zusammenfassung der Änderungen](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. Die Verbindung wird im Abschnitt **Dienst Abhängigkeiten** der Registerkarte **verbundene Dienste** angezeigt.

   ![Dienstabhängigkeiten](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Weitere Informationen

- [Azure signalr-Produktseite](https://azure.microsoft.com/services/signalr-service/)
- [Dokumentation zu Azure SignalR Service](/azure/azure-signalr)
- [Verbundene Dienste (Visual Studio für Mac)](/visualstudio/mac/connected-services)
