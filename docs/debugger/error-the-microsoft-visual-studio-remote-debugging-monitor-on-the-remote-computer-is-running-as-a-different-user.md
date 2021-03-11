---
title: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgeführt
titleSuffix: ''
description: Diese Meldung wird angezeigt, wenn Sie sich im Modus "Keine Authentifizierung debuggen" befinden, und der Benutzer, der "msvsmon" gestartet hat, nicht mit dem Benutzer identisch ist, der Visual Studio ausführt.
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cee8ea9442ab88c280a11a0b73d74cac6888e9f9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146703"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgeführt
Wenn Sie versuchen, Remotedebuggen auszuführen, wird möglicherweise folgende Fehlermeldung angezeigt:

 Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgeführt.

## <a name="cause"></a>Ursache
 Diese Meldung wird angezeigt, wenn Sie sich im Modus "Keine Authentifizierung debuggen" befinden, und der Benutzer, der "msvsmon" gestartet hat, nicht mit dem Benutzer identisch ist, der Visual Studio ausführt.

## <a name="solution"></a>Lösung
 Die sicherste und beste Lösung besteht darin, den Remotedebugmonitor (msvsmon.exe) unter demselben Benutzerkonto auszuführen wie Visual Studio. Wenn dies nicht möglich ist, können Sie den Remotedebugmonitor unter dem anderen Konto ausführen, indem Sie im Dialogfeld **Optionen** des Remotedebugmonitors die Option **Allow any user to debug** (Allen Benutzern das Debuggen erlauben) aktivieren.

> [!CAUTION]
> Indem anderen Benutzern die Berechtigung zum Herstellen einer Verbindung gewährt wird, besteht die Möglichkeit, dass unbeabsichtigt eine Verbindung mit der falschen Remotedebugsitzung hergestellt wird. Das Debuggen im Modus **Keine Authentifizierung** ist immer unsicher und sollte daher nur mit Vorsicht verwendet werden.

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
