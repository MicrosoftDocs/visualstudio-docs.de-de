---
title: 'DA0003: Viele Kernelbeispiele | Microsoft-Dokumentation'
description: Ein großer Teil der Aufruflistensamples, die für die Anwendung gesammelt wurden, wurden im Kernelmodus ausgeführt.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b93bbbcb2026ad6f7ef0d25dc359eb211a6c85f
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469949"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Zahlreiche Kernelbeispiele

|Element|Wert|
|-|-|
|Regel-ID|DA0003|
|Kategorie|Verwendung der Profilerstellungstools|
|Profilerstellungsmethoden|Sampling|
|Meldung|Im Kernelmodus ist ein hoher Anteil von Beispielen vorhanden. Dies deutet auf ein hohes Maß an E/A-Aktivitäten oder auf häufige Kontextwechsel hin. Erstellen Sie nach Möglichkeit ein neues Profil für die Anwendung, und verwenden Sie dabei den Instrumentierungsmodus.|
|Regeltyp|Information|

## <a name="cause"></a>Ursache
 Ein großer Teil der Aufruflistensamples, die für die Anwendung gesammelt wurden, wurden im Kernelmodus ausgeführt. Gegebenenfalls sollten Sie das Profil für Ihre Anwendung mit einer anderen Methode erstellen.

## <a name="rule-description"></a>Regelbeschreibung
 In Windows kann Code im Kernel- oder im Benutzermodus ausgeführt werden. Der Kernelmodus wird auch privilegierter Modus genannt. Nur spezifischer Systemcode auf niedriger Ebene wie ein Gerätetreiber wird im Kernelmodus ausgeführt. Eine Anwendung im Benutzermodus kann in den Kernelmodus wechseln, um E/A-Vorgänge auszuführen, um auf Thread- oder Prozesssynchronisierungsprimitive zu warten oder um Systemaufrufe auszuführen.

 Sampling ist am effektivsten, wenn Sie Profile für Anwendungen erstellen, die sich die meiste Zeit im Benutzermodus befinden. Die Anzahl der Samples, die während der Ausführung der Anwendung im Kernelmodus erfasst wurden, kann auf häufige E/A-Vorgänge oder häufige Kontextwechsel hindeuten. Keiner dieser Vorgänge kann mithilfe der Samplingmethode untersucht werden. Wenn zu viele Samples im Kernelmodus entnommen werden, enthalten die Samplingdaten möglicherweise zu wenig Samples aus dem Benutzermodus, um statistisch signifikant zu sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Erstellen Sie nach Möglichkeit ein neues Profil für die Anwendung, und verwenden Sie dabei eine der folgenden Optionen:

- Profilerstellung mit der Instrumentierungsmethode

- Erhöhen der Samplingrate, um weitere Samples im Benutzermodus zu sammeln
