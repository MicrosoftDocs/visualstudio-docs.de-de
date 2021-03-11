---
description: Diese Fehlermeldung bedeutet, dass Visual Studio auf dem Remotecomputer keine passende Instanz des Visual Studio-Remotedebugmonitors finden konnte.
title: Der Microsoft Visual Studio-Remotedebugmonitor (MSVSMON.EXE) wird anscheinend auf dem Remotecomputer nicht ausgeführt.
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.server_machine_no_default
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c40e36548e17bbd4d37192364667a369bdcbb47
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146793"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Fehler: Der Microsoft Visual Studio-Remotedebugmonitor (MSVSMON.EXE) wird anscheinend auf dem Remotecomputer nicht ausgeführt.
Diese Fehlermeldung bedeutet, dass Visual Studio auf dem Remotecomputer keine passende Instanz des Visual Studio-Remotedebugmonitors finden konnte. Der Visual Studio-Remotedebugmonitor muss installiert werden, damit das Remotedebuggen funktioniert. Informationen zum Herunterladen und Einrichten des Remotedebuggers finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

> [!IMPORTANT]
> Wenn Sie der Ansicht sind, dass Sie diese Meldung aufgrund eines Produktfehlers erhalten haben, [melden Sie das Problem an Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md). Wenn Sie weitere Hilfe benötigen, erfahren Sie unter [Talk to Us](../ide/feedback-options.md) , wie Sie Kontakt mit Microsoft aufnehmen.

## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Ich habe diese Meldung beim Debuggen in Visual Studio 2010 oder einer früheren Version erhalten
 Wenn Sie Visual Studio 2010 oder eine frühere Version von Visual Studio verwenden, kann dieser Fehler auch darauf hinweisen, dass die Datei- und Druckerfreigabe nicht aktiviert ist. Weitere Informationen zu diesem Problem finden Sie im Abschnitt zur Visual Studio 2010-Version in dieser Dokumentation: [Fehler: Der Microsoft Visual Studio-Remotedebugmonitor (MSVSMON.EXE) wird auf dem Remotecomputer nicht ausgeführt. (Visual Studio 2010)](/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100))

## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Ich habe diese Meldung beim lokalen Debuggen erhalten
 Wenn Sie diese Meldung beim lokalen Debuggen erhalten, kann dies an Ihrer Antivirussoftware oder einer Drittanbieter-Firewall liegen. Visual Studio ist eine 32-Bit-Anwendung, die zum Debuggen von 64-Bit-Anwendungen die 64-Bit-Version des Remotedebuggers verwendet. Die beiden Prozesse kommunizieren über das lokale Netzwerk innerhalb des lokalen Computers. Kein Datenverkehr verlässt den Computer, aber es ist möglich, dass Drittanbieter-Sicherheitssoftware die Kommunikation blockiert.

 In den folgenden Abschnitten sind einige andere Gründe aufgelistet, warum Sie diese Meldung erhalten haben und wie Sie das Problem beheben können.

## <a name="the-remote-machine-is-not-reachable"></a>Der Remotecomputer ist nicht erreichbar.
 Versuchen Sie, eine [ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) -Anforderung an den Remotecomputer zu senden. Wenn Sie keine Antwort auf die Ping-Anforderung erhalten, können auch die Remotetools keine Verbindung herstellen. Versuchen Sie, den Remotecomputer neu zu starten, und stellen Sie sicher, dass er ordnungsgemäß im Netzwerk konfiguriert ist.

## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Die Version des Remotedebuggers stimmt nicht mit der Version von Visual Studio überein
 Die lokal ausgeführte Version von Visual Studio muss mit der Version des Remotedebugmonitors übereinstimmen, der auf dem Remotecomputer ausgeführt wird. Um dieses Problem zu beheben, laden Sie die passende Version des Remotedebugmonitors herunter, und installieren Sie sie. Wechseln Sie zum [Download Center](https://www.microsoft.com/download) , um die richtige Version des Remotedebuggers zu finden.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Der lokale Computer und der Remotecomputer weisen unterschiedliche Authentifizierungsmodi auf
 Der lokale Computer und der Remotecomputer müssen den gleichen Authentifizierungsmodus verwenden. Um dieses Problem zu beheben, müssen Sie sicherstellen, dass beide Computer den gleichen Authentifizierungsmodus verwenden. Weitere Informationen zu den Authentifizierungsmodi finden Sie unter [Übersicht über die Windows-Authentifizierung](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Der Remotedebugger wird unter einem anderen Benutzerkonto ausgeführt
 Mit einer der folgenden Möglichkeiten können Sie dieses Problem beheben:

- Sie können den Remotedebugger beenden und unter dem Konto, das Sie auf dem lokalen Computer verwenden, erneut starten.

- Sie können den Remotedebugger über die Befehlszeile mit dem Parameter **/allow \<username>** starten: `msvsmon /allow <username@computer>`.

- Sie können dem Benutzer Remotedebuggerberechtigungen (im Remotedebuggerfenster unter **Extras > Berechtigungen**) hinzufügen.

- Wenn Sie die Methoden in den vorangehenden Schritten nicht verwenden können, können Sie allen Benutzern das Remotedebuggen erlauben. Öffnen Sie im Remotedebuggerfenster das Dialogfeld **Extras > Optionen**. Bei der Auswahl von   **Keine Authentifizierung** können Sie **Allen Benutzern das Debugging ermöglichen** aktivieren. Sie sollten diese Option jedoch nur verwenden, wenn es keine andere Möglichkeit gibt oder Sie sich in einem privaten Netzwerk befinden.

## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Die Firewall auf dem Remotecomputer lässt keine eingehenden Verbindungen mit dem Remotedebugger zu
 Die Firewalls auf dem Visual Studio-Computer und dem Remotecomputer müssen für die Kommunikation zwischen Visual Studio und Remotedebugger konfiguriert sein. Weitere Informationen zu den Ports, die vom Remotedebugger verwendet werden, finden Sie unter [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Weitere Informationen zum Konfigurieren der Windows-Firewall finden Sie unter [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="anti-virus-software-is-blocking-the-connections"></a>Verbindungen werden durch Antivirussoftware blockiert
 Die Windows-Antivirussoftware lässt Remotedebuggerverbindungen zu, von mancher Drittanbieter-Antivirussoftware werden sie jedoch blockiert. Informieren Sie sich in der Dokumentation Ihrer Antivirussoftware darüber, wie Sie diese Verbindungen zulassen.

## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Die Netzwerksicherheitsrichtlinie blockiert die Kommunikation zwischen dem Remotecomputer und Visual Studio
 Stellen Sie sicher, dass durch die Netzwerksicherheit keine Kommunikation blockiert wird. Weitere Informationen zur Sicherheitsrichtlinie für Windows-Netzwerke finden Sie unter [Sicherheitsrichtlinieneinstellungen](/windows/device-security/security-policy-settings/security-policy-settings).

## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Das Netzwerk ist überlastet und unterstützt daher zurzeit kein Remotedebuggen
 Möglicherweise müssen Sie das Remotedebuggen zu einem anderen Zeitpunkt ausführen oder die Arbeiten im Netzwerk für einen anderen Zeitpunkt planen.

## <a name="more-help"></a>Weitere Hilfe
 Klicken Sie im Fenster des Remotedebuggers auf **Hilfe > Verwendung**, um weitere Informationen zum Remotedebugger einschließlich Befehlszeilenoptionen zu erhalten. Wenn Sie diesen nicht geöffnet haben, können Sie die Webseite anzeigen, indem Sie die folgende Zeile in ein **Datei-Explorer**-Fenster kopieren. (Sie müssen \<Visual Studio installation directory> durch den Speicherort Ihrer Visual Studio-Installation ersetzen.)

 res:// *\<Visual Studio installation directory>* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
