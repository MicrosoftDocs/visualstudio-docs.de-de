---
title: Auswählen von Sammlungsmethoden | Microsoft-Dokumentation
description: Die Visual Studio Profilerstellungstools unterstützen drei Methoden für das Sammeln von Leistungsdaten. In diesem Artikel erfahren Sie, wie Sie die richtige Methode für Ihre Anwendung auswählen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a304006a778dc4766e6b4be9ceb133450c0dfb52
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876913"
---
# <a name="how-to-choose-collection-methods"></a>Vorgehensweise: Auswählen von Sammlungsmethoden

Die Visual Studio-Profilerstellungstools unterstützen drei Methoden zum Sammeln von Leistungsdaten: Sampling, Instrumentierung und Parallelität. Sie können zum Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauerdaten entweder die Sampling- oder Instrumentierungsmethode verwenden.

Sie können die die Eigenschaft **Methode** der Leistungssitzung verwenden, um die geeignetste Sammlungsmethode für Ihre Anwendung anzugeben. Sie können die Sammelmethode vom Leistungs-Assistent, Leistungs-Explorer oder von den Eigenschaftenseiten der Leistungssitzung festlegen. Wenn Sie die Befehlszeilentools verwenden, finden Sie weitere Informationen unter [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md).

## <a name="performance-wizard"></a>Leistungs-Assistent

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>So wählen Sie eine Sammlungsmethode mithilfe des Leistungs-Assistent aus

- Wählen Sie auf der ersten Seite des Assistenten eine der folgenden Optionen aus:

| Option | Beschreibung |
|----------------------------| - |
| **CPU-Sampling** | Sammelt Anwendungsstatistiken, die für die erste Analyse und zum Analysieren von CPU-Auslastungsproblemen nützlich sind. |
| **Instrumentation** | Sammelt ausführliche Zeitsteuerungsdaten, die zur gezielten Analyse und zur Analyse von Eingabe/Ausgabe-Leistungsproblemen nützlich sind. |
| **.NET-Speicherbelegung** | Sammelt .NET Framework-Speicherbelegungsdaten mithilfe der Sampling-Profilerstellungsmethode. |
| **Parallelität** | Sammelt numerischen Ressourcenkonfliktdaten. |

## <a name="performance-explorer"></a>Leistungs-Explorer

### <a name="to-select-a-collection-method-using-performance-explorer"></a>So wählen Sie eine Sammelmethode mithilfe des Leistungs-Explorers aus

1. Klicken Sie auf der Symbolleiste **Leistungs-Explorer** auf den Pfeil neben der Dropdownliste **Methode**

2. Klicken Sie auf die Sammlungsmethode, die Sie bevorzugen.

## <a name="performance-session-property-pages"></a>Eigenschaftenseiten der Leistungssitzung

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>So wählen Sie die Sampling- und Instrumentationsmethode mithilfe den Eigenschaften der Leistungssitzung aus

1. Klicken Sie im **Leistungs-Explorer** auf die Leistungssitzung.

     Dateinamen von Leistungssitzungen verfügen über die Erweiterung *.psess*.

2. Klicken Sie im mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie anschließend auf **Eigenschaften**.

3. Klicken Sie in den **Eigenschaftenseiten** auf **Allgemein**.

4. Klicken Sie auf die Sammlungsmethode, die Sie bevorzugen.

    - Informationen zu den anderen Optionen, die beim Sammeln von Samplingdaten verfügbar sind, finden Sie unter [Sammeln von Leistungsstatistiken durch Sampling](../profiling/collecting-performance-statistics-by-using-sampling.md)

    - Informationen zu den anderen Optionen, die beim Sammeln von Samplingdaten verfügbar sind, finden Sie unter [Sammeln von ausführlichen Zeitsteuerdaten durch Instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>So wählen Sie die Datensammlung des .NET-Speichers mithilfe der Eigenschaften der Leistungssitzung aus.

1. Klicken Sie im **Leistungs-Explorer** auf die Leistungssitzung.

     Ein Dateiname einer Leistungssitzung hat die Dateiendung „.psess“.

2. Klicken Sie im mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie anschließend auf **Eigenschaften**.

3. Klicken Sie in den **Eigenschaftenseiten** auf **Allgemein**.

4. Klicken Sie auf **Sampling** oder **Instrumentation**.

5. Klicken Sie zum Sammeln von der Größe und Anzahl von .NET Framework-Objektzuweisungen auf **.NET-Objektzuweisungsinformationen auflisten**.

6. (Optional) Klicken Sie auf **Lebensdauerinformation für .NET-Objekte auflisten** zum Sammeln von Daten über die Generierung der automatische Speicherbereinigung, in dem der Objektspeicher freigegeben wurde.

     Informationen zu den anderen Optionen, die beim Sammeln von .NET-Speicherdaten verfügbar sind, finden Sie unter [Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>So wählen Sie die Sammlung von Parallelitätsdaten mithilfe der Eigenschaften der Leistungssitzung aus.

1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie in den **Eigenschaftenseiten** auf **Allgemein**.

3. Klicken Sie auf **Parallelität**.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
[Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)
[Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)
