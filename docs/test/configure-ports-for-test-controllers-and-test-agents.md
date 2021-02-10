---
title: Konfigurieren von Ports für Testcontroller und Test-Agents
description: Lernen Sie, die vom Testcontroller, Test-Agent und Client verwendeten standardmäßigen Eingangsports zu ändern, um Konflikte mit anderer Software zu vermeiden.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 78c6dd0f9ffa89f7b1a2ac7ac7a2344b67a47970
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868048"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Konfigurieren von Ports für Testcontroller und Test-Agents

Sie können die vom Testcontroller, Test-Agent und Client verwendeten Standardports ändern. Dies ist möglicherweise erforderlich, wenn Sie den Testcontroller, Test-Agent oder Client zusammen mit anderer Software verwenden möchte, bei der ein Konflikt mit den Porteinstellungen auftritt. Ein weiterer Grund zum Ändern der Ports besteht in der Firewalleinschränkung zwischen dem Testcontroller und dem Client. In diesem Fall können Sie den Port manuell konfigurieren, um eine Firewall zuzulassen, damit der Testcontroller Ergebnisse an den Client senden kann.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Die folgende Abbildung zeigt die Verbindungspunkte zwischen Testcontroller, Test-Agent und Client an. Sie enthält die Ports für eingehende und ausgehende Verbindungen sowie die für diese Ports verwendeten Sicherheitseinschränkungen.

![Ports und Sicherheit von Testcontrollern und Test-Agents](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Eingehende Verbindungen

Der vom Testcontroller verwendete Standardport ist 6901, und der Standardport des Test-Agents ist 6910. Der Client verwendet standardmäßig einen zufälligen Port, mit dem die Testergebnisse vom Testcontroller empfangen werden. Für alle eingehenden Verbindungen authentifiziert der Testcontroller die aufrufende Partei und überprüft, ob sie zu einer bestimmten Sicherheitsgruppe gehört.

- **Testcontroller** Für eingehende Verbindungen wird TCP-Port 6901 verwendet. Konfigurieren Sie ggf. den eingehenden Port. Weitere Informationen finden Sie unter [Konfigurieren der eingehenden Ports](#configure-the-incoming-ports).

    Der Testcontroller muss ausgehende Verbindungen mit Test-Agents und dem Client herstellen können.

    > [!NOTE]
    > Für den Testcontroller muss die eingehende Verbindung für **Datei- und Druckerfreigabe** geöffnet sein.

- **Test-Agent** Für eingehende Verbindungen wird TCP-Port 6910 verwendet. Konfigurieren Sie ggf. den eingehenden Port. Weitere Informationen finden Sie unter [Konfigurieren der eingehenden Ports](#configure-the-incoming-ports).

   Der Test-Agent muss ausgehende Verbindungen mit dem Testcontroller herstellen können.

- **Client** Standardmäßig wird ein zufälliger TCP-Port für eingehende Verbindungen verwendet. Konfigurieren Sie ggf. den eingehenden Port. Weitere Informationen finden Sie unter [Konfigurieren der eingehenden Ports](#configure-the-incoming-ports).

   Möglicherweise erhalten Sie Firewallbenachrichtigungen, wenn vom Testcontroller das erste Mal eine Verbindung mit dem Client hergestellt wird.

   Unter Windows Server 2008 werden die Firewallbenachrichtigungen standardmäßig deaktiviert. Sie müssen Firewallausnahmen für Clientprogramme (*devenv.exe*, *mstest.exe*, *mlm.exe*) manuell hinzufügen, damit eingehende Verbindungen akzeptiert werden.

## <a name="outgoing-connections"></a>Ausgehende Verbindungen

Für alle ausgehenden Verbindungen werden zufällige TCP-Ports verwendet.

- **Testcontroller** Der Testcontroller muss ausgehende Verbindungen mit Agents und mit dem Client herstellen können.

- **Test-Agent** Der Test-Agent muss ausgehende Verbindungen mit dem Controller herstellen können.

- **Client** Der Client muss ausgehende Verbindungen mit dem Controller herstellen können.

## <a name="configure-the-incoming-ports"></a>Konfigurieren der eingehenden Ports

Folgen Sie diesen Anweisungen, um die Ports für einen Testcontroller und Test-Agents zu konfigurieren.

- **Controllerdienst**: Ändern Sie den Wert des Ports, indem Sie die Datei *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* bearbeiten:

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Agent-Dienst**: Ändern Sie den Port, indem Sie die Datei *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* bearbeiten:

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Client**: Fügen Sie die folgenden Registrierungswerte (**DWORD**) mithilfe des Registrierungs-Editors hinzu. Der Client verwendet einen der Ports aus dem angegebenen Bereich zum Empfangen von Daten vom Testcontroller:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Weitere Informationen

- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)
