---
title: 'Anweisungszeigeransicht: Samplingdaten zum .NET-Speicher'
description: In der Anweisungszeigeransicht der Profilerstellungsdaten für die .NET-Speicherbelegung, die mithilfe der Samplingmethode erfasst wurden, werden die Assemblyanweisungen angezeigt, die Arbeitsspeicher belegt haben.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 51f7c9faee3b93a11b3a2a304654005c80b8ad87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906831"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Anweisungszeigeransicht: Samplingdaten zum .NET-Speicher
In der Anweisungszeigeransicht der Profilerstellungsdaten für die .NET-Speicherbelegung, die mithilfe der Samplingmethode erfasst wurden, werden die Assemblyanweisungen angezeigt, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben. In den Spalten in der Ansicht werden auch die Größe und Anzahl der Zuordnungen aufgeführt.

 Es sind nur exklusive Werte aufgeführt.

|Spalte|Beschreibung|
|------------|-----------------|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses.|
|**Modulname**|Der Name des Moduls, das die Anweisung enthält|
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält|
|**Quelldatei**|Die Quelldatei, die die Anweisung enthält|
|**Funktionsname**|Der Name der Funktion.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Funktionsadresse**|Die Startadresse der Funktion.|
|**Quellanfangszeile**|Die Nummer der Anfangszeile in der Quelldatei, an der die Zuordnung aufgetreten ist.|
|**Quellendzeile**|Die Nummer der Endzeile in der Quelldatei, an der die Zuordnung aufgetreten ist.|
|**Quellanfangszeichen**|Das Offset des Startzeichens in der Quelldateizeile, an dem die Zuordnung aufgetreten ist.|
|**Quellendzeichen**|Der Offset des Endzeichens der Quelldateizeile, an dem die Zuordnung aufgetreten ist.|
|**Anweisungsadresse**|Die Adresse der Anweisung.|
|**Exklusive Speicherbelegungen**|Die Gesamtanzahl der Objekte, die von dieser Anweisung erstellt wurden.|
|**Exklusive Zuordnungen %**|Der Anteil aller Objekte, die während der Profilerstellung erstellt und von dieser Anweisung zugeordnet wurden.|
|**Exklusive Bytes**|Die Anzahl von Bytes im Speicher, die während der Profilerstellung von der Anweisung zugeordnet wurden.|
|**Exklusive Bytes %**|Der Anteil aller Bytes im Speicher, die während der Profilerstellung durch diese Anweisung zugeordnet wurden.|

## <a name="see-also"></a>Weitere Informationen
- [Anweisungszeigeransicht](../profiling/instruction-pointers-ips-view-sampling-data.md)
