---
title: Zusammenfassungsansicht – .NET-Arbeitsspeicherdaten | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Zusammenfassungsansicht. In dieser werden Informationen zu den .NET-Funktionen und -Typen angezeigt, die den meisten Arbeitsspeicher zugeordnet haben.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 590705e7fb55315176d5533a9cd009784430ea4d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722671"
---
# <a name="summary-view---net-memory-data"></a>Zusammenfassungsansicht – .NET-Arbeitsspeicherdaten
Die Zusammenfassung zeigt Informationen über die .NET-Funktionen und Typen, die den meisten Speicher belegen, und die Typen, die am häufigsten in einem Profilerstellungslauf erstellt wurden. Weitere Informationen, einschließlich einer Beschreibung der Benachrichtigungslinks und Berichtslisten, finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Zeitachsendiagramm
 Die Zeitachse in der Zusammenfassungsansicht zeigt die Auslastung des Prozessors (CPU) durch die profilierte Anwendung während des Zeitraums an, in dem die Profilerstellung stattgefunden sind. Sie können das Zeitachsendiagramm zum Filtern der Ansicht in einem ausgewählten Zeitraum verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Filtern von Berichtsansichten aus der Zeitachsenübersicht](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="functions-allocating-most-memory"></a>Funktionen, die den meisten Speicher zuordnen
 Listet die Funktionen auf, die die größte Anzahl von Bytes an Arbeitsspeicher im Profilerstellungslauf zugewiesen haben.

|Spalte|Beschreibung|
|------------|-----------------|
|**Name**|Der Name der Funktion.|
|**Bytes %**|Der Prozentsatz aller zugewiesenen Bytes im Profilerstellungslauf, die von dieser Funktion oder einer untergeordneten Funktion, die von dieser Funktion aufgerufen wurde zugewiesen wurden.|

## <a name="types-with-most-memory-allocated"></a>Typen mit der größten Speicherbelegung
 Listet die Typen auf, für die die größte Anzahl von Bytes an Arbeitsspeicher im Profilerstellungslauf zugewiesen wurde.

|Spalte|Beschreibung|
|------------|-----------------|
|**Name**|Der Name des Typs.|
|**Bytes %**|Der Prozentsatz aller zugewiesenen Bytes im Profilerstellungslauf, die für diesen Typ zugewiesen wurden.|

## <a name="types-with-most-instances"></a>Typen mit den meisten Instanzen
 Liste die Typen, die am häufigsten während des Profilerstellungslaufs erstellt wurden. had

|Spalte|Beschreibung|
|------------|-----------------|
|**Name**|Der Name des Typs.|
|**Instancen %**|Der Prozentsatz der Gesamtzahl der .NET-Objekte, die beim Profilerstellungslauf erstellt wurden und Instanzen dieses Typs sind.|

## <a name="see-also"></a>Siehe auch
- [Zusammenfassungsansicht: Samplingdaten](../profiling/summary-view-sampling-data.md)
- [Zusammenfassungsansicht – Instrumentationsdaten](../profiling/summary-view-instrumentation-data.md)
