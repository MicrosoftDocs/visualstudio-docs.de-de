---
title: 'DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 65fed5b7afd6c8b1a678a9ef94b8c86e6dc88500
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918076"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird.

|Element|Wert|
|-|-|
|Regel-ID|DA501|
|Kategorie|Ressourcenüberwachung|
|Profilerstellungsmethode|Alle|
|Meldung|Durchschnittliche CPU-Auslastung durch den Prozess, für den die Profilerstellung ausgeführt wird.|
|Regeltyp|Information|

 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.

## <a name="rule-description"></a>Regelbeschreibung
 In dieser Meldung wird der Prozentsatz der Zeit angegeben, die ein Prozessor mit dem Ausführen von Anweisungen aus der Anwendung beschäftigt war. Bei dem gemeldeten Wert handelt es sich um den Durchschnittswert aller Messintervalle, in denen der Prozess, dessen Profil erstellt wird, aktiv war. Bei einem Computer mit mehreren Prozessoren kann der Wert 100 Prozent übersteigen.

## <a name="how-to-use-rule-data"></a>Verwenden von Regeldaten
 Mithilfe des Regelwerts können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Testszenarios nachvollziehen.
