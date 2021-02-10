---
title: Remotedebuggen von ASP.NET auf einem Computer mit IIS
description: Erfahren Sie, wie Sie eine Visual Studio-App für ASP.NET MVC 4.5.2 einrichten, konfigurieren, in den IIS bereitstellen und diese über Visual Studio an den Remotedebugger anfügen.
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 854d3e23252e63d6330abd9f1704890d3b90ae36
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908302"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS
Zum Debuggen einer ASP.NET-Anwendung, die in den Internetinformationsdiensten (Internet Information Services, IIS) bereitgestellt wurde, müssen Sie die Remotetools auf dem Computer installieren und ausführen, auf dem Sie die App bereitgestellt haben, und diese anschließend über Visual Studio an Ihre laufende App anfügen.

![Remotedebuggerkomponenten](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

In diesem Leitfaden wird erläutert, wie Sie eine Visual Studio-App für ASP.NET MVC 4.5.2 einrichten, konfigurieren, in den IIS bereitstellen und diese über Visual Studio an den Remotedebugger anfügen.

> [!NOTE]
> Informationen zum Remotedebuggen von ASP.NET Core finden Sie unter [Remotedebuggen von ASP.NET Core auf einem Remotecomputer mit den IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). In Azure App Service können Sie Bereitstellungen und Debuggingvorgänge einfach auf einer vorkonfigurierten Instanz der IIS durchführen, indem Sie den [Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 erforderlich) verwenden oder [den Debugger über den Server-Explorer anfügen](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"
Visual Studio 2019 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end

Diese Verfahren wurden für die folgenden Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8 (für Windows Server 2008 R2 unterscheiden sich die Serverschritte)

## <a name="network-requirements"></a>Netzwerkanforderungen

Der Remotedebugger wird auf Windows Server-Versionen ab Windows Server 2008 Service Pack 2 unterstützt. Eine vollständige Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Das Debuggen zwischen zwei über einen Proxy verbundenen Computern wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder niedriger Bandbreite, z. B. eine DFÜ-Internetverbindung oder eine länderübergreifende Internetverbindung, wird nicht empfohlen. Der Vorgang kann fehlschlagen oder eine unzureichende Geschwindigkeit aufweisen.

## <a name="app-already-running-in-iis"></a>In den IIS ausgeführte Apps

Dieser Artikel enthält Schritte zum Einrichten einer Basiskonfiguration von IIS unter Windows Server und zum Bereitstellen der App aus Visual Studio. Damit soll sichergestellt, dass auf dem Server die erforderlichen Komponenten installiert sind, die App ordnungsgemäß ausgeführt werden kann und Sie bereit sind, das Remotedebuggen zu beginnen.

* Wenn Ihre App in IIS ausgeführt wird und Sie nur den Remotedebugger herunterladen und mit dem Debuggen starten möchten, navigieren Sie zu [Herunterladen und Installieren der Remotetools unter Windows Server](#BKMK_msvsmon).

* Wenn Sie sicherstellen möchten, dass Ihre App in IIS ordnungsgemäß eingerichtet, bereitgestellt und ausgeführt wird, damit Sie mit dem Debuggen beginnen können, führen Sie alle Schritte in diesem Thema aus.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Erstellen der ASP.NET 4.5.2-Anwendung auf dem Visual Studio-Computer

1. Erstellen Sie eine neue MVC ASP.NET-Anwendung.

    ::: moniker range=">=vs-2019"
    Drücken Sie in Visual Studio 2019 **STRG+Q**, um das Suchfeld zu öffnen, geben Sie **asp.net** ein, und wählen Sie **Vorlagen** und dann **Neue ASP.NET-Webanwendung erstellen (.NET Framework)** aus. Nennen Sie das Projekt im Dialogfeld, das nun geöffnet wird, **MyASPApp**, und wählen Sie dann **Erstellen** aus. Wählen Sie **MVC** aus, und klicken Sie auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie hierfür in Visual Studio 2017 auf **Datei > Neu > Projekt**, und wählen Sie dann **Visual C# > Web > ASP.NET-Webanwendung** aus. Im **ASP.NET 4.5.2** -Vorlagenabschnitt wählen Sie **MVC** aus. Stellen Sie sicher, dass **Docker-Unterstützung aktivieren** nicht aktiviert und **Authentifizierung** auf **Keine Authentifizierung** festgelegt ist. Geben Sie dem Projekt den Namen **MyASPApp**.
    ::: moniker-end

2. Öffnen Sie die Datei *HomeController.cs*, und legen Sie einen Haltepunkt in der `About()`-Methode fest.

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> Installieren und Konfigurieren der IIS unter Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren der Sicherheitseinstellungen des Browsers unter Windows Server

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (sie ist standardmäßig aktiviert), müssen Sie möglicherweise einige Domänen als vertrauenswürdige Sites hinzufügen, damit Sie einige der Webserverkomponenten herunterladen können. Fügen Sie die vertrauenswürdigen Sites hinzu, indem Sie zu **Internetoptionen > Sicherheit > vertrauenswürdige Sites > Sites** navigieren. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- iis.net

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen zum Erteilen der Berechtigung zum Laden verschiedener Websiteskripts und -ressourcen. Einige dieser Ressourcen sind nicht erforderlich. Um den Vorgang zu vereinfachen, klicken Sie jedoch auf **Hinzufügen**, wenn Sie dazu aufgefordert werden.

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a> Installieren von ASP.NET 4.5 unter Windows Server

Ausführlichere Informationen zur Installation von ASP.NET in den IIS finden Sie unter [IIS 8.0 mit ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Klicken Sie links im Server-Manager auf **IIS**. Klicken sie zuerst mit der rechten Maustaste auf den Server und anschließend mit der linken auf **Internet Information Services (IIS) Manager** (Internetinformationsdienste-Manager).

1. Verwenden Sie den Webplattform-Installer (Web PI), um ASP.NET 4.5 zu installieren. Klicken Sie hierzu im Knoten „Server“ in Windows Server 2012 R2 auf **Neue Webplattformkomponenten abrufen**, und suchen Sie nach ASP.NET.

    ![Screenshot des Webplattform-Installers 5.0 mit den Suchergebnissen für ASP.NET mit der Webplattformkomponente „IIS: ASP.NET 4.5“ in einem roten Kreis.](../debugger/media/remotedbg_iis_aspnet_45.png)

    > [!NOTE]
    > Wenn Sie Windows Server 2008 R2 verwenden, installieren Sie stattdessen ASP.NET 4 mit dem folgenden Befehl:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Starten Sie das System neu, oder führen Sie über eine Eingabeaufforderung **net stop was /y** gefolgt von **net start w3svc** aus, um eine Änderung am Systempfad zu übernehmen.

## <a name="choose-a-deployment-option"></a>Auswählen einer Bereitstellungsoption

Wenn Sie Hilfe bei der Bereitstellung der App in IIS benötigen, ziehen Sie die folgenden Optionen in Betracht:

* Führen Sie die Bereitstellung aus, indem Sie eine Datei mit Veröffentlichungseinstellungen in IIS erstellen und die Einstellungen in Visual Studio importieren. In einigen Szenarien ist dies eine schnelle Möglichkeit, Ihre App bereitzustellen. Wenn Sie die Datei mit den Veröffentlichungseinstellungen erstellen, werden Berechtigungen in IIS automatisch eingerichtet.

* Führen Sie die Bereitstellung durch Veröffentlichen in einem lokalen Ordner und Kopieren der Ausgabe durch eine bevorzugte Methode in einen vorbereiteten App-Ordner in IIS aus.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Optional) Bereitstellung mithilfe einer Datei mit Veröffentlichungseinstellungen

Sie können diese Option verwenden, um eine Datei mit Veröffentlichungseinstellungen zu erstellen und in Visual Studio zu importieren.

> [!NOTE]
> Bei dieser Bereitstellungsmethode wird Web Deploy verwendet und muss auf dem Server installiert sein. Wenn Sie Web Deploy manuell in konfigurieren möchten, anstatt die Einstellungen zu importieren, können Sie Web Deploy 3.6 anstelle von Web Deploy 3.6 für Hostingserver installieren. Wenn Sie Web Deploy jedoch manuell konfigurieren, müssen Sie sicherstellen, dass ein App-Ordner auf dem Server mit den richtigen Werten und Berechtigungen konfiguriert ist (siehe [Konfigurieren der ASP.NET-Website](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy für Hostingserver unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen der Veröffentlichungseinstellungsdatei in IIS unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importieren und Bereitstellen der Veröffentlichungseinstellungen in Visual Studio

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die App erfolgreich bereitgestellt wurde, sollte sie automatisch gestartet werden. Wenn die App nicht über Visual Studio gestartet wird, starten Sie sie in IIS.

1. Aktivieren Sie im Dialogfeld **Einstellungen** das Debuggen, indem Sie auf **Weiter** klicken, eine **Debugkonfiguration** auswählen und dann **Weitere Dateien im Ziel entfernen** unter den **Dateiveröffentlichungsoptionen** auswählen.

    > [!IMPORTANT]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie beim Veröffentlichen das Debuggen in der Datei *Web.config*.

1. Klicken Sie auf **Speichern**, und veröffentlichen Sie die App dann erneut.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Optional) Bereitstellung durch Veröffentlichen in einem lokalen Ordner

Sie können diese Option verwenden, um Ihre App bereitzustellen, wenn Sie die App mithilfe von PowerShell bzw. RoboCopy in die IIS kopieren oder die Dateien manuell kopieren möchten.

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Konfigurieren der ASP.NET-Website auf dem Windows Server-Computer

1. Öffnen Sie den Windows-Explorer, und erstellen Sie einen neuen Ordner (**C:\Publish**), in dem Sie später das ASP.NET-Projekt bereitstellen.

2. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , wenn dieser nicht bereits geöffnet ist. (Klicken Sie links im Server-Manager auf **IIS**. Klicken sie erst mit der rechten Maustaste auf den Server und anschließend mit der linken auf **Internetinformationsdienste-Manager**.)

3. Navigieren Sie links unter **Verbindungen** zu **Websites**.

4. Wählen Sie die **Standardwebsite** aus, klicken Sie auf **Grundeinstellungen**, und legen Sie den **physischen Pfad** auf **C:\Publish** fest.

5. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen** aus.

6. Legen Sie das Feld **Alias** auf **MyASPApp** fest. Akzeptieren Sie den Standardanwendungspool (**DefaultAppPool**), und legen Sie den **physischen Pfad** auf **C:\Publish** fest.

7. Klicken Sie unter **Verbindungen** auf **Anwendungspools**. Öffnen Sie **DefaultAppPool**, und legen Sie das Feld „Anwendungspool“ auf **ASP.NET v4.0** fest (ASP.NET 4.5 kann für den Anwendungspool nicht ausgewählt werden).

8. Wenn die Site im IIS-Manager ausgewählt ist, wählen Sie **Berechtigungen bearbeiten** aus, und stellen Sie sicher, dass IUSR, IIS_IUSRS oder der Benutzer, der für den Anwendungspool konfiguriert ist, ein autorisierter Benutzer mit Lese- und Ausführungsrechten ist. Wenn keiner dieser Benutzer vorhanden ist, fügen Sie IUSR als Benutzer mit Lese- und Ausführungsrechten hinzu.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Veröffentlichung und Bereitstellung der App über einen lokalen Ordner in Visual Studio

Sie können die App auch über das Dateisystem oder andere Tools veröffentlichen und bereitstellen.

1. (ASP.NET 4.5.2) Stellen Sie sicher, dass in der Datei „web.config“ die richtige Version von .NET aufgeführt ist.  Wenn Sie z. B. ASP.NET 4.5.2 festlegen, muss diese Version in „web.config“ aufgeführt sein.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Die Version sollte aber beispielsweise auf 4.0 festgelegt werden, wenn Sie ASP.NET 4 anstelle von ASP.NET 4.5.2 installiert haben.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Herunterladen und Installieren der Remotetools unter Windows Server

Laden Sie die Version der Remotetools herunter, die mit Ihrer Version von Visual Studio übereinstimmt.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Einrichten des Remotedebuggers unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen, den Authentifizierungsmodus oder die Portnummer für den Remotedebugger ändern müssen, finden Sie weitere Informationen unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

Weitere Informationen zum Ausführen des Remotedebuggers als Dienst finden Sie unter [(Optional) Konfigurieren des Remotedebuggers als Dienst](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die Projekt Mappe, die Sie debuggen möchten (**MyASPApp**, wenn Sie die Schritte in diesem Artikel befolgen).
2. Klicken Sie in Visual Studio auf **Debuggen > An Prozess anfügen** (STRG+ALT+P).

    > [!TIP]
    > In Visual Studio 2017 und höher können Sie erneut an denselben Prozess anfügen, an den Sie zuvor angefügt haben, indem Sie **Debuggen > Erneut an Prozess anfügen...** (UMSCHALT+ALT+P) verwenden.

3. Legen Sie das Feld „Qualifizierer“ auf **\<remote computer name>** fest, und drücken Sie die **EINGABETASTE**.

    Vergewissern Sie sich, dass Visual Studio den erforderlichen Port dem Computernamen hinzufügt, der im folgenden Format angezeigt wird: **\<remote computer name>:port**.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 sollte **\<remote computer name>:4024** angezeigt werden.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 sollte **\<remote computer name>:4022** angezeigt werden.
    ::: moniker-end
    Der Port ist erforderlich. Wenn die Portnummer nicht angezeigt wird, fügen Sie sie manuell hinzu.

4. Klicken Sie auf **Aktualisieren**.
    Im Fenster sollten einige Prozesse **Verfügbare Prozesse** angezeigt werden.

    Wenn keine Prozesse angezeigt werden, versuchen Sie, die IP-Adresse anstelle des Remotecomputernamens zu verwenden (der Port ist erforderlich). Sie können `ipconfig` in einer Befehlszeile verwenden, um die IPv4-Adresse abzurufen.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.

6. Geben Sie den ersten Buchstaben eines Prozessnamens ein, um **w3wp.exe** für ASP.NET 4.5 schnell zu finden.

    Wenn Sie mehrere Prozesse besitzen, für die **w3wp.exe** angezeigt wird, sehen Sie in der Spalte **Benutzername** nach. In einigen Szenarios wird in der Spalte **Benutzername** der Name Ihres App-Pools angezeigt, z. B. **IIS APPPOOL\DefaultAppPool**. Wenn Sie den App-Pool sehen, ist das Erstellen eines neuen benannten App-Pools für die App-Instanz, die Sie debuggen möchten, eine einfache Möglichkeit zum Identifizieren des richtigen Prozesses. Sie können ihn dann leicht in der Spalte **Benutzername** ermitteln.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klicken Sie auf **Attach** (Anhängen).

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser zu **http://\<remote computer name>** .

    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der ausgeführten ASP.NET-Anwendung auf den Link zur Seite **Info**.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Problembehandlung: Öffnen erforderlicher Ports unter Windows Server

In den meisten Setups werden erforderliche Ports durch die Installation von ASP.NET und des Remotedebuggers geöffnet. Möglicherweise müssen Sie jedoch selbst dafür sorgen, dass die Ports geöffnet sind.

> [!NOTE]
> Auf einer Azure-VM müssen Sie Ports über die [Netzwerksicherheitsgruppe](/azure/virtual-machines/windows/nsg-quickstart-portal) öffnen.

Erforderliche Ports:

* 80 – erforderlich für IIS
::: moniker range=">=vs-2019"
* 4024 – erforderlich für das Remotedebuggen aus Visual Studio 2019 (weitere Informationen finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)).
::: moniker-end
::: moniker range="vs-2017"
* 4022 – erforderlich für das Remotedebuggen aus Visual Studio 2017 (weitere Informationen finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)).
::: moniker-end
* UDP 3702 (optional) – Der Ermittlungsport aktiviert für Sie die Schaltfläche **Suchen**, wenn Sie den Remotedebugger in Visual Studio anfügen.

1. Suchen Sie im Menü **Start** nach **Windows-Firewall mit erweiterter Sicherheit**, um einen Port auf Windows Server zu öffnen.

2. Klicken Sie dann auf **Eingangsregeln > Neue Regel > Port**. Klicken Sie auf **Weiter**, und geben Sie unter **Bestimmte lokale Ports:** die Portnummer ein. Klicken Sie wieder auf **Weiter**, dann auf **Verbindung zulassen**, dann noch einmal auf „Weiter“, und geben Sie schließlich den Namen (**IIS**, **Web Deploy** oder **msvsmon**) für die Eingangsregel ein.

    Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie weitere Regeln für die restlichen erforderlichen Ports.