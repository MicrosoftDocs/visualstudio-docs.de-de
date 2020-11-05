---
title: Konfigurieren des clouddiensts mit mehreren Konfigurationen
description: Erfahren Sie, wie Sie ein Azure-Clouddienstprojekt konfigurieren, indem Sie die Dateien „ServiceDefinition.csdef“, „ServiceConfiguration.Local.cscfg“ und „ServiceConfiguration.Cloud.cscfg“ ändern.
ms.custom: SEO-VS-2020
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: a811c30114f9a45119eaccc666d6eb39be80a562
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399805"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>Konfigurieren Ihres Azure-Projekts in Visual Studio zur Verwendung mehrerer Dienstkonfigurationen

Ein Azure-Clouddienstprojekt in Visual Studio enthält drei Konfigurationsdateien: `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg` und `ServiceConfiguration.Cloud.cscfg`:

- `ServiceDefinition.csdef` wird in Azure bereitgestellt, um die Anforderungen des Clouddiensts und seiner Rollen zu beschreiben, und um Einstellungen bereitzustellen, die für alle Instanzen gelten. Einstellungen können zur Laufzeit mit der Azure Service Hosting Runtime-API gelesen werden. Diese Datei kann in Azure nur aktualisiert werden, wenn der Clouddienst beendet wird.
- `ServiceConfiguration.Local.cscfg` und `ServiceConfiguration.Cloud.cscfg` stellen Werte für Einstellungen in der Definitionsdatei bereit und legen die Anzahl der für die einzelnen Rollen auszuführenden Instanzen fest. Die „Local“-Datei enthält Werte, die beim lokalen Debuggen verwendet werden; die „Cloud“-Datei wird in Azure als `ServiceConfiguration.cscfg` bereitgestellt und bietet Einstellungen für die Serverumgebung. Diese Datei kann aktualisiert werden, während Ihr Clouddienst in Azure ausgeführt wird.

Konfigurationseinstellungen werden in Visual Studio mithilfe der Eigenschaftenseiten für die entsprechende Rolle verwaltet und geändert (klicken Sie mit der rechten Maustaste auf die Rolle, und wählen Sie **Eigenschaften** , oder doppelklicken Sie auf die Rolle). Änderungen können auf die in der Dropdownliste **Dienstkonfiguration** ausgewählte Konfiguration beschränkt werden. Die Unterschiede zwischen den ansonsten ähnlichen Eigenschaften für Web- und Workerrollen werden in den folgenden Abschnitten beschrieben.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

Informationen zu den zugrunde liegenden Schemas für die Dienstdefinition und die Dienstkonfigurationsdateien finden Sie in den Artikeln zu [CSDEF (XML-Schema)](/azure/cloud-services/schema-csdef-file) und [CSCFG (XML-Schema)](/azure/cloud-services/schema-cscfg-file). Weitere Informationen zur Dienstkonfiguration finden Sie unter [Gewusst wie: Konfigurieren von Clouddiensten](/azure/cloud-services/cloud-services-how-to-configure-portal).

## <a name="configuration-page"></a>Seite "Konfiguration"

### <a name="service-configuration"></a>Dienstkonfiguration

Legt fest, welche `ServiceConfiguration.*.cscfg`-Datei von Änderungen betroffen ist. Standardmäßig sind lokale Varianten und Cloudvarianten vorhanden, und Sie können den Befehl **... verwalten** verwenden, um Konfigurationsdateien zu kopieren, umzubenennen und zu entfernen. Diese Dateien werden Ihrem Clouddienstprojekt hinzugefügt und im **Projektmappen-Explorer** angezeigt. Das Umbenennen oder Entfernen von Konfigurationen kann jedoch nur über dieses Steuerelement erfolgen.

### <a name="instances"></a>Instanzen

Legen Sie die Eigenschaft **Instanzenanzahl** auf die Anzahl der Instanzen fest, die der Dienst für diese Rolle ausführen soll.

Legen Sie die Eigenschaft **Größe des virtuellen Computers** auf **Sehr klein** , **Klein** , **Mittel** , **Groß** oder **Sehr groß** fest.  Weitere Informationen finden Sie unter [Größen für Cloud Services](/azure/cloud-services/cloud-services-sizes-specs).

### <a name="startup-action-web-role-only"></a>Startaktion (nur Webrolle)

Legen Sie diese Eigenschaft fest, um anzugeben, dass bei Beginn des Debugvorgangs von Visual Studio ein Webbrowser für die HTTP-Endpunkte und/oder für die HTTPS-Endpunkte gestartet werden soll.

Die Option " **https-Endpunkt** " ist nur verfügbar, wenn Sie bereits einen HTTPS-Endpunkt für ihre Rolle definiert haben. Sie können einen HTTPS-Endpunkt auf der Eigenschaftenseite **Endpunkte** definieren.

Wenn Sie bereits einen HTTPS-Endpunkt hinzugefügt haben, ist die Option „HTTPS-Endpunkt“ standardmäßig aktiviert. Visual Studio startet nun beim Start des Debugvorgangs neben dem Browser für den HTTP-Endpunkt einen Browser für diesen Endpunkt, vorausgesetzt dass beide Startoptionen aktiviert sind.

### <a name="diagnostics"></a>Diagnose

Die Diagnosefunktion ist standardmäßig für die Webrolle aktiviert. Das Azure-Clouddienstprojekt und Speicherkonto wurden auf die Verwendung des lokalen Speicheremulators festgelegt. Wenn die Bereitstellung in Azure erfolgen soll, klicken Sie auf die Generatorschaltfläche ( **…** ), um stattdessen Azure-Speicher zu verwenden. Sie können die Diagnosedaten entweder bei Bedarf oder in automatisch geplanten Intervallen an das Speicherkonto übertragen. Weitere Informationen zur Azure-Diagnose erhalten Sie unter [Aktivieren der Diagnose in Azure Cloud Services und Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

## <a name="settings-page"></a>Seite "Einstellungen"

Auf der Seite **Einstellungen** Seite können Sie einer Konfiguration Einstellungen als Name/Wert-Paare hinzufügen. Code, der in der Rolle ausgeführt wird, kann die Werte der Konfigurationseinstellungen zur Laufzeit mithilfe von Klassen lesen, die von der [verwalteten Azure-Bibliothek](/previous-versions/azure/dn602775(v=azure.11))bereitgestellt werden, insbesondere die [getconfigurationsettingvalue](/previous-versions/azure/reference/ee772857(v=azure.100)) -Methode.

### <a name="configuring-a-connection-string-for-a-storage-account"></a>Konfigurieren einer Verbindungszeichenfolge für ein Speicherkonto

Eine Verbindungszeichenfolge ist eine Einstellung, die Verbindungs- und Authentifizierungsinformationen für den Speicheremulator oder für ein Azure-Speicherkonto enthält. Wenn Code in einer Rolle auf Azure-Speicher (Blobs, Warteschlangen oder Tabellen) zugreift, benötigt er eine Verbindungszeichenfolge.

> [!Note]
> Verbindungszeichenfolgen für Azure-Speicherkonten müssen ein definiertes Format aufweisen (siehe [Konfigurieren von Azure Storage-Verbindungszeichenfolgen](/azure/storage/common/storage-configure-connection-string)).

Sie können festlegen, dass die Verbindungszeichenfolge nach Bedarf lokalen Speicher verwendet, und sie dann auf ein Azure-Speicherkonto festlegen, wenn Sie die Anwendung im Clouddienst bereitstellen. Wenn die Verbindungszeichenfolge nicht ordnungsgemäß festgelegt wird, wird die Rolle möglicherweise nicht gestartet, oder die Zustände „Initialisieren“, „Ausgelastet“ und „Beenden“ werden nicht durchlaufen.

Zum Erstellen einer Verbindungszeichenfolge wählen Sie **Einstellung hinzufügen** aus und legen den **Typ** auf „Verbindungszeichenfolge“ fest.

Wählen Sie für neue oder vorhandene Verbindungs Zeichenfolgen **...** _ rechts neben dem Feld _ *Wert* *, um das Dialogfeld **Verbindungs Zeichenfolge für den Speicher erstellen** zu öffnen:

1. Wählen Sie unter **Verbindung herstellen über** die Option **Ihr Abonnement** aus, um ein Speicherkonto aus einem Abonnement auszuwählen. Visual Studio ruft dann die Anmeldeinformationen des Speicherkontos automatisch aus der `.publishsettings`-Datei ab.
1. Mit der Option **Manuell eingegebene Anmeldeinformationen** können Sie den Kontonamen und -schlüssel mithilfe von Informationen aus dem Azure-Portal direkt angeben. Kopieren des Kontoschlüssels:
    1. Navigieren Sie im Azure-Portal zum Speicherkonto, und wählen Sie **Schlüssel verwalten**.
    1. Um den Kontoschlüssel zu kopieren, navigieren Sie im Azure-Portal zu dem Speicherkonto, wählen **Einstellungen > Zugriffsschlüssel** aus und verwenden die Schaltfläche „Kopieren“, um den primären Zugriffsschlüssel in die Zwischenablage zu kopieren.
1. Wählen Sie eine der Verbindungsoptionen aus. Bei **Benutzerdefinierte Endpunkte angeben** werden Sie aufgefordert, bestimmte URLs für Blobs, Tabellen und Warteschlangen anzugeben. Benutzerdefinierte Endpunkte ermöglichen Ihnen die Verwendung [benutzerdefinierter Domänen](/azure/storage/blobs/storage-custom-domain-name) und eine genauere Steuerung des Zugriffs. Weitere Informationen finden Sie unter [Konfigurieren von Azure Storage-Verbindungszeichenfolgen](/azure/storage/common/storage-configure-connection-string).
1. Wählen Sie **OK** und dann **Datei > Speichern** , um die Konfiguration mit der neuen Verbindungszeichenfolge zu aktualisieren.

Wenn Sie Ihre Anwendung in Azure veröffentlichen, wählen Sie wieder die Dienstkonfiguration, die das Azure-Speicherkonto für die Verbindungszeichenfolge enthält. Nachdem die Anwendung veröffentlicht wurde, überprüfen Sie, dass die Anwendung mit den Azure-Speicherdiensten wie erwartet funktioniert.

Weitere Informationen zum Aktualisieren von Dienstkonfigurationen finden Sie im Abschnitt [Verwalten von Verbindungszeichenfolgen für Speicherkonten](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts).

## <a name="endpoints-page"></a>Seite "Endpunkte"

Eine Webrolle weist normalerweise einen einzelnen HTTP-Endpunkt an Port 80 auf. Eine Workerrolle kann dagegen eine beliebige Anzahl von HTTP-, HTTPS- oder TCP-Endpunkten aufweisen. Endpunkte können für externe Clients verfügbare Eingabeendpunkte oder interne Endpunkte sein, die für andere im Dienst ausgeführte Rollen verfügbar sind.

- Ändern Sie den Endpunkttyp in einen Eingabeendpunkt, und geben Sie einen Namen und die Nummer eines öffentlichen Ports an, um einen HTTP-Endpunkt für externe Clients und Webbrowser verfügbar zu machen.
- Ändern Sie den Endpunkttyp in einen **Eingabeendpunkt** , und geben Sie einen Namen, die Nummer eines öffentlichen Ports und den Namen eines Verwaltungszertifikats an, um einen HTTPS-Endpunkt für externe Clients und Webbrowser verfügbar zu machen. Sie müssen auch das Zertifikat auf der Eigenschaftenseite **Zertifikate** definieren, bevor Sie ein Verwaltungszertifikat angeben können.
- Ändern Sie den Endpunkttyp in einen internen Endpunkt, und geben Sie einen Namen und mögliche private Ports für den Endpunkt an, um einen Endpunkt für den internen Zugriff durch andere Rollen innerhalb des Clouddiensts verfügbar zu machen.

## <a name="local-storage-page"></a>Seite "Lokaler Speicher"

Sie können die Eigenschaftenseite **Lokaler Speicher** verwenden, um mindestens eine lokale Speicherressource für eine Rolle zu reservieren. Eine lokale Speicherressource ist ein reserviertes Verzeichnis im Dateisystem des virtuellen Azure-Computers, in dem eine Instanz einer Rolle ausgeführt wird.

## <a name="certificates-page"></a>Seite "Zertifikate"

Auf der Eigenschaftenseite **Zertifikate** werden der Dienstkonfiguration Informationen zu den Zertifikaten hinzugefügt. Die Zertifikate sind im Dienstpaket nicht enthalten, sondern müssen über das [Azure-Portal](https://portal.azure.com) gesondert in Azure hochgeladen werden.

Durch das Hinzufügen eines Zertifikats hier werden der Dienstkonfiguration Informationen zu den Zertifikaten hinzugefügt. Zertifikate sind nicht im Dienst enthalten. Sie müssen Ihre Zertifikate separat über das Azure-Portal hochladen.

Um der Rolle ein Zertifikat zuzuordnen, geben Sie einen Namen für das Zertifikat an. Mit diesem Namen wird beim Konfigurieren eines HTTPS-Endpunkts auf der Seite **Endpunkte** auf das Zertifikat verwiesen. Geben Sie im nächsten Schritt an, ob der Zertifikatspeicher **Lokaler Computer** oder **Aktueller Benutzer** ist. Geben Sie außerdem den Namen des Speichers an. Geben Sie zuletzt den Fingerabdruck des Zertifikats ein. Wenn sich das Zertifikat im Speicher "Current User\Personal (My)" befindet, können Sie den Fingerabdruck des Zertifikats eingeben, indem Sie das Zertifikat aus einer aufgefüllten Liste auswählen. Wenn es sich an einem beliebigen anderen Ort befindet, geben Sie den Fingerabdruckwert manuell ein.

Wenn Sie ein Zertifikat aus dem Zertifikatspeicher hinzufügen, werden den Konfigurationseinstellungen automatisch alle Zwischenzertifikate hinzugefügt. Außerdem müssen diese Zwischenzertifikate in Azure hochgeladen werden, um den Dienst ordnungsgemäß für SSL zu konfigurieren.

Alle dem Dienst zugeordneten Verwaltungszertifikate sind nur dann für den Dienst gültig, wenn er in der Cloud ausgeführt wird. Wenn der Dienst in der lokalen Entwicklungsumgebung ausgeführt wird, wird ein vom Serveremulator verwaltetes Standardzertifikat verwendet.
