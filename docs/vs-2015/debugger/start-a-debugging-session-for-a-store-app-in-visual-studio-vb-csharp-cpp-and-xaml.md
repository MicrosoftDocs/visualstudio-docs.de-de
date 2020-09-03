---
title: Starten einer Debugsitzung für eine Store-App (VB, c#, C++ und XAML) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd0a89ac1d96e2d1af829ba04e6e164f8fae7f8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542180"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Starten einer Debugsitzung für eine Store-App in Visual Studio (VB, C#, C++ und XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 In diesem Thema wird beschrieben, wie eine Debugsitzung für Store-Apps ausgeführt wird, die in XAML und Visual C++, Visual C# oder Visual Basic programmiert sind. Das Debuggen einer Anwendung umfasst sowohl das Konfigurieren der Debugsitzung als auch die Auswahl der Methode für den Anwendungsstart.

> [!NOTE]
> Informationen zu in JavaScript und HTML geschriebenen apps finden Sie unter [Starten einer Debugsitzung (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> In diesem Thema
 [Die einfache Methode zum Starten des Debuggings](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurieren der Debugsitzung](#BKMK_Configure_the_debugging_session)

- [Öffnen Sie die Debugeigenschaftenseite für das Projekt](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Wählen Sie die Buildkonfigurationsoptionen aus.](#BKMK_Choose_the_build_configuration_options)

- [Auswählen des Bereitstellungs Ziels](#BKMK_Choose_the_deployment_target)

- [Wählen Sie den zu verwendenden Debugger aus.](#BKMK_Choose_the_debugger_to_use)

- [(Optional) Verzögertes Starten der Debugsitzung](#BKMK__Optional__Delay_starting_the_debug_session)

- [Optionale Netzwerk Loop Backs deaktivieren deaktivieren](#BKMK__Optional__Disable_network_loopbacks)

- [Optionale Installieren Sie die APP neu, wenn Sie das Debugging starten.](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [Optionale Deaktivieren Sie die Authentifizierungsanforderung, um den Remote Debugger zu starten.](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Starten der Debugsitzung](#BKMK_Start_the_debugging_session)

- [Starten des Debuggens (F5)](#BKMK_Start_debugging__F5_)

- [Starten des Debuggens (F5) jedoch verzögerter Anwendungsstart](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Starten einer installierten App im Debugger](#BKMK_Start_an_installed_app_in_the_debugger)

- [Anfügen des Debuggers an eine laufende App](#BKMK_Attach_the_debugger_to_a_running_app_)

  - [Festlegen, dass die APP im Debugmodus ausgeführt wird](#BKMK_Set_the_app_to_run_in_debug_mode)

  - [Fügen Sie den Debugger an.](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a> Die einfache Methode zum Starten des Debuggens

1. Öffnen Sie in Visual Studio die Anwendungsprojektmappe.

2. Drücken Sie F5.

   In Visual Studio wird die Anwendung mit dem angefügten Debugger erstellt und gestartet. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist. Weitere Informationen finden Sie unter [Navigieren in einer Debugsitzung (XAML und c#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a> Konfigurieren der Debugsitzung

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Öffnen Sie die Eigenschaften Seite Debuggen für das Projekt.

1. Wählen Sie im Projektmappen-Explorer das Projekt aus. Wählen Sie im Kontextmenü **Eigenschaften**aus.

2. Öffnen Sie dazu die Debugeigenschaftenseite für das Projekt.

    - Wählen Sie für Visual C#- und Visual Basic-Anwendungen **Debuggen**aus.

         ![Debug-Eigenschaften Seite für C&#35; &#47; VB-Projekt](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - Erweitern Sie für Visual C++-Anwendungen den Knoten **Konfigurationseigenschaften**  , und wählen Sie dann **Debugging**aus.

         ![C&#43;&#43; Windows Store-App-Debugging (Eigenschaften Seite)](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a> Buildkonfigurationsoptionen auswählen

1. Wählen Sie in der Liste **Konfiguration** den Eintrag **Debuggen** oder **Aktive Konfiguration**aus.

2. Wählen Sie in der Liste **Plattform** die Zielplattform aus, in der der Build erfolgen soll. In den meisten Fällen ist **Any CPU** (**Alle Plattformen** in Visual C++) die beste Wahl.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a> Auswählen des Bereitstellungsziels
 ![Gilt nur für Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Sie können eine Windows Store-App auf dem Visual Studio-Computer, im Visual Studio-Simulator auf dem lokalen Computer oder auf einem Remotegerät bereitstellen und debuggen.

- Wählen Sie auf der Eigenschaftenseite **Debuggen** für C#- und Visual Basic-Apps das Ziel für das Projekt in der Liste **Zielgerät** aus.

- Wählen Sie auf der Eigenschaftenseite **Debuggen** für C++-Apps das Ziel in der Liste **Zu startender Debugger** aus.

  Wählen Sie eine der Optionen aus:

|Option|Beschreibung|
|-|-|
|**Lokaler Computer**|Debuggen Sie die Anwendung in der aktuellen Sitzung auf dem lokalen Computer. Siehe [Ausführen von Windows Store-Apps auf dem lokalen Computer](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulator**|Debuggen Sie die Anwendung im Visual Studio-Simulator für [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] -Apps. Der Simulator ist ein Desktopfenster mit dem Sie Gerätefunktionen wie z. B. die Fingereingabe und Gerätedrehung debuggen können, die nicht auf dem lokalen Computer verfügbar sind. Weitere Informationen finden Sie [unter Ausführen von Windows Store-Apps im Simulator](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Remotecomputer**|Debuggen Sie die Anwendung auf einem Gerät, das mit dem lokalen Computer über ein Intranet oder direkt über ein Ethernetkabel verbunden ist. Zum Remotedebuggen müssen die Visual Studio-Remotetools installiert sein und auf dem Remotegerät ausgeführt werden. Siehe [Ausführen von Windows Store-Apps auf einem Remote Computer](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Wenn Sie **Remotecomputer**auswählen, geben Sie den Namen oder die IP-Adresse des Remotecomputers auf eine der folgenden Weisen an:

- Geben Sie den Namen oder die IP-Adresse des Remotecomputers ein.

  - Geben Sie für C#- und Visual Basic-Anwendungen den Namen oder die IP-Adresse im Feld **Remotecomputer** ein.

  - Geben Sie für C++-Anwendungen den Namen oder die IP-Adresse im Feld **Computername** ein.

- Wählen Sie dann den Remotecomputer im Dialogfeld **Remotedebuggerverbindung auswählen** aus.

   So öffnen Sie das Dialogfeld

  - Wählen Sie für C#- und Visual Basic-Anwendungen **Suchen**aus.

  - Wählen Sie für C++-apps im Feld **Computer Name** den Pfeil nach unten aus, und wählen Sie aus **\<Locate...>** .

    ![Dialogfeld „Remoteverbindung“](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > Im Dialogfeld **remotedebuggerverbindung auswählen** werden Computer angezeigt, die sich auf dem lokalen Subnetz befinden, sowie Computer, die über ein Ethernet-Kabel direkt mit dem Visual Studio-Computer verbunden sind. Um einen anderen Computer anzugeben, geben Sie den Namen im Feld **Computername** ein.

  ![Gilt nur für Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Sie können Windows Phone Store-Apps auf einem Gerät oder einem der Visual Studio Phone Emulatoren bereitstellen und debuggen. Wählen Sie das Gerät oder den Emulator aus der Liste der **Zielgeräte** .

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Auswahl des zu verwendenden Debuggers
 In der Standardeinstellung erfolgt in Visual Studio ein Debuggen für verwalteten Code in C#- und Visual Basic-Anwendungen.

 Für C#- und Visual Basic-Anwendungen können Sie sowohl den verwalteten als auch den systemeigenen C/C++-Code der Anwendung debuggen. Aktivieren Sie das Kontrollkästchen **Debuggen von nicht verwaltetem Code aktivieren** , um systemeigenen Code in der Debugsitzung einzuschließen.

 In der Standardeinstellung erfolgt in Visual Studio das Debuggen von systemeigenem Code von C++-Anwendungen.

 Für C++-Apps können Sie zusätzlich zum oder anstelle des systemeigenen Codes bestimmte Codetypen debuggen, die sich in den Komponenten der App befinden. Sie geben den zu debuggenden Code in der Liste **Debuggertyp** auf der Eigenschaftenseite **Debuggen** des App-Projekts an.

 Wählen Sie einen dieser Debugger in der Liste **Anwendungsprozesse** aus:

|Debuggertyp|BESCHREIBUNG|
|-|-|
|**Nur Skript**|Für das Debuggen des JavaScript-Codes der Anwendung. Verwalteter und systemeigener Code werden ignoriert.|
|**Nur systemeigen**|Für das Debuggen des systemeigenen C/C++-Codes der Anwendung. Verwalteter und JavaScript-Code werden ignoriert.|
|**Nur verwaltet**|Für das Debuggen des verwalteten Codes der Anwendung. JavaScript- und systemeigener C/C++-Code werden ignoriert.|
|**Gemischt (verwaltet und systemeigen)**|Für das Debuggen des systemeigenen C/C++- und des verwalteten Codes der Anwendung. JavaScript-Code wird ignoriert.|
|**Nur GPU**|Debuggen von systemeigenem C++-Code, der auf einer Grafikverarbeitungseinheit (GPU) ausgeführt wird.|

 ![Gilt nur für Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

 Für Windows Phone Store-Apps können Sie den Debugger für Hintergrundprozesse auch aus dem **Hintergrundaufgabenprozess**wählen.

### <a name="optional-delay-starting-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_the_debug_session"></a> Optionale Verzögertes Starten der Debugsitzung
 In der Standardeinstellung wird die Anwendung in Visual Studio sofort gestartet, wenn Sie das Debuggen starten. Sie können zudem eine Debugsitzung starten, den Start der App jedoch verzögern. Wenn Sie diese Option auswählen, wird die Anwendung im Debugger gestartet, wenn diese über den Bildschirm, einen Aktivierungsvertrag oder von einem anderen Prozess oder eine Methode gestartet wird. Der Start einer App wird auch verzögert, wenn beim Debuggen einer Hintergrundaufgabe die App selbst nicht ausgeführt wird.

 Um den Start der App zu verzögern, können Sie folgende Schritte durchführen:

- Wählen Sie für Visual C#- und Visual Basic-Apps auf der Eigenschaftenseite **Debuggen** die Option **Eigenen Code zunächst nicht starten sondern debuggen** aus.

- Wählen Sie für Visual C++-Apps auf der Eigenschaftenseite **Debuggen** in der Liste **Anwendung starten** die Option **Ja** aus.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> (Optional) Netzwerkloopbacks deaktivieren
 ![Gilt nur für Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Aus Sicherheitsgründen wird einer im Standardverfahren installierten Windows Store-App nicht erlaubt, Netzwerkaufrufe an das Gerät auszuführen, auf dem sie installiert wurde. Standardmäßig wird durch die Visual Studio-Bereitstellung eine Ausnahme von dieser Regel für die bereitgestellte App erstellt. Diese Ausnahme ermöglicht das Testen von Kommunikationsverfahren auf einem einzelnen Computer. Bevor Sie die App an Windows Store senden, sollten Sie die App ohne die Ausnahme testen.

 So entfernen Sie die Netzwerkloopbackausnahme

- Bei Visual C#- und Visual Basic-Apps deaktivieren Sie auf der Eigenschaftenseite **Debuggen** das Kontrollkästchen **Netzwerkloopback zulassen** .

- Bei Visual C++-Apps wählen Sie auf der Eigenschaftenseite **Debuggen** in der Liste **Netzwerkloopback zulassen** den Eintrag **Nein** aus.

### <a name="optional-reinstall-the-app-when-you-start-debugging"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (Optional) Installieren Sie die Anwendung neu, wenn Sie das Debuggen starten.
 Um Probleme zu bestimmen, die mit der Installation und Erstkonfiguration der Visual C#- oder Visual Basic-App zusammenhängen, wählen Sie auf der Eigenschaftenseite **Debuggen** die Option **Paket deinstallieren und anschließend neu installieren**  aus, um eine ursprüngliche Installation beim Debugstart neu zu erstellen. Diese Option ist nicht für Visual C++-Projekte verfügbar.

### <a name="optional-disable-authentication-requirement-to-start-the-remote-debugger"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (Optional) Deaktivieren Sie zum Starten des Remotedebuggers die Authentifizierungsanforderung.
 ![Gilt nur für Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Standardmäßig müssen Sie zum Auszuführen des Remotedebuggers Anmeldeinformationen angeben.

> [!IMPORTANT]
> Sie haben die Möglichkeit, den Remotedebugger im Modus "Keine Authentifizierung" auszuführen, hiervon wird jedoch dringend abgeraten. In diesem Modus gibt es keine Netzwerksicherheit. Wählen Sie den Modus "Ohne Authentifizierung" nur aus, wenn Sie sicher sind, dass das Netzwerk nicht durch bösartigen oder feindlichen Datenverkehr gefährdet ist.

 Um die Authentifizierungsanforderung zu entfernen, gehen Sie wie folgt vor:

1. Bei Visual C#- und Visual Basic-Apps deaktivieren Sie auf der Eigenschaftenseite **Debuggen** das Kontrollkästchen **Authentifizierung verwenden** .

2. Bei Visual C++-Apps wählen Sie auf der Eigenschaftenseite **Debuggen** in der Liste **Authentifizierung erforderlich** den Eintrag **Nein** aus.

   [Inhalt](#BKMK_In_this_topic)

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a> Starten der Debugsitzung

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a> Debuggen starten (F5)
 Wenn Sie im Menü **Debuggen** die Option **Debuggen starten** (Tastatur: F5) auswählen, startet Visual Studio die APP mit dem angefügten Debugger. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine Ausnahme auftritt, oder bis die Anwendung beendet ist.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Starten des Debuggens (F5), verzögertes Starten der APP
 Sie können die App so einrichten, dass sie im Debugmodus ausgeführt wird, sie aber mit einer anderen Methode als dem Debugger starten. Beispielsweise, um den über das Startmenü ausgeführten Start der App zu debuggen, oder um einen Hintergrundprozess aus der App zu debuggen, ohne sie zu starten. Um den App-Start zu verzögern, gehen Sie folgendermaßen vor:

- Auf der Eigenschaftenseite **Debugging** der App (**Debuggen** in Visual C++)

  - Wählen Sie für Visual C#- und Visual Basic-Anwendungen **Eigenen Code zunächst nicht starten sondern debuggen**aus.

  - Wählen Sie für Visual C++-Anwendungen in der Liste **Anwendung starten** die Option **Ja** aus.

- Wählen Sie im Menü **Debuggen** die Option **Debuggen starten** (Tastatur: F5).

- Starten Sie die Anwendung vom Startmenü aus, über einen Ausführungsvertrag oder von einer anderen Prozedur.

  Die Anwendung wird im Debugmodus gestartet. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.

  . Weitere Informationen zum Debuggen von Hintergrundaufgaben finden Sie unter Triggern, fortsetzen [und Hintergrundereignisse für Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Starten einer installierten App im Debugger
 Wenn Sie das Debugging mit F5 beginnen, erstellt Visual Studio die App, stellt sie bereit, aktiviert den Debugmodus für die App und startet sie. Um eine App zu starten, die bereits auf dem Gerät installiert ist, verwenden Sie das Dialogfeld "Installiertes App-Paket debuggen". Diese Prozedur ist nützlich, wenn Sie eine App debuggen müssen, die aus dem Windows Store installiert wurde, oder wenn Sie zwar über die Quelldateien der App, nicht jedoch über ein Visual Studio-Projekt für die App verfügen. So kann beispielsweise ein benutzerdefiniertes Buildsystem vorhanden sein, das keine Visual Studio-Projekte oder -Projektmappen verwendet.

 Die App kann auf dem lokalen Gerät oder einem Remotegerät installiert sein.  Sie können die App sofort starten oder festlegen, dass sie im Debugger ausgeführt wird, wenn ein anderer Prozess oder eine andere Methode sie startet, z. B. das Startmenü oder ein Aktivierungskontrakt. Auch um einen Hintergrundprozess zu debuggen, können Sie festlegen, dass die App im Debugmodus ausgeführt wird. Weitere Informationen finden Sie unter [aussetzen von Triggern, fortsetzen und Hintergrund Ereignissen für Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Um festzulegen, dass die App im Debugmodus ausgeführt wird, gehen sie folgendermaßen vor:

> [!NOTE]
> Die App darf nicht ausgeführt werden, wenn Sie mit dieser Prozedur beginnen.

1. Wählen Sie im Menü **Debuggen** die Option **Debuggen Installed App Package**.

2. Wählen Sie eine der folgenden Optionen aus der Liste:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Lokaler Computer**  |                                                                                                                Debuggen Sie die Anwendung in der aktuellen Sitzung auf dem lokalen Computer. Siehe [Ausführen von Windows Store-Apps auf dem lokalen Computer](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulator**    | Debuggen Sie die Anwendung im Visual Studio-Simulator für [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] -Apps. Der Simulator ist ein Desktopfenster mit dem Sie Gerätefunktionen wie z. B. die Fingereingabe und Gerätedrehung debuggen können, die nicht auf dem lokalen Computer verfügbar sind. Weitere Informationen finden Sie [unter Ausführen von Windows Store-Apps im Simulator](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Remotecomputer** |                          Debuggen Sie die Anwendung auf einem Gerät, das mit dem lokalen Computer über ein Intranet oder direkt über ein Ethernetkabel verbunden ist. Zum Remotedebuggen müssen die Visual Studio-Remotetools installiert sein und auf dem Remotegerät ausgeführt werden. Siehe [Ausführen von Windows Store-Apps auf einem Remote Computer](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Wählen Sie die App aus der Liste **Installierte App-Pakete** .

4. Wählen Sie die Debug-Engine aus der Liste **Diesen Codetyp debuggen** .

5. (Optional) Wählen Sie **Eigenen Code zunächst nicht starten sondern debuggen** , um die App zu debuggen, wenn Sie von einer anderen Methode gestartet wird, oder um einen Hintergrundprozess zu debuggen.

   Wenn Sie auf **Starten**&gt; klicken, wird die App gestartet oder festgelegt, dass sie im Debugmodus ausgeführt werden soll.

### <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Anfügen des Debuggers an eine ausgeführte Anwendung
 Um den Debugger an eine [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] -App anzufügen, müssen Sie im Manager für debugfähige Pakete festlegen, dass die App im Debugmodus ausgeführt wird. Der Manager für debugfähige Pakete wird mit den Visual Studio-Remotetools installiert.

 Das Anfügen des Debuggers an eine App ist nützlich zum Debuggen einer bereits installierten App, wie beispielsweise eine App, die aus dem [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]installiert wurde. Das Anfügen ist erforderlich, wenn Sie über die Quelldateien für die Anwendung, nicht jedoch über ein Visual Studio-Projekt für die Anwendung verfügen. So kann beispielsweise ein benutzerdefiniertes Buildsystem vorhanden sein, das keine Visual Studio-Projekte oder -Projektmappen verwendet.

 Für das Anfügen des Debuggers an eine App sind folgende Schritte erforderlich:

1. Legen Sie die Ausführung der Anwendung im Debugmodus fest. Dies muss erfolgen, wenn die Anwendung nicht ausgeführt wird.

2. Starten Sie die App. Sie können die App über den Startbildschirm, einen Ausführungsvertrag oder eine andere Methode starten.

3. Fügen Sie den Debugger an die ausgeführte Anwendung an.

#### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Festlegen der Ausführung der Anwendung im Debugmodus

1. Installieren Sie die Visual Studio-Remotetools auf dem Gerät, auf dem die Anwendung installiert wurde. Weitere Informationen finden Sie unter [Installieren der Remotetools](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Suchen Sie auf dem Startbildschirm nach `Debuggable Package Manager` , und starten Sie diesen.

     Es wird ein ordnungsgemäß für das AppxDebug-Cmdlet konfiguriertes PowerShell-Fenster angezeigt.

3. Um das Debuggen einer Anwendung zu aktivieren, müssen Sie den PackageFullName-Bezeichner der App angeben. Um eine Liste aller Apps anzuzeigen, die PackageFullName enthält, geben Sie an der PowerShell-Eingabeaufforderung `Get-AppxPackage` ein.

4. Geben Sie an der PowerShell-Eingabeaufforderung `Enable-AppxDebug` *PackageFullName* ein, wobei *PackageFullName* der PackageFullName-Bezeichner der App ist.

#### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a> Debugger anfügen
 So fügen Sie den Debugger an

1. Klicken Sie im Menü **Debuggen** auf **An den Prozess anhängen**.

    Das Dialogfeld **An den Prozess anhängen** wird angezeigt.

2. Um an eine Anwendung auf einem Remotegerät anzufügen, geben Sie das Remotegerät im Feld **Qualifizierer** an. Sie können:

   - Geben Sie im Feld **Qualifizierer** den gewünschten Anzeigenamen ein.

   - Wählen Sie den Pfeil nach unten im Feld **Qualifizierer** aus, und wählen Sie das Gerät aus einer Liste von Geräten aus, die Sie zu zuvor angefügt haben.

   - Wählen Sie **Suchen** aus, um das Gerät aus einer Liste von Geräten im lokalen Subnetz auszuwählen.

3. Geben Sie den Typ des Codes an, den Sie im Feld **Anfügen an** debuggen möchten.

    Wählen Sie **Auswählen** aus, und gehen Sie folgendermaßen vor:

   - Wählen Sie **Zu debuggenden Codetyp automatisch bestimmen**aus.

   - Wählen Sie **Diese Codetypen debuggen** und anschließend mindestens einen Typ aus der Liste aus.

4. Wählen Sie in der Liste **Verfügbare Prozesse**  den App-Prozess aus.

5. Wählen Sie **Anfügen**aus.

   Der Debugger wird in Visual Studio an den Prozess angefügt. Die Ausführung wird fortgeführt, bis ein Haltepunkt erreicht wird, bis Sie diese manuell anhalten, bis eine unbehandelte Ausnahme auftritt, oder bis die Anwendung beendet ist.

   [Inhalt](#BKMK_In_this_topic)

## <a name="see-also"></a>Weitere Informationen
 [Debuggen von apps in Visual Studio Navigieren in](../debugger/debug-store-apps-in-visual-studio.md) [einer Debugsitzung (XAML und c#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
