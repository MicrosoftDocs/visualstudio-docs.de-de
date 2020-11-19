---
title: Hinzufügen von Azure Cache für redis mithilfe von verbundene Dienste | Microsoft-Dokumentation
description: Hinzufügen von Azure Cache for redis-Unterstützung zu ihrer App mithilfe von Visual Studio zum Hinzufügen eines verbundenen Dienstanbieter
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: ad233d51e271dfbacb80b7f5f2792d546a8a3e0a
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903060"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Hinzufügen von Azure Cache für redis mithilfe von Visual Studio verbundene Dienste

Mit Visual Studio können Sie eine der folgenden Funktionen mit Azure Cache for redis verbinden, indem Sie die **verbundene Dienste** -Funktion verwenden:

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Herstellen einer Verbindung mit Azure Cache für redis mithilfe von verbundene Dienste

1. Öffnen Sie Ihr Projekt in Visual Studio.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **verbundene Dienste** , und wählen Sie im Kontextmenü die Option **verbundenen Dienst hinzufügen** aus.

1. Wählen Sie auf der Registerkarte **verbundene Dienste** das Symbol + für **Dienst Abhängigkeiten** aus.

    ![Dienst Abhängigkeit hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Wählen Sie auf der Seite **Abhängigkeit hinzufügen** die Option **Azure Cache für redis aus**.

    ![Hinzufügen von Azure Cache for Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Wenn Sie noch nicht angemeldet sind, melden Sie sich bei Ihrem Azure-Konto an. Wenn Sie nicht über ein Azure-Konto verfügen, können Sie sich für eine [Kostenlose Testversion](https://azure.microsoft.com/account/free)registrieren.

1. Wählen Sie im Bildschirm **Azure Cache für redis konfigurieren** einen vorhandenen Azure-Cache für redis aus, und klicken Sie auf **weiter**.

    Wenn Sie eine neue Komponente erstellen müssen, fahren Sie mit dem nächsten Schritt fort. Andernfalls fahren Sie mit Schritt 7 fort.

    ![Herstellen einer Verbindung mit vorhandenem Azure-Cache für redis](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. So erstellen Sie eine Azure redis Cache:

   1. Wählen Sie unten auf dem Bildschirm **neue Azure redis Cache erstellen** aus.

   1. Füllen Sie den Bildschirm **Azure Cache for redis: Create New** aus, und klicken Sie auf **Erstellen**.

       ![Neuer Azure-Cache für redis](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Wenn der Bildschirm **Azure-Cache für redis konfigurieren** angezeigt wird, wird der neue Cache in der Liste angezeigt. Wählen Sie die neue Datenbank in der Liste aus, und klicken Sie auf **weiter**.

1. Geben Sie einen Namen für die Verbindungs Zeichenfolge ein, oder wählen Sie den Standardwert aus, und wählen Sie aus, ob die Verbindungs Zeichenfolge in einer lokalen Geheimnis Datei oder in [Azure Key Vault](/azure/key-vault)

   ![Verbindungs Zeichenfolge angeben](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. Der Bildschirm **Zusammenfassung der Änderungen** zeigt alle Änderungen an, die an Ihrem Projekt vorgenommen werden, wenn Sie den Prozess Fertigstellen. Wenn die Änderungen OK aussehen, klicken Sie auf **Fertig** stellen.

   ![Zusammenfassung der Änderungen](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. Die Verbindung wird im Abschnitt **Dienst Abhängigkeiten** der Registerkarte **verbundene Dienste** angezeigt.

   ![Dienstabhängigkeiten](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Weitere Informationen

- [Azure Cache for redis-Produktseite](https://azure.microsoft.com/services/cache)
- [Dokumentation zu Azure Cache for Redis](/azure/azure-cache-for-redis/)
- [Verbundene Dienste (Visual Studio für Mac)](/visualstudio/mac/connected-services)