---
title: 'Docker-Tutorial: Nächste Schritte'
description: Beschreibt Optionen zum Erweitern von Docker-Apps mit Orchestrierung mithilfe von Cloud Native Computing Foundation-Projekten.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8ca68b2eba710037535b4bd76c744e7c029a53e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841652"
---
# <a name="whats-next"></a>Ausblick

Obwohl Sie Ihr Tutorial abgeschlossen haben, gibt es noch VIEL mehr über Container zu erfahren!
Wir werden an dieser Stelle nicht ausführlicher darauf eingehen, aber hier sind einige weitere Bereiche, die Sie als nächstes untersuchen können.

## <a name="container-orchestration"></a>Containerorchestrierung

Die Ausführung von Containern in der Produktion ist schwierig. Sie möchten sich nicht bei einem Computer anmelden und einfach `docker run` oder `docker-compose up` ausführen. Warum nicht? Was geschieht, wenn die Container ausfallen? Wie skalieren Sie über mehrere Computern hinweg? Containerorchestrierung löst dieses Problem. Tools wie Kubernetes, Swarm, Nomad und AKS helfen Ihnen dabei, dieses Problem zu lösen.

Die allgemeine Idee besteht darin, dass Sie über „Manager“ verfügen, die den **erwarteten Status** erhalten. Dieser Status kann lauten: „Ich möchte zwei Instanzen meiner Web-App ausführen und Port 80 verfügbar machen." Die Manager untersuchen dann alle Computer im Cluster und delegieren die Aufgabe an „Workerknoten“. Die Manager überwachen Änderungen (z. B. einen Container, der beendet wird) und veranlassen dann, dass der **tatsächliche Status** den erwarteten Zustand widerspiegelt.

## <a name="cloud-native-computing-foundation-projects"></a>Cloud Native Computing Foundation-Projekte

CNCF ist ein herstellerneutraler Speicherort für verschiedene Open-Source-Projekte, einschließlich Kubernetes, Prometheus, Envoy, Linkerd, NATs und mehr! Sie können Projekte mit dem Reifegrad [Graduated und Incubating hier](https://www.cncf.io/projects/) und die gesamte [CNCF-Landschaft hier](https://landscape.cncf.io/) einsehen. Es gibt VIELE Projekte, die Ihnen dabei helfen, Probleme im Zusammenhang mit Überwachung, Protokollierung, Sicherheit, Imageregistrierungen, Messaging und mehr zu lösen!

Wenn Sie also noch nicht mit der Containerlandschaft und cloudnativer Anwendungsentwicklung vertraut sind, herzlich Willkommen! Schaffen Sie eine Verbindung mit der Community, stellen Sie Fragen, und lernen Sie Neues dazu! Wir freuen uns auf Sie!

## <a name="working-with-docker-in-vs-code"></a>Arbeiten mit Docker in VS Code

Weitere Informationen zur Verwendung der VS Code-Erweiterung von Docker finden Sie hier:

- [Übersicht über die VS Code-Erweiterung von Docker](https://code.visualstudio.com/docs/containers/overview)
- [Erste Schritte mit Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Erste Schritte mit Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Erste Schritte mit .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Debuggen von containerisierten Apps](https://code.visualstudio.com/docs/containers/debug-common)
