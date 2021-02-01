---
title: Funktionsansicht – Konfliktdaten | Microsoft-Dokumentation
description: Hier erhalten Sie ausführliche Informationen zur Funktionsberichtsansicht für Konfliktdaten, in der die Funktionen in der Profilerstellungsausführung aufgeführt sind, deren Ausführung während der Profilerstellungsausführung blockiert wurde.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07f23e38a0d2bc7b538bbe42818ce8a8a2f3d2c1
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801666"
---
# <a name="functions-view---contention-data"></a>Funktionsansicht: Konfliktdaten
Die Funktionsberichtansicht der Konfliktdatenlisten der Funktionen in der Profilerstellungsausführung, deren Ausführung während der Profilerstellung blockiert wurde.

 In der folgenden Tabelle werden die Werte erklärt, die in der Funktionsansicht einer Profilerstellungsdatendatei angezeigt werden, die anhand der Parallelitätsmethode erstellt wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**Exklusive blockierte Zeit %**|Der Zeitraum, in dem diese Funktion keinen Code im Text der Funktion ausführen konnte. Diese umfasst nicht den Zeitaufwand für Funktionen, die von dieser Funktion aufgerufen wurden.|
|**Exklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit in der Profilerstellung, für die nur diese Funktion blockiert wurde.|
|**Exklusive Konflikte**|Wie oft die Funktion vom Ausführen von Code im Text der Funktion abgehalten wurde. Konflikte in Funktionen, die von dieser Funktion aufgerufen wurden, werden nicht einbezogen.|
|**Exklusive Konflikte %**|Der Prozentsatz aller Konflikte in der Profilerstellung, die allein in dieser Funktion aufgetreten sind.|
|**Funktionsadresse**|Die Adresse der Funktion.|
|**Funktionsname**|Der vollqualifizierte Name der Funktion.|
|**Inklusive blockierte Zeit**|Die Zeit, die diese Funktion oder eine Funktion, die von dieser Funktion aufgerufen wurde, nicht ausgeführt werden konnte.|
|**Inklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, die für diese Funktion oder Methode blockiert wurde.|
|**Inklusive Konflikte %**|Wie oft diese Funktion oder eine Funktion, die von dieser Funktion aufgerufen wurde, nicht ausgeführt werden konnte.|
|**Inklusive Konflikte %**|Der Prozentsatz aller Konflikte während der Profilerstellung, die allein in dieser Funktion oder Methode aufgetreten sind.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|
|**Prozess-ID**|Der Prozess-ID (PID) des Prozesses, in dem die Funktion ausgeführt wurde.|
|**Prozessname**|Der Name des Prozesses.|
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|

## <a name="see-also"></a>Siehe auch
- [How to: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)
- [Funktionsansicht](../profiling/functions-view.md)
- [Funktionsansicht: Instrumentierung](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Funktionsansicht: Sampling](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Funktionsansicht](../profiling/functions-view-instrumentation-data.md)
- [Funktionsansicht](../profiling/functions-view-sampling-data.md)
