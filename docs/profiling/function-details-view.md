---
title: Funktionsdetailansicht | Microsoft-Dokumentation
description: Im Leistungs-Explorer erfahren Sie mehr über das Fenster „Function Details View“ (Funktionsdetailansicht), das Balkendiagramm „Kostenverteilung“, die Tabelle „Funktionsleistungsdetails“ und das Fenster „Funktionscodeansicht“.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6e812f0fdef46d0ac5ef42788c2f854922a7375c
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801260"
---
# <a name="function-details-view"></a>Funktionsdetailansicht
Im Fenster **Funktionsdetailansicht** werden folgende Informationen angezeigt:

- Im Balkendiagramm **Kostenverteilung** werden die Beziehungen zwischen einer von Ihnen ausgewählten Funktion und den aufrufenden Funktionen dargestellt, die die ausgewählte Funktion ausgeführt haben. Zudem wird die Beziehung zwischen der ausgewählten Funktion und den von dieser Funktion aufgerufenen Funktionen angezeigt.

- Die Tabelle **Funktionsleistungsdetails**, in der die Zusammenfassungsdaten zur Profilerstellung für die von Ihnen angegebene Funktion angezeigt werden.

- Das Fenster **Funktionscodeansicht**, in dem der Funktionscode angezeigt wird, wenn der Code verfügbar ist.

  Das Fenster **Funktionscodeansicht** ist ein getrennter Bereich. Die zwei Bereiche sind standardmäßig horizontal geteilt, und das Fenster **Funktionscodeansicht** befindet sich am unteren Rand des Frames.

- Klicken Sie in der Symbolleiste auf **Bildschirm vertikal teilen**, um die zwei Bereiche vertikal zu teilen.

- Klicken Sie auf den schattierten Rahmen zwischen den Frames, und ziehen Sie den Rahmen an eine andere Position, um die relative Größe der Bereiche zu ändern.

## <a name="cost-distribution-bar-chart"></a>Balkendiagramm zur Kostenverteilung

### <a name="performance-metrics"></a>Leistungsmetriken
 Sie können in der Dropdownliste **Leistungsmetriken** angeben, welche Werte in der Ansicht angezeigt werden. Welche Werte verfügbar sind, hängt von der Profilerstellungsmethode ab, die in der Profilerstellungs-Datendatei verwendet wurde. Bei den Namen in Klammern handelt es sich um die Namen der Zeilen in der Tabelle **Funktionsleistungsdetails**.

### <a name="bar-chart"></a>Balkendiagramm
 **Aufrufende Funktionen**

 In der Leiste **Aufrufende Funktionen** werden die Funktionen angezeigt, die die ausgewählte Funktion aufgerufen haben. Die Größe des Blocks mit der aufrufenden Funktion ist relativ zum Beitrag der aufrufenden Funktion zum Gesamtwert der Leistungsmetrik für die ausgewählte Funktion.

 Sie können auf den Namen einer aufrufenden Funktion klicken, um sie in der Funktionsdetailansicht auszuwählen.

- Wenn zu viele aufrufende Funktionen zum Auflisten vorhanden sind, werden Funktionen mit den kleinsten Beiträgen im Block **Andere** erfasst. Klicken Sie auf **Andere**, um alle aufrufenden und aufgerufenen Funktionen der ausgewählten Funktion im Fenster **Aufrufer-/Aufgerufener-Ansicht** anzuzeigen. Weitere Informationen finden Sie unter [Aufrufer-/Aufgerufener-Ansicht](../profiling/caller-callee-view.md).

- Wenn keine aufrufenden Funktionen vorhanden sind oder es sich bei der Funktion um die Eingabefunktion eines Threads oder Prozesses handelt, wird der Block **Anfang des Stapels** angezeigt.

  **Ausgewählte Funktion**

  In der Leiste „Ausgewählte Funktion“ werden die Beiträge der aufgerufenen Funktionen und des Codes in der ausgewählten Funktion zur gesamten Leistungsmetrik der ausgewählten Funktion angezeigt. Die Größe des Blocks mit der aufgerufenen Funktion oder dem Funktionsrumpf ist relativ zum Beitrag zum Gesamtwert der Leistungsmetrik für die ausgewählte Funktion.

  Sie können auf den Namen einer aufgerufenen Funktion klicken, um sie in der Funktionsdetailansicht auszuwählen.

- Der **Gesamtwert** ist die Leistungsmetrik der ausgewählten Funktion.

- Im Block **Funktionsrumpf** wird der Gesamtwert der Leistungsmetrik angezeigt, der bei der direkten Ausführung des Codes im Funktionsrumpf aufgetreten ist.

- Funktionen, die von der ausgewählten Funktion aufgerufen werden, werden in Blöcken aufgeführt. Die Größe des Blocks „Ausgewählte Funktionen“ stellt den Betrag der gesamten Leistungsmetrik für die ausgewählte Funktion dar, die in der aufgerufenen Funktion aufgetreten ist.

- Wenn zu viele aufrufende Funktionen zum Auflisten vorhanden sind, werden Funktionen mit den kleinsten Beiträgen im Block **Andere** erfasst. Klicken Sie auf **Andere**, um alle aufrufenden und aufgerufenen Funktionen der ausgewählten Funktion im Fenster **Aufrufer-/Aufgerufener-Ansicht** anzuzeigen. Weitere Informationen finden Sie unter [Aufrufer-/Aufgerufener-Ansicht](../profiling/caller-callee-view.md).

- Wenn keine aufgerufenen Funktionen vorhanden sind, wird der Block **Ende des Stapels** angezeigt.

## <a name="function-performance-details"></a>Funktionsleistungsdetails
 Die Tabelle „Funktionsleistungsdetails“ enthält Zusammenfassungsdaten zu den Leistungsmetriken der ausgewählten Funktion. Sowohl der Wert als auch der Prozentsatz werden angezeigt. In der Liste **Leistungsmetriken** können Sie die Profilerstellungsdaten eingeben, die im Diagramm und in der Detailtabelle angezeigt werden.

|Spalte|Beschreibung|
|------------|-----------------|
|**Exklusiv**|– Der Betrag der Leistungsmetrik, die bei der Ausführung des Funktionsrumpfs aufgetreten ist.|
|**In Aufrufen**|– Der Betrag der Leistungsmetrik, die in Funktionen aufgetreten ist, die von der ausgewählten Funktion aufgerufen wurden.|
|**Inklusive insgesamt**|– Der Gesamtbetrag der Werte **Exklusiv** und **In Aufrufen**.|

## <a name="function-code-view"></a>Funktionscodeansicht
 Im Fenster **Funktionscodeansicht** wird eine Liste des Quellcodes angezeigt, wenn diese verfügbar ist. Neben den Quellcodepositionen, die andere Funktionen aufrufen, enthält eine schattierte Spalte die Leistungsmetrikwerte der aufgerufenen Funktion. Klicken Sie zur Bearbeitung des Quellcodes auf den Link zur Quellcodedatei.

## <a name="cost-distribution-bar-chart-values"></a>Werte des Balkendiagramms zur Kostenverteilung

### <a name="sampling"></a>Sampling
 In der folgenden Tabelle werden die Werte in der Liste „Leistungsmetriken“ für Profilerstellungsdaten erläutert, die mit der Samplingmethode erfasst wurden.

|Wert|Beschreibung|
|-|-|
|**Inklusive Samplings (Aufgelistete Samplings)**|– Bei einer aufrufenden Funktion die Anzahl der Samplings, die erfasst wurden, als die ausgewählte Funktion mit dieser aufrufenden Funktion aufgerufen wurde.<br />– Beim Funktionsrumpf die Anzahl der Samplings, die erfasst wurden, als die ausgewählte Funktion einen eigenen Code ausgeführt hat.<br />– Bei einer aufgerufenen Funktion die Anzahl der Samplings, die erfasst wurden, als die aufgerufene Funktion wegen eines Aufrufs der ausgewählten Funktion ausgeführt wurde.|

### <a name="instrumentation"></a>Instrumentierung
 In der folgenden Tabelle werden die Werte in der Liste „Leistungsmetriken“ für Profilerstellungsdaten erläutert, die mit der Instrumentierungsmethode erfasst wurden.

|Wert|Beschreibung|
|-|-|
|**Verstrichene inklusive Zeit (verstrichene Zeit)**|Die verstrichene Zeit umfasst die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.<br /><br /> – Bei einer **Aufrufenden Funktion** die Zeit, die beim Ausführen der über die Funktion aufgerufenen zugehörigen Instanzen verstrichen ist. Dies umfasst die Zeit für Funktionen, die von der ausgewählten Funktion aufgerufen wurden.<br />– Beim **Funktionsrumpf** die Gesamtzeit, die beim Ausführen des Codes der ausgewählten Funktion verstrichen ist. Dies umfasst nicht die Zeit für aufgerufene Funktionen.<br />– Bei einer aufgerufenen Funktion die Zeit für die Ausführung der über die ausgewählte Funktion aufgerufenen zugehörigen Instanzen der Funktion. Die Summe umfasst die Zeit, die für von der Funktion aufgerufene Funktionen aufgewendet wurde. Dies umfasst die Zeit für Funktionen, die von der ausgewählten Funktion aufgerufen wurden.|
|**Inklusive Anwendungszeit (Anwendungszeit)**|Die Anwendungszeit umfasst nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.<br /><br /> – Bei einer **aufrufenden Funktion** die Anwendungszeit für die Ausführung der Instanzen der ausgewählten Funktion, die von der Funktion aufgerufen wurden. Dies umfasst die Zeit für Funktionen, die von der ausgewählten Funktion aufgerufen wurden.<br />– Beim **Funktionsrumpf** die gesamte Anwendungszeit für die Ausführung des Codes der ausgewählten Funktion. Dies umfasst nicht die Zeit für aufgerufene Funktionen.<br />– Bei einer aufgerufenen Funktion die Anwendungszeit für die Ausführung der über die ausgewählte Funktion aufgerufenen Instanzen der Funktion. Die Summe umfasst die Zeit, die für von der Funktion aufgerufene Funktionen aufgewendet wurde.|

### <a name="net-memory"></a>.NET-Arbeitsspeicher
 In der folgenden Tabelle werden die Werte in der Liste „Leistungsmetriken“ für Profilerstellungsdaten erläutert, die mit der .NET-Profilerstellungsmethode erfasst wurden.

|Wert|Beschreibung|
|-|-|
|**Inklusive Zuordnungen (Zuordnungen)**|– Bei einer **aufrufenden Funktion** die Anzahl von Objekten, die von den Instanzen der ausgewählten Funktion zugeordnet wurden, die von der Funktion aufgerufen wurden. Die Zahl umfasst Objekte, die von den von der ausgewählten Funktion aufgerufenen Funktionen zugeordnet wurden.<br />– Beim **Funktionsrumpf** die Anzahl von Objekten, die von der ausgewählten Funktion zugeordnet wurden, als diese ihren eigenen Code ausgeführt hat. In Funktionen zugeordnete Objekte, die von der ausgewählten Funktion aufgerufen wurden, sind nicht enthalten.<br />– Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den Instanzen der Funktion zugeordnet wurden, die von der ausgewählten Funktion aufgerufen wurden. Die Zahl umfasst Objekte, die von den von der Funktion aufgerufenen Funktionen zugeordnet wurden.|
|**Inklusive Bytes (Bytes)**|– Bei einer **aufrufenden Funktion** die Anzahl von Bytes, die von den Instanzen der ausgewählten Funktion zugeordnet wurden, die von der Funktion aufgerufen wurden. Die Zahl umfasst Bytes, die in von der ausgewählten Funktion aufgerufenen Funktionen zugeordnet wurden.<br />– Beim **Funktionsrumpf** die Gesamtzahl von Objekten, die von der ausgewählten Funktion zugeordnet wurden, als diese ihren eigenen Code ausgeführt hat. In Funktionen zugeordnete Bytes, die von der ausgewählten Funktion aufgerufen wurden, sind nicht enthalten.<br />– Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den Instanzen der Funktion zugeordnet wurden, die von der ausgewählten Funktion aufgerufen wurden. Die Zahl umfasst Bytes, die in von der Funktion aufgerufenen Funktionen zugeordnet wurden.|

### <a name="concurrency"></a>Parallelität
 In der folgenden Tabelle werden die Werte in der Liste „Leistungsmetriken“ für Profilerstellungsdaten erläutert, die mit der Parallelitätsmethode erfasst wurden.

|Wert|Beschreibung|
|-|-|
|**Inklusive Konflikte (Konflikte)**|– Bei einer **aufrufenden Funktion** die Anzahl von Ressourcenkonfliktereignissen, die in den Instanzen der ausgewählten Funktion aufgetreten sind, die von der Funktion aufgerufen wurden. Die Zahl umfasst Konfliktereignisse in Funktionen, die in von der ausgewählten Funktion aufgerufen wurden.<br />– Beim **Funktionsrumpf** die Gesamtzahl der Konfliktereignisse, die aufgetreten sind, als die Funktion ihren eigenen Code ausgeführt hat. Dies umfasst nicht die Konflikte, die von der ausgewählten Funktion aufgerufen wurden.<br />– Bei einer aufgerufenen Funktion die Anzahl von Ressourcenkonfliktereignissen, die in den Instanzen der ausgewählten Funktion aufgetreten sind, die von der Funktion aufgerufen wurden. Die Zahl umfasst Konfliktereignisse, die in von der Funktion aufgerufenen Funktionen aufgetreten sind.|
|**Inklusive blockierte Zeit (Blockierte Zeit)**|– Bei einer aufrufenden Funktion die Zeit für Ressourcenkonfliktereignisse für die Instanzen der ausgewählten Funktion, die von der Funktion aufgerufen wurden. Die Zeit umfasst die blockierte Zeit in Funktionen, die die ausgewählte Funktion aufgerufen hat.<br />– Beim **Funktionsrumpf** die Gesamtzeit für Konfliktereignisse, die aufgetreten sind, als die Funktion ihren eigenen Code ausgeführt hat. Dies umfasst nicht die Konflikte, die in Funktionen auftreten, die von der ausgewählten Funktion aufgerufen wurden.<br />– Bei einer aufgerufenen Funktion die Zeit für Ressourcenkonfliktereignisse für die Instanzen der Funktion, die von der ausgewählten Funktion aufgerufen wurden. Die Zeit umfasst die blockierte Zeit in Funktionen, die die Funktion aufgerufen hat.|
