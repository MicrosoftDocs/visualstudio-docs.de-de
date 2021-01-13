---
title: Remotedebuggen eines C++-Projekts | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Visual Studio C++-Anwendung von einem Remotecomputer aus debuggen, indem Sie diese schrittweisen Anleitungen befolgen.
ms.custom: remotedebugging
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: a8d3b578e62b917a7553b42a04e53062c406c4fd
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815801"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Remotedebuggen eines C++-Projekts in Visual Studio
Zum Debuggen einer Visual Studio-Anwendung auf einem anderen Computer installieren und führen Sie die Remotetools auf dem Computer aus, auf dem Sie die App bereitstellen möchten, konfigurieren Sie das Projekt für die Verbindung mit dem Remotecomputer über Visual Studio, und stellen Sie die App dann bereit und führen sie aus.

![Remotedebuggerkomponenten](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Weitere Informationen zum Remotedebuggen von universellen Windows-Apps (UWP) finden Sie unter [Debuggen eines installierten App-Pakets](debug-installed-app-package.md).

## <a name="requirements"></a>Anforderungen

Der Remotedebugger wird unter Windows 7 und höher (kein Smartphone) und Windows Server-Versionen ab Windows Server 2008 Service Pack 2 unterstützt. Eine vollständige Liste der Anforderungen finden Sie unter [Anforderungen](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Das Debuggen zwischen zwei über einen Proxy verbundenen Computern wird nicht unterstützt. Das Debuggen über eine Verbindung mit hoher Latenz oder niedriger Bandbreite, z. B. DFÜ-Internetverbindung oder Internetverbindung über mehrere Länder hinweg, wird nicht empfohlen und schlägt möglicherweise fehl oder weist eine unzureichende Geschwindigkeit auf.

## <a name="download-and-install-the-remote-tools"></a>Herunterladen und Installieren der Remotetools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> In einigen Szenarien kann es am effizientesten sein, den Remotedebugger von einer Dateifreigabe aus auszuführen. Weitere Informationen finden Sie unter [Ausführen des Remotedebuggers von einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Einrichten des Remotedebuggers

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Wenn Sie Berechtigungen für weitere Benutzer hinzufügen, den Authentifizierungsmodus oder die Portnummer für den Remotedebugger ändern müssen, finden Sie weitere Informationen unter [Konfigurieren des Remotedebuggers](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a> Remotedebuggen eines C++-Projekts
 Im folgenden Verfahren lautet der Name und der Pfad des Projekts „C:\remotetemp\MyMfc“ und der Name des Remotecomputers **MJO-DL**.

1. Erstellen Sie eine MFC-Anwendung mit dem Namen **mymfc**.

2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle in der Anwendung fest, z.B. in **MainFrm.cpp** am Anfang von `CMainFrame::OnCreate`.

3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus. Öffnen Sie die Registerkarte **Debuggen**.

4. Legen Sie **Zu startender Debugger** auf **Remote-Windows-Debugger** fest.

    ![Screenshot der Registerkarte „Debuggen“ in den Eigenschaften des Projektmappen-Explorers von Visual Studio. Die Eigenschaft „Zu startender Debugger“ ist auf „Remote-Windows-Debugger“ festgelegt.](../debugger/media/remotedebuggingcplus.png)

5. Nehmen Sie die folgenden Änderungen an den Eigenschaften vor:

   |Einstellung|Wert|
   |-|-|
   |Remote-Befehl|C:\remotetemp\mymfc.exe|
   |Arbeitsverzeichnis|C:\remotetemp|
   |Remoteservername|MJO-DL:*Portnummer*|
   |Verbindung|Remote mit Windows-Authentifizierung|
   |Debuggertyp|Nur systemeigen|
   |Bereitstellungsverzeichnis|C:\remotetemp.|
   |Zusätzliche bereitzustellende Dateien|C:\data\mymfcdata.txt.|

    Wenn Sie zusätzliche Dateien bereitstellen (optional), muss der Ordner auf beiden Computern vorhanden sein.

6. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Projektmappe, und wählen Sie dann **Konfigurations-Manager** aus.

7. Aktivieren Sie für die Konfiguration **Debuggen** das Kontrollkästchen **Bereitstellen**.

    ![Screenshot des Konfigurations-Managers im Projektmappen-Explorer von Visual Studio. Die Konfiguration „Debuggen“ ist ausgewählt, und das Kontrollkästchen „Bereitstellen“ ist aktiviert.](../debugger/media/remotedebugcplusdeploy.png)

8. Starten Sie das Debuggen (wählen Sie **Debuggen > Debuggen starten** aus, oder drücken Sie **F5**).

9. Die ausführbare Datei wird automatisch auf dem Remotecomputer bereitgestellt.

10. Geben Sie Netzwerkanmeldeinformationen ein, wenn Sie dazu aufgefordert werden, um eine Verbindung mit dem Remotecomputer herzustellen.

     Die erforderlichen Anmeldeinformationen sind spezifisch für die Sicherheitskonfiguration Ihres Netzwerks. Beispielsweise können Sie auf einem Domänencomputer ein Sicherheitszertifikat auswählen oder den Domänennamen und das Kennwort eingeben. Auf einem Computer, der kein Domänencomputer ist, können Sie den Computernamen und einen gültigen Benutzerkonto Namen wie <strong>MJO-DL\name@something.com</strong> zusammen mit dem richtigen Kennwort eingeben.

11. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wird.

    > [!TIP]
    > Alternativ können die Dateien in einem getrennten Schritt bereitgestellt werden. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **mymfc**, und wählen Sie dann **Bereitstellen** aus.

    Wenn Sie Dateien verwenden, die keine Codedateien, aber für die Anwendung erforderlich sind, können Sie diese unter **Zusätzlich bereitzustellende Dateien** auf der Seite **Windows-Remotedebugger** angeben.

    Alternativ dazu können Sie die Dateien in Ihr Projekt einschließen und die Eigenschaft **Inhalt** auf der Seite **Eigenschaften** für jede Datei auf **Ja** festlegen. Diese Dateien werden in das **Bereitstellungsverzeichnis** kopiert, das auf der Seite **Windows-Remotedebugger** angegeben wird. Sie können auch den **Elementtyp** in **Datei kopieren** ändern und zusätzliche Eigenschaften angeben, wenn die Dateien in einen Unterordner des **Bereitstellungsverzeichnisses** kopiert werden müssen.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Siehe auch
- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger - Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)