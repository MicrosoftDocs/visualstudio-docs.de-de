---
title: Modulansicht – .NET-Speicherinstrumentationsdaten im Profiler | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie in der Modulansicht der .NET-Speicherbelegungsdaten, die durch Verwendung der Instrumentationsmethode erfasst wurden, die Arbeitsspeicher- und Zeitsteuerungsdaten nach Modul gruppiert werden.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4ffa80d938556c33dc8eafec3068aef257219071
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879812"
---
# <a name="modules-view---net-memory-instrumentation-data"></a>Modulansicht: .NET-Speicherinstrumentierungsdaten
In der Modulansicht der .NET-Speicherbelegungsdaten, die mithilfe der Instrumentationsmethode erfasst wurden, werden die Arbeitsspeicher- und Zeitsteuerungsdaten nach den Modulen gruppiert, die während der Profilerstellung ausgeführt wurden. Die Profilerstellungsdaten für die Funktionen des Moduls werden unter dem Modulknoten aufgeführt.

## <a name="general"></a>Allgemein

|Spalte|Beschreibung|
|------------|-----------------|
|**Name**|Der Name der Funktion oder des Moduls.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Anzahl der Aufrufe**|Die Gesamtzahl von Aufrufen dieser Funktion oder dieses Moduls.|
|**Quelldatei**|Die Quelldatei mit der Definition dieser Funktion.|
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses, in dem das Modul oder die Funktion ausgeführt wurde.|
|**Exklusive Zeit der Restkapazität für Überprüfungen**|Der zusätzliche Zeitaufwand für die Funktion oder das Modul aufgrund der Instrumentation.|
|**Inklusive Zeit der Restkapazität für Überprüfungen**|Der zusätzliche Zeitaufwand für die Funktion oder das Modul und die zugehörigen untergeordneten Funktionen aufgrund der Instrumentation.|

## <a name="net-memory-values"></a>.NET-Arbeitsspeicherwerte
 Die inklusiven .NET-Arbeitsspeicherwerte einer Funktion geben die Anzahl (Zuordnungen) und die Größe (Bytes) der Objekte an, die von der Funktion und ihren untergeordneten Funktionen erstellt wurden.

 Die exklusiven Arbeitsspeicherwerte geben die Anzahl und die Größe der Objekte an, die von der Funktion, nicht jedoch von den zugehörigen untergeordneten Funktionen erstellt wurden.

 Die Werte des inklusiven und des exklusiven Arbeitsspeichers eines Moduls sind die Summe der Werte des inklusiven und des exklusiven Arbeitsspeichers der Funktionen in dem Modul.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**Inklusive Zuordnungen**|- Bei einer Funktion die Gesamtzahl von Objekten, die von der Funktion erstellt wurden. Die Zahl umfasst auch Objekte, die von den von der Funktion aufgerufenen Funktionen erstellt wurden.<br />- Bei einem Modul die Anzahl von Objekten, die während einer Profilerstellung zugeordnet wurden, als mindestens eine Funktion des Moduls ausgeführt wurde. Diese Zahl umfasst auch Objekte, die von durch den Aufruf von Modulfunktionen generierten Funktionen zugeordnet wurden.|
|**Inklusive Speicherbelegungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung als inklusive Zuordnungen dieses Moduls oder dieser Funktion zugeordnet wurden.|
|**Exklusive Speicherbelegungen**|- Bei einer Funktion die Anzahl von Objekten, die während der Ausführung von Code im Funktionstext (d.h. während sich die Funktion auf der obersten Ebene der Aufrufliste befand) erstellt wurden. Diese Zahl umfasst keine Objekte, die in den von dieser Funktion aufgerufenen Funktionen erstellt wurden.<br />- Bei einem Modul die Summe der exklusiven Zuordnungen der Funktionen im Modul.|
|**Exklusive Zuordnungen %**|Der Prozentsatz aller Objekte, die während der Profilerstellung als exklusive Zuordnungen dieses Moduls oder dieser Funktion zugeordnet wurden.|
|**Exklusive Bytes**|- Bei einer Funktion die Gesamtzahl von Bytes im Arbeitsspeicher, die während der Ausführung von Code im Funktionstext (d.h. während sich die Funktion auf der obersten Ebene der Aufrufliste befand) zugeordnet wurden. Diese Zahl umfasst nicht die Bytes, die in den von der Funktion aufgerufenen Funktionen zugeordnet wurden.<br />- Bei einem Modul die Summe der exklusiven Bytes, die von den Funktionen im Modul zugeordnet wurden.|
|**Exklusive Bytes %**|Der Prozentsatz aller während der Profilerstellung zugeordneten Bytes, die exklusive Bytes des Moduls, der Funktion, der Zeile oder der Anweisung waren.|
|**Inklusive Bytes**|- Bei einer Funktion die Gesamtzahl von Bytes, die von der Funktion zugeordnet wurden. Diese Zahl umfasst auch Bytes, die in von der Funktion aufgerufenen Funktionen zugeordnet wurden.<br />- Bei einem Modul die Anzahl von bei einer Profilerstellung zugeordneten Bytes, die während der Ausführung von mindestens einer Funktion des Moduls zugeordnet wurden. Diese Zahl umfasst auch Objekte, die in allen von den Modulfunktionen aufgerufenen Funktionen erstellt wurden.|
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes, die während der Profilerstellung als inklusive Bytes dieses Moduls oder dieser Funktion zugeordnet wurden.|

## <a name="elapsed-inclusive-values"></a>Werte für verstrichene inklusive Zeit
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst den zeitlichen Aufwand für untergeordnete Funktionen und Aufrufe des Betriebssystems (z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen).

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**verstrichene inklusive Zeit**|- Bei einer Funktion die für die Funktion aufgewendete Zeit. Sie umfasst den zeitlichen Aufwand für untergeordnete Funktionen und Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen).<br />- Bei einem Modul die Zeit, in der sich mindestens eine Funktion im Modul auf der Aufrufliste befunden hat.|
|**verstrichene inklusive Zeit %**|Der Prozentsatz der während der Profilerstellung insgesamt verstrichenen inklusiven Zeit, die sich auf die insgesamt verstrichene inklusive Zeit dieses Moduls oder dieser Funktion bezieht.|
|**Durchschnittlich verstrichene inklusive Zeit**|- Bei einer Funktion die im Durchschnitt für einen Aufruf dieser Funktion verstrichene inklusive Zeit.<br />- Bei einem Modul die im Durchschnitt für alle Aufrufe von Funktionen in diesem Modul verstrichene inklusive Zeit.|
|**Maximal verstrichene inklusive Zeit**|- Bei einer Funktion die für einen Aufruf dieser Funktion maximal verstrichene inklusive Zeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul maximal verstrichene inklusive Zeit.|
|**Mindestens verstrichene inklusive Zeit**|- Bei einer Funktion die für einen Aufruf dieses Moduls oder dieser Funktion mindestens verstrichene inklusive Zeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul mindestens verstrichene inklusive Zeit.|

## <a name="elapsed-exclusive-values"></a>Werte für verstrichene exklusive Zeit
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle der Aufrufliste ausgeführt wurde. Sie umfasst nur den zeitlichen Aufwand für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen), aber nicht die Zeit, die für untergeordnete Funktionen aufgewendet wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**verstrichene exklusive Zeit**|- Bei einer Funktion die für das Modul oder die Funktion aufgewendete Zeit. Sie umfasst nur den zeitlichen Aufwand für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen), aber nicht die Zeit, die für untergeordnete Funktionen aufgewendet wurde.<br />- Bei einem Modul die insgesamt verstrichene exklusive Zeit der Funktionen im Modul.|
|**verstrichene exklusive Zeit %**|Der Prozentsatz der während der Profilerstellung insgesamt verstrichenen exklusiven Zeit, die sich auf die insgesamt verstrichene exklusive Zeit dieses Moduls oder dieser Funktion bezieht.|
|**Durchschnittlich verstrichene exklusive Zeit**|- Bei einer Funktion die im Durchschnitt für einen Aufruf dieser Funktion verstrichene exklusive Zeit.<br />- Bei einem Modul die im Durchschnitt für alle Aufrufe von Funktionen in diesem Modul verstrichene exklusive Zeit.|
|**Maximal verstrichene exklusive Zeit**|- Bei einer Funktion die für einen Aufruf dieser Funktion maximal verstrichene exklusive Zeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul maximal verstrichene exklusive Zeit.|
|**Mindestens verstrichene exklusive Zeit**|- Bei einer Funktion die für einen Aufruf dieses Moduls oder dieser Funktion mindestens verstrichene exklusive Zeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul mindestens verstrichene exklusive Zeit.|

## <a name="application-inclusive-values"></a>Werte für inklusive Anwendungszeit
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst die Zeit in untergeordneten Funktionen, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**inklusive Anwendungszeit**|- Bei einer Funktion die für Aufrufe der Funktion aufgewendete Zeit. Sie umfasst nur den zeitlichen Aufwand für untergeordnete Funktionen, aber nicht die Zeit, die für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen) aufgewendet wurde.<br />- Bei einem Modul nur der Zeitraum, in dem sich mindestens eine Funktion des Moduls auf der Aufrufliste befunden hat, aber nicht die Zeit für Aufrufe des Betriebssystems.|
|**inklusive Anwendungszeit %**|Der Prozentsatz der während der Profilerstellung insgesamt verstrichenen inklusiven Zeit, die sich auf die inklusive Anwendungszeit dieses Moduls oder dieser Funktion bezieht.|
|**Durchschnittliche inklusive Anwendungszeit**|- Bei einer Funktion die im Durchschnitt für einen Aufruf dieser Funktion aufgewendete inklusive Anwendungszeit.<br />- Bei einem Modul die im Durchschnitt für alle Aufrufe von Funktionen in diesem Modul aufgewendete inklusive Anwendungszeit.|
|**Maximale inklusive Anwendungszeit**|- Bei einer Funktion die für einen Aufruf dieser Funktion maximal aufgewendete inklusive Anwendungszeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul maximal aufgewendete inklusive Anwendungszeit.|
|**Minimale inklusive Anwendungszeit**|- Bei einer Funktion die für einen Aufruf dieses Moduls oder dieser Funktion mindestens aufgewendete inklusive Anwendungszeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul mindestens aufgewendete inklusive Anwendungszeit.|

## <a name="application-exclusive-values"></a>Werte für exklusive Anwendungszeit
 Werte für die exklusive Anwendungszeit geben die Zeit an, die im Modul oder in der Funktion verbracht wurde. Sie umfasst weder den zeitlichen Aufwand für untergeordnete Funktionen noch die Zeit, die für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen) aufgewendet wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**exklusive Anwendungszeit**|- Bei einer Funktion die für einen Aufruf dieser Funktion insgesamt aufgewendete exklusive Anwendungszeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul insgesamt aufgewendete exklusive Anwendungszeit.|
|**Exklusive Anwendungszeit %**|Der Prozentsatz der während der Profilerstellung insgesamt verstrichenen exklusiven Zeit, die sich auf die exklusive Anwendungszeit dieses Moduls oder dieser Funktion bezieht.|
|**Durchschnittliche exklusive Anwendungszeit**|- Bei einer Funktion die im Durchschnitt für einen Aufruf dieser Funktion aufgewendete exklusive Anwendungszeit.<br />- Bei einem Modul die im Durchschnitt für alle Aufrufe von Funktionen in diesem Modul aufgewendete exklusive Anwendungszeit.|
|**Maximale exklusive Anwendungszeit**|- Bei einer Funktion die für einen Aufruf dieser Funktion maximal aufgewendete exklusive Anwendungszeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul maximal aufgewendete exklusive Anwendungszeit.|
|**Minimale exklusive Anwendungszeit**|- Bei einer Funktion die für einen Aufruf dieses Moduls oder dieser Funktion mindestens aufgewendete exklusive Anwendungszeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul mindestens aufgewendete exklusive Anwendungszeit.|

## <a name="see-also"></a>Siehe auch
- [Modulansicht: Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modulansicht](../profiling/modules-view-instrumentation-data.md)
- [Modulansicht](../profiling/modules-view-sampling-data.md)
