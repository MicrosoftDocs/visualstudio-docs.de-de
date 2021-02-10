---
title: Verwenden von Leistungsregeln zur Analyse von Daten | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zu den Leistungswarnungen der Profilerstellungstools von Visual Studio. Diese weisen auf Probleme in einer mit einem Profil versehenen Anwendung hin, die die Programmausführung verlangsamen können.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 49d0b5f3c2aade0c6cdf4bd83735de2ba1c888ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885962"
---
# <a name="use-performance-rules-to-analyze-data"></a>Verwenden von Leistungsregeln zur Analyse von Daten
Die Leistungswarnungen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools deuten auf Probleme in einer profilierten Anwendung hin, die die Programmausführung verlangsamen können. Warnungen können auch anzeigen, dass Sie möglicherweise die Auflistungsmethoden ändern müssen, um nützlichere Daten zu erfassen. Leistungswarnungen werden automatisch in einer Profilerstellungssitzung generiert. Die Warnungen werden im Fenster **Fehlerliste** angezeigt, wenn eine Datei mit Profilerstellungsdaten in Visual Studio geöffnet wird. Im Fenster **Fehlerliste** können Sie den Quellcode zu dem Problem suchen und ausführliche Informationen zu dem Fehler anzeigen, z.B. Informationen zur Problembehebung. Sie können außerdem Warnungen deaktivieren, die für Sie nicht relevant sind.

> [!NOTE]
> Leistungswarnungen des Profilers werden mithilfe der dynamischen Analyse bei der Programmausführung generiert; es besteht kein Zusammenhang mit Codeanalysewarnungen. Mit der Codeanalyse können auch Leistungswarnungen für verwalteten Code auf Grundlage der statischen Analyse des Quellcodes generiert werden. Weitere Informationen finden Sie unter [Analyzing Managed Code Quality (Analysieren der Qualität von verwaltetem Code)](../code-quality/code-analysis-for-managed-code-overview.md) und [Performance Warnings (Leistungswarnungen)](/dotnet/fundamentals/code-analysis/quality-rules/performance-warnings).

## <a name="in-this-section"></a>In diesem Abschnitt
- [Vorgehensweise: Anzeigen von Leistungswarnungen](../profiling/how-to-view-performance-warnings.md)

 Enthält Informationen zum Öffnen des Fensters **Fehlerliste**, um Leistungswarnungen des Profilers anzuzeigen.

- [Vorgehensweise: Konfigurieren von Leistungsregeln](../profiling/how-to-configure-performance-rules.md)

 Enthält Informationen zum Aktivieren und Deaktivieren von einzelnen Leistungswarnungen.

- [Referenz zu den Leistungsregeln](../profiling/performance-rules-reference.md)

 Enthält ausführliche Informationen zu den Leistungswarnungen des Profilers.
