---
title: Remotedebugger-Portzuweisungen | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über Portzuweisungen für den Visual Studio Remote Debugger auf 32-Bit- und 64-Bit-Betriebssystemen sowie in Azure. Darüber hinaus wird der Ermittlungsport behandelt.
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40081f276dc9649cf448bf00e80d11fc80f58f47
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204825"
---
# <a name="remote-debugger-port-assignments"></a>Remotedebugger - Portzuweisungen
Der Visual Studio-Remotedebugger kann als Anwendung oder als Hintergrunddienst ausgeführt werden. Bei der Ausführung als Anwendung wird standardmäßig der folgende Port zugewiesen:
::: moniker range=">=vs-2019"
- Visual Studio 2019: 4024
::: moniker-end
- Visual Studio 2017: 4022

- Visual Studio 2015: 4020

- Visual Studio 2013: 4018

- Visual Studio 2012: 4016

Die Nummer des Ports, der dem Remotedebugger zugewiesen ist, wird also für jede Version um 2 erhöht. Sie können bei Bedarf eine andere Portnummer festlegen. Das Festlegen von Portnummern wird in einem späteren Abschnitt erläutert.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Remotedebugger-Port bei 32-Bit-Betriebssystemen

::: moniker range=">=vs-2019"
 TCP 4024 (Visual Studio 2019) ist der Hauptport und für alle Szenarien erforderlich. Sie können ihn über die Befehlszeile oder das Fenster "Remotedebugger" konfigurieren.
::: moniker-end
::: moniker range="vs-2017"
 TCP 4022 (Visual Studio 2017) ist der Hauptport und für alle Szenarien erforderlich. Sie können ihn über die Befehlszeile oder das Fenster "Remotedebugger" konfigurieren.
::: moniker-end

 Klicken Sie im Fenster „Remotedebugger“ auf **Extras > Optionen**, und legen Sie die Nummer für den TCP/IP-Port fest.

 Starten Sie von der Befehlszeile aus den Remotedebugger über die Option **/port**: **msvsmon /port \<port number>** .

 Alle Remotedebugger-Befehlszeilenoptionen finden Sie in der Hilfe zum Remotedebugging (drücken Sie F1, oder klicken Sie im Fenster „Remotedebugger“ auf **Hilfe** > **Verwendung**).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Remotedebugger-Port bei 64-Bit-Betriebssystemen
::: moniker range=">=vs-2019"
 Beim Starten der 64-Bit-Version des Remotedebuggers wird standardmäßig der Hauptport (4024) verwendet.  Wenn Sie einen 32-Bit-Prozess debuggen, startet die 64-Bit-Version des Remotedebuggers eine 32-Bit-Remotedebuggerversion auf Port 4025 (die Nummer des Hauptports, inkrementiert um 1). Wenn Sie den 32-Bit-Remotedebugger ausführen, wird Port 4024 und nicht Port 4025 verwendet.
::: moniker-end
::: moniker range="vs-2017"
 Beim Starten der 64-Bit-Version des Remotedebuggers wird standardmäßig der Hauptport (4022) verwendet.  Wenn Sie einen 32-Bit-Prozess debuggen, startet die 64-Bit-Version des Remotedebuggers eine 32-Bit-Remotedebuggerversion auf Port 4023 (die Nummer des Hauptports, inkrementiert um 1). Wenn Sie den 32-Bit-Remotedebugger ausführen, wird Port 4022 und nicht Port 4023 verwendet.
:::moniker-end

 Dieser Port ist über die Befehlszeile konfigurierbar: **Msvsmon /wow64port \<port number>** .

## <a name="the-discovery-port"></a>Port für die Ermittlung
 UDP 3702 wird für die Suche nach ausgeführten Instanzen des Remotedebuggers im Netzwerk verwendet (z. B. bei **Suchen** im Dialogfeld **An den Prozess anhängen** ). Er wird nur für die Ermittlung von Computern verwendet, auf denen der Remotedebugger ausgeführt wird, und ist daher optional, wenn Sie den Computernamen oder die IP-Adresse des Zielcomputers auf andere Weise ermitteln können. Da dies der Standardport für die Ermittlung ist, kann die Portnummer nicht konfiguriert werden.

 Wenn Sie die Ermittlung nicht aktivieren möchten, können Sie msvsmon von der Befehlszeile aus mit deaktivierter Ermittlung starten:  **Msvsmon /nodiscovery**.

## <a name="remote-debugger-ports-on-azure"></a>Remotedebugger-Ports in Azure
 Die folgenden Ports werden vom Remotedebugger in Azure verwendet. Die Ports im Clouddienst werden den Ports auf den einzelnen virtuellen Computern zugeordnet. Bei allen Ports handelt es sich um TCP-Ports.

|Verbindung|Port im Clouddienst|Port auf virtuellem Computer|
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarderx86|31401|31399|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)
