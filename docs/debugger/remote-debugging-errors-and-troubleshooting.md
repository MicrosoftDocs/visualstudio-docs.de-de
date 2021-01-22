---
title: 'Remotedebuggen: Fehler und Problembehandlung | Microsoft-Dokumentation'
description: Links zu häufigen Fehlern beim Remotedebuggen in Visual Studio. Hier erfahren Sie, wie Sie den Remotedebugger als Administrator ausführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0260f939c8f6b7e5bed77ec42a4720adf0a4c720
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205657"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Remotedebuggen – Fehler und Problembehandlung

Beim Remotedebuggen können folgende Fehler auftreten.

- [Fehler: Automatischer Einzelschritt auf dem Server nicht möglich](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Fehler: Der Microsoft Visual Studio-Remotedebugmonitor (MSVSMON.EXE) wird anscheinend auf dem Remotecomputer nicht ausgeführt.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Fehler: Remotecomputer wird im Dialogfeld „Remoteverbindungen“ nicht angezeigt](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Ausführen des Remotedebuggers als Administrator

Möglicherweise treten Probleme auf, wenn Sie den Remotedebugger nicht als Administrator ausführen. Es wird möglicherweise der folgende Fehler angezeigt: „Der Visual Studio Remote Debugger („MSVSMON.EXE“) verfügt nicht über ausreichende Berechtigungen, um diesen Prozess zu debuggen.“ Wenn Sie den Remotedebugger als Anwendung (nicht als Dienst) ausführen, wird möglicherweise ein Fehler zu einem [anderen Benutzerkonten](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) angezeigt.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Beim Ausführen des Remotedebuggers als Dienst

Wenn Sie den Remotedebugger als Dienst ausführen, wird aus verschiedenen Gründen empfohlen, ihn als Administrator auszuführen:

- Der Remotedebuggerdienst lässt nur Verbindungen von Administratoren zu, sodass **keine** neuen Sicherheitsrisiken entstehen, indem er als Administrator ausgeführt wird.

- Dadurch können Fehler verhindert werden, die auftreten, wenn der Visual Studio-Benutzer mehr Berechtigungen zum Debuggen eines Prozesses besitzt als der Remotedebugger selbst.

- Zum Vereinfachen der Einrichtung und Konfiguration des Remotedebuggers.

Obwohl es möglich ist, einen Debugvorgang auszuführen, ohne den Remotedebugger als Administrator auszuführen, müssen verschiedene Anforderungen erfüllt werden, damit dies ordnungsgemäß funktioniert, und häufig sind erweiterte Dienstkonfigurationsschritte erforderlich.

- Das Konto, das Sie auf dem Remotecomputer verwenden, muss über die Berechtigung **Anmelden als Dienst** verfügen. Weitere Informationen finden Sie in den Schritten unter „Hinzufügen von Anmelden als Dienst“ im Fehlerartikel zu [fehlerhaften Rückverbindungen](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

- Das Konto muss über Rechte zum Debuggen des Zielprozesses verfügen. Um diese Rechte zu erhalten, müssen Sie den Remotedebugger unter demselben Konto wie den zu debuggenden Prozess ausführen. (Die einfachere Alternative besteht darin, den Dienst als Administrator auszuführen.) 

- Das Konto muss in der Lage sein, eine Rückverbindung mit dem Visual Studio-Computer über das Netzwerk herzustellen (d. h. sich bei ihm zu authentifizieren). In einer Domäne ist es einfacher, eine Rückverbindung herzustellen, wenn der Remotedebugger unter den integrierten lokalen System- oder den Netzwerkdienstkonten oder einem Domänenkonto ausgeführt wird. Die integrierten Konten verfügen über erhöhte Sicherheitsberechtigungen, die ein Sicherheitsrisiko darstellen können.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Beim Ausführen des Remotedebuggers als Anwendung (normaler Modus)

Wenn Sie versuchen, den Debugger an Ihren eigenen Prozess ohne erhöhte Rechte (z. B. eine normale Anwendung) anzufügen, ist es unerheblich, ob Sie den Remotedebugger als Administrator ausführen.

Sie möchten den Remotedebugger in verschiedenen Szenarien als Administrator ausführen:

- Sie möchten ihn an Prozesse anfügen, die als anderer Benutzer ausgeführt werden (z. B. beim Debuggen von IIS).

- Sie versuchen, einen anderen Prozess zu starten, und der Prozess, den Sie starten möchten, ist ein Administrator.

Sie möchten ihn **nicht** als Administrator ausführen, wenn Sie Prozesse starten möchten, und der Prozess, den Sie starten möchten, sollte **kein** Administrator sein.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)