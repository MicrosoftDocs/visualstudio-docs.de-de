---
title: Remotedebuggen eines C#- oder VB-Projekts | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Visual Studio C#- oder Visual Basic-Anwendung von einem Remotecomputer aus debuggen, indem Sie diese schrittweisen Anleitungen befolgen.
ms.custom:
- remotedebugging"=
- seodec18
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
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e814e442fe740c6a5090a43a2d76fb50168ea205
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934636"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Remotedebuggen eines C#- oder VB-Projekts in Visual Studio
Zum Debuggen einer Visual Studio-Anwendung, die auf einem anderen Computer bereitgestellt wurde, installieren und führen Sie die Remotetools auf dem Computer aus, auf dem Sie die App bereitstellen möchten, konfigurieren Sie das Projekt für die Verbindung mit dem Remotecomputer über Visual Studio, und führen Sie die App dann aus.

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

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a> Remotedebuggen des Projekts
Der Debugger kann Visual C#- oder Visual Basic-Desktopanwendungen nicht auf einem Remotecomputer bereitstellen, aber Sie können diese trotzdem wie folgt remotedebuggen. Im folgenden Verfahren wird davon ausgegangen, dass Sie die Anwendung auf einem Computer mit dem Namen **MJO-DL** debuggen möchten, wie in der Abbildung gezeigt.

1. Erstellen Sie ein WPF-Projekt mit dem Namen **MyWpf**.

2. Legen Sie einen leicht erreichbaren Haltepunkt an einer beliebigen Stelle im Code fest.

    Beispielsweise können Sie einen Haltepunkt in einem Schaltflächenhandler festlegen. Öffnen Sie hierzu die Datei „MainWindow.xaml“, und fügen Sie ein Schaltflächensteuerelement aus der Toolbox hinzu. Doppelklicken Sie dann auf die Schaltfläche, um ihren Handler zu öffnen.

3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt und dann auf **Eigenschaften**.

4. Wählen Sie auf der Seite **Eigenschaften** die Registerkarte **Debuggen** aus.

    ![Screenshot der Registerkarte „Debuggen“ in den Eigenschaften des Projektmappen-Explorers von Visual Studio. Die Eigenschaft „Remotecomputer verwenden“ ist auf „MJO-DL:4022“ festgelegt.](../debugger/media/remotedebuggercsharp.png)

5. Stellen Sie sicher, dass das Textfeld **Arbeitsverzeichnis** leer ist.

6. Wählen Sie **Remotecomputer verwenden** aus, und geben Sie **ihrcomputername:port** in das Textfeld ein. (Die Portnummer wird im Fenster des Remotedebuggers angezeigt. Die Portnummer wird für jede Version von Visual Studio um 2 erhöht.)

    Verwenden Sie in diesem Beispiel Folgendes:
    ::: moniker range=">=vs-2019"
    **MJO-DL:4024** für Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL:4022** für Visual Studio 2017
    ::: moniker-end

7. Stellen Sie sicher, dass **Debuggen von nativem Code aktivieren** nicht aktiviert ist.

8. Erstellen Sie das Projekt.

9. Erstellen Sie auf dem Remotecomputer einen Ordner mit dem gleichen Pfad wie der **Debug**-Ordner auf Ihrem Visual Studio-Computer: **\<source path>\MyWPF\MyWPF\bin\Debug**.

10. Kopieren Sie die ausführbare Datei, die Sie soeben erstellt haben, vom Visual Studio-Computer in den neu erstellten Ordner auf dem Remotecomputer.

    > [!CAUTION]
    > Führen Sie keine Änderungen und keine Neuerstellung des Codes aus (andernfalls müssen Sie diesen Schritt wiederholen). Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

    Sie können das Projekt manuell kopieren oder XCopy, Robocopy, PowerShell oder andere Optionen verwenden.

11. Stellen Sie sicher, dass der Remotedebugger auf dem Zielcomputer ausgeführt wird (wenn dies nicht der Fall ist, suchen Sie im Menü **Start** nach **Remotedebugger**). Das Remotedebuggerfenster sieht folgendermaßen aus.

     ![Screenshot des Visual Studio 2017-Remotedebuggerfensters. Eine Aktion ist aufgelistet, die anzeigt, dass der Debugger auf dem Zielcomputer ausgeführt wird.](../debugger/media/remotedebuggerwindow.png)

12. Starten Sie das Debuggen in Visual Studio (**Debuggen > Debuggen starten** oder **F5**).

13. Geben Sie Netzwerkanmeldeinformationen ein, wenn Sie dazu aufgefordert werden, um eine Verbindung mit dem Remotecomputer herzustellen.

     Die erforderlichen Anmeldeinformationen unterscheiden sich abhängig von der Sicherheitskonfiguration Ihres Netzwerks. Auf einem Domänencomputer können Sie z. B den Domänennamen und das Kennwort eingeben. Auf einem Computer, der kein Domänencomputer ist, können Sie den Computernamen und einen gültigen Benutzerkonto Namen wie <strong>MJO-DL\name@something.com</strong> zusammen mit dem richtigen Kennwort eingeben.

     Das Hauptfenster der WPF-Anwendung sollte auf dem Remotecomputer geöffnet sein.

14. Nehmen Sie ggf. Maßnahmen zum Erreichen des Breakpoints vor. Es sollte angezeigt werden, dass der Haltepunkt aktiv ist. Falls nicht, wurden die Symbole für die Anwendung nicht geladen. Wiederholen Sie den Vorgang, und wenn dies nicht funktioniert, rufen Sie Informationen zum Laden und zur Fehlerbehandlung von Symbolen unter [Verstehen von Symboldateien und den Symboleinstellungen von Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/) ab.

15. Auf dem Visual Studio-Computer sollte angezeigt werden, dass die Ausführung am Haltepunkt angehalten wurde.

    Wenn bestimmte Dateien, die keine Codedateien sind, von der Anwendung benötigt werden, müssen Sie diese in das Visual Studio-Projekt einbeziehen. Erstellen Sie einen Projektordner für die zusätzlichen Dateien (klicken Sie im **Projektmappen-Explorer** auf **Hinzufügen > Neuer Ordner**.) Fügen Sie die Dateien anschließend zum Ordner hinzu (klicken Sie im **Projektmappen-Explorer** auf **Hinzufügen > Vorhandenes Element**, und wählen Sie dann die Dateien aus). Legen Sie auf der Seite **Eigenschaften** der einzelnen Dateien die Option **In Ausgabeverzeichnis kopieren** auf **Immer kopieren** fest.

## <a name="set-up-debugging-with-remote-symbols"></a>Einrichten des Debuggings mit Remotesymbolen

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Siehe auch
- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remotedebugger - Portzuweisungen](../debugger/remote-debugger-port-assignments.md)
- [Remotedebuggen von ASP.NET auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)