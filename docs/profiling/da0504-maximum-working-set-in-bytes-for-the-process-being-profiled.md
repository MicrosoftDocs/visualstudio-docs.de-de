---
title: 'DA0504: Maximale Arbeitsseite in Bytes für den Prozess, für den die Profilerstellung ausgeführt wird | Microsoft-Dokumentation'
description: In dieser Meldung wird die maximale Menge an virtuellem Arbeitsspeicher (in Bytes) gemeldet, die derzeit vom Prozess verwendet wird.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7810646f14c61683fc3fc5e3e70eee33ba01dde1
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465789"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Maximale Arbeitsseite in Bytes für den Prozess, für den die Profilerstellung ausgeführt wird

|Element|Wert|
|-|-|
|Regel-ID|DA0504|
|Kategorie|Ressourcenverwaltung|
|Profilerstellungsmethode|Alle|
|Meldung|Diese Information wurde lediglich zu Informationszwecken erhoben. Vom Leistungsindikator für die Verarbeitung von Arbeitsseiten wird die Belegung des physischen Speichers durch den Prozess ermittelt, für den die Profilerstellung ausgeführt wird. Bei dem gemeldeten Wert handelt es sich um den Maximalwert aus allen Messintervallen.|
|Regeltyp|Information|

 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.

## <a name="rule-description"></a>Regelbeschreibung
 In dieser Meldung wird die maximale Menge an virtuellem Arbeitsspeicher (in Bytes) gemeldet, die derzeit vom Prozess verwendet wird. Die Prozessarbeitsseite stellt Seiten aus dem Prozessadressbereich dar, die sich gegenwärtig im physischen Speicher befinden. Von dieser Regel wird der maximale Wert für die Prozessarbeitsseite bei aktiver Profilerstellung gemeldet.

 Der gemeldete Wert enthält residente Seiten aus freigegebenen Arbeitsspeichersegmenten, auf die vom Prozess verwiesen wurde. In den berücksichtigten freigegebenen Arbeitsspeichersegmenten sind auch freigegebene DLLs enthalten, auf die vom Prozess verwiesen wird. Aufgrund von freigegebenen Arbeitsspeichersegmenten kann der Wert der Prozessarbeitsseite die Menge des virtuellen Arbeitsspeichers übersteigen, der vom Prozess belegt wird.

 Die Größe der Prozessarbeitsseite spiegelt die Menge des virtuellen Arbeitsspeichers wider, die aktiv vom Prozess verwendet wird. Sie wird auch von der Menge an physischem Speicher (oder RAM) beeinflusst, die zum Ausführen der Anwendung verfügbar ist, sowie von der Auslastung dieses physischen Speichers durch andere ausgeführte Prozesse. Weitere Informationen zu Prozessarbeitsseiten finden Sie unter [Working Set (Arbeitsseite)](/windows/win32/memory/working-set) in der Dokumentation zur Speicherverwaltung unter Windows auf MSDN.

## <a name="how-to-use-rule-data"></a>Verwenden von Regeldaten
 Diese Messdaten stammen aus der Windows-Leistungsüberwachung und dienen lediglich als Information. Mithilfe der Daten können Sie die Leistung anderer Versionen oder Builds des Programms vergleichen oder die Leistung der Anwendung in unterschiedlichen Testszenarios nachvollziehen.

 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur Ansicht [Markierungen](../profiling/marks-view.md) der Profilerstellungsdaten zu navigieren. Suchen Sie die Spalten mit den Leistungsindikatoren **Prozess\Arbeitsseite** und **Arbeitsspeicher\Seiten/s**. Suchen Sie anschließend den maximalen Wert von **Prozess\Arbeitsseite**, und vergleichen Sie ihn mit dem Wert von **Arbeitsspeicher\Seiten/s**. Häufig hängt der Maximalwert für Arbeitsseiten mit einem Intervall mit geringerer E/A-Auslagerungsaktivität zusammen. Dies gilt besonders bei Computern mit eingeschränktem Arbeitsspeicher.
