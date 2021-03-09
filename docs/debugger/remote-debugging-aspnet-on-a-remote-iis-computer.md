---
title: Remotedebuggen von ASP.NET Core auf einem IIS-Remotecomputer| Microsoft-Dokumentation
description: Debuggen Sie eine ASP.NET Core-Anwendung, die mit dem Visual Studio Remote Debugger auf einem IIS-Remotecomputer (Internetinformationsdienste) bereitgestellt wurde.
ms.custom: remotedebugging, SEO-VS-2020
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1b4eabfe35671b3cda0e2df71163b7c91695b264
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683072"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Remotedebuggen von ASP.NET Core auf einem IIS-Remotecomputer in Visual Studio

Zum Debuggen einer ASP.NET Core-Anwendung, die in den Internetinformationsdiensten (Internet Information Services, IIS) bereitgestellt wurde, müssen Sie die Remotetools auf dem Computer installieren und ausführen, auf dem Sie die App bereitgestellt haben, und diese anschließend über Visual Studio an Ihre laufende App anfügen.

![Komponenten des Remotedebuggers](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

In diesem Leitfaden wird erläutert, wie Sie eine Visual Studio-ASP.NET Core-App einrichten, konfigurieren, in den IIS bereitstellen und diese über Visual Studio an den Remotedebugger anfügen. Informationen zum Remotedebuggen von ASP.NET 4.5.2 finden Sie unter [Remotedebuggen von ASP.NET auf einem Remotecomputer mit den IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Sie können auch mithilfe von Azure Apps in den IIS bereitstellen und debuggen. Für Azure App Service können Sie Apps ganz einfach auf einer vorab konfigurierten IIS-Instanz und auf dem Remotecomputer bereitstellen und debuggen, indem Sie den [Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md) verwenden oder [den Debugger über den Server-Explorer anfügen](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"
Visual Studio 2019 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end

Diese Verfahren wurden für die folgenden Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8
* Windows Server 2016 und IIS 10
* Windows Server 2019 und IIS 10

## <a name="network-requirements"></a>Netzwerkanforderungen

Das Debuggen zwischen zwei über einen Proxy verbundenen Computern wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder niedriger Bandbreite, z. B. eine DFÜ-Internetverbindung oder eine länderübergreifende Internetverbindung, wird nicht empfohlen. Der Vorgang kann fehlschlagen oder eine unzureichende Geschwindigkeit aufweisen. Eine vollständige Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>In den IIS ausgeführte Apps

Dieser Artikel enthält Schritte zum Einrichten einer Basiskonfiguration von IIS unter Windows Server und zum Bereitstellen der App aus Visual Studio. Damit soll sichergestellt, dass auf dem Server die erforderlichen Komponenten installiert sind, die App ordnungsgemäß ausgeführt werden kann und Sie bereit sind, das Remotedebuggen zu beginnen.

* Wenn Ihre App in IIS ausgeführt wird und Sie nur den Remotedebugger herunterladen und mit dem Debuggen starten möchten, navigieren Sie zu [Herunterladen und Installieren der Remotetools unter Windows Server](#BKMK_msvsmon).

* Wenn Sie sicherstellen möchten, dass Ihre App in den IIS ordnungsgemäß eingerichtet, bereitgestellt und ausgeführt wird, damit Sie mit dem Debuggen beginnen können, befolgen Sie die Anleitung in diesem Artikel.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Erstellen der ASP.NET Core-Anwendung auf dem Visual Studio-Computer

1. Erstellen Sie eine neue ASP.NET Core-Webanwendung.

    ::: moniker range=">=vs-2019"
    Wählen Sie im Startfenster von Visual Studio 2019 die Option **Neues Projekt erstellen** aus. Wenn das Startfenster nicht geöffnet ist, klicken Sie auf **Datei** > **Startfenster**. Geben Sie **Web-App** ein, wählen Sie als Sprache **C#** und anschließend **ASP.NET Core-Webanwendung (Model View Controller)** aus, und klicken Sie dann auf **Weiter**. Geben Sie dem Projekt im nächsten Bildschirm den Namen **MyASPApp**, und klicken Sie dann auf **Weiter**.

    Wählen Sie entweder das empfohlene Zielframework (.NET Core 3.1) oder .NET 5 aus, und klicken Sie dann auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 **Datei > Neu > Projekt** und dann **Visual C# > Web > ASP.NET Core-Webanwendung** aus. Wählen Sie im Abschnitt zu den ASP.NET Core-Vorlagen **Webanwendung (Model-View-Controller)** aus. Stellen Sie sicher, dass ASP.NET Core 2.1 ausgewählt ist, dass **Docker-Unterstützung aktivieren** nicht ausgewählt ist und dass **Authentifizierungs** auf **Keine Authentifizierungs** festgelegt ist. Geben Sie dem Projekt den Namen **MyASPApp**.
    ::: moniker-end

4. Öffnen Sie die Datei „About.cshtml.cs“, und legen Sie einen Haltepunkt in der Methode `OnGet` fest (in älteren Vorlagen öffnen Sie stattdessen „HomeController.cs“ und legen den Haltepunkt in der Methode `About()` fest).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> Installieren und Konfigurieren der IIS unter Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren der Sicherheitseinstellungen des Browsers unter Windows Server

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (sie ist standardmäßig aktiviert), müssen Sie möglicherweise einige Domänen als vertrauenswürdige Sites hinzufügen, damit Sie einige der Webserverkomponenten herunterladen können. Fügen Sie die vertrauenswürdigen Sites hinzu, indem Sie zu **Internetoptionen > Sicherheit > vertrauenswürdige Sites > Sites** navigieren. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- iis.net

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen zum Erteilen der Berechtigung zum Laden verschiedener Websiteskripts und -ressourcen. Einige dieser Ressourcen sind nicht erforderlich. Um den Vorgang zu vereinfachen, klicken Sie jedoch auf **Hinzufügen**, wenn Sie dazu aufgefordert werden.

## <a name="install-aspnet-core-on-windows-server"></a>Installieren von ASP.NET Core unter Windows Server

1. Installieren Sie das Paket „.NET Core Hosting“ auf dem Hostingsystem. Das Paket installiert die .NET Core-Runtime, die .NET Core-Bibliothek und das ASP.NET Core-Modul. Ausführlichere Informationen finden Sie unter [IIS-Konfiguration](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    Installieren Sie für .NET Core 3 das [.NET Core-Hostingpaket](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer).
    Installieren Sie für .NET Core 2 das Paket [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, beziehen und installieren Sie *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* , bevor Sie das Paket „.NET Core Windows Server Hosting“ installieren.

2. Starten Sie das System neu, oder führen Sie über eine Eingabeaufforderung **net stop was /y** gefolgt von **net start w3svc** aus, um eine Änderung am Systempfad zu übernehmen.

## <a name="choose-a-deployment-option"></a>Auswählen einer Bereitstellungsoption

Wenn Sie Hilfe bei der Bereitstellung der App in IIS benötigen, ziehen Sie die folgenden Optionen in Betracht:

* Führen Sie die Bereitstellung aus, indem Sie eine Datei mit Veröffentlichungseinstellungen in IIS erstellen und die Einstellungen in Visual Studio importieren. In einigen Szenarien ist dies eine schnelle Möglichkeit, Ihre App bereitzustellen. Wenn Sie die Datei mit den Veröffentlichungseinstellungen erstellen, werden Berechtigungen in IIS automatisch eingerichtet.

* Führen Sie die Bereitstellung durch Veröffentlichen in einem lokalen Ordner und Kopieren der Ausgabe durch eine bevorzugte Methode in einen vorbereiteten App-Ordner in IIS aus.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Optional) Bereitstellung mithilfe einer Datei mit Veröffentlichungseinstellungen

Sie können diese Option verwenden, um eine Datei mit Veröffentlichungseinstellungen zu erstellen und in Visual Studio zu importieren.

> [!NOTE]
> Bei dieser Bereitstellungsmethode wird Web Deploy verwendet und muss auf dem Server installiert sein. Wenn Sie Web Deploy manuell in konfigurieren möchten, anstatt die Einstellungen zu importieren, können Sie Web Deploy 3.6 anstelle von Web Deploy 3.6 für Hostingserver installieren. Wenn Sie Web Deploy jedoch manuell konfigurieren, müssen Sie sicherstellen, dass ein App-Ordner auf dem Server mit den richtigen Werten und Berechtigungen konfiguriert ist (siehe [Konfigurieren der ASP.NET-Website](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>Konfigurieren einer ASP.NET Core-Website

1. Wählen Sie in IIS-Manager im linken Bereich unter **Verbindungen** die Option **Anwendungspools** aus. Öffnen Sie **DefaultAppPool**, und legen Sie die **.NET CLR-Version** auf **Kein verwalteter Code** fest. Dies ist für ASP.NET Core erforderlich. Die Standardwebsite verwendet DefaultAppPool.

2. Beenden Sie DefaultAppPool, und starten Sie ihn dann neu.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installieren und Konfigurieren von Web Deploy für Hostingserver unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Erstellen der Veröffentlichungseinstellungsdatei in IIS unter Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importieren und Bereitstellen der Veröffentlichungseinstellungen in Visual Studio

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Nachdem die App erfolgreich bereitgestellt wurde, sollte sie automatisch gestartet werden. Wenn die App nicht aus Visual Studio gestartet wird, starten Sie die App in IIS, um zu bestätigen, dass sie ordnungsgemäß ausgeführt wird. Für ASP.NET Core müssen Sie außerdem sicherstellen, dass das Feld „Anwendungspool“ für **DefaultAppPool** auf **Kein verwalteter Code** festgelegt ist.

1. Aktivieren Sie im Dialogfeld **Einstellungen** das Debuggen, indem Sie auf **Weiter** klicken, eine **Debugkonfiguration** auswählen und dann **Weitere Dateien im Ziel entfernen** unter den **Dateiveröffentlichungsoptionen** auswählen.

    > [!IMPORTANT]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie beim Veröffentlichen das Debuggen in der Datei *Web.config*.

1. Klicken Sie auf **Speichern**, und veröffentlichen Sie die App dann erneut.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Optional) Bereitstellung durch Veröffentlichen in einem lokalen Ordner

Sie können diese Option verwenden, um Ihre App bereitzustellen, wenn Sie die App mithilfe von PowerShell bzw. RoboCopy in IIS kopieren möchten, oder wenn Sie die Dateien manuell kopieren möchten.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Konfigurieren der ASP.NET Core-Website auf dem Windows Server-Computer

1. Öffnen Sie den Windows-Explorer, und erstellen Sie einen neuen Ordner (**C:\Publish**), in dem Sie später das ASP.NET Core-Projekt bereitstellen.

2. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , wenn dieser nicht bereits geöffnet ist. (Klicken Sie links im Server-Manager auf **IIS**. Klicken sie erst mit der rechten Maustaste auf den Server und anschließend mit der linken auf **Internetinformationsdienste-Manager**.)

3. Navigieren Sie links unter **Verbindungen** zu **Websites**.

4. Wählen Sie die **Standardwebsite** aus, klicken Sie auf **Grundeinstellungen**, und legen Sie den **physischen Pfad** auf **C:\Publish** fest.

4. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen** aus.

5. Legen Sie das Feld **Alias** auf **MyASPApp** fest. Akzeptieren Sie den Standardanwendungspool (**DefaultAppPool**), und legen Sie den **physischen Pfad** auf **C:\Publish** fest.

6. Klicken Sie unter **Verbindungen** auf **Anwendungspools**. Öffnen Sie den Standardanwendungspool (**DefaultAppPool**), und legen Sie das Feld für den Anwendungspool auf **Kein verwalteter Code** fest.

7. Klicken Sie im IIS-Manager mit der rechten Maustaste auf die neue Website, klicken Sie auf **Berechtigungen bearbeiten**, und stellen Sie sicher, dass IUSR, IIS_IUSRS oder der Benutzer, der für den Zugriff auf die Web-App konfiguriert ist, ein autorisierter Benutzer mit Lese- und Ausführungsrechten ist.

    Wenn einer dieser Benutzer keinen Zugriff hat, führen Sie die Schritte zum Hinzufügen von IUSR als Benutzer mit Lese- und Ausführungsrechten aus.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Veröffentlichung und Bereitstellung der App über einen lokalen Ordner in Visual Studio

Sie können die App auch über das Dateisystem oder andere Tools veröffentlichen und bereitstellen.

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

1. Öffnen Sie auf dem Visual Studio-Computer die Projektmappe, die Sie debuggen möchten (**MyASPApp**, wenn Sie die Schritte in diesem Artikel befolgen).
2. Klicken Sie in Visual Studio auf **Debuggen > Attach to Process** (An Prozess anfügen) (STRG+ALT+P).

    > [!TIP]
    > In Visual Studio 2017 und höher können Sie die App noch einmal an denselben Prozess anfügen, an den Sie zuvor angefügt haben, indem Sie auf **Debuggen > Erneut an Prozess anfügen…** (UMSCHALT+ALT+P) klicken.

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

    Wenn Sie die Schaltfläche **Suchen** verwenden möchten, müssen Sie möglicherweise [UDP-Port 3702](#bkmk_openports) auf dem Server öffnen.

5. Aktivieren Sie  **Prozesse aller Benutzer anzeigen**.

6. Geben Sie den ersten Buchstaben des Namens Ihres Prozesses ein, um Ihre App schnell zu suchen.

    * Wenn Sie das [prozessinterne Hostingmodell](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) unter IIS verwenden, wählen Sie den richtigen **w3wp.exe**-Prozess aus. Ab .NET Core 3 ist dies der Standardprozess.

    * Wählen Sie andernfalls den Prozess **dotnet.exe** aus. (Dies ist das prozessexterne Hostingmodell.)

    Wenn für mehrere Prozesse *w3wp.exe* oder *dotnet.exe* angezeigt wird, müssen Sie in der Spalte **Benutzername** nachsehen. In einigen Szenarios wird in der Spalte **Benutzername** der Name Ihres App-Pools angezeigt, z. B. **IIS APPPOOL\DefaultAppPool**. Wenn Ihnen der App-Pool angezeigt wird, der Name jedoch nicht eindeutig ist, erstellen Sie einen neuen benannten App-Pool für die App-Instanz, die Sie debuggen möchten. Sie können ihn dann leicht in der Spalte **Benutzername** wiederfinden.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Klicken Sie auf **Anfügen** aus.

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

2. Klicken Sie dann auf **Eingangsregeln > Neue Regel > Port**, und klicken Sie auf **Weiter**. (Klicken Sie für UDP 3702 stattdessen auf **Ausgehende Regeln**.)

3. Geben Sie unter **Bestimmte lokale Ports** die Portnummer ein, und klicken Sie auf **Weiter**.

4. Klicken Sie auf **Verbindung zulassen** und dann auf **Weiter**.

5. Wählen Sie mindestens einen Netzwerktyp aus, die für den Port aktiviert werden sollen, und klicken Sie auf **Weiter**.

    Ein Typ muss das Netzwerk beinhalten, mit dem der Remotecomputer verbunden ist.
6. Fügen Sie für die eingehende Regel einen Namen ein (z. B. **IIS**, **Web Deploy** oder **msvsmon**), und klicken Sie auf **Beenden**.

    Daraufhin sollte die neue Regel in der Liste „Eingangsregeln“ bzw. „Ausgangsregeln“ angezeigt werden.

    Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Erstellen Sie weitere Regeln für die restlichen erforderlichen Ports.
