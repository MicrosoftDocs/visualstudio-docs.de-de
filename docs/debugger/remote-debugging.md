---
title: Remotedebuggen | Microsoft-Dokumentation
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8051b83e0022361e4cb1cb61602dfcf8991062e
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "92298685"
---
# <a name="remote-debugging"></a>Remote Debugging
Sie können eine Visual Studio-Anwendung debuggen, die auf einem anderen Computer bereitgestellt wurde. Dazu verwenden Sie den Visual Studio Remote Debugger.

Ausführliche Anweisungen zum Remotedebuggen finden Sie in den folgenden Themen.

|Szenario|Link|
|-|-|-|
|Azure App Service|[Remotedebuggen von ASP.NET Core in IIS in Azure in Visual Studio](../debugger/remote-debugging-azure.md) oder [Debuggen von aktiven ASP.NET Azure-Apps mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md) für Visual Studio Enterprise|
|Azure VM|[Remotedebuggen von ASP.NET in Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Debuggen einer Azure Service Fabric-Anwendung](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Remotedebuggen von ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) oder [Remotedebuggen von ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# oder Visual Basic|[Remotedebuggen eines C#- oder Visual Basic-Projekts](../debugger/remote-debugging-csharp.md)|
|C++|[Remotedebuggen eines C++-Projekts](../debugger/remote-debugging-cpp.md)|
|Universelle Windows-Apps (UWP)|[Ausführen von UWP-Apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md) oder [Debuggen eines installierten App-Pakets](../debugger/debug-installed-app-package.md)|

Wenn Sie den Remotedebugger nur herunterladen und installieren möchten und keine weiteren Anweisungen für Ihr Szenario benötigen, führen Sie die Schritte in diesem Artikel aus.

## <a name="download-and-install-the-remote-tools"></a>Herunterladen und Installieren der Remotetools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Anforderungen

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> (Optional) So führen Sie den Remotedebugger über eine Dateifreigabe aus

Der Remotedebugger ( *msvsmon.exe* ) ist auf einem Computer mit Visual Studio Community, Professional oder Enterprise bereits installiert. In einigen Szenarien ist die einfachste Möglichkeit zum Einrichten des Remotedebuggens das Ausführen des Remotedebuggers („msvsmon.exe“) aus einer Dateifreigabe. Informationen zu den Nutzungsbeschränkungen finden Sie auf der Hilfeseite des Remotedebuggers ( **Hilfe > Syntax** im Remotedebugger).

1. Suchen Sie *msvsmon.exe* in dem Verzeichnis, das Ihrer Version von Visual Studio entspricht:

   ::: moniker range=">=vs-2019"

   *Programme (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Programme (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Programme (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Programme (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Geben Sie den Ordner **Remote Debugger** auf dem Computer mit Visual Studio frei.

3. Führen Sie auf dem Remotecomputer *msvsmon.exe* aus dem freigegebenen Ordner aus. Befolgen Sie die [Setupanweisungen](#bkmk_setup).

> [!TIP]
> Informationen zur Befehlszeileninstallation und Befehlszeilenreferenz finden Sie auf der Hilfeseite zu *msvsmon.exe* , indem Sie ``msvsmon.exe /?`` in die Befehlszeile auf dem Computer eingeben, auf dem Visual Studio installiert ist (oder wechseln Sie zu **Hilfe > Syntax** im Remotedebugger).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Einrichten des Remotedebuggers

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a>Konfigurieren des Remotedebuggers
Sie können einige Aspekte der Konfiguration des Remotedebuggers ändern, nachdem Sie ihn zum ersten Mal gestartet haben.

- Wenn Sie Berechtigungen für andere Benutzer zum Herstellen einer Verbindung mit dem Remotedebugger hinzufügen müssen, wählen Sie **Extras > Berechtigungen** aus. Sie müssen Administratorrechte besitzen, um Berechtigungen zu gewähren oder zu verweigern.

     > [!IMPORTANT]
     > Sie können den Remotedebugger unter einem anderen Benutzerkonto als dem auf dem Visual Studio-Computer verwendeten Benutzerkonto ausführen, allerdings müssen Sie das andere Benutzerkonto den Berechtigungen des Remotedebuggers hinzufügen.

     Sie können den Remotedebugger mit dem Parameter **/allow \<username>** auch über die Befehlszeile starten: **msvsmon /allow \<username@computer>** .

- Wenn Sie den Authentifizierungsmodus oder die Portnummer ändern müssen oder einen Timeoutwert für die Remotetools angeben möchten, wählen Sie **Extras > Optionen** aus.

     Eine Liste der standardmäßig verwendeten Portnummern finden Sie unter [Remotedebugger-Portzuweisungen](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Sie haben die Möglichkeit, die Remotetools im Modus "Keine Authentifizierung" auszuführen, hiervon wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie den Modus „Ohne Authentifizierung“ nur aus, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> (Optional) Konfigurieren des Remotedebuggers als Dienst
Zum Debuggen in ASP.NET und anderen Serverumgebungen müssen Sie den Remotedebugger als Administrator ausführen. Wenn Sie möchten, dass er immer ausgeführt wird, müssen Sie den Remotedebugger als Dienst ausführen.

 Wenn Sie den Remotedebugger als Dienst konfigurieren möchten, führen Sie die folgenden Schritte aus.

1. Suchen Sie den **Konfigurations-Assistenten für Remote Debugger** (rdbgwiz.exe). (Dies ist eine vom Remotedebugger getrennte Anwendung.) Der Konfigurations-Assistent steht nur zur Verfügung, wenn Sie die Remotetools installieren, und wird nicht mit Visual Studio installiert.

2. Starten Sie den Konfigurations-Assistenten. Wenn die erste Seite angezeigt wird, klicken Sie auf **Weiter** .

3. Aktivieren Sie das Kontrollkästchen **Visual Studio 2015 Remote Debugger als Dienst ausführen** .

4. Fügen Sie den Namen des Benutzerkontos und das Kennwort hinzu.

    Sie müssen diesem Konto möglicherweise das Benutzerrecht **Anmelden als Dienst** hinzufügen (suchen Sie nach **Lokale Sicherheitsrichtlinie** („secpol.msc“) auf der **Startseite** oder im Fenster (oder geben Sie **secpol** an einer Eingabeaufforderung ein). Wenn das Fenster angezeigt wird, doppelklicken Sie auf **Zuweisen von Benutzerrechten** , und suchen Sie dann **Anmelden als Dienst** im rechten Bereich. Doppelklicken Sie darauf. Fügen Sie das Benutzerkonto zum Fenster **Eigenschaften** hinzu, und klicken Sie auf **OK** . Klicken Sie auf **Weiter** .

5. Wählen Sie den Typ des Netzwerks aus, über das die Remotetools kommunizieren sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, sollten Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, sollten Sie das zweite bzw. dritte Element auswählen. Klicken Sie auf **Weiter** .

6. Wenn der Dienst gestartet werden kann, wird **Der Konfigurations-Assistent für Visual Studio Remote Debugger wurde erfolgreich abgeschlossen** angezeigt. Wenn der Dienst nicht gestartet werden kann, wird **Fehler beim Abschließen des Assistenten zum Konfigurieren von Visual Studio Remote Debugger** angezeigt. Die Seite bietet auch Tipps, wie Sie den Dienst ans Laufen bringen können.

7. Klicken Sie auf **Fertig stellen** .

   An diesem Punkt wird der Remotedebugger als Dienst ausgeführt. Sie können dies überprüfen, indem Sie zu **Systemsteuerung > Dienste** navigieren und nach **Visual Studio 2015 Remote Debugger** suchen.

   Sie können den Remotedebugger-Dienst über **Systemsteuerung > Dienste** beenden und starten.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggens mit Remotesymbolen

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Siehe auch

- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger - Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen von ASP.NET Core auf einem IIS-Remotecomputer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)