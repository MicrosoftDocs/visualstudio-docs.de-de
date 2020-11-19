---
title: Fügen Sie Azure-Anwendung Insights mithilfe verbundene Dienste | Microsoft-Dokumentation
description: Hinzufügen von Azure-Anwendung Insights zu ihrer App mithilfe von Visual Studio zum Hinzufügen eines verbundenen Dienstanbieter
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 1317f41c9463ab645e6dd3ba281f11b9246720a8
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901933"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Fügen Sie Azure-Anwendung Insights mithilfe von Visual Studio hinzu verbundene Dienste

Mit Visual Studio können Sie eine der folgenden Funktionen verwenden, um Einblicke zu Azure-Anwendung, indem Sie die **verbundene Dienste** -Funktion verwenden:

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

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Herstellen einer Verbindung mit Azure-Anwendung Insights mithilfe verbundene Dienste

1. Öffnen Sie Ihr Projekt in Visual Studio.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **verbundene Dienste** , und wählen Sie im Kontextmenü die Option **verbundenen Dienst hinzufügen** aus.

1. Wählen Sie auf der Registerkarte **verbundene Dienste** das Symbol + für **Dienst Abhängigkeiten** aus.

    ![Dienst Abhängigkeit hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Wählen Sie auf der Seite **Abhängigkeit hinzufügen** die Option **Azure-Anwendung Insights** aus.

    ![Hinzufügen von Azure-Anwendung Insights](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Wenn Sie noch nicht angemeldet sind, melden Sie sich bei Ihrem Azure-Konto an. Wenn Sie nicht über ein Azure-Konto verfügen, können Sie sich für eine [Kostenlose Testversion](https://azure.microsoft.com/account/free)registrieren.

1. Wählen Sie auf dem Bildschirm **Azure-Anwendung Insights konfigurieren** eine vorhandene Azure-Anwendung Insights-Komponente aus, und klicken Sie auf **weiter**.

    Wenn Sie eine neue Komponente erstellen müssen, fahren Sie mit dem nächsten Schritt fort. Andernfalls fahren Sie mit Schritt 7 fort.

    ![Verbindung mit vorhandener Application Insights Komponente herstellen](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. So erstellen Sie eine Application Insights Komponente:

   1. Wählen Sie unten auf dem Bildschirm **eine neue Application Insights Komponente erstellen** aus.

   1. Füllen Sie den **Application Insights: neuen** Bildschirm erstellen, und klicken Sie auf **Erstellen**.

       ![Neue Azure-App Insights-Komponente](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. Wenn der Bildschirm **Azure-Anwendung Insights konfigurieren** angezeigt wird, wird die neue Komponente in der Liste angezeigt. Wählen Sie die neue Komponente in der Liste aus, und klicken Sie auf **weiter**.

1. Geben Sie einen Instrumentierungs Schlüsselnamen ein, oder wählen Sie den Standardwert aus, und wählen Sie aus, ob die Verbindungs Zeichenfolge in einer lokalen Geheimnis Datei oder in [Azure Key Vault](/azure/key-vault)gespeichert werden soll.

   ![Verbindungs Zeichenfolge angeben](./media/azure-app-insights-add-connected-service/connection-string.png)

1. Der Bildschirm **Zusammenfassung der Änderungen** zeigt alle Änderungen an, die an Ihrem Projekt vorgenommen werden, wenn Sie den Prozess Fertigstellen. Wenn die Änderungen OK aussehen, klicken Sie auf **Fertig** stellen.

   ![Zusammenfassung der Änderungen](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. Die Verbindung wird im Abschnitt **Dienst Abhängigkeiten** der Registerkarte **verbundene Dienste** angezeigt.

   ![Dienstabhängigkeiten](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Weitere Informationen

- [Azure Monitor Produktseite](https://azure.microsoft.com/services/monitor/)
- [Dokumentation zu Azure-App Insights](/azure/azure-monitor/app/app-insights-overview/)
- [Verbundene Dienste (Visual Studio für Mac)](/visualstudio/mac/connected-services)
