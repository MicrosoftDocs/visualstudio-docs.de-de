---
title: Zeitlimitzeiträume für Testcontroller und Test-Agents
description: Hier erfahren Sie, wie Sie die Timeoutwerte für den Testcontroller und den Test-Agent ändern, indem Sie die zugehörigen XML-Konfigurationsdateien bearbeiten.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 3cca59fc165871e24269723635a1393d2f859178
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879565"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Vorgehensweise: Angeben von Zeitüberschreitungszeiträumen für Testcontroller und Test-Agents

Sowohl der Testcontroller als auch der Test-Agent verfügen über mehrere Timeouteinstellungen, die angeben, wie lange sie auf Antworten voneinander oder von einer Datenquelle warten, bevor ein Fehler ausgegeben wird. Unter bestimmten Umständen kann es notwendig sein, die Timeoutwerte entsprechend den Anforderungen der Topologie oder anderer Umgebungsprobleme zu bearbeiten. Um die Timeoutwerte zu ändern, bearbeiten Sie die XML-Konfigurationsdatei für den Testcontroller oder den Test-Agent wie in den folgenden Prozeduren beschrieben.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Zum Bearbeiten der verschiedenen Timeouteinstellungen eines Testcontrollers oder Test-Agents ändern Sie die folgenden Konfigurationsdateien unter Verwendung der Schlüsselnamen und -werte in den Tabellen:

- Testcontroller: *QTController.exe.config*

    |Schlüsselname|BESCHREIBUNG|Wert|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Die Anzahl von Sekunden, während der auf eine Pinganforderung des Agents gewartet wird, bevor die Verbindung als unterbrochen gilt.|"n" Sekunden.|
    |AgentSyncTimeoutInSeconds|Beim Starten eines synchronisierenden Testlaufs die Anzahl von Sekunden, während der auf die Synchronisierung aller Agents gewartet wird, bevor der Testlauf abgebrochen wird.|"n" Sekunden.|
    |AgentInitializeTimeout|Die Anzahl von Sekunden, während der am Anfang eines Testlaufs auf die Initialisierung aller Agents und der zugehörigen Datensammler gewartet wird. Dieser Wert muss bei Verwendung von Datensammlern ausreichend groß sein.|"n" Sekunden. Standard: "120 (zwei Minuten)".|
    |AgentCleanupTimeout|Die Anzahl von Sekunden, während der vor dem Abschließen des Testlaufs auf die Bereinigung aller Agents und zugehörigen Datensammler gewartet wird. Dieser Wert muss bei Verwendung von Datensammlern ausreichend groß sein.|"n" Sekunden. Standard: "120 (zwei Minuten)".|

- Test-Agent: *QTAgentService.exe.config*

    |Schlüsselname|BESCHREIBUNG|Wert|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Die Anzahl von Sekunden zwischen Verbindungsversuchen mit dem Controller.|"n" Sekunden. Standard: "30 (dreißig Sekunden)".|
    |RemotingTimeoutSeconds|Die maximale Dauer eines Remotingaufrufs in Sekunden.|"n" Sekunden. Standard: "600 (zehn Minuten)".|
    |StopTestRunCallTimeoutInSeconds|Die Anzahl von Sekunden, während der auf den Aufruf zum Beenden des Testlaufs gewartet wird.|"n" Sekunden. Standard: "120 (zwei Minuten)".|
    |GetCollectorDataTimeout|Die Anzahl von Sekunden, während der auf den Datensammler gewartet wird.|"n" Sekunden. Standard: "300 (fünf Minuten)".|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>So geben Sie Agent-Timeoutoptionen für einen Testcontroller an

1. Öffnen Sie die XML-Konfigurationsdatei *QTCcontroller.exe.config* im Verzeichnis *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Suchen Sie nach dem Tag `<appSettings>`.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

3. Bearbeiten Sie einen vorhandenen Wert für einen der Timeoutschlüssel des Testcontrollers. Sie können z. B. den Standardwert für den `AgentConnectionTimeoutInSeconds`-Schlüssel von zwei Minuten in drei Minuten ändern:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    - oder -

    Fügen Sie einen zusätzlichen Schlüssel hinzu, und geben Sie einen Timeoutwert an. Sie können z. B. den `AgentInitializeTimeout`-Schlüssel im Abschnitt `<appSettings>` hinzufügen und einen Wert von fünf Minuten angeben:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>So geben Sie Agent-Timeoutoptionen für einen Test-Agent an

1. Öffnen Sie die XML-Konfigurationsdatei *QTAgentService.exe.config* im Verzeichnis *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Suchen Sie nach dem Tag `<appSettings>`.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

3. Bearbeiten Sie einen vorhandenen Wert für einen der Timeoutschlüssel des Test-Agents. Sie können z. B. den Standardwert für den `ControllerConnectionPeriodInSeconds`-Schlüssel von 30 Sekunden in eine Minute ändern:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    - oder -

    Fügen Sie einen zusätzlichen Schlüssel hinzu, und geben Sie einen Timeoutwert an. Sie können z. B. den `RemotingTimeoutSeconds`-Schlüssel im Abschnitt `<appSettings>` hinzufügen und einen Wert von 15 Minuten angeben:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Siehe auch

- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)
- [Ändern von Einstellungen für die Auslastungstestprotokollierung](../test/modify-load-test-logging-settings.md)
- [Konfigurieren von Ports für Testcontroller und Test-Agents](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Vorgehensweise: Binden eines Testcontrollers oder Test-Agents an einen Netzwerkadapter](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
