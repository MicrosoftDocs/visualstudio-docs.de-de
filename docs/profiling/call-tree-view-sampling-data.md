---
title: Aufrufstrukturansicht – Samplingdaten | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie die Aufrufstrukturansicht Samplingdaten für die Funktionsausführungspfade im Leistungs-Explorer anzeigt, die in der Anwendung durchlaufen werden, für die die Profilerstellung durchgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1fc7493d20d09ebd606e3a6ec8e5271981fb6f62
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150521"
---
# <a name="call-tree-view---sampling-data"></a>Aufrufstrukturansicht: Samplingdaten
In der Aufrufstrukturansicht werden die Funktionsausführungspfade angezeigt, die in der mit einem Profil versehenen Anwendung durchlaufen wurden.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente. Unter den einzelnen Funktionsknoten werden alle Funktionen aufgeführt, die von dieser aufgerufen wurden. Zudem werden Leistungsdaten über diese Funktionsaufrufe angezeigt.

 Die Werte in der Aufrufstrukturansicht beziehen sich auf die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden. Prozentwerte werden berechnet, indem der Funktionsinstanzwert mit der Gesamtzahl der Samplings in der Profilerstellung verglichen wird.

## <a name="highlight-the-execution-hot-path"></a>Hervorheben des langsamsten Ausführungspfads
 Die Aufrufstrukturansicht kann erweitert werden und den Ausführungspfad des Prozesses oder der Funktion hervorheben, für die die meisten Samplings durchgeführt wurden. Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf den Prozess oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.

## <a name="set-the-call-tree-root-node"></a>Festlegen des Stammknotens der Aufrufstruktur
 Jeder Prozess in der Profilerstellung wird als Stammknoten angezeigt. Sie können den Startknoten der Aufrufstrukturansicht festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.

 Durch das Festlegen eines Stammknotens wird sichergestellt, dass in der Ansicht lediglich die Teilstruktur des ausgewählten Knotens angezeigt wird. Um den Stammknoten auf den ursprünglichen Knoten zurückzusetzen, klicken Sie mit der rechten Maustaste auf das Fenster der Aufrufstrukturansicht, und wählen Sie dann **Stamm zurücksetzen** aus.

|Spalte|Beschreibung|
|------------|-----------------|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses.|
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|
|**Funktionsname**|Der vollqualifizierte Name der Funktion.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Funktionsadresse**|Die Adresse der Funktion.|
|**Level**|Die Tiefe dieser Funktion in der Aufrufstruktur. Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|
|**Exklusive Samplings**|Die Anzahl der Samplings, die in dieser Funktion erfasst wurden, als sie von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurde. Diese Zahl umfasst keine Samplings, die in von der Funktion aufgerufenen Funktionen erfasst wurden.|
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die auf exklusive Samplings dieser Funktion entfallen, wenn diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|
|**Inklusive Samplings**|Die Anzahl der Samplings, die in dieser Funktion erfasst wurden, als sie von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurde. Diese Zahl umfasst Samplings, die in von der Funktion aufgerufenen Funktionen erfasst wurden.|
|**Inklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die auf inklusive Samplings dieser Funktion entfallen, wenn diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)
- [Aufrufstrukturansicht: Samplingdaten](../profiling/call-Tree-view-sampling-data.md)
- [Aufrufstrukturansicht: Sampling](../profiling/call-tree-view-dotnet-memory-sampling-data.md)
- [Aufrufstrukturansicht: Instrumentierungsdaten des .NET-Arbeitsspeichers](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)
- [Aufrufstrukturansicht](../profiling/call-tree-view-instrumentation-data.md)
