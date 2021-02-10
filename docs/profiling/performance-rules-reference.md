---
title: Referenz zu den Leistungsregeln | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zu den Leistungsregeln der Profilerstellungstools. Diese zeigen zusätzliche Warnungen und Informationen über die Leistung Ihrer Anwendung an.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b2c23f32e2368ffa269deeb7eddb5fb05839e4af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922135"
---
# <a name="performance-rules-reference"></a>Referenz zu den Leistungsregeln
Die Leistungsregeln der Profilerstellungstools bieten zusätzliche Warnungen und Informationen über die Leistung Ihrer Anwendung. Leistungsregeln analysieren Daten in einer Profilerstellung, die aus Quellen wie z.B. Windows und Prozessor-Leistungsindikatoren gesammelt werden. Regelnachrichten werden im Fenster Fehlerausgabe der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-IDE angezeigt. Nachrichten werden mit einer der folgenden Regelebenen aufgeführt:

|Kategorie|Beschreibung|
|-|-|
|**Fehler**|Nur wenige Regeln generieren Fehlermeldungen, da die meisten Leistungsprobleme keine tatsächlichen Fehler sind. Eine Fehlermeldung kann einen Fehler beim Erfassen von Profilerstellungsdaten angeben.|
|**Warnung**|Warnungen geben einen Bereich Ihrer Anwendung an, die eine Ursache von Leistungsproblemen sein oder die von Optimierungen profitieren können.|
|**Information**|Informationsnachrichten geben entweder die Analyse einer Regelbedingung an, die den Schwellenwert zur Erstellung einer Fehlermeldung nicht erreicht hat, oder dass die Information in der Nachricht nützlich ist, jedoch nicht auf ein Leistungsproblem hinweist.|

## <a name="in-this-section"></a>In diesem Abschnitt

[Leistungsregeln nach ID](../profiling/performance-rules-by-id.md)

Die Leistungsregeln der Profilerstellungstools sind in vier Kategorien unterteilt:

|Kategorie|Beschreibung|
|-|-|
|[Leistungsregeln für die .NET Framework-Verwendung](../profiling/dotnet-framework-usage-performance-rules.md)|Regeln, mit denen Sie .NET Framework effizient verwenden können.|
|[Leistungsregeln für Speicher und Auslagerung](../profiling/memory-and-paging-performance-rules.md)|Regeln, die den verwalteten Arbeitsspeicher und das Pagingverhalten Ihrer Anwendung analysieren.|
|[Verwendungsregeln für Profilerstellungstools](../profiling/profiling-tools-usage-rules.md)|Regeln, mit denen Sie Profilerstellungstools effizient verwenden können.|
|[Leistungsregeln für die Ressourcenüberwachung](../profiling/resource-monitoring-performance-rules.md)|Informationsnachrichten zur Auslastung von Prozessor und Arbeitsspeicher in einer Profilerstellung.|
