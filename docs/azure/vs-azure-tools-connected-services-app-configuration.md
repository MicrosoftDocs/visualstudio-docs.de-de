---
title: Fügen Sie Azure-App Konfiguration mit verbundene Dienste | Microsoft-Dokumentation
description: Hinzufügen einer Azure-Konfigurations Dienst Abhängigkeit zu ihrer App mithilfe von Visual Studio verbundene Dienste
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: a0db2f2e4993fcc3c986686322b8915615758e13
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727293"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Hinzufügen Azure-App Konfiguration mithilfe von Visual Studio verbundene Dienste

In diesem Tutorial erfahren Sie, wie Sie ganz einfach alles hinzufügen, was Sie benötigen, um die Konfiguration und featureflags für Webprojekte in Visual Studio zu Azure-App verwenden, und zwar unabhängig davon, ob Sie ASP.net Core oder eine beliebige Art von ASP.net Project verwenden. Wenn Sie die verbundene Dienste Funktion in Visual Studio verwenden, können Sie Visual Studio automatisch den gesamten Code, nuget-Pakete und Konfigurationseinstellungen hinzufügen, die Sie benötigen, um eine Verbindung mit Ihrer APP-Konfigurations Ressource in Azure herzustellen. Um dieses Feature verwenden zu können, müssen Sie Visual Studio 2019, Version 16,9 oder höher, verwenden.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Verbundene Dienste in Visual Studio für Mac](/visualstudio/mac/connected-services).

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio mit installierter Azure-Arbeitsauslastung.
- Ein Projekt mit einem der unterstützten Typen.

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>Herstellen einer Verbindung mit Azure-App Konfiguration mithilfe verbundene Dienste

1. Öffnen Sie Ihr Projekt in Visual Studio.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **verbundene Dienste** , und wählen Sie im Kontextmenü die Option **verbundenen Dienst hinzufügen** aus.

    ![Verbundenen Azure-Dienst hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Wählen Sie auf der Registerkarte **verbundene Dienste** das Symbol + für **Dienst Abhängigkeiten** aus.

    ![Dienst Abhängigkeit hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Wählen Sie auf der Seite **Abhängigkeit hinzufügen** **Azure-App Konfiguration** aus.

    ![App-Konfiguration hinzufügen](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    Wenn Sie noch nicht angemeldet sind, melden Sie sich bei Ihrem Azure-Konto an. Wenn Sie nicht über ein Azure-Konto verfügen, können Sie sich für eine [Kostenlose Testversion](https://azure.microsoft.com/free/dotnet)registrieren.

1. Wählen Sie auf dem Bildschirm **Konfiguration Azure-App Konfiguration** Ihr Abonnement und einen vorhandenen Konfigurations Speicher aus. Wählen Sie **Weiter** aus.

    Wenn Sie einen app-Konfigurations Speicher erstellen müssen, fahren Sie mit dem nächsten Schritt fort. Fahren Sie ansonsten mit Schritt 6 fort.

    ![Vorhandenes Konfigurations Konto zum Projekt hinzufügen](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. So erstellen Sie einen app-Konfigurations Speicher:

   1. Wählen Sie rechts neben dem Header **App-Konfigurations Speicher** das Symbol + aus. 

   1. Füllen Sie das Dialogfeld **Azure-App Konfiguration: neu erstellen** aus, und klicken Sie auf **Erstellen**. Beachten Sie, dass das Feld "Ressourcen Name" eindeutig sein muss. 

       ![Neuer Azure App-Konfigurations Speicher](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. Wenn das Dialogfeld **Azure-App Konfiguration** angezeigt wird, wird der neue Konfigurations Speicher in der Liste angezeigt. Wählen Sie diesen neuen Speicher aus, und klicken Sie dann auf **weiter**.

1. Geben Sie einen Namen für die Verbindungs Zeichenfolge ein, und wählen Sie aus, ob die Verbindungs Zeichenfolge in einer lokalen Geheimnis Datei oder in [Azure Key Vault](/azure/key-vault)gespeichert werden soll

   ![Verbindungs Zeichenfolge angeben](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. Der Bildschirm **Zusammenfassung der Änderungen** zeigt alle Änderungen an, die an Ihrem Projekt vorgenommen werden, wenn Sie den Prozess Fertigstellen. Wenn die Änderungen OK aussehen, klicken Sie auf **Fertig** stellen.

   ![Zusammenfassung der Änderungen](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. Nachdem der **Prozess für die Abhängigkeits Konfiguration** abgeschlossen ist, wird Azure-App Konfiguration nun unter dem Knoten **Dienst Abhängigkeiten** des Projekts angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über die Azure-App Konfiguration in [Azure-App Konfigurations Dokumentation](/azure/azure-app-configuration/overview).

## <a name="see-also"></a>Weitere Informationen

- [Tutorial für die Verwendung der dynamischen Konfiguration in einer APP-Konfiguration, die ASP.net Core App verbunden ist](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [Verbundene Dienste (Visual Studio für Mac)](/visualstudio/mac/connected-services)