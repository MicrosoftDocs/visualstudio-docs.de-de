---
title: Binden eines Testcontrollers/Test-Agents an einen Netzwerkadapter
description: Lernen Sie, einen Testcontroller oder Test-Agent mit einer IP-Adresse an einen Netzwerkadapter zu binden, falls er für mehrere Netzwerkadapter installiert ist.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: f35e870e625a0f494692d082494ee0c2511ffd8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966837"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Vorgehensweise: Binden eines Testcontrollers oder Test-Agents an einen Netzwerkadapter

Wenn ein Computer, auf dem die Testcontroller- oder Test-Agent-Software installiert ist, über mehrere Netzwerkadapter verfügt, müssen Sie anstelle des Namens des Computers die IP-Adresse angeben, um diesen Testcontroller bzw. Test-Agent zu identifizieren.

> [!WARNING]
> Beim Versuch, einen Test-Agent einzurichten, kann folgender Fehler auftreten:
>
> **Error 8110. Can not connect to the specified controller computer or access the controller object** (Fehler 8110. Verbindung zum angegebenen Controllercomputer konnte nicht hergestellt werden, oder auf das Controllerobjekt konnte nicht zugegriffen werden).
>
> Dieser Fehler kann bei der Installation des Testcontrollers auf einem Computer mit mehr als einem Netzwerkadapter auftreten. Es ist auch möglich, dass Agents erfolgreich installiert werden können und das Problem erst bei einem Testlauf auftritt.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Binden eines Testcontrollers an einen bestimmten Netzwerkadapter

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>So ermitteln Sie die IP-Adressen der Netzwerkadapter

1. Klicken Sie in Microsoft Windows auf **Start**, klicken Sie in das Feld **Suche starten**, geben Sie **cmd** ein, und drücken Sie dann die **EINGABETASTE**.

2. Geben Sie **ipconfig /all** ein.

     Die IP-Adressen für Ihre Netzwerkadapter werden angezeigt. Notieren Sie sich die IP-Adresse des Netzwerkadapters, an den Sie den Controller binden möchten.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>So binden Sie einen Netzwerkadapter an einen Testcontroller

1. Klicken Sie in Microsoft Windows auf **Start**, klicken Sie in das Feld **Suche starten**, geben Sie **services.msc** ein, und drücken Sie dann die **EINGABETASTE**.

     Das Dialogfeld **Dienste** wird angezeigt.

2. Klicken Sie im Ergebnisbereich in der Spalte **Name** mit der rechten Maustaste auf den Dienst **Visual Studio Test Controller**, und klicken Sie dann auf **Beenden**.

     - oder -

     Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und führen Sie den folgenden Befehl aus:

     `net stop vsttcontroller`

3. Öffnen Sie die XML-Konfigurationsdatei *QTCcontroller.exe.config* im Verzeichnis *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. Suchen Sie nach dem `<appSettings>`-Tag.

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

5. Fügen Sie im Abschnitt `BindTo` den `<appSettings>`-Schlüssel hinzu, um den zu verwendenden Netzwerkadapter anzugeben.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Starten Sie den Testcontrollerdienst. Führen Sie dazu den folgenden Befehl an einer Eingabeaufforderung aus:

    `net start vsttcontroller`

    > [!WARNING]
    > Sie müssen die Test-Agent-Installation erneut ausführen, um den Test-Agent mit dem Controller zu verbinden. Geben Sie dabei die IP-Adresse für den Controller anstelle des Controllernamens an.

     Dies gilt für den Controller, den Agent-Dienst und den Agent-Prozess. Die `BindTo`-Eigenschaft muss für jeden Prozess festgelegt werden, der auf einem Computer mit mehr als einem Netzwerkadapter ausgeführt wird. Zum Festlegen der `BindTo`-Eigenschaft wird für alle drei Prozesse die zuvor für den Testcontroller beschriebene Prozedur verwendet.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>So binden Sie eine Netzwerkschnittstellenkarte an einen Test-Agent

1. Klicken Sie in Microsoft Windows auf **Start**, klicken Sie in das Feld **Suche starten**, geben Sie **services.msc** ein, und drücken Sie dann die **EINGABETASTE**.

    Das Dialogfeld **Dienste** wird angezeigt.

2. Klicken Sie im Ergebnisbereich in der Spalte **Name** mit der rechten Maustaste auf den Dienst **Visual Studio Test Agent**, und klicken Sie dann auf **Beenden**.

     - oder -

     Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, und führen Sie den folgenden Befehl aus:

     **net stop vsttagent**

3. Öffnen Sie die XML-Konfigurationsdatei *QTAgentService.exe.config* im Verzeichnis *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE*.

4. Suchen Sie nach dem `<appSettings>`-Tag.

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

5. Fügen Sie im Abschnitt `BindTo` den `<appSettings>`-Schlüssel hinzu, um den zu verwendenden Netzwerkadapter anzugeben.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Starten Sie den Test-Agent-Dienst. Führen Sie dazu den folgenden Befehl an einer Eingabeaufforderung aus:

    `net start vsttagent`

## <a name="see-also"></a>Siehe auch

- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)
- [Ändern von Einstellungen für die Auslastungstestprotokollierung](../test/modify-load-test-logging-settings.md)
- [Konfigurieren von Ports für Testcontroller und Test-Agents](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [How to: Angeben von Zeitlimitzeiträumen für Testcontroller und Test-Agents](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
