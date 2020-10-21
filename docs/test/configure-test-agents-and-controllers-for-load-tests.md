---
title: Konfigurieren von Test-Agents und Testcontrollern für Auslastungstests
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4e9aea22a63f2eee8f83ee597ed11c90df7f6b1a
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099400"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>Übersicht von Test-Agents und Testcontrollern für die Ausführung von Auslastungstests

Visual Studio kann eine simulierte Auslastung für Ihre App mithilfe von physischen oder virtuellen Computern generieren. Diese Computer müssen als einzelne Testcontroller und Test-Agents eingerichtet werden. Mithilfe des Testcontrollers und der Test-Agents können Sie eine größere Auslastung generieren als mit nur einem Computer.

> [!NOTE]
> Sie können ebenfalls cloudbasierte Auslastungstests verwenden, um virtuelle Computer bereitzustellen, die die Auslastung vieler Benutzer generieren, die gleichzeitig auf Ihre Website zugreifen. Die Verwendung des Setups mit Testcontroller/Test-Agent auf in der Cloud gehosteten virtuellen Computern wird jedoch nicht unterstützt. Weitere Informationen zu cloudbasierten Auslastungstests finden Sie unter [Run load tests using Azure Test Plans (Ausführen von Auslastungstests mithilfe von Azure Test Plans)](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts&preserve-view=true).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Architektur der Auslastungssimulation

Die Architektur der Auslastungssimulation besteht aus einem Visual Studio-Client, einem Testcontroller und Test-Agents.

- Mit dem Client werden Tests entwickelt, Tests ausgeführt und Testergebnisse angezeigt.

- Mit dem Testcontroller werden die Test-Agents verwaltet und Testergebnisse gesammelt.

- Die Test-Agents werden verwendet, um die Tests auszuführen und Daten einschließlich Systeminformationen und ASP.NET-Profilerstellungsdaten zu sammeln, die in der Testeinstellung definiert sind.

Diese Architektur bietet die folgenden Vorteile:

- Die Möglichkeit, die Auslastungsgenerierung durch Hinzufügen zusätzlicher Test-Agents zu einem Testcontroller horizontal zu skalieren

- Flexibilität für die Installation der Client-, Testcontroller- und Test-Agent-Software auf den gleichen oder anderen Computern. Beispiel:

   **Lokale Konfiguration:**

  - Machine1: Visual Studio, Controller, Agent.

    ![Lokaler Computer mit Controller und Agent](./media/load-test-configa.png)

    **Typische Remotekonfiguration:**

  - Machine1 und 2: Visual Studio (ein Controller kann von mehreren Testern verwendet werden).

  - Machine3: Controller (auf diesem Computer können auch Agents installiert sein)

  - Machine4-n: Agent oder Agents, die jeweils dem Controller auf Machine3 zugeordnet sind.

    ![Remotecomputer mit Controller und Agents](./media/load-test-configb.png)

Obwohl ein Testcontroller in der Regel mehrere Test-Agents verwaltet, kann ein Agent nur einem einzelnen Controller zugeordnet sein. Jeder Test-Agent kann von einem Team von Entwicklern gemeinsam verwendet werden. Dank dieser Architektur kann die Anzahl der Test-Agents leicht erhöht werden, um größere Auslastungen zu generieren.

## <a name="test-agent-and-test-controller-interaction"></a>Interaktion zwischen Test-Agent und Testcontroller

Der Testcontroller verwaltet zum Ausführen von Tests einen Satz von Test-Agents. Der Testcontroller kommuniziert mit den Test-Agents, um Tests zu starten oder zu beenden, den Test-Agent-Status nachzuverfolgen und Testergebnisse zu sammeln.

### <a name="test-controller"></a>Testcontroller

Der Testcontroller stellt eine allgemeine Architektur zum Ausführen von Tests bereit und verfügt über spezielle Funktionen zum Ausführen von Auslastungstests. Der Testcontroller sendet den Auslastungstest an alle Test-Agents und wartet, bis der Test von den Test-Agents initialisiert wurde. Wenn alle Test-Agents bereit sind, sendet der Testcontroller eine Nachricht an die Test-Agents, dass der Test gestartet werden soll.

### <a name="test-agent"></a>Test-Agent

Der Test-Agent wird als Dienst ausgeführt, der nach Anforderungen des Testcontrollers zum Starten eines neuen Tests lauscht. Wenn der Test-Agent eine Anforderung empfängt, startet der Test-Agent-Dienst einen Prozess zum Ausführen des Tests. Jeder Test-Agent führt den gleichen Auslastungstest aus.

Den Test-Agents wird vom Administrator eine Gewichtung zugewiesen, und die Auslastung wird entsprechend der Gewichtung der Test-Agents verteilt. Wenn z. B. Test-Agent 1 eine Gewichtung von 30 und Test-Agent 2 eine Gewichtung von 70 hat, und die Auslastung auf 1.000 Benutzer festgelegt wurde, werden von Test-Agent 1 300 und von Test-Agent 2 700 virtuelle Benutzer simuliert. Weitere Informationen finden Sie unter [Verwalten von Testcontrollern und Test-Agents mit Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Der Test-Agent erhält als Eingabe einen Satz von Tests und einen Satz von Simulationsparametern. Ein Schlüsselkonzept besteht darin, dass Tests von den Computern unabhängig sind, auf denen sie ausgeführt werden.

## <a name="test-controller-and-test-agent-connection-points"></a>Verbindungspunkte zwischen Testcontrollern und Test-Agents

In der folgenden Abbildung sind die Verbindungspunkte zwischen Testcontroller, Test-Agent und Client dargestellt. Sie enthält die Ports für eingehende und ausgehende Verbindungen sowie die für diese Ports verwendeten Sicherheitseinschränkungen.

![Ports und Sicherheit von Testcontrollern und Test-Agents](./media/test-controller-agent-firewall.png)

Weitere Informationen finden Sie unter [Konfigurieren von Ports für Testcontroller und Test-Agents](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Installationsinformationen für Testcontroller und Test-Agents

Wichtige Informationen zu Hardware- und Softwareanforderungen für Testcontroller und Test-Agents, Verfahren zum Installieren dieser Komponenten und Konfigurieren der Umgebung für optimale Leistung finden Sie unter [Install and configure test agents (Installieren und Konfigurieren von Test-Agents)](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Verwenden des Testcontrollers und des Test-Agents bei Komponententests

Nachdem Sie einen Testcontroller und mindestens einen Agent installiert haben, können Sie in der Testeinstellung für die Ausführung der Auslastungstests festlegen, ob eine Remoteausführung mit dem Testcontroller erfolgen soll. Darüber hinaus können Sie in der Testeinstellung die Daten- und Diagnoseadapter angeben, die mit der den Agents zugeordneten Rolle verwendet werden sollen.

## <a name="see-also"></a>Weitere Informationen

- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)
