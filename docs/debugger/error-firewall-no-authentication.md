---
title: Firewall und „Keine Authentifizierung“ | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.noauth
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
ms.openlocfilehash: cdd1b0bc56c0316d3a79cf59f744a7e2b0a2aece
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871610"
---
# <a name="error-firewall-no-authentication"></a>Fehler: Firewall und „Keine Authentifizierung“
Die Internetverbindungsfirewall auf dem Remotecomputer wurde nicht für das Remotedebuggen eingerichtet. Für das Remotedebuggen mit `No Authentication` muss der Ausnahmenliste die Datei msvsmon.exe hinzugefügt werden. Es ist möglicherweise auch erforderlich, einige IPSEC-Anschlüsse zu öffnen.

> [!NOTE]
> Der Remotedebugger kann die Windows Firewall automatisch konfigurieren. Wenn eine andere Firewall als die Windows Firewall verwendet wird, wie z. B. eine Software- oder Hardwarefirewall eines Drittanbieters, muss die Firewall manuell konfiguriert werden, um das Remotedebugging zu ermöglichen. Lassen Sie hierzu Verkehr für die TCP/IP-Ports zu, die von msvsmon.exe abgehört werden. Standardmäßig handelt es sich hierbei um Ports 4018 und 4019, wobei 4018 auf allen Betriebssystemen und 4019 wird nur unter Windows x64 verwendet wird, um Debugging von x86-Prozessen zu ermöglichen.

 Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).