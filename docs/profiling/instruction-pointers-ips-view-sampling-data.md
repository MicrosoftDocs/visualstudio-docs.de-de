---
title: Anweisungszeigeransicht – Samplingdaten | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Anweisungszeigeransicht für Samplingdaten. Diese führt Leistungsdaten für die Assemblyanweisungen auf, die direkt ausgeführt wurden, als die Samplings erfasst wurden.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f08821516ca25ed4e1746e13e506b9c0094b0227
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721553"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Anweisungszeigeransicht: Samplingdaten
In der Anweisungszeigeransicht der Samplingdaten werden die Leistungsdaten für die Assemblyanweisungen aufgeführt, die direkt ausgeführt wurden, als die Samplings bei der Profilerstellung erfasst wurden.

> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Spalte|Beschreibung|
|------------|-----------------|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses.|
|**Modulname**|Der Name des Moduls, das die Anweisung enthält|
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält|
|**Quelldatei**|Die Quelldatei, die die Anweisung enthält|
|**Funktionsname**|Der Name der Funktion, die die Anweisung enthält|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Funktionsadresse**|Die Startspeicheradresse der Funktion in der geladenen Binärdatei|
|**Quellanfangszeile**|Die Nummer der Anfangszeile in der Quelldatei, an der dieses Sampling erfasst wurde.|
|**Quellendzeile**|Die Endzeilennummer der Quelldatei, an der dieses Sampling erfasst wurde.|
|**Quellanfangszeichen**|Der Offset des Startzeichens in der Quelldateizeile, an dem dieses Sampling erfasst wurde.|
|**Quellendzeichen**|Der Offset des Endzeichens der Quelldateizeile, an dem dieses Sampling erfasst wurde.|
|**Anweisungsadresse**|Die Adresse der Anweisung in der geladenen Binärdatei|
|**Exclusive Samplings**|Die Gesamtanzahl der Samplings, die während der Ausführung der Anweisung erfasst wurden|
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings bei der Profilerstellung, die gesammelt wurden, als die Anweisung ausgeführt wurde|

## <a name="see-also"></a>Siehe auch
- [Anweisungszeigeransicht: .NET-Speichersamplingdaten im Profiler](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
