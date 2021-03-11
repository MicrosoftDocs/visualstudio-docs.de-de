---
title: Fehler bei der Kerberos-Authentifizierung | Microsoft-Dokumentation
description: Dieser Fehler tritt auf, wenn der Visual Studio-Remotedebugmonitor unter dem lokalen Systemkonto oder dem Netzwerkdienstkonto ausgeführt wird.
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
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
ms.openlocfilehash: 41ffc4e5cb71c78462c9dbfd18472a4fc4e57c7d
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466237"
---
# <a name="error-kerberos-authentication-failed"></a>Fehler: Fehler bei der Kerberos-Authentifizierung
Beim Versuch, das Remotedebuggen auszuführen, kann die folgende Fehlermeldung ausgegeben werden:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 Dieser Fehler tritt auf, wenn der Visual Studio-Remotedebugmonitor unter dem lokalen Systemkonto oder dem Netzwerkdienstkonto ausgeführt wird. Der Remotedebugger muss unter einem dieser Konten eine Verbindung für die Kerberos-Authentifizierung herstellen, um die Kommunikation mit dem Visual Studio Debugger-Hostcomputer zu ermöglichen.

 Unter den folgenden Bedingungen ist die Kerberos-Authentifizierung nicht verfügbar:

- Entweder der Zielcomputer oder der Debuggerhostcomputer befindet sich in einer Arbeitsgruppe anstatt in einer Domäne

   \- oder -

- Kerberos wurde auf dem Domänencontroller deaktiviert

  Wenn die Kerberos-Authentifizierung nicht verfügbar ist, ändern Sie das zum Ausführen des Visual Studio-Remotedebugmonitors verwendete Konto. Die erforderlichen Schritte werden hier beschrieben: [Fehler: Der Visual Studio Remote Debugger-Dienst auf dem Zielcomputer kann die Verbindung mit diesem Computer nicht wiederherstellen](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

  Wenn beide Computer mit derselben Domäne verbunden sind und weiterhin diese Meldung ausgegeben wird, stellen Sie sicher, dass der Name des Debuggerhostcomputers vom DNS auf dem Zielcomputer ordnungsgemäß aufgelöst wird. Siehe folgendes Verfahren.

### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>So überprüfen Sie, ob der Name des Debuggerhostcomputers vom DNS auf dem Zielcomputer ordnungsgemäß aufgelöst wird

1. Klicken Sie auf dem Zielcomputer auf das Menü **Start**, zeigen Sie auf **Zubehör**, und klicken Sie dann auf **Eingabeaufforderung**.

2. Geben Sie im Fenster **Eingabeaufforderung** Folgendes ein:

    ```cmd
    ping <debugger_host_computer_name>
    ```

3. Die erste Zeile der `ping`-Antwort enthält den vollständigen Computernamen und die vollständige IP-Adresse, die vom DNS für den angegebenen Computer zurückgegeben wurden.

4. Öffnen Sie auf dem Debuggerhostcomputer das Fenster **Eingabeaufforderung**, und führen Sie `ipconfig` aus.

5. Vergleichen Sie die IP-Adresswerte.

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
