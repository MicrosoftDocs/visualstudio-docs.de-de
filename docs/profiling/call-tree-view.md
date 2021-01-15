---
title: Aufrufstrukturansicht | Microsoft-Dokumentation
description: In diesem Artikel wird die Aufrufstrukturansicht erläutert, in der die Funktionsausführungspfade angezeigt werden, die von der Anwendung durchlaufen werden, für die die Profilerstellung durchgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 386f8e85c02fe73eab9801b3edf79ec0d0b178fc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150781"
---
# <a name="call-tree-view"></a>Aufrufstrukturansicht
In der Aufrufstrukturansicht werden die Funktionsausführungspfade angezeigt, die in der mit einem Profil versehenen Anwendung durchlaufen wurden. Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente. Unter den einzelnen Funktionsknoten werden alle Funktionen aufgeführt, die von ihnen aufgerufen wurden. Zudem werden Leistungsdaten über diese Funktionsaufrufe angezeigt.

 Die Aufrufstrukturansicht kann erweitert werden und den Ausführungspfad einer Funktion hervorheben, für die die meisten Samplings durchgeführt oder die meiste Zeit verwendet wurde. Um den leistungsintensivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.

 Jeder Prozess in der Profilerstellung wird als Stammknoten angezeigt. Sie können den Startknoten der Aufrufstrukturansicht festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.

 Durch das Festlegen eines Stammknotens wird sichergestellt, dass in der Ansicht lediglich die Teilstruktur des ausgewählten Knotens angezeigt wird. Sie können den Stammknoten wieder auf den angezeigten Knoten festlegen. Klicken Sie dazu mit der rechten Maustaste in das Fenster der Aufrufstrukturansicht, und wählen Sie **Stamm zurücksetzen** aus.

 Sie können die Aufrufstrukturansicht an Ihre Bedürfnisse anpassen, indem Sie Spalten hinzufügen oder entfernen. Klicken Sie mit der rechten Maustaste auf die **Titelleiste des Spaltennamens**, und klicken Sie anschließen auf **Spalten hinzufügen/entfernen**.

 Für die Aufrufstrukturansicht kann die Rauschunterdrückung konfiguriert werden, indem Sie festlegen, das weniger Daten angezeigt werden. Leistungsprobleme werden mithilfe der Rauschunterdrückung in der Ansicht erkennbarer. Leichter zu identifizierende Leistungsprobleme können auch leichter analysiert werden. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren der Rauschunterdrückung in Berichtsansichten](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> Wenn die Rauschunterdrückung so konfiguriert ist, dass sie eine Warnung anzeigt, wenn Sie aktiviert ist, wird eine Informationsleiste im Bericht angezeigt.

 Weitere Informationen zu Definitionen von Spalten in der Aufrufstrukturansicht finden Sie in den folgenden Artikeln:

- [Aufrufstrukturansicht](../profiling/call-tree-view-sampling-data.md)

- [Aufrufstrukturansicht](../profiling/call-tree-view-instrumentation-data.md)

- [Aufrufstrukturansicht: Sampling](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Aufrufstrukturansicht](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Siehe auch
- [Leistungsberichtansichten](../profiling/performance-report-views.md)
- [Grundlagen zu Instrumentationsdatenwerten](../profiling/understanding-instrumentation-data-values.md)
- [Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)
