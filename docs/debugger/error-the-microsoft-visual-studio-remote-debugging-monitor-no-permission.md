---
title: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer verfügt nicht über die Berechtigung, eine Verbindung mit diesem Computer herzustellen
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7baed5cc2c4c8dbaa01cd3dfadc386b6db1834c
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851085"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer verfügt nicht über die Berechtigung, eine Verbindung mit diesem Computer herzustellen

Dieser Fehler tritt auf, wenn der Benutzer, der versucht, den Visual Studio-Remotedebugmonitor (msvsmon) auszuführen, kein Konto auf dem lokalen Computer hat. Dieser Fehler kann beim Remotedebuggen mit der Legacydebug-Engine auftreten.

## <a name="to-fix-this-problem"></a>So beheben Sie dieses Problem

- Fügen Sie dem Hostcomputer mit dem Visual Studio Debugger ein Benutzerkonto mit demselben Namen und Kennwort wie dem Benutzerkonto hinzu, unter dem msvsmon auf dem Remotecomputer ausgeführt wird.

   \- oder -

- Führen Sie msvsmon als Benutzer aus, der berechtigt ist, auf dem lokalen Computer Aufrufe durchzuführen. Dies bedeutet, dass der Benutzer ein Domänenbenutzer sein und Administratorrechte auf dem msvsmon-Computer besitzen muss. Sie haben zwei Möglichkeiten, um das Benutzerkonto zum Ausführen von msvsmon anzugeben:

  - Klicken Sie mit der rechten Maustaste auf das msvsmon-Symbol, und wählen Sie im Kontextmenü **Ausführen als** aus

    \- oder -

  - Führen Sie an der Eingabeaufforderung `runas.exe` aus.

## <a name="see-also"></a>Siehe auch

- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)