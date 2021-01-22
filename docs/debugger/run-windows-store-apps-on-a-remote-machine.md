---
title: Debuggen von UWP-Apps auf Remotecomputern | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit Visual Studio eine UWP-App (Universelle Windows-Plattform) remote auf einem anderen Computer oder Gerät ausführen, debuggen, profilen und testen.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: a28769237f0c1b0078e9c9c117695e68e5b521ac
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204955"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Debuggen von UWP-Apps auf Remotecomputern in Visual Studio

Sie können mit Visual Studio UWP-Apps (Universelle Windows-Plattform) auf einem anderen Computer oder Gerät ausführen, debuggen, profilen und testen. Das Ausführen einer UWP-App auf einem Remotecomputer ist besonders dann hilfreich, wenn der Visual Studio-Computer keine UWP-spezifischen Funktionen wie Toucheingabe, Geolocation oder physische Ausrichtung unterstützt.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Erforderliche Komponenten

Für das Debuggen einer UWP-App auf einem Remotegerät in Visual Studio müssen folgende Voraussetzungen erfüllt sein:

- Das Visual Studio-Projekt muss für das Remotedebuggen konfiguriert sein.
- Der Remotecomputer und der Visual Studio-Computer müssen über ein Netzwerk oder direkt über ein USB-Kabel oder Ethernetkabel miteinander verbunden sein. Das Debugging über das Internet wird nicht unterstützt.
- Sie müssen sowohl auf dem Visual Studio-Computer als auch auf dem Remotecomputer den [Entwicklermodus aktivieren](/windows/uwp/get-started/enable-your-device-for-development).
- Auf Remotecomputern muss Remotetools für Visual Studio ausgeführt werden.
  - In einigen Windows 10-Versionen werden die Remotetools automatisch gestartet und ausgeführt. Ist dies bei Ihnen nicht der Fall, [installieren Sie Remotetools für Visual Studio, und führen Sie die Tools aus](#BKMK_download).
  - Auf Windows 10 Mobile-Geräten sind die Remotetools nicht erforderlich und werden auch nicht unterstützt.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Konfigurieren eines Visual Studio-Projekts für das Remotedebuggen
<a name="BKMK_DirectConnect"></a> Geben Sie in den **Eigenschaften** des Projekts das Remotegerät an, mit dem eine Verbindung hergestellt werden soll. Die Einstellungen unterscheiden sich je nach Programmiersprache.

> [!CAUTION]
> Standardmäßig ist für Windows 10-Remoteverbindungen auf der Eigenschaftenseite **Universell (unverschlüsseltes Protokoll)** als **Authentifizierungstyp** festgelegt. Möglicherweise müssen Sie **Keine Authentifizierung** festlegen, um eine Verbindung mit dem Remotedebugger herzustellen. Die Protokolle **Universell (unverschlüsseltes Protokoll)** und **Keine Authentifizierung** stellen keine Netzwerksicherheit bereit. Daher sind die zwischen dem Entwicklungs- und dem Remotecomputer weitergegebenen Daten anfällig. Verwenden Sie diese Authentifizierungstypen nur in vertrauenswürdigen Netzwerken, bei denen Sie sicher sind, dass keine Gefährdung durch schädlichen oder bösartigen Datenverkehr besteht.
>
>Wenn Sie **Windows-Authentifizierung** als **Authentifizierungstyp** auswählen, müssen Sie sich beim Debuggen beim Remotecomputer anmelden. Der Remotedebugger muss ebenfalls im Modus **Windows-Authentifizierung** ausgeführt werden, und zwar mit dem Benutzerkonto des Visual Studio-Computers.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Konfigurieren eines C#- oder Visual Basic-Projekts für das Remotedebuggen

1. Klicken Sie in Visual Studio im **Projektmappen-Explorer** auf das C#- oder Visual Basic-Projekt, dann auf das Symbol für **Eigenschaften**, und drücken Sie **ALT**+**EINGABETASTE**. Alternativ können Sie mit der rechten Maustaste auf das Projekt und anschließend mit der linken Maustaste auf **Eigenschaften** klicken.

1. Klicken Sie auf die Registerkarte **Debuggen**.

1. Wählen Sie unter **Zielgerät** **Remotecomputer** für einen Remotecomputer oder **Gerät** für ein direkt verbundenes Windows 10 Mobile-Gerät aus.

1. Geben Sie bei einem Remotecomputer den Netzwerknamen oder die IP-Adresse in das Feld **Remotecomputer** ein, oder klicken Sie im [Dialogfeld Remoteverbindungen](#remote-connections) auf **Suchen**, um nach dem Gerät zu suchen.

    ![Verwaltete Projekteigenschaften für Remotedebuggen](../debugger/media/vsrun_managed_projprop_remote.png "Verwaltete Debugprojekteigenschaften")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Konfigurieren eines C++-Projekts für das Remotedebuggen

1. Klicken Sie in Visual Studio im **Projektmappen-Explorer** auf das C++-Projekt, dann auf das Symbol für **Eigenschaften**, und drücken Sie **ALT**+**EINGABETASTE**. Alternativ können Sie mit der rechten Maustaste auf das Projekt und anschließend mit der linken Maustaste auf **Eigenschaften** klicken.

1. Klicken Sie auf die Registerkarte **Debuggen**.

3. Wählen Sie unter **Zu startender Debugger:** **Remotecomputer** für einen Remotecomputer oder **Gerät** für ein direkt verbundenes Windows 10 Mobile-Gerät aus.

1. Geben Sie bei einem Remotecomputer den Netzwerknamen oder die IP-Adresse in das Feld **Computername** ein. Alternativ können Sie die entsprechende Dropdownliste aufklappen und auf **Suchen** klicken, um über das [Dialogfeld Remoteverbindungen](#remote-connections) nach dem Gerät zu suchen.

    ![C++-Projekteigenschaften für Remotedebugging](../debugger/media/vsrun_cpp_projprop_remote.png "Projekteigenschaften für C++-Debugging")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> Verwenden des Dialogfelds „Remoteverbindungen“

Im Dialogfeld **Remoteverbindungen** können Sie entweder nach einem bestimmten Remotecomputernamen oder einer bestimmten IP-Adresse suchen oder per Klick auf das Aktualisierungssymbol mit dem gebogenen Pfeil die automatische Erkennung von Verbindungen verwenden. Das Dialogfeld sucht nur nach Geräten im lokalen Subnetz, auf denen derzeit der Remotedebugger ausgeführt wird. Nicht alle Geräte können im Dialogfeld **Remoteverbindungen** erkannt werden.

 ![Dialogfeld „Remoteverbindung“](../debugger/media/vsrun_selectremotedebuggerdlg.png "Dialogfeld „Remoteverbindungen“")

>[!TIP]
>Wenn Sie mit einem Remotegerät über den Namen keine Verbindung herstellen können, versuchen Sie es mit der IP-Adresse. Ermitteln Sie die IP-Adresse, indem Sie auf dem Remotegerät **ipconfig** in ein Befehlsfenster eingeben. Die IP-Adresse wird als **IPv4-Adresse** angezeigt.

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> Herunterladen und Installieren der Remotetools für Visual Studio

Damit Visual Studio auf einem Remotecomputer Apps debuggen kann, muss Remotetools für Visual Studio darauf ausgeführt werden.

- Auf Windows 10 Mobile-Geräten sind die Remotetools nicht erforderlich und werden auch nicht unterstützt.
- Bei Windows 10-PCs mit Creators Update (Version 1703) und höher installieren Windows 10 Xbox-, IoT- und HoloLens-Geräte automatisch die Remotetools, wenn Sie die App bereitstellen.
- Bei PCs mit Windows 10-Versionen vor Creators Update müssen Sie die Remotetools vor dem Debuggen manuell auf dem Remotecomputer herunterladen, installieren und ausführen.

**So laden Sie die Remotetools herunter und installieren sie**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> Konfigurieren der Remotetools

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> UWP-Apps remote debuggen

Das Remotedebuggen funktioniert wie das lokale Debuggen.

1. Stellen Sie sicher, dass bei Windows 10-Versionen vor Creators Update der Remotedebugmonitor (*msvsmon.exe*) auf dem Remotegerät ausgeführt wird.

1. Stellen Sie sicher, dass auf dem Visual Studio-Computer neben dem grünen Pfeil auf der Symbolleiste das richtige Debugziel angezeigt wird (**Remotecomputer** oder **Gerät**).

1. Starten Sie das Debuggen, indem Sie auf **Debuggen** > **Debuggen starten** klicken, auf **F5** drücken oder auf den grünen Pfeil auf der Symbolleiste klicken.

   Das Projekt wird neu kompiliert und anschließend auf dem Remotegerät bereitgestellt und gestartet. An Haltepunkten unterbricht der Debugger die Ausführung, und Sie können die Optionen Einzelschritt, Prozedurschritt und Rücksprung auf den Code anwenden.

1. Klicken Sie bei Bedarf auf **Debuggen** > **Debuggen beenden**, oder drücken Sie **UMSCHALT**+**F5**, um das Debuggen zu beenden und die Remote-App zu schließen.

## <a name="see-also"></a>Siehe auch
- [Advanced remote deployment options (Erweiterte Optionen für die Remotebereitstellung)](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Testen von UWP-Apps mit Visual Studio](../test/unit-test-your-code.md)
- [Debuggen von UWP-Apps in Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
