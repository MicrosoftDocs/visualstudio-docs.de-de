---
title: Bereitstellen von UWP-Apps | Microsoft-Dokumentation
description: Stellen Sie UWP-Apps (Universelle Windows-Plattform) über Visual Studio bereit. Geben Sie ein lokales Zielgerät oder ein Remotezielgerät für die Bereitstellung an. Erhalten Sie grundlegende Informationen zu Bereitstellungsoptionen.
ms.custom: SEO-VS-2020, seodec18
ms.date: 01/16/2018
ms.topic: conceptual
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
ms.openlocfilehash: 70b4d862b69eeb34028fb0f782cc5c8d6acbdbce
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728199"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Bereitstellen von UWP-Apps aus Visual Studio

Mit der Bereitstellungsfunktion von Visual Studio werden auf einem Zielgerät in Visual Studio erstellte UWP-Apps kompiliert und registriert. Wie genau die App registriert wird, hängt davon ob, ob sich das Zielgerät lokal oder remote befindet:

- Handelt es sich bei dem Ziel um einen lokalen Visual Studio-Computer, registriert Visual Studio die App vom Erstellungsordner aus.

- Handelt es sich bei dem Ziel um ein Remotegerät, kopiert Visual Studio die erforderlichen Dateien auf den Remotecomputer und registriert anschließend die App auf dem Gerät.

Die Bereitstellung erfolgt automatisch, wenn Sie Ihre App über Visual Studio mit der Option **Debuggen starten** (Tastatur: F5) oder **Starten ohne Debuggen** (Tastatur: STRG+F5) debuggen. Sie können die App auch manuell bereitstellen. Die manuelle Bereitstellung ist in folgenden Szenarios nützlich:

- Ad-Hoc-Tests auf einem lokalen oder Remotecomputer.

- Bereitstellen einer App, die eine andere App startet, welche Sie debuggen möchten.

- Bereitstellen einer App, deren Debugging beim Start durch eine andere App oder Methode erfolgen soll.

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Bereitstellen einer UWP-App
 Das manuelle Bereitstellen einer App ist ein einfacher Vorgang:

1. Wenn Sie ein Remotegerät bereitstellen, geben Sie den Namen oder die IP-Adresse des Geräts auf der Projekteigenschaftenseite des Startprojekts der App an. (Die entsprechenden Schritte sind weiter unten in diesem Thema aufgelistet.)

2. Wählen Sie auf der Debugger-Symbolleiste von Visual Studio das Bereitstellungsziel aus der Dropdownliste neben der Schaltfläche **Debuggen starten** aus.

     ![Ausführen auf lokalem Computer](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. Klicken Sie im Menü **Erstellen** auf **Bereitstellen**.

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Festlegen eines Remotegeräts

**Erforderliche Komponenten**

Bei Windows 10-Remotegeräten müssen Sie den [Entwicklermodus](/windows/uwp/get-started/enable-your-device-for-development) aktivieren. Auf Windows 10-Geräten mit Creators Update oder höher werden die Remotetools automatisch installiert, wenn Sie Ihre App bereitstellen. Weitere Informationen finden Sie unter [Debuggen eines installierten App-Pakets](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Bei Windows 10-Versionen vor Creators Update muss Remotetools für Visual Studio auf dem Remotegerät installiert sein, und der Remotedebugger muss ausgeführt werden.

Bei der Bereitstellung wird der Remotedebugger-Netzwerkkanal verwendet, um die App-Dateien an das Remotegerät zu senden.

#### <a name="to-specify-a-remote-device"></a>So legen Sie ein Remotegerät fest

1. Geben Sie auf der Debugeigenschaftenseite für das Startprojekt den Namen oder die IP-Adresse des Remotebereitstellungsziels an.

2. Wählen Sie zum Öffnen der Debugeigenschaftenseite das Projekt im Projektmappen-Explorer aus, und klicken Sie dann im Kontextmenü auf **Eigenschaften** .

3. Wählen Sie dann den Knoten **Debuggen** im Eigenschaftenseitenfenster aus.

4. Wählen Sie für **Zielgerät** **Remotecomputer** aus.

5. Klicken Sie unter **Remotecomputer** auf **Suchen**.

6. Sie können den Namen oder die IP-Adresse des Remotegeräts eingeben oder das Gerät im Dialogfeld **Remoteverbindung** auswählen.

    ![Dialogfeld „Remoteverbindung“](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    Im Dialogfeld **Remoteverbindung** werden die Geräte im Subnetz des lokalen Netzwerks angezeigt sowie die Geräte, die über ein Ethernetkabel direkt mit dem Visual Studio-Computer verbunden sind.

   **Angeben des Remotegeräts auf einer C++-Projektseite**

   ![C&#43;&#43;-Projekteigenschaften für Remotedebuggen](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Wählen Sie **Remote Debugger** in der Liste **Zu startender Debugger** aus.

8. Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Computername** ein. Oder verwenden Sie den nach unten weisenden Pfeil im Feld, um das Gerät im Dialogfeld "Remotedebuggerverbindung auswählen" auszuwählen.

   **Angeben des Remotegeräts auf einer Visual C#- oder Visual Basic-Projektseite**

   ![Verwaltete Projekteigenschaften für Remotedebuggen](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Wählen Sie in der Liste **Zielgerät** die Option **Remotecomputer** aus.

10. Geben Sie den Netzwerknamen des Remotegeräts in das Feld **Remotecomputer** ein oder klicken Sie auf **Suchen** , um das Gerät im Dialogfeld **Remotedebuggerverbindung auswählen** auszuwählen.

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Bereitstellungsoptionen

Sie können die folgenden Bereitstellungsoptionen auf der Debugeigenschaftenseite für das Startprojekt festlegen.

**Netzwerkloopback zulassen**

Aus Sicherheitsgründen sind auf standardmäßige Weise installierte UWP- oder [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps nicht berechtigt, Netzwerkaufrufe an das Gerät tätigen, auf dem sie installiert sind. Standardmäßig wird durch die Visual Studio-Bereitstellung eine Ausnahme von dieser Regel für die bereitgestellte App erstellt. Diese Ausnahme ermöglicht das Testen von Kommunikationsverfahren auf einem einzelnen Computer. Bevor Sie die App an [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]senden, sollten Sie die App ohne die Ausnahme testen.

So entfernen Sie die Netzwerkloopbackausnahme aus der App:

- Deaktivieren Sie auf der Eigenschaftenseite „Debuggen“ für C# und Visual Basic das Kontrollkästchen bei **Allow Network Loopback** (Netzwerkloopback zulassen).

- Legen Sie auf der Eigenschaftenseite „Debuggen“ für C++ den Wert für **Allow Network Loopback** (Netzwerkloopback zulassen) auf **Nein** fest.

**Eigenen Code zunächst nicht starten, sondern debuggen (C# und Visual Basic)/Anwendung starten (C++)**

So konfigurieren Sie den automatischen Start einer Debugsitzung beim Starten der Anwendung für die Bereitstellung:

- Aktivieren Sie auf der Eigenschaftenseite „Debuggen“ für C# und Visual Basic das Kontrollkästchen bei **Eigenen Code zunächst nicht starten, sondern debuggen**.

- Legen Sie auf der Eigenschaftenseite „Debuggen“ für C++ den Wert für **Anwendung starten** auf **Ja** fest.

## <a name="see-also"></a>Siehe auch

- [Advanced remote deployment options (Erweiterte Optionen für die Remotebereitstellung)](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Debuggen eines installierten App-Pakets](../debugger/debug-installed-app-package.md)
- [Ausführen von Apps aus Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
