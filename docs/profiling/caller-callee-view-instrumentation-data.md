---
title: Aufrufer-/Aufgerufener-Ansicht – Instrumentationsdaten | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie die Aufrufer-/Aufgerufeneransicht Instrumentierungsinformationen in der Aufrufstruktur des Leistungs-Explorers anzeigt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06de8e10c57bdf6278310467d3cf0505b9c8ce4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939486"
---
# <a name="callercallee-view---instrumentation-data"></a>Aufrufer-/Aufgerufener-Ansicht – Instrumentierungsdaten
In der Aufrufer-/Aufgerufener-Ansicht werden Profilerstellungsinformationen zu einer ausgewählten Funktion und ihren übergeordneten und untergeordneten Funktionen in der Aufrufstruktur angezeigt. Die Aufrufer-/Aufgerufener-Ansicht enthält drei Raster.

 **Aktuelle Funktion** wird im mittleren Raster angezeigt und gibt Profilerstellungsinformationen zu der ausgewählten Funktion an. Die Werte enthalten alle Aufrufe an die Funktion.

 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im im obersten Raster angezeigt und gibt Profilerstellungsinformationen zu den aufrufenden (übergeordneten) Funktionen der ausgewählten Funktion an. Die Werte geben den Wert der aktuellen Funktion an, der durch Aufrufe von dieser aufrufenden Funktion generiert wurde.

 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und gibt Profilerstellungsinformationen zu Instanzen der aufgerufenen (untergeordneten) Funktionen der ausgewählten Funktion an. Die Werte geben nur die Zeit an, die in der untergeordneten Funktion aufgewendet wurde, wenn diese von der aktuellen Funktion aufgerufen wurde.

## <a name="general"></a>Allgemein
 Die allgemeinen Spalten bezeichnen die Funktion in einer Ansichtszeile.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**Funktionsname**|Der Name der Funktion.|
|**Funktionsadresse**|Die Adresse der Funktion.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Anzahl der Aufrufe**|Die Gesamtzahl der Aufrufe dieser Funktion.|
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses.|
|**Exklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion. Der zusätzliche Testaufwand wurde von allen exklusiven Zeiten subtrahiert.|
|**Inklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen. Der zusätzliche Testaufwand wurde von allen inklusiven Zeiten subtrahiert.|
|**Type**|Der Kontext der Funktion:<br /><br /> **0** – die aktuelle Funktion<br /><br /> **1** – eine Funktion, die die aktuelle Funktion aufruft<br /><br /> **2** – eine Funktionen, die von der aktuellen Funktion aufgerufen wird<br /><br /> Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|
|**Name der Stammfunktion**|Name der aktuellen Funktion. Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|

## <a name="elapsed-inclusive-values"></a>Werte für verstrichene inklusive Zeit
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst die Zeit in untergeordneten Funktionen und die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabevorgänge.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**verstrichene inklusive Zeit**|- Für die aktuelle Funktion die in der Funktion aufgewendete Zeit. Der Wert umfasst die Zeit in untergeordneten Funktionen und für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.<br />- Bei einer aufrufenden Funktion die Menge an verstrichener inklusiver Zeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />- Bei einer aufgerufenen Funktion die Zeit für die Instanzen der Funktion, die durch Aufrufe aus der aktuellen Funktion generiert wurden. Der Wert umfasst die Zeit in untergeordneten Funktionen der aufgerufenen Funktion und die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabevorgänge.|
|**verstrichene inklusive Zeit %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|
|**Durchschnittlich verstrichene inklusive Zeit**|Die durchschnittliche verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Maximal verstrichene inklusive Zeit**|Die maximale verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|

## <a name="elapsed-exclusive-values"></a>Werte für verstrichene exklusive Zeit
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle der Aufrufliste ausgeführt wurde. Sie umfasst nur den zeitlichen Aufwand für Aufrufe des Betriebssystems (z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen), aber nicht die Zeit, die für untergeordnete Funktionen aufgewendet wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**verstrichene exklusive Zeit**|- Bei der aktuellen Funktion die Zeit, die für die direkte Ausführung der Funktion aufgewendet wurde. Der Wert umfasst die Zeit in untergeordneten Funktionen und für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.<br />- Bei einer aufrufenden Funktion die Menge an verstrichener exklusiver Zeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />- Bei einer aufgerufenen Funktion die Zeit für die Instanzen der Funktion, die durch Aufrufe aus der aktuellen Funktion generiert wurden. Der Wert umfasst die Zeit für Aufrufe des Betriebssystems (z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen), jedoch nicht die Zeit in untergeordneten Funktionen der aufgerufenen Funktion.|
|**verstrichene exklusive Zeit %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der gesamten verstrichenen exklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|
|**Durchschnittlich verstrichene exklusive Zeit**|Die durchschnittliche verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Maximal verstrichene exklusive Zeit**|Die maximale verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Mindestens verstrichene exklusive Zeit**|Die mindestens verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|

## <a name="application-inclusive-values"></a>Werte für inklusive Anwendungszeit
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst die Zeit in untergeordneten Funktionen, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**inklusive Anwendungszeit**|- Bei der aktuellen Funktion die Zeit, die für die Funktion und ihre untergeordneten Funktionen aufgewendet wurde. Der Wert umfasst nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.<br />- Bei einer aufrufenden Funktion die Menge an inklusiver Anwendungszeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />- Bei einer aufgerufenen Funktion die Zeit für die Instanzen der Funktion, die durch Aufrufe aus der aktuellen Funktion generiert wurden. Der Wert umfasst die Zeit in untergeordneten Funktionen der aufgerufenen Funktion, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabevorgänge.|
|**inklusive Anwendungszeit %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit, die innerhalb der gesamten inklusiven Anwendungszeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|
|**Durchschnittliche inklusive Anwendungszeit**|Die durchschnittliche inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Maximale inklusive Anwendungszeit**|Die maximale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Minimale inklusive Anwendungszeit**|Die minimale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|

## <a name="application-exclusive-values"></a>Werte für exklusive Anwendungszeit
 Werte für die exklusive Anwendungszeit geben die Zeit an, die in der Funktion verbracht wurde. Sie umfasst weder den zeitlichen Aufwand für untergeordnete Funktionen noch die Zeit, die für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen) aufgewendet wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**exklusive Anwendungszeit**|- Bei der aktuellen Funktion die Zeit, die für die direkte Ausführung der Funktion aufgewendet wurde. Der Wert umfasst weder die Zeit in untergeordneten Funktionen noch die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.<br />- Bei einer aufrufenden Funktion die Menge an exklusiver Anwendungszeit für die aktuelle Funktion, die von Aufrufen aus dieser aufrufenden Funktion generiert wurde.<br />- Bei einer aufgerufenen Funktion die Zeit für die Instanzen der Funktion, die durch Aufrufe aus der aktuellen Funktion generiert wurden. Der Wert umfasst weder die Zeit in untergeordneten Funktionen der aufgerufenen Funktion noch die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.|
|**Exklusive Anwendungszeit %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der exklusiven Gesamtanwendungszeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|
|**Durchschnittliche exklusive Anwendungszeit**|Die durchschnittliche exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Minimale exklusive Anwendungszeit**|Die minimale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)
- [Aufrufer-/Aufgerufener-Ansicht: Samplingdaten](../profiling/caller-callee-view-sampling-data.md)
- [Aufrufer-/Aufgerufener-Ansicht – .NET-Speichersamplingdaten](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Aufrufer-/Aufgerufener-Ansicht – .NET-Speicherinstrumentierungsdaten](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
