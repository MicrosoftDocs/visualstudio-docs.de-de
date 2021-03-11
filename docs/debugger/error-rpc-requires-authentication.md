---
description: Der Visual Studio-Debugger kann keine Verbindung mit dem Remotecomputer herstellen.
title: RPC verlangt Authentifizierung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
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
ms.openlocfilehash: f22998bc1c71a242b985739b2b92ba9743535d83
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146716"
---
# <a name="error-rpc-requires-authentication"></a>Fehler: RPC verlangt Authentifizierung
Der Visual Studio-Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Auf dem lokalen Computer ist eine RPC-Richtlinie aktiviert, die das Remotedebugging verhindert.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Führen Sie `\`*windir*`\system32\regedt32.exe` aus.

2. Suchen Sie nach `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`, und löschen Sie den Eintrag.

3. Starten Sie den Computer neu, damit die Registrierungsänderung wirksam wird.

4. Wenn das Problem weiterhin besteht, bitten Sie Ihren Domänenadministrator, die Gruppenrichtlinieneinstellung **Computerkonfiguration > Administrative Vorlagen > System > Remoteprozeduraufruf > Einschränkungen für nicht authentifizierte RPC-Clients** zu überprüfen.
