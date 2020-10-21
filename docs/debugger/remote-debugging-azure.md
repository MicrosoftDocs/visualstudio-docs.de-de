---
title: Remotedebuggen von ASP.NET Core in IIS und Azure | Microsoft-Dokumentation
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 926bd4a6630d9d99726ee6c1479d04c476756c18
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "92298749"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Remotedebuggen von ASP.NET Core in IIS in Azure in Visual Studio

In diesem Leitfaden wird erläutert, wie Sie eine Visual Studio ASP.NET Core-App einrichten, konfigurieren und mithilfe von Azure in IIS bereitstellen. Außerdem wird beschrieben, wie Sie den Remotedebugger aus Visual Studio anfügen.

Die empfohlene Vorgehensweise für das Remotedebuggen in Azure hängt von Ihrem Szenario ab:

* Informationen zum Debuggen von ASP.NET Core in Azure App Service finden Sie unter [Debuggen von Azure-Apps mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md). Dies ist die empfohlene Methode.
* Um ASP.NET Core in Azure App Service mithilfe von herkömmlichen Debugfunktionen zu debuggen, führen Sie die Schritte in diesem Thema aus (siehe Abschnitt [Remotedebuggen in Azure App Service](#remote_debug_azure_app_service)).

    In diesem Szenario müssen Sie die App aus Visual Studio in Azure bereitstellen, aber Sie müssen IIS oder den Remotedebugger (diese Komponenten werden durch gepunktete Linien dargestellt) nicht manuell installieren oder konfigurieren, wie in der folgenden Abbildung dargestellt.

    ![Remotedebuggerkomponenten](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Um IIS auf einer Azure-VM zu debuggen, führen Sie die Schritte in diesem Thema aus (weitere Informationen finden Sie im Abschnitt [Remotedebuggen auf einer Azure-VM](#remote_debug_azure_vm)). Dies ermöglicht es Ihnen, eine angepasste Konfiguration von IIS zu verwenden, die Einrichtungs- und Bereitstellungsschritte sind jedoch komplizierter.

    Für eine Azure-VM müssen Sie Ihre App aus Visual Studio in Azure bereitstellen. Außerdem müssen Sie die IIS-Rolle und den Remotedebugger manuell installieren, wie in der folgenden Abbildung gezeigt.

    ![Remotedebuggerkomponenten](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Informationen zum Debuggen von ASP.NET Core in Azure Service Fabric finden Sie unter [Debuggen einer Service Fabric-Remoteanwendung](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Stellen Sie sicher, dass Sie die Azure-Ressourcen löschen, die Sie erstellt haben, nachdem Sie die Schritte in diesem Tutorial ausgeführt haben. Auf diese Weise können Sie unnötige Kosten vermeiden.

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range=">=vs-2019"
Visual Studio 2019 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 ist erforderlich, um die in diesem Artikel gezeigten Schritte auszuführen.
::: moniker-end

### <a name="network-requirements"></a>Netzwerkanforderungen

Das Debuggen zwischen zwei über einen Proxy verbundenen Computern wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder geringer Bandbreite (z. B. eine Interneteinwählverbindung oder länderübergreifend über das Internet) wird nicht empfohlen und kann fehlschlagen oder inakzeptabel langsam sein. Eine vollständige Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Erstellen der ASP.NET Core-Anwendung auf dem Visual Studio-Computer

1. Erstellen Sie eine neue ASP.NET Core-Anwendung.

    ::: moniker range=">=vs-2019"
    Geben Sie in Visual Studio 2019 **STRG+Q** ein, um das Suchfeld zu öffnen, geben Sie **asp.net** ein, und wählen Sie **Vorlagen** und dann **Neue ASP.NET Core-Webanwendung erstellen** aus. Nennen Sie das Projekt im Dialogfeld, das nun geöffnet wird, **MyASPApp**, und wählen Sie dann **Erstellen** aus. Wählen Sie dann die Option **Webanwendung (Model-View-Controller)** aus, und klicken Sie auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in Visual Studio 2017 **Datei > Neu > Projekt** und dann **Visual C# > Web > ASP.NET Core-Webanwendung** aus. Wählen Sie im Abschnitt zu den ASP.NET Core-Vorlagen **Webanwendung (Model-View-Controller)** aus. Stellen Sie sicher, dass ASP.NET Core 2.1 ausgewählt ist, dass **Docker-Unterstützung aktivieren** nicht ausgewählt ist und dass **Authentifizierungs** auf **Keine Authentifizierungs** festgelegt ist. Geben Sie dem Projekt den Namen **MyASPApp**.
    ::: moniker-end

1. Öffnen Sie die Datei „About.cshtml.cs“, und legen Sie einen Breakpoint in der `OnGet`-Methode fest (in älteren Vorlagen öffnen Sie stattdessen „HomeController.cs“ und legen den Breakpoint in der `About()`-Methode fest).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a> Remotedebuggen von ASP.NET Core in Azure App Service

Aus Visual Studio können Sie Ihre App schnell in einer vollständig bereitgestellten Instanz von IIS veröffentlichen und debuggen. Allerdings ist die Konfiguration von IIS voreingestellt, und Sie können sie nicht anpassen. Ausführlichere Anweisungen dazu finden Sie unter [Veröffentlichen einer ASP.NET Core-App in Azure mit Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Wenn Sie eine Möglichkeit zum Anpassen von IIS benötigen, versuchen Sie, das Debuggen auf einer [Azure-VM](#remote_debug_azure_vm) auszuführen.)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>So stellen Sie die App und Remotedebuggen mit Cloud-Explorer bereit

1. Klicken Sie in Visual Studio mit der rechten Maustaste auf den Projektknoten, und wählen Sie dann **Veröffentlichen** aus.

    Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie auf **Neues Profil**.

1. Wählen Sie **Azure App Service** im Dialogfeld **Veröffentlichen** aus, wählen Sie die Option **Neu erstellen** aus, und befolgen Sie die Anweisungen, um ein Profil zu erstellen.

    Ausführliche Anweisungen finden Sie unter [Veröffentlichen einer ASP.NET Core-App in Azure mit Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Veröffentlichen in Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Wählen Sie im Fenster „Veröffentlichen“ **Konfiguration bearbeiten** aus, und wechseln Sie zu einer Debugkonfiguration. Wählen Sie dann **Veröffentlichen** aus.

   Eine Debugkonfiguration ist erforderlich, um die App zu debuggen.

1. Öffnen Sie **Cloud-Explorer** (**Anzeigen** > **Cloud-Explorer**), klicken Sie mit der rechten Maustaste auf die App Service-Instanz, und wählen Sie **Debugger anfügen** aus.

   Wenn Cloud-Explorer nicht verfügbar ist, öffnen Sie stattdessen Server-Explorer. Klicken Sie dann mit der rechten Maustaste auf die App Service-Instanz in Server-Explorer, und wählen Sie **Debugger anfügen** aus.

1. Klicken Sie in der ausgeführten ASP.NET-Anwendung auf den Link zur Seite **Info**.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

    Das ist alles! Die restlichen Schritte in diesem Thema gelten für Remotedebuggen auf einer Azure-VM.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a> Remotedebuggen von ASP.NET Core auf einer Azure-VM

Sie können eine Azure-VM für Windows Server erstellen und anschließend IIS und die anderen erforderlichen Softwarekomponenten installieren und konfigurieren. Dies nimmt mehr Zeit als die Bereitstellung für einen Azure App Service in Anspruch und erfordert, dass Sie die verbleibenden Schritte in diesem Tutorial ausführen.

Diese Verfahren wurden für die folgenden Serverkonfigurationen getestet:
* Windows Server 2012 R2 und IIS 8
* Windows Server 2016 und IIS 10
* Windows Server 2019 und IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Wird die App bereits in IIS auf der Azure-VM ausgeführt?

Dieser Artikel enthält Schritte zum Einrichten einer Basiskonfiguration von IIS unter Windows Server und zum Bereitstellen der App aus Visual Studio. Diese Schritte sind enthalten, um sicherzustellen, dass auf dem Server die erforderlichen Komponenten installiert sind, dass die App ordnungsgemäß ausgeführt werden kann und dass Sie für Remotedebuggen bereit sind.

* Wenn Ihre App in IIS ausgeführt wird und Sie nur den Remotedebugger herunterladen und mit dem Debuggen starten möchten, navigieren Sie zu [Herunterladen und Installieren der Remotetools unter Windows Server](#BKMK_msvsmon).

* Wenn Sie sicherstellen möchten, dass Ihre App in IIS ordnungsgemäß eingerichtet, bereitgestellt und ausgeführt wird, damit Sie mit dem Debuggen beginnen können, führen Sie alle Schritte in diesem Thema aus.

  * Bevor Sie beginnen, führen Sie alle Schritte aus, die unter [Installieren und Ausführen von IIS](/azure/virtual-machines/windows/quick-create-portal) beschrieben werden.

  * Wenn Sie Port 80 in der Netzwerksicherheitsgruppe öffnen, öffnen Sie auch den [richtigen Port](#bkmk_openports) für den Remotedebugger (4024 oder 4022). Auf diese Weise müssen Sie ihn später nicht mehr öffnen. Wenn Sie Web Deploy verwenden, öffnen Sie auch Port 8172.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualisieren der Sicherheitseinstellungen des Browsers unter Windows Server

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer aktiviert ist (sie ist standardmäßig aktiviert), müssen Sie möglicherweise einige Domänen als vertrauenswürdige Sites hinzufügen, damit Sie einige der Webserverkomponenten herunterladen können. Fügen Sie die vertrauenswürdigen Sites hinzu, indem Sie zu **Internetoptionen > Sicherheit > vertrauenswürdige Sites > Sites** navigieren. Fügen Sie die folgenden Domänen hinzu.

- microsoft.com
- go.microsoft.com
- 0download.microsoft.com
- iis.net

Wenn Sie die Software herunterladen, erhalten Sie möglicherweise Anforderungen zum Erteilen der Berechtigung zum Laden verschiedener Websiteskripts und -ressourcen. Einige dieser Ressourcen sind nicht erforderlich. Um den Vorgang zu vereinfachen, klicken Sie jedoch auf **Hinzufügen**, wenn Sie dazu aufgefordert werden.

### <a name="install-aspnet-core-on-windows-server"></a>Installieren von ASP.NET Core unter Windows Server

1. Installieren Sie das Paket „.NET Core Hosting“ auf dem Hostingsystem. Das Paket installiert die .NET Core-Runtime, die .NET Core-Bibliothek und das ASP.NET Core-Modul. Ausführlichere Informationen finden Sie unter [IIS-Konfiguration](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    Installieren Sie für .NET Core 3 das [.NET Core-Hostingpaket](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer).
    Installieren Sie für .NET Core 2 das Paket [.NET Core Windows Server Hosting](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Wenn das System nicht über eine Internetverbindung verfügt, beziehen und installieren Sie *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* , bevor Sie das Paket „.NET Core Windows Server Hosting“ installieren.

3. Starten Sie das System neu, oder führen Sie über eine Eingabeaufforderung **net stop was /y** gefolgt von **net start w3svc** aus, um eine Änderung am Systempfad zu übernehmen.

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

> [!NOTE]
> Wenn Sie eine Azure-VM neu starten, wird die IP-Adresse möglicherweise geändert.

Nachdem die App erfolgreich bereitgestellt wurde, sollte sie automatisch gestartet werden. Wenn die App nicht aus Visual Studio gestartet wird, starten Sie die App in IIS, um zu bestätigen, dass sie ordnungsgemäß ausgeführt wird. Für ASP.NET Core müssen Sie außerdem sicherstellen, dass das Feld „Anwendungspool“ für **DefaultAppPool** auf **Kein verwalteter Code** festgelegt ist.

1. Aktivieren Sie im Dialogfeld **Einstellungen** das Debuggen, indem Sie auf **Weiter** klicken, eine **Debugkonfiguration** auswählen und dann **Weitere Dateien im Ziel entfernen** unter den **Dateiveröffentlichungsoptionen** auswählen.

    > [!IMPORTANT]
    > Wenn Sie eine Releasekonfiguration auswählen, deaktivieren Sie beim Veröffentlichen das Debuggen in der Datei *Web.config*.

1. Klicken Sie auf **Speichern**, und veröffentlichen Sie die App dann erneut.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Optional) Bereitstellung durch Veröffentlichen in einem lokalen Ordner

Sie können diese Option verwenden, um Ihre App bereitzustellen, wenn Sie die App mithilfe von PowerShell bzw. RoboCopy in IIS kopieren möchten, oder wenn Sie die Dateien manuell kopieren möchten.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Konfigurieren der ASP.NET Core-Website auf dem Windows Server-Computer

Wenn Sie Veröffentlichungseinstellungen importieren, können Sie diesen Abschnitt überspringen.

1. Öffnen Sie den **Internetinformationsdienste-Manager (IIS)** , und navigieren Sie zu **Websites**.

2. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

3. Legen Sie das Feld **Alias** auf **MyASPApp** und das Feld „Anwendungspool“ auf **Kein verwalteter Code** fest. Legen Sie den **physischen Pfad** auf **C:\Publish** fest (in dem Sie das ASP.NET Core-Projekt später bereitstellen).

4. Wenn die Site im IIS-Manager ausgewählt ist, wählen Sie **Berechtigungen bearbeiten** aus, und stellen Sie sicher, dass IUSR, IIS_IUSRS oder der Benutzer, der für den Anwendungspool konfiguriert ist, ein autorisierter Benutzer mit Lese- und Ausführungsrechten ist.

    Wenn einer dieser Benutzer keinen Zugriff hat, führen Sie die Schritte zum Hinzufügen von IUSR als Benutzer mit Lese- und Ausführungsrechten aus.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Optional) Veröffentlichung und Bereitstellung der App durch Veröffentlichen in einem lokalen Ordner in Visual Studio

Wenn Sie Web Deploy nicht verwenden, müssen Sie die App mit dem Dateisystem oder anderen Tools veröffentlichen und bereitstellen. Sie können beginnen, indem Sie ein Paket mit dem Dateisystem erstellen und das Paket dann entweder manuell bereitstellen oder andere Tools wie PowerShell, RoboCopy oder XCopy verwenden. In diesem Abschnitt wird davon ausgegangen, dass Sie das Paket manuell kopieren, wenn Sie Web Deploy nicht verwenden.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Herunterladen und Installieren der Remotetools unter Windows Server

Laden Sie die Version der Remotetools herunter, die mit Ihrer Version von Visual Studio übereinstimmt.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Einrichten des Remotedebuggers unter Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen, den Authentifizierungsmodus oder die Portnummer für den Remotedebugger ändern müssen, finden Sie weitere Informationen unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Anfügen an die ASP.NET-Anwendung vom Visual Studio-Computer aus

1. Öffnen Sie auf dem Visual Studio-Computer die Projekt Mappe, die Sie debuggen möchten (**MyASPApp**, wenn Sie die Schritte in diesem Artikel befolgen).
2. Klicken Sie in Visual Studio auf **Debuggen > An Prozess anfügen** (STRG+ALT+P).

    > [!TIP]
    > In Visual Studio 2017 und höheren Versionen können Sie an denselben Prozess, an den Sie zuvor angefügt haben, erneut anfügen, indem Sie **Debuggen > Erneut an Prozess anfügen...** (UMSCHALT+ALT+P) verwenden.

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

7. Klicken Sie auf **Anfügen**aus.

8. Öffnen Sie die Website des Remotecomputers. Navigieren Sie in einem Browser zu **http://\<remote computer name>** .

    Es sollte die ASP.NET-Webseite angezeigt werden.
9. Klicken Sie in der ausgeführten ASP.NET-Anwendung auf den Link zur Seite **Info**.

    Der Haltepunkt sollte in Visual Studio erreicht werden.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Problembehandlung: Öffnen erforderlicher Ports unter Windows Server

In den meisten Setups werden erforderliche Ports durch die Installation von ASP.NET und des Remotedebuggers geöffnet. Wenn Sie jedoch Bereitstellungsprobleme behandeln und die App hinter einer Firewall gehostet wird, müssen Sie möglicherweise überprüfen, ob die richtigen Ports geöffnet sind.

Auf einer Azure-VM müssen Sie Ports über die [Netzwerksicherheitsgruppe](/azure/virtual-machines/windows/nsg-quickstart-portal) öffnen.

Erforderliche Ports:

* 80 – erforderlich für IIS
::: moniker range=">=vs-2019"
* 4024 – erforderlich für das Remotedebuggen aus Visual Studio 2019 (weitere Informationen finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)).
::: moniker-end
::: moniker range="vs-2017"
* 4022 – erforderlich für das Remotedebuggen aus Visual Studio 2017 (weitere Informationen finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md)).
::: moniker-end
* UDP 3702 (optional) – Der Ermittlungsport aktiviert für Sie die Schaltfläche **Suchen**, wenn Sie den Remotedebugger in Visual Studio anfügen.

Außerdem sollten diese Ports bereits von der ASP.NET-Installation geöffnet worden sein:
- 8172 (optional) – erforderlich, damit Web Deploy die App aus Visual Studio bereitstellen kann.
