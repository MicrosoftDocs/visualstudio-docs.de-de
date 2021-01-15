---
title: Die Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor konnte nicht hergestellt werden
description: In diesem Artikel werden die Fehlermeldung „Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor“ (Die Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor konnte nicht hergestellt werden) sowie mögliche Ursachen und Lösungsansätze beschrieben.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 04/14/2020
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc34a5f58f8bc3c47526cc8ba8516311e94f0631
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150833"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Die Verbindung mit dem Microsoft Visual Studio-Remotedebugmonitor konnte nicht hergestellt werden
Diese Fehlermeldung kann verschiedene Ursachen haben: Entweder der Remotedebugmonitor ist auf dem Remotecomputer nicht ordnungsgemäß eingerichtet, oder auf den Remotecomputer kann aufgrund von Netzwerkproblemen bzw. wegen einer Firewall nicht zugegriffen werden.

> [!IMPORTANT]
> Wenn Sie der Ansicht sind, dass Sie diese Meldung aufgrund eines Produktfehlers erhalten haben, [melden Sie das Problem](../ide/how-to-report-a-problem-with-visual-studio.md) an Visual Studio. Wenn Sie weitere Hilfe benötigen, erfahren Sie unter [Talk to Us](../ide/feedback-options.md) , wie Sie Kontakt mit Microsoft aufnehmen.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Was lautet die ausführliche Fehlermeldung?

Die Meldung `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` ist generisch. In der Regel ist in der Fehlerzeichenfolge eine genauere Meldung enthalten, die Ihnen helfen kann, die Ursache des Problems zu identifizieren oder nach einer genaueren Lösung zu suchen. Im folgenden finden Sie einige der häufigsten Fehlermeldungen, die an die Hauptfehlermeldung angefügt werden:

- [Der Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Der Debugger konnte den angegebenen Computernamen nicht auflösen](#cannot_connect)
- [Die Verbindungsanforderung wurde vom Remotedebugger abgelehnt](#rejected)
- [Die Verbindung mit dem Remoteendpunkt wurde beendet](#connection_terminated)
- [Ungültiger Zugriff auf Speicheradresse](#invalid_access)
- [Auf dem Remotecomputer wird kein Server mit dem angegebenen Namen ausgeführt](#no_server)
- [Der angeforderte Name war gültig, es wurden jedoch keine Daten mit dem angeforderten Typ gefunden](#valid_name)
- [Der Visual Studio Remote Debugger auf dem Zielcomputer kann die Verbindung mit diesem Computer nicht wiederherstellen](#cant_connect_back)
- [Zugriff verweigert](#access_denied)
- [Ein für ein Sicherheitspaket spezifischer Fehler ist aufgetreten](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a> Der Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Der Debugger konnte den angegebenen Computernamen nicht auflösen

Führen Sie die folgenden Schritte aus:

1. Vergewissern Sie sich, dass Sie einen gültigen Computernamen und eine gültige Portnummer im Dialogfeld **An den Prozess anhängen** oder in den Projekteigenschaften eingeben (Informationen zum Festlegen von Eigenschaften finden Sie unter [diesen Schritten](#server_incorrect)). Der Computername muss das folgende Format aufweisen:

    `computername:port`

    > [!NOTE]
    > Die Portnummer muss mit der [Portnummer des Remotedebuggers](../debugger/remote-debugger-port-assignments.md) übereinstimmen, der auf dem Zielcomputer *ausgeführt werden muss*.

2. Wenn der Computername nicht funktioniert, versuchen Sie es stattdessen mit der IP-Adresse und der Portnummer.

3. Stellen Sie sicher, dass die Version des Remotedebuggers, der auf dem Zielcomputer ausgeführt wird, mit Ihrer Version von Visual Studio übereinstimmt. Informationen zum Ermitteln der richtigen Version des Remotedebuggers finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

    > [!TIP]
    > Wenn Sie an den Prozess anfügen und eine Verbindung hergestellt haben, der gewünschte Prozess jedoch nicht angezeigt wird, aktivieren Sie das Kontrollkästchen **Prozesse aller Benutzer anzeigen**. Dadurch werden Prozesse angezeigt, wenn Sie unter einem anderen Benutzerkonto verbunden sind.

4. Wenn dieser Fehler durch diese Schritte nicht behoben wird, finden Sie weitere Informationen unter [Der Remotecomputer ist nicht erreichbar](#dns).

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a> Die Verbindungsanforderung wurde vom Remotedebugger abgelehnt

Vergewissern Sie sich im Dialogfeld **An den Prozess anhängen** oder in den Projekteigenschaften, dass der Name des Remotecomputers und die Portnummer mit dem Namen und der Portnummer übereinstimmen, die im Fenster des Remotedebuggers angezeigt werden. Falls dies nicht der Fall ist, beheben Sie das Problem und versuchen Sie es erneut.

Wenn diese Werte richtig sind und in der Meldung der Modus **Windows-Authentifizierung** angegeben ist, prüfen Sie, ob sich der Remotedebugger im richtigen Authentifizierungsmodus befindet (**Extras > Optionen**).

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a> Die Verbindung mit dem Remoteendpunkt wurde beendet

Wenn Sie eine Azure App Service-App debuggen, versuchen Sie den Befehl [Debugger anfügen](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) aus dem Cloud-Explorer oder Server-Explorer anstelle von **An den Prozess anhängen** zu verwenden.

Wenn Sie zum Debuggen **An den Prozess anhängen** verwenden:

- Vergewissern Sie sich im Dialogfeld **An den Prozess anhängen** oder in den Projekteigenschaften, dass der Name des Remotecomputers und die Portnummer mit dem Namen und der Portnummer übereinstimmen, die im Fenster des Remotedebuggers angezeigt werden. Falls dies nicht der Fall ist, beheben Sie das Problem und versuchen Sie es erneut.

- Wenn Sie versuchen, eine Verbindung über einen Hostnamen herzustellen, versuchen Sie stattdessen eine IP-Adresse.

- Überprüfen Sie das Anwendungsprotokoll auf dem Server (Ereignisanzeige unter Windows) auf ausführlichere Informationen, um das Problem zu beheben.

- Versuchen Sie andernfalls, Visual Studio mit Administratorrechten neu zu starten, und wiederholen Sie anschließend den Vorgang.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a> Ungültiger Zugriff auf Speicheradresse

Interner Fehler. Starten Sie Visual Studio neu, und wiederholen Sie den Vorgang.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a> Auf dem Remotecomputer wird kein Server mit dem angegebenen Namen ausgeführt

Visual Studio konnte keine Verbindung mit dem Remotedebugger herstellen. Diese Meldung kann aus verschiedenen Gründen auftreten:

- Der Remotedebugger wird möglicherweise unter einem anderen Benutzerkonto ausgeführt. Weitere Informationen finden Sie unter [diesen Schritten](#user_accounts).

- Der Port wird in der Firewall blockiert. Stellen Sie sicher, dass die Firewall [Ihre Anforderung nicht blockiert](#firewall), insbesondere, wenn Sie eine Firewall eines Drittanbieters verwenden.

- Die Version des Remotedebuggers stimmt nicht mit Visual Studio überein. Informationen zum Ermitteln der richtigen Version des Remotedebuggers finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a> Der angeforderte Name war gültig, es wurden jedoch keine Daten mit dem angeforderten Typ gefunden

Der Remotecomputer ist vorhanden, aber Visual Studio konnte keine Verbindung mit dem Remotedebugger herstellen. Diese Meldung kann aus verschiedenen Gründen auftreten:

- Ein DNS-Problem verhindert die Verbindung. Weitere Informationen finden Sie unter [diesen Schritten](#dns).

- Der Remotedebugger wird möglicherweise unter einem anderen Benutzerkonto ausgeführt. Führen Sie [folgende Schritte](#user_accounts) aus.

- Der Port wird in der Firewall blockiert. Stellen Sie sicher, dass die Firewall [Ihre Anforderung nicht blockiert](#firewall), insbesondere, wenn Sie eine Firewall eines Drittanbieters verwenden.

- Die Version des Remotedebuggers stimmt nicht mit Visual Studio überein. Informationen zum Ermitteln der richtigen Version des Remotedebuggers finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a> Der Visual Studio Remote Debugger auf dem Zielcomputer kann die Verbindung mit diesem Computer nicht wiederherstellen

Der Remotedebugger wird möglicherweise unter einem anderen Benutzerkonto ausgeführt. Öffnen Sie im Remotedebugger **Extras > Berechtigungen**, um den Benutzer zu den Berechtigungen des Remotedebuggers hinzuzufügen. Weitere Informationen finden Sie unter [Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt](#user_accounts).

Wenn in der Fehlermeldung auch eine Firewall erwähnt wird, verhindert die Firewall auf dem lokalen Computer möglicherweise die Kommunikation zwischen dem Remotecomputer und Visual Studio. Weitere Informationen finden Sie unter [diesen Schritten](#firewall).

## <a name="access-denied"></a><a name="access_denied"></a> Zugriff verweigert

Dieser Fehler kann auftreten, wenn Sie versuchen, von einem 32-Bit-Computer aus auf einem 64-Bit-Remotecomputer zu debuggen (nicht unterstützt).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a> Ein für ein Sicherheitspaket spezifischer Fehler ist aufgetreten

Möglicherweise handelt es sich hierbei um ein Legacy-Problem, das spezifisch für Windows XP und Windows 7 ist. Hier finden Sie weitere [Informationen](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Ursachen und Empfehlungen

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a> Der Remotecomputer ist nicht erreichbar

Wenn Sie keine Verbindung über den Namen des Remotecomputers herstellen können, versuchen Sie es stattdessen mit der IP-Adresse. Sie können `ipconfig` in einer Befehlszeile auf dem Remotecomputer verwenden, um die IPv4-Adresse abzurufen. Wenn Sie eine Hostdatei verwenden, überprüfen Sie, ob sie ordnungsgemäß konfiguriert ist.

Wenn dies nicht möglich ist, überprüfen Sie, ob der Remotecomputer über das Netzwerk erreichbar ist ([Ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10))-Befehl an den Remotecomputer senden). Das Remotedebuggen über das Internet wird nicht unterstützt, außer in einigen Microsoft Azure-Szenarien.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a> Der Servername ist falsch, oder die Software von Drittanbietern beeinträchtigt den Remotedebugger

Überprüfen Sie in Visual Studio die Projekteigenschaften, und stellen Sie sicher, dass der Servername richtig ist. Weitere Informationen finden Sie unter den Themen [C# und Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) und [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Öffnen Sie für ASP.NET abhängig vom Projekttyp **Eigenschaften / Web / Server** oder **Eigenschaften / Debuggen**.

> [!NOTE]
> Wenn Sie an den Prozess anhängen, werden die Remoteeinstellungen in den Projekteigenschaften nicht verwendet.

Wenn der Servername richtig ist, blockiert möglicherweise Ihre Antivirensoftware oder eine Firewall eines Drittanbieters den Remotedebugger. Beim lokalen Debuggen kann dies auftreten, da Visual Studio eine 32-Bit-Anwendung ist und daher die 64-Bit-Version des Remotedebuggers zum Debuggen von 64-Bit-Anwendungen verwendet. Die 32-Bit- und 64-Bit-Prozesse kommunizieren über das lokale Netzwerk innerhalb des lokalen Computers. Kein Netzwerkdatenverkehr verlässt den Computer, aber es ist möglich, dass Drittanbieter-Sicherheitssoftware die Kommunikation blockiert.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a> Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt

Der Remotedebugger akzeptiert standardmäßig nur Verbindungen von dem Benutzer, der den Remotedebugger gestartet hat, sowie von den Mitgliedern der Gruppe „Administratoren“. Zusätzlichen Benutzern müssen explizit Berechtigungen erteilt werden.

Mit einer der folgenden Möglichkeiten können Sie dieses Problem beheben:

- Fügen Sie den Visual Studio-Benutzer zu den Berechtigungen des Remotedebuggers hinzu (wählen Sie im Fenster des Remotedebuggers **Extras > Berechtigungen**) aus.

- Starten Sie den Remotedebugger auf dem Remotecomputer unter demselben Benutzerkonto und mit demselben Kennwort neu, die Sie auf dem Visual Studio-Computer verwenden.

    > [!NOTE]
    > Wenn Sie den Remotedebugger auf einem Remoteserver ausführen, klicken Sie mit der rechten Maustaste auf die Remotedebugger-App, und wählen Sie **Als Administrator ausführen** aus (Sie können den Remotedebugger auch als Dienst ausführen). Wenn Sie ihn nicht auf einem Remoteserver ausführen, starten Sie ihn einfach normal.

- Sie können den Remotedebugger über die Befehlszeile mit dem Parameter **/allow \<username>** starten: `msvsmon /allow <username@computer>`.

- Alternativ können Sie allen Benutzern das Remotedebuggen gestatten. Öffnen Sie im Remotedebuggerfenster das Dialogfeld **Extras > Optionen**. Bei der Auswahl von   **Keine Authentifizierung** können Sie **Allen Benutzern das Debugging ermöglichen** aktivieren. Sie sollten diese Option jedoch nur ausprobieren, wenn die anderen Optionen fehlschlagen oder wenn Sie sich in einem privaten Netzwerk befinden.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a> Die Firewall auf dem Remotecomputer lässt keine eingehenden Verbindungen mit dem Remotedebugger zu
 Die Firewalls auf dem Visual Studio-Computer und dem Remotecomputer müssen für die Kommunikation zwischen Visual Studio und Remotedebugger konfiguriert sein. Weitere Informationen zu den Ports, die vom Remotedebugger verwendet werden, finden Sie unter [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Die Version des Remotedebuggers stimmt nicht mit der Version von Visual Studio überein
 Die lokal ausgeführte Version von Visual Studio muss mit der Version des Remotedebugmonitors übereinstimmen, der auf dem Remotecomputer ausgeführt wird. Um dieses Problem zu beheben, laden Sie die passende Version des Remotedebugmonitors herunter, und installieren Sie sie. Informationen zum Ermitteln der richtigen Version des Remotedebuggers finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Der lokale Computer und der Remotecomputer weisen unterschiedliche Authentifizierungsmodi auf
 Der lokale Computer und der Remotecomputer müssen den gleichen Authentifizierungsmodus verwenden. Um dieses Problem zu beheben, müssen Sie sicherstellen, dass beide Computer den gleichen Authentifizierungsmodus verwenden. Sie können den Authentifizierungsmodus ändern. Öffnen Sie im Remotedebuggerfenster das Dialogfeld **Extras > Optionen**.

 Weitere Informationen zu den Authentifizierungsmodi finden Sie unter [Übersicht über die Windows-Authentifizierung](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Verbindungen werden durch Antivirussoftware blockiert
 Die Windows-Antivirussoftware lässt Remotedebuggerverbindungen zu, von mancher Drittanbieter-Antivirussoftware werden sie jedoch blockiert. Informieren Sie sich in der Dokumentation Ihrer Antivirussoftware darüber, wie Sie diese Verbindungen zulassen.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Die Netzwerksicherheitsrichtlinie blockiert die Kommunikation zwischen dem Remotecomputer und Visual Studio
 Stellen Sie sicher, dass durch die Netzwerksicherheit keine Kommunikation blockiert wird. Weitere Informationen zur Sicherheitsrichtlinie für Windows-Netzwerke finden Sie unter [Sicherheitsrichtlinieneinstellungen](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Das Netzwerk ist überlastet und unterstützt daher zurzeit kein Remotedebuggen
 Möglicherweise müssen Sie das Remotedebuggen zu einem anderen Zeitpunkt ausführen oder die Arbeiten im Netzwerk für einen anderen Zeitpunkt planen.

## <a name="more-help"></a>Weitere Hilfe
 Um weitere Hilfe zum Remotedebugger zu erhalten, öffnen Sie die Hilfeseite des Remotedebuggers (**Hilfe > Verwendung** im Remotedebugger).

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)
