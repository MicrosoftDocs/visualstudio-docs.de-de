---
title: Migrieren und Veröffentlichen einer Webanwendung in einem clouddienst
description: Sie erfahren, wie Sie Ihre Webanwendung mit Visual Studio zu einem Azure-Clouddienst migrieren und veröffentlichen.
ms.custom: SEO-VS-2020
author: ghogen
manager: jillfra
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: eb87aff7bf4ca1e3eac359b27a4280877eaefc50
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399818"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Vorgehensweise: Migrieren und Veröffentlichen einer Webanwendung in einem Azure-clouddienst aus Visual Studio

Um die Vorteile der Hostingdienste und der Skalierbarkeit von Azure zu nutzen, kann es ratsam sein, Ihre Webanwendung zu einem Azure-Clouddienst zu migrieren und dort bereitzustellen. Es sind nur geringfügige Änderungen erforderlich. Dieser Artikel behandelt nur die Bereitstellung in Clouddiensten; Informationen für App Service finden Sie unter [Bereitstellen von Web-Apps in Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Diese Migration wird nur für die jeweiligen ASP.net-, WCF-und WCF-Workflow Projekte unterstützt. Für ASP.NET Core-Projekte wird sie nicht unterstützt. Siehe [Unterstützte Projektvorlagen](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migrieren eines Projekts zu Clouddiensten

1. Klicken Sie mit der rechten Maustaste auf den Projektmappenknoten, und wählen Sie **> neues Projekt hinzufügen...** aus, und fügen Sie der vorhandenen Projekt Mappe ein neues **Azure Cloud Service (klassisches)**
1. Klicken Sie im Dialogfeld **neuer Microsoft Azure clouddienst (klassisch)** auf OK, ohne dem Projektrollen hinzuzufügen.
1. Klicken Sie im neu hinzugefügten Cloud Services Projekt mit der rechten Maustaste auf den Knoten Rollen, und wählen Sie dann **Webrollen Projekt in Projekt Mappe hinzufügen aus**.
1. Wählen Sie im Dialogfeld **mit Rollen Projekt zuordnen** das Projekt aus, das Sie als webrolle zuordnen möchten.

   > [!Important]
   > Wenn Sie über andere Assemblys oder Dateien verfügen, die für diese Webanwendung benötigt werden, müssen Sie die Eigenschaften für diese Dateien manuell festlegen. Informationen zum Festlegen dieser Eigenschaften finden Sie unter [Einschließen von Dateien in das Dienstpaket](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Fehler und Warnungen

Alle auftretenden Warnungen oder Fehler geben Probleme an, die vor der Bereitstellung in Azure zu beheben sind, wie z.B. fehlende Assemblys.

Wenn Sie Ihre Anwendung erstellen, lokal mit dem Serveremulator ausführen oder unter Azure veröffentlichen, wird u.U. der folgende Fehler angezeigt: „Der angegebene Pfad oder Dateiname bzw. beide sind zu lang.“ Dieser Fehler gibt an, dass der vollqualifizierte Azure-Projektname länger als 146 Zeichen ist. Um das Problem zu beheben, verschieben Sie die Projektmappe in einen anderen Ordner mit kürzerem Pfad.

Weitere Informationen dazu, wie Sie alle Warnungen wie Fehler behandeln, finden Sie unter [Konfigurieren eines Azure-Clouddienstprojekts mit Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Lokales Testen der Migration

1. Klicken Sie in Visual Studio im **Projektmappen-Explorer** mit der rechten Maustaste auf das hinzugefügte Clouddienstprojekt, und wählen Sie dann **Als Startprojekt festlegen**.
1. Wählen Sie **Debuggen > Debugging starten** (F5), um die Azure-Debugumgebung zu starten. Diese Umgebung stellt insbesondere die Emulation verschiedener Azure-Dienste bereit.

### <a name="use-an-azure-sql-database-for-your-application"></a>Verwenden einer Azure SQL-Datenbank für die Anwendung

Wenn Sie über eine Verbindungszeichenfolge für Ihre Webanwendung verfügen, die eine lokale SQL Server-Datenbank verwendet, müssen Sie stattdessen Ihre Datenbank zu Azure SQL-Datenbank migrieren und die Verbindungszeichenfolge aktualisieren. Anleitungen für diesen Vorgang finden Sie in den folgenden Themen:

- [Migrieren einer SQL Server-Datenbank zu Azure SQL-Datenbank in der Cloud](/azure/sql-database/sql-database-cloud-migrate)
- [Stellen Sie eine Verbindung mit einer Azure SQL-Datenbank her, und fragen Sie die Datenbank mit .NET (C#) und Visual Studio ab](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Veröffentlichen der Anwendung in Azure Cloud Service

1. Erstellen Sie die erforderlichen Clouddienst- und Speicherkonten im Azure-Abonnement wie in [Vorbereiten der Veröffentlichung und Bereitstellung einer Azure-Anwendung in Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md) beschrieben.
1. Klicken Sie in Visual Studio mit der rechten Maustaste auf das Anwendungsprojekt, und wählen Sie **In Microsoft Azure veröffentlichen...** (anderer Befehl als „Veröffentlichen…“).
1. Melden Sie sich im angezeigten Fenster **Azure-Anwendung veröffentlichen** mit dem Konto Ihres Azure-Abonnements an, und wählen Sie **Weiter >**.
1. Wählen Sie auf der Registerkarte **Einstellungen > Allgemeine Einstellungen** in der Dropdownliste **Clouddienst** den Zielclouddienst zusammen mit der gewünschten Umgebung und den gewünschten Konfigurationen aus.
1. Wählen Sie in **Einstellungen > Erweiterte Einstellungen** das zu verwendende Speicherkonto aus, und wählen Sie dann **Weiter >**.
1. Legen Sie **Diagnose** fest, ob Informationen an Application Insights gesendet werden.
1. Wählen Sie **Weiter >** um eine Zusammenfassung anzuzeigen, und wählen Sie dann **Veröffentlichen** , um die Bereitstellung zu starten.
1. Visual Studio öffnet ein Aktivitätsprotokollfenster, in dem Sie den Fortschritt verfolgen können:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (Optional) Zum Abbrechen des Bereitstellungsprozesses klicken Sie mit der rechten Maustaste auf die Position im Aktivitätsprotokoll und wählen **Abbrechen und entfernen** aus. Mit diesem Befehl wird der Bereitstellungsprozess beendet und die Bereitstellungsumgebung aus Azure gelöscht. Hinweis: Sie müssen das [Azure-Portal](https://portal.azure.com)verwenden, um diese Umgebung nach der Bereitstellung zu entfernen.
1. (Optional) Nach dem Starten Ihrer Rolleninstanzen wird die Bereitstellungsumgebung in Visual Studio im Server-Explorer automatisch unter dem Knoten **Server-Explorer > Cloud Services** angezeigt. Hier können Sie den Status der einzelnen Rolleninstanzen anzeigen.
1. Um nach der Bereitstellung auf Ihre Anwendung zuzugreifen, wählen Sie den Pfeil neben Ihrer Bereitstellung aus, wenn der Status **Abgeschlossen** zusammen mit der URL im **Azure-Aktivitätsprotokoll** angezeigt wird. Die folgende Tabelle enthält die Details zum Starten eines bestimmten Typs von Webanwendung unter Azure.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Verwenden des Serveremulators und Starten der Anwendung in Azure

Alle Anwendungstypen können in einem Browser gestartet werden, der mit dem Visual Studio-Debugger verbunden ist. Wählen Sie dazu **Debuggen > Debuggen starten** (F5). Bei einem Projekt mit leerer ASP.NET-Webanwendung müssen Sie Ihrer Anwendung zunächst eine `.aspx`-Seite hinzufügen und sie als Startseite für Ihr Webprojekt festlegen.

Die folgende Tabelle enthält Details zum Starten der Anwendung in Azure:

| Webanwendungstyp | Ausführen in Azure |
| --- | --- |
| ASP.NET-Webanwendung<br/>(einschließlich MVC 2, MVC 3, MVC 4) | Wählen Sie die URL auf der Registerkarte **Bereitstellung** für das **Azure-Aktivitätsprotokoll**. |
| Leere ASP.NET-Webanwendung | Wenn in Ihrer Anwendung eine `.aspx`-Standardseite vorhanden ist, wählen Sie die URL auf der Registerkarte **Bereitstellung** für das **Azure-Aktivitätsprotokoll**. Um zu einer anderen Seite zu navigieren, geben Sie eine URL im folgenden Format in einen Browser ein: `<deployment_url>/<page_name>.aspx` |
| WCF-Dienstanwendung<br/>Dienstanwendung für WCF-Workflows | Legen Sie die `.svc`-Datei als Startseite für Ihr WCF-Dienstprojekt fest. Navigieren Sie dann zu `<deployment_url>/<service_file>.svc`. |
| ASP.NET Dynamic Entities<br/>ASP.NET Dynamic Data-LINQ to SQL | Aktualisieren Sie die Verbindungszeichenfolge wie im nächsten Abschnitt beschrieben. Navigieren Sie dann zu `<deployment_url>/<page_name>.aspx`. Für Linq to SQL müssen Sie eine Azure SQL-Datenbank verwenden. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Aktualisieren einer Verbindungszeichenfolge für ASP.NET Dynamic Entities

1. Erstellen Sie eine SQL Azure-Datenbank für eine ASP.NET Dynamic Entities-Webanwendung, wie weiter oben in (#use-an-azuresql-database-for-your-application) beschrieben.
1. Fügen Sie über das Azure-Portal die Tabellen und Felder hinzu, die Sie für diese Datenbank benötigen.
1. Geben Sie in der `web.config`-Datei eine Verbindungszeichenfolge im folgenden Format an, und speichern Sie die Datei:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

    Aktualisieren Sie den Wert *connectionString* mit der ADO.NET-Verbindungszeichenfolge wie folgt für Ihre SQL Azure-Datenbank:

    ```xml
    <add name="tempdbEntities"
     connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"
     providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Unterstützte Projektvorlagen

Anwendungen, die migriert und in Clouddiensten veröffentlicht werden können, müssen eine der Vorlagen in der folgenden Tabelle verwenden. ASP.NET Core wird nicht unterstützt.

| Vorlagengruppe | Projektvorlage |
| --- | --- |
| Web | ASP.NET-Webanwendung (.NET Framework) |
| Web | ASP.NET MVC 2-Webanwendung |
| Web | ASP.NET MVC 3-Webanwendung |
| Web | ASP.NET MVC 4-Webanwendung |
| Web | Leere ASP.NET-Webanwendung (oder Website) |
| Web | Leere ASP.NET MVC 2-Webanwendung |
| Web | Webanwendung für ASP.NET Dynamic Data Entities |
| Web | Webanwendung für ASP.NET Dynamic Data-LINQ to SQL |
| WCF | WCF-Dienstanwendung |
| WCF | Dienstanwendung für WCF-Workflows |
| Workflow | Dienstanwendung für WCF-Workflows |

## <a name="next-steps"></a>Nächste Schritte

- [Veröffentlichen und Bereitstellen einer Azure-Anwendung in Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Einrichten benannter Authentifizierungs Anmelde](vs-azure-tools-setting-up-named-authentication-credentials.md)Informationen.
