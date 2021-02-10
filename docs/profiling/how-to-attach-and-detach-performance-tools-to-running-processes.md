---
title: Anfügen von Leistungstools an laufende Prozesse
description: Hier erfahren Sie, wie Sie den Visual Studio-Profiler zum Anfügen an einen oder Trennen von einem aktuell ausgeführten Prozess verwenden, um das Sampling und Sammeln von Leistungsdaten zu vereinfachen.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 13323a768b9f42e70df9e8be6e64c9dd98438865
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958959"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Vorgehensweise: Anfügen von Leistungstools an laufende Prozesse und Trennen von Leistungstools von laufenden Prozessen
Der Profiler kann verwendet werden, um an einen laufenden Prozess angefügt zu werden oder um von ihm getrennt zu werden, damit das Sampling und Sammeln von Leistungsdaten vereinfacht wird. Sie können diese Methode zum Erstellen eines Profils verwenden, wenn Sie das Sammeln von Daten über Anwendungsladezeiten vermeiden wollen oder nachdem es einen bestimmten Zustand erreicht hat.

> [!NOTE]
> Die folgenden Schritte gelten für das Anfügen und Trennen von Prozessen innerhalb der integrierten Entwicklungsumgebung [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] (IDE) Informationen zur Verwendung von Befehlszeilentools finden Sie unter [Profilerstellung über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md). Informationen zur Erstellung von Dienstprofilen finden Sie unter [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md).

 Die Prozesse, die zur Profilerstellung verfügbar sind, hängen von den Benutzerzugriffsberechtigungen ab, die von einem Administrator des Computers festgelegt wurde. Ein Benutzerkonto kann z.B. Berechtigungen für eines der Folgenden haben:

- Erweiterte Profilerstellungsfunktionen, wenn der Administrator Treiber und Dienste gestartet hat.

- Nur Beispiel-Profilerstellung (Domänenbenutzer).

- Zugriff zur Profilerstellung für alle Benutzer verweigern.

  Weitere Informationen finden Sie unter [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md) und in den ADMIN-Optionen in [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-attach-to-a-running-process"></a>So fügen Sie einen Profiler an einen laufenden Prozess an

1. Zeigen Sie im Menü **Debuggen** auf **Profiler**, dann auf **Leistungs-Explorer**, und klicken Sie dann auf **Anfügen**.

     Das Dialogfeld **Profiler an den Prozess anhängen** wird angezeigt.

2. Klicken Sie auf den Prozessnamen, mit dem eine Verbindung hergestellt werden soll.

3. Klicken Sie auf **Anfügen** aus.

### <a name="to-detach-from-a-running-process"></a>So trennen Sie den Profiler von einem laufenden Prozess

1. Zeigen Sie im Menü **Debuggen** auf **Profiler**, dann auf **Leistungs-Explorer**, und klicken Sie dann auf **Trennen**.

     Das Dialogfeld **Profiler an den Prozess anhängen** wird angezeigt.

2. Klicken Sie auf den Imagenamen, von dem Sie den Profiler trennen möchten.

3. Klicken Sie auf **Trennen**.

## <a name="see-also"></a>Siehe auch
- [Steuerung der Datensammlung](../profiling/controlling-data-collection.md)
- [Übersicht über Leistungssitzungen](../profiling/performance-session-overview.md)
- [How to: Starten und Beenden der Sammlung von Leistungsdaten](../profiling/how-to-start-and-end-performance-data-collection.md)
- [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
