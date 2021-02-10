---
title: Datenwerte zur Arbeitsspeicherbelegung und Objektlebensdauer
description: In diesem Artikel erhalten Sie Informationen zur Profilerstellungsmethode für die .NET-Arbeitsspeicherbelegung. Hierbei werden Informationen zu Größe und Anzahl der Objekte gesammelt, die bei einer Speicherbelegung erstellt wurden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2faabb8d37cdebf1bdd6c83d10356edc1ce78690
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921930"
---
# <a name="understand-memory-allocation-and-object-lifetime-data-values"></a>Datenwerte zur Speicherbelegung und Objektlebensdauer

Die Profilerstellungsmethode *.NET-Speicherbelegung* der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools sammelt Informationen zu Größe und Anzahl von Objekten, die in einer Zuordnung erstellt oder bei einer Garbage Collection zerstört wurden, sowie weitere Informationen zur *Aufrufliste* der Funktion zu dem Zeitpunkt, als das Ereignis aufgetreten ist. Eine *Aufrufliste* ist eine dynamische Struktur, die Informationen über die Funktionen speichert, die auf dem Prozessor ausgeführt werden.

Bei der Speicherprofilerstellung wird der Computerprozessor bei jeder Zuordnung eines .NET Framework-Objekts in einer profilierten Anwendung unterbrochen. Wenn auch Objektlebensdauerdaten erfasst werden, unterbricht der Profiler den Prozessor nach jeder .NET Framework-Garbage Collection. Die Daten werden für jede profilierte Funktion und jeden Objekttyp aggregiert.

## <a name="allocation-data"></a>Speicherbelegungsdaten

Wenn ein Speicherereignis auftritt, werden die Gesamtzahlen und Größen der zugeordneten oder zerstörten Speicherobjekte erhöht.

Wenn ein Speicherbelegungsereignis auftritt, erhöht der Profiler die Samplinganzahl für jede Funktion in der Aufrufliste. Wenn die Daten erfasst werden, führt gerade nur eine Funktion auf der Aufrufliste den Code in ihrem Funktionsrumpf aus. Die anderen Funktionen in der Liste sind übergeordnete Elemente in der Hierarchie von Funktionsaufrufen, die auf den Abschluss der Funktionen warten, die sie aufgerufen haben.

- Für das Belegungsereignis erhöht der Profiler die *exklusive* Samplinganzahl der Funktion, die gerade die Anweisungen ausführt. Da ein exklusives Sampling auch Teil der gesamten (*inklusiven*) Samplings der Funktion ist, wird die inklusive Samplinganzahl der aktuell aktiven Funktion auch erhöht.

- Der Profiler erhöht die inklusive Samplinganzahl aller anderen Funktionen in der Aufrufliste.

## <a name="lifetime-data"></a>Lebensdauerdaten

Der Garbage Collector von .NET Framework verwaltet die Belegung und Freigabe von Arbeitsspeicher für die Anwendung. Zur Optimierung der Leistung des Garbage Collectors wird der verwaltete Heap in drei Generationen unterteilt: 0, 1 und 2. Der Garbage Collector der Laufzeit speichert neue Objekte in Generation 0. Objekte, die nach den Garbage Collections noch vorhanden sind, werden höhergestuft und in den Generationen 1 und 2 gespeichert.

Der Garbage Collector gibt Arbeitsspeicher frei, indem er eine ganze Generation von Objekten freigibt. Für die von der profilierten Anwendung erstellten Objekte werden in der Objektlebensdaueransicht die Zahl und die Größe der Objekte sowie die Generation angezeigt, in der diese freigegeben werden.
