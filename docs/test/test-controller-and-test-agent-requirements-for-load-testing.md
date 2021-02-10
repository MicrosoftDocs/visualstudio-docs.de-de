---
title: Anforderungen von Testcontrollern und Test-Agents (Auslastungstest)
description: Hier erfahren Sie mehr zu Testcontroller- und Test Agent-Anforderungen für Auslastungstests. Visual Studio unterstützt verschiedene Testtypen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: a123a147d038a41f799c2fdf9d4fb26eaa4f3490
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894490"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Testcontroller- und Test-Agent-Anforderungen für Auslastungstests

Mehrere Testtypen, unter anderem Komponententests, Webleistungstests, Auslastungstests und manuelle Tests, sind in Visual Studio integriert. Mithilfe eines Testcontrollers und mindestens einem Agent ermöglicht Visual Studio Benutzern von Visual Studio Application Lifecycle Management das Ausführen von Tests auf Remotecomputern. Informationen finden Sie unter [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Hardware- und Softwareanforderungen

Sowohl für den Testcontrollercomputer als auch für die Test-Agent-Computer bestehen bestimmte Hardware- und Softwareanforderungen. Darüber hinaus müssen Sie bei der Bereitstellung der Testcontroller- und Test-Agent-Computer in mehreren Sprachen planen, wie diese Sprachen unterstützt werden.

### <a name="hardware-requirements"></a>Hardwareanforderungen

Die folgende Tabelle enthält die empfohlenen Hardwareanforderungen zum Bereitstellen eines Testcontrollers und von Test-Agents:

|**Konfiguration**|**Komponente**|**CPU**|**Festplatte**|**Arbeitsspeicher**|
|-|-------------------|-|------------|-|
|< 500 virtuelle Benutzer|Test-Agent|2,6 GHz|10 GB|2 GB|
|< 1000 virtuelle Benutzer|Test-Agent|Dualprozessor, 2,6 GHz|10 GB|2 GB|
|N x 1.000 virtuelle Benutzer|Test-Agent|Skalieren auf N Agents mit jeweils einem Dualprozessor mit 2,6 GHz|10GB|2GB|
|\< 30 Computer in der Testumgebung. Dies schließt zu testende Agents und Server ein.|Testcontroller|2,6 GHz|||
|N x 30 Computer in der Testumgebung. Dies schließt zu testende Agents und Server ein.|Testcontroller|N 2,6 GHz-Prozessoren|||

> [!NOTE]
> Die Anzahl virtueller Benutzer kann von Test zu Test sehr unterschiedlich sein. Eine Hauptursache für diese Unterschiede besteht in der Abweichung der *Reaktionszeiten* oder Benutzerverzögerungen. Weitere Informationen finden Sie unter [Editing Think Times to Simulate Website Human Interaction Delays (Bearbeiten von Reaktionszeiten zum Simulieren von Website-Interaktionsverzögerungen des Benutzers)](../test/edit-think-times-in-load-test-scenarios.md). In einem Auslastungstest sind Webtests im Allgemeinen effizienter und generieren mehr Auslastung als Komponententests. Die Zahlen in der vorangehenden Tabelle gelten für die Ausführung von Webtests mit einer Reaktionszeit von 3 bis 5 Sekunden in einer typischen Webanwendung.

Die hier aufgeführten Richtlinien stellen Richtwerte für die Hardwareplanung dar. Die Testleistung kann je nach Menge der Testdaten und Anzahl der Test-Agents sehr unterschiedlich sein. Die Testauslastung eines Test-Agents ist durch die CPU-Geschwindigkeit und den verfügbaren Arbeitsspeicher eingeschränkt. Testcontroller benötigen je nach Anzahl der Test-Agents und der in den Test einbezogenen Datenmenge größere Ressourcen.

Der Server, auf dem Visual Studio ausgeführt wird, sollte über eine zuverlässige Netzwerkverbindung mit einer Bandbreite von mindestens 1 MBit/s und einer Latenz von höchstens 350 ms verfügen. Zwischen den Testagents und dem Testcontroller darf keine Firewall konfiguriert sein. Wenn die Testleistung den Erwartungen nicht entspricht, sollten Sie ein Upgrade der Hardwarekonfiguration in Betracht ziehen.

### <a name="additional-hardware-considerations"></a>Zusätzliche Überlegungen zur Hardware

Test-Agents generieren je nach Dauer und Umfang des Tests eine beträchtliche Datenmenge auf den Testcontrollern. Im Allgemeinen sollten Sie pro 24 Stunden Testdatenerfassung die Bereitstellung von 10 GB zusätzlichem Festplattenspeicher einplanen.

Neben der hier empfohlenen Hardware sollten Sie die Bereitstellung zusätzlicher Hardware (z. B. zusätzliche Netzteile und Ventilatoren) für kritische Server in Erwägung ziehen.

### <a name="language-requirements"></a>Sprachanforderungen

Zur Vermeidung von Verwechslungen und zur Vereinfachung des Betriebs sollten ein Testcontroller und Test-Agents so konfiguriert werden, dass sie die gleiche Sprache wie das Betriebssystem des Computers und das Betriebssystem von Team Foundation Server verwenden. Wenn der Test-Agent und der Testcontroller auf unterschiedlichen Computern installiert sind, müssen diese für die Verwendung derselben Sprache konfiguriert werden. Sie können jedoch auch eine andere Sprachversion von Visual Studio unter der englischen Version eines Betriebssystems installieren, sofern diese Sprache mit der Sprache der Team Foundation Server-Bereitstellung übereinstimmt.

## <a name="monitor-agent-resources"></a>Überwachen von Agent-Ressourcen

Sie können Agent-Computer überwachen, um ihre Ressourcenanforderungen zu bestimmen, indem Sie die *QTAgent\*.exe*-Prozesse überwachen, die in Tests ausgeführt und skaliert werden. Der häufigste Engpass von *QTAgent\*.exe*-Prozessen liegt in der CPU-Auslastung. Wenn sich die CPU-Auslastung konsistent im hohen neunziger Bereich befindet, ist dies ein Anzeichen dafür, dass der Agent stark beansprucht wird. Der nächste Engpass betriff die Arbeitsspeicherauslastung. Bei anspruchsvollen Tests kann die Überwachung dieser Ressourcen dabei helfen zu bestimmen, ob Sie die Ressourcen der Computer erhöhen oder Ihre Tests anders verteilen sollten.

## <a name="see-also"></a>Weitere Informationen

- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)
