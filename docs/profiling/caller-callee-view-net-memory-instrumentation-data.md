---
title: Aufrufer-/Aufgerufener-Ansicht – .NET-Speicherinstrumentationsdaten | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie mehr über die Aufrufer-/Aufgerufener-Ansicht der Profilerstellungsdaten des .NET-Arbeitsspeichers, die Speicherbelegungs- und Zeitsteuerungsdaten für eine ausgewählte Funktion und ihre übergeordneten und untergeordneten Funktionen enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3fa4928f9da81b2141eec76e54bce7887f50a074
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148077"
---
# <a name="callercallee-view---net-memory-instrumentation-data"></a>Aufrufer-/Aufgerufener-Ansicht: .NET-Speicherinstrumentationsdaten
Die Aufrufer/Aufgerufener-Ansicht für Profilerstellungsdaten zum .NET-Speicher, die mit der Instrumentationsmethode gesammelt wurden, zeigt Belegungs- und Zeitsteuerungsdaten für eine ausgewählte Funktion und die übergeordneten und untergeordneten Funktionen dieser ausgewählten Funktion an. Die Aufrufer-/Aufgerufener-Ansicht enthält drei Raster.

 **Aktuelle Funktion** wird im mittleren Raster angezeigt und gibt Speicherinformationen zur Profilerstellung für die ausgewählte Funktion an. Die Werte umfassen alle Samplingaufrufe der Funktion.

 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und gibt den Wert der ausgewählten (aktuellen) Funktion an, die durch Aufrufe der (übergeordneten) Aufruferfunktion generiert wurde.

 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und gibt Speicherdaten zur Profilerstellung für die aufgerufenen (untergeordneten) Funktionen der ausgewählten Funktion an, wenn die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.

 Doppelklicken Sie auf eine Zeile einer Aufrufer- oder Aufgerufener-Funktion, um diese Zeile zur aktuellen Funktion zu machen.

## <a name="general"></a>Allgemein

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**Funktionsname**|Der Name der Funktion.|
|**Funktionsadresse**|Die Adresse der Funktion.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Anzahl der Aufrufe**|Die Gesamtzahl der Aufrufe der Funktion.|
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|
|**Prozess-ID**|Die Prozess-ID der Profilerstellung.|
|**Prozessname**|Der Name, der dem Prozess zugewiesen ist.|
|**Exklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion. Der zusätzliche Testaufwand wurde von allen exklusiven Zeiten subtrahiert.|
|**Inklusive Zeit der Restkapazität für Überprüfungen**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen. Der zusätzliche Testaufwand wurde von allen inklusiven Zeiten subtrahiert.|
|**Type**|Der Kontext der Funktion:<br /><br /> **0** – die aktuelle Funktion<br /><br /> **1** – eine Funktion, die die aktuelle Funktion aufruft<br /><br /> **2** – eine Funktionen, die von der aktuellen Funktion aufgerufen wird<br /><br /> Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|
|**Name der Stammfunktion**|Name der aktuellen Funktion. Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|

## <a name="net-memory-allocation-values"></a>Werte zur .NET-Speicherbelegung

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**Exklusive Speicherbelegungen**|- Bei der aktuellen Funktion die Anzahl der Objekte, die während der Ausführung von Code im Funktionsrumpf erstellt wurden (d.h., während sich die Funktion an erster Stelle der Aufrufliste befand). Diese Zahl umfasst keine Objekte, die in den von dieser Funktion aufgerufenen Funktionen erstellt wurden.<br />- Bei einer aufrufenden Funktion die Anzahl der exklusiven Belegungen der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />- Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den Instanzen dieser Funktion erstellt wurden, die von der aktuellen Funktion aufgerufen wurden. Diese Zahl umfasst keine Objekte, die von den von der aufgerufenen Funktion aufgerufenen Funktionen erstellt wurden.|
|**Exklusive Zuordnungen %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und exklusive Belegungen dieser Funktion waren.|
|**Inklusive Zuordnungen**|- Bei der aktuellen Funktion die Anzahl der Objekte, die während der Profilerstellung von der Funktion belegt wurden. Die Zahl umfasst auch Objekte, die in den von der Funktion aufgerufenen Funktionen erstellt wurden.<br />- Bei einer aufrufenden Funktion die Anzahl von inklusiven Belegungen der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />- Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden. Diese Zahl umfasst Belegungen durch Funktionen, die von dieser aufgerufenen Funktion aufgerufen wurden.|
|**Inklusive Speicherbelegungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und inklusive Belegungen dieser Funktion waren.|
|**Exklusive Bytes**|- Bei der aktuellen Funktion die Anzahl der Bytes im Arbeitsspeicher, die während der Profilerstellung von der Funktion belegt wurden. Diese Zahl umfasst nicht den Speicher, der in den von der Funktion aufgerufenen Funktionen belegt wurde.<br />- Bei einer aufrufenden Funktion die Anzahl von exklusiven Bytes der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />- Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden. Diese Zahl umfasst nicht die Bytes, die in den von der Funktion aufgerufenen Funktionen zugeordnet wurden.|
|**Exklusive Bytes %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und exklusive Belegungen dieser Funktion waren.|
|**Inklusive Bytes**|- Bei der aktuellen Funktion die Anzahl der Bytes im Arbeitsspeicher, die während der Profilerstellung von der Funktion belegt wurden. Diese Zahl umfasst nicht den Speicher, der in den von der Funktion aufgerufenen Funktionen belegt wurde.<br />- Bei einer aufrufenden Funktion die Anzahl von inklusiven Bytes der Instanzen der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />- Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden. Die Zahl umfasst auch Bytes, die in von dieser aufgerufenen Funktion aufgerufenen Funktionen zugeordnet wurden.|
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und inklusive Belegungen dieser Funktion waren.|

## <a name="elapsed-inclusive-values"></a>Werte für verstrichene inklusive Zeit
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst den zeitlichen Aufwand für untergeordnete Funktionen und Aufrufe des Betriebssystems (z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen).

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**verstrichene inklusive Zeit**|- Für die aktuelle Funktion die in der Funktion aufgewendete Zeit. Der Wert umfasst die Zeit in untergeordneten Funktionen und für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.<br />- Bei einer aufrufenden Funktion die Menge an verstrichener inklusiver Zeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />- Bei einer aufgerufenen Funktion die Zeit in dieser Funktion, die auf Aufrufe aus der aktuellen Funktion entfällt. Der Wert umfasst die Zeit in untergeordneten Funktionen und für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.|
|**verstrichene inklusive Zeit %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|
|**Durchschnittlich verstrichene inklusive Zeit**|Die durchschnittliche verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Maximal verstrichene inklusive Zeit**|Die maximale verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|

## <a name="elapsed-exclusive-values"></a>Werte für verstrichene exklusive Zeit
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle der Aufrufliste ausgeführt wurde. Sie umfasst nur den zeitlichen Aufwand für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe-/Ausgabeoperationen), aber nicht die Zeit, die für untergeordnete Funktionen aufgewendet wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**verstrichene exklusive Zeit**|- Bei der aktuellen Funktion die Zeit, die für die direkte Ausführung im Funktionsrumpf aufgewendet wurde. Der Wert umfasst nicht die Zeit in untergeordneten Funktionen, Aufrufe des Betriebssystems (z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen) sind jedoch enthalten.<br />- Bei einer aufrufenden Funktion die Menge an verstrichener exklusiver Zeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />- Bei einer aufgerufenen Funktion die Zeit in dieser Funktion, die auf Aufrufe aus der aktuellen Funktion entfällt. Der Wert umfasst die Zeit für Aufrufe des Betriebssystems (z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen), jedoch nicht die Zeit in untergeordneten Funktionen der aufgerufenen Funktion.|
|**verstrichene exklusive Zeit %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der gesamten verstrichenen exklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|
|**Durchschnittlich verstrichene exklusive Zeit**|Die durchschnittliche verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Maximal verstrichene exklusive Zeit**|Die maximale verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Mindestens verstrichene exklusive Zeit**|Die mindestens verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|

## <a name="application-inclusive-values"></a>Werte für inklusive Anwendungszeit
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst die Zeit in untergeordneten Funktionen, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**inklusive Anwendungszeit**|- Bei der aktuellen Funktion die Zeit, die für die Funktion und ihre untergeordneten Funktionen aufgewendet wurde. Der Wert umfasst nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.<br />- Bei einer aufrufenden Funktion die Menge an inklusiver Anwendungszeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />- Bei einer aufgerufenen Funktion die Zeit in dieser Funktion und den untergeordneten Funktionen, die durch Aufrufe aus der aktuellen Funktion generiert wurden. Der Wert umfasst nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.|
|**inklusive Anwendungszeit %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit, die innerhalb der gesamten inklusiven Anwendungszeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|
|**Durchschnittliche inklusive Anwendungszeit**|Die durchschnittliche inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Maximale inklusive Anwendungszeit**|Die maximale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Minimale inklusive Anwendungszeit**|Die minimale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|

## <a name="application-exclusive-values"></a>Werte für exklusive Anwendungszeit
 Werte für die exklusive Anwendungszeit geben die Zeit an, die in der Funktion verbracht wurde, jedoch ohne die Zeit, die in untergeordneten Funktionen verbracht wurde. Die angegebene Zeit berücksichtigt außerdem keine Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe-/Ausgabeoperationen.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**exklusive Anwendungszeit**|- Bei der aktuellen Funktion die Zeit, die für die direkte Ausführung im Funktionsrumpf aufgewendet wurde. Der Wert umfasst weder die Zeit in untergeordneten Funktionen noch die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.<br />- Bei einer aufrufenden Funktion die Menge an exklusiver Anwendungszeit für die aktuelle Funktion, die von Aufrufen aus dieser aufrufenden Funktion generiert wurde.<br />- Bei einer aufgerufenen Funktion die Zeit in dieser Funktion, die auf Aufrufe aus der aktuellen Funktion entfällt. Der Wert umfasst weder die Zeit in untergeordneten Funktionen der aufgerufenen Funktion noch die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.|
|**Exklusive Anwendungszeit %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der exklusiven Gesamtanwendungszeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|
|**Durchschnittliche exklusive Anwendungszeit**|Die durchschnittliche exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|
|**Minimale exklusive Anwendungszeit**|Die minimale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)
- [Aufrufer-/Aufgerufener-Ansicht – .NET-Speichersamplingdaten](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Aufrufer-/Aufgerufener-Ansicht – Instrumentierungsdaten](../profiling/caller-callee-view-instrumentation-data.md)
- [Aufrufer-/Aufgerufener-Ansicht: Samplingdaten](../profiling/caller-callee-view-sampling-data.md)
