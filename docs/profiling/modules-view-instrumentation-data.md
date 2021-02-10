---
title: Modulansicht – Profiler-Instrumentationsdaten | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Modulansicht. In dieser werden die Leistungsdaten nach den in den Profilerstellungsdaten enthaltenen Modulen gruppiert angezeigt.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 031068d159b7004b7cfe7fcf1c747c2eb582afc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879773"
---
# <a name="modules-view---instrumentation-data"></a>Modulansicht: Instrumentierungsdaten
In der Modulansicht werden die Leistungsdaten nach den in den Profilerstellungsdaten enthaltenen Modulen gruppiert angezeigt. Die Funktionen des Moduls werden unter dem Modulknoten aufgeführt.

## <a name="general"></a>Allgemein
 Die allgemeinen Spalten bezeichnen die Funktion in einer Ansichtszeile.

|Spalte|Beschreibung|
|------------|-----------------|
|**Name**|Der Name der Funktion oder des Moduls.|
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|
|**Anzahl der Aufrufe**|Die Gesamtzahl von Aufrufen dieser Funktion oder dieses Moduls.|
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|
|**Prozessname**|Der Name des Prozesses, in dem das Modul oder die Funktion ausgeführt wurde.|
|**Exklusive Zeit der Restkapazität für Überprüfungen**|Der zusätzliche Zeitaufwand für die Funktion oder das Modul aufgrund der Instrumentation.|
|**Inklusive Zeit der Restkapazität für Überprüfungen**|Der zusätzliche Zeitaufwand für die Funktion oder das Modul und die zugehörigen untergeordneten Funktionen aufgrund der Instrumentation.|

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
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle der Aufrufliste ausgeführt wurde. Sie umfasst nur den zeitlichen Aufwand für Aufrufe des Betriebssystems (z.B. Kontextwechsel und Eingabe-/Ausgabeoperationen), aber nicht die Zeit, die für untergeordnete Funktionen aufgewendet wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**verstrichene exklusive Zeit**|- Bei einer Funktion die für das Modul oder die Funktion aufgewendete Zeit. Sie umfasst nur den zeitlichen Aufwand für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen), aber nicht die Zeit, die für untergeordnete Funktionen aufgewendet wurde.<br />- Bei einem Modul die insgesamt verstrichene exklusive Zeit der Funktionen im Modul.|
|**verstrichene exklusive Zeit %**|Der Prozentsatz der während der Profilerstellung insgesamt verstrichenen exklusiven Zeit, die sich auf die insgesamt verstrichene exklusive Zeit dieses Moduls oder dieser Funktion bezieht.|
|**Durchschnittlich verstrichene exklusive Zeit**|- Bei einer Funktion die im Durchschnitt für einen Aufruf dieser Funktion verstrichene exklusive Zeit.<br />- Bei einem Modul die im Durchschnitt für alle Aufrufe von Funktionen in diesem Modul verstrichene exklusive Zeit.|
|**Maximal verstrichene exklusive Zeit**|- Bei einer Funktion die für einen Aufruf dieser Funktion maximal verstrichene exklusive Zeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul maximal verstrichene exklusive Zeit.|
|**Mindestens verstrichene exklusive Zeit**|- Bei einer Funktion die für einen Aufruf dieses Moduls oder dieser Funktion mindestens verstrichene exklusive Zeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul mindestens verstrichene exklusive Zeit.|

## <a name="application-inclusive-values"></a>Werte für inklusive Anwendungszeit
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat. Die Zeit umfasst nicht den zeitlichen Aufwand für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen), sondern nur die Zeit, die für untergeordnete Funktionen aufgewendet wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**inklusive Anwendungszeit**|- Bei einer Funktion die für Aufrufe der Funktion aufgewendete Zeit. Sie umfasst nur den zeitlichen Aufwand für untergeordnete Funktionen, aber nicht die Zeit, die für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen) aufgewendet wurde.<br />- Bei einem Modul die Zeit, in der sich mindestens eine Funktion im Modul auf der Aufrufliste befunden hat. Berücksichtigt keine Zeit, die für Aufrufe des Betriebssystems aufgewendet wurde.|
|**inklusive Anwendungszeit %**|Der Prozentsatz der während der Profilerstellung insgesamt verstrichenen inklusiven Zeit, die sich auf die inklusive Anwendungszeit dieses Moduls oder dieser Funktion bezieht.|
|**Durchschnittliche inklusive Anwendungszeit**|- Bei einer Funktion die im Durchschnitt für einen Aufruf dieser Funktion aufgewendete inklusive Anwendungszeit.<br />- Bei einem Modul die im Durchschnitt für alle Aufrufe von Funktionen in diesem Modul aufgewendete inklusive Anwendungszeit.|
|**Maximale inklusive Anwendungszeit**|- Bei einer Funktion die für einen Aufruf dieser Funktion maximal aufgewendete inklusive Anwendungszeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul maximal aufgewendete inklusive Anwendungszeit.|
|**Minimale inklusive Anwendungszeit**|- Bei einer Funktion die für einen Aufruf dieses Moduls oder dieser Funktion mindestens aufgewendete inklusive Anwendungszeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul mindestens aufgewendete inklusive Anwendungszeit.|

## <a name="application-exclusive-values"></a>Werte für exklusive Anwendungszeit
 Werte für die exklusive Anwendungszeit geben die Zeit an, die im Modul oder in der Funktion verbracht wurde. Sie umfasst weder den zeitlichen Aufwand für untergeordnete Funktionen noch die Zeit, die für Aufrufe des Betriebssystems (z.B. Kontextwechsel oder Eingabe- und Ausgabeoperationen) aufgewendet wurde.

|Spalte|BESCHREIBUNG|
|------------|-----------------|
|**exklusive Anwendungszeit**|Die für alle Aufrufe von diesem Modul oder dieser Funktion aufgewendete exklusive Anwendungszeit.|
|**Exklusive Anwendungszeit %**|Der Prozentsatz der während der Profilerstellung insgesamt verstrichenen exklusiven Zeit, die sich auf die exklusive Anwendungszeit dieses Moduls oder dieser Funktion bezieht.|
|**Durchschnittliche exklusive Anwendungszeit**|- Bei einer Funktion die im Durchschnitt für einen Aufruf dieser Funktion aufgewendete exklusive Anwendungszeit.<br />- Bei einem Modul die im Durchschnitt für alle Aufrufe von Funktionen in diesem Modul aufgewendete exklusive Anwendungszeit.|
|**Maximale exklusive Anwendungszeit**|- Bei einer Funktion die für einen Aufruf dieser Funktion maximal aufgewendete exklusive Anwendungszeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul maximal aufgewendete exklusive Anwendungszeit.|
|**Minimale exklusive Anwendungszeit**|- Bei einer Funktion die für einen Aufruf dieses Moduls oder dieser Funktion mindestens aufgewendete exklusive Anwendungszeit.<br />- Bei einem Modul die für alle Aufrufe von Funktionen in diesem Modul mindestens aufgewendete exklusive Anwendungszeit.|

## <a name="see-also"></a>Siehe auch
- [Modulansicht](../profiling/modules-view-sampling-data.md)
- [Modulansicht: .NET-Speicherinstrumentierungsdaten](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modulansicht: Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)
