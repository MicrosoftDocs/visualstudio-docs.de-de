---
title: Zeilenansicht - .NET-Speichersamplingdaten | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Zeilenansicht der Profilerstellungsdaten für die .NET-Speicherbelegung. In dieser werden die Anweisungen aufgelistet, die während der Profilerstellung Arbeitsspeicher belegt haben.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 1922851b96ddec47c298b3e7d1e94a7de129505a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917850"
---
# <a name="lines-view---net-memory-sampling-data"></a>Zeilenansicht: Samplingdaten zum .NET-Speicher
In der Zeilenansicht der Profilerstellungsdaten für die .NET-Speicherbelegung, die die Samplingmethode verwenden, werden die Anweisungen angezeigt, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben. Die Spalten enthalten auch die Größe und Anzahl der Zuordnungen.

 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.

 Eine Anweisung wird mit dem Folgenden identifiziert:

- Die Quelldatei, die die Funktionsanweisung enthält.

- Die Funktion, die die Anweisung enthält.

- Die Quellzeile, an der die Anweisung beginnt.

- Das Zeichen in der Quellzeile, an dem die Anweisung beginnt.

- Die Quellzeile, an der die Anweisung endet.

- Das Zeichen in der Quellzeile, an dem die Anweisung endet.

  Die Zeilennamensspalte, die eine sortierbare Verkettung der Bezeichnerdaten bereitstellt.

  Per Definition ruft eine Anweisung keine anderen Funktionen auf. Daher sind nur exklusive Werte aufgeführt.

|Spalte|Beschreibung|
|------------|-----------------|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses.|
|**Modulname**|Der Name des Moduls, das die Anweisung enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält.|
|**Quelldatei**|Die Quelldatei, die die Anweisung enthält.|
|**Funktionsname**|Der Namen der Funktion, die die Anweisung enthält.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Funktionsadresse**|Die Startadresse der Funktion.|
|**Quellanfangszeile**|Die Nummer der Anfangszeile in der Quelldatei, an der die Zuordnung aufgetreten ist.|
|**Quellendzeile**|Die Nummer der Endzeile in der Quelldatei, an der die Zuordnung aufgetreten ist.|
|**Quellanfangszeichen**|Das Offset des Startzeichens in der Quelldateizeile, an dem die Zuordnung aufgetreten ist.|
|**Quellendzeichen**|Der Offset des Endzeichens der Quelldateizeile, an dem die Zuordnung aufgetreten ist.|
|**Zeilenname**|Ein vom Profiler generierter Bezeichner der Zeile mit folgender Syntax:`Source File` **;[** `Line Number Start` **,** `Character Start` **]->;[** `Line Number Start,Character Start` **]**|
|**Exklusive Speicherbelegungen**|Die Gesamtanzahl der Objekte, die in dieser Zeile erstellt wurden.|
|**Exklusive Zuordnungen %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt und in dieser Zeile zugeordnet wurden.|
|**Exklusive Bytes**|Der Prozentsatz aller Bytes im Speicher, die während der Profilerstellung und in dieser Zeile zugeordnet wurden.|
|**Exklusive Bytes %**|Der Prozentsatz aller Bytes im Speicher, die während der Profilerstellung und in dieser Zeile zugeordnet wurden.|

## <a name="see-also"></a>Siehe auch
- [Zeilenansicht](../profiling/lines-view-sampling-data.md)
