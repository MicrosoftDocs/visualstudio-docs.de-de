---
title: 'DA0008: Es wurden nur wenige Beispiele aufgelistet | Microsoft-Dokumentation'
description: Während der Profilerstellung wurden nur wenige Samplings gesammelt.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 483b08972d768e8c0d492f467d845642b5afcea7
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469896"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Es wurden nur wenige Beispiele aufgelistet

|Element|Wert|
|-|-|
|Regel-ID|DA0008|
|Kategorie|Verwendung der Profilerstellungstools|
|Profilerstellungsmethode|Sampling|
|Meldung|Es wurden nur wenige Samplings gesammelt. Sie sollten eine längere Ausführung oder eine schnellere Samplingrate in Betracht ziehen, um aussagekräftigere Ergebnisse zu erzielen.|
|Regeltyp|Information|

## <a name="cause"></a>Ursache
 Während der Profilerstellung wurden nur wenige Samplings gesammelt.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn die Samplingmethode verwendet wird, sollten Sie eine statistisch signifikante Anzahl von Samplings sammeln, um sicherzustellen, dass die Daten für das tatsächliche Programmverhalten repräsentativ sind. Um Samplingfehler zu minimieren, sollten Sie versuchen, mindestens 1.000 Samplings für Programmanweisungsausführungsverhalten zu sammeln. Wenn Sie nicht genug Samplings sammeln, kann die Analyse der Profilerstellungsdaten irreführend sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überlegen Sie, das Profil bei einer längeren Ausführung der Anwendung zu erstellen oder eine schnellere Samplingrate zu verwenden, um statistisch signifikante Ergebnisse zu erzielen. Weitere Informationen zum Ändern der Samplingrate in der Visual Studio IDE finden Sie unter [Vorgehensweise: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md). Weitere Informationen zum Ändern der Samplingrate über die Befehlszeile des Profilerstellungstools finden Sie unter [Timer (Zeitgeber)](../profiling/timer.md) in der [VSPerfCmd](../profiling/vsperfcmd.md)-Referenz.
