---
title: Hinzufügen von Azure Storage mithilfe von verbundenen Diensten | Microsoft-Dokumentation
description: Fügen Sie eine Azure Storage Dienst Abhängigkeit zu Ihrer APP hinzu, indem Sie Visual Studio verbundene Dienste
author: ghogen
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: d169940d6deffdf67bcbcb94e9f647631d0f606a
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902635"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Hinzufügen von Azure-Speicher mithilfe von verbundenen Visual Studio-Diensten

Mit Visual Studio können Sie eine der folgenden Funktionen mit Azure Storage verbinden, indem Sie die **verbundene Dienste** -Funktion verwenden:

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

## <a name="connect-to-azure-storage-using-connected-services"></a>Herstellen einer Verbindung mit Azure Storage mithilfe verbundene Dienste

::: moniker range="vs-2017"

1. Öffnen Sie Ihr Projekt in Visual Studio.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **verbundene Dienste** , und wählen Sie im Kontextmenü die Option **verbundenen Dienst hinzufügen** aus.

    ![Verbundenen Azure-Dienst hinzufügen](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. Wählen Sie auf der Seite **Verbundene Dienste** die Option **Cloudspeicher mit Azure Storage** aus.

    ![Azure Storage hinzufügen](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. Wählen Sie im Dialogfeld **Azure Storage** ein vorhandenes Speicherkonto aus, und klicken Sie dann auf **Hinzufügen**.

    Wenn Sie ein neues Speicherkonto erstellen müssen, fahren Sie mit dem nächsten Schritt fort. Fahren Sie ansonsten mit Schritt 6 fort.

    ![Vorhandenes Speicherkonto zum Projekt hinzufügen](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. So erstellen Sie ein Speicherkonto:

   1. Wählen Sie am unteren Rand des Dialogfelds die Option **Neues Speicherkonto erstellen** aus.

   1. Füllen Sie die erforderlichen Optionen im Dialogfeld **Speicherkonto erstellen** aus, und klicken Sie auf **Erstellen**.

       ![Neues Azure-Speicherkonto](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Wenn das Dialogfeld **Azure Storage** erneut geöffnet wird, wird das neue Speicherkonto in der Liste angezeigt. Wählen Sie das neue Speicherkonto in der Liste aus, und klicken Sie auf **Hinzufügen**.

1. Der verbundene Speicherdienst wird unter dem Knoten **Dienstverweise** Ihres Projekts angezeigt.
:::moniker-end

:::moniker range=">=vs-2019"

1. Öffnen Sie Ihr Projekt in Visual Studio.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **verbundene Dienste** , und wählen Sie im Kontextmenü die Option **verbundenen Dienst hinzufügen** aus.

    ![Verbundenen Azure-Dienst hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Wählen Sie auf der Registerkarte **verbundene Dienste** das Symbol + für **Dienst Abhängigkeiten** aus.

    ![Dienst Abhängigkeit hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Wählen Sie auf der Seite **Abhängigkeit hinzufügen** die Option **Azure Storage** aus.

    ![Azure Storage hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Wenn Sie noch nicht angemeldet sind, melden Sie sich bei Ihrem Azure-Konto an. Wenn Sie nicht über ein Azure-Konto verfügen, können Sie sich für eine [Kostenlose Testversion](https://azure.microsoft.com/account/free)registrieren.

1. Wählen Sie auf dem Bildschirm **Azure Storage konfigurieren** ein vorhandenes Speicherkonto aus, und klicken Sie auf **weiter**.

    Wenn Sie ein neues Speicherkonto erstellen müssen, fahren Sie mit dem nächsten Schritt fort. Fahren Sie ansonsten mit Schritt 6 fort.

    ![Vorhandenes Speicherkonto zum Projekt hinzufügen](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. So erstellen Sie ein Speicherkonto:

   1. Wählen Sie unten im Dialogfeld **Speicherkonto erstellen** aus.

   1. Füllen Sie das **Azure Storage:** Dialogfeld "neu erstellen" aus, und klicken Sie auf **Erstellen**.

       ![Neues Azure-Speicherkonto](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Wenn das Dialogfeld **Azure Storage** erneut geöffnet wird, wird das neue Speicherkonto in der Liste angezeigt. Wählen Sie das neue Speicherkonto in der Liste aus, und klicken Sie auf **weiter**.

1. Geben Sie einen Namen für die Verbindungs Zeichenfolge ein, und wählen Sie aus, ob die Verbindungs Zeichenfolge in einer lokalen Geheimnis Datei oder in [Azure Key Vault](/azure/key-vault)gespeichert werden soll

   ![Verbindungs Zeichenfolge angeben](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. Der Bildschirm **Zusammenfassung der Änderungen** zeigt alle Änderungen an, die an Ihrem Projekt vorgenommen werden, wenn Sie den Prozess Fertigstellen. Wenn die Änderungen OK aussehen, klicken Sie auf **Fertig** stellen.

   ![Zusammenfassung der Änderungen](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Der verbundene Speicherdienst wird unter dem Knoten **Dienstverweise** Ihres Projekts angezeigt.
:::moniker-end

## <a name="see-also"></a>Weitere Informationen

- [Azure Storage-Forum](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Azure Storage-Dokumentation](/azure/storage/)
- [Verbundene Dienste (Visual Studio für Mac)](/visualstudio/mac/connected-services)
