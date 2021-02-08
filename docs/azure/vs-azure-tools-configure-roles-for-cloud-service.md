---
title: Konfigurieren der Rollen für einen Azure-Clouddienst
description: Erfahren Sie, wie Rollen für Azure-Clouddienste mithilfe von Visual Studio eingerichtet und konfiguriert werden.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 8695840c48a39c6485d7b9c9b70835872f1104bb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844384"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Konfigurieren von Rollen für Azure-Clouddienste mit Visual Studio
Ein Azure-Clouddienst kann einen oder mehrere Worker- oder Webrollen aufweisen. Für jede Rolle müssen Sie definieren, wie die Rolle eingerichtet ist, und konfigurieren, wie die Rolle ausgeführt wird. Weitere Informationen zu Rollen in Clouddiensten erhalten Sie im Video [Introduction to Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services)(in englischer Sprache).

Die Informationen für Ihren Clouddienst werden in den folgenden Dateien gespeichert:

- Service **Definition. csdef** : die Dienst Definitionsdatei definiert die Lauf Zeit Einstellungen für Ihren clouddienst, einschließlich der erforderlichen Rollen, Endpunkte und der Größe des virtuellen Computers. Die in `ServiceDefinition.csdef` gespeicherten Daten können während der Ausführung der Rolle nicht geändert werden.
- **ServiceConfiguration.cscfg**: Die Dienstkonfigurationsdatei konfiguriert, wie viele Instanzen einer Rolle ausgeführt werden, und die Werte der für eine Rolle definierten Einstellungen. Die in `ServiceConfiguration.cscfg` gespeicherten Daten können während der Ausführung der Rolle geändert werden.

Um verschiedene Werte für die Einstellungen zur Ausführungsweise der Rolle zu speichern, können mehrere Dienstkonfigurationen definiert werden. Sie können unterschiedliche Dienstkonfigurationen für die einzelnen Bereitstellungsumgebungen verwenden. Beispielsweise können Sie die Verbindungs Zeichenfolge für das Speicherkonto so festlegen, dass der lokale Azure Storage Emulator in einer lokalen Dienst Konfiguration verwendet wird, und eine weitere Dienst Konfiguration erstellen, um Azure Storage in der Cloud zu verwenden.

Beim Erstellen eines Azure-Clouddiensts in Visual Studio werden standardmäßig zwei Dienstkonfigurationen erstellt und Ihrem Azure-Projekt hinzugefügt:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Konfigurieren eines Azure-Clouddiensts
Sie können einen Azure-Clouddienst vom Projektmappen-Explorer in Visual Studio aus konfigurieren, wie in den folgenden Schritten dargestellt:

1. Erstellen oder öffnen Sie ein Azure-Clouddienstprojekt in Visual Studio.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie im Kontextmenü die Option **Eigenschaften** aus.

    ![Projektkontextmenü des Projektmappen-Explorers](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Wählen Sie auf der Eigenschaftenseite des Projekts die Registerkarte **Entwicklung** aus.

    ![Projekt-Eigenschaftenseite – Registerkarte „Entwicklung“](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. Wählen Sie in der Liste **Dienstkonfiguration** den Namen der Dienstkonfiguration aus, die Sie bearbeiten möchten. (Wenn Sie Änderungen an allen Dienstkonfigurationen für diese Rolle vornehmen möchten, wählen Sie **Alle Konfigurationen** aus.)

    > [!IMPORTANT]
    > Wenn Sie eine bestimmte Dienstkonfiguration auswählen, sind einige Eigenschaften deaktiviert, da sie nur für alle Konfigurationen festgelegt werden können. Um diese Eigenschaften zu bearbeiten, müssen Sie **Alle Konfigurationen** auswählen.

    ![Dienstkonfigurationsliste für einen Azure-Clouddienst](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Ändern der Anzahl von Rolleninstanzen
Um die Leistung des Clouddiensts zu verbessern, können Sie die Anzahl der ausgeführten Instanzen einer Rolle basierend auf der Anzahl der Benutzer oder der erwarteten Auslastung für eine Rolle ändern. Wenn der Clouddienst in Azure ausgeführt wird, wird ein separater virtueller Computer für jede Instanz einer Rolle erstellt. Dies wirkt sich auf die Abrechnung für die Bereitstellung dieses Clouddiensts aus. Weitere Informationen zur Abrechnung finden Sie unter [Informationen zu Ihrer Rechnung für Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Erstellen oder öffnen Sie ein Azure-Clouddienstprojekt in Visual Studio.

1. Erweitern Sie in **Projektmappen-Explorer** den Projekt Knoten. Klicken Sie unter dem Knoten **Rollen** mit der rechten Maustaste auf die Rolle, die Sie aktualisieren möchten, und wählen Sie im Kontextmenü **Eigenschaften** aus.

    ![Azure-Rollenkontextmenü im Projektmappen-Explorer](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wählen Sie die Registerkarte **Konfiguration** aus.

    ![Registerkarte „Konfiguration“](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. Wählen Sie in der Liste **Dienstkonfiguration** die Dienstkonfiguration aus, die Sie aktualisieren möchten.

    ![Dienst Konfigurations Liste 1](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. Geben Sie im Textfeld **Instanzenanzahl** die Anzahl der Instanzen ein, die Sie für diese Rolle starten möchten. Jede Instanz wird auf einem separaten virtuellen Computer ausgeführt, wenn Sie den Clouddienst in Azure veröffentlichen.

    ![Aktualisieren der Anzahl der Instanzen](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Wählen Sie in der Visual Studio-Symbolleiste die Option **Speichern** aus.

## <a name="manage-connection-strings-for-storage-accounts"></a>Verwalten von Verbindungszeichenfolgen für Speicherkonten
Sie können Verbindungszeichenfolgen für Ihre Dienstkonfigurationen hinzufügen, entfernen oder ändern. Beispielsweise möchten Sie eine lokale Verbindungszeichenfolge für eine lokale Dienstkonfiguration mit dem Wert `UseDevelopmentStorage=true`festlegen. Sie können auch eine Clouddienstkonfiguration konfigurieren, die ein Speicherkonto in Azure verwendet.

> [!WARNING]
> Wenn Sie die Schlüsselinformationen eines Azure-Speicherkontos für eine Speicherkonto-Verbindungszeichenfolge eingeben, werden diese Informationen lokal in der Dienstkonfigurationsdatei gespeichert. Diese Informationen werden jedoch derzeit nicht als verschlüsselter Text gespeichert.
>
>

Wenn Sie verschiedene Werte für die einzelnen Dienstkonfigurationen verwenden, müssen Sie nicht verschiedene Verbindungszeichenfolgen im Clouddienst verwenden oder Ihren Code ändern, wenn Sie Ihren Clouddienst in Azure veröffentlichen. Im Code können Sie denselben Namen für die Verbindungszeichenfolge verwenden. Der Wert unterscheidet sich basierend auf der Dienstkonfiguration, die Sie auswählen, wenn Sie einen Clouddienst erstellen oder veröffentlichen.

1. Erstellen oder öffnen Sie ein Azure-Clouddienstprojekt in Visual Studio.

1. Erweitern Sie in **Projektmappen-Explorer** den Projekt Knoten. Klicken Sie unter dem Knoten **Rollen** mit der rechten Maustaste auf die Rolle, die Sie aktualisieren möchten, und wählen Sie im Kontextmenü **Eigenschaften** aus.

    ![Azure-Rollenkontextmenü im Projektmappen-Explorer](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wählen Sie die Registerkarte **Einstellungen** aus.

    ![Registerkarte "Einstellungen"](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Wählen Sie in der Liste **Dienstkonfiguration** die Dienstkonfiguration aus, die Sie aktualisieren möchten.

    ![Dienstkonfiguration](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Wenn Sie eine Verbindungszeichenfolge hinzufügen möchten, wählen Sie **Einstellung hinzufügen** aus.

    ![Verbindungszeichenfolge hinzufügen](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Nachdem die neue Einstellung zur Liste hinzugefügt wurde, aktualisieren Sie die Zeile in der Liste mit den erforderlichen Informationen.

    ![Neue Verbindungszeichenfolge](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Name**: Geben Sie den Namen ein, den Sie für die Verbindungszeichenfolge verwenden möchten.
    - **Typ**: Wählen Sie in der Dropdownliste **Verbindungszeichenfolge** aus.
    - **Wert**: Sie können die Verbindungszeichenfolge entweder direkt in die Zelle **Wert** eingeben oder die Auslassungspunkte (...) auswählen, um im Dialogfeld **Verbindungszeichenfolge für den Speicher erstellen** zu arbeiten.

1. Wählen Sie im Dialogfeld **Verbindungszeichenfolge für den Speicher erstellen** eine Option für **Herstellen einer Verbindung mit** aus. Befolgen Sie dann die Anweisungen für die ausgewählte Option:

    - **Microsoft Azure-Speicheremulator** : Wenn Sie diese Option auswählen, werden die restlichen Einstellungen im Dialogfeld deaktiviert, da Sie nur für Azure gelten. Klicken Sie auf **OK**.
    - **Ihr Abonnement**: Wenn Sie diese Option auswählen, verwenden Sie entweder die Dropdownliste, um ein Microsoft-Konto auszuwählen und sich anzumelden, oder fügen Sie ein Microsoft-Konto hinzu. Wählen Sie ein Azure-Abonnement- und -Speicherkonto aus. Klicken Sie auf **OK**.
    - **Manuell eingegebene Anmeldeinformationen**: Geben Sie den Speicherkontonamen und dann entweder den primären oder den sekundären Schlüssel ein. Wählen Sie eine Option für die **Verbindung** aus (HTTPS wird in den meisten Szenarien empfohlen). Wählen Sie **OK** aus.

1. Um eine Verbindungszeichenfolge zu löschen, wählen Sie die Verbindungszeichenfolge aus, und wählen Sie dann **Einstellung entfernen** aus.

1. Wählen Sie in der Visual Studio-Symbolleiste die Option **Speichern** aus.

## <a name="programmatically-access-a-connection-string"></a>Programmgesteuerter Zugriff auf eine Verbindungszeichenfolge

Die folgenden Schritte zeigen, wie Sie programmgesteuert mithilfe von C# auf eine Verbindungszeichenfolge zugreifen.

1. Fügen Sie einer C#-Datei, in der Sie die Einstellung verwenden möchten, die folgenden using-Direktiven hinzu:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Der folgende Code ist ein Beispiel für den Zugriff auf eine Verbindungszeichenfolge. Ersetzen Sie den Platzhalter &lt;NameDerVerbindungszeichenfolge> durch den passenden Wert.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Hinzufügen benutzerdefinierter Einstellungen zur Verwendung in Ihrem Azure-Clouddienst
Benutzerdefinierte Einstellungen in der Dienstkonfigurationsdatei ermöglichen das Hinzufügen eines Namens und eines Werts für eine Zeichenfolge für eine bestimmte Dienstkonfiguration. Sie können diese Einstellung verwenden, um ein Feature in Ihrem Clouddienst zu konfigurieren, indem Sie den Wert der Einstellung lesen und diesen Wert zum Steuern der Logik im Code verwenden. Sie können diese Dienstkonfigurationswerte ohne erneute Erstellung des Dienstpakets oder während der Ausführung des Clouddiensts ändern. Der Code kann auf Benachrichtigungen bzgl. Änderungen einer Einstellung prüfen. Weitere Informationen finden Sie unter [RoleEnvironment.Changing-Ereignis](/previous-versions/azure/reference/ee758134(v=azure.100)).

Sie können benutzerdefinierte Einstellungen für Ihre Dienstkonfigurationen hinzufügen, entfernen oder ändern. Möglicherweise möchten Sie verschiedene Werte für diese Zeichenfolgen für verschiedene Dienstkonfigurationen verwenden.

Wenn Sie verschiedene Werte für die einzelnen Dienstkonfigurationen verwenden, müssen Sie nicht verschiedene Zeichenfolgen im Clouddienst verwenden oder Ihren Code ändern, wenn Sie Ihren Clouddienst in Azure veröffentlichen. Im Code können Sie denselben Namen für die Zeichenfolge verwenden. Der Wert unterscheidet sich basierend auf der Dienstkonfiguration, die Sie auswählen, wenn Sie einen Clouddienst erstellen oder veröffentlichen.

1. Erstellen oder öffnen Sie ein Azure-Clouddienstprojekt in Visual Studio.

1. Erweitern Sie in **Projektmappen-Explorer** den Projekt Knoten. Klicken Sie unter dem Knoten **Rollen** mit der rechten Maustaste auf die Rolle, die Sie aktualisieren möchten, und wählen Sie im Kontextmenü **Eigenschaften** aus.

    ![Azure-Rollenkontextmenü im Projektmappen-Explorer](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wählen Sie die Registerkarte **Einstellungen** aus.

    ![Registerkarte "Einstellungen"](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Wählen Sie in der Liste **Dienstkonfiguration** die Dienstkonfiguration aus, die Sie aktualisieren möchten.

    ![Dienst Konfigurations Liste 2](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Zum Hinzufügen einer benutzerdefinierten Einstellung wählen Sie **Einstellung hinzufügen** aus.

    ![Benutzerdefinierte Einstellung hinzufügen](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Nachdem die neue Einstellung zur Liste hinzugefügt wurde, aktualisieren Sie die Zeile in der Liste mit den erforderlichen Informationen.

    ![Neue benutzerdefinierte Einstellung](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Name**: Geben Sie den Namen der Einstellung ein.
    - **Typ**: Wählen Sie in der Dropdownliste **Zeichenfolge** aus.
    - **Wert**: Geben Sie den Wert der Einstellung ein. Sie können den Wert entweder direkt in die Zelle **Wert** eingeben oder die Auslassungspunkte (...) auswählen, um den Wert im Dialogfeld **Zeichenfolge bearbeiten** einzugeben.

1. Um eine benutzerdefinierte Einstellung zu löschen, wählen Sie die Einstellung aus, und wählen Sie dann **Einstellung entfernen** aus.

1. Wählen Sie in der Visual Studio-Symbolleiste die Option **Speichern** aus.

## <a name="programmatically-access-a-custom-settings-value"></a>Programmgesteuerter Zugriff auf den Wert einer benutzerdefinierten Einstellung

Die folgenden Schritte zeigen, wie Sie programmgesteuert mithilfe von C# auf eine benutzerdefinierte Einstellung zugreifen.

1. Fügen Sie einer C#-Datei, in der Sie die Einstellung verwenden möchten, die folgenden using-Direktiven hinzu:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Der folgende Code ist ein Beispiel für den Zugriff auf eine benutzerdefinierte Einstellung. Ersetzen Sie den Platzhalter &lt;NameDerEinstellung> durch den passenden Wert.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Verwalten von lokalem Speicher für jede Rolleninstanz
Sie können lokalen Dateisystemspeicher für jede Instanz einer Rolle hinzufügen. Auf die im betreffenden Speicher gespeicherten Daten können weder andere Instanzen der Rolle, für die die Daten gespeichert wurden, noch andere Rollen zugreifen.

1. Erstellen oder öffnen Sie ein Azure-Clouddienstprojekt in Visual Studio.

1. Erweitern Sie in **Projektmappen-Explorer** den Projekt Knoten. Klicken Sie unter dem Knoten **Rollen** mit der rechten Maustaste auf die Rolle, die Sie aktualisieren möchten, und wählen Sie im Kontextmenü **Eigenschaften** aus.

    ![Azure-Rollenkontextmenü im Projektmappen-Explorer](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wählen Sie die Registerkarte **Lokaler Speicher** aus.

    ![Registerkarte „Lokaler Speicher“](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. Stellen Sie sicher, dass in der Liste **Dienstkonfiguration** der Eintrag **Alle Konfigurationen** ausgewählt ist, da sich die Einstellungen für den lokalen Speicher auf alle Dienstkonfigurationen beziehen. Jeder andere Wert führt dazu, dass alle Eingabefelder auf der Seite deaktiviert werden.

    ![Dienst Konfigurations Liste 3](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Um einen lokalen Speichereintrag hinzuzufügen, wählen Sie **Lokalen Speicher hinzufügen** aus.

    ![Lokalen Speicher hinzufügen](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Nachdem der neue lokale Speichereintrag zur Liste hinzugefügt wurde, aktualisieren Sie die Zeile in der Liste mit den erforderlichen Informationen.

    ![Neuer lokaler Speichereintrag](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Name**: Geben Sie den Namen ein, den Sie für den neuen lokalen Speicher verwenden möchten.
    - **Größe (MB)**: Geben Sie die benötigte Größe in MB für den neuen lokalen Speicher ein.
    - **Bei Wiederverwendung der Rolle bereinigen**: Aktivieren Sie diese Option, um die Daten im neuen lokalen Speicher zu entfernen, wenn der virtuelle Computer für die Rolle wiederverwendet wird.

1. Um einen lokalen Speichereintrag zu löschen, wählen Sie den Eintrag aus, und wählen Sie dann **Lokalen Speicher entfernen** aus.

1. Wählen Sie in der Visual Studio-Symbolleiste die Option **Speichern** aus.

## <a name="programmatically-accessing-local-storage"></a>Programmgesteuerter Zugriff auf lokalen Speicher

Dieser Abschnitt veranschaulicht den programmgesteuerten Zugriff auf lokalen Speicher mithilfe einer in C# erstellten Texttestdatei `MyLocalStorageTest.txt`.

### <a name="write-a-text-file-to-local-storage"></a>Schreiben einer Textdatei in den lokalen Speicher

Der folgende Code zeigt ein Beispiel für das Schreiben einer Textdatei in den lokalen Speicher. Ersetzen Sie den Platzhalter &lt;NameDesLokalenSpeichers> durch den passenden Wert.

```csharp
// Retrieve an object that points to the local storage resource
LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");

//Define the file name and path
string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
String filePath = Path.Combine(paths);

using (FileStream writeStream = File.Create(filePath))
{
    Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
    writeStream.Write(textToWrite, 0, textToWrite.Length);
}
```

### <a name="find-a-file-written-to-local-storage"></a>Suchen einer in den lokalen Speicher geschriebenen Datei

Um die durch den Code im vorhergehenden Abschnitt erstellte Datei anzuzeigen, führen Sie die folgenden Schritte aus:

1. Klicken Sie im Windows-Infobereich mit der rechten Maustaste auf das Azure-Symbol, und wählen Sie dann im Kontextmenü **Serveremulator-UI anzeigen** aus.

    ![Azure-Serveremulator anzeigen](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Wählen Sie die Webrolle aus:

    ![Azure-Serveremulator](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. Wählen Sie im Menü **Microsoft Azure-Serveremulator****Extras** > **Lokalen Speicher öffnen** aus.

    ![Menüelement „Lokalen Speicher öffnen“](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Wenn das Fenster des Windows Explorer geöffnet wird, geben Sie im Textfeld **Suchen** „MyLocalStorageTest.txt“ ein, und wählen Sie **Eingabe** aus, um die Suche zu starten.

## <a name="next-steps"></a>Nächste Schritte
Unter [Konfigurieren eines Azure-Projekts](vs-azure-tools-configuring-an-azure-project.md)erhalten Sie weitere Informationen zu Azure-Projekten in Visual Studio. Informationen zum Clouddienstschema finden Sie unter [Schemareferenz](/previous-versions/azure/dd179398(v=azure.100)).
