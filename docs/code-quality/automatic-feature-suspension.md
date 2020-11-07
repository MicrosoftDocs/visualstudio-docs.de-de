---
title: Automatisches Anhalten von Features
ms.date: 11/04/2016
description: Erfahren Sie, wie Visual Studio den Analysebereich reduziert, Garbage Collection Modus mit niedriger Latenz deaktiviert und Caches leert, wenn der Systemspeicher begrenzt ist.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12b15ed8aa02e53841b85245350735258e7ec11d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348540"
---
# <a name="automatic-feature-suspension"></a>Automatisches Anhalten von Features

Wenn Ihr verfügbarer System Arbeitsspeicher auf 200 MB oder weniger fällt, zeigt Visual Studio im Code-Editor die folgende Meldung an:

![Warnungs Text zum Anhalten der vollständigen Lösungs Analyse](../code-quality/media/fsa_alert.png)

Wenn Visual Studio eine nicht genügend Arbeitsspeicher Bedingung erkennt, werden bestimmte erweiterte Funktionen automatisch angehalten, damit Sie stabil bleiben. Visual Studio funktioniert weiterhin wie zuvor, aber seine Leistung ist beeinträchtigt.

Bei einem Mangel an Arbeitsspeicher erfolgen die folgenden Aktionen:

- Die Live Code Analyse für Visual c# und Visual Basic wird auf einen minimalen Bereich reduziert.

- Der Modus für die [Garbage Collection](/dotnet/standard/garbage-collection/index) (GC) mit niedriger Latenz für Visual c# und Visual Basic ist deaktiviert.

- Visual Studio-Caches werden geleert.

## <a name="improve-visual-studio-performance"></a>Verbessern der Leistung von Visual Studio

Tipps und Tricks zum Verbessern der Leistung von Visual Studio beim Umgang mit großen Lösungen oder Bedingungen mit geringem Arbeitsspeicher finden Sie unter [Überlegungen zur Leistung für große Lösungen](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Die Live Code Analyse wird auf einen minimalen Bereich reduziert.

Standardmäßig wird die Live Code Analyse für geöffnete Dokumente und Projekte ausgeführt. Sie können diesen Analysebereich so anpassen, dass er auf das aktuelle Dokument reduziert oder auf die gesamte Projekt Mappe erweitert wird. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren des Bereichs für die Liveanalyse für verwalteten Code](./configure-live-code-analysis-scope-managed-code.md). Bei einem Mangel an Arbeitsspeicher erzwingt Visual Studio, dass der Live Analysebereich auf das aktuelle Dokument reduziert wird. Sie können jedoch Ihren bevorzugten Analysebereich erneut aktivieren, indem Sie die Schaltfläche **erneut aktivieren** in der Info Leiste auswählen, wenn Sie angezeigt wird, oder indem Sie Visual Studio neu starten. Im Dialogfeld Optionen werden immer die aktuellen Einstellungen für die Live-Code Analysebereiche angezeigt.

## <a name="gc-low-latency-disabled"></a>GC mit geringer Latenzzeit deaktiviert

Starten Sie Visual Studio neu, um den GC-Modus mit niedriger Latenz wieder zu aktivieren. Standardmäßig ermöglicht Visual Studio den GC-Modus mit niedriger Latenz, wenn Sie eingeben, um sicherzustellen, dass Ihre Typisierung keine GC-Vorgänge blockiert. Wenn in Visual Studio jedoch aufgrund von geringem Arbeitsspeicher die automatische anhaltewarnung angezeigt wird, ist der GC-Modus mit niedriger Latenzzeit für diese Sitzung deaktiviert. Wenn Sie Visual Studio neu starten, wird das standardmäßige GC-Verhalten erneut aktiviert. Weitere Informationen finden Sie unter <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>In Visual Studio geleerte Caches

Wenn Sie die aktuelle Entwicklungs Sitzung fortsetzen oder Visual Studio neu starten, werden alle Visual Studio-Caches sofort geleert, aber mit dem erneuten Auffüllen begonnen. Die geleerten Caches enthalten Caches für die folgenden Features:

- Alle Verweise suchen

- Navigieren zu

- Hinzufügen mithilfe von

Außerdem werden Caches, die für interne Visual Studio-Vorgänge verwendet werden, ebenfalls gelöscht.

> [!NOTE]
> Die automatische Merkmals Unterbrechungs Warnung tritt nur einmal pro Lösung auf, nicht pro Sitzung. Dies bedeutet Folgendes: Wenn Sie von Visual Basic zu Visual c# wechseln (oder umgekehrt) und auf einen anderen Arbeitsspeicher Mangel stoßen, können Sie möglicherweise eine weitere Warnung zur automatischen Funktions Unterbrechung erhalten.

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Konfigurieren des Gültigkeits Bereichs der Live-Code Analyse für verwalteten Code](./configure-live-code-analysis-scope-managed-code.md)
- [Grundlagen der Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)
- [Überlegungen zur Leistung für große Lösungen](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)
