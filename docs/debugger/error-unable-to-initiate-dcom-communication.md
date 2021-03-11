---
description: Bei einem Versuch des lokalen Computers, mit dem Remotecomputer zu kommunizieren, ist ein DCOM-Fehler aufgetreten.
title: Die DCOM-Kommunikation kann nicht initiiert werden | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: e7cf87815f7d6a09242d2b361db904094fcfcdea
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146443"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Fehler: Die DCOM-Kommunikation kann nicht initiiert werden
Bei einem Versuch des lokalen Computers, mit dem Remotecomputer zu kommunizieren, ist ein DCOM-Fehler aufgetreten. Dies wird durch eine Firewall auf dem Remoteserver oder durch eine nicht funktionierende Windows-Authentifizierung auf dem Remotecomputer verursacht.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Wenn auf dem Remotecomputer die Windows-Firewall aktiviert ist, finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md) Anweisungen zum Konfigurieren der Firewall zum lokalen Debuggen.

- Versuchen Sie zum Wiederherstellen der Windows-Authentifizierung, beide Computer neu zu starten. Überprüfen Sie die Ereignisprotokolle auf dem lokalen Computer und dem Remotecomputer auf Kerberos-Fehler, und klären Sie mit den Domänenadministratoren ab, ob bekannte Probleme vorliegen.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)
