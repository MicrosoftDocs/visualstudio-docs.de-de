---
title: Starten einer Debugsitzung für eine UWP-App | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie eine Visual Studio-Debugsitzung für eine UWP-App (Universelle Windows-Plattform) starten. Außerdem konfigurieren Sie die Debugsitzung und wählen die Methode für den Start der App aus.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/20/2018
ms.topic: how-to
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 003eaa7eefffaab9ff2b3c8c25a5ce5c0d41d43b
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150365"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Starten einer Debugsitzung für eine UWP-App

In diesem Artikel wird beschrieben, wie eine Visual Studio-Debugsitzung für eine universelle Windows-Plattform-App (UWP) gestartet wird. UWP-Apps können in XAML und C++ , XAML und C#/Visual Basic geschrieben werden. Zum Starten des Debuggens einer UWP-App konfigurieren Sie die Debugsitzung und wählen die Methode für den App-Start aus.

::: moniker range=">=vs-2019"
> [!NOTE]
> Ab Visual Studio 2019 werden UWP-Apps für HTML und JavaScript nicht mehr unterstützt.
::: moniker-end
::: moniker range="vs-2017"
In Visual Studio 2017 gelten die meisten der in diesem Artikel gezeigten Befehle und Optionen auch für UWP-Apps für HTML und JavaScript. Wenn sich die Befehle zwischen verwalteten Apps und C++-Apps unterscheiden, entsprechen die Befehle für JavaScript-Apps in der Regel denen für C++-UWP-Apps.
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Starten des Debuggens über die Visual Studio-Symbolleiste

Die einfachste Möglichkeit zum Konfigurieren und Starten des Debuggens ist die Standardsymbolleiste von Visual Studio.

![Debuggen über die Symbolleiste](../debugger/media/vsrun_select_target_device.png)

1. Wählen Sie in der Dropdownliste **Konfiguration** in der Symbolleiste **Standard** die Option **Debuggen** aus.

1. Wählen Sie in der Dropdownliste **Plattform** die Zielplattform aus, in der der Build erstellt werden soll.

1. Wählen Sie in der Dropdownliste neben dem grünen Pfeil das Debugziel aus. Sie können einen lokalen Computer, ein direkt verbundenes Gerät, einen lokalen Visual Studio-Simulator, ein Remotegerät oder einen Emulator auswählen.

1. Um das Debuggen zu starten, wählen Sie den grünen Pfeil **Start** in der Visual Studio-Symbolleiste aus, oder wählen **Debuggen** > **Debuggen starten** aus oder drücken **F5**.

   In Visual Studio wird die Anwendung mit dem angefügten Debugger erstellt und gestartet.

Das Debuggen wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie es manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a> Optionen für das Bereitstellungsziel

Sie können das Debugziel in der Visual Studio-Symbolleiste oder auf der Seite mit den Debugeigenschaften des Projekts festlegen. Wählen Sie einen der folgenden Optionen aus:

|name|Beschreibung|
|-|-|
|**Lokaler Computer**|Debuggen Sie die Anwendung in der aktuellen Sitzung auf dem lokalen Computer.|
|**Simulator**|Debuggen Sie die Anwendung im Visual Studio-Simulator für UWP-Apps. Der Simulator ist ein Desktopfenster, das Gerätefunktionen simuliert, wie z. B. Touchgesten und Gerätedrehung, die auf dem lokalen Computer möglicherweise nicht vorhanden sind. Die Simulatoroption ist nur verfügbar, wenn die **Mindestversion der Zielplattform** Ihrer App kleiner oder gleich dem Betriebssystem auf dem lokalen Rechner ist. Weitere Informationen finden Sie unter [Ausführen von UWP-Apps im Simulator](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Remotecomputer**|Debuggen Sie die App auf einem Gerät, das über ein Netzwerk- oder Ethernetkabel mit dem lokalen Computer verbunden ist. Die Remotetools für Visual Studio müssen installiert sein und auf dem Remotegerät ausgeführt werden. Weitere Informationen finden Sie unter [Ausführen von UWP-Apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Gerät**|Debuggen Sie die App auf einem USB-Gerät. Das Gerät muss vom Entwickler entsperrt sein und den Bildschirm entsperrt haben.|
|**Mobile Emulator**|Starten Sie den im Emulatornamen angegebenen Emulator, stellen Sie die App bereit, und beginnen Sie mit dem Debuggen. Emulatoren sind nur auf Hyper-V-fähigen Computern verfügbar.|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Konfigurieren des Debuggens auf der Eigenschaftenseite des Projekts

Um zusätzliche Debugoptionen zu konfigurieren, verwenden Sie die Seite mit den Debuggingeigenschaften des Projekts.

**So öffnen Sie die Debuggingeigenschaften**

1. Wählen Sie im **Projektmappen-Explorer** das Projekt aus, und wählen Sie dann das Symbol **Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus.

1. Auf der linken Seite des Bereichs **Eigenschaften**:

   - Wählen Sie für C#- und Visual Basic-Apps **Debuggen** aus.

     ![Seite mit Debuggingeigenschaften des Projekts für C# und Visual Basic](../debugger/media/dbg_csvb_debugpropertypage.png)

   - Wählen Sie für C++-Apps **Konfigurationseigenschaften** > **Debuggen** aus.

     ![Debugging-Eigenschaftsseite für C++-UWP-App](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Auswahl des zu verwendenden Debuggers

Bei C#- und Visual Basic-Apps erfolgt standardmäßig das Debuggen von Code in Visual Studio. Sie können auch andere oder zusätzliche Codetypen debuggen. Sie können auch **Debuggertyp**-Werte für alle Hintergrundaufgaben festlegen, die Teil des Projekts sind.

In C++-Apps ist das Debuggen von nativem Code in Visual Studio eine Standardeinstellung. Sie können auswählen, dass bestimmte Codetypen anstelle von oder zusätzlich zu nativem Code debuggt werden.

**So geben Sie die zu debuggenden Codetypen an**

- Wählen Sie für C#- und Visual Basic-Apps einen der folgenden Debugger auf der Eigenschaftsseite **Debuggen** unter **Debuggertyp** aus den Dropdownlisten **Anwendungstyp** und **Hintergrundprozesstyp** aus.

- Wählen Sie für C++-Apps einen der folgenden Debugger auf der Eigenschaftsseite **Debuggen** aus der Dropdownliste **Debuggertyp** aus.

|name|Beschreibung|
|-|-|
|**Nur verwaltet**|Für das Debuggen des verwalteten Codes der Anwendung. JavaScript- und systemeigener C/C++-Code werden ignoriert.|
|**Nur systemeigen**|Für das Debuggen des systemeigenen C/C++-Codes der Anwendung. Verwalteter und JavaScript-Code werden ignoriert.|
|**Gemischt (verwaltet und systemeigen)**|Für das Debuggen des systemeigenen C/C++- und des verwalteten Codes der Anwendung. JavaScript-Code wird ignoriert. In C++-Projekten wird diese Option **Verwaltet und Nativ** genannt.|
|**Skript**|Für das Debuggen des JavaScript-Codes der Anwendung. Verwalteter und systemeigener Code werden ignoriert.|
|**Nativ mit Skript**|Für das Debuggen des nativen C/C++-Codes und des JavaScript-Codes der Anwendung. Verwalteter Code wird ignoriert. Nur in C++-Projekten oder Hintergrundaufgaben verfügbar.|
|**Nur GPU (C++ AMP)**|Debuggen von systemeigenem C++-Code, der auf einer Grafikverarbeitungseinheit (GPU) ausgeführt wird. Nur in C++-Projekten verfügbar.|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> Netzwerkloopbacks deaktivieren (optional)

 Aus Sicherheitsgründen kann eine UWP-Anwendung, die standardmäßig installiert ist, keine Netzwerkaufrufe an das Gerät auszuführen, auf dem sie installiert wurde. In Visual Studio sind bereitgestellte Apps standardmäßig von dieser Regel ausgenommen, sodass Sie Kommunikationsverfahren auf einem einzelnen Computer testen können. Bevor Sie die App freigeben, sollten Sie die App ohne die Ausnahme testen.

**So entfernen Sie die Netzwerkloopbackausnahme:**

- Deaktivieren Sie für C#- und Visual Basic-Apps auf der Eigenschaftsseite **Debuggen** unter **Startoptionen** das Kontrollkästchen **Lokales Netzwerkloopback zulassen**.

- Wählen Sie für C++-Apps auf der Eigenschaftsseite **Debuggen** aus der Dropdownliste **Lokales Netzwerkloopback zulassen** die Option **Nein** aus.

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Installieren Sie die Anwendung neu, wenn Sie das Debuggen starten (optional)
 Zur Diagnose von Installationsproblemen mit einer C#- oder Visual Basic-App, wählen Sie auf der Eigenschaftsseite **Debuggen** die Option **Paket deinstallieren und anschließend neu installieren** aus. Mit dieser Option wird die ursprüngliche Installation neu erstellt, wenn Sie das Debuggen starten. Diese Option ist für C++-Projekte nicht verfügbar.

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Festlegen der Authentifizierungsoptionen für das Remotedebuggen

Standardmäßig müssen Sie Windows-Anmeldeinformationen angeben, um den Remotedebugger auszuführen, wenn Sie **Remotecomputer** als Bereitstellungsziel wählen. Sie können die Authentifizierungsanforderung ändern.

Der Authentifizierungsmodus **Universell (unverschlüsseltes Protokoll)** ist für IoT-, Xbox- und HoloLens-Geräte sowie für PCs mit Creator-Update oder neuerer Windows 10-Version.

**So ändern Sie die Authentifizierungsmethode**

- Wählen Sie für C#- und Visual Basic-Apps auf der Eigenschaftsseite **Debuggen** die Option **Remotecomputer** als **Zielgerät** aus. Wählen Sie dann für **Authentifizierungsmodus** die Option **Keine** oder **Universell (unverschlüsseltes Protokoll)** aus.

- Wählen Sie für C++-Apps auf der Eigenschaftsseite **Debuggen** unter **Zu startender Debugger** die Option **Remotecomputer** aus. Wählen Sie dann für **Authentifizierungsmodus** die Option **Keine Authentifizierung** oder **Universell (unverschlüsseltes Protokoll)** aus.

> [!CAUTION]
> Die Netzwerksicherheit ist nicht gegeben, wenn Sie den Remotedebugger in den Modi **Keine** oder **Universell (unverschlüsseltes Protokoll)** ausführen. Wählen Sie diese Modi nur in vertrauenswürdigen Netzwerken, von denen Sie sicher sind, dass sie nicht durch schädlichen Code oder feindlichen Datenverkehr gefährdet sind.

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a> Startoptionen für das Debuggen

Wenn Sie **Debuggen** > **Debuggen starten** auswählen oder **F5** drücken, startet Visual Studio die App mit dem angefügten Debugger. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Starten des Debuggens mit verzögertem App-Start

In der Standardeinstellung wird die App in Visual Studio sofort gestartet, wenn Sie das Debuggen starten. Sie können die App auch so einrichten, dass sie im Debugmodus ausgeführt wird, aber außerhalb des Debuggers gestartet wird. Angenommen, Sie möchten den App-Start über das Windows-**Start**-Menü starten oder einen Hintergrundprozess in der App debuggen. Wenn Sie diese Option auswählen, wird die App beim Start im Debugger gestartet.

**So deaktivieren Sie den automatischen App-Start**

- Wählen Sie für C#- und Visual Basic-Apps auf der Eigenschaftenseite **Debuggen** unter **Startoptionen** die Option **Eigenen Code zunächst nicht starten, sondern debuggen** aus.

- Wählen Sie für C++-Apps auf der Eigenschaftsseite **Debuggen** aus der Dropdownliste **Anwendung starten** die Option **Nein** aus.

Weitere Informationen zum Debuggen von Hintergrundaufgaben finden Sie unter [Trigger suspend, resume, and background events for UWP apps](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) (Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps).

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Debuggen einer installierten oder laufenden UWP-App

Sie können **Installiertes App-Paket debuggen** verwenden, um eine UWP-App zu debuggen, die bereits auf einem lokalen Gerät oder einem Remotegerät ausgeführt wird. Möglicherweise wurde die App aus dem Microsoft Store installiert, oder es handelt sich nicht um ein Visual Studio-Projekt. So kann die App beispielsweise über ein benutzerdefiniertes Buildsystem verfügen, das keine Visual Studio-Projekte oder -Projektmappen verwendet.

Sie können die installierte App sofort starten, oder Sie können Sie so festlegen, dass Sie im Debugger ausgeführt wird, wenn Sie mit einer anderen Methode gestartet wird. Weitere Informationen finden Sie unter [Trigger suspend, resume, and background events for UWP apps](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) (Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen in UWP-Apps).

Zum Starten einer installierten oder laufenden UWP-App im Debugger wählen Sie **Debuggen** > **Andere Debugziele** > **Installiertes App-Paket debuggen** aus. Weitere Anweisungen finden Sie unter [Debuggen eines installierten App-Pakets](../debugger/debug-installed-app-package.md).

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Anfügen des Debuggers an eine ausgeführte Windows 8.x-App

Um den Debugger an eine [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] -App anzufügen, müssen Sie im Manager für debugfähige Pakete festlegen, dass die App im Debugmodus ausgeführt wird. Der Debuggable Package Manager wird mit den Remotetools für Visual Studio installiert.

1. Installieren Sie die Remotetools für Visual Studio auf dem Gerät, auf dem die App installiert wurde. Weitere Informationen finden Sie unter [Installieren der Remotetools](../debugger/remote-debugging.md).

1. Suchen Sie über den Windows-**Start** nach **Debuggable Package Manager**, und starten Sie ihn.

   Es wird ein ordnungsgemäß für das AppxDebug-Cmdlet konfiguriertes PowerShell-Fenster angezeigt.

1. Geben Sie den PackageFullName-Bezeichner der App an.

   1. Um eine Liste anzuzeigen, die PackageFullName für alle Apps enthält, geben Sie in der PowerShell-Eingabeaufforderung `Get-AppxPackage` ein.

   1. Geben Sie `Enable-AppxDebug <PackageFullName>` in der PowerShell-Eingabeaufforderung ein, wobei \<PackageFullName> dem PackageFullName-Bezeichner der App entspricht.

1. Wählen Sie **Debuggen** > **An den Prozess anhängen** aus.

1. Geben Sie im Dialogfeld **An den Prozess anhängen** das Remotegerät im Feld **Verbindungsziel** an.

   Sie können den Gerätenamen eingeben, ihn aus der Dropdownliste im Feld **Verbindungsziel** auswählen oder **Suchen** auswählen, um das Gerät im Dialogfeld **Remoteverbindungen** zu suchen.

1. Geben Sie den zu debuggenden Codetyp an, indem Sie neben dem Feld **Anfügen an** die Option **Auswählen** auswählen.

1. Wählen Sie im Dialogfeld **Codetyp auswählen** eine der folgenden Optionen aus:
   - **Zu debuggenden Codetyp automatisch bestimmen** oder
   - **Diese Codetypen debuggen**. Wählen Sie anschließend mindestens einen Codetyp aus der Liste aus.

1. Wählen Sie in der Liste **Verfügbare Prozesse**  den App-Prozess zum Debuggen aus.

1. Wählen Sie **Anfügen** aus.

 Der Debugger wird in Visual Studio an den Prozess angefügt. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript-Apps werden in einer Instanz des Prozesses *wwahost.exe* ausgeführt. Wenn mehr als eine JavaScript-App ausgeführt wird, müssen Sie die numerische Prozess-ID (PID) des *wwahost.exe*-Prozesses Ihrer App kennen, um sie anfügen zu können.
>
> Am einfachsten können Sie Ihre JavaScript-App anfügen, indem Sie alle anderen JavaScript-Apps schließen. Oder Sie können sich die PIDs der ausgeführten *wwahost.exe*-Prozesse im Windows Task-Manager notieren, bevor Sie Ihre App starten. Wenn Sie Ihre App starten, wird ihre *wwahost.exe*-PID diejenige sein, die sich von den von Ihnen zuvor genannten unterscheidet.
::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Debuggen von Apps in Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)