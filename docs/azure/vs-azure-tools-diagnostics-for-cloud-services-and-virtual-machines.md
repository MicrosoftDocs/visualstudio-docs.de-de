---
title: 'Diagnose: Azure Cloud Services & VMS'
ms.custom: SEO-VS-2020
description: Erfahren Sie mehr über das Einrichten der Diagnose für das Debuggen von Azure-Clouddiensten und virtuellen Azure-Computern (VMs) in Visual Studio.
author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.openlocfilehash: e98d335d53edb7e8771db3314944a11c534d046b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844306"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Einrichten der Diagnose für Azure-Clouddienste und virtuelle Azure-Computer
Wenn Sie Probleme bei einem Azure-Clouddienst oder virtuellen Azure-Computer beheben müssen, können Sie Visual Studio verwenden, um Azure-Diagnose leichter einzurichten. Die Diagnose erfasst Systemdaten und Protokollierungsdaten auf den virtuellen Computern und den virtuellen Computerinstanzen, auf denen der Clouddienst ausgeführt wird. Die Diagnosedaten werden in ein Speicherkonto Ihrer Wahl übertragen. Weitere Informationen zur Diagnoseprotokollierung in Azure finden Sie unter [Aktivieren der Diagnoseprotokollierung für Web-Apps in Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

In diesem Artikel wird erläutert, wie Sie Visual Studio vor und nach der Bereitstellung verwenden können, um Azure-Diagnose zu aktivieren und einzurichten. Erfahren Sie, wie Sie die Diagnose auf virtuellen Azure-Computern einrichten, die Arten der Diagnoseinformationen auswählen, die gesammelt werden sollen, und wie Sie diese Informationen anzeigen, nachdem sie gesammelt wurden.

Sie können eine der folgenden Optionen verwenden, um Azure-Diagnose einzurichten:

* Ändern Sie die Diagnoseeinstellungen im Dialogfeld **Diagnoseeinstellungen** in Visual Studio. Die Einstellungen werden in einer Datei namens „diagnostics.wadcfgx“ („diagnostics.wadcfg“ in Azure SDK 2.4 und früher) gespeichert. Sie können die Konfigurationsdatei ebenfalls direkt ändern. Wenn Sie die Datei manuell aktualisieren, werden die Änderungen bei der nächsten Bereitstellung des Clouddiensts in Azure oder bei der nächsten Ausführung des Diensts im Emulator wirksam.
* Verwenden Sie den Cloud-Explorer oder Server-Explorer in Visual Studio, um die Diagnoseeinstellungen für einen ausgeführten Clouddienst oder virtuellen Computer zu ändern.

## <a name="azure-sdk-26-diagnostics-changes"></a>Diagnoseänderungen bei Azure SDK 2.6
Folgende Änderungen gelten für Projekte in Visual Studio von Azure SDK 2.6 und höher:

* Der lokale Emulator unterstützt jetzt die Diagnose. Dies bedeutet, dass Sie Diagnosedaten sammeln und sicherstellen können, dass Ihre Anwendung die richtigen Ablaufverfolgungen erstellt, während Sie Ihre Entwicklung und Tests in Visual Studio durchführen. Die Verbindungs Zeichenfolge `UseDevelopmentStorage=true` schaltet die Diagnosedaten Sammlung ein, während Sie das clouddienstprojekt in Visual Studio mit dem Azure Storage-Emulator ausführen. Alle Diagnosedaten werden im Speicherkonto des Entwicklungsspeichers gesammelt.
* Die Verbindungszeichenfolge `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` des Diagnosespeicherkontos wird in der Dienstkonfigurationsdatei (CSCFG) gespeichert. In Azure SDK 2.5 wird das Diagnosespeicherkonto in der Datei „diagnostics.wadcfgx“ angegeben.

Die Verbindungszeichenfolge weist in Azure SDK 2.6 und höher einige grundlegende Änderungen in der Funktionsweise im Gegensatz zu Azure SDK 2.4 und früher auf:

* Bis Azure SDK 2.4 wird die Verbindungszeichenfolge vom Diagnose-Plug-In als Runtime verwendet, um Informationen zum Speicherkonto für die Übertragung der Diagnoseprotokolle abzurufen.
* Ab Azure SDK 2.6 wird die Diagnose-Verbindungszeichenfolge von Visual Studio während der Veröffentlichung zum Einrichten der Erweiterung für Azure-Diagnose mit den entsprechenden Speicherkontoinformationen verwendet. Sie können die Verbindungszeichenfolge verwenden, um verschiedenen Speicherkonten für verschiedene Dienstkonfigurationen definieren, die Visual Studio während der Veröffentlichung verwendet. Da das Diagnose-Plug-In nach Azure SDK 2.5 nicht mehr verfügbar ist, kann die CSCFG-Datei allein die Diagnoseerweiterung nicht einrichten. Sie müssen die Erweiterung separat einrichten, indem Sie Tools wie Visual Studio oder PowerShell verwenden.
* Um das Einrichten der Diagnoseerweiterung mithilfe von PowerShell zu vereinfachen, enthält die Paketausgabe von Visual Studio die öffentliche Konfigurations-XML für die Diagnoseerweiterung jeder Rolle. Visual Studio verwendet die Diagnose-Verbindungszeichenfolge zum Ausfüllen der Speicherkontoinformationen in der öffentlichen Konfiguration. Die öffentlichen Konfigurationsdateien werden im Ordner „Erweiterungen“ erstellt. Die öffentlichen Konfigurationsdateien verwenden das Namensmuster PaaSDiagnostics.&lt;Rollenname\>.PubConfig.xml. Dieses Muster kann von allen PowerShell-basierten Bereitstellungen verwendet werden, um die einzelnen Konfigurationen einer Rolle zuzuordnen.
* Das [Azure-Portal](https://portal.azure.com) verwendet die Verbindungszeichenfolge in der CSCFG-Datei, um auf die Diagnosedaten zuzugreifen. Die Daten werden auf der Registerkarte **Überwachung** angezeigt. Die Verbindungs Zeichenfolge ist erforderlich, um den Dienst so festzulegen, dass ausführliche Überwachungsdaten im Portal angezeigt werden.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Migrieren von Projekten zu Azure SDK 2.6 und höher
Wenn beim Migrieren von Azure SDK 2.5 zu Azure SDK 2.6 oder höher in der WADCFGX-Datei ein Diagnosespeicherkonto angegeben ist, dann verbleibt das Speicherkonto in dieser Datei. Um die Flexibilität nutzen zu können, die sich aus der Verwendung verschiedener Speicherkonten für unterschiedliche Speicherkonfigurationen ergibt, fügen Sie Ihrem Projekt die Verbindungszeichenfolge manuell hinzu. Wenn Sie ein Projekt aus Azure SDK 2.4 oder früher zu Azure SDK 2.6 migrieren, werden die Diagnose-Verbindungszeichenfolgen beibehalten. Beachten Sie jedoch die Änderungen im Hinblick auf die Handhabung von Verbindungszeichenfolgen in Azure SDK 2.6, die im vorherigen Abschnitt beschrieben werden.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Bestimmung des Diagnosespeicherkontos durch Visual Studio
* Wenn eine Diagnose-Verbindungszeichenfolge in der CSCFG-Datei angegeben ist, verwendet Visual Studio diese, um die Diagnoseerweiterung während der Veröffentlichung einzurichten und wenn die öffentlichen XML-Konfigurationsdateien während des Verpackens generiert werden.
* Wenn keine Diagnose-Verbindungszeichenfolge in der CSCFG-Datei angegebenen ist, verwendet Visual Studio wieder das Speicherkonto, das in der WADCFGX-Datei angegeben ist, um die Diagnoseerweiterung für das Veröffentlichen einzurichten sowie für das Generieren der öffentlichen XML-Konfigurationsdateien während des Verpackens.
* Die Diagnoseverbindungszeichenfolge in der CSCFG-Datei hat Vorrang vor dem in der WADCFGSX-Datei angegebenen Speicherkonto. Wenn eine Diagnose-Verbindungszeichenfolge in der CSCFG-Datei angegeben ist, verwendet Visual Studio diese und ignoriert das Speicherkonto in der WADCFGX-Datei.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>Wozu dient das Kontrollkästchen „Verbindungszeichenfolgen für Entwicklungsspeicher...“?
Das Kontrollkästchen **Verbindungszeichenfolgen für Entwicklungsspeicher zur Diagnose und zum Zwischenspeichern beim Veröffentlichen in Microsoft Azure mit Anmeldeinformationen für Microsoft Azure-Speicherkonto aktualisieren** ist eine bequeme Möglichkeit, um alle Verbindungszeichenfolgen für ein Entwicklungsspeicherkonto mit dem Azure-Speicherkonto zu aktualisieren, das während der Veröffentlichung angegeben wird.

Wenn Sie dieses Kontrollkästchen aktivieren und die Diagnose-Verbindungszeichenfolge beispielsweise `UseDevelopmentStorage=true` angibt, aktualisiert Visual Studio die Diagnose-Verbindungszeichenfolge automatisch mit dem Speicherkonto, das Sie im Veröffentlichungs-Assistenten angegeben haben, wenn Sie das Projekt in Azure veröffentlichen. Wenn jedoch ein echtes Speicherkonto als Diagnose-Verbindungszeichenfolge angegeben wurde, wird stattdessen dieses Konto verwendet.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Unterschiede bei der Diagnosefunktion in Azure SDK 2,4 und früher im Vergleich zu Azure SDK 2,5 und höher
Wenn Sie für Ihr Projekt ein Upgrade von Azure SDK 2.4 und früher auf Azure SDK 2.5 oder höher durchführen, sollten Sie die folgenden Unterschiede der Diagnosefunktionen beachten:

* **Konfigurations-APIs sind veraltet**. In Azure SDK 2.4 und früher ist eine programmgesteuerte Konfiguration der Diagnose verfügbar; diese Funktion ist jedoch in Azure SDK 2.5 und höher veraltet. Wenn die Diagnosekonfiguration derzeit im Code definiert ist, müssen Sie diese Einstellungen im migrierten Projekt von Grund auf neu konfigurieren, damit die Diagnose weiterhin funktioniert. Die Konfigurationsdatei für die Diagnose für Azure SDK 2.4 ist „diagnostics.wadcfg“. Die Konfigurationsdatei für die Diagnose für Azure SDK 2.5 und höher ist „diagnostics.wadcfgx“.
* **Die Diagnose für Clouddienstanwendungen kann nur auf Rollenebene konfiguriert werden**. In Azure SDK 2.5 und höher können Sie keine Diagnose für Clouddienstanwendungen auf Instanzebene einrichten.
* **Immer, wenn Sie Ihre App bereitstellen, wird die Diagnosekonfiguration aktualisiert**. Dies kann Paritätsprobleme verursachen, wenn Sie die Diagnosekonfiguration im Server-Explorer von Visual Studio ändern und anschließend die App erneut bereitstellen.
* **In Azure SDK 2.5 und höher werden Absturzabbilder in der Diagnosekonfigurationsdatei statt im Code konfiguriert**. Wenn Sie Absturzabbilder im Code konfiguriert haben, müssen Sie die Konfiguration manuell vom Code in die Konfigurationsdatei übertragen. Absturzabbilder werden nicht während der Migration zu Azure SDK 2.6 übertragen.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Aktivieren der Diagnose in Clouddienstprojekten vor der Bereitstellung
In Visual Studio können Sie Diagnosedaten für Rollen sammeln, die in Azure ausgeführt werden, wenn Sie den Dienst vor der Bereitstellung im Emulator ausführen. Alle Änderungen an den Diagnoseeinstellungen in Visual Studio werden in der Konfigurationsdatei "diagnostics.wadcfgx" gespeichert. Diese Einstellungen geben das Speicherkonto an, in dem die Diagnosedaten bei der Bereitstellung des Clouddiensts gespeichert werden.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Aktivieren der Diagnose in Visual Studio vor der Bereitstellung

1. Wählen Sie **Eigenschaften** im Kontextmenü für die Rolle aus. Klicken Sie im Dialogfeld **Eigenschaften** der Rolle auf die Registerkarte **Konfiguration**.
2. Im Abschnitt **Diagnose** muss das Kontrollkästchen **Diagnose aktivieren** aktiviert sein.

    ![Zugreifen auf die Option „Diagnose aktivieren“](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten (…), um das Speicherkonto für die Diagnosedaten anzugeben.

    ![Angeben des zu verwendenden Speicherkontos](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. Geben Sie im Dialogfeld **Verbindungs Zeichenfolge für den Speicher erstellen** an, ob Sie eine Verbindung mit dem Azure Storage-Emulator, einem Azure-Abonnement oder manuell eingegebenen Anmelde Informationen herstellen möchten.

    ![Dialogfeld "Speicherkonto"](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)

   * Wenn Sie **Microsoft Azure-Speicheremulator** auswählen, wird die Verbindungs Zeichenfolge auf festgelegt `UseDevelopmentStorage=true` .
   * Wenn Sie **Ihr Abonnement** auswählen, können Sie das Azure-Abonnement auswählen, das Sie verwenden möchten, und einen Kontonamen angeben. Klicken Sie auf **Konten verwalten**, um Ihre Azure-Abonnements zu verwalten.
   * Wenn Sie **Manuell eingegebene Anmeldeinformationen** auswählen, geben Sie den Namen und den Schlüssel des Azure-Kontos ein, das Sie verwenden möchten.
5. Klicken Sie auf **Konfigurieren**, um das Dialogfeld **Diagnosekonfiguration** anzuzeigen. Jede Registerkarte (mit Ausnahme von **Allgemein** und **Protokollverzeichnisse**) stellt eine Diagnosedatenquelle dar, die Sie sammeln können. Die Standardregisterkarte **Allgemein** enthält die folgenden Optionen für die Diagnosedatensammlung: **Nur Fehler**, **Alle Informationen** und **Benutzerdefinierter Plan**. Die Standardoption **Nur Fehler** verwendet am wenigsten Speicherplatz, da keine Warnungen oder Ablaufverfolgungsmeldungen übertragen werden. Die Option **Alle Informationen** überträgt die meisten Informationen, verwendet den meisten Speicher und ist daher die teuerste Option.

   > [!NOTE]
   > Die unterstützte Mindestgröße für "Datenträger Kontingent in MB" beträgt 50 MB, und die Standardgröße beträgt 4 GB. Wenn Sie jedoch Speicherabbilder sammeln, sollte das Datenträgerkontingent auf einen höheren Wert, z.B. 10 GB, heraufgestuft werden.
   >

    ![Aktivieren der Azure-Diagnose und Konfiguration](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. Wählen Sie für dieses Beispiel die Option **Benutzerdefinierter Plan**, um die gesammelten Daten anzupassen.
7. Über das Feld **Datenträgerkontingent in MB** können Sie festlegen, wie viel Speicherplatz Ihrem Speicherkonto für Diagnosedaten zugeordnet werden soll. Sie können die Standardwerte akzeptieren oder ändern.
8. Aktivieren Sie auf jeder Registerkarte der Diagnosedaten, die Sie erfassen möchten, das Kontrollkästchen **Übertragung \<log type\> aktivieren** . Aktivieren Sie beispielsweise das Kontrollkästchen **Übertragung von Anwendungsprotokollen aktivieren** auf der Registerkarte **Anwendungsprotokolle**, wenn Sie Anwendungsprotokolle sammeln möchten. Geben Sie auch alle andere Informationen an, die für die einzelnen Diagnosedatentypen erforderlich sind. Weitere Informationen zur Konfiguration der einzelnen Registerkarten finden Sie nachfolgend im Abschnitt **Set up diagnostics data sources (Einrichten der Diagnosedatenquellen)** dieses Artikels.
9. Nachdem Sie die Sammlung aller gewünschten Diagnosedaten aktiviert haben, klicken Sie auf **OK**.
10. Führen Sie das Azure-Clouddienstprojekt wie gewohnt in Visual Studio aus. Beim Verwenden der Anwendung werden die Protokollinformationen, die Sie aktiviert haben, im angegebenen Azure-Speicherkonto gespeichert.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Aktivieren der Diagnose für virtuelle Azure-Computer
In Visual Studio können Diagnosedaten für virtuelle Azure-Computer gesammelt werden.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Aktivieren der Diagnose für virtuelle Azure-Computer

1. Wählen Sie im Server-Explorer den Azure-Knoten aus, und stellen Sie dann eine Verbindung mit Ihrem Azure-Abonnement her, wenn noch keine Verbindung besteht.
2. Erweitern Sie den Knoten **Virtuelle Computer**. Sie können einen neuen virtuellen Computer erstellen oder einen vorhandenen Knoten auswählen.
3. Klicken Sie im Kontextmenü für den gewünschten virtuellen Computer auf **Konfigurieren**. Das Dialogfeld „Konfiguration des virtuellen Computers“ wird angezeigt.

    ![Konfigurieren eines virtuellen Azure-Computers](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Fügen Sie die Erweiterung "Microsoft Monitoring Agent-Diagnose" hinzu, wenn sie noch nicht installiert wurde. Mit dieser Erweiterung können Sie Diagnosedaten für virtuelle Azure-Computer sammeln. Wählen Sie im Dropdown-Listenfeld **Verfügbare Erweiterung auswählen** unter **Installierte Erweiterungen****Microsoft Monitoring Agent Diagnostics** (Microsoft Monitoring Agent-Diagnose) aus.

    ![Installieren einer Erweiterung für virtuelle Azure-Computer](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > Für Ihre virtuellen Computer sind noch andere Diagnoseerweiterungen verfügbar. Weitere Informationen finden Sie unter [Erweiterungen und Features für virtuelle Computer für Windows](/azure/virtual-machines/windows/extensions-features).
   >
   >
5. Klicken Sie auf **Hinzufügen**, um die Erweiterung hinzuzufügen und das entsprechende Dialogfeld **Diagnosekonfiguration** anzuzeigen.
6. Klicken Sie auf **Konfigurieren** und dann auf **OK**, um ein Speicherkonto anzugeben.

    Jede Registerkarte (mit Ausnahme von **Allgemein** und **Protokollverzeichnisse**) stellt eine Diagnosedatenquelle dar, die Sie sammeln können.

    ![Aktivieren der Azure-Diagnose und Konfiguration](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    Die Standardregisterkarte **Allgemein** enthält die folgenden Optionen für die Diagnosedatensammlung: **Nur Fehler**, **Alle Informationen** und **Benutzerdefinierter Plan**. Die Standardoption **Nur Fehler** belegt den geringsten Speicherplatz, weil sie Warnungen oder Ablaufverfolgungsmeldungen nicht überträgt. Die Option **Alle Informationen** überträgt die meisten Informationen und ist daher, bezogen auf den Speicher, die teuerste Option.
7. Wählen Sie für dieses Beispiel die Option **Benutzerdefinierter Plan** aus, damit Sie die erfassten Daten anpassen können.
8. Das Feld **Datenträgerkontingent in MB** gibt an, wie viel Speicherplatz Sie in Ihrem Speicherkonto für die Diagnosedaten zuweisen möchten. Sie können den Standardwert bei Bedarf ändern.
9. Wählen Sie auf jeder Registerkarte für Diagnosedaten, die Sie erfassen möchten, das Kontrollkästchen **Übertragung von \<log type\> aktivieren** aus.

    Wenn Sie z. b. Anwendungsprotokolle erfassen möchten, aktivieren Sie das Kontrollkästchen **Übertragung von Anwendungs Protokollen aktivieren** auf der Registerkarte **Anwendungsprotokolle** . Geben Sie außerdem alle anderen Informationen an, die für die einzelnen Diagnose Datentypen erforderlich sind. Weitere Informationen zur Konfiguration der einzelnen Registerkarten finden Sie nachfolgend im Abschnitt **Set up diagnostics data sources (Einrichten der Diagnosedatenquellen)** dieses Artikels.
10. Nachdem Sie die Sammlung aller gewünschten Diagnosedaten aktiviert haben, klicken Sie auf **OK**.
11. Speichern Sie das aktualisierte Projekt.

    Eine Meldung im Fenster **Microsoft Azure-Aktivitätsprotokoll** gibt an, dass der virtuelle Computer aktualisiert wurde.

## <a name="set-up-diagnostics-data-sources"></a>Einrichten von Diagnosedatenquellen
Nachdem Sie die Sammlung von Diagnosedaten aktiviert haben, können Sie genau auswählen, welche Datenquellen Sie sammeln möchten und welche Informationen gesammelt werden. In den folgenden Abschnitten erfolgt eine Beschreibung der Registerkarten im Dialogfeld **Diagnosekonfiguration** sowie der einzelnen Konfigurationsoptionen.

### <a name="application-logs"></a>Anwendungsprotokolle
Anwendungsprotokolle enthalten Diagnoseinformationen, die von einer Webanwendung erstellt wurden. Wenn Sie die Anwendungsprotokolle aufzeichnen möchten, aktivieren Sie das Kontrollkästchen **Übertragung von Anwendungsprotokollen aktivieren**. Ändern Sie den Wert **Übertragungszeitraum (Min.)**, um das Intervall zwischen der Übertragung von Anwendungsprotokollen an Ihr Speicherkonto zu erhöhen oder zu verringern. Sie können auch die Menge an Informationen ändern, die im Protokoll erfasst werden, indem Sie den Wert **Protokollebene** festlegen. Sie können z.B. **Ausführlich** auswählen, um weitere Informationen zu erhalten, oder **Kritisch**, um nur kritische Fehler zu erfassen. Wenn Sie einen bestimmten Diagnoseanbieter haben, der Anwendungsprotokolle ausgibt, können Sie diese erfassen, indem Sie die Anbieter-GUID in das Feld **Anbieter-GUID** einfügen.

  ![Anwendungsprotokolle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Weitere Informationen zu Anwendungsprotokollen finden Sie unter [Aktivieren der Diagnoseprotokollierung für Web-Apps in Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Windows-Ereignisprotokolle
Aktivieren Sie das Kontrollkästchen **Übertragung von Windows-Ereignisprotokollen aktivieren**, um Windows-Ereignisprotokolle zu erfassen. Ändern Sie den Wert **Übertragungszeitraum (Min.)**, um das Intervall zwischen der Übertragung von Ereignisprotokollen an Ihr Speicherkonto zu erhöhen oder zu verringern. Wählen Sie die Kontrollkästchen für die Ereignistypen aus, die Sie nachverfolgen möchten.

![Ereignisprotokolle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Wenn Sie Azure SDK 2,6 oder höher verwenden und eine benutzerdefinierte Datenquelle angeben möchten, geben Sie Sie in das **\<Data source name\>** Textfeld ein, und wählen Sie dann **Hinzufügen** aus. Die Datenquelle wird der Datei "diagnostics.cfcfg" hinzugefügt.

Wenn Sie Azure SDK 2.5 verwenden und eine benutzerdefinierte Datenquelle angeben möchten, können Sie diese wie im folgenden Beispiel dargestellt dem Abschnitt `WindowsEventLog` der Datei „diagnostics.wadcfgx“ hinzufügen:

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```

### <a name="performance-counters"></a>Leistungsindikatoren
Anhand von Leistungsindikatorinformationen können Sie nach Engpässen im System suchen und die System- und Anwendungsleistung optimieren. Weitere Informationen finden Sie unter [Erstellen und Verwenden von Leistungsindikatoren in einer Azure-Anwendung](/azure/cloud-services/diagnostics-performance-counters). Aktivieren Sie das Kontrollkästchen **Übertragung der Leistungsindikatoren aktivieren**, um Leistungsindikatoren zu erfassen. Ändern Sie den Wert **Übertragungszeitraum (Min.)**, um das Intervall zwischen der Übertragung von Ereignisprotokollen an Ihr Speicherkonto zu erhöhen oder zu verringern. Wählen Sie die Kontrollkästchen für die Leistungsindikatoren aus, die Sie nachverfolgen möchten.

![Leistungsindikatoren](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Für das Hinzufügen eines Leistungsindikators, der nicht aufgelistet ist, geben Sie diesen mit der vorgeschlagenen Syntax ein, und klicken Sie dann auf **Hinzufügen**. Das Betriebssystem auf dem virtuellen Computer bestimmt, welche Leistungsindikatoren Sie nachverfolgen können. Weitere Informationen zur Syntax finden Sie unter [Angeben eines Counter-Pfads](/windows/win32/perfctrs/specifying-a-counter-path).

### <a name="infrastructure-logs"></a>Infrastrukturprotokolle
Infrastrukturprotokolle enthalten Informationen über die Azure-Diagnoseinfrastruktur, das RemoteAccess-Modul und das RemoteForwarder-Modul. Aktivieren Sie das Kontrollkästchen **Übertragung von Infrastrukturprotokollen aktivieren**, um Informationen über Infrastrukturprotokolle zu sammeln. Ändern Sie den Wert **Übertragungszeitraum (Min.)**, um das Intervall zwischen der Übertragung von Infrastrukturprotokollen an Ihr Speicherkonto zu erhöhen oder zu verringern.

![Diagnoseinfrastrukturprotokolle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Weitere Informationen finden Sie unter [Sammeln von Protokollierungsdaten mit der Azure-Diagnose](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="log-directories"></a>Protokollverzeichnisse
Protokollverzeichnisse enthalten Daten, die aus IIS-Anforderungen (Internetinformationsdienste), fehlerhaften Anforderungen oder von Ihnen ausgewählten Ordnern gesammelt wurden. Aktivieren Sie das Kontrollkästchen **Übertragung von Protokollverzeichnissen aktivieren**, um Protokollverzeichnisse zu erfassen. Ändern Sie den Wert **Übertragungszeitraum (Min.)**, um das Intervall zwischen der Übertragung von Protokollen an Ihr Speicherkonto zu erhöhen oder zu verringern.

Sie können die Kontrollkästchen der Protokolle aktivieren, die Sie sammeln möchten, z.B. **IIS-Protokolle** und **Protokolle zu fehlerhaften Anforderungen**. Es werden standardmäßig Speichercontainernamen angegeben, Sie können die Namen jedoch ändern.

Sie können Protokolle aus einem beliebigen Ordner erfassen. Geben Sie den Pfad im Abschnitt **Protokoll aus absolutem Verzeichnis** an, und klicken Sie dann auf **Verzeichnis hinzufügen**. Die Protokolle werden in den angegebenen Containern erfasst.

![Protokollverzeichnisse](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>ETW-Protokolle
Wenn Sie [Ereignisablaufverfolgung für Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) verwenden und ETW-Protokolle erfassen möchten, aktivieren Sie das Kontrollkästchen **Übertragung von ETW-Protokollen aktivieren**. Ändern Sie den Wert **Übertragungszeitraum (Min.)**, um das Intervall zwischen der Übertragung von Protokollen an Ihr Speicherkonto zu erhöhen oder zu verringern.

Die Ereignisse werden von den Ereignisquellen und Ereignismanifesten erfasst, die Sie angeben. Geben Sie im Abschnitt **Ereignisquelle** einen Namen ein, und klicken Sie dann auf **Ereignisquelle hinzufügen**, um eine Ereignisquelle festzulegen. Gleichermaßen können Sie ein Ereignismanifest im Abschnitt **Ereignismanifeste** angeben und dann auf **Ereignismanifest hinzufügen** klicken.

![ETW-Protokolle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

Das ETW-Framework wird in ASP.NET durch Klassen im Namespace [System.Diagnostics.aspx](/dotnet/api/system.diagnostics) unterstützt. Der Microsoft.WindowsAzure.Diagnostics-Namespace, der von [System.Diagnostics.aspx](/dotnet/api/system.diagnostics)-Standardklassen erbt und diese erweitert, ermöglicht die Verwendung von [System.Diagnostics.aspx](/dotnet/api/system.diagnostics) als Protokollierungsframework in der Azure-Umgebung. Weitere Informationen finden Sie unter [Protokollierung und Ablaufverfolgung in Microsoft Azure](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) und [Aktivieren der Diagnose in Azure Cloud Services und Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Absturzabbilder
Aktivieren Sie das Kontrollkästchen **Übertragung von Absturzabbildern aktivieren**, um Informationen zum Absturz einer Rolleninstanz zu erfassen. (Da ASP.net die meisten Ausnahmen behandelt, ist dies im Allgemeinen nur für workerrollen nützlich.) Um den Prozentsatz des Speicherplatzes zu erhöhen oder zu verringern, der für die Absturz Abbilder reserviert ist, ändern Sie den Wert für das **Verzeichnis Kontingent (%)** . Sie können den Speichercontainer ändern, in dem die Absturzabbilder gespeichert werden, und Sie können angeben, ob Sie ein **vollständiges Abbild** oder ein **Miniabbild** erfassen möchten.

Die derzeit nachverfolgten Prozesse werden im folgenden Screenshot aufgelistet. Wählen Sie die Kontrollkästchen für die Prozesse aus, die Sie erfassen möchten. Geben Sie den Namen des Prozesses ein, und klicken Sie dann auf **Prozess hinzufügen**, um einen weiteren Prozess der Liste hinzuzufügen.

![Absturzabbilder](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Weitere Informationen finden Sie unter [Protokollierung und Ablaufverfolgung in Microsoft Azure](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) und [Microsoft Azure Diagnostics Part 4: Custom Logging Components and Azure Diagnostics 1.3 Changes (Microsoft Azure-Diagnose Teil 4: benutzerdefinierte Protokollierungskomponenten und Änderungen an Azure-Diagnose 1.3)](https://www.red-gate.com/simple-talk/cloud/platform-as-a-service/microsoft-azure-diagnostics-part-4-custom-logging-components-and-azure-diagnostics-1.3-changes/).

## <a name="view-the-diagnostics-data"></a>Anzeigen von Diagnosedaten
Nachdem Sie die Diagnosedaten für einen Clouddienst oder einen virtuellen Computer gesammelt haben, können Sie diese anzeigen.

### <a name="to-view-cloud-service-diagnostics-data"></a>So zeigen Sie die Clouddienst-Diagnoseinformationen an
1. Stellen Sie Ihren Clouddienst wie gewohnt bereit, und führen Sie ihn dann aus.
2. Sie können die Diagnosedaten in einem Bericht, der von Visual Studio generiert wird, oder in Tabellen in Ihrem Speicherkonto anzeigen. Öffnen Sie zum Anzeigen der Daten in einem Bericht den Cloud-Explorer oder Server-Explorer, rufen Sie das Kontextmenü des Knotens für die gewünschte Rolle auf, und klicken Sie dann auf **Diagnosedaten anzeigen**.

    ![Anzeigen von Diagnosedaten](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    Es wird ein Bericht mit den verfügbaren Daten angezeigt.

    ![Microsoft Azure-Diagnosebericht in Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    Wenn die neuesten Daten nicht angezeigt werden, sollten Sie warten, bis der Übertragungszeitraum abgelaufen ist.

    Klicken Sie auf den Link **Aktualisieren**, um die Daten sofort zu aktualisieren. Wählen Sie im Dropdown-Listenfeld **Automatische Aktualisierung** ein Intervall aus, um die Daten automatisch zu aktualisieren. Klicken Sie zum Exportieren der Fehlerdaten auf die Schaltfläche **In CSV-Datei exportieren**, um eine CSV-Datei zu erstellen, die Sie in einem Excel-Arbeitsblatt öffnen können.

    Öffnen Sie im Cloud-Explorer oder Server-Explorer das Speicherkonto, das der Bereitstellung zugeordnet ist.
3. Öffnen Sie die Diagnosetabellen im Tabellenviewer, und überprüfen Sie die erfassten Daten. Für IIS-Protokolle und benutzerdefinierte Protokolle können Sie einen Blobcontainer öffnen. Die folgende Tabelle listet die Tabellen oder Blobcontainer auf, die die Daten für die verschiedenen Protokolldateien enthalten. Zusätzlich zu den Daten für diese Protokolldatei enthalten die Tabelleneinträge **EventTickCount**, **DeploymentId**, **Role** und **RoleInstance**, mit denen Sie identifizieren können, welcher virtuelle Computer und welche Rolle die Daten generiert hat und wann.

   | Diagnosedaten | BESCHREIBUNG | Standort |
   | --- | --- | --- |
   | Anwendungsprotokolle |Protokolle, die Ihr Code durch Aufrufen von Methoden der **System. Diagnostics. Trace** -Klasse generiert. |WADLogsTable |
   | Ereignisprotokolle |Daten aus den Windows-Ereignisprotokollen auf den virtuellen Computern Windows speichert Informationen in diesen Protokollen, aber Anwendungen und Dienste verwenden diese ebenfalls, um Fehler zu melden oder Informationen zu protokollieren. |WADWindowsEventLogsTable |
   | Leistungsindikatoren |Sie können Daten zu jedem Leistungsindikator erfassen, der auf dem virtuellen Computer verfügbar ist. Das Betriebssystem bietet Leistungsindikatoren, darunter viele Statistiken, wie z.B. Speichernutzung und Prozessorzeit. |WADPerformanceCountersTable |
   | Infrastrukturprotokolle |Protokolle, die von der Diagnoseinfrastruktur selbst generiert werden |WADDiagnosticInfrastructureLogsTable |
   | IIS-Protokolle |Protokolle, die Webanforderungen aufzeichnen Wenn Ihr Clouddienst große Mengen an Datenverkehr abruft, können diese Protokolle sehr lang sein. Deshalb sollten Sie diese Daten nur bei Bedarf sammeln und speichern. |Protokolle mit fehlgeschlagenen Anforderungen finden Sie im Blobcontainer unter „wad-iis-failedreqlogs“ unter einem Pfad für diese Bereitstellung, Rolle und Instanz. Die vollständigen Protokolle finden Sie unter "wad-iis-logfiles". Einträge für jede Datei werden in der WADDirectories-Tabelle vorgenommen. |
   | Absturzabbilder |Umfassen binäre Abbilder des Clouddienstprozesses (in der Regel eine Workerrolle) |wad-crush-dumps-Blobcontainer |
   | Benutzerdefinierte Protokolldateien |Protokolle der Daten, die Sie vordefiniert haben. |Sie können im Code den Speicherort der benutzerdefinierten Protokolldateien in Ihrem Speicherkonto angeben. Sie können beispielsweise einen benutzerdefinierten Blobcontainer angeben. |
4. Wenn Daten eines beliebigen Typs abgeschnitten sind, können Sie versuchen, den Puffer für diesen Datentyp zu vergrößern oder das Intervall zwischen Datenübertragungen vom virtuellen Computer an Ihr Speicherkonto zu verkürzen.
5. (Optional) Löschen Sie gelegentlich Daten aus dem Speicherkonto, um die Gesamtspeicherkosten zu verringern.
6. Bei einer vollständigen Bereitstellung wird die Datei "diagnostics.cscfg" (bzw. die WADCFGX-Datei für Azure SDK 2.5) in Azure aktualisiert, und der Clouddienst erkennt alle Änderungen an Ihrer Diagnosekonfiguration. Wenn Sie stattdessen eine vorhandene Bereitstellung aktualisieren, wird die CSCFG-Datei in Azure nicht aktualisiert. Sie können die Diagnoseeinstellungen jedoch weiterhin ändern, indem Sie den Schritten im nächsten Abschnitt folgen. Weitere Informationen zum Durchführen einer vollständigen Bereitstellung und zum Aktualisieren einer vorhandenen Bereitstellung finden Sie unter [Assistent zur Veröffentlichung einer Azure-Anwendung](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>So zeigen Sie Diagnosedaten für den virtuellen Computer an
1. Klicken Sie im Kontextmenü für den virtuellen Computer auf **Diagnosedaten anzeigen**.

    ![Anzeigen von Diagnosedaten auf einem virtuellen Azure-Computer](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)

    Das Dialogfeld **Diagnosezusammenfassung** wird angezeigt.

    ![Diagnosezusammenfassung von virtuellen Azure-Computern](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)

    Wenn die neuesten Daten nicht angezeigt werden, sollten Sie warten, bis der Übertragungszeitraum abgelaufen ist.

    Klicken Sie auf den Link **Aktualisieren**, um die Daten sofort zu aktualisieren. Wählen Sie im Dropdown-Listenfeld **Automatische Aktualisierung** ein Intervall aus, um die Daten automatisch zu aktualisieren. Klicken Sie zum Exportieren der Fehlerdaten auf die Schaltfläche **In CSV-Datei exportieren**, um eine CSV-Datei zu erstellen, die Sie in einem Excel-Arbeitsblatt öffnen können.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Einrichten der Clouddienstdiagnose nach der Bereitstellung
Wenn Sie ein Problem mit einem Clouddienst untersuchen, der bereits ausgeführt wird, sollten Sie die Daten sammeln, die Sie vor der Bereitstellung der Rolle nicht angegeben haben. In diesem Fall können Sie mit der Sammlung dieser Daten beginnen, indem Sie die Einstellungen im Server-Explorer ändern. Sie können die Diagnose für eine einzelne Instanz oder für alle Instanzen in einer Rolle einrichten, je nachdem, ob Sie das Dialogfeld **Diagnosekonfiguration** über das Kontextmenü für die Instanz oder die Rolle öffnen. Wenn Sie den Rollenknoten konfigurieren, gelten alle von Ihnen vorgenommenen Änderungen für alle Instanzen. Wenn Sie den Instanzknoten konfigurieren, gelten alle von Ihnen vorgenommenen Änderungen nur für diese Instanz.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Einrichten der Diagnose für einen ausgeführten Clouddienst
1. Erweitern Sie im Server-Explorer den Knoten **Clouddienste**, und erweitern Sie dann die Liste der Knoten, um die Rolle oder Instanz (oder beides) anzuzeigen, die Sie untersuchen möchten.

    ![Konfigurieren der Diagnose](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. Klicken Sie im Kontextmenü für einen Instanzknoten oder einen Rollenknoten auf **Diagnoseeinstellungen aktualisieren**, und wählen Sie dann die Diagnoseeinstellungen aus, die Sie sammeln möchten.

    Weitere Informationen zu den Konfigurationseinstellungen finden Sie im Abschnitt **Konfigurieren von Diagnosedatenquellen** dieses Artikels. Weitere Informationen zum Anzeigen von Diagnosedaten finden Sie im Abschnitt **Anzeigen von Diagnosedaten** dieses Artikels.

    Wenn Sie die Datensammlung im Server-Explorer ändern, bleiben diese Änderungen wirksam, bis Sie den Clouddienst vollständig erneut bereitstellen. Wenn Sie die Standardeinstellungen für die Veröffentlichung verwenden, werden die Änderungen nicht überschrieben. Die Standardeinstellung für die Veröffentlichung ist nicht die vollständige erneute Bereitstellung, sondern das Aktualisieren der vorhandenen Bereitstellung. Wechseln Sie zur Registerkarte **Erweiterte Einstellungen** im Veröffentlichungs-Assistenten, und deaktivieren Sie das Kontrollkästchen **Deployment update** (Bereitstellungsupdate), um sicherzustellen, dass die Einstellungen zum Zeitpunkt der Bereitstellung gelöscht werden. Wenn Sie bei deaktiviertem Kontrollkästchen eine erneute Bereitstellung durchführen, werden die Einstellungen wieder auf die der WADCFGX-Datei (oder WADCFG-Datei) zurückgesetzt, die mit dem **Eigenschaften-Editor** für die Rolle festgelegt wurden. Wenn Sie Ihre Bereitstellung aktualisieren, behält Azure die früheren Einstellungen bei.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Problembehandlung für Azure-Clouddienste
Wenn Probleme mit Ihren Clouddienstprojekten auftreten, z.B. eine Rolle, die dauerhaft den Status „Beschäftigt“ hat, wiederholte Neustarts oder die Ausgabe eines internen Serverfehlers, stehen Ihnen Tools und Techniken zur Verfügung, mit denen Sie diese Probleme diagnostizieren und beheben können. Beispiele für häufige Probleme und Lösungen sowie einen Überblick über die Konzepte und Tools, die Sie zum Diagnostizieren und Beheben dieser Fehler verwenden können, finden Sie unter [Azure PaaS compute diagnostics data (Computediagnosedaten in Azure PaaS)](/archive/blogs/kwill/windows-azure-paas-compute-diagnostics-data).

## <a name="q--a"></a>Fragen und Antworten
**Wie groß ist der Puffer, und wie groß sollte er sein?**

Für jede virtuelle Computerinstanz gelten Kontingente, die festlegen, wie viele Diagnosedaten auf dem lokalen Dateisystem gespeichert werden können. Darüber hinaus geben Sie eine Puffergröße für jeden verfügbaren Diagnosedatentyp an. Diese Puffergröße fungiert als individuelles Kontingent für diesen Datentyp. Das Gesamtkontingent und der verbleibende Arbeitsspeicher werden im unteren Bereich des Dialogfelds für den Diagnosedatentyp angezeigt. Wenn Sie größere Puffer oder mehr Datentypen angeben, nähern Sie sich dem Gesamtkontingent. Sie können das Gesamtkontingent ändern, indem Sie die Konfigurationsdatei „diagnostics.wadcfg“ bzw. „diagnostics.wadcfgx“ ändern. Die Diagnosedatei wird im selben Dateisystem wie Ihre Anwendungsdaten gespeichert. Wenn Ihre Anwendung eine große Menge an Speicherplatz verwendet, sollten Sie das Gesamtkontingent für die Diagnose nicht erhöhen.

**Was ist der Übertragungszeitraum, und wie lange sollte er sein?**

Der Übertragungszeitraum ist der Zeitraum zwischen Datenerfassungen. Nach jedem Übertragungszeitraum werden Daten vom lokalen Dateisystem auf einem virtuellen Computer in die Tabellen in Ihrem Speicherkonto verschoben. Wenn die Menge an gesammelten Daten das Kontingent vor dem Ende eines Übertragungszeitraums übersteigt, werden ältere Daten verworfen. Bei Datenverlust sollten Sie den Übertragungszeitraum verkleinern, da Ihre Daten die Puffergröße oder das Gesamtkontingent überschreiten.

**Welche Zeitzone gilt für die Zeitstempel?**

Zeitstempel haben dieselbe Zeitzone wie das lokale Rechenzentrum, in dem der Clouddienst gehostet wird. Die folgenden drei Zeitstempelspalten werden in den Protokolltabellen verwendet:

* **PreciseTimeStamp**: der ETW-Zeitstempel des Ereignisses Das heißt die Zeit, zu der das Ereignis vom Client protokolliert wird.
* **TIMESTAMP**: der auf die Uploadhäufigkeitsgrenze abgerundete Wert für **PreciseTimeStamp** Wenn die Uploadhäufigkeit beispielsweise 5 Minuten beträgt und die Ereigniszeit 00:17:12 ist, lautet TIMESTAMP 00:15:00.
* **Timestamp**: Der Zeitstempel, der angibt, wann die Entität in der Azure-Tabelle erstellt wurde.

**Wie verwalte ich Kosten beim Sammeln von Diagnoseinformationen?**

Die Standardeinstellungen (**Protokollebene**, festgelegt auf **Fehler** und **Übertragungszeitraum**, festgelegt auf **1 Minute**) dienen der Minimierung von Kosten. Ihre Serverkosten steigen, wenn Sie weitere Diagnosedaten sammeln oder den Übertragungszeitraum verkürzen. Sammeln Sie nicht mehr Daten als nötig, und vergessen Sie nicht, die Datensammlung zu deaktivieren, wenn Sie sie nicht mehr benötigen. Sie können diese, wie weiter oben in diesem Artikel beschrieben, jederzeit wieder aktivieren, sogar während der Laufzeit.

**Wie sammle ich Protokolle zu fehlgeschlagenen Anforderungen von IIS?**

Standardmäßig erfasst IIS keine Protokolle zu fehlgeschlagenen Anforderungen. Sie können IIS für das Sammeln von Protokollen für fehlerhafte Anforderungen einrichten, indem Sie die „web.config“-Datei für Ihre Webrolle bearbeiten.

**Ich erhalte keine Nachverfolgungsinformationen von RoleEntryPoint-Methoden wie OnStart. Woran könnte das liegen?**

Die Methoden von **RoleEntryPoint** werden im Kontext von „WAIISHost.exe“ und nicht von IIS aufgerufen. Die Konfigurationsinformationen in der Datei „web.config“, mit denen die Nachverfolgung normalerweise aktiviert wird, gelten nicht. Fügen Sie Ihrem Webrollenprojekt eine CONFIG-Datei hinzu, um dieses Problem zu beheben, und geben Sie der Datei einen Namen, der mit der Ausgabeassembly übereinstimmt, die den **RoleEntryPoint**-Code enthält. Im standardmäßigen Webrollen Projekt sollte der Name der config-Datei WAIISHost.exe.config werden. Fügen Sie dieser Datei die folgenden Zeilen hinzu:

```xml
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

Legen Sie im Fenster **Eigenschaften** die Eigenschaft **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zur Diagnoseprotokollierung in Azure finden Sie unter [Aktivieren der Diagnose in Azure Cloud Services und Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics) und [Aktivieren der Diagnoseprotokollierung für Web-Apps in Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).
