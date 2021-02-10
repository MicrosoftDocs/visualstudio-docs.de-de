---
title: Sicherheitsüberlegungen zu Schnellansichten | Microsoft-Dokumentation
description: Eine Schnellansicht für den Visual Studio-Debugger muss mit voller Vertrauenswürdigkeit ausgeführt werden. Beachten Sie beim Schreiben Ihrer eigenen Schnellansicht mögliche Sicherheitsbedrohungen, und treffen Sie entsprechende Vorkehrungen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c735fe4a14a0412fbb41b28b5a40e27083c3bca6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884194"
---
# <a name="visualizer-security-considerations"></a>Sicherheitsüberlegungen zu Schnellansichten
Das Schreiben einer Schnellansicht kann potenzielle Sicherheitsrisiken nach sich ziehen. Bisher sind keine bekannten Angriffe auf diese potenziellen Sicherheitslücken bekannt. Trotzdem sollten Entwickler sich der Sicherheitsrisiken bewusst sein und angemessene Vorsichtsmaßnahmen treffen, wie im Folgenden beschrieben, um sich vor zukünftigen Angriffen zu schützen.

 Debuggerschnellansichten erfordern umfangreichere Privilegien, als sie von einer partiell vertrauenswürdigen Anwendung zugelassen werden. Schnellansichten werden nicht geladen, wenn die Ausführung in Code mit partieller Vertrauenswürdigkeit unterbrochen wurde. Wenn Sie in einer Schnellansicht debuggen möchten, müssen Sie den Code mit voller Vertrauenswürdigkeit ausführen.

## <a name="possible-malicious-debuggee-component"></a>Potenziell bösartige zu debuggende Komponente
 Schnellansichten bestehen aus mindestens zwei Klassen: einer Klasse auf der Seite des Debuggers und einer Klasse auf der zu debuggenden Seite. Schnellansichten werden häufig in eigenen Assemblys bereitgestellt, können aber auch von der zu debuggenden Komponente aus geladen werden. In diesem Fall führt der Debugger Code aus der zu debuggenden Komponente innerhalb des Debuggers mit voller Vertrauenswürdigkeit aus.

 Das Ausführen von Code der zu debuggenden Komponente mit voller Vertrauenswürdigkeit wird problematisch, wenn die zu debuggende Komponente nicht voll vertrauenswürdig ist. Wenn eine Schnellansicht versucht, eine teilweise vertrauenswürdige Assembly der zu debuggenden Komponente zu laden, beendet Visual Studio die Schnellansicht.

 Eine kleinere Sicherheitslücke ist allerdings immer noch vorhanden. Die zu debuggende Komponente kann einer Debugger-Komponente zugeordnet werden, die von einer anderen Quelle (nicht von der zu debuggenden Komponente) geladen wurde. Die zu debuggende Komponente kann dann eine vertrauenswürdige Debugger-Komponente mit der Ausführung von Aktionen in deren Namen beauftragen. Wenn die vertrauenswürdige debuggerseitige Klasse z. B. einen „Diese Datei löschen“-Mechanismus verfügbar macht, könnte die teilweise vertrauenswürdige zu debuggende Komponente diesen Mechanismus auslösen, wenn der Benutzer deren Schnellansicht aufruft.

 Beachten Sie die von der Schnellansicht verfügbar gemachten Schnittstellen, wenn Sie dieses Sicherheitsproblem vermeiden möchten.

## <a name="see-also"></a>Siehe auch
- [Schnellansichtarchitektur](../debugger/visualizer-architecture.md)
- [How to: Schreiben einer Schnellansicht](create-custom-visualizers-of-data.md)
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)