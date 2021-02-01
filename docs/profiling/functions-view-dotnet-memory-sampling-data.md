---
title: 'Funktionsansicht: .NET-Speichersamplingdaten | Microsoft-Dokumentation'
description: Hier erhalten Sie Informationen zur Ansicht „Funktionen“ für Speicherbelegungs-Profilerstellungsdaten für .NET, die mit der Samplingmethode gesammelt wurden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2fe4f011a88ab4cf293626fe01f708b3cf5bc68f
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801521"
---
# <a name="functions-view---net-memory-sampling-data"></a>Funktionsansicht: .NET-Speichersamplingdaten
In der Funktionsansicht der Profilerstellungsdaten für die .NET-Speicherbelegung, die mithilfe der Samplingmethode erfasst wurden, werden sowohl die Funktionen angezeigt, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben, als auch die Größe und die Anzahl der Speicherbelegungen.

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
|**Inklusive Zuordnungen**|Die Gesamtanzahl der Objekte, die in dieser Funktion und ihren untergeordneten Funktionen Speicher belegt haben.|
|**Inklusive Speicherbelegungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung Speicher belegt haben und inklusive Belegungen dieser Funktion waren.|
|**Exklusive Speicherbelegungen**|Die Anzahl der Objekte, die während der Ausführung der Funktion am Anfang der Aufrufliste erstellt wurden. Diese Zahl schließt nicht die Objekte mit ein, die in untergeordneten Funktionen erstellt wurden.|
|**Exklusive Zuordnungen %**|Der Prozentsatz aller Objekte, die während der Profilerstellung Speicher belegt haben und exklusive Belegungen dieser Funktion waren.|
|**Inklusive Bytes**|Die Anzahl der Bytes im Arbeitsspeicher, die von dieser Funktion und ihren untergeordneten Funktionen belegt wurden.|
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes im Arbeitsspeicher, die während der Profilerstellung belegt wurden und inklusive Bytes dieser Funktion waren.|
|**Exklusive Bytes**|Die Anzahl der Bytes im Arbeitsspeicher, die von dieser Funktion, nicht jedoch von ihren untergeordneten Funktionen belegt wurden.|
|**Exklusive Bytes %**|Der Prozentsatz aller Bytes im Arbeitsspeicher, die während der Profilerstellung belegt wurden und exklusive Belegungen dieser Funktion waren.|

## <a name="see-also"></a>Siehe auch
- [Funktionsansicht: Instrumentierung](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Funktionsansicht](../profiling/functions-view-sampling-data.md)
- [Funktionsansicht](../profiling/functions-view-instrumentation-data.md)
