---
title: Funktionsansicht – Instrumentierungsdaten | Microsoft-Dokumentation
description: In diesem Artikel werden die Profilerstellungsdaten-Spalten in der Berichtsansicht „Funktionen“ beschrieben, in der Profilerstellungsdaten nach Funktionsname aufgelistet sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2b12fc05f9eeb9b77e982c62ae52bfbbe784f5e6
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801362"
---
# <a name="functions-view---instrumentation-data"></a>Funktionsansicht: Instrumentierungsdaten
Die Funktionsberichtansicht listet die Profilerstellungsdaten nach Funktionsnamen auf.

## <a name="general"></a>Allgemein
 Die allgemeinen Spalten bezeichnen die Funktion in einer Ansichtszeile.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**Funktionsname**|Der Name der Funktion.|
|**Funktionsadresse**|Die Adresse der Funktion.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Anzahl der Aufrufe**|Die Gesamtzahl der Aufrufe der Funktion.|
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses.|
|**Exklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentierung verursachte zusätzliche Zeitaufwand für diese Funktion. Dieser umfasst nicht den zusätzlichen Zeitaufwand für Funktionen, die von dieser Funktion aufgerufen wurden. Der zusätzliche Testaufwand wurde von allen exklusiven Zeiten subtrahiert.|
|**Inklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentierung verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen. Dieser umfasst auch den zusätzlichen Zeitaufwand für Funktionen, die von dieser Funktion aufgerufen wurden. Der zusätzliche Testaufwand wurde von allen inklusiven Zeiten subtrahiert.|

## <a name="elapsed-inclusive-values"></a>Werte für verstrichene inklusive Zeit
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst die Zeit in Funktionen, die von der Funktion aufgerufen wurden, und die Zeit, die für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen benötigt wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**verstrichene inklusive Zeit**|Die insgesamt verstrichene inklusive Zeit aller Aufrufe dieser Funktion.|
|**verstrichene inklusive Zeit %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion auf die Profilerstellung entfällt.|
|**Durchschnittlich verstrichene inklusive Zeit**|Die durchschnittlich verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|
|**Maximal verstrichene inklusive Zeit**|Die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|

## <a name="elapsed-exclusive-values"></a>Werte für verstrichene exklusive Zeit
 Werte für die verstrichene inklusive Zeit geben an, wie lange ein Code im Text einer Funktion ausgeführt wurde, sprich, wie lange sich die Funktion ganz oben in der Aufrufliste befunden hat. Die Zeit umfasst die Zeit, die mit Aufrufen an das Betriebssystem verbracht wurde, wie z.B. Kontextwechsel oder Eingabe-/Ausgabeoperationen; sie beinhaltet jedoch nicht die Zeit, die in Funktionen verbracht wurde, die von der Funktion aufgerufen wurden.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**verstrichene exklusive Zeit**|Die insgesamt verstrichene exklusive Zeit aller Aufrufe dieser Funktion.|
|**verstrichene exklusive Zeit %**|Der Prozentsatz der während der Profilerstellung insgesamt verstrichenen exklusiven Zeit, die sich auf die insgesamt verstrichene exklusive Zeit dieser Funktion bezieht.|
|**Durchschnittlich verstrichene exklusive Zeit**|Die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|
|**Maximal verstrichene exklusive Zeit**|Die maximal verstrichene exklusive Zeit für einen Aufruf dieser Funktion.|
|**Mindestens verstrichene exklusive Zeit**|Die verstrichene exklusive Mindestzeit für einen Aufruf dieser Funktion.|

## <a name="application-inclusive-values"></a>Werte für inklusive Anwendungszeit
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst nicht die Zeit, die mit Aufrufen an das Betriebssystem verbracht wurde, wie z.B. Kontextwechsel oder Eingabe-/Ausgabeoperationen; sie beinhaltet jedoch die Zeit, die in Funktionen verbracht wurde, die von der Funktion aufgerufen wurden.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**inklusive Anwendungszeit**|Die insgesamt verstrichene inklusive Zeit aller Aufrufe dieser Funktion.|
|**inklusive Anwendungszeit %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit, die innerhalb der gesamten inklusiven Anwendungszeit dieser Funktion auf die Profilerstellung entfällt.|
|**Durchschnittliche inklusive Anwendungszeit**|Die im Durchschnitt für einen Aufruf dieser Funktion aufgewendete inklusive Anwendungszeit.|
|**Maximale inklusive Anwendungszeit**|Die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|
|**Minimale inklusive Anwendungszeit**|Die mindestens verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|

## <a name="application-exclusive-values"></a>Werte für exklusive Anwendungszeit
 Werte für exklusive Anwendungszeit geben die Zeit an, die eine Funktion direkt an erster Stelle der Aufrufliste ausgeführt wurde. Die Zeit umfasst nicht die Zeit, die mit Aufrufen an das Betriebssystem verbracht wurde, wie z.B. Kontextwechsel oder Eingabe-/Ausgabeoperationen; sie beinhaltet auch nicht die Zeit, die in Funktionen verbracht wurde, die von der Funktion aufgerufen wurden.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**exklusive Anwendungszeit**|Die gesamte exklusive Anwendungszeit aller Aufrufe dieser Funktion.|
|**Exklusive Anwendungszeit %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der exklusiven Gesamtanwendungszeit dieser Funktion auf die Profilerstellung entfällt.|
|**Durchschnittliche exklusive Anwendungszeit**|Die im Durchschnitt für einen Aufruf dieser Funktion aufgewendete exklusive Anwendungszeit.|
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit für einen Aufruf dieser Funktion.|
|**Minimale exklusive Anwendungszeit**|Die exklusive Mindestanwendungszeit für einen Aufruf dieser Funktion.|

## <a name="see-also"></a>Siehe auch
- [How to: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)
- [Funktionsansicht](../profiling/functions-view-sampling-data.md)
- [Funktionsansicht: Sampling](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Funktionsansicht: Instrumentierung](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
